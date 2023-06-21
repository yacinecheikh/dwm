### Warning

This setup is incomplete, and lacks features that I forgot to push before leaving the computer with the changes.

Most notable missing features:
* proper keybindings for dwm+bépo, compositor documentation and probably some patch for dwm
* all the configs for the other suckless software


# Main contents:
* st 0.9
	* alpha 0.8.5<Down>
* dwm
	* fibonacci 6.2
	* fullgaps 6.4
	* swallow 6.3
* dmenu 5.2
	* alpha 5.2 (2023-01-10)


# sh-tools

This directory contains script that i found useful, most of the time very simple.

## menu

This script is a wrapper around dmenu, which automatically spawns dmenu in the current window and renders the choices vertically.

Don't use it as it is, customize it for your preferences and then use an alias to use it instead of dmenu.

I also plan to do something similar for dmenu_run, to whitelist the suggestions in the launch bar.


# Config files

## xprofile

The ~/.xprofile is a file loaded by LightDM at, which is used to start things at the beginning of a session.
This includes a clock refresh script, a background wallpaper, and loading the compositor

Mine can be found in the configs folder.


## Feh

Feh is just an image displayer. With dwm, it can be used to render an image over the whole screen, essentially making a wallpaper under the dwm bar.

Feh stores the last configuration it was called with in ~/.fehbg

I currently use [this](https://www.wallpaperflare.com/oshi-no-ko-anime-girls-wallpaper-yrmec) wallpaper.
This website gives you the option of automatically resizing for your screen size, so using feh is as simple as calling:
```
feh --bg-fill wallpaper.jpg
```
(I didn't include my wallpaper in this repo because I'm afraid of copyright over anime screenshots and because it is easier if you get the correct resolution in the first place)

For more configuration options, you should check ```man feh``` and type ```/--bg-scale``` to get around the part with the rendering parameters.


## Picom

Picom is an Xorg compositor, which is used to add transparency effects in the window rendering.

It is more expansive than its predecessor xcompmgr, but allows more customization and supports the blurring effects with transparent backgrounds

It can be configured with ~/.config/picom.conf, or by running picom with --config <picom.conf>.
Picom will automatically reload the config file when changed.

The current picom settings are experimental, and broke things on my GPU-less testing virtual machine.
