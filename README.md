# Checkmk - Authenticated Arbitrary File Read
This exploit abuses an authenticated arbitrary file read in Checkmk <= 2.1.0p10, Checkmk <= 2.0.0p27 because in older versions it used NagVis with a version <1.9.34. 

This exploit uses the getHoverUrl action in /ajax_handler.php. This exploit can be chained with other exploits in the vulnerable versions for unauthenticated remote code execution as described in the following series of articles: https://www.sonarsource.com/blog/checkmk-rce-chain-1/

NOTE: This exploit requires that the mbstring extension is installed in Apache for the Checkmk instance. This extension is not installed in the Checkmk official container by default. You can enable this extension with the following commands. 
```
apt update && apt install php-mbstring -y
sed -i 's/;extension=mbstring/extension=mbstring/g' /etc/php/7.3/cli/php.ini
omd restart
```

DISCLAIMER: This script is made to audit the security of systems. Only use this script on your own systems or on systems you have written permission to exploit.

