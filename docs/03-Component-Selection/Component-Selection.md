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

| Option | Part Number & Link | Mount Type | Current Rating | Approx. Cost | Pros | Cons |
|--------|------------------|------------|----------------|--------------|------|------|
| 1 | [CUI PJ-102A-SMT](https://www.mouser.com/ProductDetail/CUI/PJ-102A-SMT) ![PJ-102A-SMT](https://www.mouser.com/images/cui/pj102a-sm.png) | Surface mount | 2A | ~$1.00 | Meets surface mount requirement; sufficient current rating; compact footprint | Slightly weaker mechanical strength than through-hole; requires careful PCB footprint |
| 2 | [Switchcraft RAPC722X](https://www.switchcraft.com/product/rapc722x) ![RAPC722X](https://www.switchcraft.com/sites/default/files/products/rapc722x.jpg) | Surface mount | 3–5A | ~$2–3 | High durability; higher current capacity; industrial quality | More expensive; over-specified for low-power system |
| 3 | [CUI PJ-102AH](https://www.mouser.com/ProductDetail/CUI/PJ-102AH) ![PJ-102AH](https://www.mouser.com/images/cui/pj102ah.png) | Through-hole | 2A | ~$0.60 | Low cost; strong mechanical retention; widely used | Not surface mount; violates class requirement |

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

| Option | Part Number & Link | Type | Max Current | Efficiency | Approx. Cost | Pros | Cons |
|--------|------------------|------|------------|------------|--------------|------|------|
| 1 | [AMS1117-3.3](https://www.digikey.com/en/products/detail/advanced-monolithic-systems/AMS1117-3-3/1914023) ![AMS1117](https://www.digikey.com/Photos/AMS1117.jpg) | Linear Regulator | 800mA | Low (~50–60%) | ~$0.30 | Very simple design; inexpensive; widely available | Poor efficiency; significant heat if Vin >5V; marginal under Wi-Fi current spikes |
| 2 | [AP2112K-3.3](https://www.digikey.com/en/products/detail/Diodes-Incorporated/AP2112K-3-3TRG1/1917197) ![AP2112K](https://www.digikey.com/Photos/AP2112K.jpg) | LDO Regulator | 600mA | Moderate | ~$0.70 | Low dropout voltage; stable regulation; small SMD package | Still inefficient at higher Vin; limited current margin |
| 3 | [MP1584EN Buck Module](https://hobbymatehobby.com/products/mini-mp1584en-dc-dc-buck-adjustable-step-down-module-4-5v-28v-input-0-8v-20v-output) ![MP1584](https://cdn.shopify.com/s/files/1/0253/1554/8289/products/MP1584-Module-2.jpg) | Buck (Switching) | >2A | High (~85–95%) | ~$1–2 | High efficiency; low heat; wide input range; handles transient current well | More complex design; requires inductor and layout care; switching noise |

---

## Selected Component  
**MP1584EN Buck Converter**

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

| Option | Part Number & Link | Mount | Approx. Cost | Pros | Cons |
|--------|------------------|-------|--------------|------|------|
| 1 | [2×4 Shrouded Box Header 2mm](https://www.ebay.ca/itm/314896057579) ![2x4 Shrouded](https://i.ebayimg.com/images/g/xyz/s-l1600.jpg) | SMD | ~$1.25 | Keyed insertion; improved mechanical stability; professional appearance | Requires careful soldering |
| 2 | [2×4 SMD Header](https://www.digikey.com/en/products/detail/TE-Connectivity-AMP/1-215850-0/2627896) ![2x4 SMD](https://www.digikey.com/Photos/TEConnectivity/1215850-0.jpg) | SMD | ~$0.50 | Meets SMD requirement; compatible with standard cables; compact | No keying; lower mechanical retention than shrouded version |
| 3 | [2×4 Pin Header Unshrouded](https://www.digikey.com/en/products/detail/TE-Connectivity-AMP/1-215848-0/2627895) ![2x4 Unshrouded](https://www.digikey.com/Photos/TEConnectivity/1215848-0.jpg) | Through-hole | ~$0.20 | Very low cost; common; easy to prototype | Not surface mount; no polarity protection |

---

## Selected Component  
**2×4 Shrouded Surface-Mount Box Header**

### Rationale

The shrouded SMD connector prevents incorrect cable insertion, improving system robustness and protecting the ESP32 from accidental miswiring. Although slightly more expensive, the improved reliability and professional integration justify the added cost. The through-hole header violates the surface-mount requirement and is therefore unsuitable.

---

# **Microcontroller Subsystem – ESP32**

---

# Final Component Selection Summary

| Subsystem | Selected Component | Justification |
|------------|------------------|--------------|
| **Power Input** | [CUI PJ-102A-SMT](https://www.mouser.com/ProductDetail/CUI/PJ-102A-SMT) | Surface mount compliant; sufficient current capacity; cost-effective |
| **Voltage Regulation** | [MP1584EN Buck Module](https://hobbymatehobby.com/products/mini-mp1584en-dc-dc-buck-adjustable-step-down-module-4-5v-28v-input-0-8v-20v-output) | Efficient; handles ESP32 transient loads; reduces thermal stress |
| **External Interface** | [2×4 Shrouded Box Header 2mm](https://www.ebay.ca/itm/314896057579) | Keyed; robust; surface-mount compliant |
| **Microcontroller** | ESP32 | Integrated Wi-Fi and Bluetooth; eliminates external modules |
