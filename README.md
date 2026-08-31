# JARGO Xray Engine (Custom Build)

[![Build Status](https://github.com/contacindogaronet-ops/vku/actions/workflows/build.yml/badge.svg)](https://github.com/contacindogaronet-ops/vku/actions)

Advanced modification of the `v2rayNG` network client, specifically heavily refactored for internal network routing, headless daemon operations, and repurposed Android CLI server environments.

## ⚙️ Core Architectural Modifications

This fork departs from the standard consumer-grade release to implement server-tier optimizations:
* **Zero-Copy I/O:** Implementation of `io.CopyBuffer` on raw sockets to trigger `splice(2)` for ultra-low latency TCP relay.
* **Dual-Pool Memory Allocation:** Discarded static buffers in favor of a 32KB (Anti-Jitter) and 4MB (VVIP MTProto) dynamic pooling system.
* **Aggressive Tear-down:** Strict RFC 1928 SOCKS5 compliance with dual `.Close()` execution upon EOF.
* **O(N) Fastcache Parser:** Memory-level subdomain routing and strict SNI sniffing injection.

## 🛠 Compilation (CI/CD)
This project uses automated GitHub Actions for ephemeral, dynamic compilation. Keystore signing is bypassed for pure internal `Debug` outputs.
1. Fork or push to the `main` branch.
2. The pipeline will reconstruct the Gradle wrapper dynamically.
3. Download the compiled `.apk` directly from the Actions Artifacts panel.

---
*Based on the original [v2rayNG](https://github.com/2dust/v2rayNG) by 2dust. Licensed under GNU GPLv3.*
