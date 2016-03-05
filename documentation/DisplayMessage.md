Display Message
==

## Bootup Kernel Display Message

> dmesg (display message or driver message) is a command on most Unix-like operating systems that prints the message buffer of the kernel. [Linux Kernel Dmesg](https://en.wikipedia.org/wiki/Dmesg)

```sh
    root@edison:~# dmesg
    ...
    root@edison:~# dmesg > dmesg.file
    root@edison:~# vi dmesg.file
    
    [    0.000000] Initializing cgroup subsys cpuset
    [    0.000000] Initializing cgroup subsys cpu
    ...
    [   17.842227] snd_intel_sst: runtime_idle called                               
    [   19.841555] snd_intel_sst: runtime_suspend called
```

```sh
root@edison:~# tail -f /var/log/messages
...
root@edison:~# dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.10.17-poky-edison+ (sys_dswci@tlsndgbuild004) (gcc version 4.9.1 (GCC) ) #1 SMP PREEMPT Fr5
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000097fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x0000000003ffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000004000000-0x0000000005ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000006000000-0x000000003f4fffff] usable
[    0.000000] BIOS-e820: [mem 0x000000003f500000-0x000000003fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec04000-0x00000000fec07fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Intel Corporation Merrifield/BODEGA BAY, BIOS 542 2015.01.21:18.19.48
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x3f500 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-back
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03F600000 mask FFFE00000 uncachable
[    0.000000]   2 base 03F800000 mask FFF800000 uncachable
[    0.000000]   3 base 004000000 mask FFE000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1014MB, range: 2MB, type UC
[    0.000000] reg 2, base: 1016MB, range: 8MB, type UC
[    0.000000] reg 3, base: 64MB, range: 32MB, type UC
[    0.000000] total RAM covered: 982M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K  chunk_size: 512M        num_reg: 5      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 512MB, type WB
[    0.000000] reg 1, base: 64MB, range: 32MB, type UC
[    0.000000] reg 2, base: 512MB, range: 512MB, type WB
[    0.000000] reg 3, base: 1014MB, range: 2MB, type UC
[    0.000000] reg 4, base: 1016MB, range: 8MB, type UC
[    0.000000] e820: update [mem 0x04000000-0x05ffffff] usable ==> reserved
[    0.000000] initial memory mapped: [mem 0x00000000-0x023fffff]
[    0.000000] Base memory trampoline at [c0094000] 94000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x03ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x03ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x06000000-0x33ffffff]
[    0.000000]  [mem 0x06000000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01e27000, 0x01e27fff] PGTABLE
[    0.000000] 121MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01e28000, 0x01e28fff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x3f4fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x00097fff]
[    0.000000]   node   0: [mem 0x00100000-0x03ffffff]
[    0.000000]   node   0: [mem 0x06000000-0x3f4fffff]
[    0.000000] On node 0 totalpages: 251031
[    0.000000] free_area_init_node: node 0, pgdat c1c59e40, node_mem_map f740e020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3991 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 216062 pages, LIFO batch:31
[    0.000000]   HighMem zone: 243 pages used for memmap
[    0.000000]   HighMem zone: 30978 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] SFI: Simple Firmware Interface v0.81 http://simplefirmware.org
[    0.000000] SFI: SYST E31F0, 0060 (v1  INTEL INTELFDK)
[    0.000000] SFI: CPUS E3296, 0020 (v1  INTEL INTELFDK)
[    0.000000] SFI: FREQ E32C2, 0030 (v1  INTEL INTELFDK)
[    0.000000] SFI: MMAP E32FE, 01A4 (v1  INTEL INTELFDK)
[    0.000000] SFI: XSDT E34B0, 002C (v1  INTEL INTELFDK)
[    0.000000] SFI: APIC E353E, 0020 (v1  INTEL INTELFDK)
[    0.000000] SFI: WAKE E356A, 0020 (v2  INTEL INTELFDK)
[    0.000000] SFI: DEVS E359E, 047D (v1  INTEL INTELFDK)
[    0.000000] SFI: GPIO E3A27, 0964 (v1  INTEL INTELFDK)
[    0.000000] SFI: OEMB E4397, 0060 (v5 UMGFDK CFGINFO!)
[    0.000000] SFI: registering lapic[0]
[    0.000000] SFI: registering lapic[2]
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-54
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 71
[    0.000000] e820: [mem 0x40000000-0xfebfffff] available for PCI devices
[    0.000000] setup_percpu: NR_CPUS:2 nr_cpumask_bits:2 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f73e8000 s33856 r0 d23488 u57344
[    0.000000] pcpu-alloc: s33856 r0 d23488 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 249247
[    0.000000] Kernel command line: rootwait root=PARTUUID=012b3303-34ac-284d-99b4-34e03a2335f4 rootfstype=ext4 console=ty
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Initializing HighMem for node 0 (00037bfe:0003f500)
[    0.000000] Memory: 982520k/1037312k available (7064k kernel code, 21604k reserved, 3679k data, 572k init, 123912k hig)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff8b000 - 0xfffff000   ( 464 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1c7e000 - 0xc1d0d000   ( 572 kB)
[    0.000000]       .data : 0xc18e60e0 - 0xc1c7dfc0   (3679 kB)
[    0.000000]       .text : 0xc1200000 - 0xc18e60e0   (7064 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Preemptible hierarchical RCU implementation.
[    0.000000]  Additional per-CPU info printed with stalls.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f6c08000 soft=f6c0a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] kmemleak: Kernel memory leak detector disabled
[    0.000000] tsc: Detected 499.200 MHz processor
[    0.000009] Calibrating delay loop (skipped), value calculated using timer frequency.. 998.40 BogoMIPS (lpj=4992000)
[    0.000032] pid_max: default: 32768 minimum: 301
[    0.000262] Security Framework initialized
[    0.000290] SELinux:  Initializing.
[    0.000352] SELinux:  Starting in permissive mode
[    0.000433] Mount-cache hash table entries: 512
[    0.001592] Initializing cgroup subsys devices
[    0.001617] Initializing cgroup subsys freezer
[    0.001635] Initializing cgroup subsys blkio
[    0.001651] Initializing cgroup subsys perf_event
[    0.001792] CPU: Physical Processor ID: 0
[    0.001808] CPU: Processor Core ID: 0
[    0.001827] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.001827] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.001847] mce: CPU supports 6 MCE banks
[    0.001879] CPU0: Thermal monitoring enabled (TM1)
[    0.001921] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.001921] Last level dTLB entries: 4KB 128, 2MB 0, 4MB 0
[    0.001921] tlb_flushall_shift: 6
[    0.002350] Freeing SMP alternatives: 28k freed
[    0.002406] SFI: MCFG E34F6, 003C (v1  INTEL INTELFDK)
[    0.002425] ftrace: allocating 28044 entries in 55 pages
[    0.069749] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.069828] smpboot: CPU0: Genuine Intel(R) CPU   4000  @  500MHz (fam: 06, model: 4a, stepping: 08)
[    0.069877] TSC deadline timer enabled
[    0.069938] Performance Events: no PEBS fmt2+, generic architected perfmon, Intel PMU driver.
[    0.069983] ... version:                3
[    0.069997] ... bit width:              40
[    0.070010] ... generic registers:      2
[    0.070023] ... value mask:             000000ffffffffff
[    0.070035] ... max period:             000000007fffffff
[    0.070047] ... fixed-purpose events:   3
[    0.070059] ... event mask:             0000000700000003
[    0.110413] ftrace: Allocated trace_printk buffers
[    0.161446] CPU 1 irqstacks, hard=f6f8c000 soft=f6f8e000
[    0.161467] smpboot: Booting Node   0, Processors  #1 OK
[    0.171674] Initializing CPU#1
[    0.172635] Skipped synchronization checks as TSC is reliable.
[    0.173084] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.173167] Brought up 2 CPUs
[    0.173188] smpboot: Total of 2 processors activated (1996.80 BogoMIPS)
[    0.175129] devtmpfs: initialized
[    0.185945] SFI: SFI sysfs interfaces init success
[    0.186528] regulator-dummy: no parameters
[    0.187026] NET: Registered protocol family 16
[    0.189125] SFI OEMB Layout
[    0.189163]  OEMB signature               : OEMB
[    0.189163]  OEMB length                  : 96
[    0.189163]  OEMB revision                : 5
[    0.189163]  OEMB checksum                : 0x8D
[    0.189163]  OEMB oem_id                  : UMGFDK
[    0.189163]  OEMB oem_table_id            : CFGINFO!
[    0.189163]  OEMB board_id                : 0x02
[    0.189163]  OEMB iafw version            : 002.012
[    0.189163]  OEMB val_hooks version       : 002.004
[    0.189163]  OEMB ia suppfw version       : 000.000
[    0.189163]  OEMB scu runtime version     : 176.073
[    0.189163]  OEMB ifwi version            : 237.015
[    0.189265] intel_soc_thermal: IPC bus = 0, name =         soc_thrm, irq = 0x 1
[    0.189482] IPC bus, name =        bcove_adc, irq = 0x32
[    0.189681] IPC bus, name =       bcove_thrm, irq = 0x34
[    0.189891] IPC bus, name =  bcove_power_btn, irq = 0x1e
[    0.190063] IPC bus, name =        pmic_ccsm, irq = 0x1b
[    0.190307] SDIO bus = 1, name = bcm43xx_clk_vmmc, ref_clock = 26000000, addr =0x401
[    0.190323] Using generic wifi platform data
[    0.190340] wifi_platform_data: GPIO == 64
[    0.190485] IPC bus, name =        msic_gpio, irq = 0x31
[    0.190665] I2C bus = 1, name =      pcal9555a-1, irq = 0x 0, addr = 0x20
[    0.190702] I2C bus = 1, name =      pcal9555a-2, irq = 0x 0, addr = 0x21
[    0.190733] I2C bus = 1, name =      pcal9555a-3, irq = 0x 0, addr = 0x22
[    0.190765] I2C bus = 1, name =      pcal9555a-4, irq = 0x 0, addr = 0x23
[    0.190797] SPI bus=5, name=         ads7955, irq=0x 0, max_freq=20000000, cs=0
[    0.190820] SPI bus=5, name=          spidev, irq=0x 0, max_freq=25000000, cs=1
[    0.190839] IPC bus, name =        mrfld_sst, irq = 0xff
[    0.191122] pgrr = 000003d5
[    0.191599] PCI: MMCONFIG for domain 0000 [bus 00-00] at [mem 0x3f500000-0x3f5fffff] (base 0x3f500000)
[    0.191624] PCI: MMCONFIG at [mem 0x3f500000-0x3f5fffff] reserved in E820
[    0.191637] PCI: Using MMCONFIG for extended config space
[    0.191650] PCI: Using configuration type 1 for base access
[    0.204933] bio: create slab <bio-0> at 0
[    0.206262] vgaarb: loaded
[    0.206947] SCSI subsystem initialized
[    0.207340] usbcore: registered new interface driver usbfs
[    0.207439] usbcore: registered new interface driver hub
[    0.207644] usbcore: registered new device driver usb
[    0.207928] media: Linux media interface: v0.10
[    0.208019] Linux video capture interface: v2.00
[    0.208092] pps_core: LinuxPPS API ver. 1 registered
[    0.208108] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.208148] PTP clock support registered
[    0.208651]  remoteproc0: intel_rproc_scu is available
[    0.208671]  remoteproc0: Note: remoteproc is still under development and considered experimental.
[    0.208686]  remoteproc0: THE BINARY FORMAT IS NOT YET FINALIZED, and backward compatibility isn't yet guaranteed.
[    0.209097]  remoteproc0: registered virtio0 (type 7)
[    0.209345]  remoteproc0: powering up intel_rproc_scu
[    0.209373]  remoteproc0: Booting fw image intel_mid/intel_mid_remoteproc.fw, size 4456
[    0.209413] Started intel scu remote processor
[    0.209430]  remoteproc0: remote processor intel_rproc_scu is now up
[    0.209777] virtio_rpmsg_bus virtio0: creating channel rpmsg_bcove_adc addr 0x24
[    0.209966] virtio_rpmsg_bus virtio0: creating channel rpmsg_mrfl_thermal addr 0x25
[    0.210137] virtio_rpmsg_bus virtio0: creating channel rpmsg_mid_powerbtn addr 0x10
[    0.210306] virtio_rpmsg_bus virtio0: creating channel rpmsg_pmic_ccsm addr 0x19
[    0.210473] virtio_rpmsg_bus virtio0: creating channel rpmsg_msic_gpio addr 0x5
[    0.210649] virtio_rpmsg_bus virtio0: creating channel rpmsg_ipc_command addr 0xa0
[    0.210817] virtio_rpmsg_bus virtio0: creating channel rpmsg_ipc_simple_command addr 0xa1
[    0.210984] virtio_rpmsg_bus virtio0: creating channel rpmsg_ipc_raw_command addr 0xa2
[    0.211163] virtio_rpmsg_bus virtio0: creating channel rpmsg_pmic addr 0xff
[    0.211332] virtio_rpmsg_bus virtio0: creating channel rpmsg_mip addr 0xec
[    0.211501] virtio_rpmsg_bus virtio0: creating channel rpmsg_fw_update addr 0x13
[    0.211682] virtio_rpmsg_bus virtio0: creating channel rpmsg_ipc_util addr 0x12
[    0.211863] virtio_rpmsg_bus virtio0: creating channel rpmsg_flis addr 0xf5
[    0.212037] virtio_rpmsg_bus virtio0: creating channel rpmsg_watchdog addr 0xf8
[    0.212209] virtio_rpmsg_bus virtio0: creating channel rpmsg_umip addr 0x14
[    0.212391] virtio_rpmsg_bus virtio0: creating channel rpmsg_osip addr 0x15
[    0.212564] virtio_rpmsg_bus virtio0: creating channel rpmsg_vrtc addr 0xfa
[    0.212778] virtio_rpmsg_bus virtio0: creating channel rpmsg_fw_logging addr 0x27
[    0.212970] virtio_rpmsg_bus virtio0: creating channel rpmsg_kpd_led addr 0x23
[    0.213149] virtio_rpmsg_bus virtio0: creating channel rpmsg_modem_nvram addr 0xa2
[    0.213326] virtio_rpmsg_bus virtio0: creating channel rpmsg_mid_pwm addr 0x22
[    0.213500] virtio_rpmsg_bus virtio0: rpmsg host is online
[    0.213626] intel_mid_rpmsg rpmsg5: Probed rpmsg_ipc device rpmsg_ipc_command
[    0.213647] intel_mid_rpmsg rpmsg5: Allocating rpmsg_instance
[    0.213703] intel_mid_rpmsg rpmsg6: Probed rpmsg_ipc device rpmsg_ipc_simple_command
[    0.213724] intel_mid_rpmsg rpmsg6: Allocating rpmsg_instance
[    0.213776] intel_mid_rpmsg rpmsg7: Probed rpmsg_ipc device rpmsg_ipc_raw_command
[    0.213796] intel_mid_rpmsg rpmsg7: Allocating rpmsg_instance
[    0.214307] Advanced Linux Sound Architecture Driver Initialized.
[    0.214326] Intel MID platform detected, using MID PCI ops
[    0.214338] PCI: Probing PCI hardware
[    0.214354] PCI: root bus 00: using default resources
[    0.214369] PCI: Probing PCI hardware (bus 00)
[    0.214633] PCI host bridge to bus 0000:00
[    0.214661] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.214684] pci_bus 0000:00: root bus resource [mem 0x00000000-0xfffffffff]
[    0.214703] pci_bus 0000:00: No busn resource found for root bus, will use [bus 00-ff]
[    0.214763] pci 0000:00:00.0: [8086:1170] type 00 class 0x060000
[    0.215157] pci 0000:00:01.0: [8086:1190] type 00 class 0x080501
[    0.215227] pci 0000:00:01.0: reg 10: [mem 0xff3fc000-0xff3fc0ff]
[    0.215441] pci 0000:00:01.0: PME# supported from D0 D3hot
[    0.215788] pci 0000:00:01.2: [8086:1190] type 00 class 0x080501
[    0.215856] pci 0000:00:01.2: reg 10: [mem 0xff3fa000-0xff3fa0ff]
[    0.216069] pci 0000:00:01.2: PME# supported from D0 D3hot
[    0.216398] pci 0000:00:01.3: [8086:1190] type 00 class 0x080501
[    0.216466] pci 0000:00:01.3: reg 10: [mem 0xff3fb000-0xff3fb0ff]
[    0.216679] pci 0000:00:01.3: PME# supported from D0 D3hot
[    0.217037] pci 0000:00:02.0: [8086:1182] type 00 class 0x038000
[    0.217107] pci 0000:00:02.0: reg 10: [mem 0xc0000000-0xc1ffffff]
[    0.217169] pci 0000:00:02.0: reg 18: [mem 0x80000000-0x8fffffff]
[    0.217229] pci 0000:00:02.0: reg 20: [io  0x7ff8-0x7fff]
[    0.217654] pci 0000:00:04.0: [8086:1191] type 00 class 0x070002
[    0.217720] pci 0000:00:04.0: reg 10: [mem 0xff010000-0xff01007f]
[    0.217933] pci 0000:00:04.0: PME# supported from D0 D3hot
[    0.218276] pci 0000:00:04.1: [8086:1191] type 00 class 0x070002
[    0.218344] pci 0000:00:04.1: reg 10: [mem 0xff010080-0xff0100ff]
[    0.218556] pci 0000:00:04.1: PME# supported from D0 D3hot
[    0.218897] pci 0000:00:04.2: [8086:1191] type 00 class 0x070002
[    0.218964] pci 0000:00:04.2: reg 10: [mem 0xff010100-0xff01017f]
[    0.219177] pci 0000:00:04.2: PME# supported from D0 D3hot
[    0.219507] pci 0000:00:04.3: [8086:1191] type 00 class 0x070002
[    0.219575] pci 0000:00:04.3: reg 10: [mem 0xff010180-0xff0101ff]
[    0.219788] pci 0000:00:04.3: PME# supported from D0 D3hot
[    0.220144] pci 0000:00:05.0: [8086:1192] type 00 class 0x070002
[    0.220211] pci 0000:00:05.0: reg 10: [mem 0xff010400-0xff0107ff]
[    0.220424] pci 0000:00:05.0: PME# supported from D0 D3hot
[    0.220756] pci 0000:00:06.0: [8086:1193] type 00 class 0x088000
[    0.220824] pci 0000:00:06.0: reg 10: [mem 0xff2a0000-0xff2a0fff]
[    0.221036] pci 0000:00:06.0: PME# supported from D0 D3hot
[    0.221418] pci 0000:00:06.1: [8086:1193] type 00 class 0x088000
[    0.221486] pci 0000:00:06.1: reg 10: [mem 0xff2a1000-0xff2a1fff]
[    0.221699] pci 0000:00:06.1: PME# supported from D0 D3hot
[    0.222060] pci 0000:00:07.0: [8086:1194] type 00 class 0x088000
[    0.222128] pci 0000:00:07.0: reg 10: [mem 0xff188000-0xff188fff]
[    0.222341] pci 0000:00:07.0: PME# supported from D0 D3hot
[    0.222677] pci 0000:00:07.1: [8086:1194] type 00 class 0x088000
[    0.222782] pci 0000:00:07.1: reg 10: [mem 0xff189000-0xff189fff]
[    0.223000] pci 0000:00:07.1: PME# supported from D0 D3hot
[    0.223342] pci 0000:00:07.2: [8086:1194] type 00 class 0x088000
[    0.223409] pci 0000:00:07.2: reg 10: [mem 0xff18a000-0xff18afff]
[    0.223622] pci 0000:00:07.2: PME# supported from D0 D3hot
[    0.223979] pci 0000:00:08.0: [8086:1195] type 00 class 0x078000
[    0.224047] pci 0000:00:08.0: reg 10: [mem 0xff18b000-0xff18bfff]
[    0.224259] pci 0000:00:08.0: PME# supported from D0 D3hot
[    0.224585] pci 0000:00:08.1: [8086:1195] type 00 class 0x078000
[    0.224653] pci 0000:00:08.1: reg 10: [mem 0xff18c000-0xff18cfff]
[    0.224865] pci 0000:00:08.1: PME# supported from D0 D3hot
[    0.225203] pci 0000:00:08.2: [8086:1195] type 00 class 0x078000
[    0.225271] pci 0000:00:08.2: reg 10: [mem 0xff18d000-0xff18dfff]
[    0.225483] pci 0000:00:08.2: PME# supported from D0 D3hot
[    0.225812] pci 0000:00:08.3: [8086:1195] type 00 class 0x078000
[    0.225879] pci 0000:00:08.3: reg 10: [mem 0xff18e000-0xff18efff]
[    0.226091] pci 0000:00:08.3: PME# supported from D0 D3hot
[    0.226445] pci 0000:00:09.0: [8086:1196] type 00 class 0x078000
[    0.226513] pci 0000:00:09.0: reg 10: [mem 0xff18f000-0xff18ffff]
[    0.226726] pci 0000:00:09.0: PME# supported from D0 D3hot
[    0.227064] pci 0000:00:09.1: [8086:1196] type 00 class 0x078000
[    0.227131] pci 0000:00:09.1: reg 10: [mem 0xff190000-0xff190fff]
[    0.227344] pci 0000:00:09.1: PME# supported from D0 D3hot
[    0.227674] pci 0000:00:09.2: [8086:1196] type 00 class 0x078000
[    0.227742] pci 0000:00:09.2: reg 10: [mem 0xff191000-0xff191fff]
[    0.227954] pci 0000:00:09.2: PME# supported from D0 D3hot
[    0.228312] pci 0000:00:0a.0: [8086:1197] type 00 class 0x078000
[    0.228380] pci 0000:00:0a.0: reg 10: [mem 0xff3f8000-0xff3f8fff]
[    0.228592] pci 0000:00:0a.0: PME# supported from D0 D3hot
[    0.228932] pci 0000:00:0b.0: [8086:1198] type 00 class 0x108000
[    0.228999] pci 0000:00:0b.0: reg 10: [mem 0xf9038000-0xf903ffff]
[    0.229212] pci 0000:00:0b.0: PME# supported from D0 D3hot
[    0.229543] pci 0000:00:0c.0: [8086:1199] type 00 class 0x088000
[    0.229610] pci 0000:00:0c.0: reg 10: [mem 0xff008000-0xff008fff]
[    0.229653] pci 0000:00:0c.0: reg 14: [mem 0x000ddcc0-0x000ddccf]
[    0.229846] pci 0000:00:0c.0: PME# supported from D0 D3hot
[    0.230190] pci 0000:00:0d.0: [8086:119a] type 00 class 0x040100
[    0.230259] pci 0000:00:0d.0: reg 10: [mem 0x05e00000-0x05ffffff]
[    0.230301] pci 0000:00:0d.0: reg 14: [mem 0xff340000-0xff343fff]
[    0.230342] pci 0000:00:0d.0: reg 18: [mem 0xff344000-0xff344fff]
[    0.230382] pci 0000:00:0d.0: reg 1c: [mem 0xff2c0000-0xff2dffff]
[    0.230422] pci 0000:00:0d.0: reg 20: [mem 0xff300000-0xff33ffff]
[    0.230559] pci 0000:00:0d.0: PME# supported from D0 D3hot
[    0.230892] pci 0000:00:0e.0: [8086:119b] type 00 class 0x088000
[    0.230959] pci 0000:00:0e.0: reg 10: [mem 0xff298000-0xff29bfff]
[    0.231000] pci 0000:00:0e.0: reg 14: [mem 0xff2a2000-0xff2a2fff]
[    0.231194] pci 0000:00:0e.0: PME# supported from D0 D3hot
[    0.231545] pci 0000:00:11.0: [8086:119e] type 00 class 0x0c0320
[    0.231658] pci 0000:00:11.0: reg 10: [mem 0xf9100000-0xf911ffff]
[    0.231873] pci 0000:00:11.0: PME# supported from D0 D3hot
[    0.232220] pci 0000:00:12.0: [8086:119f] type 00 class 0x118000
[    0.232288] pci 0000:00:12.0: reg 10: [mem 0xf9009000-0xf9009fff]
[    0.232331] pci 0000:00:12.0: reg 14: [mem 0xf90a0000-0xf90affff]
[    0.232372] pci 0000:00:12.0: reg 18: [mem 0xfa000000-0xfaffffff]
[    0.232547] pci 0000:00:12.0: PME# supported from D0 D3hot
[    0.232934] pci 0000:00:13.0: [8086:11a0] type 00 class 0x0b4000
[    0.233002] pci 0000:00:13.0: reg 10: [mem 0xff009000-0xff009fff]
[    0.233215] pci 0000:00:13.0: PME# supported from D0 D3hot
[    0.233563] pci 0000:00:14.0: [8086:11a1] type 00 class 0x0b4000
[    0.233631] pci 0000:00:14.0: reg 10: [mem 0xff00b000-0xff00bfff]
[    0.233844] pci 0000:00:14.0: PME# supported from D0 D3hot
[    0.234189] pci 0000:00:15.0: [8086:11a2] type 00 class 0x088000
[    0.234256] pci 0000:00:15.0: reg 10: [mem 0xff192000-0xff192fff]
[    0.234469] pci 0000:00:15.0: PME# supported from D0 D3hot
[    0.234802] pci 0000:00:16.0: [8086:11a3] type 00 class 0x0b4000
[    0.234870] pci 0000:00:16.0: reg 10: [mem 0xff0d9000-0xff0d90ff]
[    0.235083] pci 0000:00:16.0: PME# supported from D0 D3hot
[    0.235429] pci 0000:00:16.1: [8086:11a4] type 00 class 0x0b4000
[    0.235497] pci 0000:00:16.1: reg 10: [mem 0x04819000-0x04898fff]
[    0.235539] pci 0000:00:16.1: reg 14: [mem 0x04919000-0x04920fff]
[    0.235732] pci 0000:00:16.1: PME# supported from D0 D3hot
[    0.236103] pci 0000:00:17.0: [8086:11a5] type 00 class 0x088000
[    0.236169] pci 0000:00:17.0: reg 10: [mem 0xff013000-0xff013fff]
[    0.236382] pci 0000:00:17.0: PME# supported from D0 D3hot
[    0.236719] pci 0000:00:18.0: [8086:11a6] type 00 class 0x038000
[    0.236971] pci 0000:00:18.0: PME# supported from D0 D3hot
[    0.237349] pci_bus 0000:00: busn_res: [bus 00-ff] end is updated to 00
[    0.237514] PCI: pci_cache_line_size set to 64 bytes
[    0.237781] e820: reserve RAM buffer [mem 0x00098000-0x0009ffff]
[    0.237801] e820: reserve RAM buffer [mem 0x3f500000-0x3fffffff]
[    0.238550] Bluetooth: Core ver 2.16
[    0.238634] NET: Registered protocol family 31
[    0.238650] Bluetooth: HCI device and connection manager initialized
[    0.238680] Bluetooth: HCI socket layer initialized
[    0.238706] Bluetooth: L2CAP socket layer initialized
[    0.238802] Bluetooth: SCO socket layer initialized
[    0.239495] cfg80211: Calling CRDA to update world regulatory domain
[    0.240747] intel_scu_flis platform device created
[    0.240826] hsu core clock 38 M
[    0.240997] intel_pmu_driver 0000:00:14.0: PMU DRIVER Probe called
[    0.242277] intel_pmu_driver 0000:00:14.0: after pmu initialization
[    0.242408] Switching to clocksource refined-jiffies
[    0.498572] intel_scu_flis rpmsg12: Probed flis rpmsg device
[    0.498599] intel_scu_flis rpmsg12: Allocating rpmsg_instance
[    0.498769] intel_scu_flis intel_scu_flis: scu flis probed
[    0.511252] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.511280] pci_bus 0000:00: resource 5 [mem 0x00000000-0xfffffffff]
[    0.511509] NET: Registered protocol family 2
[    0.512461] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.512668] TCP bind hash table entries: 8192 (order: 5, 163840 bytes)
[    0.512960] TCP: Hash tables configured (established 8192 bind 8192)
[    0.513056] TCP: reno registered
[    0.513085] UDP hash table entries: 512 (order: 2, 24576 bytes)
[    0.513152] UDP-Lite hash table entries: 512 (order: 2, 24576 bytes)
[    0.513569] NET: Registered protocol family 1
[    0.514043] RPC: Registered named UNIX socket transport module.
[    0.514061] RPC: Registered udp transport module.
[    0.514074] RPC: Registered tcp transport module.
[    0.514086] RPC: Registered tcp NFSv4.1 backchannel transport module.
[    0.516587] PCI: CLS 0 bytes, default 64
[    0.516676] intel_scu_pmic rpmsg8: Probed pmic rpmsg device
[    0.516697] intel_scu_pmic rpmsg8: Allocating rpmsg_instance
[    0.517371] intel_scu_watchdog_evo rpmsg13: Probed watchdog rpmsg device
[    0.517394] intel_scu_watchdog_evo rpmsg13: Allocating rpmsg_instance
[    0.518044] intel_scu_ipcutil rpmsg11: Probed ipcutil rpmsg device
[    0.518068] intel_scu_ipcutil rpmsg11: Allocating rpmsg_instance
[    0.518221] (oshob) base addr = 0xfffff000
[    0.518237] (oshob) identified platform = INTEL_MID_CPU_CHIP_TANGIER
[    0.518253] (oshob) oshob version = 1.4
[    0.518304] (latest extend oshob) osnib ptr = 0xfffff800
[    0.518319] Using latest extended oshob structure size = 1024 bytes
[    0.518332] OSNIB Intel size = 32 bytes OEMNIB size = 96 bytes
[    0.518346] (extend oshob) SCU buffer size is 16 bytes
[    0.518414] [BOOT] RESETSRC0=0x00 RESETSRC1=0x00 (PMIT interrupt tree)
[    0.518485] [BOOT] SCU_TR[0]=0x00020011
[    0.518500] [BOOT] SCU_TR[1]=0x00000220
[    0.518513] [BOOT] SCU_TR[2]=0x00000000
[    0.518525] [BOOT] SCU_TR[3]=0x00000000
[    0.518537] [BOOT] IA_TR=0x00000000 (oshob)
[    0.518873] [BOOT] RR=[fastboot] WD=0x00 ALARM=0x00 (osnib)
[    0.518888] [BOOT] WAKESRC=[real reset] (osnib)
[    0.518903] [BOOT] RESETSRC0=0x00 RESETSRC1=0x02 (osnib)
[    0.518971] OEMNIB interface registered to debugfs
[    0.519331] iio_basincove_gpadc rpmsg0: Probed bcove_gpadc rpmsg device
[    0.519994] bcove_adc bcove_adc: bcove adc probed
[    0.520948] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    0.523041] cryptomgr_test (31) used greatest stack depth: 7548 bytes left
[    0.525447] vprog1: 1500 <--> 2800 mV at 2800 mV normal 
[    0.526175] vprog2: 1500 <--> 2850 mV at 2850 mV normal 
[    0.526873] vprog3: 1050 <--> 2800 mV at 1050 mV normal 
[    0.528207] audit: initializing netlink socket (disabled)
[    0.528270] type=2000 audit(946684808.450:1): initialized
[    0.676890] bounce pool size: 64 pages
[    0.694398] NFS: Registering the id_resolver key type
[    0.694464] Key type id_resolver registered
[    0.694481] Key type id_legacy registered
[    0.694512] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[    0.695009] fuse init (API version 7.22)
[    0.695786] msgmni has been set to 1677
[    0.696359] SELinux:  Registering netfilter hooks
[    0.697517] cryptomgr_test (48) used greatest stack depth: 7368 bytes left
[    0.699439] Key type asymmetric registered
[    0.699460] Asymmetric key parser 'x509' registered
[    0.699569] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.699825] io scheduler noop registered
[    0.700098] io scheduler cfq registered (default)
[    0.700115] list_sort_test: start testing list_sort()
[    0.703322] intel_idle: MWAIT substates: 0x33000020
[    0.703342] intel_idle: v0.4 model 0x4A
[    0.703357] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.703619] intel_mid_dma 0000:00:0e.0: setting latency timer to 64
[    0.704257] intel_mid_dma 0000:00:15.0: setting latency timer to 64
[    0.705924] HSU DMA 0000:00:05.0: FUNC: 0 driver: 5 addr:ff010400 len:400
[    0.706175] HSU serial 0000:00:04.0: FUNC: 0 driver: 0 addr:ff010000 len:80
[    0.706232] HSU serial 0000:00:04.1: FUNC: 1 driver: 0 addr:ff010080 len:80
[    0.706308] Found a Intel HSU
[    0.707156] 0000:00:04.1: ttyMFD0 at MMIO 0xff010080 (irq = 28) is a hsu_bt_port_p
[    0.707690] HSU serial 0000:00:04.2: FUNC: 2 driver: 0 addr:ff010100 len:80
[    0.707769] Found a Intel HSU
[    0.708591] 0000:00:04.2: ttyMFD1 at MMIO 0xff010100 (irq = 29) is a hsu_uart1_port_p
[    0.709147] HSU serial 0000:00:04.3: FUNC: 3 driver: 0 addr:ff010180 len:80
[    0.709227] Found a Intel HSU
[    0.709893] 0000:00:04.3: ttyMFD2 at MMIO 0xff010180 (irq = 54) is a hsu_uart2_port_p
[    0.714213] console [ttyMFD2] enabled
[    0.715344] Non-volatile memory driver v1.3
[    0.716028] Linux agpgart interface v0.103
[    0.716540] [drm] Initialized drm 1.1.0 20060810
[    0.730513] brd: module loaded
[    0.737990] loop: module loaded
[    0.740884] emmc_ipanic: init success
[    0.741661] tun: Universal TUN/TAP device driver, 1.6
[    0.741680] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.742117] usbcore: registered new interface driver asix
[    0.742199] usbcore: registered new interface driver cdc_subset
[    0.742330] usbcore: registered new interface driver cdc_ncm
[    0.742589] dwc3_otg 0000:00:11.0: setting latency timer to 64
[    0.744745] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.745065] usbcore: registered new interface driver cdc_acm
[    0.745082] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
[    0.745196] usbcore: registered new interface driver usb-storage
[    0.745385] usbcore: registered new interface driver usbserial
[    0.745456] usbcore: registered new interface driver pl2303
[    0.745524] usbserial: USB Serial support registered for pl2303
[    0.746475] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0
[    0.746631] rtc_cmos rtc_cmos: alarms up to one day, 114 bytes nvram
[    0.746686] i2c /dev entries driver
[    0.747666] pca953x 1-0020: failed reading register
[    0.752580] pca953x: probe of 1-0020 failed with error -121
[    0.752868] pca953x 1-0021: failed reading register
[    0.752956] pca953x: probe of 1-0021 failed with error -121
[    0.757941] pca953x 1-0022: failed reading register
[    0.758027] pca953x: probe of 1-0022 failed with error -121
[    0.763062] pca953x 1-0023: failed reading register
[    0.767877] pca953x: probe of 1-0023 failed with error -121
[    0.902764] coretemp: Enabled Aux0/Aux1 interrupts for coretemp
[    0.902894] coretemp: Enabled Aux0/Aux1 interrupts for coretemp
[    1.002415] MCU detected and ready to used!
[    1.002541] bcove_thrm rpmsg1: Probed mrfl_thermal rpmsg device
[    1.008573] thermal thermal_zone0: failed to read out thermal zone 0
[    1.009722] thermal thermal_zone2: failed to read out thermal zone 2
[    1.012403] Bluetooth: HCI UART driver ver 2.2
[    1.012424] Bluetooth: HCI H4 protocol initialized
[    1.012888] cpuidle: using governor ladder
[    1.013498] cpuidle: using governor menu
[    1.013568] sdhci: Secure Digital Host Controller Interface driver
[    1.013582] sdhci: Copyright(c) Pierre Ossman
[    1.013657] sdhci-pci 0000:00:01.0: SDHCI controller found [8086:1190] (rev 1)
[    1.013757] flis_addr mapped addr: f8496900
[    1.013871] sdhci-pci 0000:00:01.0: rte_addr mapped addr: f849a000
[    1.013932] sdhci-pci 0000:00:01.0: setting latency timer to 64
[    1.013962] mmc0: no vqmmc regulator found
[    1.107869] mmc0: BKOPS_EN bit is not set
[    1.416632] mmc0: new HS200 MMC card at address 0001
[    1.417437] mmcblk0: mmc0:0001 H4G1d 3.64 GiB 
[    1.417833] mmcblk0boot0: mmc0:0001 H4G1d partition 1 4.00 MiB
[    1.418205] mmcblk0boot1: mmc0:0001 H4G1d partition 2 4.00 MiB
[    1.418596] mmcblk0rpmb: mmc0:0001 H4G1d partition 3 4.00 MiB
[    1.424336]  mmcblk0: p1 p2 p3 p4 p5 p6 p7 p8 p9 p10
[    1.432550]  mmcblk0boot1: unknown partition table
[    1.436180]  mmcblk0boot0: unknown partition table
[    1.436577] mmc0: SDHCI controller on PCI [0000:00:01.0] using ADMA
[    1.455872] emmc_ipanic: panic partition found, label:panic, device:mmcblk0p6
[    1.534593] Switching to clocksource tsc
[    1.570243] emmc_ipanic: emmc_panic_notify_add: Data available in panic partition
[    1.570288] emmc_ipanic: emmc_panic_notify_add: proc entry created: emmc_ipanic_header
[    1.570308] emmc_ipanic: emmc_panic_notify_add: log file 0(1024, 44237)
[    1.570336] emmc_ipanic: emmc_panic_notify_add: proc entry created: emmc_ipanic_console
[    1.570353] emmc_ipanic: emmc_panic_notify_add: log file 1(4286578688, 0)
[    1.570367] emmc_ipanic: emmc_panic_notify_add: empty log file 1
[    1.570382] emmc_ipanic: emmc_panic_notify_add: log file 2(4286578688, 0)
[    1.570395] emmc_ipanic: emmc_panic_notify_add: empty log file 2
[    1.570479] sdhci-pci 0000:00:01.2: SDHCI controller found [8086:1190] (rev 1)
[    1.594829] sdhci-pci 0000:00:01.2: setting latency timer to 64
[    1.594861] mmc1: no vqmmc regulator found
[    1.595243] mmc1: SDHCI controller on PCI [0000:00:01.2] using ADMA
[    1.595417] sdhci-pci 0000:00:01.3: SDHCI controller found [8086:1190] (rev 1)
[    1.595520] vwlan gpio 96
[    1.595889] vwlan: 1800 mV 
[    1.596144] sdhci-pci 0000:00:01.3: setting latency timer to 64
[    1.596174] mmc2: no vqmmc regulator found
[    1.596599] mmc2: SDHCI controller on PCI [0000:00:01.3] using ADMA
[    1.605191] hidraw: raw HID events driver (C) Jiri Kosina
[    1.605839] usbcore: registered new interface driver usbhid
[    1.605858] usbhid: USB HID core driver
[    1.605936] intel_scu_fw_update rpmsg10: Probed fw_update rpmsg device
[    1.605957] intel_scu_fw_update rpmsg10: Allocating rpmsg_instance
[    1.611115] usbcore: registered new interface driver snd-usb-audio
[    1.612221] snd_soc_sst_platform: Enter:sst_soc_probe
[    1.971155] snd-soc-dummy snd-soc-dummy: ASoC: Failed to create platform debugfs directory
[    1.971395] merr_dpcm_dummy merr_dpcm_dummy.0:  snd-soc-dummy-dai <-> Headset-cpu-dai mapping ok
[    1.971531] merr_dpcm_dummy merr_dpcm_dummy.0:  snd-soc-dummy-dai <-> ssp2-codec mapping ok
[    1.971658] merr_dpcm_dummy merr_dpcm_dummy.0:  snd-soc-dummy-dai <-> snd-soc-dummy-dai mapping ok
[    1.973546] snd_merr_dpcm_probe successful
[    1.973633] snd_intel_sst: INFO: ******** SST DRIVER loading.. Ver: 3.0.8
[    1.974192] snd_intel_sst: Got drv data max stream 25
[    1.976963] snd_intel_sst: intel_sst_probe successfully done!
[    1.977027] snd_intel_sst: runtime_idle called
[    1.977046] snd_intel_sst: runtime_suspend called
[    1.977326] oprofile: using NMI interrupt.
[    1.977484] Netfilter messages via NETLINK v0.30.
[    1.977578] nf_conntrack version 0.5.0 (15352 buckets, 61408 max)
[    1.978440] NF_TPROXY: Transparent proxy support initialized, version 4.1.0
[    1.978457] NF_TPROXY: Copyright (c) 2006-2007 BalaBit IT Ltd.
[    1.979047] ip_tables: (C) 2000-2006 Netfilter Core Team
[    1.979373] TCP: cubic registered
[    1.979389] Initializing XFRM netlink socket
[    1.980546] NET: Registered protocol family 10
[    1.981873] ip6_tables: (C) 2000-2006 Netfilter Core Team
[    1.982196] sit: IPv6 over IPv4 tunneling driver
[    1.983138] NET: Registered protocol family 17
[    1.983200] NET: Registered protocol family 15
[    1.983356] Bridge firewalling registered
[    1.983666] Bluetooth: RFCOMM TTY layer initialized
[    1.983726] Bluetooth: RFCOMM socket layer initialized
[    1.983743] Bluetooth: RFCOMM ver 1.11
[    1.983758] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    1.983771] Bluetooth: BNEP filters: protocol multicast
[    1.983801] Bluetooth: BNEP socket layer initialized
[    1.983816] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[    1.983843] Bluetooth: HIDP socket layer initialized
[    1.983999] l2tp_core: L2TP core driver, V2.0
[    1.984073] Key type dns_resolver registered
[    1.985837] Using IPI No-Shortcut mode
[    1.985907] info[ 0]: name = power_btn, gpio = -1
[    1.985924] info[ 1]: name = SW1UI4, gpio = 61
[    1.987028] registered taskstats version 1
[    1.989367] intel_mid_ssp_spi_unified 0000:00:07.0: found PCI SSP controller (ID: 8086h:1194h cfg: 0dh)
[    1.990277] intel_mid_ssp_spi_unified 0000:00:07.0: register with SPI framework (bus spi3)
[    1.990440] intel_mid_ssp_spi_unified 0000:00:07.0: master is unqueued, this is deprecated
[    1.990469] intel_mid_ssp_spi_unified 0000:00:07.0: Unbalanced pm_runtime_enable!
[    1.994922] intel_mid_ssp_spi_unified 0000:00:07.1: found PCI SSP controller (ID: 8086h:1194h cfg: 15h)
[    1.995772] intel_mid_ssp_spi_unified 0000:00:07.1: register with SPI framework (bus spi5)
[    1.995945] intel_mid_ssp_spi_unified 0000:00:07.1: master is unqueued, this is deprecated
[    1.997738] intel_mid_ssp_spi_unified 0000:00:07.1: Unbalanced pm_runtime_enable!
[    2.005111] intel_mid_ssp_spi_unified 0000:00:07.2: found PCI SSP controller (ID: 8086h:1194h cfg: 19h)
[    2.005948] intel_mid_ssp_spi_unified 0000:00:07.2: register with SPI framework (bus spi6)
[    2.006110] intel_mid_ssp_spi_unified 0000:00:07.2: master is unqueued, this is deprecated
[    2.006138] intel_mid_ssp_spi_unified 0000:00:07.2: Unbalanced pm_runtime_enable!
[    2.015044] console [netcon0] enabled
[    2.015062] netconsole: network logging started
[    2.015597] input: gpio-keys as /devices/platform/gpio-keys/input/input0
[    2.016225] rtc_cmos rtc_cmos: setting system clock to 2000-01-01 00:00:10 UTC (946684810)
[    2.016314] pmic_ccsm rpmsg3: Probed pmic_ccsm rpmsg device
[    2.016536] pmic_ccsm pmic_ccsm: PMIC-ID: c9
[    2.016560] pmic_ccsm pmic_ccsm: Error reading battery profile from battid frmwrk
[    2.025231] pmic_ccsm pmic_ccsm: Battery Zone changed. Current zone is 5
[    2.027990] APIC ID: 0
[    2.028008] APIC ID: 2
[    2.028069] Num p-states 2
[    2.028087] State [0]: core_frequency[500] transition_latency[100] control[0x527]
[    2.028103] State [1]: core_frequency[500] transition_latency[100] control[0x527]
[    2.028261] Num p-states 2
[    2.028280] State [0]: core_frequency[500] transition_latency[100] control[0x527]
[    2.028295] State [1]: core_frequency[500] transition_latency[100] control[0x527]
[    2.028724] msic_power_btn rpmsg2: Probed mid_pb rpmsg device
[    2.028790] msic_power_btn mid_powerbtn: Probed mid powerbutton devivce
[    2.029145] input: mid_powerbtn as /devices/platform/mid_powerbtn/input/input1
[    2.030696] ALSA device list:
[    2.030716]   #0: Loopback 1
[    2.030730]   #1: dummy-audio
[    2.034703] pmic_ccsm pmic_ccsm: Battery Over heat exception
[    2.034771] pmic_ccsm pmic_ccsm: USB VBUS Detected. Notifying OTG driver
[    2.034795] pmic_ccsm pmic_ccsm: Battery0 temperature outside boundary
[    2.121857] EXT4-fs (mmcblk0p8): INFO: recovery required on readonly filesystem
[    2.121882] EXT4-fs (mmcblk0p8): write access will be enabled during recovery
[    2.140377] mmc2: queuing unknown CIS tuple 0x91 (3 bytes)
[    2.140416] mmc2: new ultra high speed DDR50 SDIO card at address 0001
[    2.152481] EXT4-fs (mmcblk0p8): recovery complete
[    2.153810] EXT4-fs (mmcblk0p8): mounted filesystem with ordered data mode. Opts: (null)
[    2.153894] VFS: Mounted root (ext4 filesystem) readonly on device 179:8.
[    2.154696] devtmpfs: mounted
[    2.155152] Freeing unused kernel memory: 572k freed
[    2.156059] Write protecting the kernel text: 7068k
[    2.156869] Write protecting the kernel read-only data: 2944k
[    2.156882] NX-protecting the kernel data: 5220k
[    2.382340] systemd[1]: systemd 213 running in system mode. (-PAM -AUDIT -SELINUX +IMA +SYSVINIT -LIBCRYPTSETUP -GCRYP)
[    2.383803] systemd[1]: Detected architecture 'x86'.
[    2.427286] systemd[1]: Set hostname to <edison>.
[    2.432404] systemd[1]: Hardware watchdog 'Intel_SCU IOH Watchdog', version 0
[    2.432486] systemd[1]: Set hardware watchdog to 1min 30s.
[    2.448597] systemd-system- (96) used greatest stack depth: 6364 bytes left
[    2.453781] systemd-fstab-generator[101]: Checking was requested for "rootfs", but it is not a device.
[    2.653951] systemd[1]: Configuration file /lib/systemd/system/connman-init.service is marked executable. Please remov.
[    2.697224] systemd[1]: Expecting device dev-ttyMFD2.device...
[    2.744943] systemd[1]: Starting Forward Password Requests to Wall Directory Watch.
[    2.745584] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    2.745713] systemd[1]: Starting Remote File Systems.
[    2.794810] systemd[1]: Reached target Remote File Systems.
[    2.794930] systemd[1]: Expecting device dev-disk-by\x2dpartlabel-factory.device...
[    2.844825] systemd[1]: Expecting device sys-subsystem-net-devices-usb0.device...
[    2.894865] systemd[1]: Starting Dispatch Password Requests to Console Directory Watch.
[    2.895308] systemd[1]: Started Dispatch Password Requests to Console Directory Watch.
[    2.895422] systemd[1]: Starting Paths.
[    2.944790] systemd[1]: Reached target Paths.
[    2.944919] systemd[1]: Starting Swap.
[    2.994778] systemd[1]: Reached target Swap.
[    2.994898] systemd[1]: Starting boot.automount.
[    3.056620] systemd[1]: boot.automount: Directory /boot to mount over is not empty, mounting anyway.
[    3.104880] systemd[1]: Set up automount boot.automount.
[    3.105044] systemd[1]: Starting Root Slice.
[    3.224749] systemd[1]: Created slice Root Slice.
[    3.224879] systemd[1]: Starting User and Session Slice.
[    3.274776] systemd[1]: Created slice User and Session Slice.
[    3.274901] systemd[1]: Starting Delayed Shutdown Socket.
[    3.324734] systemd[1]: Listening on Delayed Shutdown Socket.
[    3.324853] systemd[1]: Starting /dev/initctl Compatibility Named Pipe.
[    3.374729] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    3.374877] systemd[1]: Starting udev Control Socket.
[    3.424720] systemd[1]: Listening on udev Control Socket.
[    3.424862] systemd[1]: Starting udev Kernel Socket.
[    3.474725] systemd[1]: Listening on udev Kernel Socket.
[    3.474872] systemd[1]: Starting Journal Socket.
[    3.524711] systemd[1]: Listening on Journal Socket.
[    3.524899] systemd[1]: Starting System Slice.
[    3.574722] systemd[1]: Created slice System Slice.
[    3.574860] systemd[1]: Mounting Temporary Directory...
[    3.690335] systemd[1]: Starting system-serial\x2dgetty.slice.
[    3.764804] systemd[1]: Created slice system-serial\x2dgetty.slice.
[    3.764957] systemd[1]: Starting system-getty.slice.
[    3.814721] systemd[1]: Created slice system-getty.slice.
[    3.880064] systemd[1]: Starting Load Kernel Modules...
[    3.998935] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    4.028989] dhd_module_init in
[    4.029020] found wifi platform device wlan
[    4.029127] Power-up adapter 'DHD generic adapter'
[    4.078819] systemd[1]: Starting udev Coldplug all Devices...
[    4.117021] systemd[1]: Mounted Huge Pages File System.
[    4.117239] systemd[1]: Mounting Debug File System...
[    4.141647] systemd[1]: Mounting POSIX Message Queue File System...
[    4.267526] systemd[1]: Starting Apply Kernel Variables...
[    4.318656] systemd[1]: Starting Journal Service...
[    4.362196] wifi_platform_set_power = 1
[    4.434662] systemd[1]: Started Journal Service.
[    4.564313] wifi_platform_bus_enumerate device present 1
[    4.590184] bcmsdh_sdmmc: bcmsdh_sdmmc_probe Enter
[    4.590425] bcmsdh_sdmmc: bcmsdh_sdmmc_probe Enter
[    4.590446] bus num (host idx)=2, slot num (rca)=1
[    4.590462] found adapter info 'DHD generic adapter'
[    4.601020] F1 signature OK, socitype:0x1 chip:0xa94c rev:0x2 pkg:0x0
[    4.602596] DHD: dongle ram size is set to 524288(orig 524288) at 0x0
[    4.604523] wifi_platform_get_mac_addr
[    4.604594] wifi_get_mac_addr_intel: unable to open /config/wifi/mac.txt
[    4.614505] wl_create_event_handler(): thread:wl_event_handler:76 started
[    4.614970] CFG80211-ERROR) wl_event_handler : tsk Enter, tsk = 0xf5fc1540
[    4.615043] dhd_attach(): thread:dhd_watchdog_thread:7b started
[    4.624372] dhd_attach(): thread:dhd_dpc:7c started
[    4.624407] dhd_deferred_work_init: work queue initialized 
[    4.624996] Dongle Host Driver, version 1.141.59 (r)
[    4.624996] Compiled in /data/jenkins_worker/workspace/edison-weekly/out/linux64/build/tmp/work/edison-poky-linux/bcm44
[    4.626104] Register interface [wlan0]  MAC: 00:00:00:00:00:00
[    4.626104] 
[    4.626131] dhd_prot_ioctl : bus is down. we have nothing to do
[    4.626744] bcmsdh_sdmmc: bcmsdh_sdmmc_probe Enter
[    4.626864] wifi_platform_set_power = 0
[    4.627941] wifi_platform_bus_enumerate device present 0
[    4.651817] EXT4-fs (mmcblk0p8): re-mounted. Opts: discard,barrier=1,data=ordered,noauto_da_alloc
[    4.665216] g_multi gadget: using random host ethernet address
[    4.666485] usb0: MAC 02:00:86:d5:27:b6
[    4.666508] usb0: HOST MAC 46:a7:f7:30:df:64
[    4.717077] g_multi gadget: Mass Storage Function, version: 2009/09/11
[    4.717104] g_multi gadget: Number of LUNs=1
[    4.717133]  lun0: LUN: file: /dev/mmcblk0p9
[    4.717346] g_multi gadget: Multifunction Composite Gadget
[    4.717367] g_multi gadget: g_multi ready
[    4.718538] systemd-modules (105) used greatest stack depth: 5468 bytes left
[    5.836060] systemd-udevd[142]: starting version 213
[    5.984984] g_multi gadget: high-speed config #2: Multifunction with CDC ECM
[    6.151861] systemd-journald[115]: Received request to flush runtime journal from PID 1
[    6.874457] EXT4-fs (mmcblk0p5): mounted filesystem without journal. Opts: discard,barrier=1,data=ordered,noauto_da_alc
[    9.917209] EXT4-fs (mmcblk0p10): mounted filesystem with ordered data mode. Opts: discard,barrier=1,data=ordered,noauc
[   11.133554] snd_intel_sst: runtime_resume called
[   11.166043] snd_intel_sst: FW Version 01.09.00.02
[   11.166070] snd_intel_sst: Build date Jan 14 2014 Time 20:08:46
[   11.166181] snd_intel_sst: Alloc for str 14 pipe 0xe
[   11.413426] snd_intel_sst: Free for str 14 pipe 0xe
[   11.415029] snd_intel_sst: runtime_idle called
[   11.461018] snd_intel_sst: Alloc for str 14 pipe 0xe
[   11.589307] snd_intel_sst: Free for str 14 pipe 0xe
[   11.590830] snd_intel_sst: runtime_idle called
[   11.609374] snd_intel_sst: Alloc for str 1 pipe 0x90
[   11.715117] snd_intel_sst: Alloc for str 14 pipe 0xe
[   11.727602] snd_intel_sst: Free for str 14 pipe 0xe
[   11.733025] snd_intel_sst: Alloc for str 14 pipe 0xe
[   11.738725] snd_intel_sst: Free for str 14 pipe 0xe
[   11.741518] snd_intel_sst: Free for str 1 pipe 0x90
[   11.745125] snd_intel_sst: runtime_idle called
[   11.841768] snd_intel_sst: Alloc for str 1 pipe 0x90
[   11.994848] snd_intel_sst: Start for str 1 pipe 0x90
[   12.000336] snd_intel_sst: Alloc for str 14 pipe 0xe
[   12.094691] snd_intel_sst: Start for str 14 pipe 0xe
[   17.408376] snd_intel_sst: Stop for str 14 pipe 0xe
[   17.408773] snd_intel_sst: Free for str 14 pipe 0xe
[   17.414372] snd_intel_sst: Stop for str 1 pipe 0x90
[   17.414880] snd_intel_sst: Free for str 1 pipe 0x90
[   17.418527] snd_intel_sst: runtime_idle called
[   19.412615] snd_intel_sst: runtime_suspend called
```