## Email Harvester Cheatsheet

https://github.com/maldevel/EmailHarvester

**Description** 
A tool to retrieve Domain email addresses from Search Engines

```
usage: EmailHarvester.py [-h] [-d DOMAIN] [-s FILE] [-e ENGINE] [-l LIMIT]
                         [-u USER-AGENT] [-x PROXY] [--noprint]

 _____                   _  _   _   _                                _
|  ___|                 (_)| | | | | |                              | |
| |__  _ __ ___    __ _  _ | | | |_| |  __ _  _ __ __   __ ___  ___ | |_  ___  _ __
|  __|| '_ ` _ \  / _` || || | |  _  | / _` || '__|\ \ / // _ \/ __|| __|/ _ \| '__|
| |___| | | | | || (_| || || | | | | || (_| || |    \ V /|  __/\__ \| |_|  __/| |
\____/|_| |_| |_| \__,_||_||_| \_| |_/ \__,_||_|     \_/  \___||___/ \__|\___||_|

    A tool to retrieve Domain email addresses from Search Engines | @maldevel
                                Version: 1.3.2

optional arguments:
  -h, --help            show this help message and exit
  -d DOMAIN, --domain DOMAIN
                        Domain to search.
  -s FILE, --save FILE  Save the results into a TXT and XML file (both).
  -e ENGINE, --engine ENGINE
                        Select search engine(google, bing, yahoo, ask, all).
  -l LIMIT, --limit LIMIT
                        Limit the number of results.
  -u USER-AGENT, --user-agent USER-AGENT
                        Set the User-Agent request header.
  -x PROXY, --proxy PROXY
                        Setup proxy server (example: http://127.0.0.1:8080)
  --noprint             EmailHarvester will print discovered emails to terminal. 
						It is possible to tell EmailHarvester not to print results to terminal with this option.
  -r EXCLUDED_PLUGINS, --exclude EXCLUDED_PLUGINS
                        Plugins to exclude when you choose 'all' for search engine (eg. '-r google,twitter')
  -p, --list-plugins    List all available plugins.
```

Basic search using Google

```
python3 EmailHarvester.py -d example.com -e google
```

Basic search using all engines

```
python3 EmailHarvester.py -d example.com -e all
```

Limit the results

```
python3 EmailHarvester.py -d example.com -e all -l 200
```

Search all engines but exclude some

```
python3 EmailHarvester.py -d example.com -e all -r twitter,ask
```

Export

```
python3 EmailHarvester.py -d example.com -e all -s emails.txt
```

Custom User Agent

```
python3 EmailHarvester.py -d example.com -e all -u "MyUserAgentString 1.0"
```

Use a Proxy server

```
python3 EmailHarvester.py -d example.com -e all -x http://127.0.0.1:8080
```







