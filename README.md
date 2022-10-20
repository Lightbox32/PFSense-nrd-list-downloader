# pfSense Newly Registered Domains (NRD) Downloader

This script downloads and aggregates a list of Newly Registerd Domains (NRD) from WhoisDS.com to create a custom DNSBL blocklist in pfBlockerNG. It is based on work by [PeterDaveHello](https://github.com/PeterDaveHello/nrd-list-downloader).

# Usage

To use this NRD script download the dnsbl_ip_nrd_downloader.sh script to the /usr/local/pkg/pfblockerng folder of your PFSense installation and give it execute permissions. Once downloaded it will appear as a pre-processing script within pfBlockerNG.

* Enable the script by going to Firewall -> pfBlockerNG on your firewall -> DNSBL -> DNSBL Groups within pfSense. Adding a new DNSBL group is recommended.
* Expand Advanced Tuneables and select dnsbl_ip_pre_nrd_downloader under Pre-process Script.
* Under DNSBL Source Definitions add /var/db/pfblockerng/nrd/nrd-14days-free.txt for the source, make sure that the State is on, and give it a Header/Label.
* Save, and you're done! By default the script downloads domains created within the last 14 days. This can be changed by editing line 24 in the script.
```
DAY_RANGE="${DAY_RANGE:-14}" -> change 14 to the number of days to download
```

You can now force an update or wait until pfBlockerNG next refreshes. All newly created domains will be blocked. Note that these lists are large, with 14 days of NRD averaging 1.5M domains.

# Why should I block NRD?

Malicious actors often register new domains to source spam or malware campaigns or to use for phishing or hacking. Blocking newly created domains provide a level of protection against these sites.

For more information on why you should block these newly created domains check out these articles by [HelpNetSecurity](https://www.helpnetsecurity.com/2019/08/23/block-new-domains/), [TripWire](https://www.tripwire.com/state-of-security/block-newly-registered-domains-to-reduce-security-threats-in-your-organisation), and [Palo Alto Networks](https://unit42.paloaltonetworks.com/newly-registered-domains-malicious-abuse-by-bad-actors/).
