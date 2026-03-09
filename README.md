# Adaptive Smart Hospital Multi-Agent System (MAS)

A simulation-based **Adaptive Smart Hospital Resource Coordination System** built in **AnyLogic**.  
The project models hospital operations using a **multi-agent architecture** where patients, staff, equipment, and hospital infrastructure interact to simulate patient flow, resource allocation, and operational performance.

The system focuses on analyzing hospital dynamics such as **waiting times, bed occupancy, and staff utilization** under different scenarios.

---

# Project Overview

Hospitals are complex systems involving multiple interacting agents including patients, doctors, nurses, and medical equipment. Efficient coordination of these agents is essential to maintain service quality and minimize delays.

This project implements a **Multi-Agent System (MAS)** in AnyLogic to simulate hospital workflows including:

- Patient arrival and triage
- Resource allocation to medical staff
- Equipment utilization
- Bed allocation
- Scenario-based hospital demand simulations

The model allows testing how hospital performance changes under different load conditions.

---

# Current Project Status

This project was implemented **individually** as part of a Multi-Agent Systems course project.

### Implemented Features

- Multi-agent hospital environment
- Patient lifecycle simulation
- Doctor and nurse agents
- Equipment and bed resources
- Patient arrival and triage system
- Basic resource assignment based on doctor schedules
- Scenario controls for different hospital loads
- Data logging for simulation metrics

### Not Implemented / Simplified

The following planned components were **not implemented** or are simplified:

- No **Reinforcement Learning or AI optimization**
- No **external ML integration (Python / ONNX)**
- No **advanced auction-based task allocation**
- Doctor assignment uses **simple schedule-based bidding logic**
- No **3D models or animations**
- UI visualizations are minimal
- Limited scenario experimentation

---

# Simulation Architecture

The model follows a **multi-agent architecture**.

Main agent types include:

| Agent | Description |
|------|-------------|
| Patient | Represents individuals entering the hospital system |
| Staff | Base class for hospital personnel |
| Doctor | Performs consultations and procedures |
| Nurse | Assists with triage and patient monitoring |
| Equipment | Medical equipment such as MRI or CT scanners |
| Room / Bed | Hospital rooms and bed resources |
| Main | Root simulation controller |

---

# System Structure

AnyLogicProject/
Main (root agent)

agents/
Patient.agent
Staff.agent
Doctor.agent
Nurse.agent
Specialist.agent
Equipment.agent
Room.agent

resources/
ResourcePools

experiments/
Simulation

data/
arrival_profiles.csv
los_distributions.csv

docs/
README.md
run_instructions.md


---

# Patient Lifecycle

The patient agent follows a state-based lifecycle:

```
Arriving → Triage → Waiting → InService → PostCare → Discharged
```

Key steps:

1. Patient arrives (walk-in or ambulance)
2. Triage determines urgency
3. Patient waits for available staff
4. Doctor provides treatment
5. Post-treatment care
6. Patient discharge

---

# Staff Behaviour

Staff agents include doctors and nurses.

They operate according to shift schedules and availability states.

Staff Statechart:

```
OffDuty → OnShift → Busy → OnBreak
```

Doctors can:

- consult patients
- perform procedures
- update treatment outcomes

---

# Resource Management

Hospital resources include:

- Doctors
- Nurses
- Beds
- MRI / CT scanners
- Operating rooms

Resources are modeled using **AnyLogic ResourcePools** and allocated dynamically when patients require service.

---

# Task Allocation

The system currently uses a **simplified bidding mechanism**.

Doctors respond to patient treatment requests based on:

- availability
- schedule
- workload

This approach loosely follows the concept of **Contract Net Protocol**, but does not implement a full auction or negotiation process.

---

# Example Data Inputs

### Patient Arrival Profiles

```
time,arrival_rate
0,2
3600,3
7200,5
```

### Length of Stay Distributions

```
department,distribution_type,params
ED,exponential,mean=2.0
OR,lognormal,mean=3.0,sd=0.5
```

---

# Simulation Scenarios

The model supports different hospital demand scenarios:

- Normal operation
- High demand
- Emergency surge

These scenarios modify:

- patient arrival rates
- resource utilization
- system load

---

# Key Metrics

The simulation tracks operational performance indicators:

- Average patient waiting time
- Bed occupancy rate
- Staff utilization
- Patient throughput
- Treatment completion time

---

# Running the Model

### Requirements

- AnyLogic Personal Learning Edition or University License
- Java (included with AnyLogic)

### Steps

1. Clone the repository

```bash
git clone https://github.com/ShreenathKR2000/adaptive-smart-hospital-MAS.git
```
2. Open the project in AnyLogic

3. Run the Simulation experiment

4. Adjust scenario parameters from the UI controls

# Learning Resources Used

The project design was inspired by official AnyLogic healthcare examples:

- Emergency Department resilience models
- Hospital Digital Twin demonstrations
- Maternity Ward operations simulation
- Simple Hospital AI testbed examples
- Orthopedics waiting-list discrete event models

Official resources:
https://www.anylogic.com

# Future Improvements

Potential extensions for this project include:

- Reinforcement Learning for dynamic resource allocation
- Python / ONNX integration for prediction models
- Full Contract Net Protocol implementation
- Auction-based resource allocation
- Advanced visualization dashboards
- 3D hospital environment
- More detailed patient treatment pathways

# License

This project is for academic and research purposes only.
