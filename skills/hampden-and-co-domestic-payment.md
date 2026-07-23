---
name: Initiate a domestic payment via Hampden & Co (PIS)
description: >-
  Create a domestic-payment consent, obtain PSU authorisation (SCA), and submit a
  domestic payment through Hampden & Co's FAPI-secured Payment Initiation API,
  using idempotency and detached JWS signing. Grounded in real operationIds from
  the OBIE Read/Write v4.0.1 spec.
api: openapi/hampden-and-co-payment-initiation-api-openapi.yml
operations:
  - CreateDomesticPaymentConsents
  - GetDomesticPaymentConsentsConsentId
  - GetDomesticPaymentConsentsConsentIdFundsConfirmation
  - CreateDomesticPayments
  - GetDomesticPaymentsDomesticPaymentId
---

# Initiate a domestic payment via Hampden & Co (PIS)

Hampden & Co exposes the OBIE Read/Write Payment Initiation Service (PIS) as a
FAPI-secured PSD2 dedicated interface. You must be an authorised PISP with an
eIDAS/OBIE certificate.

## Prerequisites
- OBIE/eIDAS certificates; mutual-TLS to the resource host.
- OAuth2 client credentials (`TPPOAuth2Security`, scope `payments`) and the PSU
  authorization-code flow (`PSUOAuth2Security`) for SCA.
- A detached JWS signature in `x-jws-signature` on request bodies.

## Steps
1. **Create the payment consent** — `CreateDomesticPaymentConsents`. POST an
   `OBWriteDomesticConsent4` with the `Initiation` (debtor/creditor accounts,
   `InstructedAmount`, reference). Include a unique `x-idempotency-key` (valid
   24h) and `x-jws-signature`. You receive a `ConsentId`.
2. **PSU authorisation (SCA)** — redirect the PSU through the authorization-code
   flow to authorise the `ConsentId`. Confirm with
   `GetDomesticPaymentConsentsConsentId` (status `Authorised`).
3. **Optional funds check** — `GetDomesticPaymentConsentsConsentIdFundsConfirmation`
   to confirm the debtor has sufficient funds before submitting.
4. **Submit the payment** — `CreateDomesticPayments`, referencing the authorised
   `ConsentId`, with the same `Initiation` and a fresh `x-idempotency-key`. You
   receive a `DomesticPaymentId`.
5. **Track status** — `GetDomesticPaymentsDomesticPaymentId` to poll the payment
   status.

## Conventions
- Reuse the same `x-idempotency-key` on retries within 24h to avoid duplicate
  payments (see `conventions/hampden-and-co-conventions.yml`).
- Handle `UK.OBIE.Rules.AfterCutOffDateTime` (retry next cut-off) and
  `UK.OBIE.Signature.Invalid` (re-sign) from the `OBErrorResponse1` envelope (see
  `errors/hampden-and-co-problem-types.yml`).
