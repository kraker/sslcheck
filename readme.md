# SSL/HTTPS Checker #

Script to check the SSL status of a site in the CLI.

Designed to give similar output to these web-based tools:
- https://www.sslshopper.com/ssl-checker.html
- https://www.whynopadlock.com/

_Note: this script is a work in progress._


## Install ##

_*Note: install for Linux based distros._

```
wget -O ~/bin/ssl-check https://raw.githubusercontent.com/kraker/ssl-checker/master/ssl-check
chmod +x ~/bin/ssl-check
```
_You might need to source your `.bashrc` to load the script on your $PATH._
```
source ~/.bashrc
```

## Usage ##
```
ssl-check domain.com
```

Example:
```
[akraker@localhost]$ ssl-check kraker.dev
The kraker.dev domain name seems valid

# The SSL certificate has been issued for:
Domain: C = US, ST = CA, L = San Francisco, O = "Cloudflare, Inc.", CN = sni.cloudflaressl.com
----

# Force HTTPS:
Webserver is forcing HTTPS
----

# The SSL certificate expires in:
362 days
----

# Dates:
Issued On: Dec 22 00:00:00 2020 GMT
Expires On: Dec 21 23:59:59 2021 GMT
----

# The certificate has been issued by:
Issuer: C = US, O = "Cloudflare, Inc.", CN = Cloudflare Inc ECC CA-3
----

# Fingerprint:
SHA1 Fingerprint=D0:F7:58:14:5D:FF:F9:3C:F3:F9:D6:5C:B4:BF:CB:45:D4:77:8F:98
----

# Mixed Content:
Website has no Mixed Content

* This is a rudimentary check for mixed content, javascript needs to be executed
(among other things) for a more complete diagnostic.
```

## TODO ##

_Note: the mixed content checker is proving more difficult than anticipated and is still a work in progress.  To truely do this right, you probably need some kind of headless browser that not only parses and renders the HTML/CSS, but the JavaScript, and then gets whatever assets those things request. If even a single one of those assets comes from a non-HTTPS URL, then Mixed Content is broken. Right now this tool has a crude Mixed Content check that uses `wget` to mirror the page and then `grep` 's for instances of HTTP URLs. I may get around to fixing this sometime in the future, but a headless browser seems a bit heavy for a what was supposed to be a simple bash script._

## Acknowledgements ##

Large portions of this script adapted and refactored from:
https://github.com/bobbyiliev/bash-ssl-checker-tool



