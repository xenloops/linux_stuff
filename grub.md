


## GRUB doesn't boot to Linux in an EFI system

Reinstall the GRUB boot loader to your Ubuntu installation in EFI mode:

* Boot from the Ubuntu installation medium and select "Try Ubuntu without installing"
* Once in the Live desktop, open a terminal and execute the following commands (the sudo/root password for Debian Live is ```live```).
* To identify the partitions use GParted (included in the Live boot), or run ```sudo fdisk -l```.
  * ```sudo mount /dev/sdXY /mnt```
  * ```sudo mount /dev/sdXX /mnt/boot/efi```
  * ```for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done```
  * ```sudo chroot /mnt```
  * ```grub-install /dev/sdX```
  * ```update-grub```
  * ```exit```
 
Where sdX = disk, sdXX = efi partition, and sdXY = system partition.

Note: If ```grub-install``` returns an error, it cannot find efivars. Try the following while still in the chroot environment:

* ```mount -t efivarfs none /sys/firmware/efi/efivars```
* Then execute the grub-install command again: ```grub-install /dev/sdX```
* To avoid possible unexpected issues, properly unmount the file systems afterwards (rebooting should also do this).
  * ```sudo umount /dev/sdXX```
  * ```sudo umount /dev/sdXY```

After running the commands, GRUB will be installed in the separate EFI partition.
