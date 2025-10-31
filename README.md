# Impact of Level 2 Residential EV Charging on Urban Distribution Feeders

## Project Overview
This repository contains OpenDSS simulation code for analyzing the impact of residential electric vehicle (EV) charging on urban distribution network infrastructure. 
The study quantifies voltage regulation and transformer loading impacts across multiple EV penetration scenarios using the IEEE 13-node test feeder as the base model.

#### Author: Varun Kaukuntla
#### Institution: University of Technology Sydney (UTS
#### Course: 41029 Engineering Research Preparation
#### Supervisor: Prof. Li Li

## Research Objectives
- Establish baseline electrical characteristics of IEEE 13-node distribution system adapted for Australian context
- Quantify voltage regulation impacts at critical system buses for 10%, 30%, and 50% EV penetration levels
- Assess transformer loading progression under increasing EV penetration scenarios
- Analyze voltage regulator behavior and capacity constraints during peak EV charging periods
- Identify critical infrastructure threshold points for distribution system planning

## Model Specifications

### System Configuration
- **Network Model:** Modified IEEE 13-node test feeder
- **Frequency:** 50 Hz (Australian standard)
- **Voltage Levels**:
  - Primary distribution: 4.16 kV
  - Secondary distribution: 480V (residential)
  - Single-phase residential: 277V (0.48 kV / √3)
- **Key Transformer:** XFM1 (500 kVA, 4.16kV → 480V, Bus 633 → Bus 634)
- **Voltage Regulation:** Three-phase regulator bank (Reg1, Reg2, Reg3) at Bus 650 → RG60

### EV Charging Parameters
- **Charger Type:** Level 2 residential chargers
- **Power Rating:** 7.2 kW per EV
- **Voltage:** 240V single-phase
- **Power Factor:** 0.95 lagging
- **Connection Point:** Bus 634 (low voltage residential area)

### Penetration Scenarios
- **Base Case:** No EV loads
- **10% Penetration:** 2 EVs (14.4 kW total)
- **30% Penetration:** 6 EVs (43.2 kW total)
- **50% Penetration:** 12 EVs (72.0 kW total)

### Monitoring Points
- **Critical Buses:** 611, 633, 634, 652
- **Transformer:** XFM1 loading (kVA and % of rated capacity)
- **Voltage Regulators:** Tap positions (Reg1, Reg2, Reg3)
- **Analysis Period:** 24-hour daily cycle with 1-hour time steps

## Key Findings

### Voltage Regulation
- Minimal direct voltage variations (<0.4%) across all EV penetration levels
- Voltage regulators operate at maximum capacity (1.050 pu) across all scenarios including base case
- Voltage regulation capacity exhaustion identified as primary infrastructure constraint
- No voltage standard violations observed (all buses maintained above 0.94 pu)

### Transformer Loading
- **Base Case:** 2.39% peak loading (Hour 19)
- **10% EV:** 5.42% peak loading (+127% increase)
- **30% EV:** 11.48% peak loading (+381% increase)
- **50% EV:** 20.60% peak loading (+762% increase)

### Average Daily Loading
- **Base Case:** 1.59%
- **50% EV:** 8.29% (5.2x increase)

## Repository Structure
```
├── IEEE13_EV_Analysis.dss          # Main OpenDSS simulation file
├── README.md                        # This file
└── /results.csv                     # Simulation output data
    ├── voltage_profiles
    ├── transformer_loading
    └── regulator_tap_positions
```

## How to Run

### Prerequisites
- OpenDSS software (https://www.epri.com/pages/sa/opendss)
- Python (optional, for data analysis and visualization)

### Running the Simulation
1. Clone this repository
2. Open OpenDSS
3. Load the `IEEE13_EV_Analysis.dss` file
4. Run the simulation using:
   ```
   Set Mode=Daily
   Set Number=24
   Set Stepsize=1h
   Solve
   ```
5. Export results using OpenDSS monitor and export commands
6. Analyze results using spreadsheet software or Python

### Modifying EV Penetration Levels
To test different EV penetration scenarios, modify the EV load definitions in the DSS file:
- Comment/uncomment EV load sections for 10%, 30%, or 50% scenarios
- Adjust the number of EV loads and their placement as needed

## Results and Analysis
Detailed analysis of simulation results, including:
- Voltage profile plots for all critical buses
- Transformer loading comparisons across penetration levels
- Voltage regulator tap position correlations
- Statistical analysis of infrastructure impacts

Full research report and detailed findings available in the associated research paper.

## Technical Notes
- All EV loads concentrated at Bus 634 (worst-case localized scenario)
- Uncoordinated charging with evening peak coincidence
- Steady-state power flow analysis (excludes transients and harmonics)
- Australian voltage standards applied (AS60038: ±6% tolerance, 0.94-1.06 pu)

## License
This code is provided for educational and research purposes.

## Acknowledgments
- Supervisor: Prof. Li Li
- Modified IEEE 13-node test feeder specifications from IEEE PES Test Feeders
- OpenDSS simulation platform by EPRI

## Citation
If you use this code in your research, please cite:
```
Kaukuntla, V. (2025). Impact of Level 2 Residential EV Charging on Urban Distribution Feeders. 
Engineering Research Preparation, University of Technology Sydney.
```

**Last Updated:** October 2025
