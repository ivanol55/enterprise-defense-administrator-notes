# Introduction to identity and access management
On these notes we will explore what **identity and accesss management is**, authentication types available, password management fundamentals and just-in-time access, and authorization management on top of authentication. We will learn to manage **who** someone is, and **what** they can do, and that we know how to **check what they are doing**.

## Identity and Access Management basics
Identity is, essentially, what we use to **know who someone is** when trying to access a system. This identity is not necessarily private information, called **identification**, but **authentication**, the method or process where someone's identity is proven and verified, should be guarded carefully.

### Authentication
Authentication is usually handled by **credentials**, like passwords, PIN codes, biometrics, or cryptographic keys. Ideally we use more than one method of authentication, known as multi-factor authentication, for example, a PIN and a one-time use code.

### Example scenario
Let's set a scenario for the process of accessing a system with AAA (Authentication, Authorization, Accounting):
1. User attempts to access a system, providing **identity** (a username)
2. Credentials to **verify** the identity are provided (password, PIN code, MFA if required)
3. Authorization checks are run, to check if the authenticated user has **authorization** to run that action, for example with an access control list to the requested resource
4. Access is confirmed and logged for **accounting and auditing**

### Authentication, Authorization and Accountability
The **objective of IAM management** is that only the authenticated individuals can access the systems, and that they can only access the systems that they need to, nothing more. We also need to make sure these credentials are monitored and protected. This is achieved through **authentication**, **authorization** and **accountability**.

- **Authentication** verifies that the user is who they say they are through a number of knowledge-based tokens or keys, like a password and a physical security key. If required, we add something the user *is*, like biomietrics or behavior.
- **Authorization**, which ensures that identity only has access to the resources it needs to access. This is going to be a changing, ongoing condition process that evolves as necessities change. It occurs every time someone tries to access a resource. Accesses can be managed by the owner of the resource, or by a system administrator, and are given to users, groups or roles.
- **Accountability**, which after an action, tracks that that action was done in a logging location that can be checked later for auditing and security monitoring. These help us detect intrusions, monitor for suspicious activity, assist in incident response, and track actions back to individual identities. In a legal case, this information will serve as proof of changes, and the knowledge of these logs deter possible malicious actions.

### AAA Lifecycle management
If someone new joins the organization or someone leaves, there needs to be a set of tools and processes to add or remove accesses as necessary:
- **Provisioning** resurces, like creating accounts, and assigning initial permissions
- **Access control**, where over time, permissions need to be changed and adjusted for that identity, also for compliance and auditing of changing permissions
- **Deprovisioning**, where credentials need to be revoked when the subject does not require that access anymore, either by deactivation, or future deletion


### Credential management
#### Authentication types
There are **several types of authentication types** available that get used in combination for security, like passswords and PINs (something you **know**), one-time passwords and rotating codes on a physical device, cryptographic keys, NFC or RFID cards (something you **have**), and biometrics (something you **are**, like fingerprints, facial scans, eye scanners, signature analysis, typing dynamics).

These are sorted from **less to more secure**, and **less to more complicated to implement** - passwords are easy to brute-force, but it's less likely your phone will be stolen for the multi-factor codes, and it's implausible someone will get an iris scan from you. For this reason, there are usually two of these implemented at the same time in an authentication process, like requiring a password and a hardware token to log in. Multi-factor authentication should also be used in critical systems, like remote access gateways or when accessing sensitive data

#### Password management
Passwords are one of, if not **the most common way of authentication** we will find in any organization. Passwords are **stored as one-way hashes** when an account is created, so the plaintext password is never stored. When the user wants to log in again, the password input is hashed and sent to compare with what is stored to check if the values match and the password is correct. These passwords should always be transmitted using secure methods on encrypted channels, like HTTPS and SSH.

Passwords have a chance of being **brute-forced**, if every combination is tested. If a password is not complex enough, it can be cracked very quickly, that is why our password policies should make users use strong. Rotating passwords too frequently can be counter-productive, as that will make users make weaker passwords they can remember.

Passwords should be **at minimum 8 characters long**, with a maximum of 64 as a reasonable limit for avoiding brute-forcing. You should allow (or even make a rule to use) **lower and upper-case letters**, **numbers**, **symbols** and **special characters**. If possible, **compare password hashes against compromised credential lists** and dictionaries. Account lockouts after a number of failed password attempts is a common practice.

These rules are better enforced using a **password manager**. This is a tool that will hold all of your long, secure passwords you don't need to remember, kept locked by a single **strong master password** you keep yourself. Keep very close control of the credentials for this password manager, **use multi-factor authentication**, and change it if it reports as compromised.

If the account is in your organization, use **assisted password reset**, where helpdesk should do the password resets on demand, educating users to never provide passwords over a phone, and having staff use verification questions and answers to make sure the user is who is requesting the password reset.

#### Just-in-time access
Some permissions need to be tightly controlled and only provided on-demand. This is where we use just-in-time access, like needing elevated access for installing software on a machine or performing administrative maintenance.

This system provides adiministrative or elevated access **for a certain amount of time**, for a **specific resource**, and only allowed for a **certain user**. This allows us to limit the potential damage to a system from a user with administrative access.

The process is usually:
1. The user who needs elevated acccess enters a **request** into the system, providing:
   a. **Time** needed for this task
   b. **System** that the action applies to
   c. The **specific action** requested
   d. **Justification** for the request
2. A manual or automatic process **approves or denies** the request, where automatic requests are pre-approved and go through automatically (but the trace of the request is kept)
3. If approved, **permissions are granted** only for what was requested
4. All actions during this event are **audited**
5. When finished, permissions are **revoked**

### Identity and authorization
#### Authorization mechanisms
There are many different ways that administrators can grant access to systems based on how they are implemented:
- **Discretionary access control** allows the owner of the resources to set the permissions for it, to assign accesses directly themselves, generally through access control lists (A, B and C users can only read, user D can read and write). It is a very common authorization system, but it presents a risk of abuse due to the lack of central management
- **Mandatory Access Control** is used in very specific circumstances, like sensitive systems and confidential data. In this model, the owner user does not have control over permissions, rather that is managed by the administrator, which is a lot more secure by design, and is built around using security labels to know what a user has access to based on clearence. An example is `SELinux`
- **Role-Based Access Control** (**RBAC**) is a centrally administrated manner of providing access, which sets accesses to resources and resource types based on their work role. The accesses are granted a specific role, which has the permissions needed for that role. This eases administration and management of access to resources
- **Attribute-Based Access Control** (**ABAC**) is less frequent, based on a set of attributes that need to match: Access is assigned based on who (clearance level, department, group membership) is accessing what (classification of sensitivity, tyoe of record), and to do what (read, write, comment). Sometimes that includes when and where from (time of day, day of week, location)
- **Risk-based access control** does not use pre-defined sets of rules to determine access, which are static. This one is a very dynamic access control that evalutes the risk of the request in real time and grants or denies access based on the risk score taken from its context.

#### Authentication and authorization systems
Authentication and authorization between systems can be handled by several different protocols that standardize how to exchange information:
- **Service Provisioning Markup Language** (**SPML**) is an application authorization langage used to exchange user and account provisioning information between systems, so it's specifically used when creating and provisioning accounts on distributed systems. It has a requesting authority that sends the user creation information to a Provisioning service point, which sends the user information to provisioning service targets
- **Security Assertion Markup Language** (**SAML**) is a system we use to share a single credential to access multiple web-based systems without privisioning that account to those systems, sharing both authentication and authorization information for the target. Here, the Principal (user) authenticates against the identity provider (IdP) to check if it can access the service provider, or target application we are logging into. Messages are usually sent with SOAP (Simple Object Access Protocol) encapsulated in HTTP connections
- **OAuth**, an open standard used for authorization against third parties. It consists of a client, the resource server that the client is trying to acess, the authorization server that tracks for access permissions and issues tokens, and the resource owner who controls access to the resources
- **Kerberos** is aun authentication and authorization system used in many technologies, mainly in Windows with Active Directory. It uses symmetric key cryptohraphy, authenticating users in the key distribution center, and granting users Tickets, which are used to authenticate against other services with specific permissions. This eliminates the need to constantly authenticate against multiple systems, as all authentication runs against Kerberos
- **RADIUS**, or Remote Authentication Dial-In User Sevice, originally used for remote connection authentication. It is commonly used by ISP's to authenticate their customers. It is an open protocol used in enterprises to authenticate to wireless access points with centralized credentials.

#### Identity management
**Identity management** (IdM) is a process where you use various tools for identifying, authenticating and authorizing identities on your environment. It involves **credential management**, **access control**, **single sign-on** control, **auditing**, and **monitoring**. It requires managing and configuring these tools and their environment so they work properly over time, and the permissions of all of these identities over time. Several questions need to be answered for proper identity management:
- Who gets to access what resources?
- How are new accesses deemed correct and approved?
- What is the process for revoking accesses?
- How are accesses monitored and audited?
- Are there any compliance rules and regulations to take into account?
- How is access consolidated and managed across multiple systems?

##### Directory services
Directory Services are tools used in almost any organization to **manage access** to network resources using centralized credentials and identities. Most are built in a hierarchical database (**LDAP**). It allows administrators access to a **central access management platform** to manage identities, resources, and authorization settings between them.

This is usually handled in Windows environments by **Active Directory**, a Microsoft product that uses a Domain Controller to answer requests of access to resources on the network based on their Distinguished Name, a unique name composed of several attributes of an object.

##### Single sign-on
Single sign-on allows a **single set of credentials** from a credential provider we control to access resources on other environments, which allows us to have less credentials to manage, **reducing forgotten passwords and helpdesk calls**, and allow for **easier central management** of these identities. That said, this does mean that a single compromised credential gives access to multiple services, so protect it properly.

### Accountability
#### Accounting and auditing
Accounting's objective is to **keep users accountable for their actions**. We need to be able to **track down any action on the environment** back to a specific user identity, using logged activity that we can review for data. This will give us **evidence** of what happened, which will help us identify malicious activity and that controls are effective and working. We can also use them for general activity reports on data access.

We need to properly configure and set up **logging** for authentication and authorization systems we use, and monitor that this logging is working properly over time. these audit trails will tell us a story of what happened in an event. We should have:
- **Date and time** of all logs, synchronized across systems (`UTC`, for example)
- **Account activity** like logins and logouts, both successful and failed, account modifications, keeping tabs on who made those modifications and what data was modified
- Authentication and authorization **decision points**, if you're using risk-based access, to see why it decided to authorize or reject access for a user
- **activity after login** like files accessed, applications launched, databases accessed, or commands executed on that session

These logs we keep also need to be **regularly audited**, both with automated tools for simple alerting and analysis, and through routine manual reviews to dig deeper into potential events by trained analysts that understand what an incident in that environment looks like so they can identify them. Remember to **keep private information in logs protected** in case someone needs to access it when an analysis is being performed.

To make sure the logs are valid and consistent, **make sure the logs are protected** with proper permission control, viewing is limited to whoever needs to see them, and that tampering with those logs is not possible or evident. Keep them retained for your set amount of time needed, and back up your logs as necessary, ideally with an offline copy.

#### Identity and access lifecycle
**Accesses are constantly changing and evolving in an organization**. People are hired, let go, or they change teams, and that means their accesses need to change. We need to have a **set of policies** for when these changes happen, so their necessary permissions can ge granted, updated and deleted. Attackers very commonly exploit the lack of identity lifecycles in a company to access private information.

This lifecycle comes in three different phases:
1. **Provisioning**: when new employees are hired, they need a set of permissions given to them to do their job: access to network resources, user accounts, and their roles, which should be all granted following a documentation. We must be able to answer why each account was created and why each permission was granted.
2. **Access reviews**, which need to be run when a user changes positions within a company. Old accesses need to be removed, and anything new needed needs to be granted, so no unnecessary privileges are left for any identity. These accesses should be documented and defined by role.
3. **Deprovisioning**: When an employee leaves an organization, regardless of reason, there needs to be a set process to remove any access they had. Access is disabled, their data is archived, and the account is scheduled for deletion after a set amount of time, preferably automatically. Ownerships should be transferred to whoever is responsible for those resources after their departure.

If possible, **integrate your IAM system with your HR platform**. This will significantly reduce workload for identity and access management changes, as these permissions should be automatically granted and removed based on the role this user has in the HR platform.
