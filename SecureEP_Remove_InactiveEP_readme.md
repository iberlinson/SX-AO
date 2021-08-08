# 🧽 Cisco Secure EP - Remove Inactive Endpoints

> **NOTE:** This is sample code and needs to be tested properly before using in production!

## Index

1. [Use Case](#use-case)
2. [Currently Supported Solutions](#currently-supported-solutions)
3. [Design](#design)
4. [Prerequisites](#prerequisites)
5. [Installation steps](#installation-steps)
6. [Author and Contact](author-and-contact)

### Use Case

* Your list of computers in Cisco Secure Endpoint may be polluted with inactive endpoints that are not seen connected over a long period of time. The reasons can be multiple (duplication, laptop update, deleted virtual machine ...) and they consume "seats" in your license

* Use SecureX Orchestration to periodically : 
  * Identify endpoint with a last seen value over a given number of days (default 45)
  * Remove them from your computer list automatically or with a 2-Tiers approval
  * Notify
  
* This workflow can be trigger by a schedule to execute every day or X days

![Screenshot - Notification Webex](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___EP_Removal_Webex.png)
![Screenshot - Approval](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___EP_Removal_Approval.png)

### Currently Supported Solutions

 * Cisco Secure Endpoint (AMP)
 * Cisco Webex

### Design

  * 1. Calculate Past date from delay
  * 2. Query Cisco Secure Endpoint to get the list of Computer with their hostname, last seen, GUID
  * 3. For each computer, compare last seen value with Calculated past date
  * 5. Store in a temporary table Hostname, GUID of endpoint to be removed
  
![Screenshot - WKF1](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___EP_Removal_WKF1.png)

  * 5. Create Approval Request (optional)
  * 6. Notify in Cisco Webex (optional)
  * 7. Wait for approval (optional)
  * 8. If approved, delete Endpoint(s)
  
 ![Screenshot - WKF2](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___EP_Removal_WKF2.png)
 

### Prerequisites

* Cisco Secure EP API key. [Documentation](https://console.amp.cisco.com/help/en/wwhelp/wwhimpl/js/html/wwhelp.htm)
* Cisco Teams Bot for SecureX and a Cisco Teams Room (optional). [Documentation](https://developer.webex.com/docs/bots)

### Installation steps

1. Logon to SecureX via: https://sign-on.security.cisco.com/. 
> **NOTE:** If you don't have a SecureX Account, please follow the [Quick Start Guide](https://www.cisco.com/c/en/us/td/docs/security/secure-sign-on/sso-quick-start-guide/sso-qsg-welcome.html).
2. Go to Menu "Orchestration" 
  ![Install___SXO_Menu](/Images/Install___SXO_Menu.jpg)

3. Set up or Verify Targets, Account Keys and Variables

* Go to "Account Keys" and create or verify the following account. If it already exists under a different name, use it in next step.

  * Cisco Secure Endpoint - Account Keys
    * **Account Key Type* set to **HTTP Basic Authentication**
    * **Display Name** set to **AMP_Credentials**
    * **username**: **Cisco SecureEP API : 3rd Party API Client ID**
    * **Password**: **Cisco Secure EP API : API Key**
    * **Authentication option**: **Basic**

* Go to "Targets" and create the following accounts. If they already exists under a different display name and you can't rename or duplicate them, you will have to modify Target Criteria in the workflow.

  * Cisco Secure Endpoint - Target 
    * **Target Type** set to **HTTP Endpoint**
    * **Dislay Name** set to **AMP_Target**
    * **No Account Key** set to **false**
    * **Default Account keys** set to **AMP_Credrentials**
    * **Protocol** set to **HTTPS**
    * **Host** set to **api.amp.cisco.com** or **api.eu.amp.cisco.com**
    * **Port** set to **443**
    * **Path** set to **/v1**

  * Cisco Webex
    * **Target Type** set to **HTTP Endpoint**
    * **Display Name** set to **Webex Teams**
    * **No Account Key** set to **true**
    * **Protocol** set to **HTTPS**
    * **Host** set to **webexapis.com**
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
  * Import the following 
    * **Webex-Teams-Send-Simple-Adaptive-Card** from [SX-AO Atomics](https://github.com/iberlinson/SX-AO/tree/main/Atomics)   

5. Import the Workflow

* Go to Workflows and **IMPORT** the following workflow from **SX-AO**

  * **Cisco-SecureEP-Remove-Inactive-Endpoints**

6. Open and edit the imported workflow 

*  Adjust following variables to fit with your needs*

  * **Webex Room Name** set to the **Webex room name used for notification**. Remember to add you BOT to this room
  * **Number of days** set to the number of days for endpoint not seen connected
 
![image](/Images/readme___EP_Removal_Variables.png)
  
* Enable and fill the first block **Set Variabble Bot Token** in the first group **admin**

  * **Variable to update** set to Global Variable **Webex Bot Token** (step3)
  
![image](/Images/readme___EP_Removal_Webex_Token.png)

* Validate the workflow

### Author and Contact
Ivan Berlinson (Cisco) - <ivberlin@cisco.com>