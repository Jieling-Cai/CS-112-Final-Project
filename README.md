# CS-112-Final-Project: High Performance HTTP Proxy
Build an HTTP Proxy from scratch in C, supporting the following functionalities:
```bash
1. Support GET and CONNECT methods to process HTTP and HTTPS requests concurrently.
2. Ability to handle multiple clients at the same time.
3. Implement caching to facilitate the process of fetching contents. Cache policy includes evicting stale and LRU cached items when full.
4. Trusted proxy/SSL(TLS) inspection: Make proxy trusted by the clients (using a self-signed certificate), so it can handle SSL(TLS) connections to decrypt contents in HTTPS. 
5. Bandwidth limiting.  
6. Host blocking as a firewall.
7. Error handling and Unit testing (using CUnit).
```

## Dependencies 
Use the package manager [apt-get](https://linux.die.net/man/8/apt-get) to install Openssl and Openssl development package
```bash
sudo apt update
sudo apt upgrade
sudo apt-get install libssl-dev
```

## Configuration of browser
Before using proxy, set up the browser first. Take Firefox as an example:
```bash
Enter "about:config" into the address bar, proceed and search:    
    * "security.enterprise_roots.enabled" -change it to be true  
    * "network.stricttransportsecurity.preloadlist" -change it to be false  

Enter "about:preferences" into the address bar:    
    * In the "General" setting, find the "Network Settings" and proceed to set up proxy  
    * In the "Privacy & Security" setting, find "Cookies and Site Data" block and click on "Clear Data" tab.  
      Tick the checkbox "Delete cookies and site data when Firefox is closed"  
    * In the "History" setting, choose "Never remember history" option
```

## Usage
```bash
make
# Flag = 1 : enable trusted proxy, Flag = 0 : disable trusted proxy.
# Blocklist : list of hostnames that proxy wants to block, separated by comma ("NA" for not blocking). e.g: "www.tufts.com,www.youtube.com" /"www.tufts.com"/"NA"
# BandwidthLimit: The bandwidth that proxy wants to limit for one client, unit: Bytes per second
./a.out port Flag Blocklist BandwidthLimit
```

## Contributing
Jieling Cai, Kailin Zhang, Xiaoxiong Huang
