# [🏠 AdGuard Home](https://github.com/AdguardTeam/AdGuardHome) Configuration

***
# Settings -> General

### Filter update interval

Set to 12 hours.

Anything below is overkill and a waste of bandwidth.

# Settings -> DNS Settings


### 📖 DNS
[List of known DNS providers](https://adguard-dns.io/kb/general/dns-providers/)

Use the DNS provider with the lowest latency. I recommend you to test [Cloudflare](https://adguard-dns.io/kb/general/dns-providers/#cloudflare-dns), [NextDNS](https://adguard-dns.io/kb/general/dns-providers/#nextdns), [Quad9](https://adguard-dns.io/kb/general/dns-providers/#quad9-dns).

Recommended Protocol (in order from best to worst): DoQ (QUIC), DoT (TLS Encryption), DoH (HTTPS Encrypted). 


#### If using two or more upstreams change settings to parallel requests under your upstreams.

### DNS server configuration

Rate limit: 0

Enable EDNS client subnet: ⛔

Enable DNSSEC: ✔️

Disable resolving of IPV6 addresses: ⛔

Blocking Mode: Default

### DNS cache configuration

Cache size: 33554432

Override minimum TTL: 3600

Override maximum TTL: 86400

### DHCP settings

Configure if your router does not allow you to change its DNS settings. Make sure to disable DHCP on your routers side before enabling DHCP in AdGuard Home to avoid conflicts.

***
# Filters -> DNS Blocklists


### Add blocklist -> Add a custom list
#### ☁️Balanced Blocking (Rare breakages, Prioritizes functionality over blocking)

### OISD Full
Name: OISD Full

Path: https://abp.oisd.nl/


### 1Hosts Lite
Name: 1Hosts (Lite)

Path: https://badmojr.gitlab.io/1hosts/Lite/adblock.txt


### NoTracking
Name: NoTracking Blocklist

Path: https://raw.githubusercontent.com/notracking/hosts-blocklists/master/adblock/adblock.txt


### Stalkerware & Watchware Indicators
Name: Stalkerware & Watchware Indicators

Path: https://raw.githubusercontent.com/AssoEchap/stalkerware-indicators/master/generated/hosts_full


### Filters -> Choose from the list

Add:

### Security

Dandelion Sprout's Anti Malware List (contains regexes and abused tlds stripped from the curated lists above).
***
#### 🛡️Strict Blocking (More breakages, Prioritizes blocking over functionality)

Add the balanced blocking lists along with the lists below to achieve strict blocking

### Note: Don't add 1Hosts Lite if you are using 1Hosts Pro!
### 1Hosts Pro
Name: 1Hosts (Pro)

Path: https://badmojr.gitlab.io/1hosts/Pro/adblock.txt

### Lightswitch05 (Developer Dans Hosts)
Name: Lightswitch05's Ads & Tracking Extended

Path: https://www.github.developerdan.com/hosts/lists/ads-and-tracking-extended.txt

### MMotti AdGuard Home Regex Rules
Name: MMotti AdguardHome - regex

Path: https://raw.githubusercontent.com/mmotti/adguard-home-filters/master/regex.txt

***
#### 👶Parental Blocking (Adult & Porn Content)

### OISD Nsfw
Name: OISD Nsfw

Path: https://abp.oisd.nl/nsfw/

### 1Hosts kidSaf
Name: 1Hosts (kidSaf)

Path: https://badmojr.github.io/addons_1Hosts/kidSaf/adblock.txt
# Filters -> Custom filtering rules

### 🍎Stop Apple devices from bypassing our AdGuard Home server

Add the following:
```
# Block Apple iCloud Private Relay
||mask.icloud.com^$important,dnsrewrite=NXDOMAIN;;
||mask-h2.icloud.com^$important,dnsrewrite=NXDOMAIN;;
```

### DNS Rebinding Protection (Not added by AdGuard Team Yet)

Add the following:
```
/^192.0.0(.[0-9]{1,3}){1}$/
/^192.0.2(.[0-9]{1,3}){1}$/
/^198.51.100(.[0-9]{1,3}){1}$/
/^203.0.113(.[0-9]{1,3}){1}$/
/^192.168(.[0-9]{1,3}){2}$/
/^169.254(.[0-9]{1,3}){2}$/
/^10(.[0-9]{1,3}){3}$/
/^127(.[0-9]{1,3}){3}$/
/^0(.[0-9]{1,3}){3}$/
/^100.(6[4-9]|[7-9][0-9]{1}|1[0-1][0-9]|12[0-7])(.[0-9]{1,3}){2}$/
/^(22[4-9]|23[0-9])(.[0-9]{1,3}){3}$/
/^(24[0-9]|25[0-5])(.[0-9]{1,3}){3}$/
/^172.(1[6-9]|2[0-9]|3[0-1)(.[0-9]{1,3}){2}$/
/^198.(1[8-9])(.[0-9]{1,3}){2}$/
/^172.(1[6-9]|2[0-9]|3[0-1])(.[0-9]{1,3}){2}$/
```
⭐️Credits: [badmojr](https://github.com/badmojr), [sjhgvr](https://oisd.nl/), [notracking](https://github.com/notracking), [developer dan](https://www.github.developerdan.com/), [mmotti](https://github.com/mmotti), [assoechap](https://github.com/AssoEchap), [ghost](https://github.com/ghost).
