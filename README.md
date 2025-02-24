# Shell Handy Examples for Linux (SHEL)

Goal: "To became your handbook for often small tasks"

A bunch of Markdown and script files with handy code snippets for Linux shell users.

* ✓ References to trusted sources
* ✓ Open to issue reports, feature requests and merge requests
* ✓ Use it in your company for commercial use
* ✓ AI friendly structured
* ✓ Free forever

## Content

* [general shell cheatsheets](topics/general_shell_cheatsheets.md)

### TODO (sorry, not yet)

* [text manipulations](topics/text_manipulations.md) … `head`, `sed`, `awk`, `sort`, …
* [bash](topics/bash.md) … `while read`, `set`, `test` …
* [one running instance](topics/one_running_instance.md) … `flock`, `lockfile`, `pidof`, …
* [directory synchronizations](topics/directory_synchronizations.md) … `rsync`, `cp`, `btrfs`, `rclone`, …
* [directory browsers](topics/directory_browsers.md) … `mc`, `which`, `find`, …
* [directory space usage](topics/directory_space_usage.md) … `du`, `ncdu`, `btdu`, …
* [directory](topics/directory.md) … `du`, `ncdu`, `btdu`, …
* [(un)compress](topics/compress.md) … `tar`, `gzip`, `find ... -exec gzip`, …
* [partitions](topics/partitions.md) … `cfdisk`, `sfdisk`, `fdisk`, …
* [partition encryption](topics/partition_encryption.md) … `cryptsetup luksFormat`, `cryptsetup luksOpen`, `cryptsetup luksChangeKey`, …
* [block devices](topics/block_devices.md) … `lsblk`, `blkid`, `dd`, `mountpoint`, `findmnt`, …
* [LVM](topics/LVM.md) … `pvs`, `vgs`, `lvs`, …
* [fstab](topics/fstab.md) … `swap`, `ext4`, `btrfs`, …
* [systemd units](topics/systemd_units.md) … `systemctl`, `journalctl`, `*.service`, …
* [remote access](topics/remote_access.md) … `ssh`, `nxserver`, …
* [text screen multiplexers](topics/text_screen_multiplexers.md) … `screen`, `tmux`, …
* [text editors](topics/text_editors.md) … `vim`, `nano`, `mcedit`, …
* [Btrfs](topics/Btrfs.md) … `btrfs subvolume`, `btrfs filesystem`,  `btrfs property set`, `btrfs send+receive`, …
* [ZFS](topics/ZFS.md) … `zfs create`, `zfs send+receive`, …
* [file encryption](topics/file_encryption.md) … `gpg`, `ecryptfs-setup-private`, …
* [RAID](topics/RAID.md) … `/proc/mdstat`, `mdadm`, …
* [regular expressions](topics/regular_expressions.md) … `egrep`, …
* [DynamicMapper (DM)](topics/DynamicMapper_DM.md) … `losetup`, `dmsetup`, …
* [network configuration](topics/network_configuration.md) … `ip address`, `iptables`, `iptables-save`, `ufw` …
* [network monitoring](topics/network_monitoring.md) … `tcpdump`, `tshark`, `nethogs`, `netcat`, `ss`, …
* [WireGuard (VPN)](topics/WireGuard_VPN.md) … `wg`, `wg-quick`, `/etc/wireguard`, …
* [script best-practices](topics/script_best_practices.md) … `bash`, `python3`, …
* [system boot rescue](topics/system_boot_rescue.md) … `mount --rbind`, `chroot`, `update-grub`, `update-initramfs -u`, `grub-install`, …

## Author's favorite examples

### First lines of the BASH script

```shell
#!/usr/bin/env bash
set -euo pipefail
```

Explanation:

* `#!/usr/bin/env bash` … use also for `sh`, `php`, `python3`, …; makes the script compatible with strange Linuxes, BSD, macOS, …
* `set -e` … exit on error (any non-zero command return code)
* `set -u` … treat unset variables as an error (typos prevention)
* `set -o pipefail` … fail on first error in pipelines (e.g. `cat non-existing-file | head -n 2 | tail -n 1` will fail)

References:

* https://man7.org/linux/man-pages/man1/set.1p.html
* https://unix.stackexchange.com/questions/240749/bash-script-best-practice

### Rescue Linux boot from a live Linux

```shell
mkdir /target
mount /dev/... /target
cd /target
mount -t proc /proc proc
mount --rbind /sys sys
mount --rbind /dev dev
chroot .
```

You can download this script and place it to the root directory of your OS to make this easy in the future: [rescue-mount](scripts/rescue-mount)


References:

* https://superuser.com/questions/165116/mount-dev-proc-sys-in-a-chroot-environment

