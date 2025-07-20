# FPV Signal Cleaner

<div align="center">

![FPV Signal Cleaner](media/FrontHeadOn.png)

**Clean AV Buffer Module for Fat Shark Goggles + PowerPlay DVR**

[![Demo Video](https://img.shields.io/badge/YouTube-Demo%20Video-red?style=for-the-badge&logo=youtube)](https://youtu.be/c0BqS2wPbJs?si=y3qnMJqaLPZePITY)
[![OnShape CAD](https://img.shields.io/badge/OnShape-CAD%20Model-blue?style=for-the-badge&logo=onshape)](https://cad.onshape.com/documents/2e6892c1f7077560f1e7db3c/w/84a265bc11fc2bf27c14fb24/e/b1e7d4b621d2da3bc5834969)

</div>

## 📖 Overview

The FPV Signal Cleaner is a compact inline module that cleans up the composite video signal from Fat Shark FPV goggles before it reaches a DVR (like the ImmersionRC PowerPlay). While the internal video feed remains clean, the AV output suffers from amplified noise, distortion, and flashes, especially during RF signal fluctuations.

This module uses a **THS7314 video buffer chip**, low-pass filtering, and impedance matching to condition the video signal while passing audio and power through untouched. Power is taken from the PowerPlay's 7.4–8.4V barrel output and regulated to 3.3V using a buck converter to power the buffer circuit.

Everything is mounted on perfboard and housed in a small enclosure that plugs directly into the side of the PowerPlay — like a dongle.

## 🎯 Key Features

- ✅ **Cleans and buffers composite video** signal
- ✅ **Passes audio through untouched** (or disconnects if not needed)
- ✅ **Regulates 3.3V** from PowerPlay to run the chip
- ✅ **Dual-connector dongle design** - plugs into both AV and power ports on PowerPlay
- ✅ **Compact enclosure** - 3D printed case for professional appearance
- ✅ **Impedance matching** - 75Ω resistor for proper video signal integrity

## 📋 Parts List

### 🔧 Core Components
| Qty | Item | Description | Approx. Cost |
|-----|------|-------------|--------------|
| 1 | THS7314D | 3-channel video buffer (SOIC-8) – Texas Instruments | $0.75 |
| 1 | SOIC-8 to DIP adapter | With header pins for breadboard/perfboard use | $2.88 |

### 🔋 Power Components
| Qty | Item | Description | Approx. Cost |
|-----|------|-------------|--------------|
| 1 | MP1584 buck converter module | Adjustable 3.3V regulator (input: 7.4–8.4V) | $2.50 |

### 🎥 Video Path Components
| Qty | Value | Description | Approx. Cost |
|-----|-------|-------------|--------------|
| 1 | 220nF | DC blocking cap (ceramic or film) | $0.41 |
| 3 | 75Ω (1%) | Input + output matching resistors | $0.12 each |
| 1 | 470pF | Output low-pass filter cap (to GND) | $0.27 |

### ⚡ Power Filtering
| Qty | Value | Description | Approx. Cost |
|-----|-------|-------------|--------------|
| 1 | 0.1µF ceramic | THS7314 bypass cap (near VCC) | $0.27 |
| 1 | 10µF electrolytic | Bulk cap on 3.3V rail | $0.50 |

### 🔌 Connectors
| Qty | Item | Description | Approx. Cost |
|-----|------|-------------|--------------|
| 1 | TRRS 3.5mm female jack | AV in from goggles | $0.50 |
| 1 | TRRS 3.5mm male plug | AV out to PowerPlay | $0.50 |
| 1 | 5.5x2.5mm barrel female jack | Power to goggles | $1.00 |
| 1 | 5.5x2.5mm barrel male plug | Power from PowerPlay | $0.50 |

### 🧱 Optional Materials
| Qty | Item | Use | Approx. Cost |
|-----|------|-----|--------------|
| 1 | 30x70mm perfboard (cut to 30x43mm) | Mount components | $2.00 |
| 1 | 3D-printed enclosure | Enclose the module | $5.00 |
| 1 | Heat shrink / tape / glue | Wire insulation and securing parts | $3.00 |

**Total Estimated Cost: ~$20-25 USD**

## 🔌 Pinout Information

### TRRS AV Composite Pinout (sleeve to tip):
- **Sleeve**: Ground
- **Ring 1**: Video  
- **Ring 2**: AudR
- **Tip**: AudL

**Note**: We only care about the sleeve (Ground) and 3rd segment (Video) and can ignore the tip and 2nd segment (audio).

## 🛠️ Build Instructions

### 1. Circuit Assembly

1. **Mount the THS7314** on the SOIC-8 to DIP adapter
2. **Install the buck converter** and adjust to 3.3V output
3. **Add power filtering capacitors**:
   - 0.1µF ceramic near THS7314 VCC pin
   - 10µF electrolytic on 3.3V rail
4. **Install video path components**:
   - 220nF DC blocking capacitor on video input
   - 75Ω resistors for impedance matching (input, output, and THS7314 output)
   - 470pF low-pass filter capacitor on video output
5. **Connect all grounds** together
6. **Wire the connectors** according to the pinout

### 2. Enclosure Assembly

1. **Print the enclosure parts** from the OnShape model
2. **Mount the circuit board** inside the base
3. **Install the TRRS jacks** and barrel connectors
4. **Secure all components** with glue or mounting hardware
5. **Attach the door** to complete the enclosure

### 3. Testing

1. **Connect to PowerPlay** using the barrel and TRRS plugs
2. **Connect goggles** to the module's input
3. **Power on** and verify clean video output
4. **Test with various signal conditions** to ensure noise reduction

## 📁 Project Files

### 🎨 3D Models & Enclosure
- **OnShape CAD Model**: [View/Download](https://cad.onshape.com/documents/2e6892c1f7077560f1e7db3c/w/84a265bc11fc2bf27c14fb24/e/b1e7d4b621d2da3bc5834969)
- **STL Files**: Available in `enclosure/PowerPlayDongle/` directory

### 🔌 Circuit Design
- **Falstad Circuit Simulator**: Load `hardware/AVCleanerDiagram-falstad.txt` to view the interactive circuit
- **Circuit Screenshot**: `hardware/FalstadScreenshot.png`

### 📸 Build Photos
- **Front View**: `media/FrontHeadOn.png`
- **Top Close-up**: `media/TopCloseUp.png`
- **Bottom Close-up**: `media/BottomCloseUp.png`
- **Internal Views**: 
  - `media/InternalsFront.png`
  - `media/InternalsPerfboard.png`
  - `media/InternalsPerfboardTop.png`
  - `media/InternalsWired.png`
  - `media/InternalsWiredAlt.png`
- **With Goggles**: `media/WithGoggles.png`

## 🎥 Demo Video

[![Demo Video](https://img.youtube.com/vi/c0BqS2wPbJs/0.jpg)](https://youtu.be/c0BqS2wPbJs?si=y3qnMJqaLPZePITY)

Watch the full demonstration: [YouTube Demo](https://youtu.be/c0BqS2wPbJs?si=y3qnMJqaLPZePITY)

## 🔧 Technical Details

### Circuit Operation
The module uses a **THS7314D** 3-channel video buffer IC to:
- Buffer the incoming video signal
- Provide proper impedance matching (75Ω)
- Filter out high-frequency noise
- Maintain signal integrity

### Power Management
- **Input**: 7.4-8.4V from PowerPlay barrel connector
- **Regulation**: MP1584 buck converter to 3.3V
- **Filtering**: Multiple capacitors for clean power delivery

### Signal Path
1. **Video Input** → DC blocking cap → 75Ω resistor → THS7314 buffer
2. **Buffer Output** → 75Ω resistor → 470pF low-pass filter → Output
3. **Audio** → Passed through unchanged
4. **Power** → Regulated and filtered for IC operation

## 🤝 Contributing

This is an open-source project! Feel free to:
- Report issues or bugs
- Suggest improvements
- Submit pull requests
- Share your build photos

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Fat Shark** for the excellent FPV goggles
- **ImmersionRC** for the PowerPlay DVR
- **Texas Instruments** for the THS7314 video buffer IC
- The FPV community for inspiration and feedback

---

<div align="center">

**Built with ❤️ for the FPV community**

*Clean signals, smooth flights!*

</div>
