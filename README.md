# Lesker275_logger

https://github.com/b-d-doyle/Lesker275_logger

Arduino script to read pressure from a Lesker 275 convectron pressure gauge and store those pressures to an SD card

Lesker275_logger v0.0.2 11/21/2025

Purpose:

Store a time-marked log of pressure, as measured from the analog output of the convectron on GRIT, onto a micro SD card.
v0.0.2 updated for an OLED, and ADS1115. Must now be put on something like a mega for memory reasons. Sorry =)


Components:

- Arduino Mega or similar (I'm using too much memory for Uno)
- Lesker 275 convectron pressure gauge
- DS3231 RTC module
- CR2032 holder (usually comes with RTC module)
- uSD reader/writer module
- OLED display (128x64) 
- Status LEDS, 1 each of Red, Green, and Amber (Yellow)
- Resistive voltage divider. Should either be precision matched or tunable with a pot
- Various switches and basic components

# Usage Instructions
More details coming soon. 2/24/26

## Controls
**Back switch, power**: turns on/off the logger without interrupting Lesker 275 power

**Front switch, record**: toggles whether the logger is recording pressures to micro SD

**Front knob, tune**: Might not be present on every implementation! Physically tunes the read input value. Turn until the read pressure matches the pressure displayed on the vacuum gauge

## Status LEDs:
Green:
- Ready to record pressures

Amber:
- Problem detected
- Some problems inhibit recording, others do not

Red:
- Actively saving pressures to micro SD card


# Serial Commands
| Serial Settings | Config |
|---|---|
| Baud | 9600 |
| Data Bits | 8 |
| Parity | No |
| Stop Bits | 1 |

`help`\
&emsp;Inputs: None\
&emsp;Desc: Show help text

`read`\
&emsp;Inputs: None\
&emsp;Desc: Read Real Time Clock (RTC) and report to Serial\
&emsp;&emsp;       date convention is day/month/year

`set [sec] [min] [hr] [wkDay] [moDay] [mo] [yr]`\
&emsp;Inputs: int int int int int int int\
&emsp;Desc: Sets the RTC module.\
&emsp;&emsp;For example, to set the RTC to 3:02:01 AM on Wednesday, June 5th, 2007,\
&emsp;&emsp;the command would be, "set 1 2 3 4 5 6 7"

`verify`\
&emsp;Inputs: None\
&emsp;Desc: Read RTC and report whether it looks like it has been set:\
&emsp;&emsp;RTC looks unset if it is the year 2000\
&emsp;&emsp;RTC looks set if it is any other year
