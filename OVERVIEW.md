# Study Guide — *An Introduction to Computer Networks* (Peter L. Dordal)

Source: <https://intronetworks.cs.luc.edu/> — **Second Edition, desktop edition 2.0.11**
(free/open textbook; CC BY-NC-ND).

This guide lists, chapter by chapter, the topics the book covers and marks which
of those topics the end-of-chapter **Exercises** actually test. A topic is marked
**★ exercised** if one or more exercises address it, with example exercise numbers.
Topics with no marker have prose/diagrams but no exercise questions of their own.

Legend

- **★** = covered by exercise questions (example numbers in parentheses)
- **(♢)** = that exercise has a solution/hint in ch. 34 (Selected Solutions)
- Solutions/hints exist for chapters 1–23 and 30 (34.1–34.18).

---

## Coverage at a glance

| Ch | Title | Exercises? | Heavily exercised topics |
|----|-------|-----------|--------------------------|
| 1 | An Overview of Networks | Yes | Forwarding tables, routing loops, weighted (shortest-cost) paths, IP subnet tables |
| 2 | Ethernet Basics | Yes | Contention/exponential backoff, learning-switch algorithm, flooding, VLAN color |
| 3 | Advanced Ethernet | Yes | Spanning Tree, VLANs, OpenFlow/SDN |
| 4 | Wireless LANs | Yes | Wi-Fi CSMA/CA & hidden node, contention overhead, WiMAX/LTE ranging, radio model, Wi-Fi security |
| 5 | Other LANs | Yes | VPNs, Token Ring/Bus, virtual circuits, ATM/AAL-5 |

## 1. An Overview of Networks
Chapter overview of the whole field; establishes vocabulary reused everywhere.

- **1.1 Layers** — layering, protocol stacks.
- **1.2 Data rate, throughput, bandwidth** — units and definitions.
- **1.3 Packets** — why we packetize.
- **★ 1.4 Datagram forwarding** (ex. 1.0, 5.0) — build forwarding tables for switches; neighbor-form `next_hop`; default entries.
- **★ 1.5 Topology** (ex. 2.0, 10.0, 11.0) — switch topologies; choosing shortest/lowest-cost paths; link weights as cost.
- **★ 1.6 Routing loops** (ex. 7.0, 8.0) — when loops can form; why a single loop can't span a degree-1 node; all nodes in a loop must be distinct.
- **1.7 Congestion, 1.8 Packets again, 1.9 LANs and Ethernet** — conceptual intro only.
- **★ 1.10 IP — Internet Protocol** (ex. 12.0) — forwarding tables for routers connecting class-C /24 subnets, default `direct`.
- **1.11 DNS, 1.12 Transport, 1.13 Firewalls, 1.14 Utilities, 1.15 IETF/OSI, 1.16 Berkeley Unix, 1.17 Epilog** — survey only.

**Exercise focus:** the mechanics of forwarding tables, route selection, and routing loops.

## 2. Ethernet Basics
- **★ 2.1 10-Mbps Classic Ethernet** (ex. 1.0; see also 2.1.11 analysis) — CSMA/CD contention period and **exponential backoff**; slot time; collision detection; efficiency analysis.
- 2.2 100 Mbps (Fast) Ethernet, 2.3 Gigabit Ethernet — speed variants, no exercises.
- **★ 2.4 Ethernet Switches** (ex. 2.0–7.0, 10.0) — the **learning algorithm**, forwarding vs flooding, source-address learning, loops without STP.
- **★ VLAN color propagation** (ex. 9.0) — forwarding-table color tracking across switches.
- **★ ARP interaction with learning** (ex. 10.0) — broadcast then unicast reply (links to 10.2 ARP).
- 2.5 Epilog.

**Exercise focus:** simulate backoff; hand-trace learning-switch tables and which switches see which packets.

## 3. Advanced Ethernet
- **★ 3.1 Spanning Tree Algorithm and Redundancy** (ex. 1.0, 2.0 ♢) — root selection, pruning loops, surviving-links network, resulting paths.
- **★ 3.2 Virtual LAN (VLAN)** (ex. 3.0) — propagating destination-color information; re-provisioning ports.
- 3.3 TRILL and SPB — alternatives to STP, no dedicated exercise.
- **★ 3.4 Software-Defined Networking** (ex. 2.0, 5.0 ♢, 6.0, 7.0, 8.0) — **OpenFlow** switches, controller reports, installing forwarding entries, multi-table flows (learning switches in OpenFlow).
- 3.5 Epilog.

**Exercise focus:** STP link pruning; OpenFlow controller logic; VLAN information propagation. (Ex. 4.0 links Ethernet to distance-vector routing.)

## 4. Wireless LANs
- **★ 4.1 Adventures in Radioland** (ex. 6.0) — signal power, inverse-square vs **two-ray ground model** (1/r⁴), reflection/phase.
- **★ 4.2 Wi-Fi** (ex. 1.0–3.0, 7.0) — CSMA/CA, ACK/SIFS timing, **hidden-node problem**, contention interval and efficiency loss, never-reorder.
  - **★ 4.2.5 Wi-Fi Security** (ex. 7.0) — four-way handshake and a replay attack.
- **★ 4.3 WiMAX and LTE** (ex. 4.0, 5.0) — subscriber mobility, ranging, guard intervals, propagation-delay correction.
- 4.4 Fixed Wireless, 4.5 Epilog — no exercises.

**Exercise focus:** hidden-node collisions, contention overhead arithmetic, radio propagation math, WiMAX ranging, WPA handshake.

## 5. Other LANs
- **★ 5.1 Virtual Private Networks** (ex. 1.0, 2.0) — VPN routing tables, encapsulation, misconfiguration, VPN-through-NAT.
- 5.2 Carrier Ethernet — no exercise.
- **★ 5.3 Token Ring** (ex. 3.0 ♢) — token passing; Token Bus; designing a token-ordering protocol.
- **★ 5.4 Virtual Circuits** (ex. 5.0–9.0 ♢) — VCI switching tables, tracing connections, routing VCs, revisiting switches on a path.
- **★ 5.5 ATM** (ex. 4.0) — AAL-5 cell loss and **XOR recovery cell** trade-off.
- 5.6 Epilog.

**Exercise focus:** VCI table construction (many exercises), VPN routing, token passing.
