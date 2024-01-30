Now we are ready to install the additional utilities for our system.

### Install Power Management support
These packages are needed for proper suspend & resume support.
```
$ sudo apt install acpi-support acpid powermgmt-base upower
```
### Install Disk & USB support
These packages are needed for various disk and USB related operations and compatibility.
```
$ sudo apt install udisks2 usb-modeswitch usb.ids usbutils
```
### Install some useful system daemons
These daemons are responsible for various useful systemwide operations. They are quite self-explanatory.
```
$ sudo apt install eatmydata havaged irqbalance rtkit systemd-oomd thermald uuid-runtime
```
### Install sensors
These packages provide sensors to various disk related data and system temperature.
```
$ sudo apt install hdparm lm-sensors smartmontools
```
### Install system & hardware information tools
These packages will provide information of our hardware and their loads.
```
$sudo apt install htop inxi neofetch powertop intel-gpu-tools pulseaudio-utils
```
### Install Firewall
I prefer *ufw* as firewall. It's pretty secure, easy to use and has a gui which we will install later.
```
$ sudo apt install ufw
```
### Install archiving/unarchiving support
*p7zip* provides complete support of the most popular compression formats.
```
$ sudo apt install p7zip-full p7zip-rar
```
### Install NTFS support
*ntfs* file system support is needed to access Windows partitions.
```
$ sudo apt install ntfs-3g
```
### Install system cleaning tools
There are two tools in debian which can be used to remove orphaned packages and unneeded locales.
```
$ sudo apt install deborphan localepurge
```
Finally, reboot the system to proceed with the installation of the desktop environment.
```
$ sudo reboot
```
