### Warning

This setup is incomplete, and lacks features that I forgot to push before leaving the computer with the changes.

Most notable missing features:
* proper keybindings for dwm+bépo, compositor documentation and probably some patch for dwm
* all the configs for the other suckless software


# Main contents:
* st (0.9)
* dwm
	* fibonacci 6.2
	* fullgaps 6.4
	* swallow 6.3

# Other tools

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

For more configuration options, you should check ```man feh``` and type ```/--bg-scale``` to get around the part with the rendering types.




## Picom

Picom is an Xorg compositor, which is used to add transparency effects in the window rendering.

It is more expansive than its predecessor xcompmgr, but allows more customization and supports the blurring effects with transparent backgrounds

It is configured with ~/.config/picom.conf, or just running picom with --config <picom.conf>.
Picom will automatically reload the config file if it is changed.

