# Shipwrecked Radio – Hardware and Budget

> NOTE: All prices are **rough ballparks** and should be adjusted for your local market, currency, and whether you buy new/used or already own some equipment.

## 1. Summary

We have 4 stages:

1. Shipwrecked Stage (master)
2. Humming Hut
3. Hidden Reef
4. Tourtuga

For each stage we plan for:

- An **FM transmitter** for the stage.
- A **digital streaming path** to AzuraCast.
- Basic **monitoring / switching hardware**.

Additionally, Shipwrecked Stage needs:

- One extra **master FM transmitter** to distribute its audio to the other stages.

You can treat this document as a **shopping list** plus a starting budget.

---

## 2. Per-Stage Hardware

### 2.1 Common Stage Hardware (All 4 Stages)

These items are per stage.

#### a. Audio Interface

Purpose: Get the stage mix into a computer for streaming.

- Type: 2-channel USB audio interface (line-level input).
- Examples:
  - Budget: Behringer UMC22 / UM2, similar.
- Qty: 1 per stage (4 total).
- Rough cost: **$50–$100 each** → **$200–$400 total**.

#### b. Stage Encoder Computer

Purpose: Encode the audio and send to AzuraCast.

Options (pick what suits you):

- Small single-board computer (e.g. Raspberry Pi 4 or equivalent).
- Existing laptop or small PC if you already have them.

Assumption here:

- New hardware per stage (if needed): Raspberry Pi 4 (4 GB) or similar.

- Qty: 1 per stage (4 total).
- Rough cost: **$80–$120 each** (depending on market, SD card, PSU, case) → **$320–$480 total**.

#### c. Stage FM Transmitter

Purpose: Broadcast the stage mix over FM at the local area of the stage.

- Must comply with **local RF regulations** (very important).
- Power level and antenna type will depend on required coverage.

Approximate options:

- Low-power FM transmitter kits / devices:
  - Rough range: **$100–$400 each** depending on quality and power.

Assuming a mid-range legal low-power TX per stage:

- Qty: 1 per stage (4 total).
- Rough cost: **$200–$400 each** → **$800–$1,600 total**.

#### d. FM Monitor Receiver (Optional but Recommended)

Purpose: Let you monitor what the stage is actually broadcasting, and also test/align levels.

- Type: Simple FM tuner / portable FM receiver with line output if possible.
- Could be:
  - Cheap portable radios, or
  - More serious tuners for better SNR and line-out.

Assuming mid-level tuners:

- Qty: 1 per stage (4 total).
- Rough cost: **$30–$80 each** → **$120–$320 total**.

---

### 2.2 Additional Hardware for NON-Master Stages (Humming Hut, Hidden Reef, Tourtuga)

These are for receiving the Shipwrecked master FM signal and switching.

#### a. FM Receiver for Shipwrecked Master Feed

Each non-master stage needs:

- 1× **FM receiver** permanently tuned to the Shipwrecked master frequency.

This can be:

- Similar or identical to the monitor receiver above (but dedicated).
- Ideally with a stable tuner and **line-level output**.

Assuming mid-level tuners:

- Qty: 1 per non-master stage (3 total).
- Rough cost: **$30–$80 each** → **$90–$240 total**.

#### b. Audio Switch / Router (Local vs Shipwrecked)

Purpose: Select between:

- Input A: Local stage mix.
- Input B: Shipwrecked FM receiver output.
- Output: Feeds the stage FM transmitter (and optionally monitors).

Options:

1. **Manual A/B switch**:
   - Simple passive stereo A/B boxes.
   - Very low-tech, reliable.
   - Approx **$30–$80 each**.

2. **Active switch or relay-based**:
   - Audio relay board driven by stage computer (for later automation).
   - Can build or buy.
   - Approx **$50–$150 each** depending on solution.

For a **first pass**, assume manual A/B switchers:

- Qty: 1 per non-master stage (3 total).
- Rough cost: **$40–$70 each** → **$120–$210 total**.

---

## 3. Additional Hardware for SHIPWRECKED STAGE (Master)

Shipwrecked Stage has everything in **2.1**, plus:

### 3.1 Master FM Transmitter

Purpose: Send Shipwrecked Stage audio over a **single master frequency** to be received at all other stages.

- Needs enough power and a suitable antenna to reach all other stages with clear signal.
- Must comply with local broadcast rules.

Assuming a better-quality low-power or moderate-power FM transmitter:

- Qty: 1.
- Rough cost: **$300–$800** (depending on power, quality, compliance).

### 3.2 Master FM Antenna & Cabling

Purpose: Ensure good site-wide coverage from Shipwrecked Stage.

- Outdoor-rated FM antenna, mast/stand, coax, and connectors.
- Height and placement matter a lot more than raw TX power.

Approximate:

- Antenna + cable + mounts: **$150–$400**.

---

## 4. AzuraCast / Central Infrastructure

### 4.1 AzuraCast Server

You may already have this.

Options:

- Cloud VPS (e.g. 2–4 vCPU, 4–8 GB RAM, SSD).
- On-site small server.

Typical cloud VPS prices:

- **$10–$40/month**, depending on capacity and provider.
- For a multi-day festival, this is usually not the big cost item.

### 4.2 Networking

You need **IP connectivity** from each stage encoder to the AzuraCast server:

- If AzuraCast is **cloud-hosted**:
  - Internet uplink from the festival (wired or robust 4G/5G solution).
- If AzuraCast is **on-site**:
  - Local network across stages (wired or properly designed Wi‑Fi / point-to-point links).

Budget placeholder for networking gear (if not already available):

- Switches / routers / cables / possibly Wi‑Fi bridges:
  - Rough range: **$200–$800 total**, depending on how much you already own.

---

## 5. Soft Costs and Misc

### 5.1 Cables, Power, Racks

- Balanced audio cables, adapters, DI boxes if needed.
- Power distribution, UPS / surge protection.
- Racks or cases for transmitters, receivers, computers.

Placeholder budget:

- **$300–$800 total**.

### 5.2 Contingency

Electronics & events always have surprises:

- Recommended contingency: **10–20% of total hardware budget**.

---

## 6. Rough Budget Roll-Up (Very Approximate)

These numbers are intentionally wide; you’ll tighten them by picking specific models.

### 6.1 Per-Stage (x4) – mid-range estimate

- Audio interface: ~$75
- Encoder computer: ~$100
- Stage FM transmitter: ~$300
- Monitor receiver: ~$50

Per stage subtotal: **~$525**

For 4 stages: **~$2,100**

### 6.2 Extra for 3 Non-Master Stages

- Shipwrecked FM receiver: ~$50 × 3 = ~$150
- A/B audio switch: ~$60 × 3 = ~$180

Subtotal: **~$330**

### 6.3 Extra for Shipwrecked Master

- Master FM transmitter: ~$500
- Master FM antenna + cabling: ~$250

Subtotal: **~$750**

### 6.4 Infrastructure & Misc

- AzuraCast server (if hosted): say **$20–$40** for a month.
- Networking hardware (if needed): say **$400**.
- Cables, mounts, small accessories: say **$500**.
- Contingency (10–20%): **add ~ $400–$800**.

---

### 6.5 Very Rough Grand Total (mid-range, new hardware)

- Per-stage base: ~**$2,100**
- Non-master extra: ~**$330**
- Shipwrecked master extra: ~**$750**
- Infra + misc + contingency: ~**$1,000–$1,700**

**Estimated total range: ~\$4,200 – \$4,900**

This will come **down** if:

- You already own some transmitters, interfaces, or computers.
- You use cheaper second-hand gear.
- You simplify monitoring hardware.

---

## 7. Next Steps

1. **Mark what you already own**:
   - Transmitters / interfaces / PCs / cables.
2. **Pick specific models** for:
   - FM transmitters (stage + master).
   - FM receivers (line-out if possible).
   - Audio interfaces and computers.
3. Replace the ranges above with **real prices** from your suppliers.
4. Update this file with:
   - Supplier links.
   - Final per-item quantity and cost.
   - Actual total budget.

Once this is stable, we can extend the docs with wiring diagrams and a simple “how to set up each stage” checklist.