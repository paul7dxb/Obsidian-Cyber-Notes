# Analyzing Application & Network Security
## injection attacks
- RAT - Remote access trojan
- Malware can inject MAC or IP
- DLL injection
- SQLi
- LDAP injection
	- unsanitised or direct to back end
- XML injection / SOAP

## Targeted Coding Attacks
- Pointer / object dereference
	- Supply pointer to memory location unexpected
	- Null reference
	- Crash or read from unintended postiion
- Directory traversal
- Buffer/integer overflow
	- Larger than expected input. Overwrite adjacent memory
- Race conditions
	- Two or more similtaneous things needed to be done specific order
	- Sync error activities
- Time of check / Time of use
	- race condition by racing to resource
- Improper Error and input handling
	- Including collision hashes
- Session replay attack
	- Stealing valid session id

## API attacks
Application programming interface

- API calls not digitally signed
- Login attacks
	- automated attacks
- DDOS attacks
- Leverage credentials
	- Stolen creds or API keys

## Pass the Hash
- Windows vulnerability
	- Dont need PT passwords just the hash
- Safe mode vulnerabilty
- VSM defends against this

## Driver Manipulation
- Shimming
	- Steaoling info and money from point of sales / ATM
- Refactoring

## Wireless attacks
- Evil twins
	- Rogue access point instead of real one
	- MITM
	- honey pot except appear as valid network
- Disassociation Attacks
	- DOS attack against infrastrucre
	- Get client to reauthenticate with your rogue access point
	- Use MPP todefend against / WPA3
- MITM
	- Honeypot
- Jamming
- Weak Inititialisation Vector
	- Easy to crack
	- WEP
		- passive attack crack 24 hours
	- WPA3 dragonfly handshake
		- dragonblood attack patch
- Bluejacking
	- Spoof a name
- Bluesnarfing
	- Steal data through bluetooth
	- Contact/calandar text messagges
	- discoverable vulnerable
- RFID / Near Field Communnication
	- Sniffing , spoofing, replay
	- cloning
	- RFID zapping
	- Relay attacks

## MITM attacks
- Proxy ARP
- DHCP spoofing
- Inject in intended path TCP/UDP
- Simplex or duplex
- Man in the browser
	- trojan used  between browser and libraries

## Layer 2 attacks
- ARP Poisoning
	- MITM
	- Inject false frames
	- only IPv4
	- Mitigate:
		- Port security
		- DHCP snooping
		- Cloud provider hypervisor protection
- MAC flooding
	- macoff
	- flood switchport to fill CAM table
	- DOS
- MAC cloning

## DNS attacks
- Domain hijacking / clickjacking
	- Hijack clicks
- DNS poisoning
	- DNS sserver cache
	- Farming
	- Redirect to different address
- Domain repuation attacks

## DDoS
- DOS
- Consume networkm resources
	- CAM table, bandwidth, DHCP lease
- Simple to conduct
- DDOS
	- zombiefied hosts

## Malicious code or sript execution
- Virus attach to exe
- Worm self replicating
- Script virus
	- Infect other files or part of other code


# Threat Actors, Intelligence Sources & Vulnerabilities

## Actors & Threats
- Threat agents are the persons, systems, techniques that acts to support threat or exploit
- All malware are exploits nnot all exploits are malware
- Individual or group
- APT
	- Long term
	- Pre planned with cost benefit
	- Often state actors
	- Muli phased polymorphic
- Human error
- cognitive threats

## Attributes & Actors
- Internal or external
- Structured  
	- Planned, organised
	- Persistent
	- Multi phased
- Unstructured
	- Usually accidental
- Motivation
- skill set
- Probablity of action

## Threat Vectors
- Physical access (removable media)
	- switches, routers, firewalls
	- Closets
- VPN
- Wireless
- Enterprise WPA
- Messaging
- File transfer access
- Other connected enterprises
- Key access (API)
- Single sign on multi FA

## Threat Intelligence Sources
- Indicators of Compromise (IOC)
	- Cyber observable
	- Forensic aretfact
	- Registry entry, new files
	- Meurasble event
- Vulnerability database
	- Needs rapid distribution
	- CVE / MITRE
- Dark Web
- OSINT
	- maltego
	- theHarvester

## Research Sources
- Vendor sites
- Conferences
- IEEE RFC
- Industry
- Social media

## Cloud vs On-Premise Vulnerabilities
- Cloud
	- Threat actors likely external
	- Access keys
	- Many accounts reduce attack surface
- On premise
	- Biggest threat is privileged insider
	- Access beyond role

## Zero Day Vulnerabilities
- Malware or exploit
- zero day when they are discovered
- When vendor is made aware of exploit's existence

## Weak Configurations
- Human error biggest vulnerability
- Better to automate
- Weak encryption
- Unsecure protocols
- Default settings
- Improperly Configured Users
	- Least privilege policy
- Seperate admin accounts
- Auditing
	- ISE
- Shared accounts

## Third Party Risks
- Vendor Management
- System integration
- Lack of vendor support
- Supply chain security
	- Manufacture through to delivery to organisation
- Outsourced code development
	- Adequate testing
- Data Storage
	- Encrypted AES-256 GCM
	- Access Contor

## Improper Patch Managment
- Configuration Management Database (CMDB)
- Configuration Items (CI)
- Select personnel with rights to test, apply and determine urgency of patches

## Legacy Platforms
- Data loss, breach and exfiltration
	- Use of containers
	- Use of lifecycle
- Scripts available on old devices
- IoT devices use old OS and rearely patched
- DOS vulnerable

# Security Assessment & Pen Testing Techniques

## Threat Hunting
- Visibilty
- Analyse
- Hypothesis
- Hunt analytic
- analyse
- follow up
- Revise

## Vulnerability Scanning Technology
- Identifying known and unkown waknesses
- Intrusive active
- Passive
- Unpatched, misconfigured, open  ports

- Ture positive: Found + action taken
- True Negative: found + no action

- Logs
- SNMP traps
- Netflow
- SIEM Security Information and event managment
- SOAR
- NGIPS

CVE
- Common Vulnerabilites and exposures
	- ID
	- Description and reference

CVSS
- Weigh severity of vulnerability
- 0-10

## Vulnerability Scanning Tools
- Nessus
- OWASP ZAP
- Burpsuite
- Network scanning
	- Rogue IP, AP, DHCP
	- Ports
	- Locations
	- Wireless
	- Issues and outages
- Compliance Scanner
	- Auditing
	- Checks in configured to agreed standard

## Syslog & SIEM
- syslog trap
	- one way
- Informs
- UDP 514 or TCP 1468
- Severity categories
	- 0 emergency
	- 1 alert
	- 2 critical
	- 3 error
	- 4 warning
	- 5 notice
	- 6 information
	- 7 Debug
- Shouldn't be single point of failure
- 

## Pen Testing Terminology
- Black box is testing without any prior knowledge
- White box
	- 0 Detailed investigation of systems
	- 1 often have full knowledge
- Credentialed testing (given user account to use). Gives more comprehensive testing results
 black box
	- No prior knowledge to tester
- White box
	- Detailed investigation of internal logic
	- Full knowledge of systems and network usually known
- Greybox
	- Some limited knowledge
- Credentialed
	- Give existing account (white/grey)
- Intrusive / non intrusive
- In line / promiscuous

## Pen Testing Fundamentals
- Phases
	- ROE agreement
	- Recon and engagement
	- Priv esc
	- Pivoting / Lateral movement
	- Persistence
	- Clean up

## Active Recon
- Fingerprinting
- Nessus
- Burpsuite 
- Banner grabbing
- Port and address scanning

## Priv esc
- Check OS and kernel version
- Check users and current privilege
- List SUID files
- View installed packages and services for vuln version

## Exercise Teams
- Purple team
	- 0 Improving organisation
- Blue team
	- 0 Implementing controls
	- 1 Incident response
	- 2 Security monitoring

# Security Concepts in Enterprise Environment

## Configuration Management
- Diagrams & Topologies
- Baselines
- Schemas
- Naming and Tagging
	- 0 Labelling laptops
	- 1 Metadata labels

Change Management
- Changes should be logged

Change Management Lifecycle
- Submitting
- Approving
- Documenting
	- 0 Configuration Management Database (CMDB)
- Testing
- Implementing
	- 0 Schedule of change
	- 1 Milestones
	- 2 Automation through orchestration software
- Reporting

## Data Sovereignty
- Sensitive data in different jurisdications or global regions
- ITAR (International Traffic in Arms Regulations)
- Export Administration Regulation (EAR)

- Cloud computing Geolocation
	- 0 May need to restrict cloud usage dependant on region
	- 1 MAy need to use cloud physically located in specific region

## Data Protection
- Steps to protect data
- Labeling
- Handling
- Least privilege
- Data at rest vs data in motion
- Tokenization of mobile devices
	- 0 Enterprise Mobility Management = MAM + MDM (Mobile Application Management) (Mobile Device Management)
- Manage the loss and leakage beyond established domain
- Redacting

- Data
- Can leak
- To an outsider
- Resulting in a breach

## Hardware Security Module
- Crypto processor
- Haredened and tamper resistence
- Manage, process, generate and store keys for PKI, SSH
- Verify digital certificates

## Geographical Considerations
- Where to store offsite data and backups
- Cloud HSM may not be allowed and need pysical HSM on site
- Legal considerations for area
- Consideration
	- 0 Jurisdiction
	- 1 Privacy laws
	- 2 Import-export restrictions
	- 3 Cryptography

## Cloud Security Brokers
- Cloud Access Securiity Brokers
	- 0 Between customer and
	- 1 SAAS - Software as a service

## Response and Recovery Controls
- Risk Response
	- 0 Accept
	- 1 Mitigate
	- 2 Transfer/share
	- 3 Avoid (avoid actions that introduce risk)
- Security guards
- Incident Response Team
- Computer Security Incident Response Team (CSIRT)
- Backups and snapshots
- Remote wiping mobiles
- Recovery plans
- Determin RTO and RPO (Recovery Time/Point Objective)
- Disaster recovery sites

## SSL / TLS Inspection
- Secure Sockets Layering
- Transport Layer Security
	- 0 Keep up to date
	- 1 Conrol browsers that can connect
	- 2 Perfrom certficate revocation checks
	- 3 Verify encryption
	- 4 Use trusted authorities
	- 5 Pinning and OCSP stapling

## Hasking and API
- Crypto strength is half of key length
- Apply forward secrecy
- AES-256-GCM has built in hash authentication
- API Consideration
	- 0 Digitally sign API calls
	- 1 Do not embed credentials
	- 2 Only connect to trusted sources
	- 3 Protect secret keys
	- 4 Secure codign practices

## Site Resilliency
- Site resilience
- Capacity of a network to recover and continue operations
	- 0 Cold site - power only
	- 1 Warm site - some hardware, wired ethernet, some personnel
	- 2 Hot site (mirrored) - parallel site, enough duplicate hardware/software
	- 3 Mobile site
	- 4 Hybrid cloud

## Deception and Disruption
- Honeypots
- Honeynet
- Honeyfiles. Mainly used to catch privileged insider
- Fake telemetry
	- 0 Use trap assets
	- 1 fake data
	- 2 no legit person should be accessing these
	- 3 DNS sinkhole


Things to look at
Warning levels (4 warning)
SOAR - 
Cloud Access Security Broker CASB

AEAD Authenticated Encryption with Associated Data - AES-256-GCM
