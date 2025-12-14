# Shipwrecked Radio – System Plan

## 1. Overview

This document describes the audio and broadcast architecture for the **Shipwrecked** festival.

Festival stages:

1. **Shipwrecked Stage**
2. **Humming Hut**
3. **Hidden Reef**
4. **Tourtuga**

Goals:

- Each stage has:
  - A **local PA mix**.
  - An **FM transmitter** for local listening (cars, camp radios, etc.).
  - A **digital audio stream** sent to an **AzuraCast** server.
- At a scheduled time during the festival, **all stages simultaneously broadcast the Shipwrecked Stage audio** for approximately **3 hours**.
- Use **FM on the festival site** as the **primary, safest** distribution method for the Shipwrecked Stage takeover.
- Use **digital streaming (AzuraCast)** for:
  - Remote listening.
  - Recording/archiving.
  - Monitoring and future automation.

---

## 2. High-Level Architecture

### 2.1 On-Site FM Architecture

**Shipwrecked Stage**:

- Acts as the **master audio source** during the takeover.
- Feeds:
  - Its own **main stage FM transmitter** (local frequency, e.g., 88.x MHz).
  - A dedicated **“master” FM transmitter** on a **single site-wide frequency** used only for distribution of the Shipwrecked Stage audio to other stages (e.g., 87.9 MHz, or another clear frequency).
  - A **digital encoder** sending the master audio to **AzuraCast**.

**Other stages (Humming Hut, Hidden Reef, Tourtuga)**:

- Have their own **local FM transmitters** on their own frequencies.
- Each has an **FM receiver permanently tuned** to the **Shipwrecked Stage master frequency**.
- An **audio switch** at each stage chooses between:
  - **Local stage mix** (normal mode).
  - **FM receiver (Shipwrecked Stage)** (takeover mode).

During the **3-hour takeover**:

- All stages switch their FM feed input to the FM receiver output.
- Each local transmitter re-broadcasts the **Shipwrecked Stage audio** on its own frequency.

### 2.2 Digital / AzuraCast Architecture

Per stage:

- An **audio interface and small computer** (or integrated encoder) captures the local stage mix.
- The encoder sends an **audio stream** to the **AzuraCast server**, e.g.:

  - `shipwrecked-stage`
  - `humming-hut`
  - `hidden-reef`
  - `tourtuga`

AzuraCast roles:

- Public or private listening streams.
- Recording / archiving.
- Central place to **monitor whether each stage stream is up**.
- Later: could be used as a **digital backup path** for the Shipwrecked Stage audio.

---

## 3. Modes of Operation

### 3.1 Normal Mode

- Each stage:
  - Mixes its local show.
  - Sends that mix to:
    - Its **local FM transmitter**.
    - Its **digital encoder → AzuraCast**.
- Shipwrecked Stage:
  - Also transmits its audio on the **master FM frequency** that all other stage receivers are tuned to.
  - That master FM signal is **present but not selected** at the other stages (they are still on local audio).

### 3.2 Takeover Mode (Shipwrecked Stage Simulcast)

- Triggered at an agreed **time in the schedule**.
- Each stage (including Shipwrecked if desired):
  - Switches from **local mix** to **Shipwrecked Stage FM receiver output** as the source feeding its FM transmitter.
- For the duration (~3 hours):
  - All stages re-broadcast the **same Shipwrecked Stage audio** on their own local frequencies.
- After the takeover:
  - Each stage switches back to its own **local mix**.

At this level, switching can be:

- **Manual** (physical toggle switches, patching).
- Or later **software-controlled** using relay boards / GPIO.

---

## 4. Hardware Roles (Conceptual)

### 4.1 Per Stage

Each stage (including Shipwrecked) will roughly have:

- **Stage mixer / FOH output**.
- **Audio interface** (for digital streaming).
- **Small computer or streaming encoder** to send audio to AzuraCast.
- **FM transmitter** for that stage’s local broadcast.
- **FM monitor receiver** (for confidence monitoring and testing).
- **Shipwrecked-only**:
  - One additional **master FM transmitter** dedicated to distribution to other stages.

### 4.2 Non-Shipwrecked Stages (Humming Hut, Hidden Reef, Tourtuga)

Each non-master stage has additional:

- **FM receiver tuned to Shipwrecked master frequency**.
- **Audio switch / router**:
  - Input A: Local stage mix.
  - Input B: Shipwrecked FM receiver.
  - Output: Stage FM transmitter (and optionally to monitors).

Switching can be:

- Passive / mechanical (toggle switch or patchbay).
- Simple **A/B active switcher** box.
- Or later, **relay-based** and controlled by a small computer.

---

## 5. AzuraCast Integration

Per stage:

- Audio interface output → **encoder** on a small computer (e.g., Raspberry Pi, Intel NUC, or existing laptop).
- Encoder sends a live stream to AzuraCast using:
  - Icecast-compatible protocol (e.g., `liquidsoap`, `butt`, `ffmpeg`, `gstreamer`, etc.).

Per stream:

- AzuraCast stream names:
  - `shipwrecked-stage`
  - `humming-hut`
  - `hidden-reef`
  - `tourtuga`

Primary uses:

- **Off-site listening** (if desired).
- **Recordings** of all stages.
- **Monitoring** (check if the stage is live / levels are present).
- Future:
  - Potential **digital backup** for Shipwrecked Stage takeover.

---

## 6. Synchronization & Operations

### 6.1 Time & Schedule

- Keep a shared **festival master schedule**:
  - “Shipwrecked Simulcast” start and end times.
- Ensure all stage leads are briefed:
  - When to flip to Shipwrecked.
  - How to fall back to local if needed.

If computers are used:

- Optionally keep stage computers **NTP synced** (network time).
- This is helpful for logging and any later automation.

### 6.2 Testing & Rehearsal

Before the festival:

- **RF Coverage Test**:
  - Turn on Shipwrecked master FM transmitter.
  - Check signal strength and quality at each stage receiver.
  - Adjust power, antennas, or placement as needed.
- **Takeover Rehearsal**:
  - Practice switching each stage from:
    - Local → Shipwrecked → back to Local.
  - Confirm audio levels and latency are acceptable.

---

## 7. Future Software & Automation (Later Phase)

Not required for the first version, but future goals:

- **Control application** to:
  - Monitor AzuraCast stream health per stage.
  - Log events (e.g., “Takeover started” / “Takeover ended”).
  - Optionally control **relay-based input switches** at each stage.
- **Web dashboard**:
  - Show if each stage is:
    - Live to AzuraCast.
    - In LOCAL or SHIPWRECKED mode.
- **Digital backup**:
  - If the FM master link fails, a stage’s encoder/receiver can switch to a **digital stream of Shipwrecked Stage** as a fallback.

---

## 8. Open Questions

- What **power levels** and frequencies are legal and practical for FM at the site?
- Do you already own some of the gear:
  - Transmitters?
  - Audio interfaces?
  - Stage computers?
- Are you OK with **manual switching** for the first iteration, or do you want **software-controlled switching from day one**?
- Where will **AzuraCast** be hosted:
  - On-site server?
  - Cloud/VPS?

These answers will influence the exact hardware spec and budget in `hardware-and-budget.md`
