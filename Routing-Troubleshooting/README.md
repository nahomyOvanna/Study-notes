#  Routing Troubleshooting – Study Notes

Routing issues can lead to unreachable destinations, dropped packets, or misrouted traffic. This guide outlines a structured approach to troubleshooting Layer 3 routing issues in both lab and production environments.

---

##  Troubleshooting Flowchart

1️⃣ **Check Physical Connectivity**  
→ Are the interfaces up/up and cables or virtual links in place?

2️⃣ **Verify IP Addressing**  
→ Use `show interfaces` and `ping` to confirm IPs and subnet correctness.

3️⃣ **Check Routing Table**  
→ Use `show ip route` to verify if the route to destination exists and is correct.

4️⃣ **Trace the Path**  
→ Use `traceroute` to see where the packet is getting stuck.

5️⃣ **Review Routing Configuration**  
→ Static: Check next-hop IP  
→ Dynamic: Check OSPF/BGP neighbors, area IDs, timers

6️⃣ **Test End-to-End Reachability**  
→ From source to destination using `ping`, `traceroute`, and capture tools.

7️⃣ **Analyze Firewall or ACLs**  
→ Look for blocked traffic or UFW rules that may be interfering.

---

##  Useful Commands (VyOS)

```
show ip route              # View full routing table
show ip route static       # View static routes only
show ip route ospf         # View OSPF-learned routes
ping <ip>                  # Test reachability
traceroute <ip>            # Trace packet path
show interfaces            # Check interface IPs and status
```

---

##  Key Checks

|  Check               |  Why It Matters                                             |
|------------------------|--------------------------------------------------------------|
| Interface is up/up     | Without Layer 2, routing won’t work                          |
| Correct subnet mask    | Misaligned masks can break communication                     |
| Next-hop is reachable  | No reach = blackhole or drop                                 |
| Route preference (AD)  | Static vs OSPF vs BGP can override each other                |
| No routing loops       | Watch for recursive routes or faulty redistribution          |

---

##  Example Scenario

- Issue: Host can't reach 10.10.10.0/24

- Steps Taken:

    - Checked ping to next-hop → Success

    - Checked show ip route → Route missing

    - Found missing static route → Added route

    - Route appears → Host can now reach

---

##  Routing issues are almost always about:

- Misconfigurations

- Missing routes

- Bad next-hops

- Incorrect IPs or masks

### Follow a layered, logical flow — and use your show commands!








