# Introduction to security engineering
For this starting section we will be taking a look at what **security engineering** exactly is, what common threats we may face in order to properly defend against them, and look at an example threat scenario. This will help us **establish a proper knowledge baseline** for the rest of the notes.

## What is security engineering?
Security engineering is a **technical position** within a company, a role, intended to **develop and enforce security plans and procedures** to defend against potential threats. This involves **proactive work** as the environment and threats evolve, with **implementation of procedures**, **configuration of services** and environments, and **threat monitoring**. It also involves **incident response** if something goes wrong.

Some example responsibilities are:
- **configure** security controls
- **Set up** security systems and appliances
- **Assist** with policy creation
- **Manage** and tweak security controls
- **Educate** the rest of the company

## The threat landscape
One of the largest threats today is **email**. Mainly, phishing. It is usually the main entry point of most attacks to an organization, and continues to be an issue to this day. With these stolen, phished credentials, an attacker can start moving into a company. On a similar, more technical note, **misconfigured access to resources** is currently considered one of the biggest threats right now.

## To keep in mind
There are three things that you need to keep in mind when doing security engineering implementation:
- **Budget**: Every team has a set budget from the company, and you need to keep it in mind when exploring tools and appliances
- **Acceptable level of risk**: Not all risks may be worth protecting against. You cannot be 100% secure, choose your battles
- **not "if", but "when"**: Have the mindset that attacks and breaches **will** happen, and plan for that

## Sample attack scenario
Let's see an **example of an attack scenario** we may see. Let's take Ivan. Ivan works at Cognito Inc. An email with **phishing** reached him, he clicked on the page and asks him for **credentials**. He submits these credentials.

After this, an **attacker** that sent this email gets back these credentials from Ivan. As Ivan does not have MFA configured, the attacker can log into the company VPN and access the **internal network** of Cognito Inc.

This is why **defense-in-depth** is so important, something we will get further into in the rest of these notes.

## Perimeter security
There are several definitions for what a **network perimeter** is, but for our purposes, we will use our perimeter firewall, the network hardware in the DMZ (webservers, VPN servers, email servers), and our dmz-to-internal network firewall.

### The firewall
We will start out looking at **what a firewall is**. A firewall's task is to **monitor network traffic** and **permit or deny** it based on rules: **sources**, **destinations**, **ports**, **intelligence** or **analytics**. These are usually used as a check wall to **separate networks by type** (internet, DMZ, internal). They are used as a **first line of defense**. There are several types of firewalls, including **web application firewalls** or **next generation firewalls**.

There are several **low-hanging fruits** we should heavily block with a firewall, like **direct RDP** or **email directly from workstations**. Essentially anything that is not necessary for operation. The less threat surface, the better.

### The DMZ
In network and computing terms we usually have a **DMZ**, a **buffer zone**, where we keep **publicly accessible resources** from our network. This network segment usually holds elements like **email transport servers**, **VPN servers**, or **webservers**. We want these resources **separate** because if one of these are compromised, we should have **very strict rules** so they can't access internal network resources.

Email appliances are **usually very targeted**, since phishing is such a **common attack** vector we see in the threat landscape. This is why we need to **heavily protect** these in terms of networking, but also have **spam filters**, identify and potentially **block marketing and bulk emails**, scan for threats like **malicious attachments**, or try to detect **social engineering** attempts. **Data loss prevention** capabilities in case of document and intellectual property leakage is also useful to have.

Another of the potential attack targets are **remote access tools**, like **VPNs** used to connect networks together in a secure and validated way, or storefront tools used to **directly access machines** like **Citrix** or **Remote Desktop Protocol**. For these tools, **MFA should always be used**, wether it's **SMS**, **one-time tokens**, **push notifications** or **hardware tokens** such as a Yubikey.

## Detection and prevention
In the case traffic does go in from the internet or the DMZ to the internal network, or if we monitor DMZ traffic, we should have an **Intrusion Detection/Prevention system** (IDS/IPS) in place. These are pieces of **software** or **appliances** that **monitor traffic**, **alert** that there is an anomaly going on, and in the case of the IPS, **block** it from continuing.

These tools also have two variants, one **network**-based (monitoring local network traffic through that segment), and **host**-based (monitoring what is going on in that specific host).

## Network security
Network security is divided into several defensive techniques:
- Network **segmentation**, which helps with isolation, containing attacks, prevents users from accessing unwanted resources (separation of duties, following least privilege), and can be done with multiple methods (ACLs, VLANs, Network Access Control)
- Web **filtering**, used for both technical and management purposes. We use it to block malicious sites and ads, NSFW content, to stop potential data leakage, or to restrict web browsing by role or position. This is normally done on internal networks, and it involves user identification and web access logging

### Untrusted vs Trusted networks
Networks can be considered either **untrusted** or **trusted**. Trusted networks are made up of interconnected devices used by **authorized** users, and are **administratively managed**. Untrusted networks, on the other hand, are **outside of the network perimiter** we control and manage, typically **unsecured**, **public** networks.

### Active Directory
In a way, Active Directory helps protect network assets, since it helps us apply **resource access policies at scale** on the devices in an environment. Password protection, group policies (restricting access to workstations, managing firewall, enforcing encryption, setting password expiry policies...) and account management are examples of what we can use this technology for.

## Endpoint security
There are several policies we apply to endpoints to implement a proper security policy:
- follow the **least privilege principle**, only giving the users accesss to the workstations they need, and the workstations access only to the resouces required, nothing more
- for **local administrators**, manage them centrally, do not give local admin to end-users, limit the access to it and audit its usage, and if it can be avoided, don't log directly into the workstation as local admin, using access elevation instead
- use **group policies**, which allow you to centrally manage the security baseline for all of your resources in the organization easily
- Keep **User Account Control** enabled, which will limit application access to privileged resources and helps protect against malicious processes
- Use **anti-virus** (signature-based, for known malware) and **advanced malware protection** (behavior-based, for unknown malware). We can apply policies to these, like requiring a password to uninstall it, to protect its integrity
- Make sure devices use **encryption**, for the system drive, any external drives holding data, and for PII and confidential data itself
- Use **data loss prevention** software that prevents sensitive information like personally identifiable information from exiting tyour system. The main exit points are usually email, removable media and cloud storage. These data leaks can be either accidental or malicious

### Virtual desktop infrastructure
A way to protect and centrally manage desktops is to use **VDI**. This is software that **centrally hosts desktop virtual machines** that can be accessed via thin clients holding no data. This allows for **easy deployment**, **central updating** of instances, and allows us to easily **delete and redeploy compromised workstations** with ease.
