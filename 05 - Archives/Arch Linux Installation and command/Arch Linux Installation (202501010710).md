---
date: 2025-01-01T07:10
tags:
  - "#Linux"
  - "#Operating_System"
cssclasses:
  - center-images
---
# Linux Distro

### <code style="color : aqua">Source</code>  - [ArchLinux installation](https://youtu.be/4dKzYmhcGEU?si=9Ogi8suEaWQDaE9-)

## ARCHLINUX

For Linux Command - [[Arch Linux commands (202501011001)]]

Installation Steps:-
1. Create a partition for the OS (Allocated)
2. Download Arch Linux ISO [Arch Linux](https://archlinux.org/download/) x86_64iso (use the closer mirror)
3. Once done connect USB stick to the computer
4. Install Rufus [Rufus](https://rufus.ie/en/) to burn the **iso** to the USB stick 
5. Open rufus select the USB stick as *Device* and for Boot selection select the downloaded Arch Linux iso and hit start
6. Create a restore system point for window 
   ![[1-202501010710.png]]
   Hit create then name the restore point and hit create.
   (This is for recovering the windows if there an issue installing Arch)
  7. Reboot and enter BIOS
  8. In BIOS enable USB boot (if have that option)
  9. Go to the Boot option set the boot order as the USB as primary 
  10. Disable secure boot - [[Secure Boot]]
  11. Save the changes 
  12. If it fails to boot it will take you to the boot menu, where select ___Arch Linux install medium (x86_64, x64 UEFI)___ 
  13. And after that a terminal appear expecting input (here mouse functionality is disable)
  14. Type `setfont ter -132n` to increase the size and press enter to run the command
  15. Check for the internet - run `ping google.com` 
  16. Run `iwtcl` to enter iwd shell mode  (To connect from internet)
  17. Type `device list` to see the list\
  18. And type `station wlan0 get-networks` to get the wi-fi list
  19. Now run the command station `station wlan0 connect ~~wi-fi_name~~`, hit enter and press wi-fi password (if the wi-fi is connect it will not show you anything).
  20. Type `exit`
  21. Run the `ping google.com` or `ping -c 5 archlinux.org` (`ctrl + c` to interrupt the ping)
  22. Now run `pacman -Sy` to synchronize the databases
  23. Now run `pacman -S archlinux-keyring` to download packages
  24. `pacman -S archinstall`
  25. Now type `lsblk` to get all drive that present in your pc
  26. After typing the above you will see all the drive in which ==nvme0n1== is the primary drive where windows is installed now we have to create partition in the main disc for that type `cfdisk /dev/nvme0n1` (in this we can see EFI and windows partition)
  27. In the list we have to create 1 partition for the EFI files for the Linux EFI, by simply checking the free space and below type - 1G (for 1 GB) or 512M (for 512 MB).
  28. Then select he newest partition and in TYPES section select for the EFI system.
  29. And QUIT the disk manager and type `lsblk` to see the newest partition
  30. Now we have to format both the EFI and the Free space for the linux in partition by typing `mkfs.vfat -F32 /dev/(EFI name)` and `mkfs.ext4 /dev/(free space root)`. 
  31. After this we gone mount the partition for the root partition `mount /dev/(free space/root)`, now we create a directory inside of boot `mkdir /mnt/boot` and now we mount the EFI `mount --mkdir /dev/(EFI disc name) /mnt/boot`, reenter `lsblk` to check is the mount is correct(EFI disk - /mnt/boot and root - /mnt).
  32. Let's install arch now - `archinstall`
  33. Now we see a modification screen
      ![[2-Linux Installation (202501010710).png]]
      + Here select the language.
      + For the disc configuration - select the ==pre-mounted configuration== (cuz we already mounted the partition), and type `/mnt`.
      + After mounting we will see an additional option ![[3-Linux Installation (202501010710).png]] in this we secure the installation with encryption.
      + Now select the bootloader - here select either systemd-boot or grub
      + Swap value to ==True==
      + Hostname - as you want
      + Now in root password - set a root password
      + And create new user account and add it to the ==sudo== user
      + It time to install the desktop environment to do so select the profile option and set it to minimal (or other as wish -desktop have multiple)
      + Next select the graphic driver to install (remember read the types)
      + Now select the audio option and select the pipewire 
      + For kernel select the default 
      + In additional package we can enter package you wanna install in additional
      + For network configuration - use NetworkManager 
      + Select the correct timezone
      + Repo.  - depends
  34. Hit install
  35. As for next step in chroot post install - (no - esdeath , yes - default)
  36. Now we have entered the ArchLinux Terminal we are going to customize 
  37. Now run the following commands - 
      `pacman -S --needed git base-devel`
      `git clone --depth 1 https://github.com/prasanthrangan/hyprdots ~/HyDE` 
      `cd ~/HyDE/Scripts`
      `./install.sh`
  38. Now to install the login manager - `sudo pacman -S sddm`
  39. Next `hyprland` 
      `sudo pacman -S os-prober`
      `sudo nano /etc/default/grub`
      
  40. For restarting the sddm : `sudo systemctl restart sddm`
  41. To install grub in boot partition - `grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=grub` and t update the grub configuration - `grub-mkconfig -o /boot/grub/grub.cfg`
  42. now `exit` from the system and `shutdown now` and eject the pen drive
  43. <span style="background-color: red;">Important</span> -> After restart the bootloader will not show windows, so login into your arch and in terminal run `sudo pacman -Sy flatpak` for discovery
        to entry the window into grub menu  -  run `sudo -s` to enter the root mode, edit the grub menu `nano /etc/default/grub` and change the default the grub  timeout as you want and uncomment the last line `GRUB_DISABLE_OS_PROBER=FALSE` ,(`:`
      `wqa`,
      `sudo grub-mkconfig -o /boot/grub/grub.cfg`), and exit with crtl + x and inside the terminal install the `pacman -Sy os prober` and run this command to update the grub configuration - `sudo grub-mkconfig -o /boot/grub/grub.cfg` and then reboot you system - `reboot now`. 
  44. and here you finally installed ArchLinux...
  

 ![[suicide-jump.gif]]

# <span style="background-color: red;">and if you lost you whole sanity uninstall Arch</span> --> [[Deleting Dual Boot]]
