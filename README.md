# MiniBookX
Linux Chuwi MiniBook X impovements 

Some resources to have a better Linux experience

## 61-sensor
This udev ruleI have fixes the wrongly rotated screen. Just save it as /lib/udev/hwdb.d/61-sensor-MiniBookX, make sure you have [iio-sensor-proxy](https://gitlab.freedesktop.org/hadess/iio-sensor-proxy/) installed and with [screen-autorotate](https://github.com/shyzus/gnome-shell-extension-screen-autorotate) installed and activated the screen rotates always correctly.

TODO: Fix grub rotation
