# stangri's OpenWrt/LEDE Project packages repo
This repo contains some packages I've created which haven't been accepted (or submitted) to the official OpenWrt/LEDE Project repo/feeds.

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

