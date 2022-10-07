# AD Basics
## AD Objects
Users are one of the objects known as security principles
- Can be authenticated by the domain and assigned privileges

Machines
- Every computer that joins AD will cause a machine object to be created
- Also are security principles and assigned an account
-  a machine named `DC01` will have a machine account called `DC01$`.

**Security groups**
[Default Security Groups](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-security-groups)

|**Security Group**|**Description**|
|---|---|
|Domain Admins|Users of this group have administrative privileges over the entire domain. By default, they can administer any computer on the domain, including the DCs.
|Server Operators|Users in this group can administer Domain Controllers. They cannot change any administrative group memberships.
|Backup Operators|Users in this group are allowed to access any file, ignoring their permissions. They are used to perform backups of data on computers.
|Account Operators|Users in this group can create or modify other accounts in the domain.
|Domain Users|Includes all existing user accounts in the domain.
|Domain Computers|Includes all existing computers in the domain.
|Domain Controllers|Includes all existing DCs on the domain.

## Group Policy Objects GPOs

GPOs are distributed to the network via a network share called `SYSVOL`, which is stored in the DC. All users in a domain should typically have access to this share over the network to sync their GPOs periodically. The SYSVOL share points by default to the `C:\Windows\SYSVOL\sysvol\` directory on each of the DCs in our network.

force update
```cmd
gpupdate /force
```

### GPO Policies

Group Policies are held in OU "Group Policy Objects" and then linked to the desired OU's.

Computer Configuration GPO settings are ignored by user accounts. So you can add computer configurations at root level without affecting users.

Password policy
Computer Configurations -> Policies -> Windows Setting -> Security Settings -> Account Policies -> Password Policy

Control Panel access
User Configuration -> Policies -> Administrative Templates -> Hide specified Control Panel items


## Authentication

-   **Kerberos:** Used by any recent version of Windows. This is the default protocol in any recent domain.
-   **NetNTLM:** Legacy authentication protocol kept for compatibility purposes.

### Kerberos
Users who log into a service using Kerberos will be assigned tickets.
 Users with tickets can present them to a service to demonstrate they have already authenticated into the network before and are therefore enabled to use it.
 
1.  The user sends their username and a timestamp encrypted using a key derived from their password to the **Key Distribution Center (KDC)**, a service usually installed on the Domain Controller in charge of creating Kerberos tickets on the network.
    
    The KDC will create and send back a **Ticket Granting Ticket (TGT)**, which will allow the user to request additional tickets to access specific services. The need for a ticket to get more tickets may sound a bit weird, but it allows users to request service tickets without passing their credentials every time they want to connect to a service. Along with the TGT, a **Session Key** is given to the user, which they will need to generate the following requests.
    
    Notice the TGT is encrypted using the **krbtgt** account's password hash, and therefore the user can't access its contents. It is essential to know that the encrypted TGT includes a copy of the Session Key as part of its contents, and the KDC has no need to store the Session Key as it can recover a copy by decrypting the TGT if needed.
    

![Kerberos step 1](https://tryhackme-images.s3.amazonaws.com/user-uploads/5ed5961c6276df568891c3ea/room-content/d36f5a024c20fb480cdae8cd09ddc09f.png)

3.  When a user wants to connect to a service on the network like a share, website or database, they will use their TGT to ask the KDC for a **Ticket Granting Service (TGS)**. TGS are tickets that allow connection only to the specific service they were created for. To request a TGS, the user will send their username and a timestamp encrypted using the Session Key, along with the TGT and a **Service Principal Name (SPN),** which indicates the service and server name we intend to access.
    
    As a result, the KDC will send us a TGS along with a **Service Session Key**, which we will need to authenticate to the service we want to access. The TGS is encrypted using a key derived from the **Service Owner Hash**. The Service Owner is the user or machine account that the service runs under. The TGS contains a copy of the Service Session Key on its encrypted contents so that the Service Owner can access it by decrypting the TGS.
    

![Kerberos step 2](https://tryhackme-images.s3.amazonaws.com/user-uploads/5ed5961c6276df568891c3ea/room-content/84504666e78373c613d3e05d176282dc.png)

5.  The TGS can then be sent to the desired service to authenticate and establish a connection. The service will use its configured account's password hash to decrypt the TGS and validate the Service Session Key.

![Kerberos step 3](https://tryhackme-images.s3.amazonaws.com/user-uploads/5ed5961c6276df568891c3ea/room-content/8fbf08d03459c1b792f3b6efa4d7f285.png)

NetNTLM Authentication

NetNTLM works using a challenge-response mechanism. The entire process is as follows:

![NetNTLM authentication](https://tryhackme-images.s3.amazonaws.com/user-uploads/5ed5961c6276df568891c3ea/room-content/2eab5cacbd0d3e9dc9afb86169b711ec.png)

1.  The client sends an authentication request to the server they want to access.
2.  The server generates a random number and sends it as a challenge to the client.
3.  The client combines their NTLM password hash with the challenge (and other known data) to generate a response to the challenge and sends it back to the server for verification.
4.  The server forwards the challenge and the response to the Domain Controller for verification.
5.  The domain controller uses the challenge to recalculate the response and compares it to the original response sent by the client. If they both match, the client is authenticated; otherwise, access is denied. The authentication result is sent back to the server.
6.  The server forwards the authentication result to the client.

### NetNTLM Authentication
NetNTLM works using a challenge-response mechanism. The entire process is as follows:

![NetNTLM authentication](https://tryhackme-images.s3.amazonaws.com/user-uploads/5ed5961c6276df568891c3ea/room-content/2eab5cacbd0d3e9dc9afb86169b711ec.png)

1.  The client sends an authentication request to the server they want to access.
2.  The server generates a random number and sends it as a challenge to the client.
3.  The client combines their NTLM password hash with the challenge (and other known data) to generate a response to the challenge and sends it back to the server for verification.
4.  The server forwards the challenge and the response to the Domain Controller for verification.
5.  The domain controller uses the challenge to recalculate the response and compares it to the original response sent by the client. If they both match, the client is authenticated; otherwise, access is denied. The authentication result is sent back to the server.
6.  The server forwards the authentication result to the client.

Note that the user's password (or hash) is never transmitted through the network for security.

**Note:** The described process applies when using a domain account. If a local account is used, the server can verify the response to the challenge itself without requiring interaction with the domain controller since it has the password hash stored locally on its SAM.
# Structure
## Domain Structure
### Tree
Has domain admins and enterprise admins who have control over everything in the enterprise (all domains)
![](../ZZ%20-%20Pasted%20Images/Domain%20Tree.png)

### Forest
Different namespaces
![](../ZZ%20-%20Pasted%20Images/Domain%20Forest.png)

### Trust Relationship
In simple terms, having a trust relationship between domains allows you to authorise a user from domain `THM UK` to access resources from domain `MHT EU`.
The direction of the one-way trust relationship is contrary to that of the access direction.
Once a trust relationship is established, you have the chance to authorise users across different domains, but it's up to you what is actually authorised or not.
![](../ZZ%20-%20Pasted%20Images/Domain%20Trust%20Relationship.png)

-   Trees - A hierarchy of domains in Active Directory Domain Services
-   Domains - Used to group and manage objects 
-   Organizational Units (OUs) - Containers for groups, computers, users, printers and other OUs
-   Trusts - Allows users to access resources in other domains
-   Objects - users, groups, printers, computers, shares
-   Domain Services - DNS Server, LLMNR, IPv6
-   Domain Schema - Rules for object creation

## User Structure
-   Domain Admins - This is the big boss: they control the domains and are the only ones with access to the domain controller.
-   Service Accounts (Can be Domain Admins) - These are for the most part never used except for service maintenance, they are required by Windows for services such as SQL to pair a service with a service account
-   Local Administrators - These users can make changes to local machines as an administrator and may even be able to control other normal users, but they cannot access the domain controller
-   Domain Users - These are your everyday users. They can log in on the machines they have the authorization to access and may have local administrator rights to machines depending on the organization.

# Groups
-   Security Groups - These groups are used to specify permissions for a large number of users
-   Distribution Groups - These groups are used to specify **email distribution lists**. As an attacker these groups are less beneficial to us but can still be beneficial in enumeration

Default Security groups
-   Domain Controllers - All domain controllers in the domain
-   Domain Guests - All domain guests
-   Domain Users - All domain users
-   Domain Computers - All workstations and servers joined to the domain
-   Domain Admins - Designated administrators of the domain
-   Enterprise Admins - Designated administrators of the enterprise
-   Schema Admins - Designated administrators of the schema
-   DNS Admins - DNS Administrators Group
-   DNS Update Proxy - DNS clients who are permitted to perform dynamic updates on behalf of some other clients (such as DHCP servers).
-   Allowed RODC Password Replication Group - Members in this group can have their passwords replicated to all read-only domain controllers in the domain
-   Group Policy Creator Owners - Members in this group can modify group policy for the domain
-   Denied RODC Password Replication Group - Members in this group cannot have their passwords replicated to any read-only domain controllers in the domain
-   Protected Users - Members of this group are afforded additional protections against authentication security threats. See http://go.microsoft.com/fwlink/?LinkId=298939 for more information.
-   Cert Publishers - Members of this group are permitted to publish certificates to the directory
-   Read-Only Domain Controllers - Members of this group are Read-Only Domain Controllers in the domain
-   Enterprise Read-Only Domain Controllers - Members of this group are Read-Only Domain Controllers in the enterprise
-   Key Admins - Members of this group can perform administrative actions on key objects within the domain.
-   Enterprise Key Admins - Members of this group can perform administrative actions on key objects within the forest.
-   Cloneable Domain Controllers - Members of this group that are domain controllers may be cloned.
-   RAS and IAS Servers - Servers in this group can access remote access properties of users


# Trusts
![](../ZZ%20-%20Pasted%20Images/Pasted%20image%2020221007072915.png)
# Domain Controller
## Active Directory Data Store
holds the databases and processes needed to store and manage directory information such as users, groups, and services.
-   Contains the NTDS.dit - a database that contains all of the information of an Active Directory domain controller as well as password hashes for domain users
-   Stored by default in %SystemRoot%\NTDS
-   accessible only by the domain controller
# Breaching AD

-   NTLM Authenticated Services
-   LDAP Bind Credentials
-   Authentication Relays
-   Microsoft Deployment Toolkit
-   Configuration Files

###  NTLM Authenticated Services
New Technology LAN Manager (NTLM)