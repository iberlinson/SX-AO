# 🛎  RT-Monitoring-SecureEP-Umbrella-Notification-Incident 

> **NOTE:** This is sample code and needs to be tested properly before using in production!

## Index

1. [Problem Statement](#problem-statement)
2. [Solution](#solution)
3. [Design Overview](#design-overview)
4. [Currently Supported Solutions and roadmap](#currently-supported-solutions-and-roadmap)
5. [Prerequisites](#prerequisites)
6. [Installation](#installation)
7. [Authors](#authors)
8. [Contact](#contact)

# Problem Statement

* When faced with an attack that generates multiple alerts in multiple consoles, it can be difficult to quickly recognize that these alerts are all part of a common attack campaign.
* Too many alerts can result in “Alert Fatigue” which leads to critical alerts being missed or overlooked
* Management requires a simple monitoring platform to keep them abreast of an evolving situation.

# Solution

* Use SecureX Orchestration to assess, deduplicate and notify multiple alerts
* Organizations need to get timely notification of an attack campaign within a common messaging platform, regardless of:
  * the number of alerts
  * from which product they originate

* This objective is achieved through :

  * Continuous monitoring of Umbrella and/or Secure EP Security events (loop)
  * Near real time Incident creation and update (grouped by endpoint hostname, **no duplicate event**)
  * Near real time notification on new or updated incident (**no duplicate notification for same event occurring multiple times**)
  * Statistic tables
  
![readme___RT_Webex](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___RT_Webex.png)

![readme___RT_Incident](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___RT_Incident.png)

![readme___RT_Stat](https://github.com/iberlinson/SX-AO/blob/main/Images/usecase___RT_Monitoring_StatsTable.png)

# Design Overview

![usecase___RT_Monitoring_DesignOverview](/Images/usecase___RT_Monitoring_DesignOverview.png)

* **Continuous Run** 

![usecase___RT_Monitoring_Continuous](/Images/usecase___RT_Monitoring_Continuous.png)

![usecase___RT_Monitoring_Continuous_WKF](/Images/usecase___RT_Monitoring_Continuous_WKF.png)

* **Main Workflow**

  * **Collect**
 
![usecase___RT_Monitoring_Collect](/Images/usecase___RT_Monitoring_Collect.png)

![usecase___RT_Monitoring_Collect_WKF](/Images/usecase___RT_Monitoring_Collect_WKF.png)

  * **Incident - Notification - Statistics**
  
 ![usecase___RT_Monitoring_Incident_Notify_stats](/Images/usecase___RT_Monitoring_Incident_Notify_stats.png)

![usecase___RT_Monitoring_Incident_Notify_stats_WKF](/Images/usecase___RT_Monitoring_Incident_Notify_stats_WKF.png) 

# Currently Supported Solutions and roadmap

* Cisco Secure Endpoint (Event)
* Cisco Umbrella (Event)
* Cisco SecureX (Incident)
* Cisco Webex (Notification)

Other messaging and Incident platforms have “stub” placeholder code for future integration :
* TheHive
* ServiceNow
* MS Teams

![usecase___RT_Monitoring_placeholder](/Images/usecase___RT_Monitoring_placeholder.png) 

# Prerequisites

* Umbrella reporting API Key. [Documentation](https://docs.umbrella.com/umbrella-api/docs/reporting-api-authentication)
* Umbrella Org ID
* Cisco Secure EP API key. [Documentation](https://console.amp.cisco.com/help/en/wwhelp/wwhimpl/js/html/wwhelp.htm)
* Cisco Teams Bot for SecureX and a Cisco Teams Room. [Documentation](https://developer.webex.com/docs/bots)
* Cisco Threat Response API key. [Documentation](https://securex.us.security.cisco.com/help/integration)

# Installation

1. Logon to SecureX via: https://sign-on.security.cisco.com/. 
> **NOTE:** If you don't have a SecureX Account, please follow the [Quick Start Guide](https://www.cisco.com/c/en/us/td/docs/security/secure-sign-on/sso-quick-start-guide/sso-qsg-welcome.html).
2. Go to Menu "Orchestration" 
  ![Install___SXO_Menu](/Images/Install___SXO_Menu.jpg)

3. Set up or Verify Targets, Account Keys and Variables

* Go to "Account Keys" and create the following accounts. If they already exist under a different name, use them in next step.

  * Cisco Secure Endpoint - Account Keys (if use)
    * **Account Key Type* set to **HTTP Basic Authentication**
    * **Display Name** set to **AMP_Credentials**
    * **username**: **Cisco SecureEP API : 3rd Party API Client ID**
    * **Password**: **Cisco Secure EP API : API Key**
    * **Authentication option**: **Basic**

  * Cisco Umbrella - Account Keys (if use)
    * **Account Key Type* set to **HTTP Basic Authentication**
    * **Display Name** set to **Umbrella_Reporting_API**
    * **username**: **Umbrella Reporting API : Client ID**
    * **Password**: **Umbrella ReportingE API : Secret**
    * **Authentication option**: **Basic**

* Go to "Targets" and create the following accounts. If they already exists under a different display name and you can't rename or duplicate them, you will have to modify Target Criteria in the workflow.

  * Cisco Secure Endpoint - Target (if use)
    * **Target Type** set to **HTTP Endpoint**
    * **Dislay Name** set to **AMP_Target**
    * **No Account Key** set to **false**
    * **Default Account keys** set to **AMP_Credrentials**
    * **Protocol** set to **HTTPS**
    * **Host** set to **api.amp.cisco.com** or **api.eu.amp.cisco.com**
    * **Port** set to **443**
    * **Path** set to **/v1**

  * Cisco Umbrella - Target (if use)
    * **Target Type** set to **HTTP Endpoint**
    * **Display Name** set to **Cisco Umbrella Reporting V1**
    * **No Account Key** set to **false**
    * **Default Account keys** set to **Umbrella_Reporting_API_**
    * **Protocol** set to **HTTPS**
    * **Host** set to **reports.api.umbrella.com**
    * **Port** set to **443**
  
  * Cisco Webex
    * **Target Type** set to **HTTP Endpoint**
    * **Display Name** set to **Webex Teams**
    * **No Account Key** set to **true**
    * **Protocol** set to **HTTPS**
    * **Host** set to **webexapis.com**
    * **Port** set to **443**

  * Private CTIA
    * **Target Type** set to **HTTP Endpoint**
    * **Display Name** set to **Private_CTIA_Target**
    * **No Account Key** set to **true**
    * **Protocol** set to **HTTPS**
    * **Host** set to **private.intel.amp.cisco.com** or **private.eu.intel.amp.cisco.com**
    * **Port** set to **443**

* Go to **Variables** and Create or verify global variables for your **Webex Token**
  
  * **Webex Token**
    * **Data Type** set to **Secure String**
    * **Display Name** set to **Webex Bot Token**
    * **Scope** set to **Global**
    * **Value** set to **"YOUR WEBEX BOT TOKEN"**
    

4. Import SXO Atomic Actions from Github

* Go to Workflows select "Atomic Actions" and **IMPORT** Atomoc Actions

**This step is a pre-requirement to successful import the workflow in the next step!**
  ![Install___SXO_ImportAtomic](/Images/Install___SXO_ImportAtomic.jpg)
  * Import the following from Git **SX-AO-AtomicActions**
    * **Cisco-Secure-EP-Get-critical-cloud-IOC**
    * **Webex - Simple adaptive card**
    * **Create TheHive case** ( if you are not planing to integrate TheHive, just add a random value as Bearer Token )
    * **CTR - Get Incident Details**
    * **CTR - Update Incident**
    * **Cisco Umbrella- Get Last security event Table**
  
  ![image](https://user-images.githubusercontent.com/41740851/111790249-4bb33200-88c2-11eb-981c-2ab6a4cc10b0.png)

  * Import the following from Cisco Security/Atomics
    * **Webex Teams - Search for Room**
    * **Threat Response v2 - Create Relationship**
    * **Microsoft Teams - Post Adaptive Card via Webhook** 
    * **Threat Response v2 - Generate Access Token**
    * **Threat Response v2 - Create Casebook**
    * **Threat Response v2 - Create Incident**
 
5. Import the Workflow

* Go to Workflows and **IMPORT** the following workflow from **SX-AO**

  * **RT-Monitoring-SecureEP-Umbrella-Notification-Incident**

6. Open and edit the imported workflow 

*  Adjust following variables to fit with your needs*
  
  * **Umbrella_Org_ID** set to **Your Umbrella Org ID** got from Umbrella console URL
  * **Webex Room** set to the **Webex room name used for notification**. Remember to add you BOT to this room
  
![image](/Images/usecase___RT_Monitoring_Variables.png)
  
* Enable and fill the first block **Set Variables Webex Bot Token** in the first group **admin/Set Variables from Global/Notification Systems/Cisco Webex Enable**

  * **Variable to update** set to Global Variable **Webex Bot Token** (step3)
  
![image](/Images/usecase___RT_Monitoring_Webex_Token.png)
  
* Enable the trigger to run the workflow every 5 minutes

![image](/Images/usecase___RT_Monitoring_Trigger.png)

7. Run the workflow

* Before a first run or if a previous run failed, go to **Variables** and reset the following global Variables
  * **AO_Enrichment_Running** set to **False**
  * **AO-AMP_Last_detection_date** set to the oldest event date you want to collect in Cisco Secure EP (in format YYYY-MM-DDThh:mm:ss)
  * **AO-Umbrella_Last_detection_date** set to the oldest event date you want to collect in Cisco Umbrella (in format YYYY-MM-DDThh:mm:ss)

![image](/Images/usecase___RT_Monitoring_Run.png)

  * To clear detection table, import and use the workflow **RT-Monitoring-Clear-detection-stats-table**

# Authors

* Moritz Wenz, Phil Wood, Sven Kutzer, Ivan Berlinson (Cisco)

# Contact :

* <ivberlin@cisco.com>
