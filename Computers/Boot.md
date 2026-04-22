- GRUB
	- UEFI
	- Legacy ? BIOS
- GRUB2
	- supports UEFI, doesn't have to be sd-boot
- systemd-boot
	- UEFI only
	- modular, single-threaded boot management application
# UEFI
- fwupd
	- can only use UEFI runtime services to
		- schedule system firmware updates
## EFI partition
## Class 3 and above
### No more
- RAID HBA - Host Bus Adapter
	- something that lets you interface
		- main host bus (i.e. PCI-E)
		- to an external bus (e.g. SAS, SATA, USB, etc.)
- network/graphics cards
- all above which lack UEFI-compatible vBIOS
## Vulnerabilities
### Secure Boot Bypass

### System Management Mode (SMM) Flaws
Highest privilege level, even below the OS (Ring -2)
Improper validation of communication buffers.

### Improper Input Handling
#### NVRAM manipulation
Exploitation of configuration data variables

#### Image parsing (LogoFAIL)

### Early-Boot DMA Attacks
Motherboard implementation fails to configure & enable the Input-Output Memory Management Unit (IOMMU) during early boot phase, despite sometimes indicating that DMA protection is active

### Outdated Secure Boot forbidden signature database (DBX)
# Legacy BIOS