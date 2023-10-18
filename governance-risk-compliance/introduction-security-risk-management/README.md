# Introduction to security and risk management
We'll go over some basics of security management here: **governance**, **risk**, **compliance**, and how they factor into your program, **organizational roles** related to security and what they do, **training** implementation, **laws** and **regulations** to take into account, and the privacy and liability concerns addressed by compliance. We will set all of these requirements within a **common framework** you can use.

## Introduction to security management
Security management is centered around the **CIA triad**: **Confidentiality** (ensuring the privacy and protection of your organization's data and assets from unauthorized actors), **Integrity** (ensuring data and assets do not suffer any unauthorized changes, accidental or intentional) and **Availability** (making sure the systems are available and accessible in a timely and reliable manner, and that recovery is quick and secure)

Other terms that are used in relation to the triad are **authenticity** (trust and verify that the identities are who they say they are), **non-repudiation** (having proof of activity, systems, etc that we can use as evidence of changes)

The security team is **responsible from ensuring compliance** with the CIA triad: 
- **Securing data** properly
- **Managing risks** and vulnerabilities
- **ensuring business continuity** against risks
- Applying proper **system hardening** on new and existing systems
- **Ensuring IAM lifecycles are followed** for new, moving and leaving employees and service accounts
- **Educating** your teams about threats and vulnerabilities, and what security controls and mitigations they should be aware of

## Governance, risk and compliance
A GRC program needs to **cover every aspect of a security policy**: consider all the security controls in your organization, using them to ensure that the CIA triad is maintained, and use those policies to ensure compliance with regulations. This will also help your security program to align with the business objectives

### Governance
Governance will be a **framework** that **supports the goals of the organization**. It will generally originate from senior leadership and **provide direction and guidance** for your security program. It will represent a subset of the enterprise governance, specifically focusing on our cybersecurity strategy. It will be mainly a **strategic perspective**, not a step-by-step guide on actions. Governance also includes ethics in how business is handled, the training of your teams to properly handle security mesures and change management.

Governance programs **grant power** to those who need it, here our security personnel. This plan gives us the **backing from senior leadership** to enact policies and allows us to track performance of our security posture. 

We need to consider what **policies and procedures** need to apply to **who on the organizational structure**. To understand how to properly introduce governance to the organization, **several questions** need to be answered:
- What are we trying to **accomplish**? What is the point of our governance policy, like what assets are we protecting
- **Why** does it need to be done? Why is it important to have this policy on these resources?
- **How** are we trying to do it? what are the proposed policies and procedures?
- **Who** needs to be involved in the process?
- **Where** does it need to be done? What physical location is affected, or what systems are getting these changes applied to them?
- **When** do we need to get this completed by? When is it starting? How are we identifying our milestones of completion?

#### Organizational roles and responsibilities
**The whole organization** is usually involved in security one way or another, with their own set of **tasks and roles** to aid in compliance and security policy enforcement. Here are some examples:
- **The C-Suite** or executive management, who are ultimately responsible for everything that happens in the organization
    - **Chief Executive Officer**: manages the organization, oversees all operations 
    - **Chief Financial Officer**: responsible for the financial and accounting structure and budget approvals
    - **Chief Information Officer**: handles IT operations at a strategic level, ideally part technical part business
    - **Chief Security Officer**: responsible for understanding and mitigating organization risks, covering all security aspects, not just cybersecurity, having an understanding of compliance, regulations and customer expectations
    - **Chief Information Security Officer**: like the CSO, but geared towards IT
    - **Chief Privacy Officer**: Frequently an attorney, with a deep understanding of legal requirements to draft procedures to ensure that confidential information is kept safe
- **The security team**, **led by the CISO or CSO** (depending on the organization it may be a **director of information security**, similar to the CISO, usually more hands-on), comprised of:
    - **Security engineers** (a technical position that builds security infrastructure)
    - **Security administrators** (manage security infrastructure and assist engineers)
    - **Security analysts** (dedicated to day to day operational support, incident response, log analysis)
- **Data owners**, normally managers, who are in charge of who get access to their department's data
- **Data custodians**, who verify accesses and make sure that these are granted and scoped properly
- **System owners**, who directly manage servers, networks or applications, commonly IT people
- **Auditors**, who make sure everything is being done as the policies and regulations require
- **Users**, who use the system and need to understand how to operate their tools securely

#### Policies, procedures and standards
Policies, procedures and standards provide a **structured approach** to business management. These need to be **well documented** and **easy to understand**. In our case, we need to define their **scope** for security. What needs to be protected? To what extent? How should those assets be protected? It defines responsibilities in the organization and sets employee expectations, including **noncompliance consequences**. The creation of these **involve several departments** like **HR**, **Legal**, **Compliance** and **Risk**

These policies are written in broader terms and state what role security plays in the organization:
- What the organization **can and will do**
- What **responsibilities** employees have on security
- The **possible consequences** of non-compliance with policies

We also separate the security policies in several **tiers**:
- **Organizational** policies establish how the overall program is inmplemented and set goals, responsibilities, strategies and enforcement rules
- **Functional** policies address specific scenarios or issues, like acceptable email usage and workstation access
- **System** policies that target specific devices, applications and networks, regarding access and auditing requirements, encryption or system configuration

Security procedures are designed to be **detailed step-by-step tasks or instructions for specific situations**. They can apply to any individual department or to the entire organization depending on their **scope**. They state how policies, standards and guidelines will be **implemented**. Examples are the specific steps to properly install your operating system, how authentication controls are implemented to support a policy, how backups are performed, the incident response process on a runbook, or how-to documentations for how to implement a system.

**Standards describe requirements to meet policy goals**. They will be very detailed and mesurable to describe how systems are to be used, like in a policy that states sensitive data must be secured, the standard defines what data is considered sensitive, what form of encryption is used, and if data should be secured at rest and in transit. It is important to apply these standards equally across the organization.

We mesure that those standards are being met using **guidelines and baselines**. These are snapshots of a point in time where everything is proper, used for future comparison against changes being applied. They allow a fast, accurate way to detect system changes, and to understand that what needs to be done is properly applied to a system. 

We should make sure to apply all of these standards, baselines and controls to **vendors** as well as internal resources, as **vendors are often breach originators** if not managed properly. Have vendors follow **service agreements** with your security requirements to make sure they are using the required security controls. Treat these vendors as untrusted in access terms until proven otherwise.

#### Training
**Training is part of reducing risk in an organization**. We are going to explore two different sides: user training, and security team training. It's important to implement practices for both for different reasons: users need constant training for **how to protect themselves** against new threats, and the security team needs to **keep their skills up** to date to protect the organization.

User training can be implemented in several ways:
- **Security awareness training** to keep a security mindset when working with company assets. This can be done either with personal tests on learning platforms, or with attack simulations like phishing campaigns
- **Systems training** to make sure users interact with the company systems in the most secure way

Similarly, the security team needs to keep up:
- Continous learning about **new threats and vulnerabilities**
- Learning about **mitigation strategies and tactics**
- Exploration of **new products and features**

Regardless of the training type, contents should be **continuously reviewed and evaluated** to improve their effectiveness.

### Risk
Risk mesures the **likelihood of a threat exploiting a vulnerability**. **No organization is 100% secure** with no threat, there is always a risk. These are present in multiple areas, not necessarily security-related, like **natural disasters** or **equipment failure**, but generally involve **cyber-attacks**. We also need to take into account the **holistic approach**: generally security becomes a concern when it impacts business earnings, so risk management must always **consider the business impact**.

We apply risk management techniques to **identify** and **mitigate** organization risks, or **accept** them if necessary. Organizations should have **policies** in place to address these risks, handled by risk management personnel to analyze risks in our organization. Risk analysis can be either quantitative (we assign **monetary value** to a risk to understand cost and benefit) or qualitative (we assign **general ratings or levels** to the risk, using **opinions and scenarios** to evaluate the risk), and can be **automated** for **reporting** and **scenario simulation**.

The risk management process is divided into **different steps** of a risk mitigation plan:
1. **Frame** the risk. Establish context, define constraint and risk tolerance of your organization
2. **Assess** the risk. Determine what risks exist, prioritize and estimate their impact
3. **Respond** to the risk, using controls to address the risk based on our framing and assessment. These can be anything from cybersecurity controls to policy changes, to ultimately **accept**, **avoid**, **mitigate**, **share** or **transfer** a risk
4. Monitor continuously to ensure these controls are effectively in responding to this risk

#### Risk assessments and methodologies
A risk assessment aims to **identify vulnerabilities and threats** to **assess** their possible impact to your environment and **determine mitigation requirements**. Risk assessment methodologies vary in focus but have similar components, the choice of the method depending on the situation. Examples of methodologies are:
- For IT security risk and the most common, **NIST SP 800-30**, a guide from NIST to conduct risk assessments (prepare the assesment, conduct, communicate results, maintain the assessment checking results)
- **Facilitated Risk Analysis Process** (FRAP), a qualitative assessment which makes sure you're only assessing the most critical systems
- **Operationally Critical Threat, Asset and Vulnerability Evaluation** (OCTAVE), which is conducted by the people on a department who checks their own risks, facilitated by workshops that help them cover what they need to look at
- **Failure Modes and Effect Analysis** (FMEA), mostly used in development, which helps look into what may go wrong and fix it early when detected

Your risk assessment should be handled by a **risk assessment team**. The size and composition of the team depends on the assessment being done and is very situational, usually involving **departments with specialties on the answers needed** to understand the risk to add additional necessary viewpoints.

These assessments are generally done with a **set of questions**:
- **What could happen**? What threat event could occur that could result in business impact?
- **What would be the impact** if the threat event were to happen? What would happen to the organization?
- **How often** could this happen, realistically? What's the frequency?
- **How confident are we in those answers**? How much guessing was involved, if any? Is the frequency based on statistics, or known occurrences? What's our certainty?

#### Risk response, monitoring and reporting
Once a risk is assessed and prioritised, we need to **respond** to it, and make sure it **stays handled**.

There are **four ways** to respond to a risk:
- **Transfer**, where another organization or entity takes ownership of risk, for example when you purchase insurance
- **Avoidance**, where we stop activity on the system that introduces the risk, like powering off an unused machine that is not mission-critical until we have a fix
- **Mitigation**, reducing the risk to an acceptable level using controls or countermesures, for example with a WAF in front of a webserver
- **Acceptance**, when the organization understands the level of risk at hand and decides to not implement any countermesures or controls. They may choose to do this after a cost/benefit analysis where the control is more costly than the potential loss, if the risk is low enough not to be considered important, or due to lack of resources to implement the countermesure.

The decision is taken based on multiple factors, like considering the **potential loss** like fines or lost revenue vs the **cost of the countermesure**, the business impact, or public reputation effects

After the risk is responded to, this response effect needs to be **monitored**. This will help us guide future decision-making, making sure the issue does not re-appear (as infrastructure continuously changes). We also need to monitor for new risks, and to re-evaluate old risks that may have been reduced, changed or need reevaluating. We need to monitor for three main components:
1. **Effectiveness monitoring** mesures metrics to understand if the controls are still performing the task they were implemented to do, are they still properly mitigating the risk?
2. **Changes monitoring** mesures if there have been any changes to the environment like new or updated systems that may affect our controls and their effectiveness as well, or if they need this control applied to them now
3. **Compliance monitoring** mesures if your environment is in line with the laws and regulations that apply to you. Keep in mind that, while not frequently, laws and regulations change, and those changes can have a significant impact on your risk level. This will help you have the proper response to internal and external audits, as the results of those audits may affect compliance and thus your business

Those monitors need to be properly checked and communicated, that's what **reporting** is for. This will allow executive leadership and your board of directors to understand how security and compliance is being handled across the organization. This big picture will help them understand how risks are being handled and their potential impact. This also loops in **management**, who are responsible for managing risks, to understand their stake in a more detailed risk analysis. Finally, a more detailed technical report is provided for risk owners, who need to actually implement fixes and controls for the risks.

### Compliance
Compliance involves the process of ensuring all business activities **comply with regulations and laws** that affect your organization. These regulations depend on **industry and location**, like US healthcare with HIPAA having different requirements than EU companies under GDPR. Non-compliance can have financial or legal consequences.

Not all compliance is legal-based, some are open standards in the industry that are independently checked, like **PCI-DSS** for credit card management or **FedRAMP** to do buisness with US government agencies, and some are related to copyright, trademarks or software licenses.

#### Privacy
**Organizations are responsible for properly safeguarding data**, which includes customer information as well as internal employee data. There are several regulations that address this requirement, like **HIPAA** for US health information, **GDPR** for EU citizen data, **GLBA** for US finance companies. 

In some cases, like some countries, they are not legally obligated to do so, but the **ethical requirement** still exists, since it could have effects on the company like **reputation issues**, or **financial and legal penalties** in countries that protect that data.

Several types of data are considered sensitive:
- **Personally Identifiable Information** (PII), any information that allows an individual's identity to be inferred, like a driver's license number, social security numbers or ID numbers
- **Protected Health Information** (PHI), data related to health condition, services, or payment to health providers of an individual
- **Payment Card Industry** (PCI) data like credit card numbers or other payment-related data
- **Confidential company data**, unique to your organization, like propietary intellectual property or company financial records

Companies and executives can be **held liable** by laws and regulations if a data leak occurs. There needs to be proof that **due diligence** was made, which means proof that everything possible was done to provent an issue or incident. **Proper research and planning** to reach the best decision on a data handling case needs to be done. **Due care** about taking the reasonable precautions to protect data needs to be present as well. If these are not properly handled, individuals can be held liable
