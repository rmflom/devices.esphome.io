---
title: LSC Smart Connect Smart Ceiling Skyscape Light
date-published: 2026-10-05
type: light
standard: eu
board: bk72xx
difficulty: 4
---

## Product Description

This is the LSC Smart Connect **Smart Ceiling Skyscape Light**, sold by Action. The packaging specifies:

- 20 W
- 1600 lumen
- 220-240 V AC, 50/60 Hz
- 3000-6500 K tunable white
- RGBIC
- 2.4 GHz Wi-Fi
- Four advertised Skyscape modes

The tested hardware revision contains a **BK7238** Wi-Fi module connected to a separate Tuya MCU over UART. The module is marked `CBU`, even though the detected SoC is BK7238. Use the Tuya T1 BK7238 board definition shown below rather than the generic BK7238 layout.

Hardware revisions may differ, so verify the SoC before flashing.

## UART Pinout

| BK7238 pin | Function |
| --- | --- |
| P10 | RX from Tuya MCU |
| P11 | TX to Tuya MCU |

The UART runs at 9600 baud.

## Tuya Datapoints

| DP | Type | Function |
| --- | --- | --- |
| 20 | BOOL | Master power |
| 21 | ENUM | Operating mode: `0` effect, `2` white/CCT, `3` RGB |
| 22 | VALUE | Brightness, 10-1000 |
| 23 | VALUE | Colour temperature, 0-1000 |
| 24 | STRING | RGB colour, HSV `HHHHSSSSVVVV` |
| 26 | VALUE | Off timer in seconds |
| 54 | BOOL | RGB output enable |
| 63 | BOOL | White output enable |
| 64 | RAW | Built-in effect selector |

## Built-in Effects

| Effect | DP64 |
| --- | --- |
| Tricolor | `00:11` |
| RGB Cycle High | `00:12` |
| RGB Cycle Low | `00:14` |
| Color Shift | `00:15` |
| Sunrise | `00:01` |
| Sunset | `00:04` |
| Cloudy Blue Sky | `00:03` |
| Afterglow | `00:05` |

## Flashing

Serial flashing requires disassembly and soldering access to the BK7238 module. Make a full flash backup before replacing the stock firmware. The module shares its UART with the Tuya MCU, so isolate the UART lines if the secondary MCU interferes with flashing.

## Configuration

```yaml file=config.yaml
```
