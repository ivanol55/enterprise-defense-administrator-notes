# Introduction to change management
On these notes we will explore what **change management** is, why it's imporant for an organization to have a change management plan, and what benefits does it bring to our organization.

## What is change management?
Change management is a **structured plan and process** for introducing changes in your organization. Keys are **communication** and **documentation** about how a change should be implemented. The kind of change management chosen depends on the organization's culture and needs. It can be a **weekly/daily meeting discussion**, or in a larger organization or for a bigger change, a **process of submissions and approvals**.

## What do we get from it?
An organization with proper change management standards ensures **accountability** for the changes introduced, **keeps everyone informed** about the changes being implemented, enables proper **environment drift tracking**, and keeps **security up to speed** while allowing rapid evolution of needs.

## Types of change and change environments
There are different types of changes that we can distinguish from:
- **Planned major changes**, which are planned modifications to major elements of your environment. Usually larger scale, like new equipment or vendors. They need to be researched and documented, it uses the whole change management process, involves multiple meetings, and takes longer to implement
- **Break/fix maintenance** changes, which are changes implemented to fix a found issue with the environment. These are usually non-downtime issues, user-reported or admin-identified, like software configuration changes, hardware replacement needed or routine maintenance. Typically executed in shorter timeframes, and are scheduled
- **Emergency changes**, usually expedited to fix an issue introduced by a planned major change that went wrong. Normally reserved for major issues, commonly involving downtime. Unscheduled, and must be addressed immediately, though still may require approvals. Examples are a server being down or severely impacted, like email not working. Abbreviated versions of the change process are used, and root cause analysis is ran

## Detecting changes
We need to be able to detect if something has changed in an environment. For this, we use **baselines**:
- **Software and hardware** baselines give us a point of reference used for comparison, where we must know what "normal" looks like
- **Monitoring** baselines can be automated or involve routine audits, to understand that something is outside of the usual

Some examples of change detection are finding unknown hardware connected to the network, unauthorized software changes, or malware infection detection.

## Change environments
Changes are done **in stages using different environments** so we can make sure a change is being properly implemented and does what we think it is going to do. We distinguish between two main environments:
- the **Production** environment, which is the main network and systems where downtime can affect business, and changes should not be tested on
- **Test**/**Development** environments, which can be a complete or partial copy of the production environment, and may not include all redundancies, where changes are tested abd adjusted. Downtime here involves no loss of business, and you may have multiple testing environments

## The change management process
Change management is a **dynamic process**, highly situational. Usually, IT, security, project management, Legal (if needed) and procurement are always involved. Other profiles depend on the kind of change being implemented.

The process itself is usually divided in the following phases:
1. **Change introduction**, where the change we want to do is drafted. Depending on the size and type of change, it might be a meeting, or an email to the involved parties
2. **Reasearch and documentation**, where the path and timeline are defined, and documentation neded for the implementation is prepared. This might involve researching various vendors and choosing the best option for the task the change addresses or researching legal requirements, understand the support that will be implemented and the process to follow for it, understand the tool's needs
3. **Review**, where the involved parties understand the change and offer feedback on needs and potential issues. Make sure requirements from all teams, from the target to security to legal have everything they need to validate the change
4. **Implementation**, when the change is actually implemented into the environment. Milestones of the change are set, and the initiative owner monitors the change status
5. **Learning**, when the change is fully implemented and what was achieved is presented and reviewed in retrospective. Understand what could habve been differently, what roadblocks can you avoid in the future, what were the wins

## Governance, risk and compliance
Part of the security administration of environments involves **governance**, **risk** and **compliance**. This is a field of security closely related to legal requirements:
- **Governance** ensures that organizational activities are aligned with business goals
- **Risk** analyzes any risk or opportunity associated with business activities and how they can affect it
- **Compliance** ensures business activities operate within laws and regulations

Following these policies ensures more **optimal investment of resources**, **improved decision-making** for the business and **reduced fragmentation** among departments. This structured approach aligns IT with business objectives.

These policies are set by regulatory bodies, rules and frameworks like **NIST**, **ISO**, **HIPAA**, **PCI-DSS** or the EU's **GDPR**. Some of them are just for orientation and have **no regulation punishments** if not followed, some, like GDPR, involve **big fines**