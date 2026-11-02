# Lab 09 Quiz — Studying with LLM

**CS 2010 Fall 2026** · Textbook: *An Introduction to Computer Networks* (intronetworks.cs.luc.edu), chapters 1–5

- **Time limit:** 10 minutes (12 minutes recommended)
- **Allowed materials:** your one-page written cheat sheet
- **No LLM assistance** — this quiz is the LLMs-down part of the lab
- **Point values:** 10 points per question, 50 points total

All questions are exercises from the textbook. Show your work on the calculation questions; partial credit is given for correct setup.

---

## Question 1 (10 pts) — Textbook Ch. 1, Exercise 1.0

Give forwarding tables for each of the switches S1–S4 in the following network with destinations A, B, C, D. For the next_hop column, give the neighbor on the appropriate link rather than the interface number.

```
A B C
│ │ │
S1────────S2────────S3
 │
 │
 S4───D
```

**S1:**

| destination | next_hop |
|-------------|----------|
| a            |direct          |
| b            |direct          |
| c            |s3          |
| d            |s4          |

**S2:**

| destination | next_hop |
|-------------|----------|
|a             |s1          |
|b             | s1         |
|c             | s3         |
|d             | s1         |

**S3:**

| destination | next_hop |
|-------------|----------|
|a             |s1          |
|b             |s2         |
|c             |direct          |
|d             |s2          |

**S4:**

| destination | next_hop |
|-------------|----------|
|a             |s1          |
|b             |s1          |
|c             |s1          |
|d             |direct          |

---

## Question 2 (10 pts) — Textbook Ch. 2, Exercise 2.0

Suppose we have Ethernet switches S1 through S3 arranged as below; each switch uses the learning algorithm of Chapter 2. All forwarding tables are initially empty.

```
S1────────S2────────S3───D
│ │ │
A B C
```

For each part, list which switches see the packet.

**(a)** If A sends to B, which switches see this packet?
s1,s2,s3
**(b)** If B then replies to A, which switches see this packet?
s1,s2
**(c)** If C then sends to B, which switches see this packet?
s2,s1
**(d)** If C then sends to D, which switches see this packet?
s1
---

## Question 3 (10 pts) — Textbook Ch. 3, Exercise 1.0

The following network is like that of §3.1.1 Spanning Tree Example 1: Switches Only, except that the switches are numbered differently. Again, the ID of switch S_n is n, so S1 will be the root. Which links end up "pruned" by the spanning-tree algorithm, and why?

```
S1──────S4──────S6
│ │ │ │ │ │
│ │ │ │ │ │
│ │ │ │ │ │
S3──────S5──────S2
```

**Pruned links:**
s4,s5
**Why:**
because there in the center
---

## Question 4 (10 pts) — Textbook Ch. 4, Exercise 3.0

Suppose the average contention interval in a Wi-Fi network (802.11g) is 64 SlotTimes. The average packet size is 1 kB, and the data rate is 54 Mbps. At that data rate, it takes about (8×1024)/54 = 151 µsec to transmit a packet.

**(a)** How long is the average contention interval, in µsec?
c ≈ 300 m/µs
**(b)** What fraction of the total potential data rate is lost to contention?
6.6 µs
Show your work.

Subscriber moves ≤ 33 m/s; ranging refreshes once per minute; c ≈ 300 m/µs.

    Distance change in 60 s = 33 × 60 = 1980 m
    Propagation delay change = 1980 / 300 = 6.6 µs
    Since the base station doesn't know whether the subscriber approaches or recedes, it must tolerate ±6.6 µs → guard ≈ 13.2 µs.


---

## Question 5 (10 pts) — Textbook Ch. 5, Exercise 3.0(a)

Token Bus was a proprietary Ethernet-based network. It worked like Token Ring in that a small token packet was sent from one station to the next in agreed-upon order, and a station could transmit only when it had just received the token.

If the data rate is 10 Mbps and the token is 64 bytes long (the 10-Mbps Ethernet minimum packet size), what is the average wait to receive the token on an idle network with 40 stations? (The average number of stations the token must pass through is 40/2 = 20.) Ignore the propagation delay and the gap Ethernet requires between packets.

Show your work.

N = 20 data cells.

    XOR scheme: always 21 cells (20 data + 1 parity).
    Plain + retransmit: 20 cells normally, but if any of the 20 is lost (probability ≈ 20p), resend all 20.
        Expected cells ≈ 20 + (20p)(20) = 20 + 400p.

Break-even: 21 = 20 + 400p → p = 1/400 = 0.25%.

So the XOR scheme wins when cell loss is below ~0.25%, and loses (extra overhead) above it. (It also ignores the parity cell's own loss and latency cost.)

---

## Question 6 (10 pts) — Textbook Ch. 1, Exercise 12.0

Suppose we have the following three Class C IP networks, joined by routers R1–R4. There is no connection to the outside Internet. Give the forwarding table for each router. For networks directly connected to a router (eg 200.0.1/24 and R1), include the network in the table but list the next hop as direct or local.

```
R1── 200.0.1/24
│
│
│
R4──────────R2── 200.0.2/24
│
│
│
R3── 200.0.3/24
```

**R1:**

| destination | next_hop |
|-------------|----------|
|200.0.1/24    direct         |          |
|r4             |direct          |
|             |          |

**R2:**

| destination | next_hop |
|-------------|----------|
|             |          |
|             |          |
|             |          |

**R3:**

| destination | next_hop |
|-------------|----------|
|             |          |
|             |          |
|             |          |

**R4:**

| destination | next_hop |
|-------------|----------|
|             |          |
|             |          |
|             |          |
