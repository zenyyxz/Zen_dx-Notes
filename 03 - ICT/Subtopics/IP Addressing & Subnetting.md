---
title: IPv4 Addressing & Subnetting Guide
subject: AL ICT
subtopic: Networking
tags:
  - AL-ICT
  - Subtopic
  - Subnetting
  - IPv4
  - CIDR
---
# :LiGlobe2: Subtopic: IPv4 Addressing & Subnetting Guide

> [!ABSTRACT] Core Focus
> A complete beginner-to-advanced guide on how IP addresses work, the difference between Network and Host IDs, IP Classes, Private vs. Public IPs, and step-by-step subnetting (CIDR, FLSM, VLSM).

---

## 1. What is an IPv4 Address?

Think of a network like a city. To send a letter to a specific house, you need an address. In networking, every device needs an **IP (Internet Protocol) address** to communicate.

An IPv4 address is a **32-bit** binary number. For humans to read it easily, we break it into four 8-bit groups (called octets) and write it in **Dotted Decimal Notation**.

Example: `192.168.10.35` 
In binary: `11000000 . 10101000 . 00001010 . 00100011`

Every IP address is split into two logical parts:
1. **Network ID**: Identifies the specific network (like the Street Name).
2. **Host ID**: Identifies the specific device on that network (like the House Number).

How do we know which part is the Network and which is the Host? That is determined by the **Subnet Mask**.

---

## 2. Classful IP Addressing

In the early days of the internet, IP addresses were divided into strict "Classes". The class is determined by looking at the **very first bits** of the first octet.

| Class | First Bits | 1st Octet Range | Default Subnet Mask | Network / Host Structure | Max Hosts per Network | Use Case |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **A** | `0` | 0 - 127 | 255.0.0.0 | **N**.H.H.H | $2^{24} - 2$ ($\approx 16.7$ Million) | Massive networks |
| **B** | `10` | 128 - 191 | 255.255.0.0 | **N.N**.H.H | $2^{16} - 2$ (65,534) | Medium to large |
| **C** | `110` | 192 - 223 | 255.255.255.0 | **N.N.N**.H | $2^8 - 2$ (254) | Small networks (Homes/Offices) |
| **D** | `1110` | 224 - 239 | N/A | N/A | N/A | Multicast (sending to a group) |
| **E** | `1111` | 240 - 255 | N/A | N/A | N/A | Experimental / Research |

> [!WARNING] The "- 2" Rule
> Why do we subtract 2 when calculating maximum hosts? Because in every network:
> 1. The **first IP** (all host bits are `0`) is the **Network Address** (identifies the network itself).
> 2. The **last IP** (all host bits are `1`) is the **Broadcast Address** (sends a message to everyone on that network).
> These two can **never** be assigned to a computer!

### Special & Private IP Addresses

To save IP addresses from running out, certain ranges were made **Private**. Private IPs can be used by anyone inside their local network (LAN) but are **not allowed on the public internet**. A router uses **NAT (Network Address Translation)** to translate your private IP into a single public IP to browse the web.

- **Class A Private**: `10.0.0.0` to `10.255.255.255`
- **Class B Private**: `172.16.0.0` to `172.31.255.255`
- **Class C Private**: `192.168.0.0` to `192.168.255.255`

**Loopback Address (`127.0.0.1`)**: Used by your computer to send a message to itself for testing purposes.

---

## 3. Subnetting & CIDR (Classless Inter-Domain Routing)

Strict classes wasted millions of IP addresses. If a company needed 300 IPs, a Class C (254) was too small, so they had to buy a Class B (65,534) and waste over 65,000 IPs!

To fix this, **Subnetting** was introduced. Subnetting allows you to borrow bits from the Host portion to create smaller "sub-networks". 

Instead of default masks, we use **CIDR notation**, written as a slash followed by the number of Network bits.
Example: `192.168.1.0 /26` means the first 26 bits are Network bits, leaving $32 - 26 = 6$ bits for Hosts.

### Subnetting Formulas
For a given prefix `/N`:
1. **Host Bits ($h$)** = $32 - N$
2. **Total Addresses per Subnet** = $2^h$
3. **Usable Hosts per Subnet** = $2^h - 2$
4. **Block Size (Magic Number)** = $2^h$ (or $256 - \text{last non-zero octet of mask}$)

---

## 4. Step-by-Step Subnetting Worked Example

Let's do a classic exam problem.

> [!EXAMPLE] Problem
> You are given the IP `192.168.1.130/26`. Find:
> 1. The Subnet Mask
> 2. The Network ID of the subnet this IP belongs to
> 3. The Broadcast ID
> 4. The Usable Host Range

### Step 1: Find the Subnet Mask
The CIDR is `/26`. This means 26 ones, followed by zeros:
`11111111 . 11111111 . 11111111 . 11000000`
Convert to decimal: `255.255.255.192`.

### Step 2: Find the Block Size (Subnet increments)
Host bits $h = 32 - 26 = 6$.
Block size = $2^6 = 64$. (Alternatively: $256 - 192 = 64$).
This means our subnets count up by 64 in the 4th octet!
- Subnet 0: `192.168.1.0`
- Subnet 1: `192.168.1.64`
- Subnet 2: `192.168.1.128`
- Subnet 3: `192.168.1.192`

### Step 3: Locate the IP
Our IP is `192.168.1.130`. Looking at our list, 130 falls between 128 and 191.
Therefore, it belongs to Subnet 2.
- **Network ID**: `192.168.1.128`

### Step 4: Find the Broadcast ID
The Broadcast ID is always **one number less** than the *next* Network ID.
The next network is `192.168.1.192`. 
- **Broadcast ID**: `192.168.1.191`

### Step 5: Find the Usable Host Range
The usable hosts sit right between the Network ID and the Broadcast ID.
- **First Usable**: Network ID + 1 $\rightarrow$ `192.168.1.129`
- **Last Usable**: Broadcast ID - 1 $\rightarrow$ `192.168.1.190`
- **Total Usable Hosts**: $2^6 - 2 = 62$ hosts.

---

## 5. FLSM vs VLSM

- **FLSM (Fixed Length Subnet Mask)**: You divide a network into subnets that are all the **exact same size**. (E.g., cutting a pizza into 8 equal slices). If one department needs 50 IPs and another needs 2, FLSM gives them both 64, wasting IPs.
- **VLSM (Variable Length Subnet Mask)**: You divide a network into subnets of **different sizes** based on actual need. (E.g., giving the big department a `/26` with 62 hosts, and a router link a `/30` with just 2 hosts). This maximizes IP efficiency.

---

## 6. A Note on IPv6

Even with subnetting and NAT, we ran out of IPv4 addresses (there are only $\approx 4.3$ billion). 

**IPv6** was created to solve this. 
- It uses **128 bits** (instead of 32).
- Written in **Hexadecimal** (not decimal).
- Separated by **colons** (not dots).
- Example: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`
- It provides enough addresses for every atom on Earth!