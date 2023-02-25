# Local time calculation

## Basic setting - control according to source of synchronization

This setting is suitable for digital clock synchronized by a DCF receiver or controlleed by a master clock as slave clock in a time distribution system. The internal time zone table is not used.


## Calculation using MOBALine zime zones

This setting is suitable for digital clock controlled by a master clock as a MOBALine slave clock in a time distribution system with possibility to display different MOBALine time zones.


## Calculation using time zone server MOBATIME

This setting is suitable for NTP, PoE, WiFi and WiFi5 digital clocks controlled by a MOBATIME NTP servers which supports the time zone server functionality.


## Calculation using time zone entries preconfigured by MOBA-NMS software

This setting is suitable for NTP, PoE, WiFi and WiFi5 digital clocks, where several user defined time zone entries should be used. The time zone entries are preconfigured by means of the MOBA-NMS software.


## Calculation according to internal time zone table

This setting is suitable for autonomous digital clock or in cases where the displayed time is needed in another time zone than provided by the synchronization source. Displayed time and date calculation is based on the internal time zone table or on the user-specific time zone parameters.
See chapter 9 Time zone table v11.








