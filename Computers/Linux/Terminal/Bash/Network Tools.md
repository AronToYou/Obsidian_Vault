---
created: 2024-02-21 14:52:53Z
---
# Sort out
- TLS
- SSL
- TCP / UDP
- DNS
- DHCP

# DNS (Domain Name Resolution)
- `getent ahostsv4 DOMAINNAME`
Resolves the provided `DOMAINNAME` into it's IPv4 address via the NSS (Name Service Switch) utility.

### Network
 * `nethogs`
 * `glances` - [Docs](https://glances.readthedocs.io/en/latest/)
 * `iftop`
 * `tcptrack`
 * `iptraf`
 * checkmd
	 * `omd create monitoring`
	 * `omd start monitoring`

 * `netstat -aon`
 * `route`

- `iw [interface] scan` or `iwlist`

# PowerShell
`Test-NetConnection -ComputerName <Host> -Port <port>`