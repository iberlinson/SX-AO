# How to install and setup the workflows in SecureX Orchestration (SXO)

1. Logon to SecureX via: https://sign-on.security.cisco.com/. 
> **NOTE:** If you don't have a SecureX Account, please follow the [Quick Start Guide](https://www.cisco.com/c/en/us/td/docs/security/secure-sign-on/sso-quick-start-guide/sso-qsg-welcome.html).
2. Go to Menu "Orchestration" 
  ![Install___SXO_Menu](/Images/Install___SXO_Menu.jpg)

## Create or Verify Targets and Account KEYS if they exist
1. Cisco Secure Endpoint - Account Keys (if use)
  * **Account Key Type* set to **HTTP Basic Authentication**
  * **Display Name** set to **AMP_Credentials**
  * **username**: **Cisco SecureEP API : 3rd Party API Client ID**
  * **Password**: **Cisco Secure EP API : API Key**
  * **Authentication option**: **Basic**

2. Cisco Secure Endpoint - Target (if use)
  * **Target Type** set to **HTTP Endpoint**
  * **Dislay Name** set to **AMP_Target**
  * **No Account Key** set to **false**
  * **Default Account keys** set to **AMP_Credrentials**
  * **Protocol** set to **HTTPS**
  * **Host** set to **api.amp.cisco.com** or **api.eu.amp.cisco.com**
  * **Port** set to **443**
  * **Path** set to **/v1**


3 Cisco Umbrella - Account Keys (if use)
  * **Account Key Type* set to **HTTP Basic Authentication**
  * **Display Name** set to **Umbrella_Reporting_API**
  * **username**: **Umbrella Reporting API : Client ID**
  * **Password**: **Umbrella ReportingE API : Secret**
  * **Authentication option**: **Basic**
  
4. Cisco Umbrella - Target (if use)
  * **Target Type** set to **HTTP Endpoint**
  * **Display Name** set to **Cisco Umbrella Reporting V1**
  * **No Account Key** set to **false**
  * **Default Account keys** set to **Umbrella_Reporting_API_**
  * **Protocol** set to **HTTPS**
  * **Host** set to **reports.api.umbrella.com**
  * **Port** set to **443**
  
  
3. Cisco Webex
  * **Target Type** set to **HTTP Endpoint**
  * **Display Name** set to **Webex Teams**
  * **No Account Key** set to **true**
  * **Protocol** set to **HTTPS**
  * **Host** set to **webexapis.com**
  * **Port** set to **443**

4. Private CTIA
  * **Target Type** set to **HTTP Endpoint**
  * **Display Name** set to **Private_CTIA_Target**
  * **No Account Key** set to **true**
  * **Protocol** set to **HTTPS**
  * **Host** set to **private.intel.amp.cisco.com** or **private.eu.intel.amp.cisco.com**
  * **Port** set to **443**


## Import SXO Atomic Actions from Github
1. Go to Workflows select "Atomic Actions" and **IMPORT** Atomoc Actions

**This step is a pre-requirement to successful import the workflow in the next step!**
  ![Install___SXO_ImportAtomic](/Images/Install___SXO_ImportAtomic.jpg)
2. Import the following from Git **SX-AO-AtomicActions**
  *	**Cisco-Secure-EP-Get-critical-cloud-IOC**
  *	**Webex - Simple adaptive card**
  *	**Create TheHive case** ( if you are not planing to integrate TheHive, just add a random value as Bearer Token )
  *	**CTR - Get Incident Details**
  *	**CTR - Update Incident**
  *	**Cisco Umbrella- Get Last security event Table**
  ![image](https://user-images.githubusercontent.com/41740851/111790249-4bb33200-88c2-11eb-981c-2ab6a4cc10b0.png)

3. Import the following from Cisco Security/Atomics
  *	**Webex Teams - Search for Room**
  *	**Threat Response v2 - Create Relationship**
  *	**Microsoft Teams - Post Adaptive Card via Webhook** 
  *	**Threat Response v2 - Generate Access Token**
  *	**Threat Response v2 - Create Casebook**
  *	**Threat Response v2 - Create Incident**
 
## Import SXO Workflows from Github
1. Import the Workflow from Git **SX-A0**
  * **RT-Monitoring-SecureEP-Umbrella-Notification-Incident**

2. Update the missing informations
  * **Webex Bots** : fill your **BOT bearer token** - [click here to see how you can create a presistent Access Token](https://github.com/iberlinson/SX-AO/blob/main/WebexAccessToken.md)
  * **Umbrella Org ID** : fill your umbreall org id or none if net use
  
3. Import the Workflow from Git **CiscoSecureX-UnifiedAlerting**
  * **RT-Monitoring-Clear-detection-stats-table**

  
  
