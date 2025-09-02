---
created: 2023-11-15 12:51:49Z
---



# Application Launch Icons
Given some application called **sumapp**, its corresponding **launcher** & **icon** files (e.g. `sumapp.desktop` & `sumapp.png` or `sumapp.svg` respectively) must be placed as follows:
## Launcher
	$BASE/applications/sumapp.desktop

## Icons
	$BASE/pixmaps/sumapp.png
 * [See below](#the-base-directory) for values of `$BASE`

## Alternative directories for Icon images
 * The icon can be placed elsewhere, so long its full path is specified in the `Icon=` field of `sumapp.desktop`
 * See the [Icon Theme Specification](https://freedesktop.org/wiki/Specifications/icon-theme-spec/) for details on how icon search algorithm works in the context of themes.

## Theme specific Icons 
	$BASE/icons/$THEME/$SIZE/apps/sumapp.png
 * To establish a default for non-specified themes, use `$THEME=hicolor` since this folder is searched if no icon exists in the directory of the currently presiding theme.
 * Conveniently, the possible `$SIZE` directories exhibit self-explanatory names; in particular, they're named according to the pixel dimensions of the icons they should contain (e.g. `$SIZE=128x128`).
   * If one possesses an icon file of type `.svg`, then choose `$SIZE=scalable` like so
### Scalable Icon
	$BASE/icons/$THEME/scalable/apps/sumapp.svg
* [UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

# The `$BASE` directory
 * All possible choices of `$BASE` are stored in the `$XDG_DATA_DIRS` shell variable
## Locally installed for single User
### `~/.local/share` or
### `~/.local/share/flatpak/exports/share` for Flatpak applications

## Globally installed for all system Users
### `/usr/share` or `/usr/local/share`
###  `/var/lib/flatpak/exports/share` for Flatpak applications
###  `/var/lib/snapd/desktop` for Snap applications
