# Grep

If I have a file containing all uppercase victim names from a ransomware blog and I have a list of lowercase vendor names for my company and I would like to see if any of the victims match any of my vendors, I would use egrep -f and -i for case insensitivity. Normal grep works as well, but I found that it doesnt give results of matched words if there are more words in the same line, so it appears to search based on line.

```
egrep -f file1.txt file2.txt -i
```
