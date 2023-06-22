## custom st build for Xubuntu 22.04 LTS

### Patches
* alpha 0.8.5
* delkey (planned, the patch requires manual tinkering)

### Install

st can be built with ```sudo make clean install```, like dwm.

The alpha patch is used to configure background transparency without text transparency (using the compositor works, but makes the text half-unreadable)
