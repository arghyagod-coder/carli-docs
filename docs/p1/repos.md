# Understanding Linux


## What is Linux?

Linux powers a variety of computer systems from light bulbs to guns, laptops to large computer centers. Linux powers everything from your phone to your smart refrigerator.

In desktop computing, Linux provides an alternative to commercial operating systems such as Windows and macOS. 

Linux sources from some of the earliest computer operating systems from the 1960s and 1970s, and so it retains its root philosophies of strong user-level security, customization, and system stability.

## What is a Linux Distribution?

On its own Linux isn't really all that useful. You need to add other programs and tools to it in order to make it what you want it to be.

For instance, a Linux powered fridge wouldn't work with just Linux itself. Somebody needs to write the programs and device drivers required to control the thermostat, output a display showing the temperature, and every other feature which is considered to [make the fridge smart](https://www.lifewire.com/smart-refrigerator-4158327).

Linux distributions are at their very core the Linux kernel, with the GNU tools added on top and then a set of other applications that the developers decided to package together to make their distribution.

A desktop Linux distribution is generally built up with some or all of the following tools:

* The Linux kernel
* GNU/Tools
* A display manager
* A window manager
* A desktop environment
* An installer
* Package managers
* Desktop software such as office suites, email clients, web browsers, video players, audio players, etc

## What Is a Desktop Environment?

A typical Linux distribution includes several different components.

A display manager logs you in while a window manager governs windows, panel, menus, dash interfaces and core applications. Many of these items are bundled together to make a desktop environment.

Some Linux distributions ship with just one desktop environment (although others are available in the software repositories), while others offer different versions of the distribution fine-tuned for different desktop environments.

Common desktop environments include Cinnamon, GNOME, Unity, KDE, Enlightenment, XFCE, LXDE and MATE.

Cinnamon is a more conventional desktop environment that looks much like Windows 7, with a panel at the bottom, a menu, system tray icons, and quick launch icons. 

GNOME and Unity are fairly similar. They are modern desktop environments that use the concept of launcher icons and a dashboard-style display for picking applications. There are also core applications that integrate well with the overall theme of the desktop environment.

KDE is a classic-style desktop environment with many custom features and a core set of applications that are all highly customizable.

Enlightenment, XFCE, LXDE, and MATE are lightweight desktop environments with panels and menus.

## Are There Any Decent Office Suites for Linux?

For personal use and for small- to medium-sized businesses, [LibreOffice](https://www.lifewire.com/libreoffice-vs-openoffice-who-wins-2512178) presents a strong alternative to Microsoft Office, for free.

![LibreOffice|1280x720](https://www.lifewire.com/thmb/ht14T2v6GTZPsVfb1KNuSkYLRZE=/1280x720/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/libreofficewriter1-57e191cb5f9b586516055844.png)

LibreOffice comes with a word processor with the majority of the features you expect from a word processor. It also features a decent spreadsheet tool that is full-featured and includes a basic programming engine, although it isn't compatible with Excel VBA.

Other tools include the presentation, maths, database, and drawing packages which are all good.

To install libreoffice on Arch

```
sudo pacman -S libreoffice-fresh # This is the latest version with latest features
sudo pacman -S libreoffice-still # This is the stable edition with least breakage possibilities
```

## The Linux Command Line

Given its long heritage and the diversity of approach of modern desktop environments, a lot of Linux still works from a shell session. In the macOS world, these sessions are called the terminal; in Windows, the Command Prompt.

![Open A Terminal|1402x863](https://www.lifewire.com/thmb/e3xz-OC4Ck8Dn87Mbf_2K__NCqE=/1402x863/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/terminal-578e886e3df78c09e95a1057.png)

Although the graphical user interface of modern Linux DEs can do just about everything, much online education about Linux relies on the shell because it's not tied to the peculiarities of a given distribution or window manager. People new to Linux can get away with rarely or never working from the shell, but people who grow to love Linux often go to the shell first because of how easy it is to type one command instead of clicking through many different menus.

A terminal always comes with a desktop environment. You can just search up "Terminal" in your System and pick any terminal emulator.

## Packages

A package delivers and maintains new software for Linux-based computers. Just as Windows-based computers rely on executable installers, the Linux ecosystem depends on packages that are administered through software repositories. These files govern the addition, maintenance, and removal of programs on the computer.

Because each Linux computer uses different software, including different kernels, developers cannot guarantee that a "Linux program" will run correctly on any given computer. To fix this interoperability problem, packages include a manifest of dependencies, or lists of programs and versions that must be satisfied for the packaged software to run correctly on a given computer.

## Software Repository

A software repository is a storage location from which software packages are retrieved for installation.

Arch Linux official repositories contain essential and popular software, readily accessible via pacman. They are maintained by package maintainers.

Packages in the official repositories are constantly upgraded: when a package is upgraded, its old version is removed from the repository. There are no major Arch releases: each package is upgraded as new versions become available from upstream sources. Each repository is always coherent, i.e. the packages that it hosts always have reciprocally compatible versions.

A package manager does nothing but grab packages from an online software repository and embed it to your system.

## Stable repositories

### core

This repository can be found in `.../core/os/` on your favorite [mirror](https://wiki.archlinux.org/title/Mirror).

*core* contains packages for:

* booting Arch Linux
* [connecting to the Internet](https://wiki.archlinux.org/title/Network_configuration)
* [building packages](https://wiki.archlinux.org/title/Creating_packages)
* management and repair of supported [file systems](https://wiki.archlinux.org/title/File_systems)
* the system setup process (e.g. [openssh](https://archlinux.org/packages/?name=openssh))

as well as dependencies of the above (not necessarily [makedepends](https://wiki.archlinux.org/title/Makedepends)) and the [base](https://archlinux.org/packages/?name=base) [meta package](https://wiki.archlinux.org/title/Meta_package).

*core* has fairly strict quality requirements. Developers/users need to signoff on updates before package updates are accepted. For packages with low usage, a reasonable exposure is enough: informing people about update, requesting signoffs, keeping in [testing](https://wiki.archlinux.org/title/official_repositories#testing) up to a week depending on the severity of the change, lack of outstanding bug reports, along with the implicit signoff of the package maintainer.

**Tip:** To create a local repository with packages from *core* (or other repositories) without an internet connection see [Pacman tips#Installing packages from a CD/DVD or USB stick](https://wiki.archlinux.org/title/Pacman_tips#Installing_packages_from_a_CD/DVD_or_USB_stick)

### extra

This repository can be found in `.../extra/os/` on your favorite mirror.

*extra* contains all packages that do not fit in *core*. Example: Xorg, window managers, web browsers, media players, tools for working with languages such as Python and Ruby, and a lot more.

### community

This repository can be found in `.../community/os/` on your favorite mirror.

*community* contains packages that have been adopted by [Trusted Users](https://wiki.archlinux.org/title/Trusted_Users) from the [Arch User Repository](https://wiki.archlinux.org/title/Arch_User_Repository). Some of these packages may eventually make the transition to the [core](https://wiki.archlinux.org/title/official_repositories#core) or [extra](https://wiki.archlinux.org/title/official_repositories#extra) repositories as the developers consider them crucial to the distribution.

### multilib

This repository can be found in `.../multilib/os/` on your favorite mirror.

*multilib* contains 32-bit software and libraries that can be used to run and build 32-bit applications on 64-bit installs (e.g. [wine](https://archlinux.org/packages/?name=wine), [steam](https://archlinux.org/packages/?name=steam), etc).

With the multilib repository enabled, the 32-bit compatible libraries are located under `/usr/lib32/`.

#### Enabling multilib

To enable multilib repository, uncomment the `[multilib]` section in `/etc/pacman.conf`:

```
/etc/pacman.conf

[multilib] Include = /etc/pacman.d/mirrorlist
```

Then [upgrade](https://wiki.archlinux.org/title/Upgrade) the system and install the desired multilib packages.

**Tip:** Run `pacman -Sl multilib` to list all packages in the *multilib* repository. 32-bit library package names begin with `lib32-`.

#### Disabling multilib

Execute the following command to remove all packages that were installed from *multilib*:

```
pacman -R $(comm -12 <(pacman -Qq | sort) <(pacman -Slq multilib | sort))
```

If you have conflicts with gcc-libs reinstall the [gcc-libs](https://archlinux.org/packages/?name=gcc-libs) package and the [base-devel](https://archlinux.org/groups/x86_64/base-devel/) group.

Comment out the `[multilib]` section in `/etc/pacman.conf`:

```
/etc/pacman.conf

[multilib] #Include = /etc/pacman.d/mirrorlist
```

Then [upgrade](https://wiki.archlinux.org/title/Upgrade) the system.

Now you know how to use Linux as a standard user it is time to learn something a little bit more advanced such as learning how to use the command line.

Becoming proficient with the command line takes time but you can get to grips with the basics very quickly indeed.

At the very least you need to know how to navigate the file system which includes working out your present working directory, changing directories, making new directories, finding files, deleting files and creating new files.

No one can be a master Linux in a day.

You don't become an expert on any subject overnight. 

Continual use and continual learning is the only way to get to grips with anything whether it is learning to become a Linux guru or learning how to play the bagpipes.

Following online courses, keeping up to date with Linux news and getting help from the Linux community is the best way to move forward and remember the Linux man command is your friend.

## Other resources to learn

- [ArchWiki](https://wiki.archlinux.org)