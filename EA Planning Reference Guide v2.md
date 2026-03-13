The goal of this guide is to support EW operators calculating link budgets for Electronic Attack planning purposes. The math here will help determine if the jamming power, at distance, is sufficient to overpower the received signal of the enemy radio. Using this guide, the operator will:

1. Calculate your EA platform jamming output in dBm, accounting for distance to the target
2. Calculate the signal strength at the enemy receiver
3. Compare jamming and signal strength at the receiver to determine jamming effects

Flow: Start → Convert to dBm → Add Antenna Gain → (Freq Hopping?) → Calculate Path Loss (<1km OR ≥1km) → Subtract Loss = Result

> [!NOTE] IMPORTANT
> All frequencies must be calculated in megahertz (MHz) and all distances must be calculated in kilometers (km). Failure to do so will result in incorrect results.

---
# Calculate EA Platform Output
## Step 1: Convert your EA wattage to dBm utilizing the rule of three and the rule of ten.

| Rule of Three                                     |     | Rule of Ten                                                |     |
| ------------------------------------------------- | --- | ---------------------------------------------------------- | --- |
| Doubling Power Results in +3dBm (Inverse is true) |     | Increasing Power by 10 results in +10dbm (Inverse is true) |     |
| Watts                                             | dBm | Watts                                                      | dbm |
| 0.015625                                          | 12  | 0.000001                                                   | -30 |
| 0.03125                                           | 15  | 0.00001                                                    | -20 |
| 0.0625                                            | 18  | 0.0001                                                     | -10 |
| 0.125                                             | 21  | 0.001                                                      | 0   |
| 0.25                                              | 24  | 0.01                                                       | 10  |
| 0.5                                               | 27  | 0.1                                                        | 20  |
| 1                                                 | 30  | 1                                                          | 30  |
| 2                                                 | 33  | 10                                                         | 40  |
| 4                                                 | 36  | 100                                                        | 50  |
| 8                                                 | 39  | 1000                                                       | 60  |
| 16                                                | 42  | 10000                                                      | 70  |
| 32                                                | 45  | 100000                                                     | 80  |
| 64                                                | 48  | 1000000                                                    | 90  |
| 128                                               | 51  | 10000000                                                   | 100 |
**EA Platform Watts**:_________
**EA Platform dBm**:_____________________

## Step 2: Identify the gain on your antenna
**Antenna Gain**:___ dBi

## Step 3: Calculate the EIRP/ERP of your platform
**EA Platform dBm + Antenna Gain** = ___ dBm

## Step 3a: Account for Frequency Hopping (Do not use if EA platform can "follow" the frequency hop pattern or if the enemy radio is not using frequency hopping)

$$
HoppingTax(dB) = 10log(TotalJammingBandwidth/TargetChannelWidth)
$$
*See Considerations section for details on Total Jamming Bandwidth and Target Channel Width.*

**EIRP dBm - HoppingTax dB** = ___ dBm

> [!NOTE] Next choose Step 4 OR Step 4a
> Choose Step 4 for target distances 1km or greater. Choose step 4a for target distances less than 1km
## Step 4: Path Loss (d ≥ 1 km). Calculate your Path Loss when Target is 1km away or greater
$$
40log(TargetDistanceInkm) + 20log(Frequency) + 32.44 + Clutter
$$

| Clutter                 |                  |
| ----------------------- | ---------------- |
| Terrain Type            | Add to Loss (dB) |
| Free Space (Air to Air) | +0 dB            |
| Rural/Open Field        | +20 dB           |
| Light Forests/Suburbs   | +30 dB           |
| Dense Forest/Urban      | +40 dB           |
**Path Loss**=___ dB

## Step 4a: Path Loss (d < 1 km). Calculate your Path Loss when Target is less than 1km away

$$
20log(TargetDistanceInkm) + 20log(Frequency)+ 32.44 + Clutter
$$

| Clutter                 |                  |
| ----------------------- | ---------------- |
| Terrain Type            | Add to Loss (dB) |
| Free Space (Air to Air) | +0 dB            |
| Rural/Open Field        | +20 dB           |
| Light Forests/Suburbs   | +30 dB           |
| Dense Forest/Urban      | +40 dB           |
**Path Loss**=___ dB

## Step 5: Calculate Received Jamming Power
$$
EIRP (from Step 3 or Step3a) - PathLoss
$$
**Received Jamming Power**= ___ dBm


> [!NOTE] Remember
> Path Loss is a single value (either 1km or greater or less than 1km.) Do not add two Path Loss values together.


---
# Calculate Enemy Radio Output
## Step 1: Convert enemy radio wattage into dBm

| Rule of Three                                     |     | Rule of Ten                                                |     |
| ------------------------------------------------- | --- | ---------------------------------------------------------- | --- |
| Doubling Power Results in +3dBm (Inverse is true) |     | Increasing Power by 10 results in +10dbm (Inverse is true) |     |
| Watts                                             | dBm | Watts                                                      | dbm |
| 0.015625                                          | 12  | 0.000001                                                   | -30 |
| 0.03125                                           | 15  | 0.00001                                                    | -20 |
| 0.0625                                            | 18  | 0.0001                                                     | -10 |
| 0.125                                             | 21  | 0.001                                                      | 0   |
| 0.25                                              | 24  | 0.01                                                       | 10  |
| 0.5                                               | 27  | 0.1                                                        | 20  |
| 1                                                 | 30  | 1                                                          | 30  |
| 2                                                 | 33  | 10                                                         | 40  |
| 4                                                 | 36  | 100                                                        | 50  |
| 8                                                 | 39  | 1000                                                       | 60  |
| 16                                                | 42  | 10000                                                      | 70  |
| 32                                                | 45  | 100000                                                     | 80  |
| 64                                                | 48  | 1000000                                                    | 90  |
| 128                                               | 51  | 10000000                                                   | 100 |
**Enemy Radio Platform Watts**:_________
**Enemy Radio Platform dBm**:_____________________

## Step 2: Identify the gain on the enemy radio antenna
**Antenna Gain**:___ dBi

## Step 3: Calculate the EIRP/ERP of the enemy radio
**Enemy Radio Platform dBm** + **Antenna Gain** = ___ dBm


> [!NOTE] Next, choose Step 4 OR Step 4a
> Choose Step 4 when enemy radios are 1km or greater apart. Choose step 4a when enemy radios are less than 1km apart. 

## Step 4: Path Loss (d ≥ 1 km). Calculate enemy radio Path Loss when enemy radios are 1km or greater apart
$$
40log(DistanceInkm) + 20log(Frequency) + 32.44+ Clutter
$$

| Clutter                 |                  |
| ----------------------- | ---------------- |
| Terrain Type            | Add to Loss (dB) |
| Free Space (Air to Air) | +0 dB            |
| Rural/Open Field        | +20 dB           |
| Light Forests/Suburbs   | +30 dB           |
| Dense Forest/Urban      | +40 dB           |
**Total Loss**=___ dB

## Step 4a: Path Loss (d < 1 km). Calculate enemy radio Path Loss when enemy radios are less than 1km apart

$$
20log(DistanceInkm) + 20log(Frequency) + 32.44 + Clutter
$$

| Clutter                 |                  |
| ----------------------- | ---------------- |
| Terrain Type            | Add to Loss (dB) |
| Free Space (Air to Air) | +0 dB            |
| Rural/Open Field        | +20 dB           |
| Light Forests/Suburbs   | +30 dB           |
| Dense Forest/Urban      | +40 dB           |
**Total Loss**=___ dB

## Step 5: Calculate Received Enemy Radio Signal Strength
$$
EnemyRadioEIRP - PathLoss
$$
**Received Enemy Radio Signal Strength** = ___ dBm

> [!NOTE] Remember
> Path Loss is a single value (either 1km or greater or less than 1km.) Do not add two Path Loss values together.
> 

---
# Compare EA Platform Loss to Enemy Radio Loss

**Received Jamming Power**= ___ dBm
**Received Enemy Radio Signal Strength**= ___ dBm

**If the Received Jamming Power is 6 dB or more weaker than the Received Enemy Radio Signal Strength the jammer will have no effect.**

**If the Received Jamming Power and the Received Enemy Radio Signal Strength are within 0 to 5 dB (positive or negative), then the radio will hear "popcorn" or warbling sounds.**

**If the Received Jamming Power is 6 dB or stronger than the Received Enemy Radio Signal Strength, the enemy radio will only hear static.**

| Jamming Margin (J/S Ratio)             | Effect                                                                   |
| -------------------------------------- | ------------------------------------------------------------------------ |
| <= -6 dB<br><br>(Jammer is weaker)     | No effect<br><br>(Enemy signal captures the receiver)                    |
| -5 dB to +5 dB<br><br>(Contested Zone) | Warbling and popcorn effects<br><br>(Radio is switching between signals) |
| >= +6 dB<br><br>(Jammer is stronger)   | Complete jamming effect<br><br>(Jammer captures the receiver)            |

---
# Considerations
## Frequency Hopping
When an enemy uses frequency hopping (like SINCGARS or high-end commercial drones), you can no longer focus all your energy on one specific spot. You are forced to spread your energy across the entire "Hopping Band" to ensure you catch them wherever they land.

To calculate the penalty, you need to compare the **size of the enemy's listening ear** (Channel Bandwidth) to the **size of the area you are flooding** (Jamming Bandwidth).

$$
HoppingTax(dB) = 10log(TotalJammingBandwidth/TargetChannelWidth)
$$
### Example Calculation (The "SINCGARS" Scenario)

Let's say you are trying to jam a frequency hopping radio.

- **Your Jammer:** 20 Watts (+43 dBm).
- **The Problem:** The enemy is hopping around a **10 MHz** chunk of spectrum. You must blast noise across that whole 10 MHz to stop them.
- **The Enemy Radio:** It only listens to **25 kHz** at a time (standard narrowband voice).

**Step 1: Convert units to match**

- Jamming Width: 10 MHz = **10,000 kHz**.
- Target Width: **25 kHz**.

**Step 2: Calculate the Ratio**

$$
10,000 / 25=400
$$
_(You are spreading your power 400 times thinner than usual.)_

**Step 3: Convert to dB (The Tax)**

$$
10log(400)≈26dB
$$
**Step 4: Apply to your Link Budget**

- **Original Power:** +43 dBm (20W).
- **Hopping Tax:** -26 dB.
- **Effective Power per Channel:** **+17 dBm** (0.05 Watts).

### The Tactical Result

By switching to Frequency Hopping, the enemy effectively turned your **20 Watt** jammer into a **0.05 Watt** jammer.

If you plug **+17 dBm** into your range calculator (instead of +43), you will see your jamming range collapse from **2 km** to maybe **100 meters**.

However, if the EA Platform can effectively "follow" the frequency hopping pattern, then there is no effective loss and your full, original power is back.

## Advanced Radios
When facing advanced radios (like the Harris PRC-152/163 or the Silvus/Persistent Systems MPU5), the math changes. You aren't just fighting "power" anymore; you are fighting **algorithms**.

The **PRC-152** represents the peak of "Old School" (Hopping), while the **MPU5** represents "New School" (MANET/MIMO).
### 1. The PRC-152 Family (The "Hoppers")

_Also includes: PRC-148, PRC-117G, and similar NATO-standard radios._

These radios rely on **Secrecy and Speed**. They don't try to out-shout you; they try to hide from you in the noise.

**Key Info to Look For:**

- **Hop Rate (Hops Per Second):**
    
    - Standard SINCGARS hops ~111 times per second. Modern waveforms hop 1,000+ times per second.
    - **The Math Implication:** If your jammer is a "Follower" (Smart Jammer), it has a speed limit. If the enemy hops faster than your jammer can "listen-then-fire," your smart jammer is useless. You are forced to use **Barrage Jamming** (and accept the Hopping Tax).
        
- **The Waveform (HaveQuick / SINCGARS / HPW):**
    
    - _Voice_ (SINCGARS) is narrowband (easy to drown out if you accept the penalty).
    - _Data_ (HPW/ANW2) is wideband. **Jamming Data is easier than jamming Voice.** Data packets are fragile; if you corrupt even 10% of the packet, the radio has to re-send it. This slows their network to a crawl.

**Tactical Reality:** You probably cannot "deny" a PRC-152 completely with a 20W jammer. However, you can force them to repeat digital messages, slowing their internal processes.

### 2. The MPU5 Family (The "MANETs")

_Also includes: TrellisWare, Silvus StreamCaster._

These are fundamentally different. They are **Mobile Ad-Hoc Networks (MANET)**. Every radio is a repeater. If you jam the link between Soldier A and Soldier B the radio automatically routes the signal through other nodes.

**Key Info to Look For:**

- **MIMO (Multiple Input Multiple Output):**
    
    - The MPU5 uses **3 antennas**. It effectively _likes_ reflection. It uses the bounce off walls and trees to reconstruct the signal.
    - **The Math Implication:** The "Terrain Tax" (Clutter Loss) is **lower** for these radios. They might only lose 25 dB in a city where a Baofeng loses 40 dB. They are incredibly resilient in urban environments.
        
- **Frequency Band (L-Band / S-Band / C-Band):**
    
    - These radios usually operate at higher frequencies (1.3 GHz, 2.4 GHz, 4.4 GHz) to carry high-speed data.
    - **Vulnerability:** High frequency = High Path Loss. They rely on "Relays" (daisy-chaining).
    - **Attack Vector:** You don't jam the whole network. You jam the **"Critical Node"**—the one guy on the hill or the drone that connects the two squads. If you break the bridge, the network splits into two isolated islands.
---
# Notes on the Math Model Choices

I am deliberately choosing two different mathematical models when differentiating targets at 1km or greater vs less than 1km. In order to not over punish calculations at distances less than 1km, I am using a formula closer to free-space path loss. When accounting for targets beyond 1km, I am accounting for the two-ray ground reflection to conservatively account for path loss. 

Numerous physical and tactical factors affect real-world propagation. These models intentionally simplify these complexities to produce conservative, field-expedient estimates.

---
# Elevated Platform Considerations

This guide uses a 40 dB/decade slope appropriate for tactical ground-level propagation at targets greater than 1km. When one or both platforms are significantly elevated (>50 feet in clear terrain, or aerial platforms), actual propagation loss may follow a 20 dB/decade slope over longer distances, resulting in **greater effective range than predicted**.

For **aircraft or high-altitude drone EA platforms** in uncluttered environments, consider:

- Using 20 dB/decade slope beyond 1km
- Reducing clutter factors to 0-10 dB

The standard model remains valid for mixed scenarios (elevated jammer vs ground radios) **because ground-level reception and clutter typically dominate the overall path loss**, making it a conservative estimate.

---
# Model Validity Envelope

This planning model is most applicable under the following conditions:

- Frequencies in the VHF–UHF range typical of tactical communications
- Ground-level or near-ground emitters and receivers (≤15 m AGL), where two-ray ground effects dominate
- Engagement distances from hundreds of meters to tens of kilometers
- Terrain and clutter consistent with open, rural, or urban tactical environments
- Used for planning and comparative estimation, not precision prediction

Outside these conditions (e.g., high-altitude platforms, clear line-of-sight paths, or space-based systems), propagation loss may be less severe than predicted, and results should be treated as conservative estimates.