# ITX-Llama FAQs

**Q: What do I need in addition to the ITX-Llama board?**
: A: You'll need:

  - The Vortex86EX system-on-module (SOM).
  - An ATX-compatible Power Supply Unit (PSU).
  - An AGP graphics card
  - A microSD card, USB flash drive or SATA SSD or hard drive

**Q: What's the performance of this system like?**
: A: The Vortex86EX CPU can be clocked from 60-500 MHz, and has L1 and L2 caches that can be turned on and off.

  - At 500 MHz with caches enabled, the CPU is roughly comparable in speed to an Intel Pentium 233 MMX.
  - At 60 MHz with caches disabled, it's performing similarly to a 386.

**Q: Can I use an AGP riser to mount AGP graphics cards into modern compact ITX cases?**
: A: At this time, it is recommended that risers and 90-degree adapters be avoided until further testing has been done. AGP has very strict timing tolerances that likely means most adapters won't work reliably. Plan to use low-profile AGP cards if small cases are desired.

**Q: Does the ITX-Llama support adding a PicoGUS (or other ISA peripherals)?**
: A: Unfortunately no. The Vortex86EX has a stripped-down ISA interface with only a single DMA channel, and that is being used by the Crystal sound chip.

**Q: Can I connect an Optical drive?**
: A: Yes. You can either use a SATA Optical drive connected to the onboard SATA port or an IDE to SATA adapter paired with an IDE Optical drive. IDE Optical drives typically have audio output which can be connected to the onboard Crystal sound card.

**Q: What kind of PSU should I use?**
: A: Any kind will work! The board and CPU uses very little power, only a few watts. The AGP card can draw a little more, but the overall system power consumption will still be comfortably lower than what every modern PSU can deliver. PicoPSUs can be used for saving space.

**Q: Should the Vortex86EX SOM be actively cooled?**
: A: It probably won't have to be, if you have some air flow through the case. If you want to overclock the CPU or have limited air flow, a fan can be mounted above the SOM using the 4 holes around the SOM pin headers on the motherboard. There are also 3 independently controllable (through the BIOS settings menu) fan pin headers on the board. These follow the standard 4-pin PWM fan specification, and can be set to provide 5V or 12V by jumper.

**Q: What kind of ethernet controller is used?**
: A: There's a built-in RDC R6040 Fast Ethernet (10/100Mbit) controller on the Vortex86EX. This controller has drivers both for DOS and Windows 98.

**Q: What kind of USB standard is supported?**
: A: The two connectors below the Ethernet port are USB 2.0. With a flash drive plugged in, they can either be used as fixed disks in DOS and Windows (appearing to the operating systems as regular hard drives) or as removable storage. This is configured in the BIOS setting menu.
Additionally, there are two USB HID-only ports you can use to connect modern USB keyboards and mice. The HID protocol is translated into PS/2 using an RP2040 chip on the motherboard, and the connected devices appear as regular PS/2 input devices to the operating system.

**Q: What kind of serial communication does the board offer?**
: A: There are two high-speed UARTs on the board. The first (COM1) uses a standard DE-9M connector on the back side, has a proper high-voltage (+/- 12V) RS-232 transceiver for reliable signalling and is good for at least 115200 baud speeds. It has all the 8 signal lines available. The other UART (COM2) only has data lines (RX/TX), uses TTL logic-level (5V) and is connected to the ESP8266 module and an internal pin header. This can be run at anywhere up to 3 Mbps.

**Q: What's the deal with the ESP8266 module?**
: A: This module offers an emulated Hayes-compatible modem (on COM2), and talks to your WiFi network. This means you can connect to BBSes on telnet (there are still many out there!) the old skool way, or even connect to the internet on Windows 98 using dial-up networking!

**Q: How do I connect a keyboard and mouse?**
: A: You can choose whether to use real PS/2 keyboards/mice or modern USB variants. Configured by jumpers.

**Q: What's the sound card on this board?**
: A: It's the Crystal Semi / Cirrus Logic CS4237B - which is a Sound Blaster Pro 2 / Windows Sound System compatible chip, working great in both DOS and Windows. It has a very good built-in Adlib/OPL3 FM synth as well, a powerful mixer for various input sources, and can output both analog line-level audio and digital audio (S/PDIF) using a TOSLink optical transmitter connector.

**Q: What's the point of the internal OPL3 header receptacle?**
: A: While the CS4237B's emulated OPL3 synth is quite respectable, it's not a perfect 1:1 implementation of the Yamaha YMF262 (OPL3). This is where the OPL3 module comes into play. By plugging in such a module, you get the actual authentic OPL3 hardware using real Yamaha chips. Sound-wise, it's a subtle difference, but it's there.

**Q: What are my options for audio input/output?**
: A: For output you have analog (line-level) and digital (S/PDIF) audio. Inputs are microphone (with a built-in pre-amp), line-in and analog CD audio.
Line-in can be set (using jumpers) to either the external 3.5mm jack (for external MIDI synthesizers, for example), or internal - from a wavetable plugin card or a software-based MT-32 or MIDI synth on a Raspberry Pi.

**Q: What kind of internal synthesizers can I use?**
: A: There are three internal synth connectors on the board. The first is the 26-pin wavetable connector. Here you can plug in MIDI wavetable cards such as the X2, X2GS, X16, X16GS, etc. from Serdashop - _these are modern cards using the Dream chipset and uses soundfonts to replicate various MIDI synthesizers._
You've also got two 40-pin connectors for plugging in a Raspberry Pi. Either use the male header with a 40-pin female-female ribbon cable to connect a standard Pi 3 or 4, or you can plug a Pi Zero 2's pins directly into the female connector. Since the Raspberry Pis are full computers in their own sense, they can run all kinds of software synthesizers and output digital I2S audio to the motherboard. There's a PCM5102 DAC on the board to convert the audio to analog, and then feed it into the Crystal sound chip. The easiest way to get a Pi up and running as a synth is to use the mt32-pi software which requires minimal effort. It'll do MT-32 using the munt emulator, and General MIDI using the fluidsynth application with soundfonts. If you're adventurous and have a Pi 4, you can also run the SC-55 emulator nuked-sc55 on a regular Debian installation, for an extremely accurate Roland SC-55 sound.

**Q: What about the game port connector?**
: A: The game port connector offers joystick/gamepad support through the Crystal sound card. In addition, you have MIDI input and output, so you can connect an external synth (like the Roland MT-32 or SC-55) using a standard gameport-to-MIDI breakout cable.

**Q: What's the AGP compatibility of the ITX-Llama?**
: A: The mechanical/electrical connector on the board is 3.3V-keyed. That means AGP cards with the 3.3V-notch (towards the VGA connector-side of the card) as well as "universal" cards with two notches will fit and run. 1.5V-keyed cards with only the notch towards the opposite side of the VGA connector will neither fit nor be compatible with the motherboard's 3.3V-signal level.
From a protocol perspective, this is AGP 1x, with some caveats.

- > A quite technical summary; there is no native AGP support on the Vortex86EX, only PCI Express x1 (gen 1). This is converted to PCI at 66 MHz by an onboard PI7C9X118 chip. Since AGP is really only PCI running at a higher clock frequency (66 vs 33 MHz), this is fine. However, AGP supports additional features not found on PCI, like split transactions, sideband addressing and GART. What this means is that AGP cards where the Windows driver requires one or more of these AGP-only features will not work properly. In practice, most older cards should work just fine and are probably a better fit for the CPU's speed as well.
Of note is the Radeon 9200 / 9250, as well as the Voodoo3 - these have been tested extensively and found to be a very good match.

**Q: Does the board have front panel connectors?**
: A: Yes, power button, reset button, power LED and SD card activity LED.

**Q: Does the board have a PC speaker?**
: A: Yes, an internal one (with two volume settings, configured by jumper), and a pin header for connecting an external speaker.

**Q: Which operating systems are supported?**
: A: MS-DOS, FreeDOS and early Windows (3.1, 95, 98).

**Q: Which storage devices can be booted from and run an operating system?**
: A: All of them; microSD, USB and SATA.

**Q: My question isn't listed here, where can I learn more?**
: A: Try asking in the ITX-Llama thread on the [Vogons forum][vogons-thread], or join the [Discord server][discord-server].

[vogons-thread]: https://www.vogons.org/viewtopic.php?t=93480
[discord-server]: https://discord.gg/YN3XkycAXG