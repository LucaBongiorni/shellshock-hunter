shellshock-hunter
========

Search Bing and concurrently test each result for vulnerability to CVE-2014-6271: remote code execute bug in bash otherwise known as Shellshock.

Usage
-----

``` shell
git clone https://github.com/DanMcInerney/shellshock-hunter
cd shellshock-hunter/
python shellshock-hunter -s "search_terms" -k your_bing_api_key -l number_of_results_to_check
```

-l will default to 10 results if not specified

Example
-----

``` shell
python shellshock-hunter.py -s "instreamset:(url):cgi-bin ext:sh" -k AqTGBsziZHIJYYxgivLBf0hVdrAk9mWO5cQcb8Yux8sW5M8c8opEC2lZqKR1ZZXf -l 100
```

Bing doesn't recognize inurl: like Google does so we search "instreamset:(url):cgi-bin ext:sh" to catch all results with "cgi-bin" in the URL and an extension of .sh meaning it's a bash cgi script, the best case scenario for exploiting Shellshock. -l 100 means we are going to test the top 100 results. Note the key above is fake. Get a free Bing API key at: https://datamarket.azure.com/dataset/bing/search

Output will look like:
``` shell
[!] SHELLSHOCK VULNERABLE: http://domain.com/cgi-bin/script.sh
```
