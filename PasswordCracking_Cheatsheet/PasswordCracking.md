# Tools :  
- Hashcat / john <br/> 
- hashid  <br/>
- LDAPWordlistHarvester : https://github.com/p0dalirius/LDAPWordlistHarvester   
- cewl : creates wordlist by crawling websites <br/>
ex : cewl -d 5 -w wordlist.txt http://website.com/  <br/>
(d : depth of the crawling)  <br/>
- cupp : creates password lists from OSINT informations  <br/>
<br>
- fcrackzip : for cracking zip passwords  

# Wordlists   
- Wordlist for french targets: https://github.com/clem9669/wordlists  <br/>
- For internal pentests: https://github.com/p0dalirius/LDAPWordlistHarvester <br/>
- username=password  <br/>
- rockyou  <br/>
- richelieu for french targets <br/>
- SecLists (https://github.com/danielmiessler/SecLists)  <br/>

<br>

# Rules   
- OneRuleToRuleThemAll: https://github.com/NotSoSecure/password_cracking_rules/blob/master/OneRuleToRuleThemAll.rule  <br/>
- Rules for companies: https://github.com/clem9669/hashcat-rule (https://github.com/clem9669/hashcat-rule/blob/master/clem9669_large.rule) <br/>  
<br>

# Cheatsheet  
### Dictionnary   
<code>john --format=md5 hash.txt --wordlist=/usr/share/wordlists/rockyou.txt</code><br>
<code>hashcat --username -m 1800 -o found1.txt hash.txt /usr/share/wordlists/rockyou.txt</code><br>

### Rules   
<code>john --format=md5 hash.txt --wordlist=/usr/share/wordlists/rockyou.txt --rules</code><br>
<code>hashcat --username -m 1800 -o found1.txt hash.txt /usr/share/wordlists/rockyou.txt -r OneRuleToRuleThemAll.rule</code><br>
Exemple for TGS : <code>hashcat -m 13100 --force -o found1.txt kerberoastables.txt wordlist_concat_client.txt -r OneRuleToRuleThemAll.rule</code><br>


### Zip cracking  
 <code>fcrackzip -v -u -D -p /usr/share/wordlists/rockyou.txt file_to_crack.zip</code>
 
