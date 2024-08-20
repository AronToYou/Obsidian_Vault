# Standard Practices
## Unix System Resources
[Page](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html)
	/usr/
		- Reserved for distribution packages, apt
		/usr/share/
		/usr/local/
			- Resembles /usr/, for locally compiled apps
		/usr/local/share
	/opt/
		- Installation of pre-compiled apps
	/etc/
	
	/home/aron/ = ~/
		~/.local/
		~/.local/share/

	$BASE could be any of
		~/.local/share/
		~/.local/share/flatpak/exports/share/
		/usr/share/
		/usr/local/share
		/var/lib/snapd/desktop/
		/var/lib/flatpak/exports/share/
	$BASE/applications/
	$BASE/pixmaps/
	$BASE/icons/$THEME/$SIZE/apps/
	$BASE/icons/$THEME/scalable/apps/

# Technical Features
## inodes
### links
![[inode_links.png|]]