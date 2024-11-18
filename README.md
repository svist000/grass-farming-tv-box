# Farming [Grass](https://app.getgrass.io/register/?referralCode=sD8cUjUDV1uXTZO) using an old Android TV Box.
Transform your old TV box into a Grass farming device. This guide walks you through repurposing outdated hardware to create an efficient, low-cost node for cryptocurrency farming. If you want to farm on Android, please leave. We will transfrom Android box into a device with [Armbian](https://www.armbian.com/) OS. This tutorial is for A95X F3(almost same proccess with any TV Box with Amlogic CPU).
# Step 1: Install Armbian into TV BOX.
## Download the image
First, you should download an image of Armbian OS for [S9XX](https://www.armbian.com/amlogic-s9xx-tv-box/). You can check your box [here](https://github.com/devmfc/debian-on-amlogic/blob/main/README.md). I got A95X F3(S905X3) with cpu ARM Cortex-A55. I downloaded Armbian 25.2.0-trunk.13 Bookworm with Gnome for my own comfort. You can download the latest stable version and also without the Gnome, It´s up to you.
## Make bootable USB or SD-Card
You can use programms such as [Rufus](https://rufus.ie/sk/) or [balenaEtcher](https://etcher.balena.io/). File you downloaded, you should extract and then burn image from extracted file using one of this tool(rufus, balenaEtcher,...). Make sure that your image is burned well, your USB will be format into 2 partions(1 partition is OS and next partition are scripts for Armbian, which is visible partiocion). 

![Partiocion that you can open](https://github.com/user-attachments/assets/548e5b98-6b0e-4411-8bbe-69a2d9f6914e)

## Modify scripts in visible partition
When you open visible partition, in dtb\amlogic you should find your model or the most similiar to your´s e.g. i used for A95XF3 air /dtb/amlogic/meson-sm1-a95xf3-air.dtb . Copy the path and paste into extlinux.conf.  Do not forget uncomennt lines and paste there `fdt /dtb/amlogic/meson-sm1-a95xf3-air.dtb` (path to your your model).
Then, your config file should look like this:

`extlinux.conf `
```
 label Armbian_community
  kernel /Image
  initrd /uInitrd
  fdt /dtb/amlogic/meson-sm1-a95xf3-air.dtb
  append root=UUID=ace05f41-6d5a-4ed4-9f18-92f97628dedc rootflags=data=writeback console=ttyAML0,115200n8 console=tty0 rw no_console_suspend consoleblank=0 fsck.fix=yes fsck.repair=yes net.ifnames=0 splash plymouth.ignore-serial-consoles
```
 Rename file `u-boot-s905x3` into `u-boot.ext`
 
![Rename File](https://github.com/user-attachments/assets/3b53d8f7-34bb-445d-8ccc-f216265b6626)

## Boot your device.
I used USB for booting. Plug usb into the device. Plug device in electricity and at the same time stick something small, like a toothpick, into the AV port and hold for about 10 seconds. Then the devices should start booting. Then you should setup your OS with name, pass, etc... We´re done.

![Armbian Booting](https://github.com/user-attachments/assets/5fc2d12d-2b8b-4497-bb94-25c6a6119b1e)

# Step 2: Connect to your device
First, connect the device to a monitor using an HDMI cable, and attach a mouse and keyboard. Be sure, your device is connected to the internet. If you have GNOME, you can download and install Teamviewer, if not you can connect by SSH(e.g. Putty, CMD),so you won't need to connect using an external keyboard later. 
## Option 1(Teamviewer)
Simply download and install Teamviewer for linux arm64-64bit. You might see a pop-up window, and your TeamViewer may display a message such as 'deactivated.'"

![tw](https://github.com/user-attachments/assets/93895937-ac8c-4013-985d-9afc68707bfa)

To avoid this problem follow this step:
Open terminal and write
`sudo nano /etc/gdm3/daemon.conf`
 Also uncomment the existing line `#WaylandEnable=false`  -->   `WaylandEnable=false`

## Option 2(SSH)
You need to know your´s device local IP address. Use this command in your Linux: 

`ip a`

Using CMD you can connect from you PC to the device by this command: 

`ssh username@IP_address` 

Or use Putty:

![image](https://github.com/user-attachments/assets/5b4eb781-0efd-48e1-83ab-d8120844265a)

You should log by your password.

# Step 3: Start farming
If you have desktop version, you can start farming immediatly installing Brave Browser(Chromium doesn´t work for me). Brave support Chrome extensions. So you can simply search for [Grass](https://app.getgrass.io/register/?referralCode=sD8cUjUDV1uXTZO) [extension in brave](https://chromewebstore.google.com/detail/grass-lite-node/ilehaonighjijnmpnagapkhpcdbhclfg).









