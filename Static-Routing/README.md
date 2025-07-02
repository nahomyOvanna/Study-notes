# 🛰️ Static Routing – Study Notes

Static routing is a method of manually defining the path that network traffic should take between devices. Unlike dynamic routing protocols, static routes do not adapt to changes in the network automatically.

---

## 🧠 Key Concepts

- **Static Route**: A manually configured path from one network to another.
- **Use Case**: Best suited for small, stable networks with predictable paths.
- **Administrative Distance**: Static routes typically have a distance of **1**, making them preferred over most dynamic routes by default.

---

## 🛠️ Configuration (VyOS Example)

```
# Set a static route to reach 10.0.2.0/24 via next-hop 192.168.1.2
set protocols static route 10.0.2.0/24 next-hop 192.168.1.2

# Apply and save the configuration
commit
save
```

---

## 🔍 Useful Show Commands

```
# View currently configured static routes
show ip route static

# View full routing table
show ip route

# Show interface status and IP configuration
show interfaces
```

## 🧪 Troubleshooting Checklist

| ✅ Step | 🔧 Command or Tool       | 🔎 What to Check                                |
|--------|--------------------------|-------------------------------------------------|
| 1️⃣     | `ping`                   | Can you reach the next-hop or destination?      |
| 2️⃣     | `traceroute`             | Where is the traffic stopping?                  |
| 3️⃣     | `show ip route`          | Is the static route present in the table?       |
| 4️⃣     | `show interfaces`        | Are interfaces up/up with correct IPs?          |
| 5️⃣     | `tcpdump` / `Wireshark` | *(Optional)* Inspect real-time packet flow      |

---

## 💡 Best Practices

✔️ Verify interface connectivity before troubleshooting routing.

✔️ Avoid overlapping subnets and ambiguous routes.

✔️ Use descriptive documentation when applying in production.

✔️ Use static routes sparingly in large or dynamic environments.

---

## 🧪 Example Scenario (Lab 01)

Topology:

`R1` ↔️ `R2`

  - R1 is configured with a static route to reach `192.168.2.0/24` via `192.168.1.2`.

  - R2 is configured with a static route to reach `192.168.1.0/24` via `192.168.2.1`.

This enables bi-directional communication between networks using only static routes.

----

## ✅ Summary

Static routing is:

  - Simple to configure

  - Fast to process

  - Great for small labs and stable environments

But:

  - It lacks scalability

  - Doesn’t adapt to network changes automatically













