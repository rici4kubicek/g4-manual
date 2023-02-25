# NTP and PoE clock operation

Clocks support IPv4 and IPv6 protocols. You can disable individual protocols by setting parameter **n1**. The default clock setting allows both protocols at the same time (**n1: 0**).

For IPv4 mode, DHCPv4 is enabled by default (**n3: 1**).

IPv6 mode allows up to 4 different priority IP addresses in downward order:
* DHCPv6

* manually configured IP address (fix)

* auto-configuration (SLAAC / RA)

* local link address


By setting parameter **n10** you can disable DHCPv6 and / or auto-configuration (SLAAC) by settin parameter **n11**.

For IPv6 mode, DHCPv6 and auto-configuration (SLAAC) are enabled by default:

1. for DHCPv6 menu item **n10: 1**

2. for SLAAC menu item **n11: 1**


Calculation of Link Local Address:
fe80 :: 2 [2^nd^ octet MAC]: [3^rd^ octet MAC] ff: fe [4^th^ octet MAC]: [5^th^ octet MAC] [6^th^ octet MAC]


Example:

* MAC: 00: **16**:**91** : **12**:**34**:**56**

* IPv6: fe80 :: 2**16**: **91**ff: fe**12**: **3456**


## Unicast mode

The clock is synchronized to UTC (Universal Time Coordinated) from a NTP server (up to four IPv4 / IPv6 addresses for NTP server configurable) and must have assigned its own IPv4 / IPv6 address. The clock requests in defined intervals (adjustable in menu item **n9**) the actual time from the NTP server. If the server is not available, the clock tries to contact the other defined servers in cyclic way until the valid response from the NTP server is received.

This operation mode supports the monitoring and configuration of the movement via the network connection by means of the web interface (**n15: 1**), SNMP (**n14: 1**) or the MOBA-NMS software tool. For supervision and configuration with MOBA-NMS, the clock's IPv4 / IPv6 address can be used or the multicast group (**n7**) address having last octet cleared to zero (presuming the multicast is not disabled - **n13: 1**).

It is necessary to set appropriate time-zone for correct displaying of local time and date (see chapter 3 for details).

**Default network parameters:**

%tabulka


### Network parameters assigned by DHCP

IP clock mode must be set to IPv4 mode (**n1: 0/1**). The NEt menu item **n3** must be set to value **1**. Network parameters are automatically obtained from a DHCPv4 server.

The following DHCP options will be evaluated automatically:
[50]&nbsp;&nbsp;&nbsp;&nbsp;IP address

[3]&nbsp;&nbsp;&nbsp;&nbsp;gateway address

[1]&nbsp;&nbsp;&nbsp;&nbsp;subnet mask

[42]&nbsp;&nbsp;&nbsp;&nbsp;list of up to four NTP server addresses / time zone address (usually the same as the NTP server address)

[6]&nbsp;&nbsp;&nbsp;&nbsp;DNS servers

[26]&nbsp;&nbsp;&nbsp;&nbsp;MTU

[60]&nbsp;&nbsp;&nbsp;&nbsp;vendor Class ID

[43] or [223]&nbsp;&nbsp;&nbsp;&nbsp;additional options (refer to document BE-800793)


The network administrator must configure the DHCPv4 options accordingly. Assigned parameters can be checked in the submenu of items **n4-n6**.


### Manual setting through setup menu

The NEt menu parameter **n3** must be set to value **0** (DHCPv4 set to disabled).

* Enter the item **n4** submenu for setting the clock's IP address.

* Enter the item **n5** submenu for setting the subnet mask.

* Enter the item **n6** submenu for setting default gateway.

* Enter the item **n7** submenu for setting multicast group address.

* Enter the item **n8** submenu for setting unicast NTP server address.


### Setting network parameters over DHCPv6

Ip clock mode must be set to IPv6 mode (**n1: 0/2**). The NEt menu item **n11** must be set to value *1*. The network parameters are automatically retrieved from the DHCPv6 server.

The following DHCPv6 options can be processed:
[3]&nbsp;&nbsp;&nbsp;&nbsp;non-temporary addresses

[16]&nbsp;&nbsp;&nbsp;&nbsp;vendor class

[17]&nbsp;&nbsp;&nbsp;&nbsp;vendor options

[23]&nbsp;&nbsp;&nbsp;&nbsp;DNS servers

[24]&nbsp;&nbsp;&nbsp;&nbsp;DNS domains

[25]&nbsp;&nbsp;&nbsp;&nbsp;identidy association for prefix delegation

[31]&nbsp;&nbsp;&nbsp;&nbsp;SNTP

The network administrator must set the DHCPv6 options accordingly.


### Setting network parameters over autoconfiguration (SLAAC)

IP clock mode must be set to IPv6 mode (**n1: 0/2**). The NEt menu item **n10** must be set to value **1**. The network parameters are automatically retrieved from the DHCPv6 server.

The following SLAAC options can be processed:
[3]&nbsp;&nbsp;&nbsp;&nbsp;prefix info

[5]&nbsp;&nbsp;&nbsp;&nbsp;MTU

[24]&nbsp;&nbsp;&nbsp;&nbsp;route info

[25]&nbsp;&nbsp;&nbsp;&nbsp;RDNSS

The network administrator must set the SLAAC options accordingly.


### SNMP

The clock supports SNMP version 2c notifications and parameter reading and setting by means of SNMP GET and SET commands. This allows integrating the clock to a network management system. The digital clock (SNMP agent) can send alarm and alive notification to a SNMP manager. The IP address of the SNMP managem can be provided to the clock by DHCP, web interface, SNMP or the MOBA-NMS. The structure of supported parameters is defined in a MIB file (refer to document BE-800793 for details). In addition the clock supports the 'system' node parameters defined by MIB-2 (RFC-1213).

Alarm notifications are asynchronous messages and are used to inform the manager about the appereance / disappereance of alarm.

Alive notifications are sent out periodically to report availability and state of the clock. The interval time can be configured.


**SNMP community strings**
 


## Multicast mode

The clock is synchronized to UTC (Universal Time Coordinated) from a NTP server. The clock receives NTP multicast packets transmitted by the NTP server in a specified time cycle. This type of synchronization requires no clock's own IP address and is therefore suitable for an easy commissioning of the large systems of Slave clocks. Further this mode supports monitoring and parameter configuration by means of MOBA-NMS service.

For supervision and configuration with MOBA-NMS, the multicast group address can be used or the multicast group address having last octet cleared to zero.

The multicast operating mode signifies only a minimum amoiunt of configuration work for a network administrator.

It is necessary to set appropriate time-zone for correct displaying of local time and date (see chapter 3 for details).


**Default network parameters**


The NEt menu item **n2** must be set to value **1**.





