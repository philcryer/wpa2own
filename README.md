# wpa2own

<div align="center"><img src="logo.jpg" alt="SHALL WE PLAY A GAME?"></div>

## About

- built on 20180808 at [DEF CON](https://defcon.org) 26 after the [New attack on WPA/WPA2 using PMKID](https://hashcat.net/forum/thread-7717.html) announcment on the Hashcat site. More ideas taken from this nice [hackernews.com howto](https://thehackernews.com/2018/08/how-to-hack-wifi-password.html) post. 
- using Kali Linux Rolling release (4.17.0-kali1-amd64 #1 SMP Debian 4.17.8-1kali1 (2018-07-24) x86_64 GNU/Linux) for development and testing

## Requirements

hardware
     * linux
     * a network card that supports montior mode

   system utilities
     * git
     * curl
     * make
     * sudo (or run as root :\ )

   packages needed to build hcxtools 
     * libopenssl and openssl-dev installed
     * librt and librt-dev installed (should be installed by default)
     * zlib and zlib-dev installed (for gzip compressed cap/pcap/pcapng files)
     * libcurl and curl-dev installed (used by whoismac and wlancap2wpasec)
     * libpthread and pthread-dev installed (used by hcxhashcattool)
       (install in Kali: apt-get install libcurl4-openssl-dev libssl-dev zlib1g-dev libpcap-dev)
       (TODO: package list for other Linux distros. LMK if you figure any out!)

   tools that the script will download and build
     * hcxdumptool (v4.2.0+)
     * hcxtools (v4.2.0+)
     * hashcat (v4.2.0+)

## Gotchas

## Usage

## License

* [MIT License](LICENSE}

## Misc

* Image from the [WarGames](https://www.imdb.com/title/tt0086567) (1983) movie, courtesy of [BiellaColeman](https://twitter.com/BiellaColeman/status/1025078579892285440). Thanks
