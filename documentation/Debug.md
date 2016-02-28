Debug
==

## Debug Filesystem

> Debugfs exists as a simple way for kernel developers to make information available to user space.  Unlike /proc, which is only meant for information about a process, or sysfs, which has strict one-value-per-file rules, debugfs has no rules at all.

- [Linux Kernel Documentation Debugfs](https://www.kernel.org/doc/Documentation/filesystems/debugfs.txt)
- [Wikipedia Debugfs](https://en.wikipedia.org/wiki/Debugfs)

## Kernel Configuration

```sh
    Kernel hacking

        -*- Kernel debugging
        [*]   Magic SysRq key
        -*-   Debug filesystem
        [*]   Detect Soft Lockups
        [ ]   Collect scheduler statistics
        [*]   Debug slab memory allocations
        [*]     Memory leak debugging
        [*]   Mutex debugging, deadlock detection
        [*]   Spinlock debugging
        [*]   Sleep-inside-spinlock checking
        [ ]   kobject debugging
        [ ]   Highmem debugging
        [ ]   Compile the kernel with debug info
```

## Kernel Integration

```sh
    root@edison:~# mount -t debugfs none /sys/kernel/debug
    root@edison:~# ls /sys/kernel/debug/
    asoc                  gpio_debug            pmu_sync_d0ix
    bdi                   hid                   pwm
    bluetooth             hsu                   regmap
    boot_params           ieee80211             regulator
    c_states_stat         ignore_add            remoteproc
    cstate_ignore_add     ignore_remove         s3_ctrl
    cstate_ignore_remove  iio                   sched_features
    debug_feature         intel_scu_oshob       soc_thermal
    disable_emmc_ipanic   kprobes               sst
    dma_buf               mce                   suspend_stats
    dri                   mid_pmu_states        tracing
    dump_cmd              mmc0                  usb
    dump_output           mmc1                  wakeup_sources
    dwc3-device.1         mmc2                  watchdog
    dynamic_debug         pmic_ccsm             x86
    emmc_ipanic           pmu_force_d0i0
    gpio                  pmu_force_d0i3
```

## Ftrace

Tbd

# Links

- [Linux Kernel Debugfs](https://www.kernel.org/doc/Documentation/filesystems/debugfs.txt)
- [Linux Magic System Request Key Hacks](https://www.kernel.org/doc/Documentation/sysrq.txt)