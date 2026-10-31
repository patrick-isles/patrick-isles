# Patrick Baillie Isles

[![Rust](https://img.shields.io/badge/Rust-2021%20Edition-DEA584.svg?style=flat-square&logo=rust&logoColor=white)](https://www.rust-lang.org/)
[![Linux Kernel](https://img.shields.io/badge/Linux-Kernel%20%2F%20VFS%20%2F%20IOCTL-FCC624.svg?style=flat-square&logo=linux&logoColor=black)](https://kernel.org/)
[![SocketCAN](https://img.shields.io/badge/SocketCAN-AF__CAN%20%2F%20J1939-blue.svg?style=flat-square)](https://github.com/patrick-isles/can-bus-rs)
[![Prometheus](https://img.shields.io/badge/Prometheus-Ports%209106--9113-E6522C.svg?style=flat-square&logo=prometheus&logoColor=white)](https://prometheus.io/)
[![Location](https://img.shields.io/badge/Location-Portland%2C%20OR-lightgrey.svg?style=flat-square)]()
[![Resume](https://img.shields.io/badge/Resume-PDF%20Download-red.svg?style=flat-square)](./patrick_isles_systems_resume.pdf)

> **Systems & Infrastructure Engineer | Linux Kernel Diagnostics | Zero-Allocation Rust**  
> *Operating at the boundary between physical silicon, raw kernel interfaces, and deterministic low-level software.*

---

```
========================================================================================
 [SYSTEMS OPERATING MATRIX] :: PATRICK ISLES (PORTLAND, OR)
========================================================================================
 HOST SUBSYSTEMS   : Linux x86_64 | VFS Page Cache | Raw NVMe IOCTL | SysV IPC | AF_CAN | POSIX RT | PROCHOT | T10-PI
 EXECUTION ENGINE  : Pure Rust (Zero Heap Allocations in Ingestion Loops, LTO, Strip)
 TELEMETRY MESH    : 8 Prometheus Exporters (:9106 - :9113) | Real-time ANSI Dashboards
 ACADEMIC RIGOR    : PSU B.A. (Philosophy/Formal Logic, Heidelberg) + PCC Calculus (4.0)
========================================================================================
```

---

## ⚡ Core Systems Engineering & Telemetry Fleet

A portfolio of deterministic, zero-allocation systems daemons designed to monitor, audit, and remediate hostile hardware and kernel failure modes:

| Daemon / Repository | Architecture & Protocol | Key Diagnostic / Benchmark | Telemetry | Status |
|---|---|---|---|---|
| **[`blk-integrity-sentinel`](https://github.com/patrick-isles/blk-integrity-sentinel)** | Linux Block Layer T10-PI (DIF/DIX), `/sys/block/*/integrity/` | Audits end-to-end checksum protection against silent data corruption (SDC), misdirected & torn writes | **Port :9113** | 🟢 Live |
| **[`silicon-throttle-rs`](https://github.com/patrick-isles/silicon-throttle-rs)** | CPU Frequency Scaling, PROCHOT Hardware Clamping, ACPI Cooling Devices | Exposes the "Phantom Slowdown"; tracks compute penalty factors ($f_{\text{max}} / f_{\text{cur}}$) & PCIe link throttling | **Port :9112** | 🟢 Live |
| **[`rt-sched-sentinel`](https://github.com/patrick-isles/rt-sched-sentinel)** | Linux Real-Time POSIX (`SCHED_FIFO`, `SCHED_RR`), `/proc/[pid]/schedstat` | Audits Mars Pathfinder priority inversion hazards; tracks nanosecond runqueue latency (`run_delay`) | **Port :9111** | 🟢 Live |
| **[`dirty-throttle-sentinel`](https://github.com/patrick-isles/dirty-throttle-sentinel)** | Linux VFS Page Cache, `/proc/vmstat` writeback queues, sysctl tunables | Preempts synchronous `TASK_UNINTERRUPTIBLE` (`D` state) process freezes before storage chokes; zero-alloc loop | **Port :9110** | 🟢 Live |
| **[`kmem-drain-rs`](https://github.com/patrick-isles/kmem-drain-rs)** | System V `/proc/sysvipc/shm`, `shmctl(IPC_RMID)`, kernel `/proc/slabinfo` | Scans and safely reaps dead-PID unattached zombie memory; audits `SUnreclaim` kernel slab leaks | **Port :9109** | 🟢 Live |
| **[`nvme-sentinel-rs`](https://github.com/patrick-isles/nvme-sentinel-rs)** | Raw `NVME_IOCTL_ADMIN_CMD`, 512-byte packed SMART log decoding, PCIe ASPM | Hardware endurance wear, composite temperature, and PCIe link width/speed degradation (`16.0 GT/s x4`) | **Port :9108** | 🟢 Live |
| **[`can-bus-rs`](https://github.com/patrick-isles/can-bus-rs)** | Linux SocketCAN (`AF_CAN`), SAE J1939-21 29-bit extended identifier decomposition | **0.95 ns decode latency / 1.05+ billion frames/sec** throughput; DM1 Diagnostic Trouble Code parser | **Port :9107** | 🟢 Live |
| **[`telemetry-rs`](https://github.com/patrick-isles/telemetry-rs)** | Embedded UART (115200 8N1), CRC-16-CCITT, Digital Signal Processing (DSP) core | **50.79M pkts/sec / 19.69 ns latency**; computes True RMS ($V_{\text{RMS}}$), AC ripple, dynamic impedance | **Port :9106** | 🟢 Live |
| **[`rhel-idm-engine`](https://github.com/patrick-isles/rhel-idm-engine)** | Enterprise Identity Federation: Kerberos V5 (AES-256), OpenLDAP RFC 2307, SSSD | Local LDB dynamic caching for partition resilience, Host-Based Access Control (HBAC), SELinux MLS | PAM/NSS | 🟢 Reference |
| **[`g14-linux-stability-guide`](https://github.com/patrick-isles/g14-linux-stability-guide)** | Hardware Silicon Post-Mortem: AMD Zen 3+ (Ryzen 9 6900HS / Radeon RX 6700S) | Root-cause analysis resolving C6 voltage droop, PCIe ASPM, and NVMe APST collisions (`fix-g14.sh`) | Kernel Sysfs | 🟢 Production |

---

## 🛠️ Upstream Open-Source Contributions

* **[`socketcan-rs/socketcan-rs` — Pull Request #107](https://github.com/socketcan-rs/socketcan-rs/pull/107)**:
  * Implemented SAE J1939-21 29-bit extended CAN identifier bitfield decomposition and Parameter Group Number (PGN) parsing in the official Rust Linux SocketCAN crate.
  * Properly distinguishes PDU1 (peer-to-peer / destination specific) from PDU2 (broadcast) formats across the 18-bit PGN address space.
  * Passed all 98 unit and integration test suites cleanly without breaking existing public APIs, resolving upstream Issue #52.

---

## 🔬 Academic Foundation & Methodological Rigor

Combining formal analytical philosophy and historiographical research with higher-level mathematical calculus and low-level systems execution:

* **Portland State University — Bachelor of Arts (B.A.) in Philosophy, Minor in History** *(Awarded: March 2020)*:
  * **International Study**: Ruprecht-Karls-Universität Heidelberg (Germany) — German language and continental philosophy.
  * **Formal Logic & Deductive Systems (PHL 324U)**: Propositional/predicate calculus, formal validity, truth-functional semantic models.
  * **Historical Thesis Seminars (HST 492 / HST 495)**: 400-level research colloquiums centered on primary-source critical analysis, historiography, and empirical hypothesis verification.
  * **Epistemology & Linguistic Syntax (PHL 424 / PHL 433)**: Structural demarcation, epistemological truth verification, formal semantics.
  * **German Translation Series (GER 101–301)**: Technical German translation and primary source analysis.
* **Portland Community College — Electronic Engineering Technology & Mathematics Track**:
  * **Academic Honors**: **Presidents' List (4.0 Term GPA)**, Multiple Deans' List awards.
  * **Mastery**: Higher-level Calculus progression (Calculus I: MTH 251, Calculus II: MTH 252), Technical Writing (WR 227), Honors Public Speaking (COMM 111H: A), Electronic Circuit Analysis.

---

## 📐 Engineering Principles

1. **Zero Runtime Allocations in Fast Paths**: Ingestion pipelines, frame decoders, and polling loops must operate with bounded memory, zero heap allocations, and zero GC pauses.
2. **Interrogate Primary Sources**: Never infer hardware or kernel health from high-level abstractions or third-party wrappers. Query `/proc`, `sysfs`, raw IOCTL registers, and the physical bus directly.
3. **Deterministic Fault Isolation**: Treat intermittent hardware/kernel failures like an epistemological problem—eliminate variables, trace physical signals, formulate falsifiable hypotheses, and verify root causes empirically.

---

## 📄 Executive Resume

* Download the 1-Page Systems Engineering Resume: **[`patrick_isles_systems_resume.pdf`](./patrick_isles_systems_resume.pdf)**

---

## 📬 Contact & Coordinates

* **Location**: Portland, Oregon, United States
* **GitHub**: [@patrick-isles](https://github.com/patrick-isles)
* **Email**: patrick.isles@pcc.edu
