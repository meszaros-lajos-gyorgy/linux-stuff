# No video signal on boot

**step 1**: press right shift during the splash screen to show GRUB

**step 2**: start in recovery mode

**step 3**: run `vi /etc/default/grub`

**step 4**: I changed back my `GRUB_CMDLINE_LINUX_DEFAULT` from `quiet splash drm.vblankoffdelay=0` to the default `quiet splash`
