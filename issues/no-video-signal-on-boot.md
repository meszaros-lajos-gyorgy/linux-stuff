# No video signal on boot

**step 1**: press right shift during the splash screen to show GRUB

**step 2**: start in recovery mode > select "root" option

**step 3**: run `vi /etc/default/grub`

**step 4**: I changed `GRUB_CMDLINE_LINUX_DEFAULT` from the default `"quiet splash"` to `"quiet"`

**step 5**: run `sudo update-grub`

source info: https://forums.linuxmint.com/viewtopic.php?t=425655
and: https://forums.linuxmint.com/viewtopic.php?t=427068
