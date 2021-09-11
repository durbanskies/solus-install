# solus-install
### Solus (budgie) so far seems to be the best distro for Legion 5 15ARH05 as it is stable, yet rolling release with an recent kernel. Trackpad and brightness works well. The propriety tested nvidia drivers can be installed with DoFlicky. Windows 10 dual boots well with lower chance of screw ups due to two efi files. EOPKG + Flatpaks + Snaps + Appimages gives you sandboxed compatibility with basically everything on linux. Wine also runs very well (be sure to install 32bit libs for wine and for your gpu drivers). Bluetooth and printing works and the battery life is great
- https://www.youtube.com/watch?v=y7B4N4nxQ3o this tutorial is good for seperate efi dual boot
- `sudo eopkg up`
- `sudo eopkg remove libreoffice-common hexchat thunderbird`
- `sudo eopkg install wine wine32 flameshot paper-icon-theme menulibre python3 htop`
- Clone qogir-theme and install
- winecfg -> virtual desktop on
- flameshot config + shortcut
- disable nouveau !!!
  - `sudo su`
  - `echo "modprobe.blacklist=nouveau" > /etc/kernel/cmdline`
  - `clr-boot-manager update`
- amd gpu backlight brightness !!!
  - `sudo su`
  - `echo "amdgpu.backlight=0"`
  - `clr-boot-manager update`
