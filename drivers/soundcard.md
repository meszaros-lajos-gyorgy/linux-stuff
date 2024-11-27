# Soundcard driver

Focusrite Scarlett Solo 4th Gen

Based on https://github.com/Focusrite-Scarlett-on-Linux/sound-usb-kernel-module/issues/22#issuecomment-1819212736

**step 1**: open terminal

Linux Mint 22 switched to pipewire, need to go back to pulseaudio:

```
apt purge pipewire pipewire-bin
systemctl enable --user pulseaudio
```

**step 2**: have `pavucontrol` installed by running `sudo apt install pavucontrol`

**step 3**: run `pavucontrol` and go to the last tab settings and set all device profiles to `Off` except for `Scarlett Solo 4th Gen`

**step 4** still within pavucontrol settings set Scarlett's profile to `Digital Stereo (IEC958) kimenet + Többcsatornás bemenet`

**step 5** close pavucontrol

**step 6**: get the ID for the soundcard by running `pactl list sources short | grep multichannel`

It will output something like this:

```
5       alsa_input.usb-Focusrite_Scarlett_Solo_4th_Gen_XXXXXXXXXXXXXXXX-00.multichannel-input     module-alsa-card.c      s32le 4ch 44100Hz       RUNNING
```

**step 7**: add virtual devices to pulse audio config

Create a `~/.config/pulse/default.pa` file with contents:

```sh
# source: https://github.com/Focusrite-Scarlett-on-Linux/sound-usb-kernel-module/issues/22#issuecomment-1819212736

.include /etc/pulse/default.pa

load-module module-remap-source source_name=Mic master=alsa_input.usb-Focusrite_Scarlett_Solo_4th_Gen_S1677PN330264A-00.multichannel-input master_channel_map=front-right remix=no channel_map=mono
update-source-proplist Mic device.description=Mic

load-module module-remap-source source_name=StereoOut master=alsa_input.usb-Focusrite_Scarlett_Solo_4th_Gen_S1677PN330264A-00.multichannel-input master_channel_map=rear-left,rear-right remix=no channel_map=front-left,front-right
update-source-proplist StereoOut device.description=StereoOut
```

**step 8**: restart the computer
