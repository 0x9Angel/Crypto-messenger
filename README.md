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
| No enterprise tooling | **SSO, audit logs, on-prem licensing** built-in (SCIM on enterprise roadmap) |
| Phone number identity | **Cryptographic identity** — anonymous if you choose |

---

## Built on three pillars

###  Cryptography that audits well
- End-to-end encryption via **X3DH + Double Ratchet** (the protocol behind Signal).
- **Post-quantum hybrid** key exchange (X25519 + ML-KEM-768, NIST FIPS 203).
- **Forward secrecy** and post-compromise security at every layer: compromise tomorrow doesn't unlock what was said yesterday.
- Identity verification via a Signal-style **60-digit safety number** (forced, persisted), with a verified flag and an alert on pinned-key change (MITM detection). Identity-key rotation and revocation are implemented end-to-end.
- Sealed-sender envelopes — even the receiving relay doesn't know who sent the message.

###  A mixnet underneath, not just E2E on top
- Crypto runs over [**Gotham**](https://github.com/0x9Angel/gotham-protocol), a custom Sphinx-style mixnet (Gotham is now the sole transport).
- Sphinx v0.2 fixed-size 2048-byte packets, with an X25519 + ML-KEM-768 hybrid (post-quantum) KEM per hop, carried over a Noise XK / QUIC link layer.
- Loopix-style Poisson mixing with continuous cover traffic (real user sends are routed through the cover-traffic queue) — once a live network exists, observers should not be able to distinguish active users from idle ones.
- Per-hop payloads are protected by a LIONESS wide-block non-malleable PRP (Anderson–Biham, 4-round) that defeats tagging; path selection enforces global operator and network (/16 IPv4, /48 IPv6) diversity with entry ≠ exit.
- Median round-trip latency: 50–300 ms (vs 800–2000 ms for Tor). Real-time messaging works.
- **Network-level anonymity is a design goal, not yet a live guarantee.** A directory authority and 3 relays are online, but they currently share a single /16, so the (correct) path-diversity guard refuses to build a route — no message has transited the live network yet. This holds *once* a relay network spanning multiple /16s exists and an external audit has been completed. Message **content** protection (E2E, PQ hybrid) is solid and tested today.

###  Designed for enterprise from day one
- **SSO** via OpenID Connect (5 identity providers — Azure Entra, Okta, Keycloak, AD FS and peers).
- **Signed audit logs** (Ed25519) — tamper-evident, exportable as JSONL for SIEM.
- **On-premise license gating** — no phone-home, sovereign deployment.
- **Encrypted local storage** (SQLCipher AES-256 + Argon2id), FTS5 encrypted search, and encrypted DB backup/restore.
- *Enterprise roadmap:* **SCIM 2.0** provisioning and **active/passive HA replication** are planned for the enterprise tier, not yet shipped.

---

## Use cases

- **Defense primes** — Airbus, Thales, Dassault and peers, on programmes where supplier-relationship leakage is unacceptable.
- **Critical infrastructure** — energy, telecoms, banking, on sensitive trade or operations data.
- **Investigative journalism** — protecting sources at the network layer, not just the message layer.
- **Government** — for missions where existing options leave residual metadata risk.

---

## What we resist (and what we don't)

We publish our threat model. Honesty is a feature.

**Resists:** passive network observers, compromise of any single relay, replay/tagging attacks, and future quantum adversaries. By design, traffic-analysis correlation is resisted at < 10k concurrent users — but this property is conditional on a live relay network spanning multiple /16s, which does not exist yet (see Status).

**Does not resist:** global passive adversaries with NSA-level visibility, majority-relay compromise (>60%), endpoint malware on the user's own device, forced disclosure of non-ephemeral key material.

Full threat model published before commercial deployment.

---

## Status

Pre-alpha (v0.7 protocol/product line, Gotham-only transport; app builds tagged v2.1.x). The cryptography is implemented and covered by 338 automated test functions across ~31,919 lines of Rust (workspace `cargo test` green). An internal security audit (2026-05-25) plus several multi-agent adversarial reviews have been run; every confirmed finding was fixed. No external, independent third-party audit has taken place yet.

**Honest reality check.** Message **content** protection (E2E via X3DH + Double Ratchet, PQ hybrid) is solid and testable today. **Network-level anonymity is still a design goal:** a directory authority and 3 relays are online, but all 3 sit on a single /16, so the path-diversity guard (correctly) refuses to build a route — no message has yet transited the live mixnet. That guarantee awaits (a) relays across multiple /16s and (b) an external audit. The protocol is being prepared for external audit. **First commercial pilots planned for 2026.**

We are talking to:
- Tier-1 European defense industrials interested in pilot deployments.
- Cryptographic auditors (Quarkslab, Synacktiv, NCC Group) for the security review.
- Investors aligned with sovereign-tech and post-quantum thesis.


<div align="center">

*Crypto is part of the [Gotham](https://github.com/0x9Angel/gotham-protocol) protocol family.*

**No public source — by design.** Code repository access is granted under NDA to vetted partners (auditors, pilot customers, investors).

</div>
