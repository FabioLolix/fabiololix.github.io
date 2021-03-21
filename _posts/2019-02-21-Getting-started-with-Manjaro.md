---
layout: post
title: Getting started with Manjaro
---

Small guide for developers which I'll bore with compiling and packaging issues

# Getting Manjaro

Official editions XFCE, KDE, Gnome:
* <https://osdn.net/projects/manjaro/>

Community editions Cinnamon, Budgie, Deepin, i3, Mate, LXQT, LXDE, etc: 
* <https://osdn.net/projects/manjaro-community/storage/>


## Comparison of package managers commands:

* <https://wiki.archlinux.org/index.php/Pacman/Rosetta>


## After installation steps

Update pacman mirrors and update system after installation

`sudo pacman-mirrors -f5 && sudo pacman -Syyu`

Don't perform partial upgrades, use -yu or do upagrdes before installing new packages


## Development tools

Install development tools (similar to build-essential Debian/Ubuntu)

`sudo pacman -Syyu --needed git base-devel`


## Build and install one of my pkgbuild from Github

My Github pkgbuilds repo 1:
* <https://github.com/FabioLolix/PKGBUILD>

My Github pkgbuilds repo 2:
* <https://github.com/FabioLolix/PKGBUILD-AUR_fix>


`git clone https://github.com/FabioLolix/PKGBUILD`

`cd PKGBUILD/$package`

`makepkg -scCi`


## makepkg options

makepkg need to run in same folder of PKGBUILD file (by default)

* -s  Install missing dependencies using pacman (note: will not work for deps in AUR)
* -c  Clean up leftover work files and directories after a successful build.
* -C  Remove the $srcdir before building the package.
* -i  Install or upgrade the package after a successful build using pacman


* -f, --force  makepkg will not build a package if a built package already exists in the PKGDEST (set in makepkg.conf(5)) directory,
             which may default to the current directory. This allows the built package to be overwritten.

* -r  Upon successful build, remove any dependencies installed by makepkg during dependency auto-resolution and installation when using -s

* -d  Do not perform any dependency checks. This will let you override and ignore any dependencies required

## Build a package in a clean chroot

Install buildpkg

`sudo pacman Syu manjaro-tools-pkg`

buildpkg is run outside the folder where the PKGBUILD file is stored

`buildpkg -cp $package`

* -r  for using custom working directory (instead of /tmp)


### Getting started with the AUR

AUR web page
* <https://aur.archlinux.org/>

The Arch User Repository is not officially supported by Arch Linux or Manjaro etc.. 

<https://wiki.archlinux.org/index.php/Arch_User_Repository>

<https://wiki.manjaro.org/index.php?title=Arch_User_Repository>

Some command line helpers can be installed from the repository: yay, trizen and yaourt are available

Usage is like pacman but without using sudo


