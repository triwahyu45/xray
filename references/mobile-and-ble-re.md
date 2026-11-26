# Mobile, BLE & Binary Firmware Playbook

## 1. Android APK & Runtime Instrumentation
- **Static Decompilation**: Use `apktool` for manifest/resources/smali and `jadx` for readable Java/Kotlin classes; search for BLE UUIDs, crypto keys, protobuf schemas, and API endpoints.
- **Frida SSL Unpinning & Hooking**: Attach Frida to bypass certificate pinning (`TrustManagerImpl`, `OkHttp3 CertificatePinner`) and hook serialization/encryption methods to inspect plaintext payloads in transit.

## 2. BLE & Binary Asset Reverse Engineering
- **Packet Framing & L1 Protocol**: Capture HCI snoop logs (`btsnoop_hci.log`) via ADB, open in Wireshark, isolate GATT Write/Notify handles, and map header magic bytes, chunked L1 frame lengths, sequence counters, ACK opcodes, and CRC/checksums before replaying payloads via `bleak`.
- **Binary Firmware / Watchfaces (`.bin`)**:
  - Dump hex headers to locate magic signatures, version fields, resource offset tables, RLE/indexed bitmap formats, and string pools.
  - Validate custom encoders by round-tripping an unmodified sample (`decode -> encode == original_bytes`) before injecting modified assets.
- **Local Private-Server / MITM Loop**: Bypass app SSL pinning with Frida (`TrustManagerImpl`, `OkHttp3 CertificatePinner`) and verify binary/OTA payloads through a controlled local proxy/server before flashing physical wearable hardware.

## 3. Linux / Android Device Recovery
- **ADB & Fastboot**: Verify device state (`adb devices`), inspect kernel/logcat (`dmesg`, `adb logcat`), and back up partition/boot images before flashing modified kernels or rootfs.
