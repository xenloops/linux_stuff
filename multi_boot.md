# Multi-booting your PC
or "How to get your proprietary, monolithic PoS OS to share"

Please note, these instructions assume use of the KDE desktop in Debian Linux. If you're attempting this, you should have little problem adapting to other desktops and distributions.

## Put Linux on a bootable USB stick

### If you're using Linux

1. Download a "live CD/DVD/USB" version of the distro you want. (I prefer [Debian](https://cdimage.debian.org/debian-cd/current-live/amd64/bt-hybrid/), but others work well.) Once it's downloaded, be sure to check its authenticity with its SHA hash or PGP signing key (legit distros show you how).
2. Open a Terminal and find out where the USB is mounted with the command ```sudo fdisk -l```. It should be something like ```/dev/sda```, but check the size and disk model to be sure. 
3. Use _one_ of the following commands to copy the downloaded .iso to the USB stick (this will take a few minutes):
   * ```sudo cp <live iso file> <USB location>```
   * ```sudo dd if=<live iso file> of=<USB location> bs=16M status=progress oflag=sync```
5. Eject the USB stick.

### If you're using Windows

(Coming soon)

## Put Windows on a bootable USB stick
(Coming soon)

## Nothing installed yet
(Coming soon)

## If Linux is already installed

1. Back up your drive if you're concerned about losing existing data (hasn't happened to me yet, but I've only been doing this for 20 years).
2. Boot from the Linux live USB.
3. Open App menu > System > KDE Partition Manager.
4. Resize the partition(s) on the drive to make room for the new install. Recommend giving Windows a bit more than Linux, since Windows and its applications tend to take up more space than Linux. (Gotta have room for all that crappy outdated code.)
5. Reboot from the Windows USB stick.
6. Install Windows. Skip entering a product key at this time.
7. Finish installing, making setting selections that leave your computer insecure and wide open to Microsoft, advertisers, and PII data resellers. Wait for it to finish setting up your computer, cleaning up, and saying "Hi". Spend this time asking yourself why a commercially produced OS developed by thousands of highly trained and well paid engineers takes three times longer than an open-source OS written by a scrappy rag-tag bunch of volunteers to set up.
8. When it's finally done, reboot from the Linux live USB.
9. Open a terminal: App menu > System > Konsole.
10. Enter these commands in turn:
    1. List the partition data: `sudo fdisk -l`; find the Device for the Linux filesystem type that holds the Linux you normally boot into. (I'll use `/dev/sda1` for this example -- be sure to change this to suit your system.)
    2. [Coming soon: Special consideration for LVM systems]
    3. Mount the partition: `sudo mount /dev/sda1 /mnt`
    4. Mount any `/boot`, `/var`, or `/usr` partitions that are separate from the main one to `/mnt/boot`, `/mnt/var`, or `/mnt/usr`, respectively.
    5. Bind other needed mounts: `for i in /sys /proc /run /dev; do sudo mount --rbind "$i" "/mnt$i"; done`
    6. [Coming soon: Special consideration for EFI systems]
    7. Chroot into the system partition: `sudo chroot /mnt`
    8. Reinstall Grub: `grub-install /dev/sda`
    9. Update grub: `update-grub`
    10. [More EFI stuff coming soon.]
    11. Leave the chroot mode" `exit`
11. Reboot, removing the USB stick when appropriate.

This should bring you to the Grub menu, from which you should be able to select Linux or (if you must) Windows.

## If Windows is already installed
(Coming soon)


