# 🧭 DHCP vs Static IP – Study Notes

When assigning IP addresses to devices, you can use **Dynamic Host Configuration Protocol (DHCP)** or **Static IP Addressing**. Each method has its strengths depending on the use case.

---

## 🧠 Definitions

| Type | Description |
|------|-------------|
| **DHCP** | A protocol that automatically assigns IP addresses and other network settings to devices |
| **Static IP** | Manually configured IP address that does not change unless edited by an admin |

---

## 🔄 DHCP – Dynamic IP Addressing

- ✅ Assigned automatically by DHCP server (e.g., router, firewall)
- 📦 Includes IP, subnet mask, gateway, DNS, lease time
- 🔄 IPs may change over time (lease expiration or reboot)

### 📌 When to Use:
- End-user devices (laptops, phones)
- Temporary or roaming hosts
- Large networks for easier management

---

## 📍 Static IP Addressing

- ✅ Manually configured and permanently assigned
- 🧭 Requires admin knowledge of subnet, gateway, DNS
- 🔒 IP does not change unless modified

### 📌 When to Use:
- Servers (DNS, web, mail)
- Network infrastructure (routers, switches, firewalls)
- Printers or devices that need to be reachable consistently

---

## ⚖️ Comparison Table

| Feature | DHCP | Static IP |
|---------|------|-----------|
| Configuration | Automatic | Manual |
| Flexibility | High | Low |
| Stability | Can change | Fixed |
| Admin Overhead | Low | High |
| Best For | Clients, phones, general hosts | Servers, network devices |

---

## 🛠️ VyOS Interface Config Examples

### Static IP
```
set interfaces ethernet eth0 address 192.168.1.10/24
set protocols static route 0.0.0.0/0 next-hop 192.168.1.1
```

### 🧪 DHCP Client (VyOS Example)
```
set interfaces ethernet eth0 address dhcp
```

---

## 🚧 Pitfalls to Watch Out For

| ❌ Mistake                          | 🔍 Result                                         |
|------------------------------------|--------------------------------------------------|
| Static IP conflict with DHCP pool  | IP collisions on the network                     |
| Forgot default gateway             | No internet access                               |
| DHCP server down                   | Clients can't get IPs                            |
| Wrong subnet mask                  | Hosts appear reachable but can't talk            |


### ✅ Both methods are essential in networking — DHCP simplifies, while static ensures consistency. Use each wisely depending on your lab or production design.






