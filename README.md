# wpa2own
<div align="center"><img src="img/logo.jpg" alt="SHALL WE PLAY A GAME?"></div>

## About

The goal of this project is to automate the process of capturing packets on a WPA2 protected wireless network, and crack their PSK (pre-shared keys). We know that WPA3 is coming, but most didn't know that WPA2 was as susceptible to being broken as it is with this recently released [Hashcat](https://hashcat.net) method.

### History

* on August 4, 2018 there was an announcement on the Hashcat forum of a [New attack on WPA/WPA2 using PMKID](https://hashcat.net/forum/thread-7717.html) The tweet linking to it:
<div align="center"><img src="img/tweet.png" alt="The announcement tweet"></div>

* using that info, and other ideas fleshed out from [The Hacker News](https://thehackernews.com/2018/08/how-to-hack-wifi-password.html) how-to post, the genesis for this project started
* on August 8, 2018 in Las Vegas, the day before [DEF CON](https://defcon.org) 26, I started building this using [Kali Linux](https://www.kali.org/) Rolling release (4.17.0-kali1-amd64 #1 SMP Debian 4.17.8-1kali1 (2018-07-24) x86_64 GNU/Linux) for development and testing
* now that I'm working on it more, I see a many more posts about this method. The original how-to, [How to Hack WiFi Password Easily Using New Attack On WPA/WPA2](https://thehackernews.com/2018/08/how-to-hack-wifi-password.html), and others I'm finding, [A New Method Discovered to Crack WPA/WPA2 PSK Enabled WiFi Network Passwords](https://gbhackers.com/crack-wifi-network-passwords/), [New attack on WPA/WPA2 using PMKID](https://medium.com/@adam.toscher/new-attack-on-wpa-wpa2-using-pmkid-96c3119f7f99)

## Requirements

### Hardware

- a 64 bit Linux system with a network card that supports montior mode - see [Gotchas](#gotchas)
- a 64 bit Linux system with a GPU (graphics processing unit) for running Hashcat against the pcap - again, see [Gotchas](#gotchas). In this example we're assuming this is a seperate machine, but in the case that you have both on one system, we could rework things to account for that.

### System utilities

- bash
- curl
- git
- make
- rsync
- sudo 

### Packages needed to build hcxtools 
  
- libopenssl and openssl-dev installed
- librt and librt-dev installed (should be installed by default)
- zlib and zlib-dev installed (for gzip compressed cap/pcap/pcapng files)
- libcurl and curl-dev installed (used by whoismac and wlancap2wpasec)
- libpthread and pthread-dev installed (used by hcxhashcattool)
       
EXAMPLE: to install all software requirements in Debian Linux, Ubuntu Linux, or Kali Linux: 

```sudo apt-get -y install libcurl4-openssl-dev libssl-dev zlib1g-dev libpcap-dev libgmp3-dev```

__TODO: include package list for other Linux distros. LMK if you figure any out!__

### Tools that the script will download and build

- hcxdumptool (v4.2.0+)
- hcxtools (v4.2.0+)
- hashcat (v4.2.0+)

## Gotchas

1) You need a networking card that supports monitor mode under Linux, from online posts I've seen the following NICs listed:

```
Supported adapters (strict)

USB ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter
USB ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
USB ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
USB ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
USB ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
```

For development and testing, I used the [Ralink RT5370](https://www.amazon.com/Ralink-RT5370-Raspberry-adapter-function/dp/B019XUDHFC) USB wireless plugged into my Mac Book Air (6,1) laptop. The output from `lusb` is:

```
$ lsusb | grep Ralink
Bus 001 Device 039: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
```

2) The old `hashcat-legacy` uses the CPU to try and crack hashes, but that code is over 3 years old, and is going to be far too slow to crack what we're capturing here. I might provide it as an option, but it's really more of a POC that you could used in canned environments with very simple passwords. To really get the ball rolling you can should use `hashcat` with the OpenCL headers (we pull those down as part of the build), and that requires a system with a compatible GPU.

__TODO: give examples of how this works, with specfic drivers__

## Usage

After resolving the requirements and understanding the gotchas:

```
./wpa2own
```

__NOTICE (8/14/2018) currently, once the scan is complete, your output file is saved in the `out/` dir, ready to run against `hashcat` on a system with GPU processors. I'm working to get this bit automated so it will `scp` the file to a GPU enabled rig, run it there and give you the results. This is a WIP, working to have complete by next week!__

## License

* [MIT License](LICENSE)

## Disclaimer

This software is for educational purposes, in order to learn about vulnurable systems to better be able to protect yourself. I'm a big believer in ethical hacking, so do not use this software to break any laws. Don't misuse this script, or information gathered from it to gain unauthorised access to any networks or hardware. Also, be aware, performing hack attempts without permission on computers that you do not own is illegal.

__TODO flesh this out, make it more official, looking to eff.org for help here__

## Misc

* Image from the [WarGames](https://www.imdb.com/title/tt0086567) (1983) movie, courtesy of [BiellaColeman](https://twitter.com/BiellaColeman/status/1025078579892285440). 

### Thanks
