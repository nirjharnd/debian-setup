## Installation
1. Use the *netinstall* image.
2. Deselect everything during the package selection step except **Standard System Utilities**.
3. After rebooting we will be presented with a command prompt and nothing else.

## Post-Installation
Now we will have only the command prompt. We will install selected additional packages to get a lean Debian system without any bloats.
### Configure APT to not install extra packages
Create the config file:
```
$ sudo touch /etc/apt/apt.conf.d/99cleaninstall
```
Then put the following contents:
```
APT::Install-Recommends "false";
APT::Install-Suggests "false";
```
### Configure LAN/Wireless
Install the *network-manager* package:
```
$ sudo apt install network-manager
```
Configure the network:
```
$ nmtui
```
### Install Xorg
We will not use any 2D video drivers from the *xserver-xorg-video* packages. So, we will explicitly install only the *fbdev* driver to prevent others to get installed. Same goes with our input driver. We will only use more modern *libinput*. So, install the **Xorg** display server:
```
$ sudo apt install xorg xserver-xorg xserver-xorg-input-libinput xserver-xorg-video-fbdev
```
### Install Video driver & hardware acceleration plugins
Since we will be using Intel graphics with only *vaapi* decoding, we do not need the non-free package[^1].
```
$ sudo apt install intel-media-va-driver intel-gpu-tools mesa-va-drivers mesa-vulkan-drivers mesa-utils vainfo vulkan-tools gstreamer1.0-gl libva-glx2
```
### Install Sound system & plugins
We will be using newer Pipewire.
```
$ sudo apt install pipewire pipewire-audio gstreamer1.0-pipewire gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly
```
### Install Bluetooth system
We need only the bluetooth system working and nothing else. The bluetooth-audio is already handled by *pipewire*.
```
$ sudo apt install bluez bluez-obexd
```
### Install Firmware
By default, Debian installs a lot of uneeded firmwares. So, remove them first including the metapackages:
```
$ sudo apt autoremove --purge firmware*
```
Now install the required firmware[^2]:
```
$ sudo apt install firmware-linux-free firmware-misc-nonfree firmware-intel-sound firmware-realtek
```
Make sure intel microcode update is installed and remove amd microcode:
```
$ sudo apt install intel-microcode
$ sudo apt autoremove --purge amd64-microcode
```
Finally, reboot the system.
```
$ sudo reboot
```

[^1]: Replace *intel-media-va-driver* package with *i965-va-driver* package for the Intel processors older than 5th Gen.
[^2]: Refer to your system hardwares for required firmwares.
