# ITX Llama MIDI Options

The ITX Llama is equipped with several distinct options for MIDI playback, including genuine OPL-3 via an add-in module, on-chip emulated OPL-3 provided by the Crystal sound chip, Wavetable header for general MIDI add-on modules and a pair of headers for attaching a Raspberry Pi running [mt32-pi][mt32-pi] for authentic Roland MT-32 support. 

Below is a breakdown of each option and several add-ons that are compatible.

## OPL-3 FM Synthesis Support

1. Out of the box, the Crystal CS4237B sound chip can emulate OPL-3 through its Crystal FM synthesis engine. This is a close approximation to a genuine Yamaha OPL-3 for most titles but has been known to fall short in certain cases. 
1. The ITX Llama offers an OPL-3 header which accepts a [custom OPL-3 board][opl3module] containing an old-stock Yamaha YMF262-M FM synth chip. This will provide a geniune Yamaha OPL-3 sound for games utilizing FM Synthesis. 
  * <p><img src=../images/opl3module.jpg title="OPL3 Module" width=35%></p>

## Roland MT-32 Support

1. A Raspberry Pi Zero 2 is capabilty of emulating a Roland MT-32 using the excellent Munt emulator. To facilitate this as a drop-in feature, the [mt32-pi][mt32-pi] project add this functionality to a simple Pi Zero 2 and installed onto the ITX Llama for direct audio support.
    * Pros: 
        * provides a near perfect emulation of the Roland MT-32 / CM-32L
        * audio is routed through an onboard DAC to the Crystal sound chip via i2c preventing the need for additional hardware besides the Pi Zero 2 itself and an SD card.
    * Additional features:
        * mt32-pi supports General MIDI using the FluidSynth engine and user-supplied sound fonts. ITX Llama users could techincally employ *just* the Pi Zero 2 with mt32-pi in addition to the OPL-3 module to cover nearly all bases of MIDI in early DOS games.
    * Installation:
    * <p><img src=../images/pi-zero2-alignment.jpg title="Pi Zero 2 Alignment" width=50%></p>

2. A Raspberry Pi 4 can also be attached in lieu of the Pi Zero 2. This is a much more advanced option but opens the possibility of running a full OS with Munt, FluidSynth and a modified version of the nuked-SC-55 emulator for geniune Roland SC-55 sound support.
    * An IDE cable affixed to the pins on board below and to the Raspberry Pi 4 is necessary to use this feature. 
    * At this time, system setup for the Pi 4's OS is up to the user.
    * Pin Header: (_below the female Pi Zero 2 header_)
    * <p><img src=../images/som-alignment-1.jpg title="Raspberry Pi 4 header pins visible" width=50%></p>

## Wavetable MIDI Support

1. The ITX Llama contains a Wavetable compatible header as well. This can be configured with a variety of Wavetable Synth modules to provide General MIDI support through the Crystal sound chip.
    * This header can be enabled via Jumpers: J25, J26, J27
    * <p><img src=../images/pi-wt.jpg title="PI/WT configuration" width=50%></p>
        * For using a Raspberry Pi (Zero2, 3 or 4) for converting MIDI to analog audio, place the three jumpers to the rightmost position ("PI").  
        * For using a wavetable board, place the jumpers to the leftmost position ("WT").
      
## Wavetable Options

1. **Dreamblaster X2 SE / X2GS SE / X2TE**
    * **Status:** _Tested to fit_
    * General Specs:
        * 81 voice polyphony
        * 64MB of flash memory for samples
        * "GS" modules include a read-only licensed Roland GS Sample set
    * Links:
        * [X2 SE][X2SE] - General Purpose MIDI Synth with customizable samples
        * [X2GS SE][X2GS-SE] - General Purpose MIDI Synth with customizable samples and an additional licensed Roland SC-55 sample set
        * [X2 TE][X2TE] - "Tiny Edition" of the X2 SE

1. **Dreamblaster X16 / X16GS**
    * **Status:** _Will only fit without a Pi Zero 2 installed_
    * General Specs:
        * 256 voice polyphony
        * 1024MB of flash memory for sample sets (divided into 7 banks)
        * 8MB SDRAM for very high quality DSP effects
        * "GS" modules include a read-only licensed Roland GS Sample set
    * Links:
        * [X16][X16] - High-End General Purpose MIDI Synth with customizable samples
        * [X16GS][X16GS] - High-End General Purpose MIDI Synth with customizable samples and an additional licensed Roland SC-55 sample set

[X2SE]: https://www.serdashop.com/X2-SE
[X2GS-SE]: https://www.serdashop.com/X2GS-SE
[X2TE]: https://www.serdashop.com/X2TE
[X16]: https://www.serdashop.com/DreamBlaster-X16
[X16GS]: https://www.serdashop.com/DreamBlaster-X16GS
[mt32-pi]: https://github.com/dwhinham/mt32-pi
[opl3module]: https://retrodreams.ca/products/llama-opl3-module