---
created: 2024-02-21 14:52:32Z
---


# Devices
- `lshw` : lists all hardware detected on your machine
## udev
Linux subsystem that supplies your machine with device events (dis-/connections)
### `udevadm`
- `udevadm info --name=/dev/sdb --attribute-walk`: walk through all udev devices and list attributes
- `udevadm monitor`
- `udevadm info`

## Storage Devices
- `fdisk -l` - All storage devices and their partitions
	- `parted -l` - similar
	- `sfdisk` - advanced
- `lshw -class disk` - can be filtered, [reference](https://access.redhat.com/solutions/1160343)
	- `-X` for GUI
### Block Devices
- `vmstat [delay [count]]` block/sector sizes
- `df` for block devices w/o transfer rates
- `lsblk` - All **block** storage devices
#### USB
- `lsusb`
	- `-t` show speeds of ports
	- `-v` verbose

### I/O Monitoring
- `iotop` Check [here](https://www.kernel.org/doc/html/latest/accounting/delay-accounting.html#usage) to enable delay accounting
- `iostat`
### File System
- `du` for folders & files


## PCI (Peripheral Component Interconnect)
- `lspci`

# X11 (X-Windows)
## Display
- `xrandr`: something about configuring screen size
- `xprop WMClass`  -  Then click on window to obtain its *window class*.
* `xwininfo`
* `xdpyinfo`
* `wmctrl`
* `xinput [list, (float, reattach <id>) <master>)]`

# Operating System
## System Logs
`journalctl`
`strace`

## Static Info
### Version
- `lsb_release` : Ubuntu version

