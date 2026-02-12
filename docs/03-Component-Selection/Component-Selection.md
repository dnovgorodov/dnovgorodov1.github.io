# Component Selection

---

# **Power Input Subsystem – DC Barrel Jack**

## Design Requirements Considered

- Surface‑mount required (EGR 314 constraint)
- Must support expected input voltage (5–12 V)
- Must support sufficient current (≥1 A)
- Mechanically robust and documented

---

## Potential Solutions

### Table 1 – DC Barrel Jack Options

| Option | Image | Purchase Link | Mount Type | Current Rating | Cost | Pros | Cons |
|--------|-------|---------------|------------|----------------|--------------|------|------|
| 1 | ![PJ‑068B‑SMT‑TR](https://mm.digikey.com/Volume0/opasdata/d220001/derivates/1/010/135/851/MFG_PJ-068B-SMT_sml.jpg) | [PJ-068B-SMT-TR](https://www.digikey.com/en/products/detail/same-sky-formerly-cui-devices/PJ-068B-SMT-TR/2625163) | Surface mount | ~1–2 A | ~$2.04 | Meets surface‑mount requirement; wide range of center pin sizes available | Requires careful footprint design |
| 2 | ![PJ-102AH](https://mm.digikey.com/Volume0/opasdata/d220001/derivates/1/001/194/517/MFG_PJ-102AH_sml%28200x200%29.jpg) | [PJ-102AH](https://www.digikey.com/en/products/detail/same-sky-formerly-cui-devices/PJ-102AH/408448) | Through-hole | ~1 A typical | ~$0.80–$1.37 | Large variety of SMT DC jacks available; multiple pinout/pitch options | Must select correct center/outer diameter; pin spacing varies |
| 3 | ![PJ-002BH-SMT-TR](https://mm.digikey.com/Volume0/opasdata/d220001/derivates/1/001/165/469/PJ-002BH-SMT_sml.jpg) | [PJ-002BH-SMT-TR](https://www.digikey.com/en/products/detail/same-sky-formerly-cui-devices-/PJ-002BH-SMT-TR/669694) | Surface mount | ~1–2 A typical | Varies | Many options available; datasheets provided | Higher searching effort to match specs |

---

## Selected Component  
**PJ‑068B‑SMT‑TR DC Power Jack**

### Rationale

The PJ‑002BH‑SMT‑TR is a surface‑mount barrel jack, which makes it easy to place on a PCB and ideal for automated assembly. Its compact, low‑profile design saves board space, and it matches the required power plug size and ratings, providing reliable mechanical and electrical connections.

---

# **Power Regulation Subsystem – 3.3 V Supply**

## Design Requirements Considered

- Must provide stable 3.3 V
- Must handle ESP32 transient current draw (~400–500 mA)
- Surface‑mount regulator preferred
- Efficient and low heat

---

## Potential Solutions

### Table 2 – 3.3 V Regulation Options

| Option | Image | Purchase Link | Mount Type | Max Current | Approx. Cost | Pros | Cons |
|--------|-------|---------------|------|--------------|--------------|------|------|
| 1 | ![LD1117V33](https://mm.digikey.com/Volume0/opasdata/d220001/derivates/1/300/415/110/497%7ETO220-3TO220AB%7E%7E3_sml.jpg) | [LD1117V33](https://www.digikey.com/en/products/detail/stmicroelectronics/LD1117V33/586012) | Through-hole | ~1.5 A | ~$2.63 | High efficiency; suitable current for ESP32 | Requires external inductor and IC layout care |
| 2 | ![TLV75733PDBVR](https://mm.digikey.com/Volume0/opasdata/d220001/derivates/1/002/172/168/296%7E4214839%7EDBV%7E5__sml%28200x200%29.jpg) | [TLV75733PDBVR](https://www.digikey.com/en/products/detail/texas-instruments/TLV75733PDBVR/9685553) | Surface mount | ~1.5 A | ~$2.63 | Common in professional designs; good documentation | External components needed |
| 3 | ![TC1264-3.3VDB](https://mm.digikey.com/Volume0/opasdata/d220001/derivates/1/020/996/308/150%7EC04-032%7EDB%7E4_sml.jpg) | [TC1264-3.3VDB](https://www.digikey.com/en/products/detail/microchip-technology/TC1264-3.3VDB/964315) | Surface mount | Varies | ~$1.30–$3.00 | Many SMD options exist with similar performance | Must ensure sufficient current headroom |

---

## Selected Component  
**Texas Instruments TPS62111RSAR 3.3 V Buck Regulator IC**

### Rationale

The TPS62111RSAR is a dedicated surface‑mount buck regulator with adequate current capacity and excellent efficiency. Its SMD package and integrated design simplify PCB routing and thermal performance, making it a strong choice for delivering stable 3.3 V to the ESP32 on a custom board.

---

# **External Interface Subsystem – 4×2 Connector**

## Design Requirements Considered

- Surface mount preferred (EGR 314)
- Typical 0.1 in (2.54 mm) pitch for standard programming cables
- Reliable mechanical retention

---

## Potential Solutions

### Table 3 – 4×2 Connector Options

| Option | Image | Purchase Link | Mount | Approx. Cost | Pros | Cons |
|--------|-------|---------------|-------|--------------|------|------|
| 1 | ![DF13C-8P](https://media.digikey.com/Photos/HiroseElectricCoLtd/DF13C‑8P‑1.25V(51).jpg) | **:contentReference[oaicite:4]{index=4}** | Surface mount | ~$1.36 | Industry quality; board‑to‑cable connection | 1.25 mm pitch (not 2.54 mm) — verify matching cable |
| 2 | ![CNC Tech 8pos](https://via.placeholder.com/60?text=8pos+Header) | **:contentReference[oaicite:5]{index=5}** | Surface mount | ~$0.81 | Standard 2.54 mm pitch; easy to find mating cable | Unshrouded; no polarity/keying |
| 3 | ![TE Connectivity 8pos](https://via.placeholder.com/60?text=8pos+Header) | **:contentReference[oaicite:6]{index=6}** | Surface mount | ~$0.97 | Standard pitch; compact board footprint | Unshrouded; check cable alignment |

---

## Selected Component  
**Hirose Electric DF13C‑8P‑1.25V(51) SMD Header (or equivalent shrouded 8‑pos if required)**

### Rationale

The 8‑position surface‑mount header provides a standard interface for programming and external connections. While the Hirose part is high quality, choose a header with shrouding and matching pitch to your cable — e.g., 2.54 mm if that’s your target pitch. Digi‑Key and Mouser offer multiple SMD headers with various pitch and shroud options. :contentReference[oaicite:7]{index=7}

---

# **Microcontroller Subsystem – ESP32**

---

# Final Component Selection Summary

| Subsystem | Selected Component | Justification |
|------------|------------------|--------------|
| **Power Input** | **:contentReference[oaicite:8]{index=8}** | Surface‑mount compliant; documented DC jack selection; supports ~1–2 A |
| **Voltage Regulation** | **:contentReference[oaicite:9]{index=9}** | Efficient surface‑mount regulator with adequate current for ESP32 |
| **External Interface** | **:contentReference[oaicite:10]{index=10}** | Reliable header; choose correct pitch/shroud per cable |
| **Microcontroller** | ESP32 | Integrated Wi‑Fi and Bluetooth; no external BT module required |

---

### Notes

- Digi‑Key lists a broad selection of surface‑mount DC power jacks (vertical and right‑angle) with ratings up to 5 A. :contentReference[oaicite:11]{index=11}  
- For the 4×2 connector, Digi‑Key and similar distributors offer many variants; ensure pitch and shroud match your application. :contentReference[oaicite:12]{index=12}
- All selected options focus on **surface mount parts** with datasheets available from reliable distributors.

