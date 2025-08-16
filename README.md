# Gentoo

This is a personal repository containing config files for my Gentoo
installation with DWM. Plus, being Gentoo, my make.conf
and Kernel configuration file.

# Kernel
The kernelConfig file can be placed at /usr/src/linux/.config on T480 machines, minor changes to WiFi firmware loading required as of 6.6-21.
I have it setup to build with support for:
- Virtualised guest machines
- LUKS on LVM
- EXT4 root filesystem
- Support for IWD, Wireguard, NFS and CIFS/SMB

# Make.Conf
Some of the stuff that is defined here:
- Intel i7 8650U CPU Flags
- LUKS on LVM
- PipeWire Audio
- Build with en_GB localisation where available
- UEFI GRUB target
- The heretical ACCEPT_LICENSE="*"

# 16.0

Added 16.0 config (need to check it)
Switched from VirtualBox and VMWare to libvirtd, qemu and virt-manager

# DWM suckless


# Installation of Gentoo (cheatsheet)

$ emerge -av sys-kernel/gentoo-sources sys-kernel/linux-firmware
$ eselect kernel list
$ eselect kernel use {X}
$ eselect kernel set 1
$ cd /usr/src/linux
$ make localyesconfig
$ make -j13
$ make modules_install
$ make install
$ echo 'GRUB_PLATFORMS="efi-64"' >> /etc/portage/make.conf 
$ emerge --ask sys-boot/grub
$ grub-install --target=x86_64-efi --efi-directory=/efi
$ grub-mkconfig -o /boot/grub/grub.cfg
$ emerge --ask net-misc/dhcpcd
$ rc-update add dhcpcd default
$ rc-service dhcpcd start
$ emerge --ask sys-apps/iproute2 net-wireless/wpa_supplicant net-wireless/iw net-wireless/wireless-tools

