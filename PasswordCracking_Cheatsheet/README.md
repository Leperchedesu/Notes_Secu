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
john --format=<format> target.txt --wordlist=dictionnary.txt
hashcat --username -m <mode> target.txt dictionnary.txt
 
<h3>Rules</h3>
john --format=<format> target.txt --wordlist=dictionnary.txt --rules
hashcat --username -m <mode> target.txt dictionnary.txt -r OneRuleToRuleThemAll.rule
