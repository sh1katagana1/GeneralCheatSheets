## Final Recon Cheatsheet

https://github.com/thewhiteh4t/FinalRecon

**Description:**
FinalRecon is an automatic web reconnaissance tool written in python. Goal of FinalRecon is to provide an overview of the target in a short amount of time while maintaining the accuracy of results. Instead of executing several tools one after another it can provide similar results keeping dependencies small and simple.

```
usage: finalrecon.py [-h] [--headers] [--sslinfo] [--whois] [--crawl] [--dns] [--sub] [--trace] [--dir] [--ps] [--full] [-t T]
                     [-T T] [-w W] [-r] [-s] [-sp SP] [-d D] [-e E] [-m M] [-p P] [-tt TT] [-o O]
                     url

FinalRecon - The Last Web Recon Tool You Will Need | v1.1.3

positional arguments:
  url         Target URL

optional arguments:
  -h, --help  show this help message and exit
  --headers   Header Information
  --sslinfo   SSL Certificate Information
  --whois     Whois Lookup
  --crawl     Crawl Target
  --dns       DNS Enumeration
  --sub       Sub-Domain Enumeration
  --trace     Traceroute
  --dir       Directory Search
  --ps        Fast Port Scan
  --full      Full Recon

Extra Options:
  -t T        Number of Threads [ Default : 30 ]
  -T T        Request Timeout [ Default : 30.0 ]
  -w W        Path to Wordlist [ Default : wordlists/dirb_common.txt ]
  -r          Allow Redirect [ Default : False ]
  -s          Toggle SSL Verification [ Default : True ]
  -sp SP      Specify SSL Port [ Default : 443 ]
  -d D        Custom DNS Servers [ Default : 1.1.1.1 ]
  -e E        File Extensions [ Example : txt, xml, php ]
  -m M        Traceroute Mode [ Default : UDP ] [ Available : TCP, ICMP ]
  -p P        Port for Traceroute [ Default : 80 / 33434 ]
  -tt TT      Traceroute Timeout [ Default : 1.0 ]
  -o O        Export Output [ Default : txt ] [ Available : xml, csv ]
```


Some of the modules use API keys, so if you have them put them in /conf/keys.json. The only two I saw there was Facebook and Virus Total. The website shows Shodan as well, so I added that to the keys.json file.

Check headers

```
python3 finalrecon.py --headers <url>
```

Check SSL certificate

```
python3 finalrecon.py --sslinfo <url>
```

Check Whois 

```
python3 finalrecon.py --whois <url>
```

Crawl target

```
python3 finalrecon.py --crawl <url>
```

Directory searching

```
python3 finalrecon.py --dir <url> -e txt,php -w /path/to/wordlist
```

Full scan

```
python3 finalrecon.py --full <url>
```



