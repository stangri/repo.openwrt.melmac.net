# stangri's OpenWrt/LEDE Project packages repo
This repo contains packages I've created for OpenWrt/LEDE Project routers. While some of these are packages are already available from official OpenWrt trunk and LEDE Project snapshots repositories/feeds, this repo usually contains newer versions.

## How to use

#### On your router
To add this repo to your OpenWrt/LEDE Project router run the following commands:

###### OpenWrt CC 15.05.1
```sh
opkg update; opkg install wget libopenssl ca-certificates
echo -e -n 'untrusted comment: public key 7ffc7517c4cc0c56\nRWR//HUXxMwMVnx7fESOKO7x8XoW4/dRidJPjt91hAAU2L59mYvHy0Fa\n' > /tmp/stangri-repo.pub && opkg-key add /tmp/stangri-repo.pub
! grep -q 'stangri_repo' /etc/opkg/customfeeds.conf && echo 'src/gz stangri_repo https://raw.githubusercontent.com/stangri/openwrt-repo/master' >> /etc/opkg/customfeeds.conf
sed -i 's/option check_signature 1/option check_signature 0/' /etc/opkg.conf
opkg update
```

###### LEDE Project and OpenWrt DD trunk
```sh
opkg update; opkg install uclient-fetch libustream-mbedtls ca-certificates
echo -e -n 'untrusted comment: public key 7ffc7517c4cc0c56\nRWR//HUXxMwMVnx7fESOKO7x8XoW4/dRidJPjt91hAAU2L59mYvHy0Fa\n' > /tmp/stangri-repo.pub && opkg-key add /tmp/stangri-repo.pub
! grep -q 'stangri_repo' /etc/opkg/customfeeds.conf && echo 'src/gz stangri_repo https://raw.githubusercontent.com/stangri/openwrt-repo/master' >> /etc/opkg/customfeeds.conf
opkg update
```

#### In your Image Builder/SDK
###### Image Builder
Add the line ```src/gz stangri_repo https://raw.githubusercontent.com/stangri/openwrt-repo/master``` to the ```repositories.conf``` file inside your Image Bulder directory. You can use the following code:
```
! grep -q 'stangri_repo' repositories.conf && sed -i '2 i\src/gz stangri_repo https://raw.githubusercontent.com/stangri/openwrt-repo/master' repositories.conf
```

###### SDK
The packages are in various branches at [my  packages source](https://github.com/stangri/openwrt-packages) and [my  luci source](https://github.com/stangri/openwrt-luci) repositories. Check out the code you want and add it to your SDK by adding ```src-link``` to ```feeds.conf``` (OpenWrt) or ```feeds.conf.default``` (LEDE Project).




## Description of packages

#### fakeinternet
This service can be used to fake internet connectivity for local devices.
Can be used on routers with no internet access to suppress warnings on local devices on no internet connectivity. Please see the [README](https://github.com/stangri/openwrt-packages/blob/fakeinternet/net/fakeinternet/files/) and [LEDE Project Forum Thread](https://forum.lede-project.org/t/fakeinternet-service-package-wip/924) for further information.

#### luci-app-easyflash
This package installs Web UI for quickly updating your router firmware if you use automated snapshots build process which produces fully customized images and uploads them to your router. Requires sysupgrade-compatible upgrade file ```/tmp/firmware.img``` and a one-line description (target/version/filename info) in ```/tmp/firmware.tag```. WARNING: does not keep your router settings.

#### luci-app-advanced-reboot
This package enables Web UI for reboot to another partition functionality on supported (dual-partition) routers and to power off (power down) your OpenWrt/LEDE Project router. Please see the [README](https://github.com/stangri/openwrt-luci/blob/luci-app-advanced-reboot/applications/luci-app-advanced-reboot/README.md) and [LEDE Project Forum Thread](https://forum.lede-project.org/t/web-ui-to-reboot-to-another-partition-for-dual-partition-routers/3423) for further information.

#### luci-mod-alt-reboot
This package enables Web UI for reboot to another partition functionality on supported (dual-partition) routers and to power off (power down) your OpenWrt/LEDE Project router by overwriting default System --> Reboot page. Please see the [README](https://github.com/stangri/openwrt-luci/blob/luci-mod-alt-reboot/modules/luci-mod-alt-reboot/README.md) for further information. This package has been superseded by ```luci-mod-advanced-reboot``` and is no longer developed/supported.

#### vpn-policy-routing & luci-app-vpn-policy-routing
This service can be used to enable policy-based routing for OpenVPN and/or Wireguard tunnel(s) and WAN/WAN6 interface(s). Supports policies based on domain names, IP addresses and/or ports. Compatible with legacy (IPv4) and modern (IPv6) protocols. Please see the [README](https://github.com/stangri/openwrt-packages/blob/vpn-policy-routing/net/vpn-policy-routing/files/README.md) and [LEDE Project Forum Thread](https://forum.lede-project.org/t/openvpn-policy-based-routing-web-ui-testers-needed/1422/1) for further information.


#### simple-adblock & luci-app-simple-adblock
This service provides lightweight and very fast dnsmasq-based ad blocking. Please see the [README](https://github.com/stangri/openwrt-packages/blob/simple-adblock/net/simple-adblock/files/README.md) and [LEDE Project Forum Thread](https://forum.lede-project.org/t/simple-adblock-fast-lightweight-and-fully-uci-luci-configurable-ad-blocking/1327) for further information.


#### vpnbypass & luci-app-vpnbypass
This service can be used to enable simple VPN split tunneling. Supports accessing domains, IP ranges outside of your VPN tunnel. Also supports dedicating local ports/IP ranges for direct internet access (outside of your VPN tunnel). Please see the [README](https://github.com/stangri/openwrt-packages/blob/vpnbypass/net/vpnbypass/files/README.md) and [LEDE Project Forum Thread](https://forum.lede-project.org/t/vpn-bypass-split-tunneling-service-luci-ui/1106/12) for further information.
