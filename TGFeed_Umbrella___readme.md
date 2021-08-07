# SecureX orchestration workflows : TG Feeds to Umbrella BlockList - 2-Tiers Approval

> **NOTE:** This is sample code and needs to be tested properly before using in production!

**Periodically check for TG Feed and push domains to Umbrella destinations block list with 2-Tiers approval and notification**

## Index

1. [Flow](#flow)
2. [Requirement](#requirement)
2. [Installation steps](#installation-steps)

# Flow

* Trigger by an hourly schedule
  * Collect current hour TG Feed
  * Extract domains in feed
  * Get domains list with only unique values
  * Notify in Webex Team and Request for approval before adding to block list
  * On approval, add each domain to block list

![Screenshot - Notification Webex](https://github.com/iberlinson/SX-AO/blob/main/Images/Readme_TGFeed_umbrella___notification.png)
![Screenshot - Approval](https://github.com/iberlinson/SX-AO/blob/main/Images/Readme_TGFeed_umbrella___approval.png)
![Screenshot - Destinations-List](https://github.com/iberlinson/SX-AO/blob/main/Images/Readme_TGFeed_umbrella___DestinationList.png)

# Requirement

* Mandatory
  * Cisco Umbrella - Management API
  * Cisco Malware Analytics Cloud API (AKA Threat Grid)
* Optional
  * Cisco Webex Token (Bot) - [click here to see how you can create a presistent Access Token](https://github.com/iberlinson/SX-AO/blob/main/WebexAccessToken.md)
  
## Installation steps


1. Logon to SecureX via: https://sign-on.security.cisco.com/. 
> **NOTE:** If you don't have a SecureX Account, please follow the [Quick Start Guide](https://www.cisco.com/c/en/us/td/docs/security/secure-sign-on/sso-quick-start-guide/sso-qsg-welcome.html).
2. Go to Menu "Orchestration" 
  ![Install___SXO_Menu](/Images/Install___SXO_Menu.jpg)

3. Set up or Verify Targets, Account Keys and Variables

* Go to "Account Keys" and create the following account. If it already exists under a different name, use it in step step for "Umbrella target"

  * Cisco Umbrella Management API - Account Keys from your Umbrella console
  
    * **Account Key Type** set to **HTTP Basic Authentication**
    * **Display Name** set to **Umbrella_Management_API**
    * **username**: **Umbrella Management API : Client ID**
    * **Password**: **Umbrella Management API : Secret**
    * **Authentication option**: **Basic**
 
* Go to "Targets" and create the following accounts. If they already exists under a different display name and you can't rename or duplicate them, you will have to modify Target Criteria in the workflow.
  
  * Cisco Umbrella Management API - Target
    * **Target Type** set to **HTTP Endpoint**
    * **Display Name** set to **Cisco Umbrella Management V1**
    * **No Account Key** set to **false**
    * **Default Account keys** set to **Umbrella_Management_API_**
    * **Protocol** set to **HTTPS**
    * **Host** set to **management.api.umbrella.com**
    * **Port** set to **443**
  
  
  * Cisco Secure Malware Analytics (Threat Grid)
    * **Target Type** set to **HTTP Endpoint**
    * **Display Name** set to **Cisco ThreatGrid**
    * **No Account Key** set to **true**
    * **Protocol** set to **HTTPS**
    * **Host** set to **panacea.threatgrid.com** or **panacea.threatgrid.eu**
    * **Port** set to **443**
  
  * Cisco Webex
    * **Target Type** set to **HTTP Endpoint**
    * **Display Name** set to **Webex Teams**
    * **No Account Key** set to **true**
    * **Protocol** set to **HTTPS**
    * **Host** set to **webexapis.com**
    * **Port** set to **443**

  * Private CTIA (should already exists)
    * **Target Type** set to **HTTP Endpoint**
    * **Display Name** set to **Private_CTIA_Target**
    * **No Account Key** set to **true**
    * **Protocol** set to **HTTPS**
    * **Host** set to **private.intel.amp.cisco.com** or **private.eu.intel.amp.cisco.com**
    * **Port** set to **443**


* Go to **Variables** and Create or verify global variables for your **TG API** and **Webex Token**
  
  * **TG_API**
    * **Data Type** set to **Secure String**
    * **Display Name** set to **ThreatGrid API**
    * **Scope** set to **Global**
    * **Value** set to **"YOUR THREATGRID API"**
  
  * **Webex Token**
    * **Data Type** set to **Secure String**
    * **Display Name** set to **Webex Bot Token**
    * **Scope** set to **Global**
    * **Value** set to **"YOUR WEBEX BOT TOKEN"**
    
* Go to Variables and verify settings (email) for **Task Requestor** and **Task Approver**
  

5. Import required Atomic Actions - **This step is a pre-requirement to successful import the workflow in step 6**

* Go to Workflows select "Atomic Actions" and **IMPORT** Atomoc Actions


  ![Install___SXO_ImportAtomic](/Images/Install___SXO_ImportAtomic.jpg)
  
  * Import the following from Git **SX-AO-AtomicActions**
  
    * **Webex-Teams-Send-Simple-Adaptive-Card-V2** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Webex-Teams-Send-Simple-Adaptive-Card-V2__definition_workflow_01MXL3QX1CI992DKEA4Anda0qAiNhyIdcCm)
    * **Cisco-Malware-Analytics-TG-Collect-Feed** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Cisco-Malware-Analytics-TG-Collect-Feed__definition_workflow_01QFLDMMVX5L61VvlcUzlpg7Jp7vBMaDeFU)
    * **Core-Get-List-Table-with-unique-Values** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Core-Get-List-Table-with-unique-Values__definition_workflow_01JQV4DC02D934XLB7J1u6CcmV9yNotBbE3)

  
  ![image](https://user-images.githubusercontent.com/41740851/111790249-4bb33200-88c2-11eb-981c-2ab6a4cc10b0.png)

  * Import the following from Git **Cisco Security/Atomics**
  
    * **Webex Teams - Search for Room**
    * **Umbrella - Management V1 - Add Record to Destination List**

6. Import the Workflow

* Go to Workflows and **IMPORT** the following workflow from **SX-AO**

  * **TG-Feeds-to-Umbrella-BlockList-2-Tiers-approval** [Link](https://github.com/iberlinson/SX-AO/tree/main/Workflows/TG-Feeds-to-Umbrella-BlockList-2-Tiers-approval__definition_workflow_01QFMWUZAEW9Z7O9qE3CoSTpLenZc3GTMb8)

7. Open and edit the imported workflow 

*  Adjust following variables to fit with your needs*
  
  * **Detection_List_name** set to the name of the **Umbrella Destinations** list to update
  * **Umbrella_Org_ID** set to **Your Umbrella Org ID** got from Umbrella console URL
  * **Webex Room** set to the **Webex room name used for notification**. Remember to add you BOT to this room
  * **TG Feed Name** set to one of the following :
    * autorun-registry
    * banking-dns
    * dga-dns
    * dll-hijacking-dns
    * doc-net-com-dns
    * downloaded-pe-dns
    * dynamic-dns
    * irc-dns
    * modified-hosts-dns
    * parked-dns
    * public-ip-check-dns
    * ransomware-dns
    * rat-dns
    * scheduled-tasks
    * sinkholed-ip-dns
    * stolen-cert-dns*
    
![Readme___TGFeed_Umbrella_variables](https://github.com/iberlinson/SX-AO/blob/main/Images/Readme___TGFeed_Umbrella_variables.png)
    
* Enable and fill the first block **Set Variables Tokens**
  * **Variable to update 1** set to Global Variable **ThreatGrid API** (step3)
  * **Variable to update 2** set to Global Variable **Webex Bot Token** (step3)
  
![Readme___TGFeed_Umbrella_Tokens](https://github.com/iberlinson/SX-AO/blob/main/Images/Readme___TGFeed_Umbrella_Tokens.png)
8. Validate and test the workflow (run)

9. Enable the Trigger in the workflow if you want the workflow to run automatically every hour.

![Readme___TGFeed_Umbrella_trigger](https://github.com/iberlinson/SX-AO/blob/main/Images/Readme___TGFeed_Umbrella_trigger.png)
