#  VyOS Commands Cheat Sheet

VyOS is a powerful open-source network OS used for routing, firewalling, and VPN setups — perfect for lab environments and real-world simulations.

This cheat sheet covers essential VyOS commands for configuration, troubleshooting, and interface management.

---

##  Configuration Basics

| Task | Command |
|------|---------|
| Enter configuration mode | `configure` |
| Save changes | `commit` → `save` |
| Discard changes | `discard` |
| Exit config mode | `exit` |
| Exit session | `exit` (again) |

---

##  Interface Management

```
# Set a static IP on an interface
set interfaces ethernet eth0 address 192.168.1.10/24

# Set interface to use DHCP
set interfaces ethernet eth0 address dhcp

# Show interface status
show interfaces

# Bring interface up or down
set interfaces ethernet eth0 disable   # disable interface
delete interfaces ethernet eth0 disable  # enable interface
```

---

##  Static Routing

```
# Add a static route
set protocols static route 10.0.2.0/24 next-hop 192.168.1.2

# View routing table
show ip route
```
---

###  Dynamic Routing (OSPF/BGP)

```
# Set router ID
set protocols ospf parameters router-id 1.1.1.1

# Advertise a network into OSPF
set protocols ospf area 0 network 10.0.0.0/24

# BGP config basics
set protocols bgp 65001 parameters router-id 1.1.1.1
set protocols bgp 65001 neighbor 192.0.2.2 remote-as 65002
set protocols bgp 65001 network 10.10.10.0/24
```

---

##  Show / Debug Commands

|  Purpose                     |  Command                    |
|-------------------------------|-------------------------------|
| Show running configuration    | `show configuration`          |
| Show interface IPs & status   | `show interfaces`             |
| Show routing table            | `show ip route`               |
| Show OSPF neighbors           | `show ip ospf neighbor`       |
| Show BGP summary              | `show ip bgp summary`         |
| Ping a destination            | `ping <ip>`                   |
| Traceroute                    | `traceroute <ip>`             |

---

##  Firewall Example (UFW not used in VyOS)

```
# Create a firewall rule
set firewall name BLOCK-IN rule 10 action drop
set firewall name BLOCK-IN rule 10 source address 192.168.1.100

# Apply to an interface
set interfaces ethernet eth0 firewall in name BLOCK-IN
```

---

##   Best Practices

- Always commit then save after making changes

- Use show configuration to verify syntax before committing

- Use loopbacks for router IDs in OSPF/BGP setups

- Use tab for autocompletion — VyOS has CLI help built-in!

---

###  VyOS gives you enterprise-grade control in an open, scriptable, and GNS3-friendly platform. Mastering these commands gives you an edge in routing, firewalls, and infrastructure design.






