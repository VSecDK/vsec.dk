---
title: "Community Article - Hunting Windows Event Logs"
date: 2022-09-13
author: Avesta Fahimipour
categories:
  - Blog
tags:
  - Member
  - Community
  - Article
---

Event logs are a great way to detect adversary activity on a windows machine and be able to tell the story of what and how it happened.  
Unfortunately, there are many event logs and not all of them are useful. Going through these logs can be daunting and requires keen eyes.  
In this blog post, we will see what event logs are more useful than others and how we can utilize them.  

**Windows Event Log Structure**  
Windows event log provides information about hardware and software events occurring on a Windows operating system.  
Windows event logs are stored under:  
C:\Windows\System32\winevt\Logs  

Events are written to event log channels and each event has an event ID.  

**Common channels are:**  
•	Security  
•	System  
•	Application  

There are 4 channel types:  

**Common**  
•	Administrative  
•	Operational  

**Uncommon**  
•	Debug  
•	Analytic  

Now that you understand the basics let’s dive into the events.  

### Logon
Adversaries will steal your credentials and reuse them.  
You will commonly see ids 4624 and 4634, successful logon and logoff.  
These events have a field called logon ID.  If a logon and logoff event have the same logon ID you can determine the session length.  

When looking at 4624 events it’s vital that you whitelist built-in DWM and UMFD (Desktop Windows Manager & Usermode Font Driver) logons, this will considerably decrease the noise.  
* A large number of failed logons which is 4625 show brute force activity.  
* A large number of successful logons indicate lateral movement activity.  

When other credentials are used for different tasks like process creation, network share, RDP, etc. event 4648 records them.  
Using 4672 and 4624 you can detect user logons with admin-level privileges.  When monitoring these events you should whitelist built-in windows accounts like SYSTEM.  If adversaries create new accounts, event 4720 will detect this.  

The logon event has a field called logon type, this field indicates how the logon occurred.  
To understand the various ways you can log in to a system, use Microsoft's official documents:  
https://docs.microsoft.com/en-us/windows-server/identity/securing-privileged-access/reference-tools-logon-types  

**Summary:**  
4624: Logon  
4625: Failed Logon  
4634,4647: Successful Logoff  
4672: Account logon with superuser rights (special logon)  
4720: An account was created  
4726: An account was deleted  
4648: Logon using explicit credentials  

### Groups
Adversaries might add accounts to groups with administrative access.  You can use these events to monitor the groups.  

**Summary:**  
4728: A member was added to a security-enabled global group  
4732: A member was added to a security-enabled local group  
4756: A member was added to a security-enabled universal group  

### Account Logon
Your first question might be “what’s the difference between account logon and logon?”  
Logon refers to local login activity that occurs on the local system hence the log will be generated on the local system.  
Account Logon refers to third-party authentication. In an enterprise domain users authenticate to the domain controller because of that you will generate logs on the DC and the local system.  
If you login using a local account Account Logon events will be generated on the local system.  

In an enterprise environment, you will have two types of authentication: NTLM and Kerberos.  
Pass the hash (PtH) is a common technique that adversaries use which uses NTLM.  In this case, event 4776 will be seen along with 4624 type 9 or 3, 4648, and 4672.  
If Kerberos is the only method of authentication adversaries can utilize OverPass the hash by directly sending the RC4 or AES hashes, this will generate 4768, 4769, and 4771 along with 4624, 4648, and 4672.  

**Summary:**  
4776: The computer attempted to validate the credentials for an account  
4768: A Kerberos authentication ticket (TGT) was requested  
4769: A Kerberos service ticket was requested  
4771: Kerberos pre-authentication failed  

### Enumeration
These events were added with Windows 10. They allow you to detect reconnaissance activity in the network.
You will need to whitelist mmc, services, taskhostw, and explorer.  
PowerView and [Bloodhound](https://github.com/BloodHoundAD/BloodHound) are tools that adversaries use to enumerate your privileged users and groups.  
You can use these events to detect who is running what process to enumerate your privileged users and groups.  

**Summary:**  
4798: A user's local group membership was enumerated    
4799: A security-enabled local group membership was enumerated  

### RDP
There are various ways for adversaries to move in your environment, including RDP.  
RDP generates session reconnect 4778 and session disconnect 4779 events.
But that’s not all, normal logon 4624 types 7 and 10 are also related to RDP.  
It is important to emphasize that 4778 does not record new connections, only reconnects.  
I should also mention that other channels record RDP activity too.  

**Summary:**  
4778: A session was reconnected to a Window Station  
4779: A session was disconnected from a Window Station  

### Processes
At some point, adversaries will run their malware which will trigger 4688 (process creation) and 4689 (process exit).  
Event 4688 can also capture the command line related to the process.  

**Summary:**  
4688: A new process has been created  
4689: A process has exited  

### Network Share
Network shares can be used to mount shares like C$, ADMIN$, and IPC$ to move in the environment laterally.  
When a share is accessed 5140 will be recorded, but this may not contain all the information you desire so you can use the much more verbose event 5145.  

**Summary:**  
5140: Network share was accessed  
5145: Shared object accessed  

### Scheduled Tasks
Persistence is very important to adversaries and scheduled tasks are one way they maintain persistence.  
When an adversary creates a new scheduled task 4698 and 106 will trigger.  

**Summary:**  
4698: Scheduled Task Created  
4699: Scheduled Task Deleted  
4700: Scheduled Task Enabled  
4701: Scheduled Task Disabled  
4702: Scheduled Task Updated  

You can also look into the Task Scheduler channel for:  
106: Scheduled Task Created  
140: Scheduled Task Updated  
141: Scheduled Task Deleted  
200: Scheduled Task Executed  
201: Scheduled Task Completed  

### Services
Services can be heavily targeted by adversaries for different purposes.  
If an adversary breaks a service when exploiting it, event 7034 will trigger.  
If adversaries use services for persistence and install a new service, events 7045 and 4697 will record it.  

**Summary:**  
7034: Service crashed  
4697: A new service was installed on the system  
7045: A new service was installed on the system  
7040: Start type changed  
7036: Service started or stopped  

### Powershell
Powershell is a great built-in tool for adversaries to use in our networks and because we can’t block access to it, PowerShell v5 comes with different logging capabilities.  
Adversaries commonly use obfuscation with Powershell to evade security products. Script block logging will record it and it might automatically decode it as well.  

**Summary:**  
4103: Module Logging  
4104: Scriptblock Logging  

### WMI
If you have been targeted by Tural or APT29 you will understand that WMI, just like Powershell, gives you access to do many things.  
Adversaries will use the ConsumerFilter binding to achieve their goal. For this to happen they need to create a consumer, and a filter, and bind them together.  
When going through these steps various event logs will record their action but at the end, 5861 will give you the best view of the actions that have occurred.  

**Summary:**   
5857: WMI Activity was detected  
5858: WMI errors detected  
5859,5860: WMI Filter/Consumer activity was detected  
5861: WMI FilterConsumer Binding was detected  

### Removable Devices
These events allow you to track rogue BYODs, internal users exfiltrating sensitive data, and adversaries physically attacking your environment.  

**Summary:**  
4663: An attempt was made to access an object  
4656: A handle to an object was requested  
6416: A new external device was recognized by the System  

### Log Clearing
Legitimate log clearing can happen but it can be part of your baseline.  Seeing logs being cleared at random times should be investigated using 1102 and 104.  

**Summary:**  
1102: The audit log was cleared  

Under the System channel look for:  
104: The audit log was cleared  

### Conclusion
While this is not an exhaustive list of all the events, it can be an amazing starting point for you to learn about the event logs and become more comfortable with them.  
After you become familiar with these events it should be much simpler to expand your knowledge of event logs and find order amongst the chaos.
