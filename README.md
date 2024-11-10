# zmk-hammerbeam-display
# OLED Display

This module repository provides a ZMK shield that replaces the built-in status screen with a custom screen designed for 128x32-pixel OLED displays.

## Usage

To use this module, first add it to your `config/west.yml` by adding a new entry to `remotes` and `projects`:

```yaml west.yml
manifest:
  remotes:
    - name: zmkfirmware
      url-base: https://github.com/zmkfirmware
    - name: williambonfim
      url-base: https://github.com/williambonfim
  projects:
    - name: zmk
      remote: zmkfirmware
      revision: main
      import: app/west.yml
    - name: zmk-hammerbeam-display
      remote: williambonfim
      revision: main
  self:
    path: config
```

Next, replace the built-in status screen by adding `hammerbeam_display` to your `build.yaml`:

```yaml build.yaml
---
include:
  - board: nice_nano_v2
    shield: corne_peripheral_right hammerbeam_display
```

This shield assumes that the oled screen is already set up and functioning with the built-in status screen.

by default the this urchin animation will run for a duration of 300 seconds, 10 seconds per picture, fairly slow to save battery

# Usage
If you want to change the speed of the animation, you can edit the speed by changing the `CONFIG_CUSTOM_ANIMATION_SPEED` in your `.conf` file

```conf
CONFIG_CUSTOM_ANIMATION_SPEED=300000 # 300 second total duration
# 30 pictures - 300/30 = 10 seconds per picture
```

## References
- [Dongle display](https://github.com/englmaxi/zmk-dongle-display/blob/main/README.md) by englmaxi
- [Hammerbeam slideshow to nice!view](https://github.com/GPeye/hammerbeam-slideshow) by GPeye