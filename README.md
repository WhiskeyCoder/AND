# AND - Advanced Network Disruptor

> **"Sometimes chaos is an art form."**


## NOTE:
Due to dangerous involved in a public release of such a tool that is basically a DoS Worm I will not be releasing the source anytime soon. but I have attached network logs and pcaps.

## 🧨 Project Overview
**AND (Advanced Network Disruptor)** is a high-intensity, simulation-based network traffic generator designed to stress-test edge devices, simulate catastrophic protocol collisions, and observe multi-protocol cascading network failures in a controlled environment.

It mimics the behavior of a misconfigured rogue device, legacy malware, or malformed packet worm with spoofed ICMP, UDP, TCP, and other random packet types. It is built for **educational**, **research**, and **defensive analysis** use only.

---

## ⚙️ Key Features
- 🔁 **Multi-Protocol Chaos:** Fires ICMP, TCP, UDP, DNS, NTP, MEMCACHE, and more.
- 🎯 **Target-Agnostic Simulation:** Simulated storm can affect randomized local ranges for realism.
- 🧪 **Simulation Mode:** Outputs a Wireshark-compatible `.pcap` file for analysis (no real packets sent).
- ⛔ **Built-in Kill Switch:** Graceful Ctrl+C interruption to stop the tool cleanly.
- 🔒 **Does NOT activate by default.** All dangerous payloads require intentional user command.

---

## 📸 Sample Output
![Sample PCAP](https://github.com/WhiskeyCoder/AND/blob/main/2025-04-19%2022_45_33-Window.png)  
*Realistic TTL Exceeded, Host Unreachable, and Fragmentation Failure simulations.*

---

## 🧪 Simulation Mode
Use this to generate realistic `.pcap` output without touching your actual network.

```bash
python3 cisco_down.py --simulate --count 200 --output simulated_storm.pcap
```

- `--simulate` → Enables PCAP simulation only (no packets sent)
- `--count` → Number of packets to simulate
- `--output` → File path to save `.pcap`

> 📂 Open this file in Wireshark for full analysis.

---

## 💀 Real Mode (Not Recommended)
```bash
sudo python3 cisco_down.py --target 192.168.1.1
```
> ⚠️ This sends raw packets. Use **only** in **isolated test environments**. Never on public networks.

---

## 🛑 Kill Switch
Press `Ctrl+C` at any time to safely stop packet flood. You'll see:
```
🔥 Kill switch activated. Exiting cleanly.
```

---

## 🧠 Inspiration & Lore
AND is a chaotic recreation of a real-world event where a misconfigured student tool took down an entire Cisco lab — causing switches to reboot from echo floods, protocol spam, and malformed fragments. It became the stuff of **legend** in the college's network lore as the fastest DoS ever on campus with only taking 3 second to take down the entire lab infrastrcture.

This project pays tribute to that chaotic moment in history by recreating the "digital entropy" in a **controlled** environment, with simulation and testing modes that allow for safe analysis.

---

## 📘 Recommended Use Cases
- Blue team training labs
- Simulated malware traffic
- IDS/IPS stress tests
- Chaos engineering for networks

---

## 📄 License & Legal
This tool is provided for **educational** and **ethical research** purposes only.
**Do not deploy it on networks without permission.**
Any misuse is the sole responsibility of the user.

> **Author:** [WhiskeyCoder](https://github.com/WhiskeyCoder) 
> **Project Codename:** "AND" — *Because sometimes, all it takes is one more packet... AND everything falls apart.*

---

## 💬 Want to contribute?
Have an idea for better simulation logic or want to add detection evasion layers for Red/Blue training scenarios?
Feel free to fork and submit a pull request!

---

## 🧪 Next Features (WIP)
- [ ] Add spoofed MAC address simulation
- [ ] Emulate ARP storm edge-case
- [ ] `--loop` flag for endless chaos until killed
- [ ] IPv6 options and malformed header injection
- [ ] Add attack signature database for detection training

---

**Run safe. Simulate smart. Cause chaos... responsibly.**
