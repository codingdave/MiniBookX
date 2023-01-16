# MiniBookX
Linux Chuwi MiniBook X impovements 

Some resources to have a better Linux experience

## 61-sensor
This udev ruleI have fixes the wrongly rotated screen. Just save it as /lib/udev/hwdb.d/61-sensor-MiniBookX, make sure you have [iio-sensor-proxy](https://gitlab.freedesktop.org/hadess/iio-sensor-proxy/) installed and with [screen-autorotate](https://github.com/shyzus/gnome-shell-extension-screen-autorotate) installed and activated the screen rotates always correctly.

TODO: Fix grub rotation

## Workaround when touchpad freezes:
Unload the kernel module and load it again: 

   sudo modprobe -r i2c_hid_acpi
   sudo modprobe i2c_hid_acpi

## Workaround for xrandr:
Use [gnome-randr](https://gitlab.com/Oschowa/gnome-randr). 

   # xrandr --output XWAYLAND0 --rotate right
   gnome-randr --output DSI-1 --rotate right

## Known issues / Not yet fully working
- S3 (hibernation): screen stays black
- Touchpad: Sometimes the movement stall, the buttons are stil active. Workaround above
- Keyboard: There seem to be a bug in which the key keeps being pressed although it was released.
- Grub rotation is wrong
- When going from the laptop to the tablet mode (convertible) the touchpad and keyboard shall get disabled and vice versa. 
- xrandr cannot rotate the screen with Wayland. See workaround on top.
