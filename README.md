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

# Serial Commands

`help`
  Inputs: None
  Desc: Show help text

`read`
  Inputs: None
  Desc: Read Real Time Clock (RTC) and report to Serial
         date convention is day/month/year
         the command would be, "set 1 2 3 4 5 6 7"

`set [sec] [min] [hr] [wkDay] [moDay] [mo] [yr]`
  Inputs: int int int int int int int
  Desc: Sets the RTC module.
        For example, to set the RTC to 3:02:01 AM on Wednesday, June 5th, 2007,

`verify`
  Inputs: None
  Desc: Read RTC and report whether it looks like it has been set:
         RTC looks unset if it is the year 2000
         RTC looks set if it is any other year
