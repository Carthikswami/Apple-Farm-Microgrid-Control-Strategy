# Apple Farm Agrivoltaic Microgrid – EMS Control Strategy

This repository documents the design of a microgrid control strategy for an agrivoltaic deployment at a commercial apple farm. The system supports both photovoltaic generation and controlled-environment agriculture (CEA) loads while operating on a constrained distribution feeder with strict import and export limits.

The Energy Management System (EMS) developed for this project coordinates a hybrid PV–battery architecture to prioritize self-consumption, minimize clipping, and stagger inverter output under real-time feeder constraints.

---

## Control Strategy Objectives

- Operate under strict non-export or export-limited conditions on a rural feeder.
- Prevent inverter clipping by staggering PV output relative to irradiance and load transitions.
- Coordinate battery charging and discharging to absorb surplus production and reduce grid imports during high demand.
- Support CEA operations (pumps, climate control, storage refrigeration) through demand-response scheduling.
- Provide a scalable and repeatable control template for agrivoltaic microgrids with high PV penetration.

---

## Microgrid Architecture (Overview)

The control strategy assumes a hybrid inverter and battery system where:

- PV inverters operate in a **priority-limited output mode** based on irradiance and feeder headroom.
- The battery absorbs surplus generation during mid-day and discharges during load peaks.
- CEA and farm-related loads respond to demand response signals based on environmental and operational conditions.
- Non-export constraints override all operating modes, forcing discharge suppression or diversion to site loads.

This architecture supports both PV generation and real-time farm operations without exceeding feeder constraints.

---

## EMS Control Logic

The EMS control framework includes:

| Decision Layer | Function |
|----------------|----------|
| Inverter Sequencing | Staggers PV output based on irradiance forecast and real-time feeder limits |
| Battery Dispatch | Absorbs surplus PV; discharges to offset imports when headroom is low |
| Load Coordination | Prioritizes CEA operations based on environmental risk and energy cost |
| Export Limit Enforcement | Caps inverter output based on allowable export capacity |

The logic is based on irradiance-driven switching, site-specific demand windows, and feeder headroom thresholds.

The `control-logic/` directory contains state diagrams and rule sets illustrating key transitions.

---

