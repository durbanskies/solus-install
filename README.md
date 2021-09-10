# solus-install

- https://www.youtube.com/watch?v=y7B4N4nxQ3o this tutorial is good for seperate efi dual boot
- `sudo eopkg up`
- `sudo eopkg remove libreoffice-common hexchat thunderbird`
- `sudo eopkg install wine wine32 flameshot paper-icon-theme menulibre python3 htop`
- Clone qogir-theme and install
- winecfg -> virtual desktop on
- flameshot config + shortcut
- disable nouveau
  - sudo su
  - echo "modprobe.blacklist=nouveau" > /etc/kernel/cmdline
  - clr-boot-manager update
- amd gpu backlight brightness
  - sudo su
  - echo "amdgpu.backlight=0"
