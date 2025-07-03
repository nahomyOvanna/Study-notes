# 🔀 OSPF – Study Notes

OSPF (Open Shortest Path First) is a **link-state routing protocol** used to dynamically exchange routing information within an autonomous system. It's widely used in enterprise networks for its scalability, fast convergence, and area-based hierarchy.

---

## 🧠 Key Concepts

- **Link-State Protocol**: Routers exchange information about all known routes (topology map).
- **Cost Metric**: Calculated based on bandwidth. Lower cost = preferred path.
- **Hello Packets**: Used to discover and maintain neighbor relationships.
- **LSA (Link-State Advertisements)**: OSPF’s way of sharing topology data.
- **DR/BDR**: Elected on multi-access networks to reduce LSA flooding.

---

## 🏗️ OSPF Areas

| Area Type | Description |
|-----------|-------------|
| **Backbone (Area 0)** | Central hub for all inter-area communication |
| **Standard Area** | Regular area that connects to Area 0 |
| **ABR (Area Border Router)** | Connects Area 0 to other areas |
| **ASBR (Autonomous System Boundary Router)** | Redistributes routes from another protocol into OSPF |

---

## ⚙️ OSPF Configuration – VyOS (Single Area)

```
# Set OSPF process and advertise interfaces
set protocols ospf area 0 network 10.0.0.0/24
set protocols ospf parameters router-id 1.1.1.1

# Apply and save
commit
save
```

## ⚙️ Multi-Area OSPF (Example)

```
# Advertise different interfaces into different areas
set protocols ospf area 0 network 10.0.0.0/24
set protocols ospf area 1 network 192.168.1.0/24
set protocols ospf parameters router-id 3.3.3.3

# Apply and save
commit
save
```

## 🔍 OSPF Verification Commands (VyOS)

```
# View OSPF neighbors and their status
show ip ospf neighbor

# View OSPF routing table
show ip route ospf

# View router ID and configured areas
show ip ospf

# Detailed interface-level info
show ip ospf interface
```

---

## 🧪 OSPF Troubleshooting Tips

| 🧩 Issue             | 🔍 Cause                               | 🛠️ Fix                                                                  |
|----------------------|----------------------------------------|-------------------------------------------------------------------------|
| No neighbor          | Mismatched area ID, MTU, subnet        | Check `show ip ospf neighbor` and interface settings                    |
| One-way adjacency    | Hello/dead timer mismatch              | Verify timers and OSPF settings on both routers                         |
| Routes missing       | No network advertised                  | Check `set protocols ospf area` for correct subnet                      |
| DR/BDR not forming   | Multiple routers in broadcast segment  | Check priority and timers                                               |

---

## 💡 Best Practices

 - Always set a router ID explicitly for stability.

 - Use loopback interfaces as stable router IDs.

 - Keep area 0 as the backbone — all other areas must connect to it.

 - Minimize LSA flooding with appropriate area design.

---

## 📚 Related Labs

 - Lab 04 – Single-area OSPF

 - Lab 05 – Multi-area OSPF + Loopbacks

 - OSPF Route Filtering and Redistribution

---

## ✅ Summary

 - OSPF is ideal for large, structured networks that require:

 - Hierarchical design

 - Faster convergence

 - Scalability with areas

 - Link-state accuracy

Understanding OSPF deeply helps build the foundation for protocols like BGP, EIGRP, or IS-IS, and is essential for enterprise network engineering.





