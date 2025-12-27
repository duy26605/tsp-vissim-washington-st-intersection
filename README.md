# Transit Signal Priority (TSP) Evaluation in VISSIM  
### Washington St – Bowdoin St – Harvard St Intersection, Boston, MA

This repository presents a microsimulation-based evaluation of **Transit Signal Priority (TSP)** strategies implemented using **PTV VISSIM** and **Vehicle Actuated Programming (VAP)**.  
The study compares a **base actuated signal control** with two TSP alternatives to assess impacts on **bus delay** and **overall vehicle delay** under **peak and non-peak traffic conditions**.

---

## 📌 Project Objectives

- Implement an **8-phase NEMA dual-ring actuated controller**
- Design and test **Transit Signal Priority (TSP)** strategies
- Compare:
  - Base Case (No TSP)
  - Green Extension (GE)
  - Green Extension with Phase Rotation (GE + PR)
- Evaluate performance under **peak and non-peak demand**
- Quantify impacts on:
  - Average delay for all vehicles
  - Average delay for buses

---

## 📍 Study Location

- **Intersection:** Washington Street – Bowdoin Street – Harvard Street  
- **City:** Boston, Massachusetts  
- **Context:** Urban arterial with frequent bus service and mixed traffic

---

## 🚦 Signal Control Strategies

### 1. Base Case (No TSP)
- Fully actuated **8-phase NEMA dual-ring controller**
- Major street through movements operate under recall
- Standard max-green and gap-out logic

### 2. TSP Alternative 1 — Green Extension (GE)
- Applied to major street through phases
- When a bus is detected near the end of green:
  - Green extends up to **+10 seconds**
  - Extension ends early if the bus clears the intersection

### 3. TSP Alternative 2 — Green Extension + Phase Rotation (GE + PR)
- Includes Green Extension logic
- Adds **phase rotation at the barrier**:
  - Through movement is served before left-turn when a bus is present
  - Prevents buses from waiting through a full left-turn phase

---

## 📊 Traffic Demand and Bus Modeling

### Vehicle Demand
- Turning movement counts collected over 20 minutes
- Scaled to hourly volumes
- **Non-peak demand = 60% of peak volumes**

### Bus Arrivals
- Mean headway ≈ **8 minutes**
- Bus arrivals generated using Python
- Separate arrival streams for northbound and southbound buses

---

## 📈 Key Results

### Non-Peak Conditions

| Control Strategy | Avg Delay (All Vehicles) | Avg Delay (Buses) |
|------------------|--------------------------|-------------------|
| Base Case        | 18.51 s/veh              | 24.73 s/bus      |
| Green Extension | 24.02 s/veh              | 16.85 s/bus      |
| GE + Phase Rotation | **16.47 s/veh** | **8.09 s/bus** |

**Key Observations**
- Green Extension reduces bus delay but increases general vehicle delay
- GE + Phase Rotation provides the **lowest delays for both buses and all vehicles**

---

### Peak Conditions

| Control Strategy | Avg Delay (All Vehicles) | Avg Delay (Buses) |
|------------------|--------------------------|-------------------|
| Base Case        | 26.80 s/veh              | 27.11 s/bus      |
| Green Extension | 26.59 s/veh              | 28.02 s/bus      |
| GE + Phase Rotation | **23.48 s/veh** | **11.13 s/bus** |

**Key Observations**
- Green Extension alone is ineffective during peak congestion
- GE + Phase Rotation achieves:
  - ~59% reduction in bus delay relative to the base case
  - Lower overall vehicle delay despite prioritizing transit

---

## 🧪 Simulation Environment

- **Software:** PTV VISSIM
- **Controller:** Vehicle Actuated Programming (VAP)
- **Execution Frequency:** 10 Hz
- **Verification:** Dummy signal groups used to visualize:
  - Bus detection
  - Active TSP state
  - Green extension
  - Phase rotation behavior


