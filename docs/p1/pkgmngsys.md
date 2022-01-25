# How To Manage Packages Using Pacman

Pacman is a package manager for the arch Linux and arch-based Linux distributions. If you have used Debian-based OS like ubuntu, then the  Pacman is similar to the apt command of Debian-based operating systems. Pacman contains the compressed files as a package format and maintains a text-based package database. Pacman keeps the system up to date by synchronizing package lists with the master server. Pacman can install the packages from the official repositories or your own build packages. It is the terminal way of installing software in Arch Linux, just like you install software in Windows/Mac

In this section, I'll introduce you to some of the common pacman commands that you may need on a daily basis.

### How To Install Packages Using Pacman

To install a package using pacman, you can use the following command syntax. For example, to install rust:

```
# sudo pacman -S <package name>

sudo pacman -S rust
```

You can install multiple packages as follows:

```
# sudo pacman -S <package name> <package name>

sudo pacman -S rust golang
```

You can also specify the repository you want to install the package from like this:

```
# sudo pacman -S <package repository>/<package name>

sudo pacman -S extra/rust
```

In this command, the `-S` option means synchronize which is equivalent to install in the case of apt or dnf package managers.

### How To Remove Packages Using Pacman

To remove a package using pacman you can use the following syntax:

```
# sudo pacman -R <package name>

sudo pacman -R rust
```

This will remove the package but will leave the dependencies. You can remove the package with dependencies if they're not required by any other package by executing the following command:

```
# sudo pacman -Rs <package name>

sudo pacman -Rs rust
```

Pacman often saves important configuration files when removing certain applications. You can override this behavior by using the following syntax:

```
# sudo pacman -Rn <package name>

sudo pacman -Rn rust
```

I usually use `sudo pacman -Rns` whenever I want to uninstall something. One last thing that I want to show is how to remove orphan packages.

In Ubuntu the `sudo apt autoremove` command uninstalls any unnecessary package. The equivalent command in Arch is:

```
sudo pacman -Qdtq | pacman -Rs -
```

This will cleanup any leftover package from previously installed packages.

### How To Upgrade Packages Using Pacman

To upgrade all the packages in your system, you can use the following syntax:

```
sudo pacman -Syu
```

In this command, the `S` option synchronizes the packages, `y` refreshes the local package cache, and `u` updates the system. This is like the ultimate upgrade command and I run it at least once everyday.

### How To Search for Packages Using Pacman

To search for a package in the database, you can use the following syntax:

```
# sudo pacman -Ss <package name>

sudo pacman -Ss rust
```

This will print out all the packages found in the database with that search term and will also indicate if any of those are already installed.

If you would like to check if a package is already installed or not, you can use the following command:

```
# sudo pacman -Qs <package name>

sudo pacman -Qs rust
```

This is useful when you want to uninstall a package but do not know its exact name.

## How To Use AUR in Arch Linux

According to [It's FOSS](https://itsfoss.com/aur-arch-linux/),

> AUR stands for Arch User Repository. It is a community-driven repository for Arch-based Linux distributions users. It contains package descriptions named PKGBUILDs that allow you to compile a package from source with makepkg and then install it via pacman (package manager in Arch Linux).

AUR is one of the most attractive features of Arch Linux. It's due to AUR that Arch Linux has a package count almost equal to Debian. You've already used `pacman` to install various packages. Sadly, you can not use that to install packages from AUR.

You'll have to install one of the AUR helpers instead. Arch Linux doesn't support any of these helpers and advises you to learn how to build packages manually. I'll explain both techniques here. If you understand how a helper works, you'll be able to do it manually as well.

### How To Install Packages Using a Helper

Among the available and currently maintained AUR helpers, I like the `yay` or yet another yogurt package. It's written in Go and is quite solid.

You can not install `yay` like other packages. You'll have to get the source code and compile the program. You'll need `git` and the `base-devel` package to do so. Assuming you've already installed `base-devel` during Arch Linux installation:

```
pacman -S git
```

Clone the yay repository from GitHub and `cd` into it:

```
git clone https://aur.archlinux.org/yay.git && cd yay
```

To build and install yay from source, execute the following command:

```
makepkg -si
```

The makepkg script automates the build process of packages. The `-si` options stand for sync dependencies and install. The first option will install required dependencies (Golang in this case) and the later option will install the built package.

After the build process finishes, makepkg will ask for installation confirmation and your password. Input your password carefully and let the installation finish.

Check if yay has been installed properly or not:

```
yay --version

# yay v11.1.0 - libalpm v13.0.1
```

Now let's install something using yay. One of the common packages you may want to install is the [visual-studio-code-bin](https://aur.archlinux.org/packages/visual-studio-code-bin/) package. To do so, execute the following command:

```
yay -S visual-studio-code-bin
```

Unlike pacman, you shouldn't run yay with sudo. Yay will look for the given package and will ask whether you would like to see the diff or not:

![](https://www.freecodecamp.org/news/content/images/2022/01/VirtualBox_archlinux-2022.01.01-x86_64_14_01_2022_21_07_26.png)

All the repositories over at AUR comes with a PKGBUILD file which contains the instructions for building this package. Yay has this nice feature where it shows you what has changed in the PKGBUILD file since the last time.

For now, I'll pick `N` for none and hit enter. Yay will now look for the dependencies and ask for your password to install them.

![](https://www.freecodecamp.org/news/content/images/2022/01/VirtualBox_archlinux-2022.01.01-x86_64_14_01_2022_21_19_58.png)

Confirm the installation and provide your password. Yay will then install the dependencies and start building the package. Once built, yay will install the package and prompt for your password where necessary.

After the installation finishes, search for Visual Studio Code in the application launcher:

![](https://www.freecodecamp.org/news/content/images/2022/01/VirtualBox_archlinux-2022.01.01-x86_64_14_01_2022_21_28_42.png)

Congratulations on installing your first package from AUR. Yay commands are almost identical to pacman, so if you can do something with pacman, you should be able to do that with yay as well.

In fact, yay can also install packages from official Arch Linux repositories like pacman. But I would suggest you to use yay only for installing packages from AUR when necessary and pacman for everything else.

### How To Install Packages Manually

Like I said in the previous section, the ArchWiki suggests avoiding any AUR helper and installing packages from AUR manually. I'll now show you how to do it.

Make sure you have `git` and `base-devel` packages installed. If not, use `pacman` to install them.

For the demonstration, let's install Spotify this time. First visit the AUR page for the spotify package - https://aur.archlinux.org/packages/spotify/ and copy the "Git Clone URL" from there.

![](https://www.freecodecamp.org/news/content/images/2022/01/image-68.png)

The page even lists all the dependencies you'll need. Clone the repository to your machine:

![](https://www.freecodecamp.org/news/content/images/2022/01/VirtualBox_archlinux-2022.01.01-x86_64_16_01_2022_21_16_43.png)

Every AUR repository comes with a PKGBUILD file containing the instructions for building the package. Whenever you're installing a package from AUR, it's a great idea to checkout the PKGBUILD file using something like the `cat` command:

![](https://www.freecodecamp.org/news/content/images/2022/01/VirtualBox_archlinux-2022.01.01-x86_64_16_01_2022_21_22_37.png)

Make sure there's nothing harmful in the file. Once you're satisfied, use `makepkg` to install any dependencies, build the package, and install it. Ideally there shouldn't be any issues but sometimes, things can take an unexpected turn.

![](https://www.freecodecamp.org/news/content/images/2022/01/VirtualBox_archlinux-2022.01.01-x86_64_16_01_2022_21_34_29.png)

In these cases, go back to the corresponding AUR page and check the user comments. Like in this case, I found the following pinned comment:

![](https://www.freecodecamp.org/news/content/images/2022/01/image-69.png)

Turns out the package requires you to add the Spotify for Linux gpg key to the user kyechain. This command downloads the gpg key using `curl` and pipes it as the input of the `gpg --import` command:

![](https://www.freecodecamp.org/news/content/images/2022/01/VirtualBox_archlinux-2022.01.01-x86_64_16_01_2022_21_37_50.png)

Try executing `makepkg -si` once again and everything should work fine this time:

![](https://www.freecodecamp.org/news/content/images/2022/01/VirtualBox_archlinux-2022.01.01-x86_64_16_01_2022_21_39_33.png)

See, told ya! Manually installing packages often involves such troubleshooting but help is almost always around the comment corner. Let's enjoy some music now.