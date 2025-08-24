# An open, secure and fair network

**Pubkey connects everything. Peer‑to‑peer access without IPs, domains, or platforms.**

---

## What it is
**Decent Network** is a **permissionless public communication substrate**. It lets people and devices address each other by **public keys**, removing dependence on IPs/domains and third‑party platforms. No company or individual can control it; anyone can help operate it and benefit from it. **Built and governed on existing crypto infrastructure via public blockchains** — with transparent metering, payouts, and grants — **not corporate ledgers**.

---

## Background & Problem (Why this matters)
- **Visibility asymmetry on the web**: publishers are visible; visitors are effectively invisible. This makes two‑way interaction and portable relationships hard—and raises the cost of building trust.
- **Platform power & information asymmetry (amplified by AI)**: centralized intermediaries gate naming, addressing, access, and data. Opaque data extraction and model training further tilt the field.
- **IP & DNS scarcity and capture**: IP space is finite; DNS is first‑come‑first‑served. High‑value names are scarce; registries/authorities are concentrated and become single points of control.
- **Security & fragility of centralized registries**: a few institutions hold critical databases (IP allocation, domain roots). They’re attractive targets and operational chokepoints.
- **Bidirectional access is cumbersome**: NAT/CGNAT, enterprise firewalls, and platform limits make inbound reachability awkward; teams resort to tunnels, static IPs, and manual DNS.

**We need a change**: a base layer where **peer‑to‑peer is default**, addressing is by **pubkeys**, and participation is **permissionless**. **Decent Network** focuses on that minimal, decentralized communication substrate—so safer, friendlier, and more efficient apps (next‑gen social, AI agents, IoT/edge) can be built on top.

---

## Why it matters (Who & Why)
- **Next‑gen social**: build social apps that don’t sit behind a platform’s gate. Identity = pubkey; relationships are portable; creators and communities own their graph.
- **AI agents**: agents can find, call, and collaborate with other agents and devices by pubkey—without centralized relays or NAT gymnastics.
- **IoT & edge fleets**: ship devices that are addressable from day one; vendor‑neutral remote ops and telemetry.
- **Builders & self‑hosters**: publish services from anywhere without buying static IPs or managing DNS/tunnels.

---

## What makes it different
- **Permissionless & neutral**: a public good, like Bitcoin/Ethereum—but for communication.
- **Peer‑to‑peer by design**: identity‑routed connections across networks and organizations, without platform custody.
- **Open economics**: usage is metered on‑chain; **node operators** earn by contributing capacity; **treasury** funds public goods via grants/bounties.
- **Portable identity**: your pubkey is your address across apps; no lock‑in.
- **SDK‑first DX**: SDK is the developer interface to use the network; **connectivity and routing are provided by the network itself**.

---

## Core capabilities
- **Pubkey directory (DHT)**: signed identity→reachability records.
- **Connectivity across networks**: the decentralized node network supplies STUN/TURN/relay capacity and NAT traversal (ICE).
- **Transports**: WebRTC DataChannel / QUIC / HTTP/3 MASQUE / WebSocket.
- **Security**: E2E by default (session keys, ACLs, tokens); minimal metadata.
- **Observability & metering**: latency/success/bandwidth; public integrity logs.

---

## Developer quickstart (TS)
```ts
import { connect } from '@decent/sdk'

const peer = 'pubkey://0xABCD...'
const conn = await connect(peer)
conn.send('hello')
```

---

## Participation & settlement (brief)
- **Unit:** **Usage Credits (UC)** (~$1 soft peg), usage‑based.
- **Split:** **70%** node operators / **20%** protocol treasury (ops, grants, bounties) / **10%** ecosystem.
- **Run a node:** community members can operate discovery/relay capacity and earn **transparently on chain**.

---

## Use cases
- Social messaging/feeds/live rooms without platform custody.
- Agent‑to‑agent coordination; agent↔device calls; tool servers.
- IoT/edge onboarding at scale; remote ops & command routing.
- Self‑hosting: webhooks, demos, reverse callbacks—no DNS or static IPs.

---

## Call to action
- **Download test app:** https://linktr.ee/0xl
- **Start building:** SDK & docs
- **Run a node:** join the community network and contribute capacity

> Contact: wli@decent.network | GitHub: github.com/decentnetworks | X: @0xwli
