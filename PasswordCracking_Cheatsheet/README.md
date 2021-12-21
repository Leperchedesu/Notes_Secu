<h1># Tools :</h1>  
- Hashcat / john      
- hashid  
- cewl : creates wordlist by crawling websites 
ex : cewl -d 5 -w wordlist.txt http://website.com/  
(d : depth of the crawling)  
- cupp : creates password lists from OSINT informations  
  
<h1># Wordlists</h1>  
- username=password  
- rockyou  
- SecLists (https://github.com/danielmiessler/SecLists)  
    
<h1># Rules</h1>   
OneRuleToRuleThemAll : https://github.com/NotSoSecure/password_cracking_rules/blob/master/OneRuleToRuleThemAll.rule  
  
<h1># Cheatsheet</h1>  
<h3>Dictionnary</h3>  
<h5>Hashcat</h5>  
`hashcat -a 0 -m <hash_type> <hash> <wordlist> -r <rule>`  
`hashcat --username -m <mode> hash.txt dictionnary.txt`  
<h5>John</h5>  
`john --format=<format> hash.txt --wordlist=dictionnary.txt`  
