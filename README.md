# Farming [Grass](https://app.getgrass.io/register/?referralCode=sD8cUjUDV1uXTZO) using an old Android TV Box.
Transform your old TV box into a Grass farming device. This guide walks you through repurposing outdated hardware to create an efficient, low-cost node for cryptocurrency farming. If you want to farm on Android, please leave. We will transfrom Android box into a device with [Armbian](https://www.armbian.com/) OS. This tutorial is for A95X F3(almost same proccess with any TV Box with Amlogic CPU).
# Step 1: Install Armbian into TV BOX.
## Download the image
First, you should download an image of Armbian OS for [S9XX](https://www.armbian.com/amlogic-s9xx-tv-box/). You can check your box [here](https://github.com/devmfc/debian-on-amlogic/blob/main/README.md). I got A95X F3(S905X3) with cpu ARM Cortex-A55. I downloaded Armbian 25.2.0-trunk.13 Bookworm with Gnome for my own comfort. You can download the latest stable version and also without the Gnome, It´s up to you.
## Make bootable USB or SD-Card
You can use programms such as [Rufus](https://rufus.ie/sk/) or [balenaEtcher](https://etcher.balena.io/). File you downloaded, you should extract and then burn image from extracted file using one of this tool(rufus, balenaEtcher,...). Make sure that your image is burned well, your USB will be format into 2 partions(1 particion is OS and next particion are scripts for Armbian, which is visible partiocion). 
![image](https://github.com/user-attachments/assets/548e5b98-6b0e-4411-8bbe-69a2d9f6914e)
In dtb\amlogic you should find your model or the most similiar to your model e.g. i used for A95XF3 air /dtb/amlogic/meson-sm1-a95xf3-air.dtb . Copy the path and paste into extlinux.conf .

` \t label Armbian_community
\t  kernel /Image`
\t  initrd /uInitrd`
\t  fdt /dtb/amlogic/meson-sm1-a95xf3-air.dtb`
\t  append root=UUID=ace05f41-6d5a-4ed4-9f18-92f97628dedc rootflags=data=writeback console=ttyAML0,115200n8 console=tty0 rw no_console_suspend consoleblank=0 fsck.fix=yes fsck.repair=yes net.ifnames=0 splash plymouth.ignore-serial-consoles`
  


