# OnionSearch

**Description:**
This queries a multitude of Dark Web search engines at once for specific keywords

**Notes**
As .onion addresses cannot be reached without going through Tor, we need to have Tor installed (not just the Tor Browser)

First we start Tor

`service tor start`

Then we verify its running with:

`service tor status`

Next we search for a key term using all search engines and using Tor proxy

`onionsearch --proxy 127.0.0.1:9050 "Conti"`

To request all the engines excepted "Ahmia" and "Candle" for the word "computer":

`onionsearch "computer" --exclude ahmia candle`

To request only "Tor66", "DeepLink" and "Phobos" for the word "computer":

`onionsearch "computer" --engines tor66 deeplink phobos`

The same as previously but limiting to 3 the number of pages to load per engine:

`onionsearch "computer" --engines tor66 deeplink phobos --limit 3`

**Output**
By default, the file is written at the end of the process. The file will be csv formatted, containing the following columns:

`"engine","name of the link","url"`

You can customize what will be flush in the output file by using the parameters --fields and --field_delimiter. You can for instance choose to output:

`"engine","name of the link","url","domain"`

By using this switch:

`--fields engine name link domain`

The filename will be set by default to output_$DATE_$SEARCH.txt, where $DATE represents the current datetime and $SEARCH the first characters of the search string. You can modify this filename by using --output when running the script, for instance:

`onionsearch "computer" --output "\$DATE.csv"`

`onionsearch "computer" --output output.txt`

`onionsearch "computer" --output "\$DATE_\$SEARCH.csv"`


