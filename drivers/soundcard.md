# Soundcard driver

Focusrite Scarlett Solo gen 4

https://github.com/Focusrite-Scarlett-on-Linux/sound-usb-kernel-module/issues/22#issuecomment-1819212736

**step 1**: get the ID for the soundcard:

`pactl list sources short | grep multichannel`

It will output something like this:

```
5       alsa_input.usb-Focusrite_Scarlett_Solo_4th_Gen_XXXXXXXXXXXXXXXX-00.multichannel-input     module-alsa-card.c      s32le 4ch 44100Hz       RUNNING
```

**step 2**: add a virtual mono device to pulse audio config

Create a `~/.config/pulse/default.pa` file with contents like this:

```sh
.include /etc/pulse/default.pa

load-module module-remap-source source_name=Mic master=alsa_input.usb-Focusrite_Scarlett_Solo_4th_Gen_XXXXXXXXXXXXXXXX-00.multichannel-input master_channel_map=front-right remix=no channel_map=mono
update-source-proplist Mic device.description=Mic
```

**step 3**: restart the computer
