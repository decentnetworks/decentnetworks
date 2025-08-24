# Decent Network — Whitepaper (v0.92, EN)

## 0) Abstract
The web privileges one‑way fetching over two‑way reachability. Scarce, centralized naming and addressing (IP/DNS), plus perimeterized networks, make inbound access fragile and platform‑dependent. **Decent Network** introduces a **permissionless public communication substrate** where **pubkey is the address**. Discovery uses a signed **DHT**; connectivity comes from a community‑operated layer that supplies **STUN/TURN/relay** capacity and NAT traversal (ICE), with transports such as **WebRTC DataChannel / QUIC / HTTP/3 MASQUE / WebSocket**. Security is end‑to‑end by default. Economics are usage‑based and transparent on public blockchains. The goal is a minimal, neutral base that enables safer, friendlier, and more efficient applications — notably next‑gen social and AI agents.

## 1) Motivation & Problem Statement
- **Visibility asymmetry**: publishers are visible; visitors are effectively invisible, complicating interaction and durable reputation.
- **IP/DNS scarcity & capture**: finite addresses, first‑come‑first‑served naming, and centralized registries produce chokepoints and rent‑seeking.
- **Perimeterized connectivity**: NAT/CGNAT, firewalls, and browser/runtime policies obstruct inbound paths; teams reach for tunnels, static IPs, or custodial relays.
- **Platform custody & AI amplification**: intermediaries accumulate data/control; opaque training pipelines magnify asymmetry.
- **Developer friction**: every project repeats the same network plumbing.

## 2) Principles (non‑negotiables)
1. **Permissionless participation** — anyone can run nodes and publish services.
2. **Identity‑routed** — **pubkey is the address**; optional name overlays.
3. **Network‑provided connectivity & routing** — SDKs are interfaces, not traversal engines.
4. **End‑to‑end by default** — session key agreement, rotation, revocation; least‑privilege ACLs/tokens.
5. **Transparency** — verifiable metering/settlement on public chains; public integrity logs.
6. **Minimality** — a substrate, not a platform; opinionated about connectivity, neutral about apps and tokens.

## 3) Architecture Overview
### 3.1 Identity & Addressing
- Self‑generated keypairs (ed25519/Curve25519 or equivalent). URIs `pubkey://<hex|bech32>`.
- Optional mapping from wallets/ENS or organizational namespaces.
- Authorization primitives: signed capabilities/one‑time tokens; ACLs at service endpoints.

### 3.2 Discovery Directory (DHT)
- Kademlia‑like overlay; key = pubkey (or service hash), value = reachability record(s).
- **Records**: endpoint candidates (IP:port/host, relay hints), freshness, validity window, and publisher signature.
- **Integrity**: multi‑source consistency checks, anti‑poisoning filters, eclipse‑resistance via diversified peers and provider records.
- **Privacy**: avoid storing plaintext application metadata; rotate identifiers where possible.

### 3.3 Connectivity Layer
- **Traversal orchestration (ICE)**: candidate gathering (host/reflexive/relayed), nomination, and keepalives.
- **Capacity** provided by independent node operators: **STUN/TURN/relay** roles are permissionless to join.
- **Transports**: **WebRTC DataChannel**, **QUIC**, **HTTP/3 MASQUE**, **WebSocket** — negotiated per pair; selection guided by policy (latency/availability/cost).
- **Observability**: success rate/latency/bandwidth, exported as privacy‑minimal telemetry.

### 3.4 SDKs
- Languages: TS/JS, Go, Rust; (roadmap: Swift/Kotlin).
- Canonical APIs: `connect(pubkey, opts) → connection`; `publish(service, policy)`; streams/messages/files; auth tokens; retries.
- Guarantees: the **network** provides connectivity & routing; the SDK offers a unified developer surface.

## 4) Security Model
- **E2E encryption**: X25519 + AEAD; PFS; session rotation; secure renegotiation.
- **Access control**: signed capabilities, allow/deny lists, rate‑limits; optional mTLS between nodes.
- **Directory hardening**: signed records, quorum fetching, poisoning/evasion detection.
- **Metadata minimization**: separate usage metering from path details; aggregate counters by time buckets.

## 5) Economics & Settlement (minimal, token‑agnostic)
- **Unit**: **Usage Credits (UC)** (~$1 soft peg). Direct peer traffic is free; consumption primarily covers relayed bytes and premium features (pinning, QoS, storage add‑ons).
- **Split**: **70%** to node operators; **20%** to protocol treasury (ops, grants, bounties); **10%** to ecosystem incentives.
- **Metering**: usage proofs aggregated and **settled on‑chain**; public integrity logs enable external auditing.
- **Operator incentives**: light staking + behavioral reputation can influence routing and payouts; slashing for egregious abuse is possible but conservative.

## 6) Governance
- Governance focuses on protocol upgrades, treasury allocations, and integrity‑log policies. No single company can seize control; dispute and appeal processes are transparent; deny‑lists are shared but forkable.

## 7) Interoperability & Compatibility
- Works alongside the public internet and existing CDNs/VPNs; does not replace ISPs.
- Can bridge to name systems (ENS/DNS‑overlays) and identity wallets.
- Browser support via WebRTC; native via QUIC/HTTP3 stacks.

## 8) Compliance & Abuse Mitigation
- E2E encryption with least‑exposure defaults; rate‑limits and anomaly detection at relays; opt‑in shared deny‑lists; clear appeal processes.
- No centralized data custody; operators handle transport, not payload content.

## 9) Implementation Status & Roadmap
- **v0** POC: DHT + basic relay + TS SDK.
- **v1** Testnet: on‑chain metering dashboards; Go/Rust SDKs; multi‑region bootstrap.
- **v2** Beta: Swift/Kotlin SDKs; QoS/SLA tiers; ecosystem pilots (social, agents, IoT).
- **v3** GA: scale‑out; compliance whitepaper/pentest; interop bridges.

## 10) Risks & Mitigations
- **Re‑centralization pressure** → open governance, forkability, portable identities, multi‑operator markets.
- **Abuse** → rate‑limits, tokens/ACLs, privacy‑respecting telemetry, operator tooling.
- **Regulatory** → transport‑only stance; no custody of user content or keys; transparency logs.

## 11) Conclusion
Decent Network aims to restore symmetry to the internet: **address by identity, connect across boundaries, and coordinate in the open**. By keeping the base layer minimal and neutral, we give builders the freedom to invent next‑gen social, agent ecosystems, and resilient edge applications on a foundation that no one controls.

## 12) Glossary (abridged)
- **DHT**: Distributed Hash Table for discovery/announce/fetch.
- **ICE**: Interactive Connectivity Establishment for NAT traversal.
- **STUN/TURN/Relay**: roles that provide connectivity hints and relayed transport.
- **UC**: Usage Credits for usage‑based settlement.
