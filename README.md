# Brantenna Creations Brand Assets

Single source of truth for client brand assets used in email signatures, marketing collateral, and external surfaces. This repository is intentionally public so referenced assets resolve in any email client without authentication.

Maintained by Brantenna Creations as part of the Brantenna Substrate operating standard. All work on these assets follows the Constitution at `WEBSITE_DEVELOPMENT_CONSTITUTION.md` v1.0.0.

## Repository Structure

```
brand-assets/
  Logo-Web.png        Daima Luxury primary logo (transparent PNG)
  signature.html      Daima Luxury canonical email signature block
  README.md           This document
```

When additional clients are onboarded, each receives a dedicated subdirectory at the repository root, and this README is updated to reflect the new asset set.

## Asset Registry

### Daima Luxury Limited

| Asset | Public URL | Notes |
|---|---|---|
| Logo | `https://cdn.jsdelivr.net/gh/brantenna-creations/brand-assets@main/Logo-Web.png` | Primary corporate mark, transparent PNG, served via jsDelivr CDN for global low-latency resolution |
| Signature HTML | `https://cdn.jsdelivr.net/gh/brantenna-creations/brand-assets@main/signature.html` | Canonical signature block installed in every Daima mailbox |

The jsDelivr CDN is preferred over `raw.githubusercontent.com` because jsDelivr is purpose-built for serving GitHub-hosted assets in production, applies global edge caching, and does not enforce GitHub's hot-link rate limits.

## Daima Luxury Mailbox Registry

Ten mailboxes exist on `daimaluxury.co.ke`, hosted at HostPinnacle. The same canonical signature is installed in every mailbox. Sender identity is typed into the message body at compose time and never embedded into the signature.

| Mailbox | Function | Outbound Capable |
|---|---|---|
| `accounts@daimaluxury.co.ke` | Accounts and finance | Yes |
| `admin@daimaluxury.co.ke` | Administration and operations | Yes |
| `billing@daimaluxury.co.ke` | Invoicing and billing | Yes |
| `careers@daimaluxury.co.ke` | Recruitment and careers | Yes |
| `contact@daimaluxury.co.ke` | General contact and concierge | Yes |
| `dmarc@daimaluxury.co.ke` | DMARC report aggregation | No (inbound reports only) |
| `hello@daimaluxury.co.ke` | First contact and inquiries | Yes |
| `info@daimaluxury.co.ke` | Front office and information | Yes |
| `sales@daimaluxury.co.ke` | Reservations and sales | Yes |
| `support@daimaluxury.co.ke` | Client support | Yes |

The signature is installed on the nine outbound-capable mailboxes. The `dmarc@` mailbox is an inbound-only address for DMARC aggregate reports and does not require a signature.

## Installation Procedure (Roundcube Webmail)

For each mailbox, complete this procedure once.

1. Log into Roundcube at `https://daimaluxury.co.ke/webmail` using the mailbox credentials.
2. Click the gear icon in the top-right corner to open Settings.
3. In the left sidebar, click `Identities`.
4. Click the row for the mailbox identity (the email address).
5. Tick the `HTML signature` checkbox.
6. In the signature editor toolbar, click the `< >` Source Code button to switch the editor into raw HTML mode.
7. Open `signature.html` from this repository in a browser, copy its entire contents, and paste into the source code editor.
8. Click the `< >` Source Code button again to exit source mode. The rendered signature appears in the editor.
9. Click `Save` at the bottom of the page.
10. Compose a test message to a Gmail address and an Outlook address. Confirm the logo loads, the layout holds, and the links are clickable in both inboxes.

## Compose Convention

The signature carries the corporate brand block only. Sender identity is typed into the message body above the signature when applicable. The recommended closing format is:

```
Kind regards,

Full Name
Role or Department
```

For shared mailboxes (`info@`, `contact@`, `hello@`, `sales@`, `support@`), the closing may use a department designation rather than an individual name when the message is sent on behalf of the team rather than an individual. Examples:

```
Kind regards,

Daima Luxury Concierge Desk
```

```
Kind regards,

Daima Luxury Reservations
```

For named-individual mailboxes or when an individual is signing a shared-mailbox message, the personal closing format applies.

## Maintenance Procedure

Updates to the signature are applied at the canonical file in this repository, then propagated to mailboxes per the rules below.

1. Edit `signature.html` in this repository.
2. Increment the version number in the header comment.
3. Commit using a conventional commit message, for example: `chore(signature): update tagline colour to brand-secondary`.
4. Apply the change to mailboxes per the propagation rules below.

### Propagation Rules

| Type of Change | Propagation |
|---|---|
| Image asset replaced (logo, banner) | Automatic. Every installed signature renders the new image on next email open because the asset is referenced by URL, not embedded. No mailbox re-installation required. |
| HTML structure, text, links, colours | Manual. The Installation Procedure must be repeated for every mailbox. Allow approximately three minutes per mailbox. |
| Asset URL change (e.g., file rename) | Manual. The new URL must be reflected in `signature.html`, then mailboxes re-installed. |

## Versioning

The version number in the `signature.html` header is the audit trail for which canonical revision is currently installed. The version is incremented on every change, however small.

| Version | Date | Change |
|---|---|---|
| 1.0.0 | 2026-05-07 | Initial canonical signature established for Daima Luxury Limited |

## Audit Log

| Mailbox | Last Installation | Version |
|---|---|---|
| `accounts@daimaluxury.co.ke` | (pending) | (pending) |
| `admin@daimaluxury.co.ke` | (pending) | (pending) |
| `billing@daimaluxury.co.ke` | (pending) | (pending) |
| `careers@daimaluxury.co.ke` | (pending) | (pending) |
| `contact@daimaluxury.co.ke` | (pending) | (pending) |
| `hello@daimaluxury.co.ke` | (pending) | (pending) |
| `info@daimaluxury.co.ke` | (pending) | (pending) |
| `sales@daimaluxury.co.ke` | (pending) | (pending) |
| `support@daimaluxury.co.ke` | (pending) | (pending) |

The audit log is updated by the installer after each mailbox installation completes successfully.

## Rights

The contents of this repository are the property of Brantenna Creations and the named clients. Logo files and signature templates are not redistributable. Brantenna Creations reserves all rights to the registry structure and procedures documented herein.
