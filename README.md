# lxbmc


board managment controller for the solid-run honeycomb arm server


 - screws into a 2.5' drive bay
 - controlls power on.off
 - usb for virtual ethernet and disk
 - access the cpus local serial terminal remotely


# setup


after installing ubuntu with the usual usbboot thing:

    echo 'dtoverlay=dwc2,dr_mode=peripheral' >> /boot/firmware/config.txt

    systemctl stop serial-getty@ttyS0.service
    systemctl mask serial-getty@ttyS0.service

    systemctl stop systemd-resolved
    systemctl disable systemd-resolved
    rm /etc/resolv.conf
    echo nameserver 8.8.8.8 >  /etc/resolv.conf
    apt install dnsmasq
    systemctl stop dnsmasq
    systemctl disable dnsmasq


then install starfeldt bmc and config as:

    [power]
    switch='gpio5'

    [serial]
    device='/dev/ttyS0'

    [usb]


or if you're not a devguard customer maybe look at pikvm.org for a free alternative



# fan

https://github.com/neg2led/cm4io-fan
