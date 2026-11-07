# InterviewAce AI:  Asymmetric Dual-Screen WebRTC Teleprompter 🎯

<div align="center">

[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org/)
[![WebRTC](https://img.shields.io/badge/WebRTC-Peer--to--Peer-333333?style=for-the-badge&logo=webrtc)](https://webrtc.org/)
[![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://react.dev/)
[![TanStack](https://img.shields.io/badge/TanStack-Query-FF4154?style=for-the-badge&logo=react-query)](https://tanstack.com/)

**An asymmetric dual-device WebRTC intelligence platform and adaptive teleprompter designed for real-time interview transcription, contextual answer generation, and low-latency display synchronization.**

[Architecture Overview](#system-architecture) • [Dual-Screen Protocol](#asymmetric-dual-screen-protocol) • [Adaptive Teleprompter](#adaptive-teleprompter-engine) • [Quickstart](#local-development)

</div>

---

## ⚡ Overview

Preparing for high-stakes technical and executive interviews requires instantaneous access to talking points, architectural diagrams, and structured thought frameworks without breaking eye contact or disrupting video feeds. 

**InterviewAce AI** solves this through an **asymmetric dual-device architecture**:
* **Device A (The Sender / Capture Node):** Operates on an external mobile device or secondary screen, listening to interview questions via direct microphone input or system audio.
* **Device B (The Receiver / Teleprompter Node):** Placed directly in the candidate's line of sight behind the camera, rendering real-time streaming answer structures on a dynamic auto-scrolling teleprompter.

---

## 🏛️ System Architecture

```
┌─────────────────────────────────┐                 ┌─────────────────────────────────┐
│     DEVICE A: SENDER NODE       │                 │     DEVICE B: RECEIVER NODE     │
│   (Mobile / Capture Screen)     │                 │   (Primary Line-of-Sight HUD)   │
│                                 │                 │                                 │
│  • Audio Ingestion / Mic Stream │                 │  • Auto-Scrolling Teleprompter  │
│  • Speech-to-Text Pipeline      │                 │  • Real-Time AI Answer Stream   │
│  • Session Controls & Trigger   │                 │  • Dynamic Font & Speed HUD     │
└────────────────┬────────────────┘                 └────────────────▲────────────────┘
                 │                                                   │
                 │                 Peer-to-Peer DataChannel          │
                 └───────────────────────────────────────────────────┘
                                   [WebRTC Peer Mesh]
```

---

## 🔬 Core Engineering Innovations

### 1. Asymmetric WebRTC Data Pipeline (`useWebRTC.ts`, `SenderPage.tsx`, `ReceiverPage.tsx`)
* Implements direct peer-to-peer WebRTC connections with zero server intermediary latency once signaling is established.
* Encrypted payload transmission for session state, transcribed prompts, and synthesized talking points.
* Resilient reconnection logic handling temporary network degradation or device orientation shifts.

### 2. Velocity-Adaptive Teleprompter Engine (`Teleprompter.tsx`)
* Custom scrolling mechanics that dynamically adjust vertical scroll velocity based on streaming token ingestion rates:
  $$\Delta v \propto \frac{\text{incoming tokens}}{\Delta t}$$
* Prevents jerky auto-scroll jumps, ensuring the text remains locked in the natural focal plane of the user.
* Adjustable typography (custom font scaling, high-contrast dark mode) designed for glass teleprompters and mirrored monitors.

### 3. Real-Time Session Controller (`SessionControls.tsx`, `SessionScreen.tsx`)
* Low-friction hotkeys and controls to pause generation, regenerate bulleted architectural trade-offs, or switch question domains on the fly.
* Multi-source audio routing (hardware microphone, system loopback, or virtual audio cables).

---

## 🛠️ Tech Stack Breakdown

- **Core Technologies:** React 18, TypeScript, Vite
- **Peer-to-Peer Networking:** Native WebRTC (RTCPeerConnection, RTCDataChannel)
- **State & Data Management:** TanStack Query (`@tanstack/react-query`)
- **UI & UX:** Tailwind CSS, Radix UI primitives, Lucide Icons, Sonner notifications

---

## 💻 Local Development

### Prerequisites
* **Node.js**: v18+
* Modern WebRTC-compatible browser (Chrome, Edge, Firefox, Safari)

### Setup
```bash
# 1. Clone repository
git clone https://github.com/mdroushanalam-astra/interview-ace-ai.git
cd interview-ace-ai

# 2. Install dependencies
npm install

# 3. Launch development server
npm run dev
```

1. Open `http://localhost:5173/sender` on Device A (Capture device).
2. Open `http://localhost:5173/receiver` on Device B (Teleprompter screen).
3. Connect via the generated session pair code.

---

<div align="center">
  <sub>Engineered by <a href="https://github.com/mdroushanalam-astra">Md. Roushan Alam</a></sub>
</div>
