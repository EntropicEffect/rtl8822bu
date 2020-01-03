<u>**8822BU for Linux**</u>

Driver for 802.11ac USB Adapter with  
RTL8822BU chipset  
Only STA/Monitor Mode is supported, no AP.  

A few known wireless cards that use this driver include 
* [Edimax EW-7822ULC](http://us.edimax.com/edimax/merchandise/merchandise_detail/data/edimax/us/wireless_adapters_ac1200_dual-band/ew-7822ulc/)
* [ASUS AC-53 NANO](https://www.asus.com/Networking/USB-AC53-Nano/)
* [D-Link DWA-182 (Revision D1 only)](http://ca.dlink.com/products/connect/wireless-ac1200-dual-band-usb-adapter/)


> NOTE: At least v4.7 is needed to compile this module
> sorry people with older kernels, the code is removed.
> Upon request I can work towards making it backwards compatible.

Currently tested on X86_64 and ARM platform(s) **only**,  
cross compile possible.

For manual installation type  
`make`  
in source dir; then, to install the firmware files  
`sudo make install`

Or, for DKMS-compatible distros, (after installing `dkms` package,) place or link the source dir as  
`/usr/src/rtl8822bu-git`  
then execute  
`sudo dkms install rtl8822bu/git`


To Unload driver you may need to disconnect the device  

If the driver fails building consult your distro how to  
install the kernel sources and build an <u>external</u> module.


**NOTES**  
This driver allows use of wpa_supplicant by using the nl80211 driver
`wpa_supplicant -Dnl80211`

If installing on Rasberry Pi or other "armv71" devices, edit the Makefile and set `CONFIG_PLATFORM_ARM_RPI = y` and `CONFIG_PLATFORM_I386_PC = n`

On Debian with some wireless managers (KDE confirmed) you must append the following to /etc/NetworkManager/NetworkManager.conf:

[device]
wifi.scan-rand-mac-address=no

Otherwise, you may get stuck in an infinte loop of failed connection and a prompt for password. Source page here:
https://wiki.debian.org/WiFi

**STATUS**  
Driver works fine (some sort of)  
Most of the work is done is cleaning the driver and make this mess **readable**   for conversion.
Updates for wireless-ext/cfg80211  are not accepted.  

  
**BUGS**  
