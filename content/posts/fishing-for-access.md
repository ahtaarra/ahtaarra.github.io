---
title: "Fishing for eduroam access using PSK"
date: 2024-06-26T20:27:37+01:00
tags:
 - Tech
 - Idea
draft: true
---

# The Main Bit...

## Situation
One key IT issue people run into with after joining university is connecting to the _eduroam_ Wi-Fi network which is a network group operating in the UK and some other parts of the world. While they solve the cruical technical issue of privacy, secure access and scale, the connection instructions available are not always adequate for all end-users. This sometimes calls for simpler solutions as can be seen below.

This was clear from my observation when having to install and use the _ClearPass Quick Connect_  Android app on the custom ROMs (LineageOS and GrapheneOS) on my phones. I would not use _Google Play_ store app to download the this companion app. The operating system’s intent handler for some reason would then not to open the subsequently downloaded configuration file (or ‘profile’) using the aforementioned app. This would get in the way of finishing the onboarding process. Therefore, what I had to do was to simply open the configuration certificate using it manually from my browser’s download page. Meanwhile, for other Linux-based systems, it is only the Ubuntu variant that appears to be officially supported, at least according to my university Intranet.

## Task
Now, what still remained was accesssing the same network which also extended to my university accommodation from my laptop. Generally, the entire process involves following a detailed set of instructions. Firstly, connect to a provisional network (an SSID titled ‘_*-Wireless_’) which gives one limited internet access, use the internal onboarding page to log in using own university account credentials which directs one to the companion app and then configuration profile download links to be used. Finally, disconnect from the original network, and connect to _eduroam_ instead. However, for Ubuntu what had been made available is a shell script (`ArubaQuickConnect.sh`) with which I had no success on my somewhat minimal Arch Linux system. I had to find another way.

## Action
One thing I tried was was using the graphical `nm-connection-editor` tool which is something I ordinarily do not have on my system as I primarily rely on `NetworkManager` utilities. Despite following instructions for ChromeOS which advised manually adding and configuring the network and configuration files, it did not work. In the end, I concluded that the vendor-specific instructions on the university Intranet and others available on the Internet were impractical for my specific setup. Thus, my initial recourse had been to connect my laptop to the internet using my phone’s hotspot either wirelessly or through USB tethering, until, of course, I found a more convenient solution.

This final solution was deceptively simple. After further research, I found on the Intranet instructions for ‘_Connecting wireless accessories to the network_’ and it provided access through another Network SSID titled ‘_*-PSK_’. This involved using university account credentials to log into a portal (in my case, it followed https://guest.*.ac.uk scheme), adding the laptop’s MAC address to generate a device-specific password.

## Result
I currently use the generated password to automatically connect to the WPA-PSK (an SSID titled ‘_*-PSK_’) network. While this is to be renewed every 12 months, this provided a reasonable solution to my connectivity issue.

# Wait... is this legal?


# Bonus content: using WireGuard VPN
`NetworkManager` can also be used to handle VPNs using its TUI. While it does not provide simple drop-downs to select regions out of the box, Wireguard/OpenVPN configuration entries can be added for each of the ones desired by following instructions found [here](https://blogs.gnome.org/thaller/2019/03/15/wireguard-in-networkmanager/):
> nmcli connection import type wireguard file "$CONF_FILE"

# Closing words
I now connect to _eduroam_ from my laptop automatically on my somewhat minimal system which, works reasonably well on my system. At least until after I graduate, this will have to do.
