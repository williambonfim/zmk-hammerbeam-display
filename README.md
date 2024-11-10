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

Next, replace the built-in status screen by adding `dongle_display` to your `build.yaml`:

```yaml build.yaml
---
include:
  - board: nice_nano_v2
    shield: corne_peripheral_right hammerbeam_display
```

This shield assumes that the oled screen is already set up and functioning with the built-in status screen.