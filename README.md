# DALI_GAIA_example

Example of a DALI multi-agent system project designed according to the GAIA methodology guidelines.

Title: __Multi-Agent System for Emergency Management in a Smart Building__

## Objective
Design and implement a multi-agent system in the [DALI](https://github.com/AAAI-DISIM-UnivAQ/DALI) language for the detection and coordinated management of emergency events (e.g., fire, gas leak, earthquake) inside a smart building, following the **GAIA methodology**.

---

## Phase 1: Design according to the GAIA Methodology

### 1.1 Roles

| Role         | Main Responsibilities                                     |
|--------------|-----------------------------------------------------------|
| **Sensor**   | Detects environmental anomalies (smoke, gas, tremors).    |
| **Coordinator** | Evaluates the severity of events and decides on a plan. |
| **Evacuator**| Guides occupants to safe exits.                           |
| **Logger**   | Records all events, actions, and system status.           |

---

### 1.2 Virtual Organization

- **Name**: `EmergencyManagementSystem`
- **Goals**:
  - Minimize risks to people and infrastructure.
  - Ensure prompt and coordinated reaction to emergencies.
  - Support distributed decision-making among agents.
- **Roles and Interactions**:
  - `Sensor → Coordinator`: sends alarm messages.
  - `Coordinator → Evacuator`: sends evacuation commands.
  - `All → Logger`: record of all relevant events and actions.

---

### 1.3 Event Table

#### Sensor

| Event                | Type     | Source      |
|----------------------|----------|-------------|
| `detect_smoke`        | external | environment |
| `detect_gas`          | external | environment |
| `detect_earthquake`   | external | environment |

#### Coordinator

| Event                | Type     | Source      |
|----------------------|----------|-------------|
| `alarm(smoke)`        | external | Sensor      |
| `alarm(gas)`          | external | Sensor      |
| `alarm(earthquake)`   | external | Sensor      |
| `evacuation_done`     | external | Evacuator   |

---

### 1.4 Action Table

#### Evacuator

| Action                      | Description                                 |
|-----------------------------|---------------------------------------------|
| `guide_people_to_exit(X)`   | Guides people to exit `X` safely            |
| `report(evacuation_done)`   | Notifies the Coordinator that evacuation is complete |

---

### 1.5 Agent Behaviors

- **Sensor**: reactive; generates alarms upon detecting anomalies.
- **Coordinator**: reactive to incoming alarms; proactive in managing the response strategy.
- **Evacuator**: reactive to evacuation commands; can report issues or confirmation.
- **Logger**: reactive; logs every received message or command.

---
