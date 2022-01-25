# Install Arch Linux with Calam-Arch

As this tutorial is made for beginners, we use the Calam Arch installer. It is an excellent tool that can install vanilla Arch Linux with ease, rather than via the command line. Here’s how to use it.

**Note: The Calam Arch Linux installer ISO requires at least 1 GB of space. For best results, use a 1 GB USB flash drive or larger. Alternatively, burning an ISO file to a DVD also works, though DVD instructions are not covered in this guide.**

![|1200x674](https://www.addictivetips.com/app/uploads/2021/08/calam-arch-startup.png)

## Downloading Calam Arch ISO

The Calam Arch ISO installer is available for download on the project’s SourceForge page. To download the latest release of the ISO installer to your computer, do the following.

First, head over to the [Calam Arch SourceForge page](https://sourceforge.net/projects/blue-arch-installer/). Once on the page, locate the green “Download” button. When you select this button, the Calam Arch ISO file will begin to download.

Alternatively, if you need an older release of the Calam Arch installer, find the “Files” tab, select it. Then, click on the “Files” folder to check out older releases of the installer.

## Installing Calam Arch on VirtualBox

!!! Warning 
    Use this method ONLY IF you are gonna install Arch in a Virtual Machine

Undoubtedly, you need to first [install VirtualBox on Linux](https://itsfoss.com/install-virtualbox-ubuntu/) or Windows. On Windows, simply go to the Oracle’s website and download VirtualBox.

**[Download VirtualBox](https://www.virtualbox.org/wiki/Downloads)**

If you are using Windows 10 or newer version, please ensure that you have virtualization enabled on your system.

Keep your downloaded ISO ready.

### Part 1. Creating the Virtual Machine

**Step 1:** First, you need to set up a few things in VirtualBox. Launch VirtualBox and click on “**New**” to create a virtual machine.

![virtualbox new|800x562](https://i0.wp.com/itsfoss.com/wp-content/uploads/2021/10/virtualbox-new.png?resize=800%2C562&ssl=1)

Note that you can continue creating the virtual machine using the guided mode, but you get more options at a single glance with the expert mode.

![virtualbox expert mode|707x438](https://i0.wp.com/itsfoss.com/wp-content/uploads/2021/10/virtualbox-expert-mode.png?resize=707%2C438&ssl=1)

Hence, I recommend using the expert mode to create the virtual machine.

Fret not, the expert mode is as easy, with just a bit of extra available options and nothing else to worry about.

**Step 2**: Enter the name of your virtual machine, it should auto-detect the “Type” and “Version” respectively when you type in “**Arch Linux**” in the name field.

![virtualbox create|800x536](https://i0.wp.com/itsfoss.com/wp-content/uploads/2021/10/virtualbox-create.png?resize=800%2C536&ssl=1)

You should increase the memory size to use the virtual machine comfortably. If it is just for minor testing, you can go ahead with the default setting.

In my case, I allocate ~**4 GB of RAM**.

Also, make sure to **create a virtual hard disk** under the “Hard disk” option. It should be the selected option by default.

Now, proceed to set the virtual hard disk size.

**Step 3:** You can choose a preferred location path for the virtual hard disk and tweak the size as per your requirements. The installation should not be a problem with the minimum allocated size (8 GB), but to be on the safe side, you may want to allocate at least 10-15 GB.

![virtualbox disk|800x528](https://i0.wp.com/itsfoss.com/wp-content/uploads/2021/10/virtualbox-disk.png?resize=800%2C528&ssl=1)

Next, you need to select the hard disk file type as “**VDI (VirtualBox Disk Image)**” and the storage as “**Dynamically allocated**,” as shown in the image above.

VDI is the most common hard disk type for the virtual hard disk.

And, when you select the “**Dynamically allocated**” option for the hard disk storage, it means that the storage space will be utilized as per usage. In other words, 15 GB of space won’t be locked from your disk as soon as the virtual machine is created.

Now, all you have to do is hit “**Create**” to add the virtual machine.

### Part 2. Adding the ISO File to Start Installing Arch Linux

![choose disk virtualbox arch|800x440](https://i0.wp.com/itsfoss.com/wp-content/uploads/2021/10/choose-disk-virtualbox-arch.png?resize=800%2C440&ssl=1)

Once the VM has been listed, you can look at its configuration and select the ISO as the disk drive under the **Storage** option.

You can also separately head to the virtual machine settings to explore more and choose the ISO file.

![virtualbox settings option|800x551](https://i0.wp.com/itsfoss.com/wp-content/uploads/2021/10/virtualbox-settings-option.png?resize=800%2C551&ssl=1)

To do that, navigate your way to the “**Storage**” setting of the VM.

![virtualbox choose iso|800x314](https://i0.wp.com/itsfoss.com/wp-content/uploads/2021/10/virtualbox-choose-iso.png?resize=800%2C314&ssl=1)

Here, you will have to click on the “**Empty**” device under Controller and then proceed to select the Calam-Arch ISO file as the disk file (as shown in the image above).

My ISO's name is archlinux-date-arch.iso but your might be something else, according to what you have downloaded

![virtualbox arch iso select|800x348](https://i0.wp.com/itsfoss.com/wp-content/uploads/2021/10/virtualbox-arch-iso-select.png?resize=800%2C348&ssl=1)

Once you select it, hit “**OK**” to save the changes to your setting.

Here’s how the virtual machine setting should look like with the ISO set as the disk to boot:

![virtualbox set start|800x548](https://i0.wp.com/itsfoss.com/wp-content/uploads/2021/10/virtualbox-set-start.png?resize=800%2C548&ssl=1)

Now, hit “**Start**” to start the VM and get started with the installation.

Then start the VM, you'll boot into Calam-Arch
## Creating Calam Arch USB installer

!!! Warning 
    Use this method ONLY IF you are gonna install Arch in real hardware

The Calam Arch installer ISO file needs to be flashed to a USB flash drive. There are many ways to create a USB flash drive with an ISO file. In this guide, we’ll focus on the Etcher application.

Why Etcher? It is cross-platform. So, no matter what operating system you flash the Calam Arch ISO file to, the instructions are the same. To get your hands on the Etcher application, head over to the official website. Download Etcher and install it on your computer.

After installing the Etcher application on your computer, open it up and follow the step-by-step instructions below to make your Calam Arch USB installer.

![|1200x785](https://www.addictivetips.com/app/uploads/2020/01/etcher-page.jpg)

**Step 1:** Select the “Flash from file” button with the mouse. When you click on this button, a pop-up menu will appear on the screen. Using the menu, locate the Calam Arch ISO file on your computer and select it.

**Step 2:** Find the “Select target” button with the mouse. Then, choose the USB flash drive you wish to install the Calam Arch ISO file to.

**Step 3:** Click on the “Flash!” button in the Etcher application to start the flashing process. This process will take quite a bit of time, so be patient. When it is complete, close Etcher.

After closing the Etcher application, reboot the computer you plan to install Arch Linux on. Then, boot into the BIOS and configure it to boot from the USB flash drive.

## Installing Arch Linux with Calam Arch

To install Arch Linux with Calam Arch, start by clicking on the black Arch Linux logo on the desktop. Then, follow the step-by-step instructions below.

**Step 1:** Allow the Calam installer to launch on the desktop. Then, on the installer’s welcome page, find your preferred language. Then, click on the “Next” button to move to the next page in the installer.

![|1200x675](https://www.addictivetips.com/app/uploads/2021/08/calam-arch-welcome.png)

**Step 2:** After selecting your language, you’ll need to select your timezone. Using the on-screen map, choose your preferred timezone. Or, use the drop-down menus to choose your timezone.

![|1200x682](https://www.addictivetips.com/app/uploads/2021/08/calam-arch-timezone.png)

Click “Next” to continue to the next page.

**Step 3:** You’ll now need to select your keyboard layout. Using the on-screen menu, find the keyboard layout you prefer. Or leave it as default, as the Calam Arch installer should automatically detect it.

![|1200x676](https://www.addictivetips.com/app/uploads/2021/08/calam-arch-keyboard-layout.png)

Click the “Next” button to move to the next page.

**Step 4:** Once the keyboard is configured, it is time to choose your partitioning method. Select “Install alongside” if you prefer to dual-boot with Windows. Or, if you wish to erase the hard drive, select the “Erase disk” option.

If you are using a Virtual Machine, then just use "Erase Disk" option

![|1200x679](https://www.addictivetips.com/app/uploads/2021/08/calam-arch-partitioning.png)

When done, click the “Next” button.

**Step 5:** Following the partition setup, you’ll need to choose packages you wish to install with the new Arch Linux installation. Go through the list, choose your preferred desktop environment, graphics driver preferences, printer support (if needed), and other things.

**Package Information:**

- **Base-Devel + Common Packages**- Select this always
- **GeForce GTX-RTX Closed Drivers**- Select this if you have a Nvidia GPU and you are not using a virtual machine.
- **GeForce Open Drivers**- Select this if you have a Nvidia GPU and you are not using a virtual machine.
- **AMD Video Drivers**- Select this if you have an AMD GPU and you are not using a virtual machine.
- **Intel Video Drivers**- Select this if you have a Intel Integrated GPU and you are not using a virtual machine.

Now time to choose your desktop interface:

- **XFCE4 Desktop**- Select this if you want the XFCE Desktop Environment. XFCE Desktop looks like the following:

![](https://www.debugpoint.com/wp-content/uploads/2021/02/xfce416review.jpg)

- **GNOME Desktop**- Select this if you want the XFCE Desktop Environment. XFCE Desktop looks like the following:

![](https://www.gnome.org/wp-content/uploads/2021/03/wgo-splash-40.png)

- **KDE Desktop**- Select this if you want the XFCE Desktop Environment. XFCE Desktop looks like the following:

![](https://kde.org/announcements/plasma/5/5.22.0/plasma.png)

- **Cinnamon Desktop**- Select this if you want the XFCE Desktop Environment. XFCE Desktop looks like the following:

![](https://www.debugpoint.com/wp-content/uploads/2021/02/xfce416review.jpg)

- **Budgie Desktop**- Select this if you want the XFCE Desktop Environment. XFCE Desktop looks like the following:

![](https://www.debugpoint.com/wp-content/uploads/2021/02/xfce416review.jpg)

- **Deepin Desktop**- Select this if you want the XFCE Desktop Environment. XFCE Desktop looks like the following:

![](https://fostips.com/wp-content/uploads/2021/06/deepin-dark-feature.jpg)

All of the desktops are customizable and can be customized your own way. I personally recommend KDE or GNOME. KDE is light and also the most customizable desktop.

- **Printing Support**- Select this to get Printing Support on your machine. This is preferred when you install Arch Linux in real hardware. 
- **Web Browsers**- Select your favourite web browser (I recommend firefox) from the drop down list. 

![|1200x675](https://www.addictivetips.com/app/uploads/2021/08/calam-arch-select-packages.png)

When all packages are selected, click the “Next” button to confirm your choice.

**Step 6:** After setting up your packages for the Calam Arch Linux installer, you’ll have to set up your user account. First, write in your name in the “What is your name box.” Then, configure your username, and the name of your computer.

![|1200x675](https://www.addictivetips.com/app/uploads/2021/08/calam-install-overview.png)After setting up your name, username, and computer name, enter your password. Be sure to enter in a secure, memorable password. Click on the “Next” button to move to the next step in the installer.

**Step 7:** Following setting up your username, the Calam Arch installer will show a summary of your installation. Look it over and make sure everything looks good. When done, click on the “Install” button at the bottom of the page to install the operating system onto your computer.

![|1200x674](https://www.addictivetips.com/app/uploads/2021/08/calam-arch-startup.png)

When the installation is complete, unplug your USB flash drive and reboot. Upon rebooting, Arch Linux will be ready to use. Enjoy!

!!! Note
    To reboot on VirtualBox, remove the Optical ISO image we added in the "Storage" section of Settings.

## Reference Video Links

- [Installing Calam-Arch on VirtualBox](https://www.youtube.com/watch?v=X9DSQk9GXd4)