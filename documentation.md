# Installation guide for macbook air 2015 Debian 13
# Wrote by AkiraDev7004

1. Install the .zip file on https://interhost-network.com/sites/akiradevstools/debian-drivers.zip

2. Get an USB stick (Needs atleast 1GB)

3. Put everything on there from my github repo

4. Boot into Debian13

 Become the root user:

    su -

find stick and mount (OPTIONAL):
    lsblk
    mkdir -p /mnt/usb
    mount /dev/sdX2 /mnt/usb
    ls /mnt/usb

Install all packages:

    cd /mnt/usb
    dpkg -i *.deb
    dpkg --configure -a

Load drivers:

    modprobe -r b43 bcma ssb
    modprobe wl
    ip link

Now connect to your internet (Command is optional. you can also do it with the gui.)

    ip link set wlp3s0 up
    iw wlp3s0 scan | grep SSID
    wpa_passphrase "YOUR WIFI´S NAME" "YOUR_WIFI_PASSWORD" > /etc/wpa_supplicant/wpa_supplicant.conf
    wpa_supplicant -B -i wlp3s0 -c /etc/wpa_supplicant/wpa_supplicant.conf
    dhcpcd wlp3s0
    ping -c 3 debian.org


# OTHER BUGS AND FIXES:

   # IF THE TOUCHPAD IS BROKEN:
      modprobe -r usbmouse
      modprobe -r bcm5974
      modprobe bcm5974
