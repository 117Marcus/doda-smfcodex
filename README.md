# SMF Encoder — Python Starter Pack
### Sumerian Mathematical Framework · DODA Research

---

## What Is This?

The SMF Encoder is a **novel two-layer encoding system** that does something
standard encoders (Base64, SHA, etc.) cannot: it encodes not just the *value*
of a number, but *where that value sits in geometric space*.

Every encoded string tells you:
- Which **sector** (0–11) the value maps to on a 360° geometric ring
- Which **position** (0–29) within that sector
- Whether the value crossed a **structural boundary** (Cardinal Event)
- Whether **phi-scaling** (golden ratio) was applied
- A **base-60 checksum** for integrity

---

## What's In This Package

| File | Description |
|------|-------------|
| `smf_encoder_sample.py` | Free sample encoder (Stage 1–3 pipeline) |
| `smf_full_codec.py` | **Full encode + decode** pipeline (paid) |
| `smf_hash.py` | SMF hash function — string → SMF digest |
| `smf_test_suite.py` | 100-case validation harness (categories A–N) |
| `SMF_Technical_Overview.pdf` | Plain-English explanation of the framework |

---

## Quick Start

```python
from smf_encoder_sample import smf_encode, smf_hash

# Encode a number
print(smf_encode(90))     # → Cardinal Event at Kinetic node
print(smf_encode(37))     # → phi-scaled value

# Hash a string
print(smf_hash("DODA"))  # → 8-symbol SMF digest
```

---

## Why This Is Different From Base64

| Feature | Base64 | SMF |
|---------|--------|-----|
| Encodes value | ✅ | ✅ |
| Encodes geometric position | ❌ | ✅ |
| Structural boundary detection | ❌ | ✅ (Cardinal Events) |
| phi-scaling applied | ❌ | ✅ |
| State resolution | 64 states | 960 states (15x) |
| Built-in checksum | ❌ | ✅ (base-60) |

---

## The Three-Stage Pipeline

```
Input Integer
     │
     ▼
Stage 1 ── L1 Arithmetic Normalizer
           Decomposes into base-60 digits
           Classifies as regular or irregular (cryptographic value)
     │
     ▼
Stage 2 ── phi-Bridge Transformer
           Applies golden ratio scaling (if value > √60)
           Maps to 360° geometric ring position
           Detects Cardinal Events (0°, 90°, 180°, 270°)
     │
     ▼
Stage 3 ── L2 Geometric Encoder
           Converts to 12-sector × 30-position address
           Attaches flags and base-60 checksum
     │
     ▼
SMF Symbol String  e.g. "3F!^2"
```

---

## SMF Symbol Reference

```
Output:  SECTOR_SYM  POSITION_SYM  [FLAGS]  CHECKSUM_SYM

Symbols: 0–9, A–Z, a–x  (60 unique symbols, one per base-60 digit)

Flags:
  !  Cardinal Event  — value landed on 0°, 90°, 180°, or 270°
  ~  Irregular element — cryptographic non-terminating sequence
  ^  phi-scaled — golden ratio applied in Stage 2
```

---

## Status

- Phases 0–8 complete
- Prior art search: 7 searches, all clear — no prior art found
- 100-case test suite: round-trip closure validated

---

## License

© 2026 DODA Research. All rights reserved.
Purchasers may use this code for personal and commercial projects.
Redistribution or resale of the source files is not permitted.

---

*Questions? Reach out via the product page.*
