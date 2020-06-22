# procedures
1. connect to the internet `wpa_supplicant, ip link`
2. set time `timedatectl set-ntp true`
3. partition by `fisk` make sure if you use efi by `ls /sys/firmware/efi/efivars`
4. format the partitions `mkfs.fat -F32` `mkfs.ext4` `mkswap` then `swapon`
5. set pacman the mirror list and others like color etc.
6. mount the `/` and `/boot`
7. install archlinux `pacstrap /mnt base base-devel linux linux-firmware vim`
8. generate fstab `genfstab -U /mnt >> /mnt/etc/fstab`
9. change root `arch-chroot /mnt`
10. localtime set `ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime`
11. Synchronize the time `hwclock --systohc`
12. uncomment line with `en_US` in `/etc/locale.gen`
13. generate locale `locale-gen`
14. make `locale.conf` file in `/etc/locale.conf` `LANG=en_US.UTF-8`
15. make `/etc/vconsole.conf` and map `caplock` key to esc by `keycode 58 = Escape`
16. set hostname `/etc/hostname`
17. set hosts `/etc/hosts` `127.0.0.1 hostname; ::1 hostname; 127.0.0.1; hostname.localdomain hostname`
18. set passwd
19. install bootloader grub `pacman -S grub efibootmgr intel-ucode(for intel only) os-prober`
20. set grub `mkdir /boot/grub`
21. generate grub conf `grub-mkconfig > /boot/grub/grub.cfg`
22. install grub `uname -m` `grub-install --target=x86_64-efi --efi-directory=/boot`
23. install network connect tools before reboot `pacman -S wpa_supplicant dhcpcd`
24. reboot
25. basic install completed
26. add user and append to wheel group `useradd -m -G wheel name` and set passwd `passwd name`
27. add wheel to sudoer `visudo`
28. refresh archlinux keyring `pacman -Sy archlinux-keyring`
29. install git
30. umcomment `color` `ilovecandy` in `pacman.conf`
31. use all core for compile files `sed -i "s/-j2/-j$(nproc)/;s/^#MAKEFLAGS/MAKEFLAGS/" /etc/makepkg.conf`
32. install yay `curl -sO https://aur.archlinux.org/cgit/aur.git/snapshot/yay.tar.gz` `cd tar makepkg`
33. dbus uuid `dbus-uuidgen > /var/lib/dbus/machine-id`
34. system bee off `rmmod pcspkr; echo "blacklist pcspkr" > /etc/modprobe.d/nobeep.conf`


# Softwares
install the softwares after connect to internet and sort the fastest mirrors
p: pacman a: aur g:git

| packages               | how to | comments                                      |
|------------------------|--------|-----------------------------------------------|
| man                    | p      | manual page                                   |
| man-db                 |        | man page                                      |
| networkmanager         | p      | for internet(systemctl enable NetworkManager) |
| network-manager-applet | <++>   | <++>                                          |
| xorg                   |        | x                                             |
| xorg-server            |        | x                                             |
| xorg-xinit             |        | x                                             |
| xdg-utils              |        | filetype utilitoes                            |
| python3 pip            | <++>   | <++>                                          |
| i3                     |        | wm                                            |
| compton                |        | desktop env                                   |
| fontconfig             |        | dev                                           |
| noto-fonts             |        | <++>                                          |
| ttf-linux-libertine    |        | font                                          |
| arandr                 |        | UI for screen adjustment                      |
| bc                     |        | caculator                                     |
| dosfstools             |        | access dos-like filesystem                    |
| exfat-utils            |        | fat filesystem manage                         |
| neovim                 |        | editor                                        |
| ffmpeg                 |        | video editing                                 |
| mpv                    |        | video player                                  |
| ntfs-3g                |        | ntfs partition                                |
| pulseaudio-alsa        |        | audio system                                  |
| unclutter              |        | hides inactive mouse                          |
| unzip                  |        | decompress                                    |
| unrar                  |        | decompress                                    |
| youtube-dl             |        | download videos                               |
| zathura                |        | pdf reader                                    |
| zathura-pdf-mupdf      |        | reader                                        |
| pandoc                 |        | pdf tools                                     |
| mediainfo              |        | video audio tool                              |
| atool                  |        | archives tool                                 |
| fzf                    |        | fuzzy finder                                  |
| highlight              |        | highlight code                                |
| ranger                 |        | file explorer                                 |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
| <++>                   | <++>   | <++>                                          |
