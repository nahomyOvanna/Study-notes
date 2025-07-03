# 💡 GNS3 Tips – Study Notes

GNS3 (Graphical Network Simulator 3) is a powerful tool for creating virtual network labs using real device images like VyOS, Cisco IOS, and Linux VMs. This guide captures tips, tricks, and fixes from hands-on experience.

---

## 🚀 Getting Started

- ✅ **Run GNS3 as Administrator** (on Windows) or use `sudo` on Linux/Mac to avoid permission errors.
- 🧠 Use the **GNS3 VM** with VirtualBox or VMware for better performance and full feature support.
- 📦 Import appliances like VyOS or Kali Linux using `.gns3a` files from the [GNS3 Marketplace](https://gns3.com/marketplace).

---

## 🛠️ Common Setup Tips

| Task | Tip |
|------|-----|
| Persistent VyOS setup | Use QCOW2 disk images instead of ISO for saved configs |
| Interface naming | Map interface labels clearly (e.g., eth0 → R1 to R2) |
| Snapshots | Take snapshots before major config changes |
| Auto start nodes | Right-click device → Configure → "Start this node when the project starts" |
| Save layout | Save project often to avoid broken topologies after crash |

---

## 🔍 Troubleshooting Lab Issues

| Issue | Fix |
|-------|-----|
| No IP assigned | Check if interface is using DHCP or if config was saved |
| Config lost on reboot | Use `commit` then `save` in VyOS |
| Packet drops | Verify interfaces are connected + `ping` both ends |
| No internet on VMs | Check NAT Cloud config and allow outbound access |
| GNS3 VM not connected | Verify host-only adapter and VM network settings |

---

## ⚙️ Helpful Features

- 🖼️ **Drawings & Labels** – Use annotation tools to map out topologies visually
- 🔌 **Capture packets** – Right-click a link → Start Wireshark capture (great for analysis)
- 🧲 **Cloud Node** – Use it to bridge virtual devices to your physical machine or internet
- 🛑 **Stop/Reload Individual Devices** – No need to reload the whole project

---

## 📂 File & Project Tips

- 🔖 Use short, consistent naming: `Lab01-Static-VyOS`, `Lab05-OSPF-MultiArea`
- 📁 Store configs, topologies, and screenshots together in your repo
- 📝 Document each step for learning + GitHub portfolio

---

## 🧠 Pro Tips

- Enable **console logging** in VyOS for better visibility:
  ```
  set system console device ttyS0 speed 9600
  ```
- Create a base VyOS template with hostname + SSH configured

- Use loopback interfaces in dynamic routing labs for stability

---

### ✅ GNS3 is more than a visual tool — it’s your lab universe.








  
