---
name: Access Hampden & Co accounts and transactions (AIS)
description: >-
  Set up an OBIE account-access consent and read a PSU's accounts, balances, and
  transactions from Hampden & Co's FAPI-secured Account & Transaction Information
  API. Grounded in real operationIds from the OBIE Read/Write v4.0.1 spec.
api: openapi/hampden-and-co-account-information-api-openapi.yml
operations:
  - CreateAccountAccessConsents
  - GetAccountAccessConsentsConsentId
  - GetAccounts
  - GetAccountsAccountId
  - GetAccountsAccountIdBalances
  - GetAccountsAccountIdTransactions
---

# Access Hampden & Co accounts and transactions (AIS)

Hampden & Co is an FCA-authorised ASPSP exposing the OBIE Read/Write Account &
Transaction Information Service (AIS). Access is FAPI-secured: you must be an
authorised TPP (AISP) with an eIDAS/OBIE certificate and dynamically registered
client.

## Prerequisites
- OBIE/eIDAS transport + signing certificates; mutual-TLS to the resource host.
- OAuth2 client credentials (`TPPOAuth2Security`, scope `accounts`) for consent
  creation, and the PSU authorization-code flow (`PSUOAuth2Security`) for SCA.

## Steps
1. **Create the consent** — `CreateAccountAccessConsents`. POST an
   `OBReadConsent1` listing the permissions you need (e.g. `ReadAccountsDetail`,
   `ReadBalances`, `ReadTransactionsDetail`). Send `x-fapi-interaction-id` and a
   signed request. You receive a `ConsentId` in `AwaitingAuthorisation` status.
2. **Get the PSU to authorise (SCA)** — redirect the PSU through the
   authorization-code flow so they complete strong customer authentication and
   authorise the `ConsentId`. Verify status with
   `GetAccountAccessConsentsConsentId` (expect `Authorised`).
3. **List accounts** — `GetAccounts` with the PSU access token returns the
   accounts covered by the consent, each with an `AccountId`.
4. **Read balances** — `GetAccountsAccountIdBalances` for a given `AccountId`.
5. **Read transactions** — `GetAccountsAccountIdTransactions`, filtering with
   `fromBookingDateTime` / `toBookingDateTime`. Page with `Links.Next`.

## Conventions
- Echo/track `x-fapi-interaction-id` on every call (see
  `conventions/hampden-and-co-conventions.yml`).
- Errors return the `OBErrorResponse1` envelope with `UK.OBIE.*` error codes
  (see `errors/hampden-and-co-problem-types.yml`); on `UK.OBIE.Reauthenticate`
  send the PSU back through SCA.
