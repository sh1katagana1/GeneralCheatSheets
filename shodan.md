# Shodan Usage

Find devices in a particular city.
```
city:Austin
```
Find devices in a particular country. 
```
country:IN
```
Find devices by giving geographical coordinates.
```
geo:37.702152,-121.935791
```
Find devices matching the hostname
```
hostname:example.com
```
```
hostname:example.com,example.org
```
Find devices based on an IP address or /x CIDR
```
net:210.214.0.0/16
```
Find by organization name
```
org:microsoft
```
Find by Operating system
```
os:"windows 7"
```
Find devices based on port
```
proftpd port:21
```
Find SSL certs that are expired
```
ssl.cert.expired:true
```
```
ssl.cert.expired:true hostname:trinet.com
```
Search by device type
```
device:firewall
```
```
device:router
```
```
device:printer
```
Find devices by server type
```
server:nginx hostname:trinet.com
```

## Shodan CLI

Install
```
pip install -U --user shodan
```
Confirm its installed
```
shodan
```
Put in your API key
```
shodan init YOUR_API_KEY
```
General searching. Usage: shodan search [OPTIONS] <search query>
```
shodan search nginx
```
Download the results. shodan download [OPTIONS] <filename> <search query> You have to use the format json.tgz
```
shodan download --limit 500 4-51-172-176-28.json.gz net:4.51.172.176/25
```
Convert to Excel from the json.tgz. shodan convert <data file> <file format>
```
shodan convert 4-51-172-176-28.json.gz xlsx
```



