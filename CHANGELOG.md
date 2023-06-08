# Change Log

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/)
and this project adheres to [Semantic Versioning](http://semver.org/).

## [Open]

### To Add

* Add parts missed here but used [here](https://gist.github.com/Soulsuke/6a7d1f09f7fef968a2f32e0ff32a5c4c)
* Add [encrypted swap partition](https://github.com/stevleibelt/arch-linux-configuration/issues) to support suspend-to-disk
* Add automatic installation of fitting [xorg drivers](https://wiki.archlinux.org/title/Xorg#Installation)
* Add [pacman hook](https://wiki.archlinux.org/title/Dynamic_Kernel_Module_Support#Initial_ramdisk) when zfs-dkms is installed
* Add usage of `localectl set-{keymap|locale|x11-keymap}` as figured out [here](https://github.com/sddm/sddm/issues/202)

### zfsbootmenu

* Dynamic disk in 01-mount.sh recover script
* Periodic trim with timer when host is down ? https://unix.stackexchange.com/a/352596
* Reflector systemd timer
* ZFS
  * Zfs hibernate without swap ?
  * Smart test timer ?
  * Periodic zfs-scrub
  * Pacman hook to "generate-zbm" at each zfs-dkms upgrade
* DNS
  * Fix DNS per interface ? as https://github.com/jonathanio/update-systemd-resolved#preventing-leakage-to-corporate-networks
* SERVICES
  * Hardware acceleration packages
  * Disable ipv6
* IMPROVMENTS
  * Move max aur package to community equivalents
* TESTS
  * Zfs trim + zfs autoscrub systemd timer
  * Reflector at startup
  * Test resume in GRUB_CMDLINE_LINUX

### To Change

* Move `install.conf` creation out of 02-installation.sh and put it in 01-configuration.sh
  * Create a `install.dist.conf` that is used in 02-installation.sh if `install.conf` is not available
* Solve locale grub : https://forums.archlinux.fr/viewtopic.php?t=13830

## [Unreleased]

### Added

### Changed

## [2.0.1](https://github.com/stevleibelt/arch-linux-configuration/tree/2.0.1) - released at 20230608

### Changed

* Fixed [issue/3](https://github.com/stevleibelt/arch-linux-configuration/issues/3)

## [2.0.0](https://github.com/stevleibelt/arch-linux-configuration/tree/2.0.0) - released at 20230608

### Added

* Added option to create an unencrypted `zroot`
* [ZFS Install](scripts/zfs/install)
  * Added support for `install.dist.conf`
* Started [help](doc/help) section
* Added selection of `archzfs-dkms` or `archzfs-linux[-lts]` should be installed

### Changed

* Fixed [issue/2](https://github.com/stevleibelt/arch-linux-configuration/issues/2)
* Fixed issue with $zpoolname in the `mkinitcpio.conf` generation
* Fixed issue when configuring dns
* Fixed issue when configuring network by using NetworkManager
* Fixed issue when removing existing user
* Changed where the configuration is done
  * Configuration is now done in `01-configure.sh`
  * You can execute `02-install.sh` without any previously done configuration, `install.dist.conf` is then used

## [1.1.0](https://github.com/stevleibelt/arch-linux-configuration/tree/1.1.0) - released at 20230101

### Changed

* Merged with [latest](https://github.com/eoli3n/arch-config/commit/fe88200e17a26a6734eb954e96f2a9b6cf4efe71) code from [upstream](https://github.com/eoli3n/arch-config)

## [1.0.0](https://github.com/stevleibelt/arch-linux-configuration/tree/1.0.0) - released at 20220820

### Added

* Added [LICENCE](LICENCE)
* [ZFS Install](scripts/zfs/install)
  * Added asking for zpool name
  * Added asking for keymap
  * Added asking for locale
  * Added asking for timezone
  * Added asking to configure networking
  * Added asking to configure dns
  * Added asking for kernel (`linux` or `linux-lts`)
  * Added usage of install.conf file to ease up multiple runs of the script (yep, perfect if you have to develop this script)
  * Added support for networkmanager configuration
  * Added prefix of >>:: << on each `print`-output
  * Added automatic detection of ucode package file (currently only amd and intel are supported)
* This [CHANGELOG](CHANGELOG.md)

### Changed

* Updated [README.md](README.nd)
* [ZFS Install](scripts/zfs/install)
  * Added switch to either install amd or intel ucode
  * Added check to only configure intel gpu modules when intel gpu is on the system
  * Moved installation of `iwd` and `wpa_supplicant` into section "configure networking"

