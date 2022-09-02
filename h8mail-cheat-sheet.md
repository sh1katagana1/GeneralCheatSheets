# H8mail Cheat Sheet

**Description:** 
This tool is used to search Breach Data sources. It can do online searches if you have API keys, like Haveibeenpwned, but it can also search local databases as well, like CompilationOfManyBreaches

**Notes**
I added export PATH="$HOME/.local/bin:$PATH" to PATH as for some reason pip didnt install it there, so now you can just 
type h8mail -h in any terminal and it will work

UPDATE: the above wasnt working so you can run it from here:

`/usr/local/bin$ sudo ./h8mail --gen-config`

The generated h8mail template configuration file is at /usr/local/bin/h8mail-config.ini but you can save it anywhere. I created and saved the API config file at home/sh1katagana1/osint/h8mail/h8mail_config.ini

So I used theHarvester with the intelx plugin and got the list of target emails. I then run them through h8mail using the HIBP API and output it to a csv file with the command below:
```
h8mail -t /home/sh1katagana1/recon/target_emails -c /home/sh1katagana1/osint/h8mail/h8mail_config.ini -o /home/sh1katagana1/recon/pwned_targets.csv
```
When I want to use one of my local breach files, I do: 
```
h8mail -t dabluezpreacher@gmail.com -lb '5000000 Gmail.txt' -sk
```
-sk is to skip default API checks

To search emails using Compilation Of Many Breaches, I do: 
```
h8mail -t dabluezpreacher@gmail.com -sk -bc CompilationOfManyBreaches
```
I can also replace my email with a text file of emails
```
h8mail -t targets.txt -sk -bc CompilationOfManyBreaches
```
To search just by domain: 
```
h8mail -t example.com fcorp.com -sk -lb ./CompilationOfManyBreaches/ --loose
```
--loose param tells h8mail to accept any type of input, instead of enforcing the email pattern.
-lb param tells h8mail to perform a standard local breach search using multiprocessing.

To search for specific passwords: 
```
h8mail -t "Yourefired" "Another_s3cretP@ss" -sk -lb ./CompilationOfManyBreaches/ --loose
```
Query online databases for a single target
```
h8mail -t target@example.com
```
Query for list of targets, indicate config file for API keys, output to pwned_targets.csv
```
h8mail -t targets.txt -c config.ini -o pwned_targets.csv
```
Search every .gz file for targets found in targets.txt locally, skip default checks
```
h8mail -t targets.txt -gz /tmp/Collection1/ -sk
```
Check a cleartext dump for target. Add the next 10 related emails to targets to check. Read keys from CLI
```
h8mail -t admin@evilcorp.com -lb /tmp/4k_Combo.txt -ch 10 -k "hunterio=ABCDE123"
```
Fetch URL content (CLI + file). Target all found emails
```
h8mail -u "https://pastebin.com/raw/kQ6WNKqY" "list_of_urls.txt"
```
