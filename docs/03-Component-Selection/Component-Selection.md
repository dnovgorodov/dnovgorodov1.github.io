# Component Selection

---

# **Power Input Subsystem – DC Barrel Jack**

## Design Requirements Considered

- Surface‑mount required (Class requirement)
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
**PJ‑068B‑SMT‑TR**

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
**TLV75733PDBVR**

### Rationale

I chose the TLV75733PDBVR because it comes in a smaller SOT-23 package and can supply up to 1 A, giving us more current headroom in a compact design. It also includes an enable pin, which gives us better control over power management in the circuit.

---
