# CloudBrute Cheat Sheet

**Description:**

```
A tool to brute force files and directories on Cloud platforms

usage: CloudBrute [-h|--help] -d|--domain "<value>" -k|--keyword "<value>"
                  -w|--wordlist "<value>" [-c|--cloud "<value>"] [-t|--threads
                  <integer>] [-T|--timeout <integer>] [-p|--proxy "<value>"]
                  [-a|--randomagent "<value>"] [-D|--debug] [-q|--quite]
                  [-m|--mode "<value>"] [-o|--output "<value>"]
                  [-C|--configFolder "<value>"]

                  Awesome Cloud Enumerator

Arguments:

  -h  --help          Print help information
  -d  --domain        domain
  -k  --keyword       keyword used to generator urls
  -w  --wordlist      path to wordlist
  -c  --cloud         force a search, check config.yaml providers list
  -t  --threads       number of threads. Default: 80
  -T  --timeout       timeout per request in seconds. Default: 10
  -p  --proxy         use proxy list
  -a  --randomagent   user agent randomization
  -D  --debug         show debug logs. Default: false
  -q  --quite         suppress all output. Default: false
  -m  --mode          storage or app. Default: storage
  -o  --output        Output file. Default: out.txt
  -C  --configFolder  Config path. Default: config
 ```
 
Bruteforce target.com using the keyword 'target', looking for Buckets, 80 threads, timeout per request is 10 seconds and a path to the wordlist used in the brute force.
  
  `CloudBrute -d target.com -k target -m storage -t 80 -T 10 -w "./data/storage_small.txt"`
  
  If I dont know the cloud platform of the target, and I want to specify one:
  
  `CloudBrute -d target.com -k keyword -m storage -t 80 -T 10 -w -c amazon -o target_output.txt`
