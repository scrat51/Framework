How to use it ?

Help menu
---------

python xss_scanner_advanced.py -h
Usage: xss_scanner_advanced.py [options]

Options:
  --version          show program's version number and exit
  -h, --help         show this help message and exit
  -u URL, --url=URL  Target URL (e.g. "http://www.target.com/page.htm?id=1")
  --data=DATA        POST data (e.g. "query=test")
  --cookie=COOKIE    HTTP Cookie header value
  --user-agent=UA    HTTP User-Agent header value
  --referer=REFERER  HTTP Referer header value
  --proxy=PROXY      HTTP proxy address (e.g. "http://127.0.0.1:8080")
```

```
$ python xss_scanner_advanced.py -u "http://testphp.vulnweb.com/search.php?test=query" --data="s
earchFor=foobar"

* scanning GET parameter 'test'
* scanning POST parameter 'searchFor'
 (i) POST parameter 'searchFor' appears to be XSS vulnerable (">.xss.<", outside
 of tags, no filtering)

scan results: possible vulnerabilities found
```

```
$ python xss_scanner_advanced.py -u "http://public-firing-range.appspot.com/address/location.has
h/replace"

 (i) page itself appears to be XSS vulnerable (DOM)
  (o) ...<script>
      var payload = window.location.hash.substr(1);location.replace(payload); 

    </script>...
 (x) no usable GET/POST parameters found

scan results: possible vulnerabilities found
```

Requirements
Python 2.6 or 2.7
