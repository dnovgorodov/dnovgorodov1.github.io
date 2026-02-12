# Component Selection

---

# **Power Input Subsystem – DC Barrel Jack**

## Design Requirements Considered

- Surface-mount required (EGR 314 constraint)
- Must support expected input voltage (5–12V assumed)
- Must support ≥1A current
- Mechanically robust for repeated insertion
- Available from reputable supplier with datasheet

---

## Potential Solutions

### Table 1 – DC Barrel Jack Options

| Option | Part Number | Mount Type | Current Rating | Approx. Cost | Pros | Cons |
|--------|------------|------------|----------------|--------------|------|------|
| 1 | CUI PJ-102AH | Through-hole | 2A | ~$0.60 | Low cost; strong mechanical retention; widely used | Not surface mount; violates EGR 314 requirement |
| 2 | CUI PJ-102A-SMT | Surface mount | 2A | ~$1.00 | Meets surface mount requirement; sufficient current rating; compact footprint | Slightly weaker mechanical strength than through-hole; requires careful PCB footprint |
| 3 | Switchcraft RAPC722X | Surface mount | 3–5A | ~$2–3 | High durability; higher current capacity; industrial quality | More expensive; over-specified for low-power system |

---

## Selected Component  
**CUI PJ-102A-SMT**

### Rationale

The PJ-102A-SMT satisfies the surface-mount requirement while providing sufficient current capacity (2A) for the system. It balances cost, mechanical reliability, and electrical performance. The industrial-grade Switchcraft option is unnecessarily expensive and exceeds system needs, while the through-hole option violates course constraints.

---

# **Power Regulation Subsystem – 3.3V Supply**

## Design Requirements Considered

- Must supply stable 3.3V
- Must handle ESP32 current spikes (~400–500mA during Wi-Fi transmission)
- Surface mount only
- Efficient thermal performance
- Reliable under dynamic load

---

## Potential Solutions

### Table 2 – 3.3V Regulation Options

| Option | Part Number | Type | Max Current | Efficiency | Approx. Cost | Pros | Cons |
|--------|------------|------|------------|------------|--------------|------|------|
| 1 | AMS1117-3.3 | Linear Regulator | 800mA | Low (~50–60%) | ~$0.30 | Very simple design; inexpensive; widely available | Poor efficiency; significant heat if Vin >5V; marginal under Wi-Fi current spikes |
| 2 | AP2112K-3.3 | LDO Regulator | 600mA | Moderate | ~$0.70 | Low dropout voltage; stable regulation; small SMD package | Still inefficient at higher Vin; limited current margin |
| 3 | MP1584 | Buck (Switching) Regulator | >2A | High (~85–95%) | ~$1–2 | High efficiency; low heat; wide input range; handles transient current well | More complex design; requires inductor and layout care; switching noise |

---

## Selected Component  
**MP1584 Buck Converter**

### Rationale

The ESP32 exhibits high transient current draw during Wi-Fi and Bluetooth transmission. A linear regulator would dissipate excessive heat when stepping down from 9–12V input, potentially causing thermal instability. The MP1584 switching regulator provides high efficiency, significantly reduced thermal stress, and sufficient current headroom. Although more complex to implement, it provides superior reliability and power integrity for the system.

---

# **External Interface Subsystem – 4×2 Connector**

## Design Requirements Considered

- Surface-mount only
- Reliable mechanical retention
- Standard 2.54mm pitch compatibility
- Supports programming/debugging interface
- Prevent accidental reverse insertion

---

## Potential Solutions

### Table 3 – 4×2 Connector Options

| Option | Type | Mount | Approx. Cost | Pros | Cons |
|--------|------|-------|--------------|------|------|
| 1 | 2×4 Pin Header (Unshrouded) | Through-hole | ~$0.20 | Very low cost; common; easy to prototype | Not surface mount; no polarity protection |
| 2 | 2×4 SMD Header | Surface mount | ~$0.50 | Meets SMD requirement; compatible with standard cables; compact | No keying; lower mechanical retention than shrouded version |
| 3 | 2×4 Shrouded Box Header (SMD) | Surface mount | ~$1–2 | Keyed insertion; improved mechanical stability; professional appearance | Higher cost; larger PCB footprint |

---

## Selected Component  
**2×4 Shrouded Surface-Mount Box Header**

### Rationale

The shrouded SMD connector prevents incorrect cable insertion, improving system robustness and protecting the ESP32 from accidental miswiring. Although slightly more expensive, the improved reliability and professional integration justify the added cost. The through-hole header violates the surface-mount requirement and is therefore unsuitable.

---

# **Microcontroller Subsystem – ESP32**

*(Completed separately per assignment requirements.)*

---

# Final Component Selection Summary

| Subsystem | Selected Component | Justification |
|------------|------------------|--------------|
| **Power Input** | CUI PJ-102A-SMT | Surface mount compliant; sufficient current capacity; cost-effective |
| **Voltage Regulation** | MP1584 Buck Converter | Efficient; handles ESP32 transient loads; reduces thermal stress |
| **External Interface** | 2×4 Shrouded SMD Header | Keyed; robust; surface mount compliant |
| **Microcontroller** | ESP32 | Integrated Wi-Fi and Bluetooth; eliminates external modules |
