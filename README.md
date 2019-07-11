# win2alt

A plugin for [Interception Tools](https://gitlab.com/interception/linux/tools)
for swapping "super" and "left_alt" buttons.


## Intoduction

Due to muscle memory of using mac keyboard layout for several years I got used
to have "left alt" button before "super" button. After switcing back to Linux
I've tried to restore a conviniet set of keybindings such as capslock to
ctlr/esc. I found a great [caps2esc](https://gitlab.com/interception/linux/plugins/caps2esc) project which provides exactly what I needed.

Unfortuanetly, for some reason when I set up caps2esc, I lost all keybindings
which I set up via xmodmap. This plugin is just a workaround while I'm trying
to figure out an appropriate solution.

## Building

```
$ git clone https://github.com/keepclean/win2alt.git
$ cd win2alt && mkdir build && cd build
$ cmake ../
$ make
```

## Notes

### About KEY_COPY

On my laptop button "super" aka "win" is "KEY_COPY" and has keycode "133".
List of Linux events codes is [here](https://github.com/torvalds/linux/blob/master/include/uapi/linux/input-event-codes.h).

`xev` program can help to find out which keycode stands for "super" button on system.

### An example of udevmon.yaml config file

```
- JOB: "intercept -g $DEVNODE | caps2esc | win2alt | uinput -d $DEVNODE"
  DEVICE:
    EVENTS:
      EV_KEY: [KEY_CAPSLOCK, KEY_ESC, KEY_COPY, KEY_LEFTALT]
```
