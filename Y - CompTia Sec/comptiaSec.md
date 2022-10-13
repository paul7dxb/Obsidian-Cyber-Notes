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

## Secure Application Environments
- Secure by design
	- SDLC - Secure development life cycle
- Secure by Deployment
	- Put into an environment where security is in network
	- Air gapped
- Secure by default
	- Disabling insecure functions

## Provisioning and Deprovisioning
- Providing or removing software access on an as needed basis
- Prevent privilege creep
- Enablers
	- automation
	- auto sclaing
	- VMs and containers
	- rapid deployment agile, spiral
	- Hybrid as a cloud

## Integrity Measurement
- NIST SP 800-155 - BIOS integrity
- Check for digitially signed codes and programs
- Use Linux IMA (Integrity measurement architecture) subsystem
	- Kernel hashes of files
- Trusted Computing Base Solutions (TPM)
- Execution validation
- WS-Secuirity (WSS)
	- SOAP extension
	- Allows commuinication of authentication formats

## Secure Coding Techniques
- Normalization
	- error handling
	- Input validation
	- Ensure there is no data redundancy and similar components are stored together
- Camoflage / obfuscation
- Dead code
	- remove unneccessar code
- Memory management
	- Counter buffer overflow
	- Memory leak
		- NX bit (never execute)
		- Address space layout randomisation (ASLR)
- Data exposure
	- Abstract origianl data. Act on a view of the original data
	- Access control and least privilege
	- Sign API calss
	- Emply DLPs (Data Loss Prevention)
- Stored procedures

## OWASP for Application Development
- Open Web Application Security Project
- OWASP MSTG (mobile secuuirty testing guide)

## Software Diversity
- Methodology where two or more functionally duplicate versions are developed from same specification
- Made by different teams
- Low level code is more liekly to be exploited
- Diversity decreases attack surface size

## Automation and scripting in application developement
- Continuous monitoring
- Validation
	- Finding bugs
- Integration
	- Tools to run code analysis tests
- Delivery
- Deployment
	- Containers
	- Functions as a service


# Authentication & Authorization Design Concepts

## Authentication, Authorization and Accounting (AAA)
- Authentication
	- Validate identity
	- Origin (origin of packet)
		- Follow up with more advanced layers of authentication
- Authorization
	- Granting authenticated entity permission
- Accounting
	- Billing and chargeback
		- Budgets
	- Auditing and reporting

## Character vs Packet Mode
- Network authenticing device
- Character
	- Send keystrokes to network device
	- Configuring and commands
- packet mode
	- Interface mode or link protocol session
	- Communicate with device on other side of authenticating device
	- Midiated access
- ![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221011182007.png)

## Directory Services
- AD components
	- Schema
		- Limits, formatting of naming convention
	- Global catalog
		- Global catalog of all objects
	- Query and indexing service
	- Service to replicate data across network
		- DC

- LDAP
	- Lightweight Directory Access Protocol
	- Often used for accesss to management app and browsers

- Securing the directory
	- Least privilege
	- Pysical security
	- Seperate admin accounts
	- Just in time admin passwords
		- Laps tool
	- Azure Advanced Threat Protection (ATP)
	- MFA (Multi Factor Authentication) for admin / power users
	- TLS IPSec for data in transit
	- CASB (Cloud Access Security Broker)

## Federation and Attestation
- Trust between ID provider (AD) and some service
- Attestation using tokens and assertions

## Authentication Technologies
- 2FA
	- Time based one time password
	- Software based token (google authenticator)
	- HOTP (HMAC based one time password)
	- SMS
	- Token key
- Static Codes
- Authentication applications like lastpass
- Push Notifications

## Smart Card Authentication
- From of 2FA
- Contact card to host computer
	- Common Access Card (CAC)

## Biometrics
- Part of MFA (multi factor authentication)
- Fingerprints
- Facial Recognition
	- non intrusive
	- Principal Component Analysis (PCA)
		- fast with low computational overhead
- Retinal scan
	- Invasive (close to eye piece)
- Iris scan
	- colour and size of pupil
	- Camera technology with IR light
	- **More widely accepted as a commericial modality**

![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221012054225.png)

- Voice recognition
	- Speech recognition
	- Speaker recognition
		- aural aspects of speech that are unique to person
- Vein analyisis
	- Palm, finger, retina
- Gait analysis
	- non invasive
- Accuracy
	- FAR: False acceptance rate (false positive)
		- Number of false acceptance / number of authentication attempts
	- FRR: False rejection rate
		- Reject authentic user
	- CER: crossover error rate
		- Value of FAR and FRR when sensitivity is setup so FAR and FRR are the same
		- Used to compare biometrics

## Multi Factor Authentication
- Something you know
- Something you have
- Something you are
- ABAC: Attribute based 
	- somewhere you are
	- Something you can do (VPN connection, use root)
	- Something you can exhibit

## Cloud vs On-premise Authentication & Authentication
- Cloud concerned with layer 3 and above
- On premise starts at physical edge of campus
![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221012062220.png)


# 10. Implementing Identity and Account Management & AAA Solutions

## Identity Controls
- IdP: Identity Providers
	- system service that provides single set of login credentials that works over platforms
		- Facebook ligin
	- Uses translation and assertion services
	- ![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221012063949.png)
- 3 types of identity controls
	- Tokens
	- Assertions
		- Azure Shared Access Signature
		- SAML 2.0
	- Certificates
		- X.509v3

## Acount Types
- ACcount Types
	- User
	- Guest & generic
	- Shared accounts and credentials
	- Service and application accounts
	- Energency (fallback) account
		- RADIUS
- Rootkits can create and install hidden accounts
- Dual operator pronciples for certain activities
	- Two different accounts to perform an action

## Common Account Policies
- IAM
	- Identity and Access Management
	- AWS uses Managed policies to assign permissions

## Advanced Account Policies
- Geofencing and geolocation
	- Device useage by location
- May disable
	- Geolocation from metdata
- Mobile Device Management (MDM)
	- Time of day restricitons
	- GPS tags
- Risk based attribute based access control (ABAC)
	- fine grained authorization
		- Policy and attributes for that policy (limitations (value of transfers))

## Authentication Mangement
- Key management is main vulnerability to cryptosystems
- AUP: Acceptable Use Policy
- Password vault == Password Manager
- Trusted Computing (TC) and Trusted Execution Environments (TEE)
	- TPM: Trusted Platform Module
		- module embedded in a system
		- tamper resistent security chip
	- SED: self encrypting drive
		- aka Full disk encryption
		- Cannot be turned off
		- Less susceptable than software based
	- HSM: dedicated crypto processor
		- Hardware Security Module
		- Physcial or virtualised (HSA: hardware security abstraction)
- KBS: Knowledge based authentication
	- secuirty questions
	- Info that only user can know
	- Dynamic KBA
		- Generate questions from credit history or public records (out of wallet)

## Common Authentication Protocols
- PAP: Password Authentication Protocol
	- Authentication phase before network layer
	- First send LCP during MAC establishment
	- 2 way hand shake
- MS-CHAPv2
	- Challenge Authentication Protocol
	- Secure PPP in a tunnel
		- Uses GRE Generic routing encapsulation
	- ![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221012073558.png)
	- Use weak 56 bit DES encryption
- IEE 802.1x (PNAC)
	- Port based network access control
	- ![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221012073707.png)
	- Initially send out EAPOL frames
		- Extensible Auithentication protocol over the LAN
	- EAP
	- PEAP
	- EAP-FAST (Cisco)
	- EAP-TLS
		- x509 certificates
	- EAP TTLS (tunneling)
		- Highest level of security
		- Requires deplyment of certificates
	- ![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221012074029.png)
- RADIUS
	- Remote Authentication Dial-In User Service
	- Enables remote access server to communicate with central server to authenticate users and authorize
	- Client server modfel
		- client is a router or AP
	- use shared secret between client and server ich is never sent over network. Only password is encrypted
	- UDP 1812 (authentication)
	- UDP 1813 (accounting)
	- Earlier was 1645 and 1646
	- RADIUS server sends authentication and what user can do back to client router

## Authentication Protocols for Federation
- SAML (Security Assertions Markup Language)
- OAuth
- (OIDC) OpenID Connect
- Shibboleth
- Kerberos

- SAML (Security Assertions Markup Language)
	- Based for web pages
	- XML based
	- SOAP simple object access protocol
	- Open source
	- Used with SaaS
	- Identity provider gives assertion and gives to service provider
- OAuth
	- JSON
	- publish and iteract with protected data
- (OIDC) OpenID Connect
	- Identity layer on top of OAuth
	- Verifies end user ID
	- Basic profile info
	- Web based, mobile and JS
	- Extensions can be added
- Shibboleth
	- Inter/intraorganisational connection
	- univeristy / public
- Kerberos
	- AD 
	- Replaced NTLM
	- Ticket
	- Mutual authentication
	- All communication encrypted
	- KDC Key Distribution Center 3rd party
	- ![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221012125141.png)
	- 

## Access Control Schemes
- (DAC) Discretionary Access Control
	- Restricts access to data based on identity or group
	- Usually owner can change permissions
- RBAC (Role based Access Control)
	- Based on org chart, roles and responsibilities
	- Framework set by admins not user
	- Negatives
		- Scope creep
		- Roles must be audited
		- Multi tenancy capabilities need AD OUs
- (RB-RBAC) Rule Based Access Control
	- Dynamically assigned roles
	- Can be time based (e.g access only 6-6 mon - fri)
	- Common in routers, switches
	- Stateless or stateful
	- `access-list 100 permit tcp any IP eq ftp-data`
- (MAC) Mandatory Access Control
	- Strict non-discretionary model
	- Subjects and Objects
	- Assigns sensitivity labels
	- "need to know"
		- minimise scope creep
		- Bell-LaPadula

# 11. Physical Security Controls
## Types of physical Barriers
- 1 Residential Gate operation
- 2 Commericial
- 3 Industrial
- 4 restricted access operation, supervisory

## Cameras & Surveillance Methods
- Industrial Comoflage
	- Camoflage into areas
	- Telephone tower looking like a tree
	- Temporary building with high security ea underground

## Personnel Controls
- Guests register in
- Robot Sentries
	- cameras, sensors

## Locking Mechanism
- Preventative mechanism
- Lock picking
	- Tumblers in line with shear line
	- Raking locks
	- Brute forcing locks
		- Hammers, firearms
- Type os lock
	- Key
	- Warded
	- Wafer/tumbler
	- Pin tumbler
	- Deadbolt
	- Interchangeable core
	- Combination
	- Electornic combination
	- Keyless (buttons / cipher)
	- Smart lock
		- Plastic card (hotel)
	- Cable lock (laptop)

## Fire Prevention and Suppression
- Categories
	- Prevention
	- Detection
	- Suppression
- Fire Controls
	- Type A: common combustable
	- Type B: combustable liquids
	- Type C: electrical
	- Type D: Combustable metals

## Types of sensors
- Lighting
- Photoelectric - break in light beam
- Passive infrared
- Vibration
- Acoustical
- Microwave
- Electro-mechanical: break in circuit (door/window open)
- Electrostatic - presence of human
- Moisture / temperature detection - for server rooms to monitor environment

## Secure Areas
- Mantraps
	- Only one open door at a time
	- One person at a time to stop tailgaiting
- Faraday cage
- Cable runs and distribution frames need to be protected
	- MDF rooms
- Safes and vaults
- Air gap
- Hot and cold aisles

## Secure Data Destruction
Digital
- Degaussing - removing magnetic field of physical drive, zeroise
- Purging - software
- Wiping - overwrite pseudorandom
- Encryption

Written form
- Burning
- Shredding
- Pulping
- Pulverizing
- 3rd party

# 12. Basic Cryptography & PKI

## Symmetric vs Asymmetric

![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221012170138.png)

CIA
- Confid
- Hiding data at rest
- Integrity
	- Ensure data hasn't been altered
- Availability
	- Protect systems from flooding
- Non-repudiation
	- Ensures original sender cannot deny sending data
		- Digital signatures

Layers
![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221012170359.png)

Symmetric
- Same key
- Efficient and fast
- Inexpensive computationally
- Shorter key length
- Key management more complex
- DOes not scale well

Asymmetric
- Mathematically related pair
- Efficient key management
- Scalable
- Longer key lengths
- Slower and more computationally expensive


## Characteristics of Cryptographic Keys
- Keyspace = total number of mathematical possibilites in the set
	- 2^n
- Static
	- Used for long period
	- OSPF/BGP
	- Multiople time
- Session key
	- Used for specific session
	- cryptanalytic attacks more difficult
- Ephemeral keys
	- Used for one key establishment process
	- Never stored in memory. Not retained
- Key Stretching
	- PBKDF2 / BCRYPT
	- Password + salt many times
- Kerberos 4096 iterations

**Weaknesses of crypto:
Key management and human implementation**


## Block vs Stream Cipher Suites
Block
- Fixed blocks of data
- Use padding
- DES
- 3DES
- AES-CBC
- AES_GBC
- Blowfish
- Cipher Block Chaining
	- ![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221012174540.png)
- Counter mode
	- Generates pseudo random nonce
	- Used once with a given key
	- ![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221012174642.png)

- Galois Counter Mode
- ![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221012174732.png)
-  Authenticated Encryption Authenticated Decryption
- Auth tag to give authenticity of data

Stream data cipher
- Xor with keystream bits
- Faster
- Fish
- CryptMT
- Scream
- RC4


AES
- Replaced DES
- Block cipher
- CBC and GCM modes most common

## Cryptographic Hasing
- Strength is half of bit size
- Avalanche effect - small change in input for big change in output

- Use HMAC (Hashed Message Authentication Code) verify sender information
	- Uses hashing (H) with secret key (MAC)
![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221012180036.png)
HMAC for router updates
![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221012180236.png)

## Key Exchange Mechanisms
- Asymmetric key exchange
	- RSA
	- Diffie-Helmen (DHKE)
		- two parties over unsecure channel
	- Elliptic curve DIffie-Helman
		- Most efficient
		- Smaller key with more strength
	- Ephemeral Diffie-Helman
		- Give forward secrecy
		- Can also be used with elliptic curve

## Modes of Operation
- Crypto can be authenticated
	- HMAC for origin authentication
- GCM
	- Only gives confidentiality
- Some use counter
- Ephemeral
	- Forward secrecy
- Perfect FOrward Secrecy
	- IPSec
	- Compromise of long term does not allow attacker to obtain past session keys
- Lightweight cryptography
	- Sensor networks
	- IoT
	- Lighter mechanisms needed

## Advanced Cryptography Concepts
- Digital certificates
	- Authenticity, integrity and non repudiation
	- Not offer confidentiality
- Quantum computer
	- qubits
- Post quantum crypto
	- Rsistant to attacks from quantum computer
	- Lattice spaced crypto
	- Increase size of keys
- Quantum communications
	- protect data
	- QKD (Quantum key distribution)
	- Decryption key sent in quantum state
- Homomorphic Encryption
	- Protect data in use
	- Remains encrypted while being processed
	- Algebraic system to allow operations to take place on it
- Blockchain
	- data, time and amount
	- transactions verified

## Common Use Cases and Limitations
- Low power -> low latency and high resiliency
	- lightweight crypto and elliptic curve
- Confidentiality
- Integrity
- Obfuscation
	- When someone knows underlying technology hiding crypto keys underneath
- Authentication
- Non repudiation

Limitations
- Speed
- Size on suppported key space
- Weak keys
- Time
- Longevity
	- Longer used more likely to be brute forced
- Predicability
	- Weak passwords
- Key reuse
- Entropy
	- Neutralise structure of output
- Computational overhead

## PKI
- Web of Trust
- Trusted introducer

![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221013064111.png)

- CSR: Certificate signing request

## Types of Certificates
- X.509v3 format
	- Version number
	- Serial number
		- Used to revoke certificates
	- Signature algortihm ID
	- Issuer name
		- Could be CA in domain
	- Valid to and from
	- Subject name
	- Public key infor
		- algorithm
		- public key
	- Extensions
	- Certificate signature and algorithm used
	- Certificate extensions
		- ![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221013070226.png)
		- ![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221013070254.png)

- Types of certificate
	- Wildcard: Multiple sub domains
		- \*.mycompany.com
	- Subject Alternate Name (SAN)
		- Additional names based on email, IP, DNS names
	- Code signing
		- Authenticate source and integrity of code
	- Self signed certificates
		- Used by root CAs
	- Email (S/MIME)
	- Machine / Computer
		- Authenticate device to network
	- User

- Certificate Validation
	- ![](ZZ%20-%20Pasted%20Images/Pasted%20image%2020221013070759.png)

## Core PKI Concepts
- CA Trust model
	- Single CA
		- Directly provide certificates to everyone
		- Always online
	- Hierarchical
		- Root CA and intermediate CAs
		- Root can be online or offline
			- Offline: apply certificates using removable media
	- Revocation and suspension
		- All keys have finties life due to brute force
		- Revoked (permanent)
		- Suspended (temporary): Can be reactivated
			- Loss of device then found
		- CRL Certificate Revocation List
			- Issue by CA who issued CA
			- Published periodically
			- Time gap between CRL and client downloading
		- OCSP (Online Certificate Status Protocol)
			- List of not valid certificates
			- Generated and published immediately
			- Database can be queried 24/7
	- Certificate Stapling
		- Certificate containes a time-stamped OCSP response
		- Owner pays for stapling
	- Certficiate Pinning
		- Allow list of digital certificates
		- Only pinned certificates are trusted
		- Used in hostile enironment or need to be 100% sure of remote host identity
	- Common cryto best practices
		- Use trusted CA
		- Validate certificate chains
		- consider OCSP
		- Key management
		- MSSP (third party PKI management)














# Things to look at
SOAP injection - XML

bluesnarfing - bluetooth prank
blujacking - bluetooth steal data
dragonblood - timing based side channel attack against WPA3

DNS hijacking

Warning levels (4 warning)
SOAR - 
Cloud Access Security Broker CASB

AEAD Authenticated Encryption with Associated Data - AES-256-GCM

Infrastructure as code

Function as a service (AWS lambda)

HSM - Hardware security modules??

WS Security: SOAP extension published by OASIS used to enforce web confidentiuality and integrity security

Amazon web service: **Cognito** Create SSO solutions

HOTP

IEE 802.1xEOPL

federation Protocols