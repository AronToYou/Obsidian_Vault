# Connections
## [SATA](https://en.wikipedia.org/wiki/SATA) (Serial AT Attachment)
- Computer Bus Interface connecting Host Bus Adapters to Mass Storage Devices, s.a.
	- HDD
	- Optical Drives
	- SSD
- Most SATA drives today use [Advanced Format](:/4ea594b041e043418f30b4ee6538f617#advanced-format-4k-sector)

## [SCSI](https://en.wikipedia.org/wiki/SCSI) (Small Computer System Interface)
- set of standards for physicall connecting and transferring data between computers and peripheral devices (e.g. USB sticks)
### random
- `htobe32()` - `htonl()`
- `htobe16()` - `htons()`
- `scsi_read()`
- **READ(10)** command of SCSI

# Storage Layout Formats
### Physical Sectors or Blocks
- [good link](https://utcc.utoronto.ca/~cks/space/blog/tech/AdvancedFormatDrives)
- Smallest section of memory the device can read to or write from per operation
### Logical Sectors
- The logical *blocks* to each of which addresses are designated
- Always less than or equal to Phsical Sectors
### Blocks

# Advanced Format (4K Sector)
- 8 traditional 512-byte sectors are combined together as single 4096-byte sectors
- ## Applies to magnetic storage devices (HDD)