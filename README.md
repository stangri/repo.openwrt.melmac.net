# stangri's OpenWrt/LEDE Project packages repo
This repo contains some packages I've created which haven't been accepted (or submitted) to the official OpenWrt/LEDE Project repo/feeds.


## Description of packages

#### fakeinternet
This service can be used to fake internet connectivity for local devices.
Can be used on routers with no internet access to suppress warnings on local devices on no internet connectivity. Please see the [README](https://github.com/stangri/openwrt-packages/blob/fakeinternet/net/fakeinternet/files/) and [LEDE Project Forum Thread](https://forum.lede-project.org/t/fakeinternet-service-package-wip/924) for further information.

#### luci-app-easyflash
This package installs Web UI for quickly updating your router firmware if you automated snapshots build process. Requires sysupgrade-compatible upgrade file ```/tmp/firmware.img``` and a one-line description (target/version info) in ```/tmp/firmware.tag```. WARNING: does not keep your router settings.

#### openvpn-policy-routing & luci-app-openvpn-policy-routing
This service can be used to enable policy-based routing for OpenVPN tunnel and WAN interface.
Supports accessing domains, IP ranges outside of your VPN tunnel.
Also supports dedicating local ports/IP ranges for direct internet access (outside of your VPN tunnel).
Please see the [README](https://github.com/stangri/openwrt-packages/blob/openvpn-policy-routing/net/openvpn-policy-routing/files/) and [LEDE Project Forum Thread](https://forum.lede-project.org/t/openvpn-policy-based-routing-web-ui-testers-needed/1422/1) for further information.


#### simple-adblock & luci-app-simple-adblock
This service provides dnsmasq-based ad blocking.
Please see the [README](https://github.com/stangri/openwrt-packages/blob/simple-adblock/net/simple-adblock/files/) and [LEDE Project Forum Thread](https://forum.lede-project.org/t/simple-adblock-fast-lightweight-and-fully-uci-luci-configurable-ad-blocking/1327) for further information.


#### vpnbypass & luci-app-vpnbypass
This service can be used to enable simple VPN split tunnelling.
Supports accessing domains, IP ranges outside of your VPN tunnel.
Also supports dedicating local ports/IP ranges for direct internet access (outside of your VPN tunnel).
Please see the [README](https://github.com/stangri/openwrt-packages/blob/vpnbypass/net/vpnbypass/files/) and [LEDE Project Forum Thread](https://forum.lede-project.org/t/vpn-bypass-split-tunneling-service-luci-ui/1106/12) for further information.

## How to use

### On your router
To add this repo to your OpenWrt/LEDE Project router run commands below.

- OpenWrt
```sh
opkg update; opkg install wget libopenssl
wget --no-check-certificate https://raw.githubusercontent.com/stangri/openwrt-repo/master/stangri-repo.pub -O /tmp/stangri-repo.pub
opkg-key add /tmp/stangri-repo.pub
opkg update
```

- LEDE Project
```sh
opkg update; opkg install uclient-fetch libustream-mbedtls
wget --no-check-certificate https://raw.githubusercontent.com/stangri/openwrt-repo/master/stangri-repo.pub -O /tmp/stangri-repo.pub
opkg-key add /tmp/stangri-repo.pub
opkg update
```

### In your Image Builder/SDK

