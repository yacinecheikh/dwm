## custom dwm setup

This repository includes dwm and the modifications I made for my setup.

I used this to patch my Xubuntu 22 light install and use dwm instead of xfce4.
I also customized the keybindings for my [bépo](https://bepo.fr/wiki/Accueil) keyboard.


This version of dwm includes the following patches:
 * swallow
 * full gaps
 * next prev tag (shiftview.c)
 * fibonacci layout

I also used the following programs to complete the setup:
 * feh
 * dmenu
 * xcompmgr


### Requirements before building

Although you can try dwm without building it, you have to build it by yourself if you want to customize it like I did.
In order to build dwm, you will need the following packages:

```
sudo apt install build-essential suckless-tools libx11-dev libxinerama-dev libxft-dev stterm
```
 * stterm is the suckless st simple terminal, and is not required if you plan to use the xfce4-terminal instead (I prefer the xfce terminal)
 * In case I missed it, you might need sharutils too

If you use my patched code, the swallow patch requires dependencies that are not in the package manager:
 * libxcb
 * Xlib-libxcb
 * xcb-res

By googling the headers needed, I found these (debian) packages that provide the same headers:
 * libx11-xcb-dev
 * libxcb-res0-dev

If you want to do it the proper way, the libraries can be built from source



## Installation

There are two ways to install dwm.

The first one, the easiest, is to just download the binaries from apt:

```
sudo apt install dwm suckless-tools feh
```

This binary of dwm is configured to use xfce4-terminal already, so you do not need st.

dmenu, the app starting menu for dwm, is included in the suckless-tools package

feh is needed unless you want to keep the wallpaper of the login screen theme. I prefer having a different wallpaper once logged in.


Note:

While testing, I found out that dwm can be run from the terminal with xinit, after stopping the graphical interface lightdm with ```sudo service stop lightdm``` and manually writing ~/.xinitrc with ```numlockx on``` to enable the numpad, ```~/.fehbg``` to enable the background and ```exec dwm``` to start dwm.

Since I didn't know the difference between a display manager and a window manager, I also replaced the path to lightdm in /etc/X11/default-display-manager with /usr/bin/dwm

Although it worked perfectly for days, my OS would stop at the splash screen after reboot. I don't really recommend it if you don't know what you are doing, unless you want to have to chroot into your system from a live usb in order to undo these changes.

Ctrl+Alt+[1-9] is the key binding to switch between linux desktops

This is a fun experience if you like being able to manually break and repair your linux by yourself.


After installing dwm, you can choose which window manager you want to use on the (lightdm) login screen.

The default keybindings for dwm can be found [here](https://gist.github.com/erlendaakre/12eb90eef84a3ab81f7b531e516c9594).

The Mod key is Alt by default, and Alt+p can be used to start new processes if you have dmenu. You can also quit dwm with Alt+Shift+q

(That's usually the moment where you have to think about what you want to do with your computer, once you have nothing on the desktop and no start menu anymore)




If you want to configure dwm by yourself (or use my custom version), you just have to build and install dwm in order to replace any previously existing (apt) dwm install.

If you already have the requirements to build dwm, you can install it from the source folder with:

```
sudo make clean install
```



To setup your own background wallpaper, see the Background section below.

To customize dwm and install your own patches, see the Customization section below.


### Background
----------
I used feh to run the background.

Although using it is simple, the exact command you use depends on how much your wallpaper matches your screen resolution.

```man feh``` and a /--bg-scale query will set you around the parameters you will need to use.

The basic usage is something like this: ```feh --bg-fill image.png```

Once you have used feh to load a background wallpaper from the terminal, you can add ```~/.fehbg``` to ~/.xprofile (this file is loaded by lightdm after login) the wallpaper persistant.

### Transparency

Adding transparency was [far simpler than I expected](https://wiki.archlinux.org/title/xcompmgr).

If you have the same setup as mine (Ubuntu LTS 22.04), the only thing to do is install xcompmgr:

```
sudo apt install xcompmgr
```

run it

```
xcompmgr -c
```

and add it to .xprofile with the feh background command

```
~/.fehbg
xcompmgr -c &
```


### Customization

dwm can be further patched with ```patch -p1 < patches/<patch>```,
and can be configured by editing config.h.

The config.def.h is a generated default config, and is modified by patches.

If you add new patches that modify config.def.h, you will have to include these changes in your config.h.
