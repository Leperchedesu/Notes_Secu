# Tools :  
- Hashcat / john <br/> 
- hashid  <br/>
- cewl : creates wordlist by crawling websites <br/>
ex : cewl -d 5 -w wordlist.txt http://website.com/  <br/>
(d : depth of the crawling)  <br/>
- cupp : creates password lists from OSINT informations  <br/>
<br>
- fcrackzip : for cracking zip passwords  

# Wordlists   
- username=password  <br/>
- rockyou  <br/>
- richelieu for french targets <br/>
- SecLists (https://github.com/danielmiessler/SecLists)  <br/>
<br>

# Rules   
OneRuleToRuleThemAll : https://github.com/NotSoSecure/password_cracking_rules/blob/master/OneRuleToRuleThemAll.rule  <br/>
<br>

# Cheatsheet  
### Dictionnary   
<code>john --format=<format> hash.txt --wordlist=/usr/share/wordlists/rockyou.txt</code><br>
<code>hashcat --username -m <mode> hash.txt /usr/share/wordlists/rockyou.txt</code><br>

### Rules   
<code>john --format=<format> hash.txt --wordlist=/usr/share/wordlists/rockyou.txt --rules</code><br>
<code>hashcat --username -m <mode> hash.txt /usr/share/wordlists/rockyou.txt -r OneRuleToRuleThemAll.rule</code><br>

### Zip cracking  
 <code>fcrackzip -v -u -D -p /usr/share/wordlists/rockyou.txt <file_to_crack>.zip</code>
 
