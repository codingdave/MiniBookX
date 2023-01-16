# MiniBookX
Linux Chuwi MiniBook X impovements 

Some resources to have a better Linux experience

## Fixes

### 61-sensor
This udev rule fixes the wrongly rotated screen. Just save it as /lib/udev/hwdb.d/61-sensor-MiniBookX, make sure you have [iio-sensor-proxy](https://gitlab.freedesktop.org/hadess/iio-sensor-proxy/) installed and with [screen-autorotate](https://github.com/shyzus/gnome-shell-extension-screen-autorotate) installed and activated the screen rotates always correctly. 

### Grub menu too small:
Edit `/etc/default/grub` and change `GRUB_GFXMODE` to `1280x1024x32`. Then re-create the grub boot menu.

```
GRUB_GFXMODE=1280x1024x32
```
=

### kernel boot messages rotated:
Edit `/etc/default/grub` and add `fbcon=rotate:1` to `GRUB_CMDLINE_LINUX`. Then re-create the grub boot menu.

```
GRUB_CMDLINE_LINUX="fbcon=rotate:1"
```

## Workarounds

### Touchpad freezes:
Unload the kernel module and load it again: 

```
sudo modprobe -r i2c_hid_acpi
sudo modprobe i2c_hid_acpi
```

### xrandr:
randr does not work and either does nothing or reports an error:

```
xrandr --output XWAYLAND0 --rotate normal
 X Error of failed request:  BadMatch (invalid parameter attributes)
   Major opcode of failed request:  140 (RANDR)
   Minor opcode of failed request:  7 (RRSetScreenSize)
   Serial number of failed request:  22
   Current serial number in output stream:  2
```

Using [gnome-randr](https://gitlab.com/Oschowa/gnome-randr) you can change the display from the command line

```
gnome-randr --output DSI-1 --rotate right
```

## Known issues / Not yet fully working
- S3 (hibernation): screen stays black
- Touchpad: Sometimes the movement stall, the buttons are stil active. Workaround above
- Keyboard: There seem to be a bug in which the key keeps being pressed although it was released.
- Grub rotation is wrong
- When going from the laptop to the tablet mode (convertible) the touchpad and keyboard shall get disabled and vice versa. 
- xrandr cannot rotate the screen with Wayland. See workaround on top.

## TODO
- grub rotation
- detect-tablet-mode
- tablet-mode
