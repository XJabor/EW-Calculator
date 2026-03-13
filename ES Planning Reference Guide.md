The goal of this guide is to support EW operators calculating detection areas for Electronic Support operations. TUsing this guide, the operator will:

1. Estimate Enemy EIRP
2. Calculate Max Loss
3. Estimate Detection Range


> [!NOTE] IMPORTANT
> All frequencies are calculated in megahertz (MHz) and all distances are calculated in kilometers (km). Deviation from this will result in incorrect estimations. 

> [!NOTE] Friendly vs Enemy Information
> These equations take enemy and friendly capabilities into account. For brevity, only enemy information is explicitly stated as such. For example, reference to a "radio" is a friendly radio. An "enemy radio" is denoted as such.

---
## Step 1: Estimate Enemy EIRP

Use any information available or estimate based on the best analysis possible. Covert Watts into dBm (base power) and add the gain of the antenna. 

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
**Emitter Watts**: __
**Emitter dBm**:__
**Emitter Antenna Gain**:__

$$
EnyEIRP = EnemyEmitterdBm + EnemyEmitterAntennaGain
$$

**Enemy EIRP**:__

---
## Step 2: Calculate Max Loss

The Operator must know the sensitivity of their equipment in dBm. Utilize the Enemy EIRP and Equipment Sensitivity to determine Max Loss.

**Antenna Gain**:__
**Equipment Sensitivity**:__

$$
MaxLoss = EnemyEIRP + AntennaGain - EquipmentSensitivity
$$
**Max Loss**:__

---
## Step 3: Estimate Detection Range

Operators will now utilize the enemy equipment capabilities, their sensor capabilities, and the natural environmental "clutter" to estimate the detection range of the enemy emission. The final "Distance" calculation is the estimated detection range for that signal in kilometers.

| Clutter                 |                  |
| ----------------------- | ---------------- |
| Terrain Type            | Add to Loss (dB) |
| Free Space (Air to Air) | +0 dB            |
| Rural/Open Field        | +20 dB           |
| Light Forests/Suburbs   | +30 dB           |
| Dense Forest/Urban      | +40 dB           |
**Clutter**:__
**Enemy Frequency**:__
$$
Distance= 10 ^ \frac{MaxLoss - 20 \log(EnemyFrequency) - 32.44 - Clutter}{40}
$$

**Distance**:__ 