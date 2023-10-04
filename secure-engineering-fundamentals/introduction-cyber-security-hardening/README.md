# Introduction to cybersecurity hardening
In these notes, we'll explore **cybersecurity hardening** guidelines and baselines for some of the standard frameworks you may find. We'll go over some hardening practices for **networking**, **windows servers** and **workstations**, **active directory** security, some **Linux** environments, and an introduction to **printers**, **IoT** and **industrial security**

## What is security hardening?
Security hardening is a term that describes all **tools**, **techniques** and **best practices** that we apply to reduce security risk by minimizing attack surface, also helping with security compliance and auditing. Examples **are removing extra functions** or applications, **disabling unnecessary services**, or **changing default passwords** and accounts. **Not all hardening involves technical controls**, some changes are cultural or behavior-based!

We can't protect everything, so we need to have awareness of what our current attack vectors are so we can **focus on the biggest risks** in our environment. 

## General hardening guidelines
Some general guidelines you can use when hardening:
- Use a **checklist** to keep track of usual tasks
- Create, use, and verify **baselines**
- Routinely **audit** systems
- Have proper **inventory** management
- Have, as we discussed previously, a proper **change management** process
- Patch the **low-hanging fruits**!
  - Change **default passwords**
  - Close **unnecessary ports**
  - Stop **unneeded services**

**Any** software, hardware, and system can be hardened. **There are always improvements** to be made from the baseline. Especially on vendor systems, **verify** what their hardening is and what you can improve upon. **Document** verifications so there is a paper trail for auditing.

## Guidelines, baselines and frameworks
### Security baselines
Security baselines are the **starting points** we use for comparison, the "normal". What we use to understand if a system has changed. They are usually formally documented. **Automated systems** usually help manage this baseline monitoring, as when a new system is built, we can apply the baseline expectations to it and **understand what we can expect** of that system.

These baselines are **critically important for proper hardening**, as we explained with our hardening checklist topic. We can automate compliance monitoring and remediation with **Security Content Automation Protocol**, a set of open standards and applications we can use for this purpose. These tools run a scan of our systems against a set of **security standards** and return a **score** to quickly evaluate our security posture. This greatly assists with meeting regulatory requirements for compliance.

### Guidelines and frameworks
These security baselines get compared against a set of **guidelines and frameworks**, security risk assessment guides that helps us **understand our security posture**. They are based on existing and updated **security practices**, and give cybersecurity a commonn organizing structure.

These have three main components:
1. the **Core**, the set of desired activities and outcomes that guides organizations in managing and reducing risk. It provides guidance for developing organizational risk profiles
2. the **Implementation tiers**, which help provide context on how to view risk management and guides organizations to consider appropiate effort
3. the **Profiles**, used to identify and prioritize actions

Some organizations, like the Center for Internet Security, offer **resources** to help with compliance:
- **CIS controls**, which are recommended sets of actions for general cyber defense
- **CIS benchmarks**, configuration guidelines for multiple specific widespread products
- **CIS Hardened images**, pre-hardened images of popular systems according to their benchmarks

## Cybersecurity hardening
### Network perimeter
Network perimieters are our **first line of defense** against attackers. It contains firewalls, public access resources and VPN access points, so it needs to be properly secured and hardened. Common techniques and practices are:
- Block unnecessary inbound and outbound traffic
  - Block inbound **RDP**. Sometimes outbound depending on your environment
  - Block **SMB** (file sharing protocol), both inbound and outbound, it's almost never required
  - SMTP, your local network probably does not need to send or receive emails unless it's an email appliance
- Have HTTPS for all your sites so traffic is encrypted and private
- Disable any insecure management protocols on appliances, like Telnet and older versions of SNMP, or plain versions of FTP which are unencrypted
- All email traffic should flow through your email security appliance to avoid malware or harmful documents sent through email
- Any type of access from external networks should require multi-factor authentication
- Do not open system management interfaces to the internet
- Keep your DMZ systems patched and up to date

### Securing network devices
One important part of network hardening is **properly configuring your network appliances** like routers, switches and firewalls. Some important recommendations are:
- **change the default password** on the appliance
- **Use secure protocols to access** them, like using SSH or pyisical management interfaces instead of telnet, and transfer files using SCP instead of FTP, and keep the network management protocols like SNMP on a whitelist basis
- **Disable unused services** so the attack surface is reduced
- **Configure central authentication** so access can be managed without depending on the device and you can see all accesses on a single place
- Enable logging and monitor the baseline behavior of the appliance
- **Ensure the system is patched and up to date** so you get security fixes and new security features
- **Implement redundancy** and high availability in case of a problem
- For **wireless access points**, keep the minimum services enabled and configure a secure authentication protocol, like WPA2 pre-shared key or WPA2-Enterprise so your user needs to authenticate using their Active Directory user
- If the devices are static, implement **MAC address filtering** policies so no unknown devices can connect through a port

## Hardening Windows servers
Windows environments are very common in on-premise server environments especially. Here's some notes about securing them:
- Many settings are **secure by default**, but remember to **verify** that this applies
- Take into account if the server is **standalone** or **domain-joined**, which changes what we should be managing and where, like AD-managed or local accounts, centralised or local GPOs
- Don't **assume** anything - if you didn't configure it, **check** everything just in case
- Apply any of the open **checklists** for system hardening, like the ones offered by NIST
- Take a pass with the [Windows Security baselines and compliance toolkit](https://www.microsoft.com/en-US/download/details.aspx?id=55319)
- Always make sure systems are properly **patched** and **up to date**
- Create **new local administrative accounts**, change their **passwords**, and **disable the built-in administrative account** to avoid having a known account attackers can exploit
- Use **complex, lengthy passwords** to protect accounts, and **rotate them** routinely
- use a **LAPS** (Local Administrator Password Solution) that automatically does this password management for you and stores it on AD for administrators to use
- **Apply hardening group policies** to your organization: password requirements, audit log rules
- Keep the **local windows firewall** enabled, continuously verify it's enabled
- Keep **windows defender** or other **AV**/**EDR** solutions on your system so you can monitor for malicious activity
- **Disable unnecessary services** you're not using and verify they stay off
- If you don't need internet access on a server, **block access to external networks** from it, preferably with a web filtering appliance and not from the server itself
- Apply **application whitelisting** to make sure the servers only run what you expect them to run and no unexpected, unwanted processes are on the system
- **Keep proper logging and auditing** policies and **check those logs** often to make sure there is nothing unexpected going on, having those logs on a centralized repository
- **Apply encryption** where possible, for example using Bitlocker

## Active Directory
Active Directory is the Microsoft product used to **manage a Windows environment**. Essentially, it's a **database** and a **set of services** used to hold environment information like **users**, **computers**, **roles** and their **permissions**, and controls much of a windows network in a centralised way with the **Domain Controllers** (the windows servers that manage the domain). As Active Directory involves many products and services, there are some hardening guidelines we should always follow:
- Make sure you **control access to privilege accounts**, and **recreate** them to avoid well-known account IDs. These users have elevated access to the environment and if leaked can be a dangerous tool for attackers. There are different types of privileged accounts:
  - **Permanent**, which always have these permissions due to the role they have attached, generally have access to the entire environment
  - **Privilege-attached**, which are given administrative access on certain domain parts, like certain machines
- **Separate out privileged roles**, make sure you control who has it and why. Make sure no one is member of all the groups *Domain Admin*, *Enterprise Admin* and *Schema Admin*, so even in elevated access, there is still some separation of duties
- Give elevated access **only when needed**, and **remove it afterwards** when it is not used anymore
- **Regularly verify permissions** and roles in the organization. Check for **unusual password resets** and **group membership changes**
- **Use managed service accounts** for applications that need Active Directory access, so you don't need to manage credentials for that account automatically and coordinate password changes without your interaction
- Make sure local administrators use a **different password on each endpoint**, so if one is compromised, no other workstations are affected, this can be made easy with the LAPS tool we mentioned earlier
- **Limit user access** to local administrator on their workstation
- Be careful with giving C-level users or VIPs **excessive permissions**, they are more open to social engineering attacks that can exploit them
- **Secure administrative workstations**, physical or virtual, so privileged access-capable machines are especially cared for. Restrict them to certain expected users, and make sure administrative users can only log in from the administrative machines
- Ideally, run domain controllers as **separate physical hosts**, and if possible, **use Server Core deployments** which have a lot less potentially insecure elements installed by default
- Apply windows server **standard hardening guidelines** provided by open organizations
- **Install only the absolutely necessary tools** on domain controllers, do not install anything that does not support being a domain controller
- **Heavily restrict remote access** to administrative machines, and **block internet access** to your domain controller if possible
- Set up a **RODC** (**Read-Only domain controller**) used in smaller offices, used to check data locally without having access to changing organization configuration when it's not needed

## Windows workstations and applications
We have talked a lot about server hardening on windows, but almost just as important is **hardening your workstations** that your team uses, as they are a much bigger attack surface. Here are some guidelines you should follow:
- As mentioned before, **heavily control access to administrative accounts** and centrally manage them. Replace the local administration account to replace its SID so the attackers can't exploit knowing it
- **Disable any services** that are not used in workstations
- Keep the endpoint **firewall** properly configured
- **Restrict RDP access**, generally remote desktop to endpoints are not necessary, and if needed, keep it only from verified endpoints
- Apply application whitelisting, though this one might be harder on endpoint workstations
- Keep **antivirus and EDR solutions** on all your endpoints running
- **Do not give** end users administrative access. This both limits what end users can do, and controls that malware that may get to the workstation cannot escalate permissions to local administrator
- **Encrypt all data** on the endpoints so you protect PII in case of physical compromise, like using Bitlocker to encrypt the entire system drive, and can make the endpoint ask for a password on startup before Windows actually boots
- **Manage what browsers are allowed** on endpoints so you can make sure users are going through your set browser security policies, and that the used browsers can be centrally managed for enterprise deployments
- **Manage browser add-ons** so you install all necessary tools automatically, and prevent users from installing non-approved add-ons that could be malicious
- **Prevent password saving** to the browser, which is usually used by attackers, who dump browser files that store those passwords and can potentially be leaked
- **Block access to certain sites** deemed unnecessary or a risk in your environment
- **Whitelist only necessary software** so no malware or unwanted software can run on the endpoints and represent a risk, you can use tools like Microsoft AppLocker (legacy, windows 10 pre-1903) or Defender Application Control (new, supported). This software also allows controlling application reputation, drivers installed, or codesigning certificates
- If you need to allow **PowerShell**, **only allow digitally signed scripts** from a trusted third party, like your administration team, and keep execution logging and auditing enabled, or even keep a list of whitelisted scripts. Additionally, keep it locked under authentication and authorization and allow it only on endpoints that need it.

## Linux hardening
Most endpoint machines in an enterprise will probably use Windows, but a lot of server environments and some desktops may run **Linux**. **Linux hardening** is fundamentally **different** in practices than Windows, but we can have some **similar recommendations**:
- Use a **checklist**! the usual security awareness organizations like NIST have checklists for Linux as well that you can use
- If the system is headless, access it with **secure protocols**, like SSH for shell or SCP/SFTP for file transfers. Avoid accessing using just passwords and **use public key authentication**, and give that key only to whoever needs it
- **Uninstall insecure management methods**, like telnet and plain ftp
- **Enable and configure SELinux** (security-enhanced linux) to give further access controls to the system
- Configure access control tools that **detect and block attacks**, like fail2ban to block bruteforce attacks
- Try to **avoid using the `root` user** as much as possible. use the `sudo` tool when possible, and consider disabling the root user entirely, especially on SSH connections
- **Configure the system firewall** to harden the system. Generally this will be iptables or nftables
- Be careful with **files that anyone can write or execute**, as they can be potential attack vectors

## Other endpoints and systems
Apart from windows and linux endpoints and servers, corporate environments have **other devices** we should go over that should be secured:

### Printers
- If possible, **use a central print server** that helps manage printers into their own network. They should only accept printing jobs from this print server
- Ensure **administrative access** to the printer is restricted
- **Change default credentials** on all printers
- **Change and harden** the default SNMP settings if the printer has this service
- Ensure the printers' **firmware is always up to date** to avoid known vulnerabilities
- **Disable unnecessary protocols** that you don't use on them (bluetooth, wireless)
- If the printer is multi-function, **disable functions that are not used** (faxing, for example), and ensure sensitive scanned information is not kept on printer memory

### IoT devices
- Make sure that **IoT devices you can't validate** are hardened: thermostats, media devices like Apple TVs or chromecasts, security cameras, doorbells, smoke detectors, smart locks...
- Follow the same **general guidelines** of other devices when possible
- **Network segmentation** is critical and a good help for these devices. If possible, disallow access to the enterprise network entirely
