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

# Implementing Cybersecurity Resilience

## Redundancy Concepts
- Passive. Uses additional capacity to reduce impact of component failures
- Active. Similtaneous capacity in use. Hot/parallel sites
- Geograpical dispersal
- RAID (Redundant Array of Independent Disks)
	- 0 RAID 0 - Data split between disks. No redundancy. Striping.
	- 1 RAID 1 - Mirroring. Same data. Slow write
	- 2 RAID 5 - atleast 3 drives. Striped with parity
	- 3 RAID 6 - RAID 5 but with 2 parity data. webserver. Not for heavy writing
	- 4 RAID 10 - mirroring and striping (1&2 stripe and mirror onto 3&4)

	![image](https://user-images.githubusercontent.com/62883464/194934467-fa0fef9a-bb3f-45c4-a149-5199ca9db4e3.png)

- Network Load Balancer
	- 0 In cloud can grow horizontally
- Redundant Power

## Replication Methods
- SAN: Storage Area Network
	- ![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221011054353.png)
	- IPsec AH for integrity and origin authentication for data in transit
	- Encrypt with AES-256-GCM
- Virtualisation
	- Hypervisors control interaction between VMs and 
	- Type 1 - bare metal
	- Type 2 - hosted hypervisor on OS (ontop of Windows)
	- Vulnerabilities
		- VM sprawl
		- VM escape. Interacts directly with host OS or hypervisor
	- Containers
		- Isolated abstracted applications
		- Package up applications with all dependencies as a package
		- Consistent experience
		- Immutable
		- Docker / Kubernetes

## Backup Types
- Full backup
- Incremental backup
	- Only archive bit set, new or updated file
	- Clears archive bit onve backup complete
	- Slowest to restore, need all backups
- Differential backup
	- Does not clear archive bit once complete
	- Last full backup and most recent differential needed
- Snapshot
	- Immediate point in time copy
	- Improved RTO and RPO

## Non-persistence Concepts
- Revert to known state
- Last known good config (before win 10)
- Live boot media
	- Security threat if regular users can live boot

## High Availability Concepts
- Availability
	- System uptime
	- Ability to access
- Durability
	- Long term data protection: degregation
	- 11 9's to 16 9's
- Scalability
	- Ability to increase workload on current hardware
	- Scale up
- Elasticity
	- Ability to increase workload on its current and additionally added on demand hardware resources
	- Scale out

## Order of Restoration
- Repair hard drive
- Image drive to new disk image file
- Recovery of files from clone
- Repair damaged files

![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221011060645.png)

- DRP Restoration
	- Protect people and critical assets
	- Sustain ongoing operational viability
	- Financial stability
	- Deliver profitability

## Diversity Concepts
Avoiding single point of failure:
- Technologies
- Vendors
- Cryptosystems
- Controls

# Virtualization, Cloud computing & Cloud Cybersecurity

## Virtualization basics & VM Security
- Hypervisors
	- Software that makes and manages virtual infrastructure
	- Controls resources
- Type 1 Hypervisor
	- Bare metal / metal
	- Blade / rack mounted
- Type 2 Hypervisor
	- Host OS on top of hardware
	- Hypervisor on top of OS
- Vulnerabilites
	- VM Sprawl
		- Number of VM's becomes unmanageable
		- Enforce strict policy including who can deply VM's
	- VM  escape
		- Guest VM interact with host VM in unintended way

## Cloud Models
![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221011064719.png)
- Cost saving 
- Elasticity and Agility
- Broad Access
- IaaS
	- Processing, storage and networks for arbitrary software
	- ![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221011064445.png)
- PaaS (Platform as a service)
	- Consumer doesn't manage cloud infrastructure
	- Development platforms
	- Container services
	- Managed databases
	- Security
- SaaS (Software as a service)
	- Use provider's applications on cloud
	- Usually interact with application through a browser
- Private cloud
	- Personal information, credit card info
- Public cloud
	- For customer consumption
- Community cloud
- Hybrid cloud

## Cloud Service Provider
- MSSP (Managed Security Service Provider)
	- Outsourced security monitoring and management
- Fog Computing
	- Place resources close to where they are needed
- Microservices
	- Small self contained form part of larger applications with API
	- Modular and independantly deployable

## Infrastructure as Code
- Use template language e.g YAML or JSON

## Containerisation
- Include all components needed
- Portable
- Libraries can be across containers
- Replace container instead of updating
- ![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221011073438.png)
- Docker vs Kubernetes
	![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221011073527.png)

Use docker to deploy and then kubernetes to scale after deployment

## Serverless Architecture
- CSP handles all server overhead
- Services Integration
	- Take value of delivered services
	- Integration platform software
		- Handle complex integration
	- iPaaS
		- Integration Platform as a Service
	- SaaS vendor tooling
		- plug ins integrate between application
	- Custom coding
		- Team creates integration
	- Function Platform as a Service (fPaaS)
		- Create suite of integration tools

## Transit Gateways
- Connect on premise networks to single component
- Connect different VPNs
- ![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221011074047.png)

## Cloud Storage Security
- Block and object storage
- Secrets Management
- Data publicly access through URL or API calls
- data in rest can be server side encrypted
- Can use client side encryption and send to service
- High availablilty and fault tolerence

## Cloud Network Security
- Public or private subnets
- DDoS solutions
- ![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221011080841.png)
- WAF with deep packet inspection
- Site to site VPN's

## Cloud Compute Security
- Private subnets and firewalls
- Cloud functions enhance security
- Single source of truth
- Container secuirty by design

OWASP top10 IoT
- Weak passwords
- Insecure network services
- Insecure ecosystem interfaces
- Lack os secure update mechanism
- Insecure or outdated components
- Insufficient privacy protection
- Insecure data transfer
- Lack of device management
- Insecure default settings
- Lack of physical hardening

## Cloud Security Solutions
![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221011083656.png)

- CASB (Cloud Access Security Brokers)
	- software between cloud customer and SaaS
	- On premise or cloud
	- Acts as a gatekeeper
- Next Generation Secure Web Gateway (SWG)
	- Protects from cloud enabled threats
	- Web content filtering
	- Data loss protection
	- ATP
- Audit processes
	- Transparency
	- collocation
	- Scale
	- Scope
	- Security and privcay
	- Complexity
- SAS Statement on Auditing standards 70
- SSAE Standards for Attestation Engagements 16
- ISAE International Standard on Assurance Engagements 3402

# Controls & Application Development & Automation

## Categories of Controls
- NIST SP 800-53
	- Managerial
		- Administrative controls
		- Published in policies
		- Training programmes
	- Operational
		- Change and configuration management database
		- Conducting training
		- Physical and environmental controls
		- incident response
		- disaster recovery
	- Technical
		- Security mechanisms that systems run
		- CIA protections

## Types of Controls
- Preventative
	- Counter measure from atttacker delivering payload
	- IPS
- Detective
	- ID security violations
	- IDS
- Corrective
	- React to detection to eliminate opportunity
- Deterrent
	- Warnings of consequences
	- Presence of other controls can be a deterent
- Compensating
	- Assist other controls
	- Data loss prevention to email agent

![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221011092755.png)



# Things to look at
Warning levels (4 warning)
SOAR - 
Cloud Access Security Broker CASB

AEAD Authenticated Encryption with Associated Data - AES-256-GCM

Infrastructure as code

Function as a service (AWS lambda)

HSM - Hardware security modules??