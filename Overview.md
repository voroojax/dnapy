A multi-processed framework consisting of multiple extensions used to detect anomalies in domain names.

Primarily designed to work with DNS, but extension to other protocols is trivial (blacklisted domain/ip extension is completely agnostic, and has been used in combination with dpkt http parser as well).


Known White & Black listed IP's and Domains
-Domain inspection system that mimics a DNS tree, allowing for complex signatures segregated by sub-domains.
-bit-level ip "binary tree" for ip based signatures.
-Regex support planned.


whois information analysis
-planned support for using whios/nslookup records in understanding the nature of a domain
-for example, active domains older than 1 year are less likely to be malicious


domain name analysis
-vowel analysis: ratio vow/con, no vowels, placement of vowels, etc
-number analysis: ratio num/length, placement of numbers
-character frequency: how closely a domain resembles the english language using ZIPF'S Law and n-gram analysis.


DNS answer analysis (DNS specific)
-relation maps: domain-IP-domain
-TTL values: number of distinct TTL values, average TTL, etc...
-alias analysis: number of aliases reported


beacon detection
-utilizing CUSUM algorithm to detect DNS beaconing


analysis fusion
utilize above features together to detect fast-flux botnets with random name generation
example 1:
-recognizing an anomalous domain zzzzftd.com
-finding the related domain-ip-domain map,
-treat all related domains as one "entity"
-recalculating the beaconing frequency to find patterns
example 2:
-detect known blacklisted domain in dns request
-read dns query response, add ip into "suspect ip" list
-flag future traffic based on meta-data, which leads to streamlined detection of HTTP/SSL/FTP/anything that utilizes the DNS system for resolution but not for C&C.


most of the work is based on the white papers:
-"EXPOSURE: Finding Malicious Domains Using Passive DNS Analysis"
--http://iseclab.org/papers/bilge-ndss11.pdf
-"Detecting DNS Tunnels Using Character Frequency Analysis"
--http://arxiv.org/ftp/arxiv/papers/1004/1004.4358.pdf

others, to be added as updated.