## custom st build for Xubuntu 22.04 LTS

### Patches
* alpha 5.2 (2023-01-10)


### Install

```sudo make clean install```
The alpha patch is essential, as it allows dmenu to run in windows that support transparency (almost any window).
To run dmenu in a window, run ```dmenu -w $WINDOWID```.
