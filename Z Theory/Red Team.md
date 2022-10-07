# Fundamentals 
## Phases of Pen test
- Vulnerability scan to identify
- Establish measures to protect the network
- Evaluate how an attacker could profit off of vulnerabilities
- Exploit
- Post exploitation

## Limitations in Pen test
- Time
- Budget
- Limited scope
- non-disruptive
- Heavy IT focus

## Red Team Engagements
- Red vs blue to get to some defined crown jewl or flag
- Shows defensive ability to **detect and respond**
- Simulate TTP's (Tactics, Techniques and Procedures) of attackers for blue to learn from
- Also use:
	- Technical Infrastructure
	- Social Engineering
	- Pysical Intrusion
- Can be run as:
	- Full engagement
	- Assumed breach
	- Table-top exercise

## Teams and Functions:
![[../ZZ - Pasted Images/Pasted image 20220930133412.png]]

## Engagement Structure

| Technique| Purpose| Examples|
| --- |--- | --- |
|Reconnaissance| Obtain information on the target |Harvesting emails, OSINT
|Weaponization |Combine the objective with an exploit. Commonly results in a deliverable payload.|Exploit with backdoor, malicious office document
|Delivery| How will the weaponized function be delivered to the target|Email, web, USB
|Exploitation |Exploit the target's system to execute code| MS17-010, Zero-Logon, etc.
|Installation |install malware or other tooling |Mimikatz, Rubeus, etc.
|Command & Control |Control the compromised asset from a remote central controller| Empire, Cobalt Strike, etc.
|Actions on Objectives |Any end objectives: ransomware, data exfiltration, etc.| Conti, LockBit2.0, etc.


# Engagements
- Scope and objectives
	- Need to define concrete objectives and expectations
	- Decide how focused the assessment will be
	- Well defined scope
		- Can or cannot do or target

## Rules of Engagement

|**Section Name**| **Section Details**|
| ---|---|
|Executive Summary | Overarching summary of all contents and authorization within RoE document  
|Purpose |Defines why the RoE document is used
|References|Any references used throughout the RoE document (HIPAA, ISO, etc.)  
|Scope|Statement of the agreement to restrictions and guidelines  
|Definitions|Definitions of technical terms used throughout the RoE document  
|Rules of Engagement and Support Agreement|Defines obligations of both parties and general technical expectations of engagement conduct  
|Provisions|Define exceptions and additional information from the Rules of Engagement  
|Requirements, Restrictions, and Authority |Define specific expectations of the red team cell  
|Ground Rules|Define limitations of the red team cell's interactions  
|Resolution of Issues/Points of Contact|Contains all essential personnel involved in an engagement  
|Authorization|Statement of authorization for the engagement  
|Approval |Signatures from both parties approving all subsections of the preceding document  
|Appendix|Any further information from preceding subsections

[ROE Template](https://redteam.guide/docs/templates/roe_template/)

## Conops
Concept of Operations
- Details a high level overview of the proceedings of engagement
- Assume reader has minimal technical experience
- Componets:
	- Client Name
	- Service Provider
	- Timeframe
	- General Objectives/Phases
	- Other Training Objectives (Exfiltration)
	- High-Level Tools/Techniques planned to be used
	- Threat group to emulate (if any)

## Resource Plan

Usually written as bullet points

Example template:
-   Header
    -   Personnel writing
    -   Dates
    -   Customer
-   Engagement Dates
    -   Reconnaissance Dates
    -   Initial Compromise Dates
    -   Post-Exploitation and Persistence Dates
    -   Misc. Dates
-   Knowledge Required (optional)
    -   Reconnaissance
    -   Initial Compromise
    -   Post-Exploitation
-   Resource Requirements
    -   Personnel
    -   Hardware
    -   Cloud
    -   Misc.

## Operations Plan

- Considered from a business and client perspective
- Specific details of engaement and actions occuring
- Done in bullet points

Template:

-   Header
    -   Personnel writing
    -   Dates
    -   Customer
-   Halting/stopping conditions (can be placed in ROE depending on depth)
-   Required/assigned personnel
-   Specific TTPs and attacks planned
-   Communications plan
-   Rules of Engagement (optional)

Comms plan:
- How red cell communicates with other cells

## Mission Plan

Actions to be completed by operators
From red cell and operator perspective

Minimum details is:
-   Objectives
-   Operators
-   Exploits/Attacks
-   Targets (users/machines/objectives)
-   Execution plan variations

# Threat Intel
(TI) or Cyber Threat Intelligence (CTI)

- Info and TTPs (tactics, techniques and procedures) attributed to an adversery
- Distributed by ISACs (Information and Sharing Analysis Centers)

## TIBER-EU Framework

- **TIBER-EU** (**T**hreat **I**ntelligence-**b**ased **E**thical **R**ed Teaming) is a common framework developed by the European Central Bank that centers around the use of threat intelligence.

![](../ZZ%20-%20Pasted%20Images/Pasted%20image%2020221001084819.png)

## TTP Mapping

Example: APT 39, run by Iranian ministry

## Kill chain to MITRE

|**Cyber Kill Chain**|**MITRE ATT&CK**|
|---|---|
|Recon|Reconnaissance
|Weaponization|Execution
|Delivery|Initial Access
|Exploitation|Initial Access
|Installation|Persistence / Defense Evasion
|Command & Control|Command and Control
|Actions on Objectives|Exfiltration / Impact

PowerShell, Spearphishing Attachment, External Remote Services, BITS Jobs, DNS, Keylogging

# OPSEC
 OPSEC is a process to _identify_, _control_ and _protect_ any information related to the planning and execution of our activities.
 
The OPSEC process has five steps:

1.  Identify critical information
2.  Analyse threats
3.  Analyse vulnerabilities
4.  Assess risks
5.  Apply appropriate countermeasures

## Critical Information
- In terms of red team it is the info that if the blue team were to obtain it, would hinder or degrade the red team's mission
- jeopardises your plans if leaked to an adversary
- Could include:
	- Client info your team has learned
	- Plans and capabilites
	- TTP's
	- Cloud provider / C2 network
		- e.g Pentoo
	- public IP address / domain names / hosted websites