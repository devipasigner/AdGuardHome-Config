# [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome) Configuration

***
# Settings -> General

### Filter update interval

12 or 24 hours. 

Anything below is overkill and a waste of bandwidth.

# Settings -> DNS Settings


### DNS
[List of known DNS providers](https://adguard-dns.io/kb/general/dns-providers/)

Use the DNS provider with the lowest latency. I recommend you to test [Cloudflare](https://adguard-dns.io/kb/general/dns-providers/#cloudflare-dns), [NextDNS](https://adguard-dns.io/kb/general/dns-providers/#nextdns), [Quad9](https://adguard-dns.io/kb/general/dns-providers/#quad9-dns).

Recommended Protocol (in order from best to worst): DoQ (QUIC), DoT (TLS Encryption), DoH (HTTPS Encrypted). 

### DNS server configuration

Rate limit: 0
Enable EDNS client subnet: NO
Enable DNSSEC: YES
Disable resolving of IPV6 addresses: NO
Blocking Mode: Default

### DNS cache configuration

Cache size: 33554432
Override minimum TTL: 3600
Override maximum TTL: 86400

### DHCP settings

Configure if your router does not allow you to change the DNS settings. Make sure to disable DHCP on your routers side before enabling DHCP in AdGuard Home to avoid conflicts.

***
# Filters -> DNS Blocklists


Add blocklist -> Add a custom list

### OISD Full
Name: OISD Full

Path: https://abp.oisd.nl/


### 1Hosts Lite
Name: 1Hosts Lite

Path: https://badmojr.gitlab.io/1hosts/Lite/adblock.txt


### NoTracking
Name: NoTracking Blocklist

Path: https://raw.githubusercontent.com/notracking/hosts-blocklists/master/adblock/adblock.txt

# Filters -> Custom filtering rules

### Stop Apple devices from using Apple's iCloud Private Relay service which bypasses our AdGuard Home server

Add the following:
```
# Block Apple iCloud Private Relay
||mask.icloud.com^$important,dnsrewrite=NXDOMAIN;;
||mask-h2.icloud.com^$important,dnsrewrite=NXDOMAIN;;
```
