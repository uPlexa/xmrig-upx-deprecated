# XMRig-UPX

[![GitHub Release Date](https://img.shields.io/github/release-date-pre/xmrig/xmrig.svg)](https://github.com/uPlexa/xmrig-upx/releases)
[![GitHub license](https://img.shields.io/github/license/xmrig/xmrig.svg)](https://github.com/uPlexa/xmrig-upx/blob/master/LICENSE)

XMRig-UPX is a high performance uPlexa (UPX) CPU miner, with official support for Windows and Linux.
Originally based on cpuminer-multi with heavy optimizations/rewrites and removing a lot of legacy code, since version 1.0.0 completely rewritten from scratch on C++.

<img src="https://i.imgur.com/ZhkaKA1.png" width="619" >

#### Table of contents
* [Features](#features)
* [Download](#download)
* [Usage](#usage)
* [Algorithm variations](#algorithm-variations)
* [Build](https://github.com/uPlexa/xmrig-upx/wiki/Build)
* [Other information](#other-information)
* [Contacts](#contacts)

## UPXTWO HARDFORK SUPPORT
* use cryptonight-upx/1 for UPX variant 1
* use cryptonight-upx/2 for UPX variant 2 (or use cryptonight-upxtwo)
* use cryptonight-upx will revert to variant 1, post hardfork upx v1 will be deprecated
* Autoswitching from v1 to v2 will not work due to memory changes

## Download
* Binary releases: https://github.com/uPlexa/xmrig-upx/releases
* Git tree: https://github.com/uPlexa/xmrig-upx.git
  * Clone with `git clone https://github.com/uPlexa/xmrig-upx.git` :hammer: [Build instructions](https://github.com/uPlexa/xmrig-upx/wiki/Build).

## Usage
Use [config.xmrig.com](https://config.xmrig.com/xmrig) to generate, edit or share configurations.

### Options
```
  -a, --algo=ALGO          specify the algorithm to use
                             cryptonight-upx
  -o, --url=URL            URL of mining server
  -O, --userpass=U:P       username:password pair for mining server
  -u, --user=USERNAME      username for mining server
  -p, --pass=PASSWORD      password for mining server
      --rig-id=ID          rig identifier for pool-side statistics (needs pool support)
  -t, --threads=N          number of miner threads
  -v, --av=N               algorithm variation, 0 auto select
  -k, --keepalive          send keepalived packet for prevent timeout (needs pool support)
      --nicehash           enable nicehash.com support
      --tls                enable SSL/TLS support (needs pool support)
      --tls-fingerprint=F  pool TLS certificate fingerprint, if set enable strict certificate pinning
  -r, --retries=N          number of times to retry before switch to backup server (default: 5)
  -R, --retry-pause=N      time to pause between retries (default: 5)
      --cpu-affinity       set process affinity to CPU core(s), mask 0x3 for cores 0 and 1
      --cpu-priority       set process priority (0 idle, 2 normal to 5 highest)
      --no-huge-pages      disable huge pages support
      --no-color           disable colored output
      --variant            algorithm PoW variant
      --donate-level=N     donate level, default 5% (5 minutes in 100 minutes)
      --user-agent         set custom user-agent string for pool
  -B, --background         run the miner in the background
  -c, --config=FILE        load a JSON-format configuration file
  -l, --log-file=FILE      log all output to a file
  -S, --syslog             use system log for output messages
      --max-cpu-usage=N    maximum CPU usage for automatic threads mode (default 75)
      --safe               safe adjust threads and av settings for current CPU
      --asm=ASM            ASM code for cn/2, possible values: auto, none, intel, ryzen.
      --print-time=N       print hashrate report every N seconds
      --api-port=N         port for the miner API
      --api-access-token=T access token for API
      --api-worker-id=ID   custom worker-id for API
      --api-id=ID          custom instance ID for API
      --api-ipv6           enable IPv6 support for API
      --api-no-restricted  enable full remote access (only if API token set)
      --dry-run            test configuration and exit
  -h, --help               display this help and exit
  -V, --version            output version information and exit
```

Also you can use configuration via config file, default name **config.json**.

## Algorithm variations

- `av` option used for automatic and simple threads mode (when you specify only threads count).

| av | Hashes per round | Hardware AES |
|----|------------------|--------------|
| 1  | 1 (Single)       | yes          |
| 2  | 2 (Double)       | yes          |
| 3  | 1 (Single)       | no           |
| 4  | 2 (Double)       | no           |
| 5  | 3 (Triple)       | yes          |
| 6  | 4 (Quard)        | yes          |
| 7  | 5 (Penta)        | yes          |
| 8  | 3 (Triple)       | no           |
| 9  | 4 (Quard)        | no           |
| 10 | 5 (Penta)        | no           |

### HUGE PAGES unavailable
* Run XMRig as Administrator.

## Other information
* No HTTP support, only stratum protocol support.

### Maximum performance checklist
* Idle operating system.
* Do not exceed optimal thread count.
* Use modern CPUs with AES-NI instruction set.
* Try setup optimal cpu affinity.
* Enable fast memory (Large/Huge pages).


## Contacts
* [uplexa](https://reddit.com/r/uplexa)
* [discord](https://discord.gg/a7mAQwJ)
