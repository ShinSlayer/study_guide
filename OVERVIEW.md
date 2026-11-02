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


# Chapters 1–5 Study Pack — *An Introduction to Computer Networks* (Dordal, 2e)

Companion to `intro-computer-networks-study-guide.md`.
Contains, for **chapters 1–5**:

1. **Flashcards** (Q/A, plus an import-ready TSV block)
2. **Sample problems** with answers
3. **Worked examples** (fully solved, step by step)
4. **Web pages with helpful animations** (link-checked)

Links were verified reachable on **2026-11-02**.

---

# 1. Flash cards

## Chapter 1 — An Overview of Networks

| # | Front | Back |
|---|-------|------|
| 1.1 | What does a forwarding-table entry map? | A destination address → a next hop (and, in "interface form", an outbound interface). |
| 1.2 | Routing vs. forwarding? | Routing *builds* the tables (control plane); forwarding *uses* them per packet (data plane). |
| 1.3 | What is a routing loop? | A cycle of routers in which each hop's next hop heads to the next, so packets circulate forever until a TTL/hop limit expires. |
| 1.4 | Why can't a datagram routing loop be a "free-floating linear" loop? | Because forwarding is fixed per destination, the switch sequence must repeat, and consecutive switches must be adjacent — so a loop is either back-and-forth between two nodes or an actual cycle in the topology. |
| 1.5 | What is a default route? | A catch-all table entry (e.g. `0.0.0.0/0`) used when no more-specific prefix matches. |
| 1.6 | Define bandwidth-delay product. | Bandwidth × round-trip time = the amount of data "in flight" needed to keep a path full. |
| 1.7 | A LAN vs. an internetwork? | A LAN connects hosts in one local scope; an internetwork connects multiple networks together via routers. |
| 1.8 | Layering: name the classic five layers. | Physical → Link → Network (IP) → Transport → Application. |
| 1.9 | What is congestion? | Too much traffic for a shared bottleneck, producing queue growth, delay, and packet loss. |
| 1.10 | What does DNS do? | Resolves human names to IP addresses. |

## Chapter 2 — Ethernet Basics

| # | Front | Back |
|---|-------|------|
| 2.1 | CSMA/CD stands for… | Carrier Sense Multiple Access with Collision Detection. |
| 2.2 | Why does 10 Mbps Ethernet impose a **64-byte minimum frame**? | So a sender is still transmitting when a far-end collision returns — making collision detection possible. 64 bytes = 512 bit times = the slot time. |
| 2.3 | What is the Ethernet slot time (10 Mbps)? | 512 bit times = **51.2 µs**. |
| 2.4 | Binary exponential backoff after the *k*-th collision? | Pick a random integer in `{0 … 2^k − 1}` and wait that many slot times. |
| 2.5 | Backoff cap / give-up rule? | Cap the exponent at 10 (max wait 1023 slots); give up after **16** collisions. |
| 2.6 | What does a switch do with a frame to an **unknown** destination? | Floods it out all ports except the arrival port. |
| 2.7 | How does a switch learn addresses? | It records the **source MAC** + arrival port of every frame into its forwarding table. |
| 2.8 | What is address aging? | Removing stale table entries after an idle timeout so moved hosts get relearned. |
| 2.9 | Ethernet broadcast address? | `FF:FF:FF:FF:FF:FF`. |
| 2.10 | Why are loops fatal to a switched Ethernet? | No TTL: broadcasts/multicasts and unknown-unicast frames circulate forever → **broadcast storm** and duplicated frames. |
| 2.11 | Half- vs. full-duplex Ethernet? | Half-duplex shares a medium and uses CSMA/CD; full-duplex is point-to-point through a switch, no collisions. |

## Chapter 3 — Advanced Ethernet

| # | Front | Back |
|---|-------|------|
| 3.1 | What is the Spanning Tree Algorithm for? | Automatically prune a redundant switched topology down to a loop-free tree (the idea behind IEEE 802.1D STP). |
| 3.2 | How is the root bridge chosen? | The switch with the **lowest bridge ID** (in the book, lowest switch number; in real STP, priority then MAC). |
| 3.3 | Root port vs. designated port? | A **root port** is a non-root switch's least-cost port toward the root; a **designated port** is the port on a segment belonging to the segment's best bridge toward the root. |
| 3.4 | What happens to the losing ports on a redundant link? | They are blocked (no forwarding), leaving a single active path per segment. |
| 3.5 | What is a VLAN? | A logically separated LAN independent of physical wiring; hosts in one VLAN don't see another VLAN's traffic without routing. |
| 3.6 | Access port vs. trunk port? | Access port carries one VLAN to an end host; trunk carries multiple tagged VLANs between switches. |
| 3.7 | What is the 802.1Q tag? | A 4-byte tag (with a 12-bit VLAN ID) inserted in the Ethernet header on trunk links. |
| 3.8 | What do TRILL and SPB do differently from STP? | They use link-state routing + encapsulation so *all* links can be used (multipath), instead of blocking redundant links. |
| 3.9 | What is Software-Defined Networking (SDN)? | Separating the control plane (a central controller) from the data plane (simple switches). |
| 3.10 | What is an OpenFlow rule? | A **match → action** flow-table entry (e.g. match destination MAC, forward out port 2 / flood / send to controller). |

## Chapter 4 — Wireless LANs

| # | Front | Back |
|---|-------|------|
| 4.1 | Why CSMA/**CA** instead of CSMA/CD on wireless? | A station generally cannot hear collisions at the receiver, so it *avoids* them via deferral/timing rather than detecting them. |
| 4.2 | Role of DIFS vs. SIFS? | DIFS is the long wait before contending for the medium; SIFS is the short gap reserved for high-priority replies like ACKs (so they win). |
| 4.3 | What is the hidden-node problem? | Two stations can each reach the access point but not each other, so their transmissions collide at the AP despite carrier sensing. |
| 4.4 | How does RTS/CTS help? | The AP's CTS reserves the medium and is heard by the hidden station, silencing it for the duration. |
| 4.5 | Why may an ACK be sent *without* listening first? | It follows a SIFS and the receiver is the intended station; stations that heard the data are still deferring, and hidden nodes that are transmitting are typically too far to collide with the ACK at the receiver. |
| 4.6 | What protects Wi-Fi with WPA2? | The four-way handshake, which proves both sides hold the key and binds fresh nonces, defeating simple replay. |
| 4.7 | How do WiMAX/LTE differ from Wi-Fi access? | A base station **schedules** subscriber transmissions (no contention); subscribers are not expected to hear one another. |
| 4.8 | Why guard intervals in mobile wireless? | Moving subscribers change propagation delay, so arrivals shift early/late; a guard time absorbs the difference. |
| 4.9 | What does the two-ray ground model predict? | Signal power decays as **1/r⁴** (direct + ground-reflected paths cancel increasingly with distance), not 1/r². |

## Chapter 5 — Other LANs

| # | Front | Back |
|---|-------|------|
| 5.1 | What is a VPN? | Private connectivity over a public network, usually by **tunneling/encapsulation**. |
| 5.2 | What is tunneling? | Wrapping an inner packet inside an outer packet so the network delivers it to a tunnel endpoint. |
| 5.3 | What is "split tunneling"? | Sending only some traffic through the VPN while the rest goes directly. |
| 5.4 | How does Token Ring avoid collisions? | A single **token** circulates; only the station holding it may transmit. |
| 5.5 | What is a virtual circuit? | A connection-oriented path set up in advance; switches hold per-connection state and translate a **VCI** at each link. |
| 5.6 | Virtual circuit vs. datagram switching? | VC: setup + stateful switches + fixed path; datagram: no setup, each packet routed independently. |
| 5.7 | What is ATM's cell size? | **53 bytes** total = 5-byte header + 48-byte payload. |
| 5.8 | Why fixed-size cells? | Predictable, regular transmission/queuing (helps delay/jitter and simplifies fast hardware). |
| 5.9 | What is AAL-5's XOR "parity cell"? | With N data cells, one trailing cell carries their XOR, letting the receiver recover any one lost cell at the cost of ~1/N extra overhead. |
| 5.10 | What is Carrier Ethernet? | Extending Ethernet service across a provider network using EVCs (Ethernet Virtual Connections). |

### Import-ready TSV (Anki / Quizlet)

Save the block below as `ch1-5-flashcards.tsv` (tab-separated; `#` lines are comments).

```
# An Introduction to Computer Networks, ch.1-5 flashcards
# front<TAB>back
Forwarding-table entry maps...	Destination address -> next hop (and outbound interface in interface form)
Routing vs forwarding	Routing builds tables (control plane); forwarding uses them per packet (data plane)
Routing loop	A cycle where each next hop leads to the next, so packets circulate until TTL expires
A datagram routing loop must be...	Either a two-node back-and-forth or an actual cycle in the topology
Default route	A catch-all entry used when no more-specific prefix matches
Bandwidth-delay product	Bandwidth x round-trip time = data in flight to keep a path full
Classic five layers	Physical, Link, Network (IP), Transport, Application
Congestion	Too much traffic for a shared bottleneck -> queues, delay, loss
CSMA/CD	Carrier Sense Multiple Access with Collision Detection
Ethernet minimum frame size	64 bytes (=512 bit times) so collisions can be detected before transmission ends
10 Mbps Ethernet slot time	512 bit times = 51.2 microseconds
Binary exponential backoff after k collisions	Random wait in {0 .. 2^k - 1} slot times
Backoff give-up rule	Cap exponent at 10; abort after 16 collisions
Switch with unknown destination	Flood out all ports except the arrival port
Switch learning	Record source MAC + arrival port in the forwarding table
Ethernet broadcast address	FF:FF:FF:FF:FF:FF
Why loops are fatal to Ethernet	No TTL -> broadcast storms and duplicate frames
Spanning Tree Algorithm purpose	Prune redundant switched topology to a loop-free tree
Root bridge choice	Lowest bridge ID (book: lowest switch number)
Root port vs designated port	Root port = non-root switch's least-cost port to root; designated = best port on a segment toward root
VLAN	A logical LAN independent of physical wiring
Access vs trunk port	Access = one VLAN to a host; trunk = multiple tagged VLANs between switches
802.1Q tag	4-byte tag with a 12-bit VLAN ID, inserted on trunk links
TRILL / SPB vs STP	Use link-state routing + encapsulation to use all links (multipath) instead of blocking
SDN	Separating the control plane (central controller) from the data plane (simple switches)
OpenFlow rule	A match -> action flow-table entry
Why CSMA/CA on wireless	Cannot reliably detect collisions at the receiver, so avoid them
DIFS vs SIFS	DIFS = long contention wait; SIFS = short gap reserved for ACK/priority replies
Hidden-node problem	Two stations can reach the AP but not each other, so they collide at the AP
RTS/CTS	AP's CTS reserves the medium and silences hidden stations
WPA2 protection	Four-way handshake binds fresh nonces, defeating simple replay
WiMAX/LTE vs Wi-Fi	Base station schedules subscribers (no contention)
Guard intervals	Absorb early/late arrivals caused by subscriber mobility
Two-ray ground model	Received power decays as 1/r^4
VPN	Private connectivity over a public network, usually by tunneling
Tunneling	Encapsulating an inner packet inside an outer packet
Virtual circuit	Connection-oriented path with per-link VCI translation and switch state
ATM cell size	53 bytes = 5-byte header + 48-byte payload
AAL-5 parity cell	One XOR cell lets the receiver recover any single lost cell
Carrier Ethernet	Ethernet service across a provider network using EVCs
```

---

# 2. Sample problems (with answers)

## Chapter 1

**1.1** A switch has the table `A→port1, B→port1, C→port2, default→port3`. A frame arrives destined for D. Out which port(s) does it go, and why?
> **Answer:** Out port 3 only (the default). D has no specific entry, so the default route is used; the switch does not flood when a default exists.

**1.2** In the network below, give S1's forwarding table in neighbor form (destinations A–D).
```
A──S1──S2──B
   │
   S3──C
D is attached to S3
```
> **Answer:** `A→direct, B→S2, C→S3, D→S3`. (C and D share next hop S3.)

**1.3** True/False: a routing loop can pass through the same switch twice but never repeat an edge.
> **Answer:** **False as stated / True in the useful sense.** A single forwarding loop is either a 2-node back-and-forth (one edge used twice) or a genuine topology cycle. It can revisit a switch in the cycle sense.

**1.4** Explain why "hops" is a weaker metric than "total link cost."
> **Answer:** Hop count treats every link as equal; cost lets you prefer, e.g., a 2-hop fiber path over a 1-hop congested/slow link.

## Chapter 2

**2.1** Five stations collide at T = 0. Station A draws k = 0, B draws k = 2, C draws k = 1, D draws k = 0, E draws k = 3 (slot = 1 unit). Who transmits first, and what happens?
> **Answer:** A and D transmit at T = 1 and **collide again**; C transmits at T = 2 (if the medium is idle then); B at T = 3; E at T = 4.

**2.2** In a 3-switch line `S1—S2—S3` with host A on S1, hosts B and C on S2, and host D on S3, all tables empty: A sends to D. Which switches see the frame?
> **Answer:** **All three (S1, S2, S3)** — D is unknown everywhere, so the frame is flooded along the line. Each switch also learns `A` on the port toward S1.

**2.3** After 2.2, D replies to A. Which switches flood, and why?
> **Answer:** None flood. S3 knows `A` via S2 (learned while flooding A's frame), so it forwards toward S2; S2 already knows `A` via S1; S1 knows A on its local port.

**2.4** Why does a learning switch need address aging?
> **Answer:** A host may move or a port may change. Without aging, stale entries would misdirect frames indefinitely.

## Chapter 3

**3.1** A 2-switch loop `S1—S2` (two parallel links) has S1 as root. What does STP produce?
> **Answer:** One of the two S1–S2 links is blocked at S2's end, leaving a single active link (a tree with no loop).

**3.2** In the 2×3 grid of the worked example, which two ports are blocked?
> **Answer:** S5's port toward S4, and S2's port toward S6 (see Worked Example 3.1).

**3.3** A frame from VLAN 10 host A enters switch S1's access port and must reach VLAN 10 host B on switch S2. Describe the headers.
> **Answer:** S1 adds an 802.1Q tag with VLAN ID 10, sends it over the trunk to S2; S2 reads the tag, forwards only to VLAN-10 access ports, and strips the tag before delivering to B.

**3.4** In OpenFlow terms, what is the difference between "flood" and "send to controller"?
> **Answer:** Flood is a data-plane action sending the frame out all eligible ports; "send to controller" punts it to the control plane (e.g. so a learning/SDN app can decide and install a rule).

## Chapter 4

**4.1** Average contention interval = 64 slots; 802.11g slot = 9 µs; average packet = 151 µs to transmit. What fraction of the medium's potential is lost to contention?
> **Answer:** Contention = 64 × 9 = 576 µs. Lost fraction = 576/(576+151) ≈ **79%**.

**4.2** Nodes A and C can each reach AP B but not each other. Describe what happens when both transmit at once, and how RTS/CTS fixes it.
> **Answer:** A and C both sense an idle medium and transmit; the signals collide **at B**, so B decodes neither. With RTS/CTS: A sends RTS to B; B's CTS (heard by C) reserves time; C defers.

**4.3** A subscriber moves at 33 m/s; ranging updates every 60 s; light speed ≈ 300 m/µs. How large must the guard interval be?
> **Answer:** Distance change = 33 × 60 = 1980 m → delay shift = 1980/300 = **6.6 µs** early or late; the guard must cover 2 × 6.6 = **13.2 µs**.

**4.4** In the two-ray model, why does power fall as 1/r⁴ rather than 1/r²?
> **Answer:** The ground reflection arrives 180° out of phase, cancelling part of the direct signal; the residual grows proportional to the path-length difference, which itself shrinks with distance, giving 1/r⁴.

## Chapter 5

**5.1** Give the VCI-table entries for the connection `A → S1 → S2 → B` if A→S1 uses VCI 1, S1→S2 uses VCI 7, and S2→B uses VCI 4.
> **Answer:**
> - S1: `(1, port A) → (7, port S2)`
> - S2: `(7, port S1) → (4, port B)`

**5.2** Why must S1's *out VCI* on the S1–S2 link equal S2's *in VCI* on that same link?
> **Answer:** The VCI is a label meaningful only on one link; the sender writes the label the receiver expects for that link.

**5.3** With N = 20 data cells and an AAL-5 XOR cell, at what cell loss rate does the XOR scheme cost about the same as retransmission (which resends all 20 cells on any loss)? Ignore the parity cell's own loss.
> **Answer:** Without XOR: expected cells = 20 + 20·(20p) = 20 + 400p. With XOR: always 21. Set 21 = 20 + 400p → p = **1/400 = 0.0025 (0.25%)**.

**5.4** Why can't a datagram network guarantee fixed delay the way a virtual-circuit (ATM) network can?
> **Answer:** Datagram packets may take different paths/queues and be reordered; VC traffic follows one reserved path with per-connection state, making delay more controllable.

---

# 3. Worked examples

## Worked Example 1.1 — Building forwarding tables by hand

Network (each line is one link):
```
A──S1──S2──S3──C
     │
     S4──D
B is attached to S1 as well
```
Destinations: A, B, C, D. Use neighbor-form next hops and keep paths shortest.

**Step 1 — list direct attachments.**
- A, B attach to S1 → S1 reaches them *direct*.
- C attaches to S3 → S3 reaches C *direct*.
- D attaches to S4 → S4 reaches D *direct*.

**Step 2 — fill each switch, choosing the shortest neighbor path.**

| Switch | A | B | C | D |
|--------|---|---|---|---|
| S1 | direct | direct | S2 | S4 |
| S2 | S1 | S1 | S3 | S1 |
| S3 | S2 | S2 | direct | S2 |
| S4 | S1 | S1 | S1 | direct |

**Step 3 — sanity check.** C is 3 hops from S1 (S1→S2→S3); every table routes it that way. D is 2 hops from S2 (S2→S1→S4). Good.

## Worked Example 1.2 — Choosing a least-cost path

Weights: `S1–S2 = 1`, `S2–S3 = 1`, `S1–S4 = 5`, `S4–S3 = 1`.

- Via S2: `S1→S2→S3` = 1 + 1 = **2**
- Via S4: `S1→S4→S3` = 5 + 1 = **6**

S1's entry for C is therefore `C → S2` (cost 2). This shows why cost beats hop count: the S4 path also has 2 hops but is 3× as expensive.

## Worked Example 2.1 — Exponential backoff timeline

Four stations collide at T = 0 (one slot = 1 unit). Round 1: each draws `k ∈ {0,1}`.

| Station | k | Retransmit at |
|---------|---|---------------|
| A | 0 | T = 1 |
| B | 1 | T = 2 |
| C | 1 | T = 2 |
| D | 0 | T = 1 |

A and D collide again at T = 1. Round 2 for A, D: draw `k ∈ {0,1,2,3}`.

| Station | k | Retransmit at |
|---------|---|---------------|
| A | 2 | T = 3 |
| D | 0 | T = 1 |

Meanwhile B and C transmit at T = 2 (C first if B and C also drew distinct slots; if they collide, each doubles again). Result: A waits longer after repeated collisions, spreading traffic out. Note that a good backoff **increase** is what prevents repeated lock-step collisions — exactly the "Sorcerer's Apprentice" risk seen later in sliding windows.

## Worked Example 2.2 — Learning-switch tables step by step

Topology: `A——S1——S2——S3——D`, with `B` also on S1 and `C` on S2. All tables start empty.

Packets, in order: **(1) A→B, (2) B→A, (3) C→B.**

**After (1) A→B:**
- S1 learns `A` on the A-port. B unknown → flood toward S2.
- S2 learns `A` on the S1-port. Flood toward S1 and S3.
- S3 learns `A` on the S2-port. Flood toward D.

| | A | B | C | D |
|---|---|---|---|---|
| S1 | port-A | — | — | — |
| S2 | port-S1 | — | — | — |
| S3 | port-S2 | — | — | — |

**After (2) B→A:**
- S1 learns `B` on the B-port; knows A → forwards directly to A (no flood).
- S2 never sees it; S3 never sees it.

**After (3) C→B:**
- S2 learns `C` on the C-port; knows B via S1 → forwards toward S1.
- S1 already knows B, forwards directly to B. S3 never sees it.

Final tables:

| | A | B | C | D |
|---|---|---|---|---|
| S1 | port-A | port-B | — | — |
| S2 | port-S1 | port-S1 | port-C | — |
| S3 | port-S2 | — | — | — |

## Worked Example 3.1 — Spanning Tree on a 2×3 grid

```
S1────S4────S6
│     │     │
S3────S5────S2
```
Switch IDs = their numbers, so **S1 is root**.

**Step 1 — shortest cost to root (all links cost 1).**

| Switch | Cost to S1 | Root port (tie → lower-ID neighbor) |
|--------|-----------|-------------------------------------|
| S1 | 0 | — (root) |
| S3 | 1 (via S1) | link to S1 |
| S4 | 1 (via S1) | link to S1 |
| S5 | 2 (via S3 or S4) | link to S3 (S3 < S4) |
| S6 | 2 (via S4) | link to S4 |
| S2 | 3 (via S5 or S6) | link to S5 (S5 < S6) |

**Step 2 — designated bridge per segment** (lowest cost; tie → lower ID):

| Segment | Best bridge (cost) | Designated |
|---------|--------------------|-----------|
| S1–S4 | S1 (0) | S1 |
| S4–S6 | S4 (1) | S4 |
| S1–S3 | S1 (0) | S1 |
| S3–S5 | S3 (1) | S3 |
| S5–S2 | S5 (2) < S2 (3) | S5 |
| S4–S5 | S4 (1) < S5 (2) | S4 |
| S6–S2 | S6 (2) < S2 (3) | S6 |

**Step 3 — block non-root, non-designated ports.**
- On segment S4–S5, S5's port is neither its root port (that's toward S3) nor designated → **S5 blocks the S4 link**.
- On segment S6–S2, S2's port is neither its root port (toward S5) nor designated → **S2 blocks the S6 link**.

**Result — surviving tree:** S1–S4, S1–S3, S4–S6, S3–S5, S5–S2. Path S2→S6 is now S2→S5→S3→S1→S4→S6.

## Worked Example 3.2 — VLAN tagging across a trunk

VLAN 10: host A on switch S1, host B on switch S2. Trunk link S1–S2.

1. A sends an untagged frame to S1's **access** port (configured for VLAN 10).
2. S1 inserts an **802.1Q tag** (VLAN ID = 10) and forwards on the **trunk** to S2.
3. S2 sees the tag, looks up VLAN 10's ports, and forwards only to VLAN-10 access ports.
4. S2 **strips** the tag before delivering to B.

Hosts in VLAN 20 on S1/S2 never see A's frame; reaching B from VLAN 20 would require routing.

## Worked Example 4.1 — Wi-Fi contention overhead

Given: average contention interval = 64 slots, 802.11g slot time = 9 µs, average packet transmission = 151 µs.

- Contention time = 64 × 9 µs = **576 µs**
- Useful time per cycle = 151 µs
- Efficiency = 151 / (576 + 151) = 151 / 727 ≈ **20.8%**
- **Fraction lost to contention ≈ 79%.**

This shows why minimizing the contention window (and the number of active contenders) matters so much at high data rates.

## Worked Example 4.2 — Hidden node, with and without RTS/CTS

Stations A, C; access point B. A hears B but not C; C hears B but not A.

**Without RTS/CTS:**
1. A senses idle → transmits to B.
2. C also senses idle (it can't hear A) → transmits to B.
3. At B the two signals overlap → **collision**; B decodes neither, sends no ACK.
4. A and C time out, double their contention windows, retry.

**With RTS/CTS:**
1. A sends a short RTS to B.
2. B replies with CTS (heard by *both* A and C, since C can hear B).
3. C now knows the medium is reserved and defers for the indicated duration.
4. A sends its data; B ACKs. Collision avoided — at the cost of RTS/CTS overhead.

## Worked Example 4.3 — Mobile guard interval (WiMAX)

Subscriber moves ≤ 33 m/s; ranging refreshes once per minute; c ≈ 300 m/µs.

- Distance change in 60 s = 33 × 60 = **1980 m**
- Propagation delay change = 1980 / 300 = **6.6 µs**
- Since the base station doesn't know whether the subscriber approaches or recedes, it must tolerate ±6.6 µs → guard ≈ **13.2 µs**.

## Worked Example 5.1 — Virtual-circuit switching tables

Topology (each host on a switch):
```
A───S1────────S2───B
    │          │
C───S3────────S4───D
```
Set up two connections: **A → S1 → S2 → D** and **C → S3 → S4 → B**. Assign VCIs per link.

**A → S1 → S2 → D** (use VCIs 1, 2, 3 by link):

| Switch | In (VCI, port) | Out (VCI, port) |
|--------|----------------|-----------------|
| S1 | (1, A) | (2, S2) |
| S2 | (2, S1) | (3, D) |

**C → S3 → S4 → B** (use VCIs 1, 2, 4):

| Switch | In (VCI, port) | Out (VCI, port) |
|--------|----------------|-----------------|
| S3 | (1, C) | (2, S4) |
| S4 | (2, S3) | (4, B) |

Check the link rule: S1's out-VCI 2 on S1–S2 = S2's in-VCI 2 on S1–S2. The same number on *different* links (e.g. VCI 1 on A–S1 vs. VCI 1 on C–S3) is fine — VCIs are local.

## Worked Example 5.2 — VPN routing puzzle

Host A has eth0 = 12.1.2.3 (normal Internet) and ppp0 = 10.0.0.44 (VPN to B = 200.0.0.7). Sending via ppp0 encapsulates the packet and forwards it (over the real Internet) to B.

**Case (a):** table = `200.0.0.7 → eth0`, `everything else → ppp0`.
- A's traffic to any host *other than B* goes via ppp0 → encapsulated → tunneled to B → B forwards it out.
- **Return traffic from the outside is the problem:** the remote host answers A's *public* address 12.1.2.3, which arrives on eth0. A sends replies to that remote host via ppp0 (because "everything else" → ppp0), so the return path is asymmetric and likely breaks the connection.
- An intruder M connecting to 12.1.2.3 gets replies that A routes via ppp0 (through the tunnel), so M may never receive them → the inbound connection fails.

**Case (b):** table = `everything → ppp0`.
- To reach B, A must encapsulate and send to B — but the packet to B *also* matches "everything else," so it too is encapsulated toward B. The underlay packet destined for B is thus itself wrapped, creating a **loop / black hole**: A never gets a plain packet out to B's real Internet address.

**Lesson:** the VPN's own endpoint must have a specific route out the underlay interface; everything else may then use the tunnel.

## Worked Example 5.3 — AAL-5 XOR cell trade-off

N = 20 data cells.

- **XOR scheme:** always 21 cells (20 data + 1 parity).
- **Plain + retransmit:** 20 cells normally, but if any of the 20 is lost (probability ≈ 20p), resend all 20.
  - Expected cells ≈ 20 + (20p)(20) = **20 + 400p**.

Break-even: `21 = 20 + 400p` → **p = 1/400 = 0.25%**.

So the XOR scheme wins when cell loss is below ~0.25%, and loses (extra overhead) above it. (It also ignores the parity cell's own loss and latency cost.)

---

# 4. Web pages with helpful animations & interactives

> All links below returned HTTP 200 on 2026-11-02. They are external; content may
> change or move over time.

## General (useful across all chapters)

- **Kurose & Ross — Interactive End-of-Chapter Problems** — <https://gaia.cs.umass.edu/kurose_ross/interactive/>
  Free, auto-generated interactive exercises that animate/parametrize networking
  concepts (many complement ch. 1–5). Excellent for drilling.
- **Packet Switching Simulator (OpenLabs)** — <https://www.openlabs.org.in/computer-science/networking/packet-switching>
  Watch packets hop node-by-node with queueing and path selection. Great for ch. 1 and ch. 5 (datagram vs. connection-oriented).
- **Routing-table simulator (SubnetCalculator.dev)** — <https://subnetcalculator.dev/routing-simulator/>
  Interactive forwarding tables / longest-prefix matching. Ch. 1 (and ch. 9/14 later).

## Chapter 1 — Overview / datagram forwarding

- **Longest-prefix matching, interactive** — <https://gaia.cs.umass.edu/kurose_ross/interactive/longestprefix.php/index.php>
  A packet arrives with a destination address; choose the correct outbound interface. Reinforces forwarding-table lookup.
- **INET IPv4 routing-table visualizer** — <https://inet.omnetpp.org/docs/showcases/visualizer/canvas/routingtable/doc/index.html>
  Animated simulation that draws routers' routing tables and packet paths. Good for seeing how tables drive forwarding.

## Chapter 2 — Ethernet / CSMA-CD / learning switches

- **Ethernet Switch Visualization (Galles-style)** — <https://cuuduongthancong.com/app/galles/visualization/EthernetSwitch.html>
  **Best single resource for ch. 2–3.** Watch two switches learn MAC addresses, flood
  unknown frames, age entries out, and produce a **broadcast storm** when STP is off.
- **CSMA/CD (Wikipedia, with diagrams)** — <https://en.wikipedia.org/wiki/Carrier-sense_multiple_access_with_collision_detection>
  Clear collision/interframe-gap sequence diagrams and the backoff discussion.
- **CSMA/CD course notes (Univ. of Kentucky)** — <http://protocols.netlab.uky.edu/~griff/classes/cs471/notes/ch8/notes/node11.html>
  Static but concise walk-through of carrier sense and collision detection.

## Chapter 3 — STP / VLANs / SDN

- **Interactive tour of the Spanning Tree Protocol** — <https://vincent.bernat.ch/en/blog/2026-spanning-tree>
  Runs the real STP algorithm live in the browser; step through root election and
  port blocking. Directly matches Worked Example 3.1.
- **Ethernet Switch Visualization** — <https://cuuduongthancong.com/app/galles/visualization/EthernetSwitch.html>
  Same tool as above: toggle **STP** and **VLANs** to see pruning and VLAN delivery.
- **Spanning Tree Algorithm lesson (NetworkAcademy.io)** — <https://www.networkacademy.io/ccna/spanning-tree/the-spanning-tree-algorithm>
  Step-by-step diagrams of the algorithm.
- **Introduction to Spanning Tree (NetworkLessons)** — <https://networklessons.com/spanning-tree/introduction-to-spanning-tree>
  Visual primer on loops, root bridges and blocked ports.

## Chapter 4 — Wireless / hidden node / CSMA-CA

- **The Hidden Node Problem — INET/OMNeT++ showcase** — <https://inet.omnetpp.org/docs/showcases/wireless/hiddennode/doc/index.html>
  A real 802.11 simulation demonstrating a hidden-node collision **and** how
  **RTS/CTS** fixes it. Directly matches Worked Example 4.2.
- **Hidden node problem (Wikipedia, with animation)** — <https://en.wikipedia.org/wiki/Hidden_node_problem>
  Includes the classic A–B–C diagram and the exposed-node contrast.
- **WiFi's Hidden Node Problem (Computerphile video)** — <https://www.youtube.com/watch?v=UgQM0rVDIQE>
  Short animated explanation of why coverage overlap causes the problem.

## Chapter 5 — Other LANs / virtual circuits / token ring

- **Token Ring and Token Bus Working Animation** — <https://instrumentationtools.com/token-ring-token-bus-working-animation/>
  Animated token circulation and frame passing for Token Ring/Bus.
- **How Token Ring Works (with animated GIF)** — <https://www.datacottage.com/nch/troperation.htm>
  Animated ring operation with a clear frame-flow description.
- **Packet Switching Simulator (OpenLabs)** — <https://www.openlabs.org.in/computer-science/networking/packet-switching>
  Compare connection-oriented path behavior against independent packet routing (datagram vs. virtual circuit).

---

## Suggested study loop (per chapter)

1. Read the chapter using `intro-computer-networks-study-guide.md`.
2. Drill the **flashcards** above (TSV import for spaced repetition).
3. Do the **sample problems**, then the book's own ★ exercises.
4. Walk the **worked examples**, re-deriving them on paper.
5. Open the **animation link(s)** for that chapter and predict the outcome before it runs.
