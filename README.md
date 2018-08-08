# wpa2own

<div align="center"><img src="logo.jpg" alt="SHALL WE PLAY A GAME?"></div>

## About

- on 2018-08-07 a [New attack on WPA/WPA2 using PMKID](https://hashcat.net/forum/thread-7717.html) announcment was made on the Hashcat site. After this ideas were fleshed out in a [hackernews.com howto](https://thehackernews.com/2018/08/how-to-hack-wifi-password.html) post. Using these resources, and others online, the idea for this project started.
- on 2018-08-08, the day before [DEF CON](https://defcon.org) 26, I started building this using [Kali Linux](https://www.kali.org/) Rolling release (4.17.0-kali1-amd64 #1 SMP Debian 4.17.8-1kali1 (2018-07-24) x86_64 GNU/Linux) for development and testing

## Requirements

### Hardware

- GNU/Linux (64 bit)
- a network card that supports montior mode (see [Gotchas](#gotchas)

### System utilities

- git
- curl
- make
- bash
- sudo (or run as root :\ )

### Packages needed to build hcxtools 
  
- libopenssl and openssl-dev installed
- librt and librt-dev installed (should be installed by default)
- zlib and zlib-dev installed (for gzip compressed cap/pcap/pcapng files)
- libcurl and curl-dev installed (used by whoismac and wlancap2wpasec)
- libpthread and pthread-dev installed (used by hcxhashcattool)
       
EXAMPLE: to install all software requirements in Kali Linux: 

```apt-get install libcurl4-openssl-dev libssl-dev zlib1g-dev libpcap-dev)```

__TODO: include package list for other Linux distros. LMK if you figure any out!__

### Tools that the script will download and build

- hcxdumptool (v4.2.0+)
- hcxtools (v4.2.0+)
- hashcat (v4.2.0+)

## Gotchas

1) You need a networking card that supports monitor mode under Linux
2) While the script can use `hashcat-legacy`, that code is over 3 years old, and relies on your CPU to crack passwords. To really get the ball rolling you can should use `hashcat` with the OpenCL headers (we pull those down as part of the build), but that requires a compatible GPU.

__TODO: give examples of how this works, with specfic drivers__

## Usage

After resolving the requirements and understanding the gotchas:

```
./wpa2own
```

## License

* [MIT License](LICENSE)

## Disclaimer

This software is for educational purposes, in order to learn about vulnurable systems to better be able to protect yourself. I'm a big believer in ethical hacking, so do not use this software to break any laws. Don't misuse this script, or information gathered from it to gain unauthorised access to any networks or hardware. Also, be aware, performing hack attempts without permission on computers that you do not own is illegal.

__TODO flesh this out, make it more official, looking to eff.org for help here__

## Misc

* Image from the [WarGames](https://www.imdb.com/title/tt0086567) (1983) movie, courtesy of [BiellaColeman](https://twitter.com/BiellaColeman/status/1025078579892285440). 

### Thanks
