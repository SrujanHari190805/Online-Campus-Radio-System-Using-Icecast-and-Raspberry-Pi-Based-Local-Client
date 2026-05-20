# Online Campus Radio System Using Icecast & Raspberry Pi

> A three-layer internet radio broadcasting system using Icecast, BUTT, and a Raspberry Pi Zero 2W as a low-cost local group client. Supports up to 500 concurrent listeners with sub-2-second LAN latency.

![IEEE Published](https://img.shields.io/badge/Published-COMSIGPRO%202024-blue)
![Platform](https://img.shields.io/badge/Platform-Raspberry%20Pi%20%7C%20Icecast%20%7C%20ESP32-green)
![Listeners](https://img.shields.io/badge/Validated-500%20Concurrent%20Listeners-orange)

---

## 📄 Publication

> **Design and Implementation of an Online Campus Radio System Using Icecast and Pi Based Local Client**
> Raghunandan G H, Sharana Reddy, Nitish K S, Tarun Patil, Sri Srujan Hari T, Harshitha K V
> *COMSIGPRO 2024*

---

## 📻 Overview

Traditional FM campus radio is expensive (frequency licensing), geographically limited, and offers no interactivity. This system replaces it with an internet-based broadcasting architecture built entirely from open-source software and low-cost hardware. It is globally accessible, scalable, interactive, and runs at a fraction of the cost.

The design has one unique innovation: a **Raspberry Pi Zero 2W as a group access client**, connecting via Bluetooth to an amplifier for campus-wide audio broadcasting in public spaces — enabling both individual listening (web/mobile) and synchronized group listening (auditoriums, common areas).

---



## 🏗️ Three-Layer Architecture

```
┌──────────────────────────────────────────────────────────┐
│                    LAYER 1: INPUT                         │
│  Condenser Mic → Channel Audio Mixer                      │
│  Audacity (recording/editing) + OBS Studio (live stream)  │
└────────────────────────┬─────────────────────────────────┘
                         │ Audio stream
┌────────────────────────▼─────────────────────────────────┐
│                   LAYER 2: BROADCAST                      │
│  Icecast Streaming Server (128 kbps MP3)                  │
│  BUTT (Broadcast Using This Tool) — connects audio input  │
│  Mixx — audio mixing                                      │
│  Local hardware server / NAS for pre-recorded content     │
└────────────────────────┬─────────────────────────────────┘
                         │ HTTP audio stream
         ┌───────────────┴──────────────────┐
         ▼ Individual Access                ▼ Group Access
┌────────────────────┐        ┌──────────────────────────────┐
│  HTML5 Web Player  │        │  Raspberry Pi Zero 2W         │
│  (any browser)     │        │  → Bluetooth → Amplifier      │
│  Real-time metadata│        │  VLC auto-playback             │
│  Campus SSO login  │        │  ESP32 + Relay + Blynk         │
└────────────────────┘        │  (Remote ON/OFF control)      │
                              └──────────────────────────────┘
```

---
![Architecture](images/radio.arc.png)
![Overview](images/radio.overview.png)
![Broadcast Interface](images/radio.interface.png)
![Group Access](images/radio.user.png)

## 🔧 Hardware & Software Stack

### Hardware
| Component | Purpose |
|---|---|
| Raspberry Pi Zero 2W | Low-cost local group broadcast client |
| Condenser Microphone | High-quality live audio capture |
| Channel Audio Mixer | Multi-source audio management |
| ESP32 + Relay Module | Remote control of Pi and amplifier via Blynk |
| Bluetooth Amplifier | Campus-wide audio output for group listening |
| Local Server / NAS | Hosts Icecast; stores pre-recorded content |

### Software
| Software | Role |
|---|---|
| Icecast | Open-source streaming server; MP3/OGG/AAC output |
| BUTT (Broadcast Using This Tool) | Live audio encoder; connects to Icecast |
| Mixx | Real-time audio mixing |
| Audacity | Pre-recording, editing, noise reduction |
| OBS Studio | Multi-source live stream management |
| VLC | Automatic stream playback on Pi client |
| Blynk | Remote control interface for Pi + amplifier relay |
| HTML5 Web Player | Individual listener web interface |

---

## 📊 Performance Results

| Scenario | Jitter (ms) | Packet Loss (%) | Latency (ms) | MOS |
|---|---|---|---|---|
| Library (High-density) | 20–70 | 5% | 130 | 4.0 |
| Campus Courtyard (Outdoor) | 15–90 | 8% | 140 | 3.7 |
| Lab Block (Low-traffic) | 10–20 | 2% | 100 | **4.5** |
| Walking User (Mobile) | 25–120 | 7% | 150 | 3.8 |
| Parking Area (Weak signal) | 30–150 | **12%** | **250** | 3.5 |

**Key findings:**
- Maximum validated concurrent listeners: **500** — no stream quality degradation
- LAN latency: **sub-2 seconds**
- Best experience (MOS 4.5/5) in low-traffic lab zones
- System outperforms FM radio on cost, reach, interactivity, and scalability

---

## 🆚 System Comparison

| Feature | FM Radio | Existing Online | This System |
|---|---|---|---|
| Geographic Reach | Local (10–20 km) | Global | Global |
| Licensing | Expensive | None | None |
| Setup Cost | High | Moderate | **Low** |
| Real-Time Interaction | Call-in only | Basic | Chat, requests |
| Group Broadcast Hardware | None | None | Pi + BT amplifier setup |
| Scalability | Limited | Limited | Scalable |
| Streaming Latency | Minimal | Moderate | Low |

---

## 🔮 Future Enhancements

- AWS cloud integration for global scalability beyond campus
- Live call-in feature for real-time audience interaction
- AI-driven playlist personalization
- Mobile app with push notifications and song requests
- Advanced audio processing for professional broadcast quality

---

## 👥 Authors

| Name | Affiliation |
|---|---|
| Raghunandan G H | ECE, BMSIT&M |
| Sharana Reddy | EEE, BITM Ballari |
| Nitish K S | ECE, BMSIT&M |
| Tarun Patil | ECE, BMSIT&M |
| Sri Srujan Hari T | ECE, BMSIT&M |
| Harshitha K V | ECE, BMSIT&M |
