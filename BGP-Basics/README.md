#  BGP Basics – Study Notes

Border Gateway Protocol (BGP) is a **path vector routing protocol** used to exchange routing information between **autonomous systems (AS)**. It is the backbone of the internet and a key protocol in large-scale enterprise and hybrid cloud environments.

---

##  Key Concepts

| Term | Description |
|------|-------------|
| **AS (Autonomous System)** | A collection of IP networks under a single administrative domain |
| **eBGP** | External BGP – used between different ASes |
| **iBGP** | Internal BGP – used within the same AS |
| **Next-Hop** | IP address used to reach the advertised network |
| **Path Attributes** | Information used to select best path (AS-Path, Local Pref, MED, etc.) |
| **Administrative Distance** | eBGP = 20, iBGP = 200 (lower is preferred) |

---

##  BGP Characteristics

- **Path Vector Protocol**
- **TCP-based (port 179)**
- Supports **CIDR** and **classless routing**
- Does **not** rely on periodic updates
- Manual configuration — no auto discovery

---

##  BGP Configuration Example (VyOS)

```
# Set the local AS
set protocols bgp 65001 parameters router-id 1.1.1.1

# Define a neighbor in another AS
set protocols bgp 65001 neighbor 192.0.2.2 remote-as 65002

# Advertise a local network
set protocols bgp 65001 network 10.0.0.0/24

# Commit and save
commit
save
```

---

##  Show Commands (VyOS)

|  Command                 |  Description                |
|---------------------------|-------------------------------|
| `show ip bgp summary`     | BGP neighbor status           |
| `show ip bgp`             | View BGP routing table        |
| `show ip bgp neighbors`   | Detailed neighbor info        |

---

##  Path Selection (Simplified Order)

1. **Highest Local Preference** (iBGP)
2. **Shortest AS Path** (eBGP)
3. **Lowest Origin Type**
4. **Lowest MED**
5. **eBGP over iBGP**
6. **Lowest IGP metric to next-hop**
7. **Oldest route**
8. **Lowest Router ID**

---

##  Real-World Use Cases

- Connecting to an ISP (eBGP)
- Connecting cloud environments to on-prem via VPN or Direct Connect
- Inter-DC routing in multi-vendor or multi-region setups
- Load balancing and multi-path failover scenarios

---

##  BGP Pitfalls to Avoid

|  Mistake |  Result |
|------------|-----------|
| No `network` statement | Routes not advertised |
| No `neighbor` config   | Peering won't establish |
| Firewall blocks port 179 | No BGP session |
| Missing `update-source` for loopback peers | Session won't come up |

---

###  **BGP is powerful but sensitive** — it gives you full control, but with that comes responsibility.





















