# ITX-Llama Project

The ITX-Llama is a modern recreation of the best that late DOS/early Windows 98 computing had to offer, now reimagined into an ITX form-factor! For more information, visit the [Vogons thread][vogons-thread].

## Documentation Contents
- [User's Guide](user-guide.md)
- [FAQ](faq.md)
- [Hardware Compatibility](compatibility-hw.md)

<p>
  <img src=images/overview.jpg title="ITX-Llama w/Vortex86EX SoM" width=50%>
</p>

## Specs
- **CPU:** Designed specifically for the Vortex86EX System on Module:
    - High performance, 32bit 486/Pentium equivalent CPU
        - Selectable clock from 60MHz to 500MHz
        - 16KB WT L1 cache
        - 128BK WT/WB L2 Cache
        - [...more information](https://www.vortex86.com/products/Vortex86EX)
- **RAM:** 128MB DDR3
- **Sound:** Crystal Audio CS4237B
    - Sound Blaster 16 emulation / General MIDI / OPL-3 Synth support

## Ports and Expansion
- Keyboard/Mouse: (selectable)
    - 2x USB emulated peripheral interface ports
        - Optional: An onboard Raspberry Pi Pico emulates PS/2 keyboard/mouse 
        - Default: Dedicated onboard PS/2 keyboard/mouse ports accept legacy devices
    - PS/2 Keyboard and Mouse ports
- Audio:
    - Gameport/MPU-401 Interface port
    - S/PDIF digital output port
    - Line-In / Line-Out / Mic-In ports
    - Internal header for optional genuine Yamaha OPL-3 
    - Internal header for Wavetable MIDI cards
    - Internal header for a Raspberry Pi Zero 2 to emulate Roland MT-32 [mt32pi][mt32-pi]
- Storage / Peripherals:
    - 2x USB 2.0 Host ports
    - SD card (on IDE Primary)
    - SATA 1.5Gbps Port (on IDE Secondary)
- Network / Modem:
    - Onboard 10/100 NIC (realtek with win98 driver support)
    - Optional E
- Graphics:
    - Universal AGP 1x slot in "PCI Mode" running at 66MHz

[vogons-thread]: https://www.vogons.org/viewtopic.php?t=93480
[mt32-pi]: https://github.com/dwhinham/mt32-pi