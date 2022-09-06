## DNS Recon Cheatsheet

https://github.com/darkoperator/dnsrecon

**Description**
General DNS Recon

```
usage: dnsrecon.py [-h] [-d DOMAIN] [-n NS_SERVER] [-r RANGE] [-D DICTIONARY] [-f] [-a] [-s] [-b] [-y] [-k] [-w] [-z]
                   [--threads THREADS] [--lifetime LIFETIME] [--tcp] [--db DB] [-x XML] [-c CSV] [-j JSON] [--iw]
                   [--disable_check_recursion] [--disable_check_bindversion] [-V] [-v] [-t TYPE]

optional arguments:
  -h, --help            show this help message and exit
  -d DOMAIN, --domain DOMAIN
                        Target domain.
  -n NS_SERVER, --name_server NS_SERVER
                        Domain server to use. If none is given, the SOA of the target will be used. Multiple servers can be specified using a comma separated list.
  -r RANGE, --range RANGE
                        IP range for reverse lookup brute force in formats   (first-last) or in (range/bitmask).
  -D DICTIONARY, --dictionary DICTIONARY
                        Dictionary file of subdomain and hostnames to use for brute force. Filter out of brute force domain lookup, records that resolve to the wildcard defined IP address when saving records.
  -f                    Filter out of brute force domain lookup, records that resolve to the wildcard defined IP address when saving records.
  -a                    Perform AXFR with standard enumeration.
  -s                    Perform a reverse lookup of IPv4 ranges in the SPF record with standard enumeration.
  -b                    Perform Bing enumeration with standard enumeration.
  -y                    Perform Yandex enumeration with standard enumeration.
  -k                    Perform crt.sh enumeration with standard enumeration.
  -w                    Perform deep whois record analysis and reverse lookup of IP ranges found through Whois when doing a standard enumeration.
  -z                    Performs a DNSSEC zone walk with standard enumeration.
  --threads THREADS     Number of threads to use in reverse lookups, forward lookups, brute force and SRV record enumeration.
  --lifetime LIFETIME   Time to wait for a server to respond to a query. default is 3.0
  --tcp                 Use TCP protocol to make queries.
  --db DB               SQLite 3 file to save found records.
  -x XML, --xml XML     XML file to save found records.
  -c CSV, --csv CSV     Save output to a comma separated value file.
  -j JSON, --json JSON  save output to a JSON file.
  --iw                  Continue brute forcing a domain even if a wildcard record is discovered.
  --disable_check_recursion
                        Disables check for recursion on name servers
  --disable_check_bindversion
                        Disables check for BIND version on name servers
  -V, --version         Show DNSrecon version
  -v, --verbose         Enable verbose
  -t TYPE, --type TYPE  Type of enumeration to perform.
                        Possible types:
                            std:      SOA, NS, A, AAAA, MX and SRV.
                            rvl:      Reverse lookup of a given CIDR or IP range.
                            brt:      Brute force domains and hosts using a given dictionary.
                            srv:      SRV records.
                            axfr:     Test all NS servers for a zone transfer.
                            bing:     Perform Bing search for subdomains and hosts.
                            yand:     Perform Yandex search for subdomains and hosts.
                            crt:      Perform crt.sh search for subdomains and hosts.
                            snoop:    Perform cache snooping against all NS servers for a given domain, testing
                                      all with file containing the domains, file given with -D option.
                        
                            tld:      Remove the TLD of given domain and test against all TLDs registered in IANA.
                            zonewalk: Perform a DNSSEC zone walk using NSEC records.
```

Basic usage

```
python3 dnsrecon.py -d leroyjenkins.com
```

Zone Transfer attempt

```
python3 dnsrecon.py -d leroyjenkins.com -a
```
