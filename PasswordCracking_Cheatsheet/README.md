<h1># Tools :</h1>  
- Hashcat / john <br/> 
- hashid  <br/>
- cewl : creates wordlist by crawling websites <br/>
ex : cewl -d 5 -w wordlist.txt http://website.com/  <br/>
(d : depth of the crawling)  <br/>
- cupp : creates password lists from OSINT informations  <br/>
  
<h1># Wordlists</h1>  
- username=password  <br/>
- rockyou  <br/>
- SecLists (https://github.com/danielmiessler/SecLists)  <br/>
    
<h1># Rules</h1>   
OneRuleToRuleThemAll : https://github.com/NotSoSecure/password_cracking_rules/blob/master/OneRuleToRuleThemAll.rule  <br/>
  
<h1># Cheatsheet</h1>  
<h3>Dictionnary</h3>  
<h5>Hashcat</h5>  
`hashcat -a 0 -m <hash_type> <hash> <wordlist> -r <rule>`  <br/>
`hashcat --username -m <mode> hash.txt dictionnary.txt`  <br/>
<h5>John</h5>  
`john --format=<format> hash.txt --wordlist=dictionnary.txt`  <br/>
