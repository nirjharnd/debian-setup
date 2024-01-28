# Grub Setup
### Optimizations list:
- Disable watchdog
- Disable ipv6 stack systemwide
- Disable cpu mitigations
- Enable Intel *fastboot* and *frame buffer compression*
- Clean booting[^1] & enable plymouth[^2]

Edit */etc/default/grub*:
```
GRUB_CMDLINE_LINUX_DEFAULT="nowatchdog ipv6.disable=1 mitigations=off i915.fastboot=1 i915.enable_fbc=1 quiet splash loglevel=0"
GRUB_CMDLINE_LINUX="ipv6.disable=1"
GRUB_GFXMODE=1366x768x32
```
Run:
```
$ sudo update-grub
```

# Plymouth Setup
Install the required packages:
```
$ sudo apt install plymouth plymouth-themes
```
Set *emerald*[^3] as the selected theme:
```
$ sudo plymouth-set-default-theme -R emerald
```


[^1]: *quiet splash loglevel=0* must be at the end of the line.
[^2]: *GFXMODE* resolution must match any supported display resolution
[^3]: default theme for debian bookworm
