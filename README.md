<div align="center">
 
  <h1 align="center">linux-cachyos-bore for Fedora</h1>
</div>

# KERNEL

### linux-cachyos-bore uses as default the BORE scheduler
- BORE (Burst-Oriented Response Enhancer) CPU Scheduler by [firelzrd (BORE)](https://github.com/firelzrd/bore-scheduler)

### Features:
- Choose between `LLVM/LTO` or `GCC`.
- AMD PSTATE Guided Driver enabled by default and with enhancements patches/fixes.
- RCU fixes and improvements.
- Latest BTRFS improvements & fixes.
- Latest & improved ZSTD 1.5.5 patch-set.
- UserKSM daemon from pf.
- Improved BFQ Scheduler.
- zram patches from upstream.
- Clearlinux Patchset.
- Back-ported patches from `linux-next`.
- BBRv2 tcp_congestion_control.
- Scheduler patches from linux-next/tip.
- General improved sysctl settings and upstream scheduler fixes.
- OpenRGB and ACS Override support.
- HDR Patches for AMD GPU's and gamescope.
- maple-tree and MG-LRU fixes from upstream.
- Default support for Steam Deck.
- [per VMA lock](https://lore.kernel.org/lkml/20230109205336.3665937-1-surenb@google.com/T/#ma04517b963591298a9eb76d96d2c453256a4d9ab).

### Checking for the cpu support:
Check support by the following the command
```
/lib64/ld-linux-x86-64.so.2 --help | grep "(supported, searched)"

```
If it does not detect x86_64_v3 support do not install the kernel. Otherwise you will end up with a non-functioning operating system! 

### Installation instructions:

```
sudo dnf copr enable bieszczaders/kernel-cachyos
```

and next

```
sudo dnf install kernel-cachyos-bore
```

OR
```
sudo dnf install kernel-cachyos-bore-lto
```

### Install drivers for lto kernel:
If you build external modules (e.g. for Nvidia graphics card drivers) and use the -lto kernel, you need to install the following dependencies:
```
dnf install clang clang-devel llvm lld
```

# UKSMD

Check description [here](https://github.com/CachyOS/uksmd).

### Installation instructions:

```
sudo dnf copr enable bieszczaders/kernel-cachyos-addons
```

### Install required packages:

```
sudo dnf install libcap-ng libcap-ng-devel procps-ng procps-ng-devel
```

### Install UKSMD:

```
sudo dnf install uksmd
```

### Enable UKSMD:

```
sudo systemd enable uksmd && sudo systemd start uksmd
```

### Checking the correct operation of the uksmd:

```
systemctl status uksmd
```

and

```
uksmdstats
```
