# Display Message

# Bootup Kernel Display Message

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
tail: can't open '/var/log/messages': No such file or directory
tail: no files
root@edison:~# dmesg                                                            
[    0.000000] Initializing cgroup subsys cpuset                                
[    0.000000] Initializing cgroup subsys cpu                                   
[    0.000000] Initializing cgroup subsys cpuacct                               
[    0.000000] Linux version 3.10.98-poky-edison+ (neck@flax) (gcc version 4.9.6
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
[    0.000000] DMI: Intel Corporation Merrifield/BODEGA BAY, BIOS 542 2015.01.28
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
[    0.000000]  gran_size: 64K  chunk_size: 512M        num_reg: 5      lose coG
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
[    0.000000] init_memory_mapping: [mem 0x37400000-0x375fffff]                 
[    0.000000]  [mem 0x37400000-0x375fffff] page 2M                             
[    0.000000] init_memory_mapping: [mem 0x34000000-0x373fffff]                 
[    0.000000]  [mem 0x34000000-0x373fffff] page 2M                             
[    0.000000] init_memory_mapping: [mem 0x00100000-0x03ffffff]                 
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k                             
[    0.000000]  [mem 0x00200000-0x03ffffff] page 2M                             
[    0.000000] init_memory_mapping: [mem 0x06000000-0x33ffffff]                 
[    0.000000]  [mem 0x06000000-0x33ffffff] page 2M                             
[    0.000000] init_memory_mapping: [mem 0x37600000-0x377fdfff]                 
[    0.000000]  [mem 0x37600000-0x377fdfff] page 4k                             
[    0.000000] BRK [0x01e31000, 0x01e31fff] PGTABLE                             
[    0.000000] BRK [0x01e32000, 0x01e32fff] PGTABLE                             
[    0.000000] 125MB HIGHMEM available.                                         
[    0.000000] 887MB LOWMEM available.                                          
[    0.000000]   mapped low ram: 0 - 377fe000                                   
[    0.000000]   low ram: 0 - 377fe000                                          
[    0.000000] BRK [0x01e33000, 0x01e33fff] PGTABLE                             
[    0.000000] Zone ranges:                                                     
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]                           
[    0.000000]   Normal   [mem 0x01000000-0x377fdfff]                           
[    0.000000]   HighMem  [mem 0x377fe000-0x3f4fffff]                           
[    0.000000] Movable zone start for each node                                 
[    0.000000] Early memory node ranges                                         
[    0.000000]   node   0: [mem 0x00001000-0x00097fff]                          
[    0.000000]   node   0: [mem 0x00100000-0x03ffffff]                          
[    0.000000]   node   0: [mem 0x06000000-0x3f4fffff]                          
[    0.000000] On node 0 totalpages: 251031                                     
[    0.000000] free_area_init_node: node 0, pgdat c1c666c0, node_mem_map f700e00
[    0.000000]   DMA zone: 32 pages used for memmap                             
[    0.000000]   DMA zone: 0 pages reserved                                     
[    0.000000]   DMA zone: 3991 pages, LIFO batch:0                             
[    0.000000]   Normal zone: 1744 pages used for memmap                        
[    0.000000]   Normal zone: 215038 pages, LIFO batch:31                       
[    0.000000]   HighMem zone: 251 pages used for memmap                        
[    0.000000]   HighMem zone: 32002 pages, LIFO batch:7                        
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
[    0.000000] setup_percpu: NR_CPUS:2 nr_cpumask_bits:2 nr_cpu_ids:2 nr_node_i1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f6fe8000 s33152 r0 d24192 u57344  
[    0.000000] pcpu-alloc: s33152 r0 d24192 u57344 alloc=14*4096                
[    0.000000] pcpu-alloc: [0] 0 [0] 1                                          
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pa5
[    0.000000] Kernel command line: rootwait root=PARTUUID=012b3303-34ac-284d-9y
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)             
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes) 
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)   
[    0.000000] Initializing CPU#0                                               
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f500)              
[    0.000000] Memory: 982480k/1037312k available (7105k kernel code, 21644k re)
[    0.000000] virtual kernel memory layout:                                    
    fixmap  : 0xfff8b000 - 0xfffff000   ( 464 kB)                               
    pkmap   : 0xff800000 - 0xffa00000   (2048 kB)                               
    vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)                               
    lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)                               
      .init : 0xc1c8b000 - 0xc1d17000   ( 560 kB)                               
      .data : 0xc18f066e - 0xc1c8a9c0   (3688 kB)                               
      .text : 0xc1200000 - 0xc18f066e   (7105 kB)                               
[    0.000000] Checking if this processor honours the WP bit even in supervisor.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1       
[    0.000000] Preemptible hierarchical RCU implementation.                     
[    0.000000]  Additional per-CPU info printed with stalls.                    
[    0.000000] NR_IRQS:2304 nr_irqs:512 16                                      
[    0.000000] CPU 0 irqstacks, hard=f6808000 soft=f680a000                     
[    0.000000] Console: colour dummy device 80x25                               
[    0.000000] kmemleak: Kernel memory leak detector disabled                   
[    0.000000] tsc: Detected 499.200 MHz processor                              
[    0.000009] Calibrating delay loop (skipped), value calculated using timer f)
[    0.000033] pid_max: default: 32768 minimum: 301                             
[    0.000259] Security Framework initialized                                   
[    0.000287] SELinux:  Initializing.                                          
[    0.000350] SELinux:  Starting in permissive mode                            
[    0.000428] Mount-cache hash table entries: 512                              
[    0.001564] Initializing cgroup subsys devices                               
[    0.001589] Initializing cgroup subsys freezer                               
[    0.001608] Initializing cgroup subsys blkio                                 
[    0.001624] Initializing cgroup subsys perf_event                            
[    0.001764] CPU: Physical Processor ID: 0                                    
[    0.001780] CPU: Processor Core ID: 0                                        
[    0.001799] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'             
ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)                
[    0.001820] mce: CPU supports 6 MCE banks                                    
[    0.001851] CPU0: Thermal monitoring enabled (TM1)                           
[    0.001896] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0                     
Last level dTLB entries: 4KB 128, 2MB 0, 4MB 0                                  
tlb_flushall_shift: 6                                                           
[    0.002339] Freeing SMP alternatives: 28k freed                              
[    0.002394] SFI: MCFG E34F6, 003C (v1  INTEL INTELFDK)                       
[    0.002414] ftrace: allocating 28147 entries in 55 pages                     
[    0.070009] Enabling APIC mode:  Flat.  Using 1 I/O APICs                    
[    0.070090] smpboot: CPU0: Genuine Intel(R) CPU   4000  @  500MHz (fam: 06, )
[    0.070138] TSC deadline timer enabled                                       
[    0.070200] Performance Events: no PEBS fmt2+, generic architected perfmon, .
[    0.070245] ... version:                3                                    
[    0.070259] ... bit width:              40                                   
[    0.070272] ... generic registers:      2                                    
[    0.070285] ... value mask:             000000ffffffffff                     
[    0.070298] ... max period:             000000007fffffff                     
[    0.070310] ... fixed-purpose events:   3                                    
[    0.070322] ... event mask:             0000000700000003                     
[    0.110679] ftrace: Allocated trace_printk buffers                           
[    0.161723] CPU 1 irqstacks, hard=f6b8c000 soft=f6b8e000                     
[    0.161744] smpboot: Booting Node   0, Processors  #1 OK                     
[    0.171955] Initializing CPU#1                                               
[    0.172914] Skipped synchronization checks as TSC is reliable.               
[    0.173366] NMI watchdog: enabled on all CPUs, permanently consumes one hw-P.
[    0.173449] Brought up 2 CPUs                                                
[    0.173470] smpboot: Total of 2 processors activated (1996.80 BogoMIPS)      
[    0.175407] devtmpfs: initialized                                            
[    0.186483] SFI: SFI sysfs interfaces init success                           
[    0.187048] regulator-dummy: no parameters                                   
[    0.187532] NET: Registered protocol family 16                               
[    0.189621] SFI OEMB Layout                                                  
[    0.189658]  OEMB signature               : OEMB                             
        OEMB length                  : 96                                       
        OEMB revision                : 5                                        
        OEMB checksum                : 0x8D                                     
        OEMB oem_id                  : UMGFDK                                   
        OEMB oem_table_id            : CFGINFO!                                 
        OEMB board_id                : 0x02                                     
        OEMB iafw version            : 002.012                                  
        OEMB val_hooks version       : 002.004                                  
        OEMB ia suppfw version       : 000.000                                  
        OEMB scu runtime version     : 176.073                                  
        OEMB ifwi version            : 237.015                                  
[    0.189762] intel_soc_thermal: IPC bus = 0, name =         soc_thrm, irq = 01
[    0.189978] IPC bus, name =        bcove_adc, irq = 0x32                     
[    0.190175] IPC bus, name =       bcove_thrm, irq = 0x34                     
[    0.190381] IPC bus, name =  bcove_power_btn, irq = 0x1e                     
[    0.190551] IPC bus, name =        pmic_ccsm, irq = 0x1b                     
[    0.190792] SDIO bus = 1, name = bcm43xx_clk_vmmc, ref_clock = 26000000, add1
[    0.190808] Using generic wifi platform data                                 
[    0.190824] wifi_platform_data: GPIO == 64                                   
[    0.190968] IPC bus, name =        msic_gpio, irq = 0x31                     
[    0.191146] I2C bus = 1, name =      pcal9555a-1, irq = 0x 0, addr = 0x20    
[    0.191181] I2C bus = 1, name =      pcal9555a-2, irq = 0x 0, addr = 0x21    
[    0.191213] I2C bus = 1, name =      pcal9555a-3, irq = 0x 0, addr = 0x22    
[    0.191244] I2C bus = 1, name =      pcal9555a-4, irq = 0x 0, addr = 0x23    
[    0.191277] SPI bus=5, name=         ads7955, irq=0x 0, max_freq=20000000, c0
[    0.191299] SPI bus=5, name=          spidev, irq=0x 0, max_freq=25000000, c1
[    0.191320] IPC bus, name =        mrfld_sst, irq = 0xff                     
[    0.191597] pgrr = 000003d5                                                  
[    0.192065] PCI: MMCONFIG for domain 0000 [bus 00-00] at [mem 0x3f500000-0x3)
[    0.192089] PCI: MMCONFIG at [mem 0x3f500000-0x3f5fffff] reserved in E820    
[    0.192102] PCI: Using MMCONFIG for extended config space                    
[    0.192115] PCI: Using configuration type 1 for base access                  
[    0.205192] bio: create slab <bio-0> at 0                                    
[    0.206698] vgaarb: loaded                                                   
[    0.207392] SCSI subsystem initialized                                       
[    0.207761] usbcore: registered new interface driver usbfs                   
[    0.207861] usbcore: registered new interface driver hub                     
[    0.208070] usbcore: registered new device driver usb                        
[    0.208363] media: Linux media interface: v0.10                              
[    0.208443] Linux video capture interface: v2.00                             
[    0.208514] pps_core: LinuxPPS API ver. 1 registered                         
[    0.208529] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giom>
[    0.208568] PTP clock support registered                                     
[    0.209067]  remoteproc0: intel_rproc_scu is available                       
[    0.209088]  remoteproc0: Note: remoteproc is still under development and co.
[    0.209104]  remoteproc0: THE BINARY FORMAT IS NOT YET FINALIZED, and backwa.
[    0.209524]  remoteproc0: registered virtio0 (type 7)                        
[    0.209775]  remoteproc0: powering up intel_rproc_scu                        
[    0.209803]  remoteproc0: Booting fw image intel_mid/intel_mid_remoteproc.fw6
[    0.209843] Started intel scu remote processor                               
[    0.209861]  remoteproc0: remote processor intel_rproc_scu is now up         
[    0.210211] virtio_rpmsg_bus virtio0: creating channel rpmsg_bcove_adc addr 4
[    0.210403] virtio_rpmsg_bus virtio0: creating channel rpmsg_mrfl_thermal ad5
[    0.210575] virtio_rpmsg_bus virtio0: creating channel rpmsg_mid_powerbtn ad0
[    0.210742] virtio_rpmsg_bus virtio0: creating channel rpmsg_pmic_ccsm addr 9
[    0.210921] virtio_rpmsg_bus virtio0: creating channel rpmsg_msic_gpio addr 5
[    0.211090] virtio_rpmsg_bus virtio0: creating channel rpmsg_ipc_command add0
[    0.211258] virtio_rpmsg_bus virtio0: creating channel rpmsg_ipc_simple_comm1
[    0.211427] virtio_rpmsg_bus virtio0: creating channel rpmsg_ipc_raw_command2
[    0.211607] virtio_rpmsg_bus virtio0: creating channel rpmsg_pmic addr 0xff  
[    0.211776] virtio_rpmsg_bus virtio0: creating channel rpmsg_mip addr 0xec   
[    0.211945] virtio_rpmsg_bus virtio0: creating channel rpmsg_fw_update addr 3
[    0.212135] virtio_rpmsg_bus virtio0: creating channel rpmsg_ipc_util addr 02
[    0.212307] virtio_rpmsg_bus virtio0: creating channel rpmsg_flis addr 0xf5  
[    0.212478] virtio_rpmsg_bus virtio0: creating channel rpmsg_watchdog addr 08
[    0.212663] virtio_rpmsg_bus virtio0: creating channel rpmsg_umip addr 0x14  
[    0.212837] virtio_rpmsg_bus virtio0: creating channel rpmsg_osip addr 0x15  
[    0.213055] virtio_rpmsg_bus virtio0: creating channel rpmsg_vrtc addr 0xfa  
[    0.213235] virtio_rpmsg_bus virtio0: creating channel rpmsg_fw_logging addr7
[    0.213423] virtio_rpmsg_bus virtio0: creating channel rpmsg_kpd_led addr 0x3
[    0.213599] virtio_rpmsg_bus virtio0: creating channel rpmsg_modem_nvram add2
[    0.213776] virtio_rpmsg_bus virtio0: creating channel rpmsg_mid_pwm addr 0x2
[    0.213962] virtio_rpmsg_bus virtio0: rpmsg host is online                   
[    0.214076] intel_mid_rpmsg rpmsg5: Probed rpmsg_ipc device rpmsg_ipc_command
[    0.214098] intel_mid_rpmsg rpmsg5: Allocating rpmsg_instance                
[    0.214153] intel_mid_rpmsg rpmsg6: Probed rpmsg_ipc device rpmsg_ipc_simpled
[    0.214174] intel_mid_rpmsg rpmsg6: Allocating rpmsg_instance                
[    0.214225] intel_mid_rpmsg rpmsg7: Probed rpmsg_ipc device rpmsg_ipc_raw_cod
[    0.214245] intel_mid_rpmsg rpmsg7: Allocating rpmsg_instance                
[    0.214756] Advanced Linux Sound Architecture Driver Initialized.            
[    0.214774] Intel MID platform detected, using MID PCI ops                   
[    0.214788] PCI: Probing PCI hardware                                        
[    0.214803] PCI: root bus 00: using default resources                        
[    0.214819] PCI: Probing PCI hardware (bus 00)                               
[    0.215083] PCI host bridge to bus 0000:00                                   
[    0.215112] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]           
[    0.215136] pci_bus 0000:00: root bus resource [mem 0x00000000-0xfffffffff]  
[    0.215155] pci_bus 0000:00: No busn resource found for root bus, will use []
[    0.215216] pci 0000:00:00.0: [8086:1170] type 00 class 0x060000             
[    0.215614] pci 0000:00:01.0: [8086:1190] type 00 class 0x080501             
[    0.215685] pci 0000:00:01.0: reg 10: [mem 0xff3fc000-0xff3fc0ff]            
[    0.215901] pci 0000:00:01.0: PME# supported from D0 D3hot                   
[    0.216251] pci 0000:00:01.2: [8086:1190] type 00 class 0x080501             
[    0.216318] pci 0000:00:01.2: reg 10: [mem 0xff3fa000-0xff3fa0ff]            
[    0.216533] pci 0000:00:01.2: PME# supported from D0 D3hot                   
[    0.216865] pci 0000:00:01.3: [8086:1190] type 00 class 0x080501             
[    0.216931] pci 0000:00:01.3: reg 10: [mem 0xff3fb000-0xff3fb0ff]            
[    0.217145] pci 0000:00:01.3: PME# supported from D0 D3hot                   
[    0.217514] pci 0000:00:02.0: [8086:1182] type 00 class 0x038000             
[    0.217583] pci 0000:00:02.0: reg 10: [mem 0xc0000000-0xc1ffffff]            
[    0.217646] pci 0000:00:02.0: reg 18: [mem 0x80000000-0x8fffffff]            
[    0.217707] pci 0000:00:02.0: reg 20: [io  0x7ff8-0x7fff]                    
[    0.218125] pci 0000:00:04.0: [8086:1191] type 00 class 0x070002             
[    0.218191] pci 0000:00:04.0: reg 10: [mem 0xff010000-0xff01007f]            
[    0.218404] pci 0000:00:04.0: PME# supported from D0 D3hot                   
[    0.218751] pci 0000:00:04.1: [8086:1191] type 00 class 0x070002             
[    0.218818] pci 0000:00:04.1: reg 10: [mem 0xff010080-0xff0100ff]            
[    0.219031] pci 0000:00:04.1: PME# supported from D0 D3hot                   
[    0.219378] pci 0000:00:04.2: [8086:1191] type 00 class 0x070002             
[    0.219445] pci 0000:00:04.2: reg 10: [mem 0xff010100-0xff01017f]            
[    0.219659] pci 0000:00:04.2: PME# supported from D0 D3hot                   
[    0.219991] pci 0000:00:04.3: [8086:1191] type 00 class 0x070002             
[    0.220057] pci 0000:00:04.3: reg 10: [mem 0xff010180-0xff0101ff]            
[    0.220271] pci 0000:00:04.3: PME# supported from D0 D3hot                   
[    0.220630] pci 0000:00:05.0: [8086:1192] type 00 class 0x070002             
[    0.220697] pci 0000:00:05.0: reg 10: [mem 0xff010400-0xff0107ff]            
[    0.220911] pci 0000:00:05.0: PME# supported from D0 D3hot                   
[    0.221259] pci 0000:00:06.0: [8086:1193] type 00 class 0x088000             
[    0.221327] pci 0000:00:06.0: reg 10: [mem 0xff2a0000-0xff2a0fff]            
[    0.221541] pci 0000:00:06.0: PME# supported from D0 D3hot                   
[    0.221918] pci 0000:00:06.1: [8086:1193] type 00 class 0x088000             
[    0.221985] pci 0000:00:06.1: reg 10: [mem 0xff2a1000-0xff2a1fff]            
[    0.222199] pci 0000:00:06.1: PME# supported from D0 D3hot                   
[    0.222556] pci 0000:00:07.0: [8086:1194] type 00 class 0x088000             
[    0.222623] pci 0000:00:07.0: reg 10: [mem 0xff188000-0xff188fff]            
[    0.222837] pci 0000:00:07.0: PME# supported from D0 D3hot                   
[    0.223222] pci 0000:00:07.1: [8086:1194] type 00 class 0x088000             
[    0.223290] pci 0000:00:07.1: reg 10: [mem 0xff189000-0xff189fff]            
[    0.223504] pci 0000:00:07.1: PME# supported from D0 D3hot                   
[    0.223846] pci 0000:00:07.2: [8086:1194] type 00 class 0x088000             
[    0.223915] pci 0000:00:07.2: reg 10: [mem 0xff18a000-0xff18afff]            
[    0.224129] pci 0000:00:07.2: PME# supported from D0 D3hot                   
[    0.224489] pci 0000:00:08.0: [8086:1195] type 00 class 0x078000             
[    0.224556] pci 0000:00:08.0: reg 10: [mem 0xff18b000-0xff18bfff]            
[    0.224771] pci 0000:00:08.0: PME# supported from D0 D3hot                   
[    0.225101] pci 0000:00:08.1: [8086:1195] type 00 class 0x078000             
[    0.225168] pci 0000:00:08.1: reg 10: [mem 0xff18c000-0xff18cfff]            
[    0.225381] pci 0000:00:08.1: PME# supported from D0 D3hot                   
[    0.225723] pci 0000:00:08.2: [8086:1195] type 00 class 0x078000             
[    0.225790] pci 0000:00:08.2: reg 10: [mem 0xff18d000-0xff18dfff]            
[    0.226004] pci 0000:00:08.2: PME# supported from D0 D3hot                   
[    0.226347] pci 0000:00:08.3: [8086:1195] type 00 class 0x078000             
[    0.226415] pci 0000:00:08.3: reg 10: [mem 0xff18e000-0xff18efff]            
[    0.226629] pci 0000:00:08.3: PME# supported from D0 D3hot                   
[    0.226973] pci 0000:00:09.0: [8086:1196] type 00 class 0x078000             
[    0.227040] pci 0000:00:09.0: reg 10: [mem 0xff18f000-0xff18ffff]            
[    0.227253] pci 0000:00:09.0: PME# supported from D0 D3hot                   
[    0.227597] pci 0000:00:09.1: [8086:1196] type 00 class 0x078000             
[    0.227664] pci 0000:00:09.1: reg 10: [mem 0xff190000-0xff190fff]            
[    0.227879] pci 0000:00:09.1: PME# supported from D0 D3hot                   
[    0.228211] pci 0000:00:09.2: [8086:1196] type 00 class 0x078000             
[    0.228278] pci 0000:00:09.2: reg 10: [mem 0xff191000-0xff191fff]            
[    0.228492] pci 0000:00:09.2: PME# supported from D0 D3hot                   
[    0.228853] pci 0000:00:0a.0: [8086:1197] type 00 class 0x078000             
[    0.228920] pci 0000:00:0a.0: reg 10: [mem 0xff3f8000-0xff3f8fff]            
[    0.229135] pci 0000:00:0a.0: PME# supported from D0 D3hot                   
[    0.229480] pci 0000:00:0b.0: [8086:1198] type 00 class 0x108000             
[    0.229547] pci 0000:00:0b.0: reg 10: [mem 0xf9038000-0xf903ffff]            
[    0.229761] pci 0000:00:0b.0: PME# supported from D0 D3hot                   
[    0.230095] pci 0000:00:0c.0: [8086:1199] type 00 class 0x088000             
[    0.230162] pci 0000:00:0c.0: reg 10: [mem 0xff008000-0xff008fff]            
[    0.230204] pci 0000:00:0c.0: reg 14: [mem 0x000ddcc0-0x000ddccf]            
[    0.230399] pci 0000:00:0c.0: PME# supported from D0 D3hot                   
[    0.230745] pci 0000:00:0d.0: [8086:119a] type 00 class 0x040100             
[    0.230813] pci 0000:00:0d.0: reg 10: [mem 0x05e00000-0x05ffffff]            
[    0.230857] pci 0000:00:0d.0: reg 14: [mem 0xff340000-0xff343fff]            
[    0.230898] pci 0000:00:0d.0: reg 18: [mem 0xff344000-0xff344fff]            
[    0.230939] pci 0000:00:0d.0: reg 1c: [mem 0xff2c0000-0xff2dffff]            
[    0.230980] pci 0000:00:0d.0: reg 20: [mem 0xff300000-0xff33ffff]            
[    0.231120] pci 0000:00:0d.0: PME# supported from D0 D3hot                   
[    0.231467] pci 0000:00:0e.0: [8086:119b] type 00 class 0x088000             
[    0.231534] pci 0000:00:0e.0: reg 10: [mem 0xff298000-0xff29bfff]            
[    0.231577] pci 0000:00:0e.0: reg 14: [mem 0xff2a2000-0xff2a2fff]            
[    0.231771] pci 0000:00:0e.0: PME# supported from D0 D3hot                   
[    0.232115] pci 0000:00:11.0: [8086:119e] type 00 class 0x0c0320             
[    0.232226] pci 0000:00:11.0: reg 10: [mem 0xf9100000-0xf911ffff]            
[    0.232442] pci 0000:00:11.0: PME# supported from D0 D3hot                   
[    0.232792] pci 0000:00:12.0: [8086:119f] type 00 class 0x118000             
[    0.232859] pci 0000:00:12.0: reg 10: [mem 0xf9009000-0xf9009fff]            
[    0.232902] pci 0000:00:12.0: reg 14: [mem 0xf90a0000-0xf90affff]            
[    0.232943] pci 0000:00:12.0: reg 18: [mem 0xfa000000-0xfaffffff]            
[    0.233157] pci 0000:00:12.0: PME# supported from D0 D3hot                   
[    0.233521] pci 0000:00:13.0: [8086:11a0] type 00 class 0x0b4000             
[    0.233588] pci 0000:00:13.0: reg 10: [mem 0xff009000-0xff009fff]            
[    0.233803] pci 0000:00:13.0: PME# supported from D0 D3hot                   
[    0.234141] pci 0000:00:14.0: [8086:11a1] type 00 class 0x0b4000             
[    0.234208] pci 0000:00:14.0: reg 10: [mem 0xff00b000-0xff00bfff]            
[    0.234422] pci 0000:00:14.0: PME# supported from D0 D3hot                   
[    0.234772] pci 0000:00:15.0: [8086:11a2] type 00 class 0x088000             
[    0.234840] pci 0000:00:15.0: reg 10: [mem 0xff192000-0xff192fff]            
[    0.235055] pci 0000:00:15.0: PME# supported from D0 D3hot                   
[    0.235394] pci 0000:00:16.0: [8086:11a3] type 00 class 0x0b4000             
[    0.235460] pci 0000:00:16.0: reg 10: [mem 0xff0d9000-0xff0d90ff]            
[    0.235674] pci 0000:00:16.0: PME# supported from D0 D3hot                   
[    0.236024] pci 0000:00:16.1: [8086:11a4] type 00 class 0x0b4000             
[    0.236091] pci 0000:00:16.1: reg 10: [mem 0x04819000-0x04898fff]            
[    0.236134] pci 0000:00:16.1: reg 14: [mem 0x04919000-0x04920fff]            
[    0.236327] pci 0000:00:16.1: PME# supported from D0 D3hot                   
[    0.236701] pci 0000:00:17.0: [8086:11a5] type 00 class 0x088000             
[    0.236767] pci 0000:00:17.0: reg 10: [mem 0xff013000-0xff013fff]            
[    0.236980] pci 0000:00:17.0: PME# supported from D0 D3hot                   
[    0.237320] pci 0000:00:18.0: [8086:11a6] type 00 class 0x038000             
[    0.237572] pci 0000:00:18.0: PME# supported from D0 D3hot                   
[    0.237948] pci_bus 0000:00: busn_res: [bus 00-ff] end is updated to 00      
[    0.238113] PCI: pci_cache_line_size set to 64 bytes                         
[    0.238389] e820: reserve RAM buffer [mem 0x00098000-0x0009ffff]             
[    0.238410] e820: reserve RAM buffer [mem 0x3f500000-0x3fffffff]             
[    0.239144] Bluetooth: Core ver 2.16                                         
[    0.239226] NET: Registered protocol family 31                               
[    0.239242] Bluetooth: HCI device and connection manager initialized         
[    0.239271] Bluetooth: HCI socket layer initialized                          
[    0.239298] Bluetooth: L2CAP socket layer initialized                        
[    0.239393] Bluetooth: SCO socket layer initialized                          
[    0.240073] cfg80211: Calling CRDA to update world regulatory domain         
[    0.241331] intel_scu_flis platform device created                           
[    0.241408] hsu core clock 38 M                                              
[    0.241591] intel_pmu_driver 0000:00:14.0: PMU DRIVER Probe called           
[    0.242875] intel_pmu_driver 0000:00:14.0: after pmu initialization          
[    0.243008] Switching to clocksource refined-jiffies                         
[    0.484336] intel_scu_flis rpmsg12: Probed flis rpmsg device                 
[    0.484365] intel_scu_flis rpmsg12: Allocating rpmsg_instance                
[    0.484526] intel_scu_flis intel_scu_flis: scu flis probed                   
[    0.501485] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]                  
[    0.501513] pci_bus 0000:00: resource 5 [mem 0x00000000-0xfffffffff]         
[    0.501718] NET: Registered protocol family 2                                
[    0.503090] TCP established hash table entries: 8192 (order: 4, 65536 bytes) 
[    0.503298] TCP bind hash table entries: 8192 (order: 5, 163840 bytes)       
[    0.503592] TCP: Hash tables configured (established 8192 bind 8192)         
[    0.503690] TCP: reno registered                                             
[    0.503720] UDP hash table entries: 512 (order: 2, 24576 bytes)              
[    0.503787] UDP-Lite hash table entries: 512 (order: 2, 24576 bytes)         
[    0.504181] NET: Registered protocol family 1                                
[    0.504690] RPC: Registered named UNIX socket transport module.              
[    0.504710] RPC: Registered udp transport module.                            
[    0.504724] RPC: Registered tcp transport module.                            
[    0.504736] RPC: Registered tcp NFSv4.1 backchannel transport module.        
[    0.507196] PCI: CLS 0 bytes, default 64                                     
[    0.507285] intel_scu_pmic rpmsg8: Probed pmic rpmsg device                  
[    0.507306] intel_scu_pmic rpmsg8: Allocating rpmsg_instance                 
[    0.507948] intel_scu_watchdog_evo rpmsg13: Probed watchdog rpmsg device     
[    0.507972] intel_scu_watchdog_evo rpmsg13: Allocating rpmsg_instance        
[    0.508635] intel_scu_ipcutil rpmsg11: Probed ipcutil rpmsg device           
[    0.508659] intel_scu_ipcutil rpmsg11: Allocating rpmsg_instance             
[    0.508801] (oshob) base addr = 0xfffff000                                   
[    0.508817] (oshob) identified platform = INTEL_MID_CPU_CHIP_TANGIER         
[    0.508834] (oshob) oshob version = 1.4                                      
[    0.508884] (latest extend oshob) osnib ptr = 0xfffff800                     
[    0.508899] Using latest extended oshob structure size = 1024 bytes          
[    0.508912] OSNIB Intel size = 32 bytes OEMNIB size = 96 bytes               
[    0.508926] (extend oshob) SCU buffer size is 16 bytes                       
[    0.508991] [BOOT] RESETSRC0=0x00 RESETSRC1=0x00 (PMIT interrupt tree)       
[    0.509064] [BOOT] SCU_TR[0]=0x00020011                                      
[    0.509079] [BOOT] SCU_TR[1]=0x00000220                                      
[    0.509092] [BOOT] SCU_TR[2]=0x00000000                                      
[    0.509104] [BOOT] SCU_TR[3]=0x00000000                                      
[    0.509116] [BOOT] IA_TR=0x00000000 (oshob)                                  
[    0.509448] [BOOT] RR=[fastboot] WD=0x00 ALARM=0x00 (osnib)                  
[    0.509463] [BOOT] WAKESRC=[real reset] (osnib)                              
[    0.509478] [BOOT] RESETSRC0=0x00 RESETSRC1=0x02 (osnib)                     
[    0.509543] OEMNIB interface registered to debugfs                           
[    0.509932] iio_basincove_gpadc rpmsg0: Probed bcove_gpadc rpmsg device      
[    0.510620] bcove_adc bcove_adc: bcove adc probed                            
[    0.511666] platform rtc_cmos: registered platform RTC device (no PNP device)
[    0.513696] cryptomgr_test (32) used greatest stack depth: 7532 bytes left   
[    0.514079] cryptomgr_test (34) used greatest stack depth: 7368 bytes left   
[    0.516146] vprog1: 1500 <--> 2800 mV at 2800 mV normal                      
[    0.516880] vprog2: 1500 <--> 2850 mV at 2850 mV normal                      
[    0.517574] vprog3: 1050 <--> 2800 mV at 1050 mV normal                      
[    0.518873] audit: initializing netlink socket (disabled)                    
[    0.518939] type=2000 audit(946684808.440:1): initialized                    
[    0.667289] bounce pool size: 64 pages                                       
[    0.684289] NFS: Registering the id_resolver key type                        
[    0.684356] Key type id_resolver registered                                  
[    0.684374] Key type id_legacy registered                                    
[    0.684405] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).         
[    0.684890] fuse init (API version 7.22)                                     
[    0.685665] msgmni has been set to 1668                                      
[    0.686178] SELinux:  Registering netfilter hooks                            
[    0.689037] Key type asymmetric registered                                   
[    0.689059] Asymmetric key parser 'x509' registered                          
[    0.689172] Block layer SCSI generic (bsg) driver version 0.4 loaded (major )
[    0.689396] io scheduler noop registered                                     
[    0.689660] io scheduler cfq registered (default)                            
[    0.689676] list_sort_test: start testing list_sort()                        
[    0.692804] intel_idle: MWAIT substates: 0x33000020                          
[    0.692824] intel_idle: v0.4 model 0x4A                                      
[    0.692839] intel_idle: lapic_timer_reliable_states 0xffffffff               
[    0.693119] intel_mid_dma 0000:00:0e.0: setting latency timer to 64          
[    0.693739] intel_mid_dma 0000:00:15.0: setting latency timer to 64          
[    0.695441] HSU DMA 0000:00:05.0: FUNC: 0 driver: 5 addr:ff010400 len:400    
[    0.695709] HSU serial 0000:00:04.0: FUNC: 0 driver: 0 addr:ff010000 len:80  
[    0.695766] HSU serial 0000:00:04.1: FUNC: 1 driver: 0 addr:ff010080 len:80  
[    0.695847] Found a Intel HSU                                                
[    0.696669] 0000:00:04.1: ttyMFD0 at MMIO 0xff010080 (irq = 28) is a hsu_bt_p
[    0.697211] HSU serial 0000:00:04.2: FUNC: 2 driver: 0 addr:ff010100 len:80  
[    0.697298] Found a Intel HSU                                                
[    0.698098] 0000:00:04.2: ttyMFD1 at MMIO 0xff010100 (irq = 29) is a hsu_uarp
[    0.698626] HSU serial 0000:00:04.3: FUNC: 3 driver: 0 addr:ff010180 len:80  
[    0.698712] Found a Intel HSU                                                
[    0.699381] 0000:00:04.3: ttyMFD2 at MMIO 0xff010180 (irq = 54) is a hsu_uarp
[    0.704499] console [ttyMFD2] enabled                                        
[    0.705628] Non-volatile memory driver v1.3                                  
[    0.706300] Linux agpgart interface v0.103                                   
[    0.706799] [drm] Initialized drm 1.1.0 20060810                             
[    0.720555] brd: module loaded                                               
[    0.727864] loop: module loaded                                              
[    0.729064] emmc_ipanic: init success                                        
[    0.729762] tun: Universal TUN/TAP device driver, 1.6                        
[    0.729780] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>           
[    0.730193] usbcore: registered new interface driver asix                    
[    0.730274] usbcore: registered new interface driver cdc_subset              
[    0.730406] usbcore: registered new interface driver cdc_ncm                 
[    0.730667] dwc3_otg 0000:00:11.0: setting latency timer to 64               
[    0.732841] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver       
[    0.733186] usbcore: registered new interface driver cdc_acm                 
[    0.733203] cdc_acm: USB Abstract Control Model driver for USB modems and ISs
[    0.733305] usbcore: registered new interface driver usb-storage             
[    0.733483] usbcore: registered new interface driver usbserial               
[    0.733554] usbcore: registered new interface driver pl2303                  
[    0.733623] usbserial: USB Serial support registered for pl2303              
[    0.734536] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0         
[    0.734690] rtc_cmos rtc_cmos: alarms up to one day, 114 bytes nvram         
[    0.734753] i2c /dev entries driver                                          
[    0.874861] coretemp: Enabled Aux0/Aux1 interrupts for coretemp              
[    0.874968] coretemp: Enabled Aux0/Aux1 interrupts for coretemp              
[    0.974426] MCU detected and ready to used!                                  
[    0.974548] bcove_thrm rpmsg1: Probed mrfl_thermal rpmsg device              
[    0.978737] thermal thermal_zone0: failed to read out thermal zone 0         
[    0.979307] thermal thermal_zone1: failed to read out thermal zone 1         
[    0.979896] thermal thermal_zone2: failed to read out thermal zone 2         
[    0.982658] Bluetooth: HCI UART driver ver 2.2                               
[    0.982680] Bluetooth: HCI H4 protocol initialized                           
[    0.983145] cpuidle: using governor ladder                                   
[    0.983750] cpuidle: using governor menu                                     
[    0.983819] sdhci: Secure Digital Host Controller Interface driver           
[    0.983833] sdhci: Copyright(c) Pierre Ossman                                
[    0.983909] sdhci-pci 0000:00:01.0: SDHCI controller found [8086:1190] (rev )
[    0.983993] flis_addr mapped addr: f8096900                                  
[    0.984114] sdhci-pci 0000:00:01.0: rte_addr mapped addr: f809a000           
[    0.984176] sdhci-pci 0000:00:01.0: setting latency timer to 64              
[    0.984205] mmc0: no vqmmc regulator found                                   
[    1.076952] mmc0: BKOPS_EN bit is not set                                    
[    1.385771] mmc0: new HS200 MMC card at address 0001                         
[    1.386619] mmcblk0: mmc0:0001 H4G1d 3.64 GiB                               
[    1.387065] mmcblk0boot0: mmc0:0001 H4G1d partition 1 4.00 MiB              
[    1.387459] mmcblk0boot1: mmc0:0001 H4G1d partition 2 4.00 MiB              
[    1.387862] mmcblk0rpmb: mmc0:0001 H4G1d partition 3 4.00 MiB               
[    1.393538]  mmcblk0: p1 p2 p3 p4 p5 p6 p7 p8 p9 p10                         
[    1.401550]  mmcblk0boot1: unknown partition table                           
[    1.405108]  mmcblk0boot0: unknown partition table                           
[    1.405514] mmc0: SDHCI controller on PCI [0000:00:01.0] using ADMA          
[    1.425026] emmc_ipanic: panic partition found, label:panic, device:mmcblk0p6
[    1.515147] Switching to clocksource tsc                                     
[    1.556071] emmc_ipanic: emmc_panic_notify_add: Data available in panic partn
[    1.556120] emmc_ipanic: emmc_panic_notify_add: proc entry created: emmc_ipar
[    1.556228] emmc_ipanic: emmc_panic_notify_add: log file 0(1024, 40493)      
[    1.556262] emmc_ipanic: emmc_panic_notify_add: proc entry created: emmc_ipae
[    1.556280] emmc_ipanic: emmc_panic_notify_add: log file 1(4286578688, 0)    
[    1.556294] emmc_ipanic: emmc_panic_notify_add: empty log file 1             
[    1.556309] emmc_ipanic: emmc_panic_notify_add: log file 2(4286578688, 0)    
[    1.556323] emmc_ipanic: emmc_panic_notify_add: empty log file 2             
[    1.556416] sdhci-pci 0000:00:01.2: SDHCI controller found [8086:1190] (rev )
[    1.585478] sdhci-pci 0000:00:01.2: setting latency timer to 64              
[    1.585519] mmc1: no vqmmc regulator found                                   
[    1.585921] mmc1: SDHCI controller on PCI [0000:00:01.2] using ADMA          
[    1.586104] sdhci-pci 0000:00:01.3: SDHCI controller found [8086:1190] (rev )
[    1.586225] vwlan gpio 96                                                    
[    1.586596] vwlan: 1800 mV                                                   
[    1.586852] sdhci-pci 0000:00:01.3: setting latency timer to 64              
[    1.586882] mmc2: no vqmmc regulator found                                   
[    1.587328] mmc2: SDHCI controller on PCI [0000:00:01.3] using ADMA          
[    1.596235] hidraw: raw HID events driver (C) Jiri Kosina                    
[    1.597073] usbcore: registered new interface driver usbhid                  
[    1.597092] usbhid: USB HID core driver                                      
[    1.597174] intel_scu_fw_update rpmsg10: Probed fw_update rpmsg device       
[    1.597195] intel_scu_fw_update rpmsg10: Allocating rpmsg_instance           
[    1.602534] usbcore: registered new interface driver snd-usb-audio           
[    1.603619] snd_soc_sst_platform: Enter:sst_soc_probe                        
[    1.899010] snd-soc-dummy snd-soc-dummy: ASoC: Failed to create platform deby
[    1.899235] merr_dpcm_dummy merr_dpcm_dummy.0:  snd-soc-dummy-dai <-> Headsek
[    1.899372] merr_dpcm_dummy merr_dpcm_dummy.0:  snd-soc-dummy-dai <-> ssp2-ck
[    1.899498] merr_dpcm_dummy merr_dpcm_dummy.0:  snd-soc-dummy-dai <-> snd-sok
[    1.901386] snd_merr_dpcm_probe successful                                   
[    1.901471] snd_intel_sst: INFO: ******** SST DRIVER loading.. Ver: 3.0.8    
[    1.902016] snd_intel_sst: Got drv data max stream 25                        
[    1.905999] snd_intel_sst: intel_sst_probe successfully done!                
[    1.906237] oprofile: using NMI interrupt.                                   
[    1.906381] Netfilter messages via NETLINK v0.30.                            
[    1.906473] nf_conntrack version 0.5.0 (15351 buckets, 61404 max)            
[    1.907337] NF_TPROXY: Transparent proxy support initialized, version 4.1.0  
[    1.907356] NF_TPROXY: Copyright (c) 2006-2007 BalaBit IT Ltd.               
[    1.907944] ip_tables: (C) 2000-2006 Netfilter Core Team                     
[    1.908250] TCP: cubic registered                                            
[    1.908266] Initializing XFRM netlink socket                                 
[    1.909395] NET: Registered protocol family 10                               
[    1.910728] ip6_tables: (C) 2000-2006 Netfilter Core Team                    
[    1.911052] sit: IPv6 over IPv4 tunneling driver                             
[    1.911981] NET: Registered protocol family 17                               
[    1.912051] NET: Registered protocol family 15                               
[    1.912197] Bridge firewalling registered                                    
[    1.912470] Bluetooth: RFCOMM TTY layer initialized                          
[    1.912530] Bluetooth: RFCOMM socket layer initialized                       
[    1.912547] Bluetooth: RFCOMM ver 1.11                                       
[    1.912563] Bluetooth: BNEP (Ethernet Emulation) ver 1.3                     
[    1.912576] Bluetooth: BNEP filters: protocol multicast                      
[    1.912606] Bluetooth: BNEP socket layer initialized                         
[    1.912620] Bluetooth: HIDP (Human Interface Emulation) ver 1.2              
[    1.912647] Bluetooth: HIDP socket layer initialized                         
[    1.912799] l2tp_core: L2TP core driver, V2.0                                
[    1.912861] Key type dns_resolver registered                                 
[    1.914375] Using IPI No-Shortcut mode                                       
[    1.914419] info[ 0]: name = power_btn, gpio = -1                            
[    1.914436] info[ 1]: name = SW1UI4, gpio = 61                               
[    1.915620] registered taskstats version 1                                   
[    1.917348] snd_intel_sst: runtime_idle called                               
[    1.917370] snd_intel_sst: runtime_suspend called                            
[    2.062043] regulator-dummy: incomplete constraints, leaving on              
[    2.062480] intel_mid_ssp_spi_unified 0000:00:07.0: found PCI SSP controller)
[    2.063430] intel_mid_ssp_spi_unified 0000:00:07.0: register with SPI framew)
[    2.063608] intel_mid_ssp_spi_unified 0000:00:07.0: master is unqueued, thisd
[    2.063639] intel_mid_ssp_spi_unified 0000:00:07.0: Unbalanced pm_runtime_en!
[    2.065368] intel_mid_ssp_spi_unified 0000:00:07.1: found PCI SSP controller)
[    2.066305] intel_mid_ssp_spi_unified 0000:00:07.1: register with SPI framew)
[    2.066470] intel_mid_ssp_spi_unified 0000:00:07.1: master is unqueued, thisd
[    2.069231] intel_mid_ssp_spi_unified 0000:00:07.1: Unbalanced pm_runtime_en!
[    2.075879] intel_mid_ssp_spi_unified 0000:00:07.2: found PCI SSP controller)
[    2.076881] intel_mid_ssp_spi_unified 0000:00:07.2: register with SPI framew)
[    2.077059] intel_mid_ssp_spi_unified 0000:00:07.2: master is unqueued, thisd
[    2.077089] intel_mid_ssp_spi_unified 0000:00:07.2: Unbalanced pm_runtime_en!
[    2.085579] console [netcon0] enabled                                        
[    2.085599] netconsole: network logging started                              
[    2.086234] input: gpio-keys as /devices/platform/gpio-keys/input/input0     
[    2.086853] rtc_cmos rtc_cmos: setting system clock to 2000-01-01 00:00:10 U)
[    2.086931] pmic_ccsm rpmsg3: Probed pmic_ccsm rpmsg device                  
[    2.087133] pmic_ccsm pmic_ccsm: PMIC-ID: c9                                 
[    2.087155] pmic_ccsm pmic_ccsm: Error reading battery profile from battid fk
[    2.096126] pmic_ccsm pmic_ccsm: Battery Over heat exception                 
[    2.096208] pmic_ccsm pmic_ccsm: Battery0 temperature inside boundary        
[    2.096275] pmic_ccsm pmic_ccsm: USB VBUS Detected. Notifying OTG driver     
[    2.096442] pmic_ccsm pmic_ccsm: Battery Zone changed. Current zone is 5     
[    2.111022] APIC ID: 0                                                       
[    2.111040] APIC ID: 2                                                       
[    2.111104] Num p-states 2                                                   
[    2.111122] State [0]: core_frequency[500] transition_latency[100] control[0]
[    2.111138] State [1]: core_frequency[500] transition_latency[100] control[0]
[    2.111344] Num p-states 2                                                   
[    2.111364] State [0]: core_frequency[500] transition_latency[100] control[0]
[    2.111379] State [1]: core_frequency[500] transition_latency[100] control[0]
[    2.111880] msic_power_btn rpmsg2: Probed mid_pb rpmsg device                
[    2.112007] msic_power_btn mid_powerbtn: Probed mid powerbutton devivce      
[    2.112437] input: mid_powerbtn as /devices/platform/mid_powerbtn/input/inpu1
[    2.114079] ALSA device list:                                                
[    2.114099]   #0: Loopback 1                                                 
[    2.114113]   #1: dummy-audio                                                
[    2.130409] mmc2: queuing unknown CIS tuple 0x91 (3 bytes)                   
[    2.130449] mmc2: new ultra high speed DDR50 SDIO card at address 0001       
[    2.175236] EXT4-fs (mmcblk0p8): INFO: recovery required on readonly filesysm
[    2.175262] EXT4-fs (mmcblk0p8): write access will be enabled during recovery
[    2.202748] EXT4-fs (mmcblk0p8): recovery complete                           
[    2.204675] EXT4-fs (mmcblk0p8): mounted filesystem with ordered data mode. )
[    2.204770] VFS: Mounted root (ext4 filesystem) readonly on device 179:8.    
[    2.207393] devtmpfs: mounted                                                
[    2.207758] Freeing unused kernel memory: 560k freed                         
[    2.208484] Write protecting the kernel text: 7108k                          
[    2.209110] Write protecting the kernel read-only data: 2956k                
[    2.209124] NX-protecting the kernel data: 5180k                             
[    2.432593] systemd[1]: systemd 213 running in system mode. (+PAM -AUDIT -SE)
[    2.434069] systemd[1]: Detected architecture 'x86'.                         
[    2.547614] systemd[1]: Set hostname to <edison>.                            
[    2.555008] systemd[1]: Hardware watchdog 'Intel_SCU IOH Watchdog', version 0
[    2.555094] systemd[1]: Set hardware watchdog to 1min 30s.                   
[    2.574478] systemd-getty-g (97) used greatest stack depth: 6372 bytes left  
[    2.583649] systemd-fstab-generator[102]: Checking was requested for "rootfs.
[    2.587348] systemd-efi-boo (100) used greatest stack depth: 6300 bytes left 
[    2.771628] systemd[1]: [/lib/systemd/system/wyliodrin-server.service:3] Fait
[    2.774813] systemd[1]: [/lib/systemd/system/wyliodrin-hypervisor.service:3]t
[    2.778573] systemd[1]: Configuration file /lib/systemd/system/connman-init..
[    2.788255] systemd[1]: [/lib/systemd/system/redis.service:7] Unknown lvalue'
[    2.832092] systemd[1]: Expecting device dev-ttyMFD2.device...               
[    2.895498] systemd[1]: Starting Forward Password Requests to Wall Directory.
[    2.896132] systemd[1]: Started Forward Password Requests to Wall Directory .
[    2.896262] systemd[1]: Starting Remote File Systems.                        
[    2.945393] systemd[1]: Reached target Remote File Systems.                  
[    2.945521] systemd[1]: Expecting device dev-disk-by\x2dpartlabel-factory.de.
[    2.995412] systemd[1]: Expecting device sys-subsystem-net-devices-usb0.devi.
[    3.045449] systemd[1]: Starting Dispatch Password Requests to Console Direc.
[    3.045884] systemd[1]: Started Dispatch Password Requests to Console Direct.
[    3.045999] systemd[1]: Starting Paths.                                      
[    3.095377] systemd[1]: Reached target Paths.                                
[    3.095495] systemd[1]: Starting Swap.                                       
[    3.145363] systemd[1]: Reached target Swap.                                 
[    3.145483] systemd[1]: Starting boot.automount.                             
[    3.207546] systemd[1]: boot.automount: Directory /boot to mount over is not.
[    3.255469] systemd[1]: Set up automount boot.automount.                     
[    3.255629] systemd[1]: Starting Root Slice.                                 
[    3.375338] systemd[1]: Created slice Root Slice.                            
[    3.375469] systemd[1]: Starting User and Session Slice.                     
[    3.425366] systemd[1]: Created slice User and Session Slice.                
[    3.425492] systemd[1]: Starting Delayed Shutdown Socket.                    
[    3.475322] systemd[1]: Listening on Delayed Shutdown Socket.                
[    3.475443] systemd[1]: Starting /dev/initctl Compatibility Named Pipe.      
[    3.525315] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.  
[    3.525471] systemd[1]: Starting udev Control Socket.                        
[    3.575309] systemd[1]: Listening on udev Control Socket.                    
[    3.575452] systemd[1]: Starting udev Kernel Socket.                         
[    3.625313] systemd[1]: Listening on udev Kernel Socket.                     
[    3.625467] systemd[1]: Starting Journal Socket.                             
[    3.675294] systemd[1]: Listening on Journal Socket.                         
[    3.675489] systemd[1]: Starting System Slice.                               
[    3.725311] systemd[1]: Created slice System Slice.                          
[    3.725451] systemd[1]: Mounting Temporary Directory...                      
[    3.840607] systemd[1]: Starting system-serial\x2dgetty.slice.               
[    3.905398] systemd[1]: Created slice system-serial\x2dgetty.slice.          
[    3.905551] systemd[1]: Starting system-getty.slice.                         
[    3.955314] systemd[1]: Created slice system-getty.slice.                    
[    4.018359] systemd[1]: Starting Create list of required static device nodes.
[    4.069391] systemd[1]: Starting udev Coldplug all Devices...                
[    4.134053] systemd[1]: Starting Load Kernel Modules...                      
[    4.180131] systemd[1]: Mounting Debug File System...                        
[    4.229218] systemd[1]: Mounted Huge Pages File System.                      
[    4.229467] systemd[1]: Mounting POSIX Message Queue File System...          
[    4.274374] systemd[1]: Starting Apply Kernel Variables...                   
[    4.289982] dhd_module_init in                                               
[    4.290014] found wifi platform device wlan                                  
[    4.290121] Power-up adapter 'DHD generic adapter'                           
[    4.298696] systemd[1]: Starting Journal Service...                          
[    4.403314] systemd[1]: Started Journal Service.                             
[    4.555268] EXT4-fs (mmcblk0p8): re-mounted. Opts: discard,barrier=1,data=orc
[    4.715961] wifi_platform_set_power = 1                                      
[    4.924894] wifi_platform_bus_enumerate device present 1                     
[    4.950710] bcmsdh_sdmmc: bcmsdh_sdmmc_probe Enter                           
[    4.950934] bcmsdh_sdmmc: bcmsdh_sdmmc_probe Enter                           
[    4.950955] bus num (host idx)=2, slot num (rca)=1                           
[    4.950970] found adapter info 'DHD generic adapter'                         
[    4.961330] F1 signature OK, socitype:0x1 chip:0xa94c rev:0x2 pkg:0x0        
[    4.962881] DHD: dongle ram size is set to 524288(orig 524288) at 0x0        
[    4.964657] wifi_platform_get_mac_addr                                       
[    4.964739] wifi_get_mac_addr_intel: unable to open /config/wifi/mac.txt     
[    4.965948] wl_create_event_handler(): thread:wl_event_handler:7e started    
[    4.974874] CFG80211-ERROR) wl_event_handler : tsk Enter, tsk = 0xf5001540   
[    4.975006] dhd_attach(): thread:dhd_watchdog_thread:7f started              
[    4.984966] dhd_attach(): thread:dhd_dpc:80 started                          
[    4.985000] dhd_deferred_work_init: work queue initialized                   
[    4.985615] Dongle Host Driver, version 1.141.59 (r)                         
Compiled in /export/users/neck/iotdk_3.5_dev/workdir/build_edison/tmp/work/edis7
[    4.986705] Register interface [wlan0]  MAC: 00:00:00:00:00:00               
                                                                                
[    4.986734] dhd_prot_ioctl : bus is down. we have nothing to do              
[    4.987346] bcmsdh_sdmmc: bcmsdh_sdmmc_probe Enter                           
[    4.987472] wifi_platform_set_power = 0                                      
[    4.988557] wifi_platform_bus_enumerate device present 0                     
[    5.064149] g_multi gadget: using random host ethernet address               
[    5.065334] usb0: MAC 02:00:86:58:c2:af                                      
[    5.065357] usb0: HOST MAC d2:aa:a7:ff:43:58                                 
[    5.084993] g_multi gadget: Mass Storage Function, version: 2009/09/11       
[    5.085020] g_multi gadget: Number of LUNs=1                                 
[    5.085048]  lun0: LUN: file: /dev/mmcblk0p9                                 
[    5.085247] g_multi gadget: Multifunction Composite Gadget                   
[    5.085266] g_multi gadget: g_multi ready                                    
[    5.097795] systemd-modules (109) used greatest stack depth: 5444 bytes left 
[    5.855125] systemd-udevd[143]: starting version 213                         
[    6.227320] systemd-journald[117]: Received request to flush runtime journal1
[    6.361626] g_multi gadget: high-speed config #2: Multifunction with CDC ECM 
[    7.142147] EXT4-fs (mmcblk0p5): mounted filesystem without journal. Opts: dc
[   10.851914] EXT4-fs (mmcblk0p10): mounted filesystem with ordered data mode.c
[   12.004007] snd_intel_sst: runtime_resume called                             
[   12.034532] snd_intel_sst: FW Version 01.09.00.02                            
[   12.034558] snd_intel_sst: Build date Jan 14 2014 Time 20:08:46              
[   12.034669] snd_intel_sst: Alloc for str 14 pipe 0xe                         
[   12.263921] snd_intel_sst: Free for str 14 pipe 0xe                          
[   12.265521] snd_intel_sst: runtime_idle called                               
[   12.354303] snd_intel_sst: Alloc for str 14 pipe 0xe                         
[   12.473929] snd_intel_sst: Free for str 14 pipe 0xe                          
[   12.475351] snd_intel_sst: runtime_idle called                               
[   12.502515] snd_intel_sst: Alloc for str 1 pipe 0x90                         
[   12.697170] snd_intel_sst: Alloc for str 14 pipe 0xe                         
[   12.702996] snd_intel_sst: Free for str 14 pipe 0xe                          
[   12.724261] snd_intel_sst: Alloc for str 14 pipe 0xe                         
[   12.728953] snd_intel_sst: Free for str 14 pipe 0xe                          
[   12.731250] snd_intel_sst: Free for str 1 pipe 0x90                          
[   12.733716] snd_intel_sst: runtime_idle called                               
[   12.794060] snd_intel_sst: Alloc for str 1 pipe 0x90                         
[   12.959715] snd_intel_sst: Start for str 1 pipe 0x90                         
[   12.975143] snd_intel_sst: Alloc for str 14 pipe 0xe                         
[   13.035501] snd_intel_sst: Start for str 14 pipe 0xe                         
[   18.668303] snd_intel_sst: Stop for str 14 pipe 0xe                          
[   18.668980] snd_intel_sst: Free for str 14 pipe 0xe                          
[   18.673752] snd_intel_sst: Stop for str 1 pipe 0x90                          
[   18.674629] snd_intel_sst: Free for str 1 pipe 0x90                          
[   18.677124] snd_intel_sst: runtime_idle called                               
[   20.673034] snd_intel_sst: runtime_suspend called                            
root@edison:~# 
```