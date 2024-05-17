## Linux
---
#### IPTraf currently supports the following network interface types and names.

## lo
 - The loopback interface. Every machine has one, and has an IP address of 127.0.0.1. lo is also indicated if data is detected on the dummyn interface(s).

## ethn
 - An Ethernet interface. n starts from 0. Therefore, eth0 refers to the first Ethernet interface, eth1 to the second, and so on. Most machines only have one.

## fddin
 - An FDDI interface. n starts from 0.

## trn
 - A Token Ring interface, where n starts from 0.

## pppn
 - A PPP interface. n starts from 0.

## slin
 - A SLIP interface. n starts from 0.

## ipppn
 - A synchronous PPP interface using ISDN. n starts from 0.

## isdnn
 - ISDN interfaces can be given arbitrary names, but for them to work with IPTraf, they must be named isdnn. IPTraf supports synchronous PPP (the ipppn interfaces above), raw IP, and Cisco-HDLC encapsulation.

## plipn
 - PLIP interfaces. These are point-to-point IP connections using the PC parallel port.

## ipsecn
 - This refers to Free s/WAN (and possibly other) logical VPN interfaces.

## sbnin
 - SBNI long-range modem interfaces

## dvbn, sm200, sm300
 - DVB satellite-receive interfaces

## wlann, wvlann
 - Wireless LAN interfaces

## hdlcn
 - Frame Relay base (FRAD) interfaces (non-PVC)

## pvcn
 - Frame Relay Permanent Virtual Circuit interfaces

#### Your system's network interfaces must be named according to the schemes specified above.