# Nmap-Cheat-Sheet

Reference guide for scanning networks with Nmap.

Table of Contents

What is Nmap?
How to Use Nmap
Command Line
Basic Scanning Techniques
Scan a Single Target
Scan Multiple Targets
Scan a List of Targets
Scan a Range of Hosts
Scan an Entire Subnet
Scan Random Hosts
Exclude Targets From a Scan
Exclude Targets Using a List
Perform an Aggresive Scan
Scan an IPv6 Target
Port Scanning Options
Perform a Fast Scan
Scan Specific Ports
Scan Ports by Name
Scan Ports by Protocol
Scan All Ports
Scan Top Ports
Perform a Sequential Port Scan
Attempt to Guess an Unknown OS
Service Version Detection
Troubleshoot Version Scan
Perform a RPC Scan
Discovery Options
Perform a Ping Only Scan
Do Not Ping
TCP SYN Ping
TCP ACK Ping
UDP Ping
SCTP INIT Ping
ICMP Echo Ping
ICMP Timestamp Ping
ICMP Address Mask Ping
IP Protocol Ping
ARP Ping
Traceroute
Force Reverse DNS Resolution
Disable Reverse DNS Resolution
Alternative DNS Lookup
Manually Specify DNS Server
Create a Host List
Firewall Evasion Techniques
Fragment Packets
Specify a Specific MTU
Use a Decoy
Idle Zombie Scan
Manually Specify a Source Port
Append Random Data
Randomize Target Scan Order
Spoof MAC Address
Send Bad Checksums
Advanced Scanning Functions
TCP SYN Scan
TCP Connect Scan
UDP Scan
TCP NULL Scan
TCP FIN Scan
Xmas Scan
TCP ACK Scan
Custom TCP Scan
IP Protocol Scan
Send Raw Ethernet Packets
Send IP Packets
Timing Options
Timing Templates
Set the Packet TTL
Minimum Number of Parallel Operations
Maximum Number of Parallel Operations
Minimum Host Group Size
Maximum Host Group Size
Maximum RTT Timeout
Initial RTT TImeout
Maximum Number of Retries
Host Timeout
Minimum Scan Delay
Maximum Scan Delay
Minimum Packet Rate
Maximum Packet Rate
Defeat Reset Rate Limits
Output Options
Save Output to a Text File
Save Output to a XML File
Grepable Output
Output All Supported File Types
Periodically Display Statistics
1337 Output
Compare Scans
Comparison Using Ndiff
Ndiff Verbose Mode
XML Output Mode
Troubleshooting and Debugging
Get Help
Display Nmap Version
Verbose Output
Debugging
Display Port State Reason
Only Display Open Ports
Trace Packets
Display Host Networking
Specify a Network Interface
Nmap Scripting Engine
Execute Individual Scripts
Execute Multiple Scripts
Execute Scripts by Category
Execute Multiple Script Categories
Troubleshoot Scripts
Update the Script Database
What is Nmap?
Nmap ("Network Mapper") is a free and open source utility for network discovery and security auditing. Many systems and network administrators also find it useful for tasks such as network inventory, managing service upgrade schedules, and monitoring host or service uptime. Nmap uses raw IP packets in novel ways to determine what hosts are available on the network, what services (application name and version) those hosts are offering, what operating systems (and OS versions) they are running. It was designed to rapidly scan large networks, but works fine against single hosts.

How to Use Nmap
Nmap can be used in a variety of ways depending on the user's level of technical expertise.

Technical Expertise	Usage
Beginner	Zenmap the graphical user interface for Nmap
Intermediate	Command line
Advanced	Python scripting with the Python-Nmap package
Command Line
nmap [ <Scan Type> ...] [ <Options> ] { <target specification> }
Basic Scanning Techniques
The -s switch determines the type of scan to perform.

Nmap Switch	Description
-sA	ACK scan
-sF	FIN scan
-sI	IDLE scan
-sL	DNS scan (a.k.a. list scan)
-sN	NULL scan
-sO	Protocol scan
-sP	Ping scan
-sR	RPC scan
-sS	SYN scan
-sT	TCP connect scan
-sW	Windows scan
-sX	XMAS scan
Scan a Single Target
nmap [target]
Scan Multiple Targets
nmap [target1, target2, etc]
Scan a List of Targets
nmap -iL [list.txt]
Scan a Range of Hosts
nmap [range of IP addresses]
Scan an Entire Subnet
nmap [ip address/cdir]
Scan Random Hosts
nmap -iR [number]
Exclude Targets From a Scan
nmap [targets] --exclude [targets]
Exclude Targets Using a List
nmap [targets] --excludefile [list.txt]
Perform an Aggresive Scan
nmap -A [target]
Scan an IPv6 Target
nmap -6 [target]
Port Scanning Options
Perform a Fast Scan
nmap -F [target]
Scan Specific Ports
nmap -p [port(s)] [target]
Scan Ports by Name
nmap -p [port name(s)] [target]
Scan Ports by Protocol
nmap -sU -sT -p U:[ports],T:[ports] [target]
Scan All Ports
nmap -p 1-65535 [target]
Scan Top Ports
nmap --top-ports [number] [target]
Perform a Sequential Port Scan
nmap -r [target]
Attempt to Guess an Unknown OS
nmap -O --osscan-guess [target]
Service Version Detection
nmap -sV [target]
Troubleshoot Version Scan
nmap -sV --version-trace [target]
Perform a RPC Scan
nmap -sR [target]
Discovery Options
Host Discovery The -p switch determines the type of ping to perform.

Nmap Switch	Description
-PI	ICMP ping
-Po	No ping
-PS	SYN ping
-PT	TCP ping
Perform a Ping Only Scan
nmap -sn [target]
Do Not Ping
nmap -Pn [target]
TCP SYN Ping
nmap -PS [target]
TCP ACK Ping
nmap -PA [target]
UDP Ping
nmap -PU [target]
SCTP INIT Ping
nmap -PY [target]
ICMP Echo Ping
nmap -PE [target]
ICMP Timestamp Ping
nmap -PP [target]
ICMP Address Mask Ping
nmap -PM [target]
IP Protocol Ping
nmap -PO [target]
ARP ping
nmap -PR [target]
Traceroute
nmap --traceroute [target]
Force Reverse DNS Resolution
nmap -R [target]
Disable Reverse DNS Resolution
nmap -n [target]
Alternative DNS Lookup
nmap --system-dns [target]
Manually Specify DNS Server
Can specify a single server or multiple.

nmap --dns-servers [servers] [target]
Create a Host List
nmap -sL [targets]
Port Specification and Scan Order
Nmap Switch	Description
Service/Version Detection
Nmap Switch	Description
-sV	Enumerates software versions
Script Scan
Nmap Switch	Description
-sC	Run all default scripts
OS Detection
Nmap Switch	Description
Timing and Performance
The -t switch determines the speed and stealth performed.

Nmap Switch	Description
-T0	Serial, slowest scan
-T1	Serial, slow scan
-T2	Serial, normal speed scan
-T3	Parallel, normal speed scan
-T4	Parallel, fast scan
Not specifying a T value will default to -T3, or normal speed.

Firewall Evasion Techniques
Firewall/IDS Evasion and Spoofing
Nmap Switch	Description
Fragment Packets
nmap -f [target]
Specify a Specific MTU
nmap --mtu [MTU] [target]
Use a Decoy
nmap -D RND:[number] [target]
Idle Zombie Scan
nmap -sI [zombie] [target]
Manually Specify a Source Port
nmap --source-port [port] [target]
Append Random Data
nmap --data-length [size] [target]
Randomize Target Scan Order
nmap --randomize-hosts [target]
Spoof MAC Address
nmap --spoof-mac [MAC|0|vendor] [target]
Send Bad Checksums
nmap --badsum [target]
Advanced Scanning Functions
TCP SYN Scan
nmap -sS [target]
TCP Connect Scan
nmap -sT [target]
UDP Scan
nmap -sU [target]
TCP NULL Scan
nmap -sN [target]
TCP FIN Scan
nmap -sF [target]
Xmas Scan
nmap -sA [target]
TCP ACK Scan
nmap -sA [target]
Custom TCP Scan
nmap --scanflags [flags] [target]
IP Protocol Scan
nmap -sO [target]
Send Raw Ethernet Packets
nmap --send-eth [target]
Send IP Packets
nmap --send-ip [target]
Timing Options
Timing Templates
nmap -T[0-5] [target]
Set the Packet TTL
nmap --ttl [time] [target]
Minimum NUmber of Parallel Operations
nmap --min-parallelism [number] [target]
Maximum Number of Parallel Operations
nmap --max-parallelism [number] [target]
Minimum Host Group Size
nmap --min-hostgroup [number] [targets]
Maximum Host Group Size
nmap --max-hostgroup [number] [targets]
Maximum RTT Timeout
nmap --initial-rtt-timeout [time] [target]
Initial RTT Timeout
nmap --max-rtt-timeout [TTL] [target]
Maximum Number of Retries
nmap --max-retries [number] [target]
Host Timeout
nmap --host-timeout [time] [target]
Minimum Scan Delay
nmap --scan-delay [time] [target]
Maxmimum Scan Delay
nmap --max-scan-delay [time] [target]
Minimum Packet Rate
nmap --min-rate [number] [target]
Maximum Packet Rate
nmap --max-rate [number] [target]
Defeat Reset Rate Limits
nmap --defeat-rst-ratelimit [target]
Output Options
Nmap Switch	Description
-oN	Normal output
-oX	XML output
-oA	Normal, XML, and Grepable format all at once
Save Output to a Text File
nmap -oN [scan.txt] [target]
Save Output to a XML File
nmap -oX [scan.xml] [target]
Grepable Output
nmap -oG [scan.txt] [target]
Output All Supported File Types
nmap -oA [path/filename] [target]
Periodically Display Statistics
nmap --stats-every [time] [target]
1337 Output
nmap -oS [scan.txt] [target]
Compare Scans
Comparison Using Ndiff
ndiff [scan1.xml] [scan2.xml]
Ndiff Verbose Mode
ndiff -v [scan1.xml] [scan2.xml]
XML Output Mode
ndiff --xml [scan1.xml] [scan2.xml]
Troubleshooting and Debugging
Get Help
nmap -h
Display Nmap Version
nmap -V
Verbose Output
nmap -v [target]
Debugging
nmap -d [target]
Display Port State Reason
nmap --reason [target]
Only Display Open Ports
nmap --open [target]
Trace Packets
nmap --packet-trace [target]
Display Host Networking
nmap --iflist
Specify a Network Interface
nmap -e [interface] [target]
Nmap Scripting Engine
Execute Individual Scripts
nmap --script [script.nse] [target]
Execute Multiple Scripts
nmap --script [expression] [target]
Execute Scripts by Category
nmap --script [category] [target]
Execute Multiple Script Categories
nmap --script [category1,category2,etc]
Troubleshoot Scripts
nmap --script [script] --script-trace [target]
Update the Script Database
nmap --script-updatedb
Reference Sites

 Nmap - The Basics
 Reference link 1
 Beginner's Guide to Nmap
 Top 32 Nmap Command
 Nmap Linux man page
 29 Practical Examples of Nmap Commands
 Nmap Scanning Types, Scanning Commands , NSE Scripts
 Nmap CheatSheet
 Nmap Cheat Sheet
 Nmap Cheat Sheet: From Discovery to Exploits
 Nmap: my own cheatsheet
 NMAP Commands Cheatsheet
 Nmap Cheat Sheet
 Nmap Cheat Sheet
