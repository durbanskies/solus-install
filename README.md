# solus-install
### Solus (budgie) so far seems to be the best distro for Legion 5 15ARH05 as it is stable, yet rolling release with an recent kernel.
#### Trackpad and brightness works well. The propriety tested nvidia drivers can be installed with DoFlicky. Windows 10 dual boots well with lower chance of screw ups due to two efi files. EOPKG + Flatpaks + Snaps gives you sandboxed compatibility with basically everything on linux. Wine also runs very well (be sure to install 32bit libs for wine and for your gpu drivers). Bluetooth and printing works and the battery life is great

## Installation :
 (Dual boot Solus and Windows 10 with seperate EFI files)
- Solus requires a minimum 500mb EFI so **either** [resize windows EFI](https://superuser.com/questions/1230741/how-to-resize-the-efi-system-partition) or use 2 EFI files and choose between them in the boot device selection menu. This is on a UEFI system
- Windows 10 :
  - Shrink (C:) partition using diskmgmt.msc
  - Disable fast startup in power options
- Boot into Solus while on hybrid mode
- Launch GParted :
  - Create 3 partitions in free space you made before
    - 512MB as **FAT32**
    - 4096MB as **linux-swap**
    - Remaining as **EXT4**
  - After created, right click and assign boot flag to the *512MB FAT32 EFI*
  - The windows 10 installation also has a 100MB FAT32 EFI file, right click and uncheck the boot flag
  - Making sure there is only 1 partition with the **boot, esp** flags, the other efi for windows is likely now flagged as *msftdata*
  ![onlybootflag](onlybootflag.png)
- Close Gparted and **restart** to prevent the installer from being stuck on the "Examining local storage" operation
- Run the installer, on the *Disks* section :
  - Choose the option to assign mount points
  - Find the EXT4 partition we made in Gparted, and choose `/` as the mount point

## Post Install :
- `sudo eopkg up`
- `sudo eopkg remove libreoffice-common hexchat thunderbird`
- `#sudo epokg install wine wine32`
- `sudo eopkg install flameshot paper-icon-theme menulibre python3 htop ant-dracula-gtk-theme openjdk-8 protonvpn-cli git`
- enable backlight + blacklist nouveau
  - `sudo su`
  - `echo "amdgpu.backlight=0 modprobe.blacklist=nouveau" > /etc/kernel/cmdline`
  - `clr-boot-manager update`