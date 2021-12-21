# For password cracking/bruteforcing :
- cewl : creates wordlist by crawling websites
ex : cewl -d 5 -w wordlist.txt http://website.com/
(d : depth of the crawling)
- cupp : creates password lists from OSINT informations
- Rules : best64.rule + https://github.com/praetorian-inc/Hob0Rules + OneRuleTo$
ex : $ hashcat -a 0 -m <hash_type> <hash> <wordlist> -r <rule>
