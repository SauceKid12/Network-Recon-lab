# Network-Recon-lab
a beginner friendly cybersecurity lab exploring network recon, port scanning, service enumeration and security analysis using nmap in a controlled windows environment

  Network Reconnaissance & Service Enumeration Lab

PROJECT OVERVIEW

This project documents a beginner-friendly cybersecurity lab focused on network reconnaissance, port scanning, and service enumeration using Nmap.

The scan was performed against a Windows lab machine in a controlled environment to identify reachable ports, discover running services, and understand basic network security observations.

PROJECT OBJECTIVE

* Understand network reconnaissance.
* Identify open, closed, and filtered ports.
* Detect services and their versions using Nmap.
* Interpret scan results and identify security configuration observations.
* Document findings in a cybersecurity portfolio.

 TOOLS USED
 
* Kali Linux
* Nmap 7.98
* Windows lab machine
* GitHub for documentation

METHODOLOGY

Step 1: Test Connectivity

Command:

ping -c 4 172.20.10.6

The target responded to all four packets, indicating that it was reachable from the scanning machine at that time.

Step 2: Perform a Basic Scan

Command:

nmap 172.20.10.6

This scan checked Nmap’s default set of 1,000 common TCP ports.

Step 3: Detect Services and Versions

Command:

nmap -sC -sV 172.20.10.6

* -sC runs Nmap’s default script set.
* -sV attempts to identify services and their versions.

5. Scan Results

Port	State	Service	Observation
135/tcp	Open	MSRPC	Microsoft Windows RPC service
139/tcp	Open	NetBIOS-SSN	NetBIOS session service
445/tcp	Open	Microsoft-DS	SMB-related Windows service
5357/tcp	Open	HTTP	Microsoft HTTPAPI 2.0
8000/tcp	Open	HTTP	Splunk web interface
8089/tcp	Open	HTTPS/HTTP over TLS	Splunk management service

Additional observation: Nmap reported 994 filtered TCP ports in this scan. A filtered result means Nmap could not determine whether those ports were open or closed because responses were blocked or absent.

6. Security Observations

SMB SIGNINGS

The scan reported that SMB 3.1.1 message signing was enabled but not required.

This means the system supports SMB message signing, but it does not require signing for every applicable SMB communication. Requiring signing may help defend against certain relay or man-in-the-middle attacks, depending on the environment.

This finding is a configuration observation, not proof that the system is vulnerable.

Splunk Services

Ports 8000 and 8089 were reachable during the scan and identified as Splunk-related services.

These services should be accessible only to authorized users and systems. Their presence alone does not prove a vulnerability.

Microsoft HTTPAPI

Port 5357 returned a service-unavailable response. This was recorded as an observation and was not treated as proof of vilnerability

CHALLENGES ENCOUNTERED

During the lab, a later scan showed all 1,000 scanned ports as filtered. Investigation revealed that the Kali Linux and Windows machines were on different networks.

This demonstrated that a service listening on a Windows machine may not be reachable remotely when network routing, network configuration, or firewall rules prevent access.

8. Key Lessons Learned

* How to perform basic Nmap scans.
* How to use -sC and -sV.
* How to interpret open and filtered ports.
* How to identify common Windows and Splunk services.
* How to recognize security configuration observations without overstating their significance.
* How network topology and firewall rules affect scan results.
* How to document technical findings for a cybersecurity portfolio.


LAB EVIDENCE
NMAP DETTECTION SCAN 


