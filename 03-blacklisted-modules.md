### Blacklist PC Speaker
To disable the annoying beep sound in the login screen or in terminal, we need to disable the builtin pc speaker in the system board.
Create the blacklist file:
```
$ sudo touch /etc/modprobe.d/nobeep.conf
```
Append the following lines:
```
blacklist pcspkr
blacklist snd_pcsp
```

### Blacklist NMI Watchdog
In laptop systems the watchdog module is unnecessary and consume more power. Though, it is disabled through the **grub**, the modules somehow gets loaded into the system.
To disable, create the blacklist file:
```
$ sudo touch /etc/modprobe.d/nmi-watchdog-blacklist.conf
```
Then, append the following lines:
```
blacklist iTCO_wdt
blacklist iTCO_vendor_support
```
