# pfSense Newly Registered Domains (NRD) Downloader

This script downloads and aggregates a list of Newly Registerd Domains (NRD) from WhoisDS.com to create a custom DNSBL blocklist in pfBlockerNG. It is based on work by [PeterDaveHello](https://github.com/PeterDaveHello/nrd-list-downloader).

# Usage

To use this NRD script download the dnsbl_ip_nrd_downloader.sh script to the /usr/local/pkg/pfblockerng folder of your PFSense installation and give it execute permissions. Once downloaded it will appear as a pre-processing script within pfBlockerNG.

* Enable the script by going to Firewall -> pfBlockerNG on your firewall -> DNSBL -> DNSBL Groups within pfSense. Adding a new DNSBL group is recommended.
* Expand Advanced Tuneables and select dnsbl_ip_pre_nrd_downloader under Pre-process Script.
* Under DNSBL Source Definitions add /var/db/pfblockerng/nrd/nrd-14days-free.txt for the source, make sure that the State is on, and give it a Header/Label.
* Save, and you're done! By default the script downloads domains created within the last 14 days. This can be changed by editing the script.

You can now force an update or wait until pfBlockerNG next refreshes. All newly created domains will be blocked.
