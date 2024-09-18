The init system is the first process that starts outside of the kernel, acting as the backend managing all other services
- Init Systems
	- `systemd`
	- `sysvinit`
	- `upstart`
- Other Service Management Tools
	- `inetd`
	- `xinetd`
---
# `systemd`
- Init system
- Centralized management of 
	- processes, daemons
	- services, mount points.
- Makes available to daemons
	- Unix domain sockets
	- D-Bus
## Concepts
### Unit
If marked as `enabled`, will try to start on boot.
## Utility Programs
- Facilitates creation / management of Linux containers
	- `systemd-nspawn`
	- `machinectl`
## Commands
- `systemctl` -- Returns list of all Units
	- `systemctl start UNIT`
	- `systemctl stop UNIT`
	- `systemctl restart UNIT`
	- `systemctl status UNIT`
- `journalctl -xn` -- Log messages of last `systemctl` command
---
# Other Daemons
Eventually started by `systemd`
### `journald`
### `logind`
### `networkd`
Handles configuration of network interfaces.
- statically assigned addresses
- bridging
- DHCP server
- `networkctl` -- review network links
New interfaces added as `/lib/systemd/network/newif.network`