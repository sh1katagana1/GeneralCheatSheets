## Cloudflair Cheatsheet

https://github.com/christophetd/CloudFlair

**Description:**
CloudFlair is a tool to find origin servers of websites protected by CloudFlare who are publicly exposed and don't restrict network access to the CloudFlare IP ranges as they should.

```
usage: cloudflair.py [-h] [-o OUTPUT_FILE] [--censys-api-id CENSYS_API_ID]
                     [--censys-api-secret CENSYS_API_SECRET]
                     domain

positional arguments:
  domain                The domain to scan

optional arguments:
  -h, --help            show this help message and exit
  -o OUTPUT_FILE, --output OUTPUT_FILE
                        A file to output likely origin servers to (default:
                        None)
  --censys-api-id CENSYS_API_ID
                        Censys API ID. Can also be defined using the
                        CENSYS_API_ID environment variable (default: None)
  --censys-api-secret CENSYS_API_SECRET
                        Censys API secret. Can also be defined using the
                        CENSYS_API_SECRET environment variable (default: None
```

If you have Censys.io API keys, add them like this:

```
$ export CENSYS_API_ID=...
$ export CENSYS_API_SECRET=...
```

Basic usage:

```
python cloudflair.py myvulnerable.site
```


