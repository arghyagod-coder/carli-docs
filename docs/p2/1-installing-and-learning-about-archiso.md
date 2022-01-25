# Installing and Learning About ArchISO

## Concepts 
- Learn about archiso package
- Read all the information about archiso you can find
- Use archiso to build an ISO yourself
- Analyze permissions, user and group names
- No local repository but instead online

## Preliminary

Read [this Article](https://wiki.archlinux.org/title/archiso) before proceeding.

## Course

We start by reading the vision [here](https://www.arcolinuxiso.com/goal-and-vision/). We need to read the article about **archiso** on the Arch Wiki (see preliminary) and we will set up our github on [https://github.com/arcolinuxiso/.](https://github.com/arcolinuxiso/). It is a must to know what files and folders you get when installing archiso.

We install archiso with this command:

```
sudo pacman -S archiso
```

Now you can use **pamac** to see **what** is installed **where** and you can go read what is installed.

`mkarchiso` is the most important script/application that will be used later on to build the ISO.

There are two profiles: baseline, and releng. **We will only use the releng profile.**

We create a new github for Carli. We will number them to the phase we are in.

We will re-use the files from our githubs. Setting up githubs is explained [here](https://arcolinuxd.com/getting-ready-for-the-next-phases/).

We copy/paste the releng profile inside the Carli folder and post it online to Github.

Read all the files from archiso package and read the page on the arch wiki about [mkinitcpio.](https://wiki.archlinux.org/index.php/Mkinitcpio)

We talk about the following files :

* packages.x86_64 file provides the content for the ISO
* mkinitcpio.conf – configuration file for your initial ramdisk
* pacman.conf – the repositories pacman will use and its settings
* airootfs – overlay for your future ISO
* customize_airootfs.sh – a script to change your future linux system
* build.sh – open it and read it

We can start building with

sudo ./build.sh -v

Use the -v to get more information while it is building. We will add it to the script later on.

There will be two extra folders.

1. work
2. out

Now you can load this ISO into VirtualBox.

If there is a **work** directory, you can **not** run the build script again.

We make a **cleanup** **script** to be able to build again.

We also create the file **.gitignore** to ensure the work folder and out folder will never go online.

We check the content of our ISO by mounting it and check again on VirtualBox.

Let us set the -v option by default in the build.sh