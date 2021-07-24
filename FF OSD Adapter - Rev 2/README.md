# FF OSD Adapter - Rev 2

This adapter allows a FF OSD Blue Pill to be easily connected to a Gotek and a supported Amiga RGBtoHDMI adapter.

keirf's FF OSD: https://github.com/keirf/FF_OSD

Supported RGBtoHDMI boards: https://github.com/solarmon/RGBtoHDMI

## Rev 2

Improvements in Rev 2 include:

* Added support for 3 x button signals from RGBtoHDMI board, to allow for keyboard integration.
  - **Note:** This requires a custom build for custom hotkeys to be mapped to the button signals - see https://github.com/solarmon/FF_OSD 

Top:
![Top](https://github.com/solarmon/FlashFloppy/blob/main/FF%20OSD%20Adapter%20-%20Rev%202/FF%20OSD%20Adapter%20-%20Rev%202%20-%20Top.png)

Bottom:
![Bottom](https://github.com/solarmon/FlashFloppy/blob/main/FF%20OSD%20Adapter%20-%20Rev%202/FF%20OSD%20Adapter%20-%20Rev%202%20-%20Bottom.png)

Schematics PDF: https://github.com/solarmon/FlashFloppy/blob/main/FF%20OSD%20Adapter%20-%20Rev%202/FF%20OSD%20Adapter%20-%20Rev%202.pdf

## FF OSD Firmware ##

In order to support keyboard integration for the RGBtoHDMI menu buttons , FF OSD needs to be built with support for it. I have forked off the FF OSD files and have provided the example config required to build it with RGBtoHDMI button support - see:

https://github.com/solarmon/FF_OSD
