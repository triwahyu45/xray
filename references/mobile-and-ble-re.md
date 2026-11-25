# Mobile, BLE & Binary Firmware Playbook

## 1. Android APK & Runtime Instrumentation
- **Static Decompilation**: Use `apktool` for manifest/resources/smali and `jadx` for readable Java/Kotlin classes; search for BLE UUIDs, crypto keys, protobuf schemas, and API endpoints.
- **Frida SSL Unpinning & Hooking**: Attach Frida to bypass certificate pinning (`TrustManagerImpl`, `OkHttp3 CertificatePinner`) and hook serialization/encryption methods to inspect plaintext payloads in transit.

## 2. BLE & Binary Asset Reverse Engineering
- **Packet Framing**: Capture HCI snoop logs (`btsnoop_hci.log`) via ADB, open in Wireshark, isolate GATT Write/Notify handles, and map header magic bytes, length fields, sequence counters, and CRC/checksums.
- **Binary Firmware / Watchfaces**:
  - Dump hex headers to locate magic signatures, version fields, resource offset tables, and string/bitmap pools.
  - Validate custom encoders by round-tripping an unmodified sample (`decode -> encode == original_bytes`) before injecting modified assets.

## 3. Linux / Android Device Recovery
- **ADB & Fastboot**: Verify device state (`adb devices`), inspect kernel/logcat (`dmesg`, `adb logcat`), and back up partition/boot images before flashing modified kernels or rootfs.
