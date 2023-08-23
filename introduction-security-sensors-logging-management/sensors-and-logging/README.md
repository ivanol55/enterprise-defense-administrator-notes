# Introduction to security sensors and logging management
In these notes we'll explore **security sensors and logging**, why this data gathering is important, and what can we do with them from a defense perspective to fight back against threats from attackers. We will explore both **network and host security sensors**, **security logging** and how to manage it and the usage of **SIEM** and **SOAR** platforms.

## What are security sensors?
Security sensors **collect information** about a **network**, **device**, **service** or **application**, that we can use for **security data-driven decisions**. It doesn't have to be designed for security, any data-gathering tool that assists in **analyzing data and events** can be used as a sensor. Examples are firewall taps in network devices, event logs in servers, or IoT devices for physical-layer security.

Data is usually gathered from these **scattered sources** and **aggregated** into a **central location** which can process this data and allows us to see it in a single place. We need several types of sensors, because no one single sensor can capture everything we may need, and what sensors you need is very specific to your infrastructure. In the end, you need a complete system that **captures all meaningful events** to your platform, and what is meaningful depends on your environment. You should also make sure you have **no duplicated events**.

### Security sensor locations
You should have several types of security sensors scattered through different locations of your network:
- You should have security monitors on your **DMZ**, as whatever is on that network is exposed to the internet as a public service, and should be closely kept tabs on
- Have **authentication** bruteforce sensors on any device that requires authentication: email servers, web servers, VPN appliances
- Keep EDR centralized logging for whatever devices has **privileged access** to your network

### Security sensor types
Depending on what data you need and from where, sensors can be classified on types:
- **Network sensors** give information about traffic, like a span port that mirrors packets or detections from your IDS or IPS
- **Device or host sensors** gather information about the device itself, like the event logs, SNMP logs or EDR detections
- **Service sensors**, usually installed on servers, that monitor software running a service, like webservers or mail servers

#### Network sensors
Network sensors can be individual devices dedicated to gather data, or a configuration change in your network devices that forwards data to a centralized location. It **provides data on network traffic**, and what data it provides depends on where it's placed on your network and its visiblity: if your sensor is on a network switch, it'll see all traffic that passes that switch, but not any other device.

These sensors are useful to **understand exactly what is happening inside of your network**: see if there is any Command&Control activity, detect data exfiltration or catch workstations downloading payloads from suspicious servers.

One kind of device used as a network sensor is a **network tap**, usually a standalone device that gets all traffic from the device cloned to a logging location. An IPS or IDS can use this network tap information to monitor and block dangerous traffic. This can be also done with **port mirroring** on a switch directly into the IDS or IPS device port. Keep in mind that this port mirroring practice can affect performance on that device.

Another sensor we can use is **SNMP** (Simple Network Management Protocol), used to monitor data on the network device itself: device statistics like CPU usage, traffic statistics, or login attempts. This helps us monitor the health and security of the appliance itself.

Some more complex devices with a more involved setup allows us to **read encrypted traffic**. Without any changes, source and destination can still be monitored, but not contents of a request. With more work and changes, we can **monitor the contents** as well, generally done with a man-in-the-middle certificate making all traffic go through an SSL or TLS **proxy**. This, keep in mind, can add a lot of network overhead, and may make some sites throw errors back.

#### Host sensors
These are sensors that get installed on a **specific host or device**. It generally gathers logs from the **operating system** itself, and from the **applications** running on that server or workstation. These can also be **dedicated central devices** that get data forwarded to them. They mainly assist on **detecting host-level threats**, like bruteforce login attempts with windows event logs, EDR detection of malicious files or processes or forwarded logs from application webservers.

Every environment is different, but usual elements have **proven-necessary data sources**: 
- Security, application and system events from **Windows endpoints**
- **SMTP logs** and filtering/email security alerts from **email systems**
- Device health information from specific devices, like network appliances - you don't need to relate it to the device, but you need to know someone is trying to log into it
- **Service sensors**, dedicated to gathering data on specific applications or services running on a server, like a webserver or accesses to a VPN appliance, or database queries that appear out of the ordinary
- **EDR logs** for host agents, that gather data about malicious files and processes and may block or quarantine files or connections
- Alerts from host-based intrusion detection and prevention systems (**HIDS**/**HIPS**)

## Logging
**Proper logging is key to any security infrastructure** so we have detailed information on what is going on around our environment. It helps to keep tabs on **what has happened, where, and when**, keeping a **registry of events** that can be checked back to confirm scenarios. Logging can help us **identify many types of attacks** thanks to behavior: port scans, bruteforce attacks, denial of service, account compromises. This helps us achieve real-time data reporting and incident alerting.

Having logs from multiple sources also allows us to do **correlation of events**: we can see that a user received a phishing email with mail logs, then they opened the phishing link thanks to webfilter logs, and that the phished credentials were used as their VPN connected through the firewall from an unusual IP address at an unusual time. We have the ability to **build a picture of what happened**. We don't need to do it at the time it happens either, as logging gives us historical and forensic data up to a retention point.

We need to keep in mind **what needs to be logged**. Not everything needs to go into your logging platform, and **not all logs need to be retained for the same amount of time**. Some critical audit logs may be required to be kept for a lot longer due to legislation, while simpler application error logs can be kept for much less. Prioritise and keep what you may need the most, like account logins, successful or failed, account modifications or configuration changes, or certain critical windows events.

### Centralized logging
**Centralized logging is critical** for security infrastructure when you start to grow out to make response easier and faster. This will give you a single dashboard where you can see **statistics**, **historical data**, and **simplified analysis** of data correlation. This setup also allows you to introduce **automation** and **alerting** with more complex rules and decisions and **improves resilience against attackers deleting logs** to cover tracks locally.

A lot of information can give you **alert fatigue**. This happens when not properly tuned alerts fire too frequently, which gets you used to the alert and makes you not look at it as much as you should. A lot of the work on a security platform is **tuning** it to your own case, so only actual security scenarios come through as alerts.

Having this central place to check information **facilitates third-party security audits**, getting rid of long audit processes, and makes **internal security audits easier and faster**, which makes it so they can be a routine practice.

### SIEM
A SIEM (**Security Information & Event Management**) platform is a product or software platform that provides real-time analysis of events, logs, and information to alert on security events that may be happening on your environment. **It's the brain of your centralized logging infrastructure**, it's what will process those logs and give you the **real-time intelligence** of events. It will correlate log sources and analyze their contents to understand what bigger picture they paint, and alert on issues, or act on them automatically.

This platform generally helps converting logs into a standard format it can use to correlate information, called **normalization**. This allows you to read, query and correlate data yourself if necessary in one common standard. This helps you make **simpler, more efficient alerts** that may fire less and reduce alert fatigue. Some platforms include **automation**, like blocking a known-bad IP that is being contacted.

The platform assists on **visualization of large-scale data volumes**, so it makes it **easier for analysts to understand** if something is out of the ordinary, providing an at-a-glance look at alert streams. We can also **build our own dashboards** that give us desired metrics and information for a specific scenario we want to monitor for. These may give us a look into a potential issue that has not necessarily triggered an alert or doesn't have one. This, however, is only useful if a dashboard is being **actively monitored**.

These platforms look at **several different scenarios** made possible by their data correlation between sources, like **impossible travel** (login to the app from two sides of the world in 5 minutes), or excessive file copying out of the ordinary that may indicate **data exfiltration**.

### SOAR
**Security Orchestration, Automation and Response** platforms focus on completing security response tasks with **little to no interaction**, with **almost automated handling**. This software runs different tasks based on input to execute set processes and procedures you configure, based on what you want to happen based on incidents or alerts, connecting multiple security tools and systems togethers, like receiving an alert from your SIEM about a vulnerability scan, and sending a block IP order to your firewall.

### Manual log review
As the name implies, sometimes logs need to be reviewed manually for details. This is a **slow and manual process** with little to no automation, where you may or may not use centralized logging systems (although it is still encouraged to use them when possible). This is very commonly **used alongside automated analysis**, to investigate **specific issues** we need to gather details on.

If we view events on the source system, we get the advantage of seeing **untreated logs stream in real time**, which allows for a faster response if we identify the targets. Going to the source also **bypasses the log filtering** that we may have configured and that may be getting applied before the logs are sent to the central location. This way we may catch things being missed by automated analysis.

### Automated log analysis
In contrast to manual log review, automated log analysis is going to provide **more information**, **faster results**, and **more advanced alerts**. Target systems may offer simple alerts, but the majority of your complex alerts will originate after your SIEM has completed data correlation and enrichment. This includes **special features** your platform may have like analysis of emails, URL sandboxing and behavioral indicators.

This setup requires gathering a lot of intelligence: **the more data sources** you give the platform to correlate, **the better story you can get**. Good data sources to have include **login and authentication** systems like AD and Radius servers, all **public-facing** systems like remote access gateways and webservers, your **security appliances**, and your network devices. Send all this gathered data to a **SIEM** that **processes** this data, **analyzes** its information, and generates **intelligence** from it.

The alerts generated by these platforms need to be taken care of and **tuned**. Tuning **reduces alert count**, thus reducing **alert fatigue**, and helps **avoiding false positives** on your security platform. With enough knowledge of your environment, you can even **automate response** to certain incidents, like blocking traffic from certain sources. This will free up analyst time so they can do the actually necessary analysis on legitimate alerts.

## Continuous monitoring and alerting
Depending on how your logs are delivered, you will get information to act on **faster or slower**. If you upload your logs on a schedule or do batch uploads, you may take some time to process events, and all of those logs are ingested at once. This will delay analysis, which may take away time of response. You should, when possible, use continuous log shipment, where logs are **delivered as they generate**, often used in critical systems for near real-time identification of potential issues.

Continuous monitoring of these logs requires a centralized log management system as we spoke about earlier for event correlation. This allows this platform to **analyze logs as they arrive** when they are pushed or pulled into the platform. This is critical to have with **often-targeted systems** like remote access systems, authentication servers like Active Directory domain controllers, public webservers or permiter firewalls. This also allows for immediate alerting based on these events.

Alerting can either trigger **from the endpoint, or from the SIEM**, the former one acting faster but with less available information, and the latter having some more delay of processing, but providing much more enriched data.
