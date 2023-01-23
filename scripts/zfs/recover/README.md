# ArchIso

## Connect to wifi

```bash
#start programm
iwctl

#list available devices
device list

#fetch available networks
station <string: device> scan

#display found networks
station <string: device> get-networks

#connect
station <string: device> connect <string: ssid>
```

## Fix broken installation

This can fix if zfs module can't be loaded during boot.

Best of luck!

* Boot [archiso with zfs](https://archzfs.leibelt.de/)
* `git clone https://github.com/stevleibelt/arch-linux-configuration`
* `bash arch-linux-configuration/scripts/zfs/recover/01-mount.sh`
* `arch-chroot /mnt`
* `yay -S zfs-dkms`
* `mkinitcpio -P`

