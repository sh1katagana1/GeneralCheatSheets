## Cloud Enum Cheat Sheet

https://github.com/initstring/cloud_enum

**Description:**
Multi-cloud OSINT tool. Enumerate public resources in AWS, Azure, and Google Cloud.

```
usage: cloud_enum.py [-h] -k KEYWORD [-m MUTATIONS] [-b BRUTE]

Multi-cloud enumeration utility. All hail OSINT!

optional arguments:
  -h, --help            show this help message and exit
  -k KEYWORD, --keyword KEYWORD
                        Keyword. Can use argument multiple times.
  -kf KEYFILE, --keyfile KEYFILE
                        Input file with a single keyword per line.
  -m MUTATIONS, --mutations MUTATIONS
                        Mutations. Default: enum_tools/fuzz.txt
  -b BRUTE, --brute BRUTE
                        List to brute-force Azure container names. Default: enum_tools/fuzz.txt
  -t THREADS, --threads THREADS
                        Threads for HTTP brute-force. Default = 5
  -ns NAMESERVER, --nameserver NAMESERVER
                        DNS server to use in brute-force.
  -l LOGFILE, --logfile LOGFILE
                        Will APPEND found items to specified file.
  -f FORMAT, --format FORMAT
                        Format for log file (text,json,csv - defaults to text)
  --disable-aws         Disable Amazon checks.
  --disable-azure       Disable Azure checks.
  --disable-gcp         Disable Google checks.
  -qs, --quickscan      Disable all mutations and second-level scans
  
  ```
  



The only required argument is at least one keyword. You can use the built-in fuzzing strings, but you will get better results if you supply your own with -m and/or -b. You can provide multiple keywords by specifying the -k argument multiple times.

```
./cloud_enum.py -k somecompany -k somecompany.io -k leroyjenkins.com

```
I can increase the thread count as well, but be wary of cloud providers throttling after a certain amount

```
./cloud_enum.py -k keyword -t 10
```




