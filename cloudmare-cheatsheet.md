## Cloudmare Cheat Sheet

https://github.com/mrh0wl/Cloudmare

**Description**
Cloudmare is a simple tool to find the origin servers of websites protected by Cloudflare, Sucuri or Incapsula with a misconfiguration DNS.

```
usage: Example: python Cloudmare.py -u site.com

optional arguments:
  -h, --help                                           show this help message and exit
  --hh, --help-hack                                    Show advanced help message and exit
  --version                                            Show program's version number and exit
  -v                                                   Verbosity for sublist3r: True/False (default: False)

Target:
  At least one of these options has to be provided to define the target(s)

  -u target, --url target                              Target URL as first argument (e.g. python Cloudmare.py site.com)
  --disable-sublister                                  Disable subdomain listing for testing
  --bruter                                             Bruteforcing target to find associated domains
  --subbruter                                          Bruteforcing target's subdomains using subbrute module

Request:
  These options can be used to specify how to connect to the target URL

  --user-agent UAGENT                                  Set HTTP User-Agent header value
  --random-agent                                       Set randomly selected HTTP User-Agent header value
  --host HOST                                          HTTP Host header value
  --headers HEADERS                                    Set custom headers (e.g. "Origin: originwebsite.com, ETag: 123")
  --ignore-redirects                                   Ignore Redirection attempts
  --threads [THREADS]                                  Max number of concurrent HTTP(s) requests (default 1)

Search:
  These options can be used to perform advanced searches

  -sC [CENSYS], --search-censys [CENSYS]               Perform search using Censys API
  -sSh [SHODAN], --search-shodan [SHODAN]              Perform search using Shodan API
  -sSt [SECURITYTRAILS], --search-st [SECURITYTRAILS]  Perform search using Securitytrails API

Output:
  These options can be used to save the subdomains results

  -o, --output                                         Save the subdomains into: "data/output/subdomains-from-[domain].txt"
  --oG, --output-good                                  Save [good response] subdomains into: "data/output/good-subdomains-
                                                       from-[domain].txt"
  --oI, --output-ip                                    Save subdomains IP into: "data/output/good-subdomains-from-[domain].txt"

```
To use the API options, you need to go to the Cloudmare folder /data/APIS/api.conf and enter in your APIs


Basic usage

```
python Cloudmare.py -u target.site --bruter -sC -sSh -sSt --host verified.site
```

