Power
==

> D0, Device power state, equivalent to “fully on”. D1 and D2 are intermediate states; D3 is “Off”

> S0ix, An “active idle” sleep state, which delivers the same power consumption as S3 sleep, yet provides a quick activate time into full S0 state

Links

- https://scivision.co/measured-power-consumption-of-intel-edison/
- https://communities.intel.com/thread/61067?tstart=0
- cat scaling_available_frequencies
- https://communities.intel.com/message/338257#338257
- [Intel Edison Power consumption](http://www.helios.de/heliosapp/edison/)


## Kernel Integration

```sh
    root@edison:~# rfkill block Bluetooth # BlueTooth
    
    root@edison:~# modprobe -r bcm4334x # WiFi
    root@edison:~# modprobe bcm4334x # WiFi
    
    root@edison:~# /sbin/iwconfig wlan0 power off
    root@edison:~# /sbin/iwconfig wlan0 power on 
    
    root@edison:~# cat /sys/power/state 
    freeze mem
    root@edison:~# cat /sys/power/pm_test
    [none] core processors platform devices freezer

    root@edison:~# echo 1 > /sys/devices/system/cpu/offline 

    root@edison:~# ls /sys/power/
    pm_async           pm_print_times     state              wake_unlock
    pm_freeze_timeout  pm_test            wake_lock          wakeup_count
    root@edison:~# cat /sys/devices/system/cpu/     
    cpu0/       cpuidle/    offline     power/      release     
    cpu1/       kernel_max  online      present     uevent      
    cpufreq/    modalias    possible    probe
    root@edison:~# ls /sys/devices/system/cpu/cpu0/cpufreq/                         
    affected_cpus                  scaling_cur_freq
    cpuinfo_cur_freq               scaling_driver
    cpuinfo_max_freq               scaling_governor
    cpuinfo_min_freq               scaling_max_freq
    cpuinfo_transition_latency     scaling_min_freq
    related_cpus                   scaling_setspeed
    scaling_available_frequencies  stats
    scaling_available_governors
    root@edison:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
    ondemand userspace performance
    root@edison:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
    500000
```sh

### Suspend to Ram, Yocto 3.0

```sh
root@edison:~# echo mem > /sys/power/state 
[   64.899755] intel_scu_watchdog_evo: watchdog_stop
root@edison:~# echo mem > /sys/power/state 
[   72.953877] intel_scu_watchdog_evo: watchdog_stop
```

### Suspend to Ram, Yocto 2.1

```sh
    root@edison:~# echo "mem" > /sys/power/state
    [23496.070128] pci_pm_suspend(): sdhci_pci_suspend+0x0/0xd0 returns -16
    [23496.070144] dpm_run_callback(): pci_pm_suspend+0x0/0x1d0 returns -16
    [23496.070158] PM: Device 0000:00:01.3 failed to suspend async: error -16
    [23496.091362] PM: Some devices failed to suspend
    -sh: echo: write error: Device or resource busy
    
    [23495.740274] PM: Syncing filesystems ... done.
    [23495.743025] PM: Preparing system for mem sleep
    [23495.752571] Freezing user space processes ... (elapsed 0.06 seconds) done.
    [23495.820232] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
    [23495.840185] PM: Entering mem sleep
    [23495.840463] Suspending console(s) (use no_console_suspend to debug)
    [23495.980087] snd_intel_sst: runtime_resume called
    [23496.001158] CFG80211-ERROR) wl_cfg80211_disconnect : Reason 3
    [23496.005525] CFG80211-ERROR) wl_is_linkdown : Link down Reason : WLC_E_LINK
    [23496.005543] link down if wlan0 may call cfg80211_disconnected. event : 16, reason=2 from     f8:01:13:a8:2b:40
    [23496.007379] CFG80211-ERROR) wl_is_linkdown : Link down Reason : WLC_E_DEAUTH
    [23496.007392] CFG80211-ERROR) wl_is_linkdown : Link down Reason : WLC_E_DEAUTH
    [23496.011506] snd_intel_sst: runtime_suspend called
    [23496.011626] bcove_thrm bcove_thrm: suspend called.
    [23496.011798] cfg80211: Calling CRDA for country: MX
    [23496.020168] bcmsdh_sdmmc_suspend Enter
    [23496.020174] bcmsdh_sdmmc_suspend Enter
    [23496.070092] bcmsdh_sdmmc_resume Enter
    [23496.070128] pci_pm_suspend(): sdhci_pci_suspend+0x0/0xd0 returns -16
    [23496.070144] dpm_run_callback(): pci_pm_suspend+0x0/0x1d0 returns -16
    [23496.070158] PM: Device 0000:00:01.3 failed to suspend async: error -16
    [23496.091362] PM: Some devices failed to suspend
    [23496.091661] bcove_thrm bcove_thrm: resume called.
    [23496.092335] snd_intel_sst: runtime_resume called
    [23496.200343] PM: resume of devices complete after 108.965 msecs
    [23496.202457] PM: Finishing wakeup.
    [23496.202472] Restarting tasks ... done.
    [23496.239956] snd_intel_sst: runtime_idle called
    [23496.239982] snd_intel_sst: runtime_suspend called
    [23496.249816] ------------[ cut here ]------------
    [23496.249861] WARNING: at /data/jenkins_worker/workspace/edison-weekly/linux-kernel/drivers/usb/dwc3/gadget.c:1248 __dwc)
    [23496.249875] Modules linked in: bcm4334x(O) usb_f_acm u_serial g_multilibcomposite bcm_bt_lpm [last unloaded: bcm4334x]
    [23496.249941] CPU: 0 PID: 142 Comm: systemd-udevd Tainted: GO3.10.17-poky-edison+ #1
    [23496.249956] Hardware name: Intel Corporation Merrifield/BODEGA BAY, BIOS 5422015.01.21:18.19.48
    [23496.249969]  c1b4326c 00000000 f6c0bd00 c18d9eea f6c0bd28 c12408be c1ae1657c1b4326c
    [23496.250020]  000004e0 c15fa14e c15fa14e f6c49020 f675f180 f6c0bd88 f6c0bd38c1240982
    [23496.250068]  00000009 00000000 f6c0bd94 c15fa14e f6c0bd7c 00000000 0000003635dac802
    [23496.250116] Call Trace:
    [23496.250150]  [<c18d9eea>] dump_stack+0x16/0x18
    [23496.250179]  [<c12408be>] warn_slowpath_common+0x5e/0x80
    [23496.250204]  [<c15fa14e>] ? __dwc3_gadget_kick_transfer+0x3de/0x430
    [23496.250227]  [<c15fa14e>] ? __dwc3_gadget_kick_transfer+0x3de/0x430
    [23496.250253]  [<c1240982>] warn_slowpath_null+0x22/0x30
    [23496.250277]  [<c15fa14e>] __dwc3_gadget_kick_transfer+0x3de/0x430
    [23496.250305]  [<c15fa47e>] dwc3_gadget_ep_queue+0x2de/0x3a0
    [23496.250353]  [<f8906824>] eth_start_xmit+0x1a4/0x330 [g_multi]
    [23496.250382]  [<c17411e3>] dev_hard_start_xmit+0x343/0x570
    [23496.250407]  [<c18df22f>] ? _raw_spin_unlock_bh+0x1f/0x30
    [23496.250432]  [<c176506a>] ? __nf_conntrack_confirm+0x21a/0x340
    [23496.250459]  [<c175ad1c>] sch_direct_xmit+0x7c/0x1c0
    [23496.250484]  [<c1741572>] dev_queue_xmit+0x162/0x400
    [23496.250512]  [<c177a2e0>] ip_finish_output+0x210/0x3a0
    [23496.250536]  [<c177a0d0>] ? ip_fragment+0x970/0x970
    [23496.250562]  [<c177bb17>] ip_output+0xb7/0xc0
    [23496.250586]  [<c177a0d0>] ? ip_fragment+0x970/0x970
    [23496.250611]  [<c177b230>] ip_local_out+0x20/0x30
    [23496.250637]  [<c17ac771>] igmpv3_sendpack+0x51/0x60
    [23496.250663]  [<c17ad2c3>] igmp_ifc_timer_expire+0x173/0x290
    [23496.250689]  [<c1250c02>] call_timer_fn+0x32/0x140
    [23496.250715]  [<c17ad150>] ? igmp_gq_timer_expire+0x30/0x30
    [23496.250739]  [<c1250e52>] run_timer_softirq+0x142/0x230
    [23496.250766]  [<c1270ddb>] ? get_parent_ip+0xb/0x40
    [23496.250791]  [<c17ad150>] ? igmp_gq_timer_expire+0x30/0x30
    [23496.250817]  [<c1249251>] __do_softirq+0xe1/0x260
    [23496.250843]  [<c1249170>] ? tasklet_action+0x120/0x120
    [23496.250856]  <IRQ>  [<c1249555>] ? irq_exit+0xa5/0xb0
    [23496.250899]  [<c18e535b>] ? smp_apic_timer_interrupt+0x5b/0x8b
    [23496.250928]  [<c14d9ee4>] ? trace_hardirqs_off_thunk+0xc/0x18
    [23496.250953]  [<c18dfc2a>] ? apic_timer_interrupt+0x32/0x38
    [23496.250978]  [<c18d0000>] ? init_intel_cacheinfo+0x1b3/0x37e
    [23496.250994] ---[ end trace ab9c379ac6289fd6 ]---
    [23500.707829] CFG80211-ERROR) wl_cfg80211_connect : Connectting withf8:01:13:a8:2b:40 channel (1) ssid "INFINITUMfjph", )
    [23500.707829] 
    [23500.763280] wl_bss_connect_done succeeded with f8:01:13:a8:2b:40
    [23500.769798] wl_bss_connect_done succeeded with f8:01:13:a8:2b:40
```

- https://communities.intel.com/thread/61067?tstart=0
- https://github.com/01org/edison-linux/commit/149de7abd8829bcc009641e215b53fe89fcf29b2

## Userspace Applications

### SystemCtl, Yocto 2.1

```sh
root@edison:~# systemctl suspend
[ 2283.848450] intel_scu_watchdog_evo: watchdog_stop
[ 2283.907087] pci_pm_suspend(): sdhci_pci_suspend+0x0/0xd0 returns -16
[ 2283.907105] dpm_run_callback(): pci_pm_suspend+0x0/0x1d0 returns -16
[ 2283.907120] PM: Device 0000:00:01.3 failed to suspend async: error -16
[ 2283.928403] PM: Some devices failed to suspend
[ 2284.491363] intel_scu_watchdog_evo: watchdog_stop
[ 2284.537447] pci_pm_suspend(): sdhci_pci_suspend+0x0/0xd0 returns -16
[ 2284.537464] dpm_run_callback(): pci_pm_suspend+0x0/0x1d0 returns -16
[ 2284.537479] PM: Device 0000:00:01.3 failed to suspend async: error -16
[ 2284.558639] PM: Some devices failed to suspend
A dependency job for suspend.target failed. See 'journalctl -xn' for details.
root@edison:~# 
```

```sh
root@edison:~# dmesg
...
[ 2284.038549] Restarting tasks ... done.
[ 2284.088450] snd_intel_sst: runtime_idle called
[ 2284.088478] snd_intel_sst: runtime_suspend called
[ 2284.096683] PM: Syncing filesystems ... done.
[ 2284.100314] PM: Preparing system for freeze sleep
[ 2284.106998] ------------[ cut here ]------------
[ 2284.107045] WARNING: at /iotdk/noel/newpull/devkit-build-tools/workdir/poky/$
[ 2284.107060] Modules linked in: usb_f_acm u_serial g_multi libcomposite bcm_b$
[ 2284.107123] CPU: 1 PID: 406 Comm: kworker/u4:2 Tainted: G           O 3.10.1$
[ 2284.107137] Hardware name: Intel Corporation Merrifield/BODEGA BAY, BIOS 542$
[ 2284.107160] Workqueue: kmmcd mmc_rescan
[ 2284.107176]  c1b472c8 00000000 f6f8fd00 c18dc6da f6f8fd28 c12408ae c1ae494a $
[ 2284.107226]  000004e0 c15fa18e c15fa18e f6c49020 f5c20000 f6f8fd88 f6f8fd38 $
[ 2284.107273]  00000009 00000000 f6f8fd94 c15fa18e f6f8fd7c 00000000 00000036 $
[ 2284.107321] Call Trace:
[ 2284.107353]  [<c18dc6da>] dump_stack+0x16/0x18
[ 2284.107384]  [<c12408ae>] warn_slowpath_common+0x5e/0x80
[ 2284.107409]  [<c15fa18e>] ? __dwc3_gadget_kick_transfer+0x3de/0x430
...
[ 2284.108500]  [<c1263560>] ? kthread+0xa0/0xb0
[ 2284.108523]  [<c18e5465>] ? sub_preempt_count+0x95/0xf0
[ 2284.108551]  [<c18e73f7>] ? ret_from_kernel_thread+0x1b/0x28
[ 2284.108574]  [<c12634c0>] ? kthread_create_on_node+0xc0/0xc0
[ 2284.108592] ---[ end trace 33110b433ad381ba ]---
[ 2284.299642] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 2284.317476] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) do$
[ 2284.337404] PM: Entering freeze sleep
[ 2284.337423] Suspending console(s) (use no_console_suspend to debug)
[ 2284.467318] snd_intel_sst: runtime_resume called
[ 2284.490418] snd_intel_sst: runtime_suspend called
[ 2284.491080] bcmsdh_sdmmc_suspend Enter
[ 2284.491087] bcmsdh_sdmmc_suspend Enter
[ 2284.491363] intel_scu_watchdog_evo: watchdog_stop
[ 2284.491761] bcove_thrm bcove_thrm: suspend called.
[ 2284.537411] bcmsdh_sdmmc_resume Enter
[ 2284.537447] pci_pm_suspend(): sdhci_pci_suspend+0x0/0xd0 returns -16
[ 2284.537464] dpm_run_callback(): pci_pm_suspend+0x0/0x1d0 returns -16
[ 2284.537479] PM: Device 0000:00:01.3 failed to suspend async: error -16
[ 2284.558639] PM: Some devices failed to suspend
[ 2284.558944] bcove_thrm bcove_thrm: resume called.
[ 2284.559690] snd_intel_sst: runtime_resume called
[ 2284.670305] PM: resume of devices complete after 111.609 msecs
[ 2284.672284] PM: Finishing wakeup.
[ 2284.702653] snd_intel_sst: runtime_idle called
[ 2284.702678] snd_intel_sst: runtime_suspend called
[ 2284.672297] Restarting tasks ... done.
[ 2288.575692] CFG80211-ERROR) wl_cfg80211_connect : Connectting withf8:01:13:a$

```

```sh
    root@edison:~# systemctl poweroff
    root@edison:~# cat /sys/module/pcie_aspm/parameters/policy
    default [performance] powersave 
    root@edison:~# cpufreq-info
    root@edison:~# head /sys/class/regulator/*/name
```

## Setup
### Opkg
### Apt-Get
## Device Configuration
## Usage Models
## Links

- [ACPI Wikipedia](https://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)
- http://www.helios.de/heliosapp/edison/index.html
- https://www.kernel.org/doc/Documentation/cpu-freq/governors.txt
- https://www.kernel.org/doc/Documentation/power/states.txt
- https://www.kernel.org/doc/Documentation/power/basic-pm-debugging.txt
- https://communities.intel.com/thread/61067
- performance states (P-states) or power saving states (C-states)
- Dongle Host Driver, version 1.141.59 (r)

## Suspend Issue

In the latest Yocto release (2.1 from 09/28/15), there is a problem when trying to put asleep the edison board. The commands to put the edison board in S3 state are:

```sh
    root@debian8:~# systemctl stop wpa_supplicant
    root@debian8:~# echo -n "mem" > /sys/power/state
```

But this only works the first time after a reboot. The patch involves modifying two lines of code from intel_soc_pmu.c file from the linux kernel: 

https://github.com/01org/edison-linux/commit/149de7abd8829bcc009641e215b53fe89fcf29b2


Assuming you have a working yocto build environment (Check Edison BSP instructions for this), the file is on the following path:

```sh
    iotlab@debian8:~/edison-src$ vim ./out/linux64/build/tmp/work/edison-poky-linux/linux- yocto/3.10.17-r0/linux/arch/x86/platform/intel-mid/intel_soc_pmu.c
```

Then we need to recompile and rebuild the image:

```sh
    iotlab@debian8:~/edison-src/out/linux64$ source poky/oe-init-build-env iotlab@debian8:~/edison-src/out/linux64/build$ bitbake linux-yocto -f -c compile iotlab@debian8:~/edison-src/out/linux64/build$ bitbake edison-image iotlab@debian8:~/edison-src/out/linux64/build$ cd ~/edison-src/meta-intel-edison/utils/flash iotlab@debian8:~/edison-src/meta-intel-edison/utils/flash$ ./postBuild.sh
```
