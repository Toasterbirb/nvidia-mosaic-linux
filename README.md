# Nvidia mosaic on linux
An example on how to use nvidia mosaic with 3 monitors on Linux. Script to toggle it on and off included.

Settings in the provided xorg.conf are made for the following monitor configuration:
![monitor array](./monitor_configuration.png)
(1920x1080 2560x1080 1920x1080)

Setup the monitors with arandr and then tweak the following settings depending on your monitor array.

The magical part in /etc/X11/xorg.conf
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "GPU-0.HDMI-0: nvidia-auto-select +1920+0, GPU-0.DP-1: nvidia-auto-select +0+0, GPU-0.DP-3: nvidia-auto-select +4480+0"
    Option         "nvidiaXineramaInfo" "True"
    Option         "BaseMosaic" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```
