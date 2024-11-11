# ITX-Llama Hardware Compatibility

## Graphics
| Family | Model       | Tested (y/n) | Notes                         |
| :----: | :---------: | :----------: | :---------------------------- |
| ATI    | Radeon 7500 | y            | Works natively in DOS / Win98 |
| ATI    | Radeon 9250 | y            | Works natively in DOS / Win98 |
| 3DFx   | Voodoo3     | y            | Works natively in DOS / Win98 |
| nVidia | TNT2        | y            | Works natively in DOS only    |

## Wavetable Options
| Module    | MIDI Type                       | Connector   | Notes                        |
| :----:    | :-----------------------------: | :---------: | :--------------------------- |
| X2GS      | GM/GS Wavetable                 | Wavetable   | Fits without issue           |
| X16GS     | GM/GS Wavetable                 | Wavetable   | Fits but overlaps Pi headers |
| OPL-3     | FM Synth                        | OPL Header  | Fits without issue           |
| Pi Zero 2 | MT-32 / Soundfont               | GPIO Header | Fits without issue           |
| Pi 4      | MT-32 / Soundfont / Nuked SC-55 | GPIO Header | Fits without issue           |