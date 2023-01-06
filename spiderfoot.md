# Spiderfoot

**Description:** SpiderFoot is an open source intelligence (OSINT) automation tool. It integrates with just about every data source available and utilises a range of methods for data analysis, making that data easy to navigate.

To install, follow the instructions <a href="https://github.com/smicallef/spiderfoot">here</a>
<hr>

To run the webserver for it, navigate to your Spiderfoot directory and type:

```
python3 ./sf.py -l 127.0.0.1:5001

```

```
usage: sf.py [-h] [-d] [-l IP:port] [-m mod1,mod2,...] [-M] [-C scanID] [-s TARGET] [-t type1,type2,...]
             [-u {all,footprint,investigate,passive}] [-T] [-o {tab,csv,json}] [-H] [-n] [-r] [-S LENGTH] [-D DELIMITER]
             [-f] [-F type1,type2,...] [-x] [-q] [-V] [-max-threads MAX_THREADS]

SpiderFoot 4.0.0: Open Source Intelligence Automation.

options:
  -h, --help            show this help message and exit
  -d, --debug           Enable debug output.
  -l IP:port            IP and port to listen on.
  -m mod1,mod2,...      Modules to enable.
  -M, --modules         List available modules.
  -C scanID, --correlate scanID
                        Run correlation rules against a scan ID.
  -s TARGET             Target for the scan.
  -t type1,type2,...    Event types to collect (modules selected automatically).
  -u {all,footprint,investigate,passive}
                        Select modules automatically by use case
  -T, --types           List available event types.
  -o {tab,csv,json}     Output format. Tab is default.
  -H                    Don't print field headers, just data.
  -n                    Strip newlines from data.
  -r                    Include the source data field in tab/csv output.
  -S LENGTH             Maximum data length to display. By default, all data is shown.
  -D DELIMITER          Delimiter to use for CSV output. Default is ,.
  -f                    Filter out other event types that weren't requested with -t.
  -F type1,type2,...    Show only a set of event types, comma-separated.
  -x                    STRICT MODE. Will only enable modules that can directly consume your target, and if -t was
                        specified only those events will be consumed by modules. This overrides -t and -m options.
  -q                    Disable logging. This will also hide errors!
  -V, --version         Display the version of SpiderFoot and exit.
  -max-threads MAX_THREADS
                        Max number of modules to run concurrently.

```



To use the CLI, you need to first know what the modules are named. To find this type:

```
python3 sf.py -M
```

To run in Scan mode, I can use this (The -q is to just return the data not the debug info):

```
python3 sf.py -m sfp_dnsresolve -s binarypool.com -q
```

To run every single module:

```
python3 sf.py -s binarypool.com -q
```

List all available Types:

```
python3 sf.py -T
```

Types can be used when you want to pull out just a specific type of data. For example, if you wanted just an email address

```
python3 sf.py -s spiderfoot.net -t EMAILADDR -f -x -q
```



