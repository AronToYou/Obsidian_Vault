# aumid-stopgap-tools
---
- [GitHub Page](https://github.com/tksh164/aumid-stopgap-tools)

`{powershell title:CreateShortcut}mklnkwaumid <ShortcutFilePath> <AppUserModelID> <Target> [<ParametersForTarget>]`

`{PowerShell title:Execute}runwaumid -tp <AppUserModelID> <WindowTitle> <TargetToOpen> [<ParametersForTargetToOpen>]`
```powershell title:"CreateShortcut (Powershell):"
.\mklnkwaumid.exe 'D:\temp\Obsidian-Vault1.lnk' Tksh164.Obsidian.Vault1 'C:\bin\runwaumid.exe' '-tp Tksh164.Obsidian.Vault1 \"Vault1 - Obsidian\" obsidian://open?vault=Vault1'

.\mklnkwaumid.exe 'C:\Users\aron.lloyd\Desktop\ObsidianVault.lnk' md.obsidian.ObsidianVault 'C:\Program Files\aumid-stopgap-tools-0.1.0-x64\runwaumid.exe' '-tp md.obsidian.ObsidianVault \"Obsidian_Vault - Obsidian\" obsidian://open?vault=Obsidian_Vault'

.\mklnkwaumid.exe 'C:\Users\aron.lloyd\Desktop\Languages.lnk' md.obsidian.Languages 'C:\Program Files\aumid-stopgap-tools-0.1.0-x64\runwaumid.exe' '-tp md.obsidian.Languages \"Languages - Obsidian\" obsidian://open?vault=Languages'
```

```PowerShell title:"Created Links"
"C:\Program Files\aumid-stopgap-tools-0.1.0-x64\runwaumid.exe" -tp md.obsidian.ObsidianVault "Obsidian_Vault - Obsidian" obsidian://open?vault=Obsidian_Vault

"C:\Program Files\aumid-stopgap-tools-0.1.0-x64\runwaumid.exe" -tp md.obsidian.RheinEnergie "RheinEnergie - Obsidian" obsidian://open?vault=RheinEnergie

"C:\Program Files\aumid-stopgap-tools-0.1.0-x64\runwaumid.exe" -tp md.obsidian.Languages "Languages - Obsidian" obsidian://open?vault=Languages
```
### Icon
- put `32x32.ico` file in `.obsidian\` directory and link to shortcut
- pin shortcut to taskbar
	- delete desktop shortcut


# Code Style
---
- ` ```cpp fold title:example_title `
- ` ```cpp title=example_title fold ` (same effect as above line)
- ` ``` fold title:example_title ` (if no language set)


# Résumé
---

| booty   | booty_1   | booty_2            | booty_3         |
| ------- | --------- | ------------------ | --------------- |
| science | tech_lean | simple_2_unskilled | stash (711a550) |


# All
---
- Software
	- Git, GitLab
	- Linux, bash, gprof, GDB
	- Languages
		- Go, Java, Node.js, HTML/CSS, SQL
	- Python
		- matplotlib, SciPy, 
		- PyTorch, pandas, scikit-learn, dask
		- pipenv, setuptools
	- C/C++
		- Boost, Eigen, CMake, Ctags
	- Documentation
		- Jira, Latex, Obsidian markdown, Sphinx
	- Containers
		- lxc, Docker, Vagrant
	- Database
		- MongoDB, SQLite, InfluxDB, Elastic Stack
		- PostgreSQL, RaimaDB, HDF5, JSON
	- protocols
		- protocol buffers, ReST, TCP/IP, PGP, SSH, HTTP, DOM
	- Other
		- Kubernetes, Terraform, Ansible
- Hardware
	- peripherals, RISC-V
	- FPGA
		- Icarus Verilog, Vivado, GTKWave
	- instruments
		- VNA, Oscilloscope, Spectrum Analyzer
	- Programs
		- Eagle, LTSpice, Autodesk Inventor
	- Protocols
		- UART, CAN, PCIe
		- I2C, Ethernet, SPI
- Lab
	- Laser, Embedded Systems
# Science
## Laboratory & Instrumentation
cable topology, vacuum systems, 
### Lasers
frequency stabilization, nonlinear, solid-state, ECDL
### Optics
beam alignment, fiber coupling, polarization optics, PDs, AOM/EOM
lens systems, cavities
### Data Acquisition / Control
VNA, Spectrum Analyzer, Oscilloscope
LabVIEW
DAQ
FPGA
analog/digital electronics 
### Automation
   pyVISA, GPIB, serial protocols, PCIe, UART, 
   microcontrollers
   DAC

### Data Analysis & Modeling
QuTiP 
Python, matplotlib, SciPy, scikit-learn
SIgnal processing
error, fourier, uncertainty
#### ML
PyTorch, pandas, dask

## Documentation
LaTeX, Obsidian, SPhinx, WiKi
## Programming
Git, LaTeX?, bash, Linux
Go Node, HTML
### Development
GDB, gprof, jira, Git, bash
### Software
#### Databases
Mongo, SQLite, Influx, Elastic
#### Containerization
   lxc, docker, vagrant
   
   
# Communication & Research Skills
---
- Project Management
	- planning phased deployments
	- iterative refinement
	- metric-based development
- Team Collaboration	
	- Cross-disciplinary collaboration with theorists, engineers, or visiting researchers
- Technical Communication
	- writing clear SOPs and Documentation
- Attention to Detail
	- Precision alignment, calibration, and system diagnostics
	- multi-layered issues