.. SPDX-License-Identifier: GPL-2.0

==================================
Useful kernel modules and features
==================================

This document summarizes a handful of widely used kernel modules and
features. It also provides high-level suggestions on how these
components might be improved to better serve users and developers.

Filesystems
-----------

* **ext4** — the default filesystem on many distributions, known for its
  balance between performance and reliability.  Further integration of
  encryption and snapshot capabilities would make ext4 more flexible for
  modern workloads.

* **Btrfs** — offers advanced features such as snapshots and built-in
  RAID.  Continued focus on performance and stability would help it
  become a stronger general-purpose choice.

* **XFS** — scalable and well suited for large files and high
  concurrency.  Tools for simpler online resizing and improved metadata
  recovery would enhance usability.

* **F2FS** — designed for flash storage devices.  Enhancing zone-aware
  optimizations and wear-leveling support would extend the life of
  solid-state drives.

* **OverlayFS** — provides a union mount for layered filesystems.  More
  consistent behavior across kernel versions and tighter integration with
  container managers could simplify deployments.
* **FUSE** — allows user-space filesystems through a simple interface.
  Better caching and isolation mechanisms would enable more creative
  custom filesystem projects.
* **NILFS2** — a log-structured filesystem offering continuous snapshots.
  Enhanced recovery tools and documentation could help make it a
  dependable choice for audit trails.

* **CephFS** — a distributed network filesystem.  Better monitoring tools
  and simplified client configuration would ease large-scale deployment.

* **exFAT** — useful for removable media.  Improved interoperability tests
  with Windows and other systems could prevent data corruption.

* **NFS** — a network filesystem used for remote access to files.  Smarter
  client-side caching and stronger security options would boost reliability.

* **CIFS** — provides SMB file sharing support.  Better defaults for modern
  protocol dialects could ease cross-platform interoperability.

* **tmpfs** — an in-memory temporary filesystem.  Usage monitoring and
  optional compression would help manage ephemeral workloads.
* **UBIFS** — targets raw flash devices.  More robust wear-leveling and compression options could extend flash lifetime.
* **EROFS** — efficient read-only filesystem often used for containers.  Richer image creation tools would streamline deployments.
* **eCryptfs** — a stacked encryption filesystem.  Modernizing maintenance and improving performance would keep it viable.
* **9P** — lightweight network filesystem commonly used in virtualization.  Smarter caching could boost throughput.
* **SquashFS** — a compressed read-only filesystem popular for immutable
  system images.  Faster decompression and incremental update tools would
  ease embedded deployments.
* **Bcachefs** — a copy-on-write filesystem in development that combines
  Btrfs-style features with speed.  Thorough testing and stability
  improvements could position it as a next-generation default.
* **JFFS2** — an older flash-oriented filesystem still used on small
  devices.  Modern wear-leveling helpers and migration guides would help
  maintain legacy hardware.

* **NTFS3** — provides native read/write support for the NTFS filesystem.
  Enhanced journaling and full parity with Windows features would reduce
  the risk of data corruption when exchanging disks.

* **procfs** — exposes process and system details through ``/proc``.
  Better namespace integration and clearer documentation would minimize
  confusion for new administrators.

* **sysfs** — exports kernel object information under ``/sys``.  Stronger
  ABI guarantees could improve compatibility for user-space tools.

* **debugfs** — provides internal diagnostics.  Optional filtering and
  secure defaults would make it safer to enable in production.

* **vfat** — the FAT filesystem used by many removable drives.  Enhanced
  Unicode handling and journaling would prevent data loss across
  platforms.

* **FS-verity** — provides transparent integrity checking for read-only
  files.  Better signing tools and cross-distro support would help secure
  package distribution.

* **GFS2** — a cluster filesystem for shared-disk setups.  Streamlined
  management utilities could simplify high-availability deployments.

* **OCFS2** — Oracle's open cluster filesystem.  Improved upstream
  support and documentation would ease long-term maintenance.

* **DAX** — allows direct access to persistent memory, bypassing the page
  cache.  Wider testing and failure-handling guidance would expand its
  use.

* **ReiserFS** — a once innovative journaling filesystem known for
  efficient handling of small files.  Ongoing maintenance and modern
  compatibility fixes could keep it viable on niche workloads.

* **LogFS** — a log-structured filesystem for flash devices.  Revived
  development and better tooling might provide a lightweight option for
  embedded storage.

* **UDF** — widely used on optical media such as DVDs.  Improved
  verification utilities and cross-platform testing would reduce the risk
  of data corruption when exchanging discs.


Networking
----------

* **Netfilter** — the framework behind `iptables` and `nftables` used for
  packet filtering and network address translation.  Centralized tooling
  that combines rule management and performance statistics could simplify
  administration.

* **eBPF** — enables safe, in-kernel program execution for tracing and
  networking.  A richer library of reusable eBPF programs and easier
  debugging support would encourage broader adoption.

* **WireGuard** — a streamlined VPN protocol built into the kernel.  More
  robust peer discovery and administration tooling would improve secure
  networking setups.

* **TCP BBR** — a modern congestion control algorithm.  Wider
  cross-platform testing and automated tuning could yield better
  throughput on diverse networks.

* **XDP** — provides a high-performance, programmable packet processing
  path.  Easier integration with user-space libraries would expand its
  usage in networking appliances.

* **Bonding** — aggregates multiple network interfaces for redundancy or
  throughput.  Simplified failover monitoring and dynamic reconfiguration
  would enhance reliability.

* **IPv6** — the next-generation Internet protocol.  Streamlined transition
  tools and hardened default settings would ease widespread adoption.

* **MACVLAN** — allows creation of virtual network interfaces with unique
  MAC addresses.  Better integration with container runtimes would
  simplify multi-tenant deployments.
* **Bridge** — implements the IEEE 802.1D Ethernet bridge.  Improved VLAN
  filtering and support for hardware offload would aid complex network
  topologies.
* **IPVS** — provides load balancing capabilities in the kernel.
  Tighter integration with container orchestrators could simplify service
  scaling.
* **IPsec** — offers encrypted IP communication.  Streamlined key
  management and clearer diagnostics would encourage secure deployments.
* **nftables** — modern packet filtering that replaces legacy `iptables`.
  Integrated conversion tools would help administrators migrate existing
  rule sets.
* **Open vSwitch** — advanced software switch for virtual networks.  Hardware offload support would improve throughput.
* **traffic control (tc)** — the kernel's packet scheduler and shaper.  Consolidated documentation would help administrators tune QoS.
* **MACsec** — layer 2 encryption for Ethernet.  Easier key management would enhance secure LAN deployments.
* **DSA** — distributed switch architecture for off-chip switch chips.  Broader hardware support would expand its reach.
* **veth** — virtual Ethernet pairs for connecting namespaces.  Integrated diagnostics would simplify container networking.
* **VXLAN** — provides network overlays for virtualized or containerized
  workloads.  Hardware offload and scalable control-plane tools would help
  large deployments.
* **Multi-path TCP (MPTCP)** — allows a single connection to use multiple
  network paths.  Improved congestion control could increase reliability on
  mobile and heterogeneous networks.
* **CAN bus** — built-in support for automotive and industrial networks.
  Additional configuration utilities would simplify diagnostics on embedded
  systems.

* **L2TP** — Layer 2 Tunneling Protocol often used for VPNs.  Integrated
  debugging aids and connection management tools would improve reliability
  across diverse network setups.

* **SCTP** — a message-oriented transport protocol with built-in
  multi-homing.  Better NAT traversal and modern tooling would broaden
  deployment options.

* **Bluetooth stack** — supports wireless peripherals from keyboards to
  headsets.  Unified configuration utilities and power-saving features
  would enhance reliability on mobile systems.

* **mac80211/cfg80211** — common framework for Wi-Fi drivers.  Improved
  debugging facilities and roaming support could strengthen wireless
  connectivity.

* **VRF** — virtual routing and forwarding for network namespaces.
  Better debugging tools could simplify multi-tenant routing.

* **team driver** — alternative to bonding for interface aggregation.
  User-friendly libraries would help dynamic link management.

* **ifb** — intermediate functional block for ingress shaping.
  More examples in traffic control documentation would prevent
  misconfiguration.

* **B.A.T.M.A.N.** — routing protocol for mesh networks.
  Streamlined status reporting would aid large deployments.

* **conntrack** — tracks network connections for NAT and filtering.
  Scalable state export could assist high-performance gateways.

* **macvtap** — combines MACVLAN with tap interfaces for virtual
  machines.  Closer integration with management tools would smooth guest
  networking.

* **6LoWPAN** — IPv6 over low-power wireless networks for IoT devices.
  Integration with sensor frameworks and easier debugging utilities would
  encourage energy-efficient deployments.

* **PPP and PPPoE** — point-to-point protocols used for dial-up and
  broadband links.  Modern authentication plugins and robust IPv6 support
  would extend their usefulness.

* **ISDN** — digital telephony networking stack.  Unified configuration
  helpers could simplify maintenance of legacy infrastructure.


Virtualization
--------------

* **KVM** — the built-in hypervisor used by many virtual machine
  managers.  Better default tooling for live migration and memory
  management could streamline large-scale deployments.

* **virtio** — a standardized set of paravirtualized device drivers used
  by guests.  Faster initialization and improved diagnostics for device
  resets would help maintain stable virtual machines.

* **Xen** — an alternative hypervisor supported by Linux.  Streamlined
  tools for dom0 management and improved documentation would lower the
  barrier for adoption.

* **VFIO** — exposes devices directly to virtual machines for near-native
  performance.  Richer management utilities for hot-plugging would smooth
  passthrough setups.
* **SR-IOV** — allows a single PCIe device to present multiple virtual
  functions.  Simpler provisioning tools would ease high-density
  virtualization deployments.
* **virtiofs** — shares host storage with guests using a paravirtualized
  file system.  Better caching and security hardening would improve
  reliability for container workloads.
* **Hyper-V guest drivers** — optimize Linux when running on Microsoft Hyper-V.  Improved feature parity with Windows would smooth cross-platform deployments.
* **virtio-vsock** — provides efficient host/guest communication.  More robust security boundaries could broaden its use.
* **vhost** — accelerates virtio devices by moving data handling to the
  kernel.  Automated device assignment and better statistics would improve
  throughput for virtual switches.
* **AMD SEV** — encrypts guest memory to protect it from the host.  Easier
  key management and clearer performance guidance would help secure
  multi-tenant clouds.

* **vDPA** — enables flexible passthrough of virtio devices with a vendor
  neutral interface.  Streamlined tooling and sample drivers would
  encourage adoption by hypervisor vendors.

* **mediated devices (mdev)** — share a single hardware accelerator among
  multiple guests.  Broader hardware support and runtime monitoring would
  make it easier to deploy GPU and AI workloads in virtual machines.

* **Nested virtualization** — runs a hypervisor inside another virtual
  machine.  Optimized hardware support and simplified configuration would
  assist cloud development and testing.

* **ACRN** — a lightweight hypervisor aimed at real-time and embedded
  systems.  Upstream driver integration and management tooling could
  encourage adoption in safety-critical deployments.

* **virtio-balloon** — adjusts guest memory to fit host capacity.  More
  intelligent algorithms would lessen fragmentation and swap thrashing.

* **virtio-rng** — supplies entropy to guests via a paravirtual device.
  Ongoing review of randomness guarantees will improve isolation.

* **vTPM** — virtual Trusted Platform Module for guest attestation.
  Strong tooling for key management could simplify secure cloud
  deployments.

* **virtio-mem** — dynamically adds or removes memory from running
  guests.  Wider guest operating system support and clearer tuning
  guidance would aid cloud elasticity.

* **ivshmem** — shared memory device for inter-VM communication.
  Standardized management tools could streamline multi-VM workloads that
  need low-latency data sharing.

* **paravirtualized clocks** — reduce timer overhead inside guests.
  Broader hypervisor support would minimize drift and improve timekeeping
  accuracy.


Device and driver frameworks
----------------------------

* **Loadable modules** allow drivers to be added or removed at runtime.
  Improved dependency tracking and clearer diagnostics when module loading
  fails would ease troubleshooting.

* **DeviceTree and ACPI** provide hardware description to the kernel.
  Consistent documentation and validation tools for these interfaces can
  help avoid configuration mistakes.

* **Device Mapper** — provides a flexible infrastructure for creating
  virtual block devices, such as LVM volumes.  Improved monitoring tools
  and clearer error reporting would aid storage administration.

* **IOMMU** — maps device DMA safely into memory.  Better default
  diagnostics for mapping failures would help track down buggy drivers.

* **DRM/KMS** — the Direct Rendering Manager and Kernel Mode Setting
  framework.  More consistent user-space APIs would simplify graphics
  stack development.

* **USB gadget framework** — lets systems emulate USB devices in software.
  Expanded documentation and sample configurations would help developers
  build custom peripherals.
* **ALSA** — the Advanced Linux Sound Architecture used for audio
  devices.  Unified tooling for diagnosing mixer and codec issues would
  aid professional audio setups.
* **Input subsystem** — handles keyboards, mice and other input devices.
  A shared testing framework could reduce regressions across hardware.
* **Firmware loader** — uploads firmware to devices during boot.
  Simplifying fallback and version checks would lower barriers for new
  hardware.
* **Hotplug** — manages runtime addition and removal of devices.
  Better event tracing would help diagnose enumeration problems.
* **regulator framework** — provides a unified API for voltage and current
  regulators.  Improved debugging tools would aid board bring-up and
  power tuning.
* **GPIO subsystem** — provides a generic interface to digital pins.  Better debugfs introspection could simplify board bring-up.
* **I2C subsystem** — handles serial buses for many peripherals.  Improved bus recovery would reduce lockups.
* **SPI subsystem** — supports high-speed serial peripherals.  More DMA helpers could boost throughput.
* **Industrial I/O (IIO)** — unifies sensor drivers.  Expanded documentation and userspace examples would help integrators.
* **regmap** — common register access helpers for device drivers.  Improved
  tracing support would simplify debugging complex chips.
* **pinctrl subsystem** — manages pin multiplexing and bias settings.
  Easier board configuration tools would reduce hardware bring-up time.
* **power supply class** — monitors batteries and chargers.  More
  standardized reporting could enhance desktop and mobile integration.

* **HID subsystem** — handles human interface devices like keyboards and
  mice.  Unified tooling for feature discovery and better low-latency
  input paths would improve desktop responsiveness.

* **Video4Linux2 (V4L2)** — common framework for video capture and
  output devices.  Expanded test utilities and documentation could aid
  driver development.

* **FireWire (IEEE 1394)** — supports high-speed serial buses for audio
  and video equipment.  Modernized maintenance and diagnostics would help
  keep legacy hardware usable.

* **PCI subsystem** — enumerates and configures PCI devices.  Better
  hotplug support and clearer error messages would ease server expansion.

* **DMAEngine** — provides a generic interface to DMA controllers.
  Broader driver support and runtime statistics could improve overall
  throughput.

* **clock framework** — centralizes clock management on complex SoCs.
  More device-tree examples and debugging helpers would simplify board
  bring-up.

* **UIO** — exposes interrupts and memory-mapped devices to user space.
  Better example drivers and libraries would speed up custom hardware
  experiments.

* **devcoredump** — captures device crash data for later analysis.
  User-space utilities to parse and report these dumps would simplify
  driver debugging.

* **ASoC** — the ALSA System on Chip layer for embedded audio.  More
  template drivers and machine definitions could accelerate board
  bring-up.

* **serial core** — common infrastructure for UART and TTY drivers.
  Enhanced console features and buffering options would improve early
  boot diagnostics.

* **mailbox framework** — standard interface for hardware messaging
  units.  Additional generic controller drivers would increase reuse
  across SoCs.


Security modules
----------------

* **SELinux** — widely deployed mandatory access control.  Improved tools
  for policy generation and analysis would make SELinux more approachable.

* **AppArmor** — a profile-based access control system.  More unified
  interfaces across distributions and clearer guidance would help
  administrators take advantage of it.

* **IMA/EVM** — measures and verifies file integrity.  Streamlined key
  management and simplified policy configuration could broaden adoption.

* **seccomp** — filters system calls for untrusted programs.  More
  descriptive logging of blocked calls would help developers harden their
  applications.

* **Kernel lockdown** — restricts runtime modifications when secure boot
  is enabled.  Tools to inspect and manage the current lockdown state
  would aid in verifying system integrity.

* **SMACK** — Simplified Mandatory Access Control Kernel.  Additional
  examples and cross-distro tooling could broaden usage.

* **Yama** — enhances ptrace restrictions.  Clearer feedback when access
  is denied would help developers troubleshoot policies.

* **fscrypt** — per-file encryption for supported filesystems.  Broader
  tooling support and simpler key management would make it easier to
  protect sensitive data.
* **DM-Verity** — verifies read-only block devices for integrity.
  Easier integration with distribution tooling would strengthen system
  security.
* **BPF LSM** — allows security policies written in eBPF.  Richer helper
  functions and policy verification could unlock more flexible sandboxes.
* **Landlock** — unprivileged sandboxing using eBPF hooks.  Additional
  language bindings and tutorials could encourage widespread adoption.
* **TPM subsystem** — interface to Trusted Platform Modules.  Stronger tooling for key management would enhance secure boot processes.
* **kernel keyring** — stores credentials and keys in kernel memory.  Unified APIs across subsystems would simplify secure storage.
* **UEFI Secure Boot** — verifies kernel signatures at boot.  Easier customization of key databases would assist enterprise deployments.
* **Module signature verification** — checks cryptographic signatures on
  loadable modules.  Streamlined key management would help distributions
  ship secure kernel add-ons.
* **loadpin** — ensures modules and firmware are loaded from a trusted
  filesystem.  Better auditing of policy violations could improve system
  hardening.

* **crypto API** — the kernel's cryptographic framework for ciphers and
  digests.  Additional hardware acceleration drivers and stable
  interfaces would benefit security workloads.

* **KASLR** — randomizes the kernel memory layout at boot.  Better entropy
  sources and straightforward configuration would strengthen exploit
  defenses.

* **stack canaries** — insert guard values to detect stack overflows.
  Automatic coverage reports could ensure consistent protection across the
  code base.

* **LSM stacking** — ability to run multiple security modules together.
  Improved compatibility testing would let administrators combine
  complementary policies.

* **Intel SGX** — encloses sensitive code in secure enclaves.  Enhanced
  debugging support and container integration could broaden practical
  deployments.

* **page table isolation (PTI)** — mitigates speculative execution
  attacks.  Continued tuning to balance security and performance would
  benefit all systems.


Resource management
-------------------

* **cgroups** — provide fine-grained control over CPU, memory and I/O
  resources.  Better integration with systemd and clearer documentation on
  controller interactions would aid in tuning workloads.

* **Namespaces** — isolate global resources for containers.  Additional
  tooling for debugging namespace setups and easier configuration would
  benefit container environments.

* **Pressure Stall Information (PSI)** — reports CPU, memory and I/O
  pressure.  Built-in visualization tools could help administrators gauge
  saturation and plan capacity.

* **cpuset** — assigns CPUs and memory nodes to tasks.  Better tie-ins
  with resource managers would simplify NUMA-aware scheduling.

* **RDT (resctrl)** — implements Intel Resource Director Technology for
  cache and memory bandwidth control.  Improved tooling and visibility of
  allocation conflicts would aid performance tuning.
* **cgroup v2** — unifies resource controllers under a single hierarchy.
  More comprehensive examples and migration guides would ease adoption.
* **PIDs controller** — restricts the number of tasks in a cgroup.  More precise accounting would aid resource planning.
* **I/O controller** — throttles or prioritizes block I/O per cgroup.  Improved monitoring tools could reveal bottlenecks sooner.
* **freezer controller** — temporarily pauses all tasks in a cgroup.
  Integration with checkpoint/restore tools would aid container live
  migration.
* **memory.high** — allows soft limiting of memory in cgroup v2.  Clearer
  documentation on reclaim behavior would help avoid unexpected OOM
  events.

* **memory.low** — protects a portion of memory from reclaim within a
  cgroup.  Detailed guidelines on tuning values would help container
  workloads maintain responsiveness under pressure.

* **memory.swap.max** — limits swap usage for a cgroup.
  Clear documentation and tooling would help avoid thrashing under load.

* **memory protection keys (PKU)** — enable fast per-page permission
  changes on x86.  Broader library support could unlock new sandboxing
  techniques.

* **rlimits** — per-process resource limits enforced by the kernel.
  Unified configuration utilities would aid system-wide policy
  management.

* **control-group CPU bandwidth** — enforces CPU usage ceilings over
  specific intervals.  Better visualization tools could help balance
  workloads in shared environments.


Tracing and debugging
---------------------

* **ftrace** — lightweight in-kernel tracing framework.  Easier output
  formatting and integration with eBPF would speed up diagnostics.

* **perf** — performance analysis tool.  Streamlined default metrics and
  richer tutorials could encourage more developers to profile code.

* **kprobes** — allows dynamic instrumentation of running kernels.  Safer
  default policies and example scripts would lower the barrier to entry.

* **SystemTap** — provides scriptable tracing of kernel events.  Improved
  packaging and support for more architectures would boost adoption.

* **KGDB** — enables remote debugging of the kernel.  Streamlined set-up
  guides could help developers diagnose difficult issues.

* **bpftrace** — leverages eBPF for powerful yet simple tracing scripts.
  Additional kernel helpers and packaged examples would speed up
  troubleshooting.
* **KUnit** — framework for kernel unit testing.  Wider subsystem
  coverage and stable APIs would help maintain code quality.
* **KASAN** — detects memory errors during runtime.  Lower overhead modes
  could enable continuous use in production kernels.
* **lockdep** — checks locking for potential deadlocks.  Better reporting
  tools would assist in fixing complex interactions.
* **kcov** — collects code coverage information from kernel code.
  Automated reporting and integration with fuzzers would aid robustness.
* **tracefs** — dedicated filesystem for tracing outputs.  Consistent tooling across utilities would simplify trace collection.
* **dynamic debug** — toggles kernel debugging messages at runtime.  Improved filters could make troubleshooting less noisy.
* **BTF** — BPF Type Format for typed kernel data.  Wider annotation coverage would enhance eBPF introspection.
* **KCSAN** — the Kernel Concurrency Sanitizer.  Lower overhead and
  automatic reporting would help catch data races earlier.
* **kmemleak** — detects leaked kernel memory.  More efficient scanning
  could make it practical for long-running systems.

* **KDB** — interactive in-kernel debugger.  Improved documentation and
  remote access features would help track down early boot issues.

* **ftrace hist triggers** — allow custom aggregation within the tracing
  subsystem.  Expanded examples and tooling could simplify performance
  monitoring.

* **drgn** — in-kernel introspection tool leveraging Python.  Wider
  architecture support and packaged examples would help developers
  analyze live systems.


Power management
----------------

* **CPUFreq** — adjusts processor speed to save power.  Smarter defaults
  that learn workloads could strike a better balance between performance
  and energy use.

* **Suspend and hibernate** — enable low-power or no-power states.
  Consistent driver support and debugging tools would reduce wake-up
  issues across hardware.

* **Energy-aware scheduling (EAS)** — places tasks on the most efficient
  cores.  Ongoing tuning for new systems can extend battery life on
  portable devices.

* **devfreq** — scales the frequency of GPUs and other devices.  Adaptive
  policies could prolong battery life without sacrificing responsiveness.
* **thermal framework** — monitors sensors and controls cooling devices.
  More automatic policy generation could keep systems within safe
  temperatures.
* **cpuidle** — manages processor idle states.  Smarter governors would
  squeeze more power savings out of modern CPUs.
* **runtime PM** — automatically powers down idle hardware devices.
  Wider driver support would extend battery life across platforms.
* **intel_pstate** — governs CPU frequency on modern Intel CPUs.  Improved reporting via sysfs would aid tuning.
* **schedutil governor** — ties CPU frequency to scheduler utilization.  Wider testing on heterogeneous systems could boost efficiency.
* **powercap (RAPL)** — enforces power limits on Intel processors.  More
  accessible tooling could help data centers manage energy budgets.
* **cpupower** — a user-space utility that interacts with CPUFreq and
  cpuidle.  Expanded reporting options would make tuning simpler for
  administrators.

* **intel_idle** — Intel-specific idle driver offering deeper sleep
  states.  Continuous tuning across processor generations would maximize
  battery life on laptops and servers.

* **Power Management QoS** — lets drivers express latency or throughput
  requirements.  Easier user-space interfaces could encourage application
  tuning for energy efficiency.

* **Energy Model (EM)** — describes the power cost of CPU operating
  points.  Shipping more default models would help schedulers balance
  performance with energy use on new SoCs.

* **generic power domains (genpd)** — group devices so they can be
  powered down together.  Better runtime diagnostics would ease
  integration into complex platforms.


Memory management
-----------------

* **Transparent Hugepages (THP)** — merges small pages into large ones for
  better performance.  Smarter heuristics could minimize fragmentation and
  unexpected latency spikes.

* **ZRAM** — offers a compressed in-memory swap device.  Automatic sizing
  based on available RAM would help desktops and small devices alike.

* **Zswap** — provides compressed caching for swap.  Further optimizations
  for high-memory systems could reduce I/O pressure.

* **KSM** — Kernel Samepage Merging deduplicates identical memory pages
  across processes.  Smarter heuristics could reduce overhead when
  workloads fluctuate.
* **hugetlbfs** — reserves large pages for special workloads.  Easier
  reservation and accounting tools would improve performance tuning.
* **memfd** — allows creation of anonymous memory-backed files.  Enhanced
  sealing features could benefit sandboxing and IPC uses.
* **DAMON** — monitors memory access patterns efficiently.  Integration
  with performance tooling would help identify optimization targets.
* **memory hotplug** — add or remove RAM while the system runs.  Better coordination with user space could minimize disruption.
* **balloon driver** — dynamically reallocates memory for virtual machines.  Improved heuristics could avoid performance hits.
* **CMA (Contiguous Memory Allocator)** — reserves large physically
  contiguous blocks.  Better monitoring tools would help tune allocations
  for DMA-heavy workloads.
* **userfaultfd** — enables user-space handling of page faults.  Wider
  architecture support could simplify live migration and checkpointing.

* **Heterogeneous Memory Management (HMM)** — allows devices to share
  system RAM with the CPU.  Expanding driver support would accelerate GPU
  and accelerator workloads.

* **KFENCE** — low-overhead memory safety error detector.  Making reports
  easier to interpret would help developers quickly root-cause bugs.

* **soft-dirty tracking** — marks pages modified since a checkpoint.
  Enhanced tooling could streamline live migration and incremental
  backups.


Storage and I/O
---------------

* **blk-mq** — the multi-queue block layer for modern storage devices.
  Tools to monitor queue depth would assist in tuning high-performance
  systems.

* **I/O schedulers (BFQ, Kyber, mq-deadline)** — choose request ordering
  strategies.  Auto-selection based on device type could deliver better
  latency with less manual tuning.

* **dm-crypt** — provides transparent block device encryption.  Simplified
  key rotation procedures and stronger defaults would improve data
  security.
* **MD RAID** — software-based RAID implementation.  Automated rebuilds
  and clearer monitoring tools would reduce maintenance burdens.
* **Bcache** — caches slower block devices onto faster ones.  Better
  write-back policies and statistics would aid hybrid storage setups.
* **NVMe over Fabrics** — extends NVMe protocol across networks.
  Simplified configuration and performance metrics would ease deployment
  in data centers.
* **io_uring** — modern asynchronous I/O interface.  Continued work on
  zero-copy and networking support could expand high-performance use
  cases.
* **DM multipath** — maintains multiple I/O paths to storage devices.  Automatic failover improvements would increase reliability.
* **loop device** — maps files as block devices.  Tighter security defaults could prevent privilege escalation.
* **Network Block Device (NBD)** — exposes remote block storage.  Built-in encryption options would improve data safety.
* **SCSI target (LIO)** — lets Linux present block devices to remote systems.  Simplified configuration tools would encourage small SAN deployments.
* **zoned block devices** — support for SMR and ZBC hard drives.  Better
  tooling for zone-aware filesystems would improve utilization of these
  high-capacity disks.

* **dm-writecache** — caches writes using persistent memory.  More
  benchmarking and tuning guides would help adopters.

* **dm-thin-provisioning** — creates flexible virtual block devices with
  on-demand allocation.  Enhanced monitoring and automated trimming would
  simplify storage management.

* **iSCSI** — kernel target and initiator for block storage over IP.
  Streamlined authentication and boot integration could improve
  enterprise deployments.

* **rbd (Ceph RADOS block device)** — client driver for distributed block
  storage.  Smarter caching and failover handling would boost resilience
  in large clusters.


Scheduler features
------------------

* **CFS** — the default Completely Fair Scheduler.  Exposing more
  user-space knobs would help administrators balance throughput and
  responsiveness.

* **PREEMPT_RT** — the real-time patch set.  Continued merging and testing
  will improve determinism for latency-critical workloads.

* **deadline scheduler** — a scheduler aimed at meeting task deadlines.
  Closer integration with cgroup controllers would help mix real-time and
  best-effort workloads safely.

* **SCHED_FIFO and SCHED_RR** — fixed-priority schedulers for strict
  real-time tasks.  Clearer documentation and runtime tuning helpers
  could improve determinism for critical applications.
* **utilization clamping (uclamp)** — allows tasks to specify minimum and
  maximum CPU utilization.  Better documentation would help tune mobile
  devices and power-sensitive workloads.
* **SCHED_CORE** — isolates groups of tasks to mitigate SMT side-channel
  attacks.  Hardware-aware defaults could minimize performance impact.
* **tickless kernel (NO_HZ)** — reduces scheduler overhead when idle.  Further refinements could extend battery life.
* **NUMA balancing** — automatically places tasks on memory nodes.  Smarter adaptation to workload patterns would boost performance.
* **CPU isolation** — allows dedicating CPUs to real-time or latency-critical
  tasks.  Easier runtime configuration would help specialized workloads.
* **schedstats** — provides detailed scheduling statistics.  Automated
  collection and analysis could guide tuning efforts.

* **SCHED_DEADLINE** — implements earliest-deadline-first scheduling for
  real-time tasks.  User-friendly tracing and admission control tools
  would make it safer for industrial applications.

* **core scheduling** — pairs tasks to isolate SMT threads and reduce
  side-channel risk.  Simplified configuration could help administrators
  adopt it on shared systems.


Boot and initialization
-----------------------

* **initramfs** — a temporary root filesystem used during boot.  Better
  debugging tools and consistent tooling could speed up kernel upgrades.
* **kexec** — lets the system boot directly into a new kernel without
  firmware involvement.  Improved memory preservation would reduce
  downtime in crash recovery.
* **kdump** — captures crash dumps using kexec.  Automated testing and
  more flexible storage targets would aid post-mortem analysis.

* **firmware-assisted dump (fadump)** — preserves crash data using
  firmware on supported platforms.  Broader architecture support could
  speed up failure analysis in production.
* **UEFI firmware support** — uses standardized boot protocols.  Better cross-vendor testing would enhance reliability.
* **Device tree overlays** — allow runtime modification of hardware descriptions.  Expanded tooling could simplify embedded development.
* **EFI stub** — lets the kernel be loaded directly by UEFI firmware.
  Additional diagnostics and secure-boot integration would make updates
  smoother on modern systems.

* **bootconfig** — allows structured kernel parameters through a side
  file.  Tooling to automatically generate entries would simplify
  deployments with many options.

* **unified kernel images (UKI)** — bundles kernel, initramfs and metadata
  in a single signed file.  Standard build helpers could streamline secure
  boot on diverse platforms.


Additional subsystems
---------------------

* **livepatch** — apply kernel fixes at runtime without rebooting.
  Unified tools and automated pre-checks would make patching safer and
  simpler.
* **watchdog** — monitors system health and can reboot a machine that
  becomes unresponsive.  Closer integration with systemd would make
  hardware watchdogs easier to configure.
* **hardware monitoring (hwmon)** — exposes temperature, voltage and fan
  data.  Consistent sensor names and per-sensor alerts could improve
  observability.
* **configfs** — provides a virtual filesystem for configuring kernel
  objects.  More examples and helper utilities would reduce setup
  mistakes.
* **PTP hardware clocks** — enable sub-microsecond time synchronization.
  Wider hardware support and better diagnostics would aid industrial and
  networking deployments.
* **RDMA and InfiniBand** — support low-latency, high-throughput
  networking.  Simplified connection management and broader
  documentation could boost adoption in data centers.
* **USB Type-C framework** — manages alternate modes and power
  negotiation.  Additional compatibility testing and user-space
  libraries would help ensure safe operation.
* **pstore** — preserves crash logs across reboots.  User-friendly tools
  to extract and rotate entries would aid remote debugging.
* **LED subsystem** — controls status indicators on many devices.
  Unified triggers and configuration utilities could improve usability.
* **nvmem subsystem** — access device non-volatile memory areas.  User-space utilities could ease calibration storage.
* **FPGA manager** — loads programmable logic bitstreams.  Signed image support would strengthen security.
* **PCI hotplug** — handles adding and removing PCI devices at runtime.  More consistent user-space notifications would aid maintenance.
* **Thunderbolt subsystem** — manages high-speed peripheral connections.
  Broader firmware update support would improve reliability for docks and
  external GPUs.
* **PWM framework** — controls pulse-width modulation devices.  Unified
  configuration tools could simplify LED and fan control.
* **Greybus** — provides a generic communication framework for modular
  hardware.  Continued driver support would enable more flexible designs.

* **remoteproc and RPMsg** — manage auxiliary processors and
  inter-processor messaging.  Enhanced debugging tools would ease
  development on heterogeneous SoCs.

* **IPMI** — remote management interface for servers.  Stronger
  authentication defaults and streamlined user-space utilities would help
  secure out-of-band access.

* **EDAC** — reports memory and PCIe errors through standardized logs.
  Expanded platform coverage would improve detection of hardware faults.

* **devlink** — provides a unified interface for managing complex network
  devices.  Richer diagnostics and transactional configuration would ease
  switch bring-up.

* **hwspinlock** — coordinates access to shared resources across CPU
  clusters.  Broader driver support could simplify multi-processor SoCs.

* **libnvdimm** — manages persistent memory modules such as NVDIMMs.
  Richer tooling for error recovery and secure erase would assist
  enterprise deployments.

* **UACCE** — provides a unified interface for accelerator hardware used
  for crypto or compression.  Stronger resource isolation and
  virtualization support could make sharing these devices safer.

* **MHI bus** — connects modern modems over PCIe.  Additional debugging
  utilities and open firmware examples would broaden compatibility.

* **SoundWire subsystem** — standardized low-power audio bus for SoCs.
  More generic drivers and dynamic routing support would ease embedded
  audio design.

* **Coresight** — trace infrastructure on ARM systems.  Better
  integration with ``perf`` and open decode tools would simplify complex
  debugging sessions.

* **WWAN subsystem** — manages cellular modems and network interfaces.
  Streamlined user-space configuration could accelerate connected IoT
  deployments.


Why enhancements matter
-----------------------

The modules and features above are used on countless systems.  Evolving
usability, performance and observability will help both administrators
and developers maintain secure and efficient systems.  Small
improvements in tooling and documentation often translate into significant
productivity gains and fewer errors when configuring the kernel.

