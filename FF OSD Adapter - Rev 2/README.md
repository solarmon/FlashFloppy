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

The only change is to add the button code to `src/default_config.c`:

```c
#if 1
    /* An example for RGBtoHDMI momentary buttons */
    .user_pin_opendrain = U(2) | U(1) | U(0),	/* Set these pins as open drain */
    .user_pin_pushpull  = 0,					/* No buttons as pushpull */
	.user_pin_high		= U(2) | U(1) | U(0),	/* Initialise then as HIGH */

    .hotkey = {
        [F(1)]  = { .str = "RGBtoHDMI\0Button 1",	/* Test OSD text */
                    .pin_mod  = U(0), 
					.flags = HKF_momentary, },
        [F(2)]  = { .str = "RGBtoHDMI\0Button 2",	/* Test OSD text */
                    .pin_mod  = U(1), 
					.flags = HKF_momentary, },
		[F(3)]  = { .str = "RGBtoHDMI\0Button 3",	/* Test OSD text */
                    .pin_mod  = U(2), 
					.flags = HKF_momentary, },
    }
#endif
```
So you can take the original and latest source code from https://github.com/keirf/flashfloppy-osd and update `src/default_config.c` to include this three button mapping, and build the Blue Pill firmware yourself (see https://github.com/keirf/flashfloppy-osd/wiki/Building-From-Source)

## Installation and Connectivity

Here is an example summary installation connectivity with a supported RGBtoHDMI board and Gotek.

![Bottom](https://github.com/solarmon/FlashFloppy/blob/main/FF%20OSD%20Adapter%20-%20Rev%202/RGBtoHDMI%20FF%20OSD%20Adapter%20Rev%202.png)

For dual output of FF OSD on Amiga RGB and RGBtoHDMI HDMI, use the FF OSD menu to set the option **Display Enable** to **A15** and to set **A15** to **Active Low**.
