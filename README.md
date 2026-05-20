# 📻 Online Campus Radio System Using Icecast & Raspberry Pi

> **Published at COMSIGPRO 2024**

A campus-wide internet radio broadcasting system built on Icecast streaming server hosted on a Raspberry Pi — enabling live audio transmission accessible from any device on the campus network.

---

## 📌 Problem Statement

Campus-wide audio broadcasting traditionally requires expensive dedicated hardware infrastructure. Existing PA systems lack the flexibility for on-demand programming, and there was no accessible platform for students and staff to broadcast or consume live audio content across the institution.

---

## 💡 Solution

A fully software-defined campus radio system using open-source tools (Icecast + Liquidsoap) hosted on a low-cost Raspberry Pi. Any device connected to the campus network can tune in via a browser or media player — no special hardware required for listeners.

---

## 🏗️ System Architecture

```
[Audio Source]
   ├── Microphone / Live Input
   ├── Music Library
   └── Scheduled Playlists
         │
   [Raspberry Pi – Encoder & Server]
   ├── Liquidsoap / DarkIce – Audio encoding
   ├── Icecast – Streaming server
   └── Stream management scripts
         │
   [Campus Network]
         │
   [Listeners]
   ├── Browser (HTTP stream)
   ├── VLC / Media Player
   └── Mobile Devices
```

---

## ⚙️ Tech Stack

| Component | Role |
|---|---|
| Raspberry Pi 4 | Server host (low-cost, low-power) |
| Icecast2 | Open-source streaming server |
| Liquidsoap / DarkIce | Audio encoding & stream management |
| ALSA / PulseAudio | Linux audio input pipeline |
| Shell Scripts | Automation & stream management |
| Campus Wi-Fi / LAN | Distribution network |

---

## 🚀 Setup Overview

### 1. Install Icecast on Raspberry Pi
```bash
sudo apt update
sudo apt install icecast2
```

### 2. Configure Icecast (`/etc/icecast2/icecast.xml`)
```xml
<icecast>
  <location>BMSIT&M Campus</location>
  <hostname>localhost</hostname>
  <limits>
    <clients>100</clients>
    <sources>2</sources>
  </limits>
  <authentication>
    <source-password>hackme</source-password>
    <admin-user>admin</admin-user>
    <admin-password>hackme</admin-password>
  </authentication>
  <listen-socket>
    <port>8000</port>
  </listen-socket>
</icecast>
```

### 3. Start streaming with DarkIce or Liquidsoap
```bash
# Example with DarkIce
darkice -c /etc/darkice.cfg
```

### 4. Tune in from any campus device
```
http://<raspberry-pi-ip>:8000/campus-radio
```

---

## 📡 Features

- Live audio broadcast over campus network
- Scheduled playlist automation
- Low-latency streaming (tested and benchmarked)
- Minimal hardware overhead — entire system runs on a single Pi
- Web-based admin panel for stream management
- Scalable to additional sources with no hardware changes

---

## 📊 Performance Benchmarks

| Metric | Result |
|---|---|
| Stream Latency | < 2 seconds (LAN) |
| Concurrent Listeners | 100+ (tested) |
| Server Load (Raspberry Pi 4) | < 20% CPU at full load |
| Audio Quality | 128 kbps MP3 / 44.1 kHz |

---

## 📄 Publication

> **"Design and Implementation of an Online Campus Radio System Using Icecast and Pi Based Local Client"**
> COMSIGPRO 2024
> Covers system architecture, latency benchmarks, and scalability considerations for low-cost institutional broadcasting.

---

## 🔧 Scalability

The architecture supports:
- Multiple simultaneous broadcast sources
- Remote broadcasting via authenticated source clients
- Extension to internet-facing streaming with port forwarding
- Integration with existing campus event infrastructure

---

## 👤 Author

**Sri Srujan Hari T**
B.E – Electronics & Communication Engineering, BMSIT&M
[LinkedIn](https://www.linkedin.com/in/srujan-hari-undefined-1a7364399) | thammineedisrujanhari@gmail.com
