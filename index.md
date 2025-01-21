---
layout: default
---

Text can be **bold**, _italic_, ~~strikethrough~~ or `keyword`.

[Link to another page](./another-page.html).

<!--There should be whitespace between paragraphs. We recommend including a README, or a file with information about your project.-->
# Project #1 SIEM with a Threat Intelligence Feed
This project demonstrates how to monitor and secure a Windows 10 Pro virtual machine (VM) on Azure by leveraging Microsoft Sentinel. The project sets up an environment to collect and analyze security event logs, focusing on Remote Desktop Protocol (RDP) connection attempts. An alerting mechanism was configured to notify of successful connections, showcasing how Sentinel can enhance security monitoring and response capabilities.

**Table of contents**
<ol>
  <li>Introduction</li>
  <li>Prerequisites</li>
  <li>Step-by-step implementation
       <ul>
         <li>Creating the Azure environment</li>
         <li>Configuring Microsoft Sentinel</li>
         <li>Setting up data collection</li>
         <li>Creating an Alert Rule</li>
         <li>Simulating a successful connection</li>
       </ul>
  </li>
  <li>Results</li>
  <li>Conclusion</li>
</ol>
  

## 1. Introduction

This project showcases how to monitor and enhance the security of an Azure-hosted Windows 10 Pro virtual machine using Microsoft Sentinel. It covers setting up a VM, enabling security event logging, configuring alert rules, and simulating successful RDP connections to validate monitoring.

### 2. Prerequites

*   An active Azure account.
*   Basic understanding of Azure portal and Vm's.
*   Familiarity with Microsoft Sentinel.

#### 3. Step-by-step implementation

**Creating the Azure environment**
1.  Log into your Azure account.
2.  Navigate to Virtual Machines and create a new VM:
    * OS: Windows 10 Pro.
    * Networking: Ensure RDP is open on port 3389.
  

3.  Deploy the VM and note its public IP address for future RDP access.

**Configuring Microsoft Sentinel**
1. Search for Microsoft Sentinel in the Azure portal and create a workspace
2. Open Sentinel and go to Data Connectors.
3. Select Windows Security Events and follow the prompts to connect your VM:
   * Install the Log Analytics agent on your VM.
   * Configure the agent to send logs to your Sentinel workspace.

**Setting up Data Collection**
1. Go to the Log Analytics workspace linked to your Sentinel instance.
2. Create a Data Collection Rule (DCR)
   * Name: WindowsEventsToSentinel.
   * Scope: Select your VM.
   * Logs: Include event IDs related to RDP connections (e.g., Event ID 4624 for successful logins).
3. Save an enable the rule

**Creating an Alert Rule**
1. In Sentinel, go to Analytics > Create Alert Rule.
2. Define the rule:
   * Trigger Condition: Log query for successful RDP connections.
   * Set a threshold for alerting.
   * Notification: Configure email or other alert mechanisms.

**Simulatting a Successful Connection**
1. Use an RDP client to connect to the VM using its public IP and credentials.
2. Verify the connection logs in Microsoft Sentinel. 

##### 4. Log Query Example
```kql
SecurityEvent
| where Activity contains "success"
      and Account !contains "system"
```


##### 5. Results

* Logs of all attempted and successful RDP connections were collected in Sentinel.
* An alert was triggered for the simulated successful connection.
* The project demonstrates effective use of Sentinel for security monitoring.

###### 6. Conclusion

This project highlights how to monitor and respond to RDP connection events using Microsoft Sentinel. It provides a scalable approach to securing Azure-hosted VMs and serves as a foundation for further exploration into Azure security tools.

<!--There's a horizontal rule below this.-->
* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

![vmpage](VM page.PNG)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
