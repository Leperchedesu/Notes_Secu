<h1># Tools :</h1>  
- Hashcat / john <br/> 
- hashid  <br/>
- cewl : creates wordlist by crawling websites <br/>
ex : cewl -d 5 -w wordlist.txt http://website.com/  <br/>
(d : depth of the crawling)  <br/>
- cupp : creates password lists from OSINT informations  <br/>
<br>

<h1># Wordlists</h1>  
- username=password  <br/>
- rockyou  <br/>
- SecLists (https://github.com/danielmiessler/SecLists)  <br/>
<br>

<h1># Rules</h1>   
OneRuleToRuleThemAll : https://github.com/NotSoSecure/password_cracking_rules/blob/master/OneRuleToRuleThemAll.rule  <br/>
<br>

<h1># Cheatsheet</h1>  
<h3>Dictionnary</h3>  
<code>john --format=&lt;format&gt; target.txt --wordlist=dictionnary.txt</code><br>
<code>hashcat --username -m &lt;mode&gt; target.txt dictionnary.txt</code><br>
<h3>Rules</h3>
<code>john --format=&lt;format&gt; target.txt --wordlist=dictionnary.txt --rules</code><br>
<code>hashcat --username -m &lt;mode&gt; target.txt dictionnary.txt -r OneRuleToRuleThemAll.rule</code><br>
