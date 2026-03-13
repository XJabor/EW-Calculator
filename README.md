# EW Planning Calculator
An Android app for Electronic Warfare operators to quickly calculate detection areas and jamming effectiveness in the field. Wraps a self-contained HTML/JS calculator in a native Android WebView. The PDFs can be used by by-hand calculations and the HTML file is the same calculator without the Android requirement. 

## Calculators
   
  ### Electronic Attack (EA)
  Determines whether a jammer has sufficient power to overpower an enemy radio at a target location.
   
  **Inputs:**
  - EA platform power (Watts or dBm) and antenna gain → EIRP
  - Optional frequency hopping tax (total jamming bandwidth vs. target channel width)
  - Jammer-to-target distance, frequency, and terrain type → path loss and received jamming power
  - Enemy radio power, antenna gain, distance, frequency, and terrain type → received enemy signal strength
  
  **Output:** Jamming margin (J/S ratio in dB) with effect assessment:
  | Margin | Effect |
  |---|---|
  | ≤ −6 dB | No Effect — enemy signal captures the receiver |
  | −6 to +6 dB | Partial Effect — warbling / popcorn sounds |
  | ≥ +6 dB | Complete Jamming — jammer captures the receiver |
  
  ### Electronic Support (ES)
  Estimates the maximum range at which a sensor can detect an enemy emission.
  
  **Inputs:**
  - Enemy emitter power (Watts or dBm) and antenna gain → enemy EIRP
  - Sensor antenna gain and equipment sensitivity → max loss
  - Enemy frequency and terrain type
  
  **Output:** Estimated detection range in kilometers
  
  ## Notes
  
  - All frequencies must be entered in **MHz**
  - All distances must be entered in **km**
  - Path loss model is selected automatically: 20 dB/decade for distances < 1 km, 40 dB/decade for ≥ 1 km
  - Watts and dBm fields are bidirectional — enter either one and the other updates automatically

  ## Requirements
  - Android 10 (API 29) or higher
  - A calculator for using the guides by hand

# Disclaimer
These guides and applications were built heavily with AI. These models are used as a conservative estimates. Use these calculators at your own risk.
