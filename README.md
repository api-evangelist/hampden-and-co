# Hampden & Co (hampden-and-co)

Hampden & Co (trading as Hampden Bank since March 2024) is an independent UK private bank headquartered in Charlotte Square, Edinburgh, with offices in London and Manchester, serving high-net-worth individuals, their families, and their businesses with day-to-day banking, deposits, and specialist lending. Incorporated in 2010 as "Scoban" and launched in 2015, it was the first newly created UK private bank in three decades. It is a shareholder-owned public limited company (SC386922) — not a mutual or building society — authorised by the Prudential Regulation Authority and regulated by the Financial Conduct Authority and the PRA.

Hampden & Co is not one of the CMA9 mandated banks, but it is an FCA-authorised ASPSP registered with the Open Banking Implementation Entity (OBIE). It exposes a PSD2 dedicated interface — an Open Data reference API plus the OBIE Read/Write family (Account & Transaction Information, Payment Initiation, and Confirmation of Funds) — onboarded through a developer sandbox portal and secured with FAPI-grade OAuth2/OIDC, mutual-TLS, PSD2 strong customer authentication, and eIDAS/OBIE certificate-based dynamic client registration.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/hampden-and-co/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/hampden-and-co/refs/heads/main/apis.yml)

## Tags

- Financial Services
- Banking
- Private Banking
- Open Banking
- PSD2
- OBIE
- FAPI
- United Kingdom
- Payments
- Account Information

## Timestamps

- **Created:** 2026-07-23
- **Modified:** 2026-07-23

## APIs

### Hampden & Co Open Data API

Public, unauthenticated Open Data reference API conforming to the OBIE UK Open Banking Open Data standard. Listed on Hampden & Co's Open Banking register entry; a live Open Data endpoint could not be independently confirmed at bootstrap (the developer portal is a single-page app that returns HTML for all paths).

- **Human URL:** [https://developer-sandbox.hampdendigital.com/](https://developer-sandbox.hampdendigital.com/)

#### Tags

- Open Data
- Reference Data

#### Properties

- [Documentation](https://developer-sandbox.hampdendigital.com/home)
- [Registration](https://www.openbanking.org.uk/regulated-providers/hampden-co-plc/)

### Hampden & Co Account & Transaction Information API

OBIE Read/Write Account Information Service (AIS). The bundled OpenAPI is the shared OBIE Read/Write standard (v4.0.1), not a Hampden-proprietary contract; production access requires TPP onboarding with eIDAS/OBIE certificates.

- **Human URL:** [https://developer-sandbox.hampdendigital.com/](https://developer-sandbox.hampdendigital.com/)

#### Tags

- Account Information
- AIS

#### Properties

- [OpenAPI](openapi/hampden-and-co-account-information-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://developer-sandbox.hampdendigital.com/home)
- [API Reference](https://standards.openbanking.org.uk/api-specifications/latest/)
- [Registration](https://www.hampdenbank.com/tpp-registration)

### Hampden & Co Payment Initiation API

OBIE Read/Write Payment Initiation Service (PIS). The bundled OpenAPI is the shared OBIE Read/Write standard (v4.0.1), not a Hampden-proprietary contract; production access requires TPP onboarding with eIDAS/OBIE certificates and PSD2 strong customer authentication.

- **Human URL:** [https://developer-sandbox.hampdendigital.com/](https://developer-sandbox.hampdendigital.com/)

#### Tags

- Payment Initiation
- PIS

#### Properties

- [OpenAPI](openapi/hampden-and-co-payment-initiation-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://developer-sandbox.hampdendigital.com/home)
- [API Reference](https://standards.openbanking.org.uk/api-specifications/latest/)
- [Registration](https://www.hampdenbank.com/tpp-registration)

### Hampden & Co Confirmation of Funds API

OBIE Read/Write Confirmation of Funds Service (CBPII). The bundled OpenAPI is the shared OBIE Read/Write standard (v4.0.1), not a Hampden-proprietary contract; production access requires TPP onboarding with eIDAS/OBIE certificates.

- **Human URL:** [https://developer-sandbox.hampdendigital.com/](https://developer-sandbox.hampdendigital.com/)

#### Tags

- Confirmation of Funds
- CBPII

#### Properties

- [OpenAPI](openapi/hampden-and-co-confirmation-of-funds-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://developer-sandbox.hampdendigital.com/home)
- [API Reference](https://standards.openbanking.org.uk/api-specifications/latest/)
- [Registration](https://www.hampdenbank.com/tpp-registration)

## Common Properties

- [Website](https://www.hampdenbank.com/)
- [Developer Portal](https://developer-sandbox.hampdendigital.com/)
- [Documentation](https://developer-sandbox.hampdendigital.com/home)
- [Sign Up (TPP Registration)](https://www.hampdenbank.com/tpp-registration)
- [Open Banking Register](https://www.openbanking.org.uk/regulated-providers/hampden-co-plc/)
- [LinkedIn](https://www.linkedin.com/company/hampden-bank)
- [Blog](https://www.hampdenbank.com/insights)
- [Support](https://www.hampdenbank.com/contact-us)
- [Terms of Service](https://www.hampdenbank.com/terms-conditions)
- [Privacy Policy](https://www.hampdenbank.com/privacy-notice)
- [Cookie Policy](https://www.hampdenbank.com/cookie-policy)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
