# 📐 Subnetting Cheat Sheet

Subnetting is the process of dividing a larger network (network ID) into smaller, efficient sub-networks. It helps with IP address management, segmentation, and improved routing performance.

---

## 🧠 Key Terms

| Term | Definition |
|------|------------|
| **IP Address** | Unique identifier for a device on a network (e.g., 192.168.1.10) |
| **Subnet Mask** | Determines how many bits are used for network vs host (e.g., 255.255.255.0) |
| **CIDR Notation** | Shorthand for subnet mask (e.g., /24) |
| **Network Address** | First address in the range (all host bits = 0) |
| **Broadcast Address** | Last address in the range (all host bits = 1) |
| **Usable Hosts** | Total IPs in a subnet minus 2 (network + broadcast)

---

## 📏 Subnetting Table (IPv4)

| CIDR | Subnet Mask | # of Subnets (Class C) | # of Hosts per Subnet | Wildcard Mask |
|------|-------------|------------------------|------------------------|---------------|
| /24  | 255.255.255.0 | 1   | 254 | 0.0.0.255 |
| /25  | 255.255.255.128 | 2  | 126 | 0.0.0.127 |
| /26  | 255.255.255.192 | 4  | 62  | 0.0.0.63 |
| /27  | 255.255.255.224 | 8  | 30  | 0.0.0.31 |
| /28  | 255.255.255.240 | 16 | 14  | 0.0.0.15 |
| /29  | 255.255.255.248 | 32 | 6   | 0.0.0.7  |
| /30  | 255.255.255.252 | 64 | 2   | 0.0.0.3  |

---

## 🧮 Formulas

- 🖩 **Number of Hosts** = `2^(32 - CIDR)` − 2  
- 🧩 **Block Size** = `256 - last octet of subnet mask`  
- 📦 **Total Subnets (in a Class C)** = `2^borrowed bits`

---

## 🛠️ Quick Reference Examples

| Subnet | CIDR | Network | Broadcast | Host Range |
|--------|------|---------|-----------|------------|
| 192.168.1.0/26 | /26 | 192.168.1.0 | 192.168.1.63 | 192.168.1.1 – 192.168.1.62 |
| 10.0.0.0/24 | /24 | 10.0.0.0 | 10.0.0.255 | 10.0.0.1 – 10.0.0.254 |
| 172.16.0.0/30 | /30 | 172.16.0.0 | 172.16.0.3 | 172.16.0.1 – 172.16.0.2 |

---

## 🧠 Tips to Remember

- /30 is great for **point-to-point links** (only 2 hosts needed).
- A **/24** subnet is the classic 254-host LAN range.
- Subnetting can occur **beyond Class A/B/C limits** thanks to CIDR.

---

## 🚧 Practice Scenario

You're given `192.168.10.0/24` and asked to divide it into 4 subnets.  
- Subnet mask? → **/26**  
- How many IPs per subnet? → 64 total, **62 usable**
  - First subnet:  
  - Network: `192.168.10.0`  
  - Broadcast: `192.168.10.63`  
  - Hosts: `192.168.10.1 – 192.168.10.62`

---

### ✅ **Subnetting is a must-have skill** for IP planning, security segmentation, and efficient routing — especially in lab and cloud design work.
