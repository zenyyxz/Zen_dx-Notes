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
> Binary structure of IPv4 addresses, subnet masks, CIDR notation, calculating Network ID, Broadcast ID, and host ranges for A/L ICT past paper problems.

---
# 1. Structure of an IPv4 Address

An IPv4 address consists of **32 bits** divided into 4 octets (bytes) separated by dots.

$$\text{Example: } 192.168.10.35 = 11000000.10101000.00001010.00100011_2$$

An IP address is divided into two parts:
$$\text{IP Address} = \text{Network ID} + 	\text{Host ID}$$

---
## 2. Subnetting Formulas

For a given CIDR prefix `/N` (where $N$ is the number of Network bits):
- **Host Bits ($h$)** = $32 - N$
- **Total Addresses in Subnet** = $2^h$
- **Usable Host Addresses** = $2^h - 2$ *(Subtracting Network ID and Broadcast ID)*
- **Subnet Mask**: First $N$ bits set to `1`, remaining $h$ bits set to `0`.

---
## 3. Step-by-Step Subnetting Worked Example

> [!EXAMPLE] Problem
> Given IP `192.168.1.130/26`, find:
> 1. Subnet Mask
> 2. Network ID
> 3. First Usable Host IP
> 4. Last Usable Host IP
> 5. Broadcast ID

### Solution Steps:

1. **CIDR Prefix**: `/26` $\rightarrow N = 26$, Host bits $h = 32 - 26 = 6$.
2. **Subnet Mask**:
   - 26 ones: `11111111.11111111.11111111.11000000`
   - In Decimal: `255.255.255.192`
3. **Block Size (Magic Number)**:
   - $256 - 192 = 64$ (or $2^h = 2^6 = 64$).
   - Subnet boundaries increment by 64: `0, 64, 128, 192`.
4. **Determine Subnet**:
   - Target host `130` falls between `128` and `191`.
   - **Network ID**: `192.168.1.128`
   - **Broadcast ID**: `192.168.1.191` (one less than next subnet 192).
5. **Usable Host Range**:
   - **First Host**: `192.168.1.129`
   - **Last Host**: `192.168.1.190`
   - **Total Usable Hosts**: $2^6 - 2 = 62$ hosts.