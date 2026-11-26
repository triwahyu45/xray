---
name: XRAY
description: Hardware, Firmware, Wearable & Mobile Reverse Engineering suite combining evidence-first REA methodology with APK decompilation (JADX/apktool), Frida SSL unpinning, BLE packet protocol analysis, binary watchface/firmware mapping, and Android/Linux device debugging.
---

# Xray — Hardware, Firmware & Mobile Reverse Engineering

Evidence-first reverse engineering playbook for Android apps, BLE wearables, binary firmware/watchfaces, and embedded Linux devices.

---

## Core Evidence-First Rules

1. **Observe Before Hypothesizing**: Inspect actual binaries, headers, decompiled classes, and live packet captures before guessing formats.
2. **Trace Static ↔ Runtime**: Correlate static symbols/offsets (JADX, Ghidra/objdump, `rea` MCP) with live runtime hooks (Frida, ADB logcat, BLE/MITM captures).
3. **Verify Every Claim**: Test reconstructed parsers/builders byte-for-byte against known-good samples.

---

## Reference Module

- **Mobile, BLE & Binary Firmware Playbook**: [`references/mobile-and-ble-re.md`](references/mobile-and-ble-re.md)
---

## Mandatory Self-Audit & Revise-Before-Delivery Gate

Before delivering any RE parser, patch, or protocol reconstruction:
1. Prove custom encoders/parsers with a byte-for-byte roundtrip test (`decode -> encode == original_bytes`) on an unmodified sample.
2. Verify Frida/ADB/BLE behavior on live captures/logs and label any unverified inference explicitly.
