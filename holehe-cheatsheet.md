## Holehe Cheatsheet

https://github.com/megadose/holehe

**Description**
Holehe checks if an email is attached to an account on sites like twitter, instagram, imgur and more than 120 others.

```
usage: holehe [-h] [--only-used] [--no-color] [--no-clear] [-NP] [-C] [-T TIMEOUT] EMAIL [EMAIL ...]

holehe v1.61

positional arguments:
  EMAIL                 Target Email

optional arguments:
  -h, --help            show this help message and exit
  --only-used           Displays only the sites used by the target email address.
  --no-color            Don't color terminal output
  --no-clear            Do not clear the terminal to display the results
  -NP, --no-password-recovery
                        Do not try password recovery on the websites
  -C, --csv             Create a CSV with the results
  -T TIMEOUT, --timeout TIMEOUT
                        Set max timeout value (default 10)
```

Basic usage

```
holehe test@gmail.com
```


