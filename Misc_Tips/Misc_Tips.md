## Find the meaning of unknown error codes with certutil:
`Certutil -error <error_id>`

## Access HTTPS proxy with proxychains:
Proxychains supports SOCKS4, SOCKS5 and HTTP but not HTTPS.  
Using socat to create an HTTPS tunnel between a local port and a remote proxy:  
`socat TCP-LISTEN:19999,bind=127.0.0.1,fork,reuseaddr OPENSSL:proxy.yolo.com:8000,verify=0`  
(verify=0 to bypass certificate errors, example self-signed client certificate)  

Then in `/etc/proxychains.conf` :
`http 127.0.0.1 19999`

From <https://github.com/rofl0r/proxychains-ng/issues/337> 
