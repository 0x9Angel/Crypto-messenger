<div align="center">

# Crypto

### Sovereign encrypted messaging for European enterprise and defense

*Built in France · Powered by Gotham mixnet · Post-quantum from day one*

![Status](https://img.shields.io/badge/status-pre--alpha-orange?style=for-the-badge)
![Built with Rust](https://img.shields.io/badge/built%20with-Rust-000?style=for-the-badge&logo=rust)
![License](https://img.shields.io/badge/license-AGPLv3%20%2B%20Commercial-blue?style=for-the-badge)
![Made in EU](https://img.shields.io/badge/Made%20in-EU-003399?style=for-the-badge)

</div>

---

## What is Crypto?

Crypto is an **encrypted messaging platform** designed from scratch for organisations where **metadata leakage is itself a security incident** — defense industrials, banks, investigative journalism, government.

Where existing solutions hide your messages but leak who-talks-to-whom-and-when, Crypto hides **the conversation graph itself**.

> **The problem we solve.** When Signal protects your message but the server still sees that Alice contacted Bob at 14:32 for 4 seconds, an adversary monitoring six months of traffic can reconstruct your entire R&D organisation chart, predict mergers before they're announced, or unmask a journalist's sources — **without ever decrypting a single byte**.

---

## What makes Crypto different

| Most messengers | Crypto |
|---|---|
| Hide message content (E2E encryption) | Same — Signal-protocol grade |
| Leak metadata to the server | **No server sees the conversation graph** |
| Subject to CLOUD Act (US providers) | **EU-sovereign by design** |
| Vulnerable to future quantum computers | **Post-quantum hybrid from day one** |
| No enterprise tooling | **SSO, SCIM, audit logs, on-prem licensing** built-in |
| Phone number identity | **Cryptographic identity** — anonymous if you choose |

---

## Built on three pillars

###  Cryptography that audits well
- End-to-end encryption via **X3DH + Double Ratchet** (the protocol behind Signal).
- **Post-quantum hybrid** key exchange (X25519 + ML-KEM-768, NIST FIPS 203).
- **Forward secrecy** at every layer: compromise tomorrow doesn't unlock what was said yesterday.
- Sealed-sender envelopes — even the receiving relay doesn't know who sent the message.

###  A mixnet underneath, not just E2E on top
- Crypto runs over [**Gotham**](https://github.com/0x9Angel/gotham-protocol), a custom Sphinx-style mixnet.
- Messages traverse 3–5 anonymising hops with Poisson-distributed delays.
- Continuous cover traffic — observers cannot distinguish active users from idle ones.
- Median round-trip latency: 50–300 ms (vs 800–2000 ms for Tor). Real-time messaging works.

###  Designed for enterprise from day one
- **SSO** via OpenID Connect (Azure Entra, Okta, Keycloak, AD FS).
- **SCIM 2.0** provisioning — automated account lifecycle from your directory.
- **Signed audit logs** (Ed25519) — tamper-evident, exportable for compliance.
- **On-premise license gating** — no phone-home, sovereign deployment.
- **Active/passive HA replication** for critical-availability deployments.
- **Encrypted local storage** (SQLCipher + Argon2id).

---

## Use cases

- **Defense primes** — Airbus, Thales, Dassault and peers, on programmes where supplier-relationship leakage is unacceptable.
- **Critical infrastructure** — energy, telecoms, banking, on sensitive trade or operations data.
- **Investigative journalism** — protecting sources at the network layer, not just the message layer.
- **Government** — for missions where existing options leave residual metadata risk.

---

## What we resist (and what we don't)

We publish our threat model. Honesty is a feature.

**Resists:** passive network observers, compromise of any single relay, replay/tagging attacks, traffic-analysis correlation at < 10k concurrent users, future quantum adversaries.

**Does not resist:** global passive adversaries with NSA-level visibility, majority-relay compromise (>60%), endpoint malware on the user's own device, forced disclosure of non-ephemeral key material.

Full threat model published before commercial deployment.

---

## Status

Pre-alpha. The cryptography is implemented and unit-tested. The protocol is being prepared for external audit. **First commercial pilots planned for 2026.**

We are talking to:
- Tier-1 European defense industrials interested in pilot deployments.
- Cryptographic auditors (Quarkslab, Synacktiv, NCC Group) for the security review.
- Investors aligned with sovereign-tech and post-quantum thesis.

---

## Get in touch

-  **Pilot enquiries** — [your-email]
-  **Security disclosure** — [your-pgp-key-fingerprint]
-  **Auditors / partners** — [your-email]
-  **Updates** — [your-handle]

---

<div align="center">

*Crypto is part of the [Gotham](https://github.com/0x9Angel/gotham-protocol) protocol family.*

**No public source — by design.** Code repository access is granted under NDA to vetted partners (auditors, pilot customers, investors).

</div>
