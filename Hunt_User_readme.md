# 🔦 Hunt - Search User - Orbital

> **NOTE:** This is sample code and needs to be tested properly before using in production!

## Index

1. [Use Case](#use-case)
2. [Currently Supported Solutions](#currently-supported-solutions)
3. [Design](#design)
4. [Prerequisites](#prerequisites)
5. [Installation steps](#installation-steps)
6. [Trigger the workflow](trigger-the-workflow)
7. [Author and Contact](author-and-contact)

### Use Case

* Identify user activity inside the Organisation using Cisco Secure Endpoint and Orbital

![Screenshot - Notification Webex](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___Hunt_User_Webex.png)
![Screenshot - casebook](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___Hunt_User_casebook.png)

### Currently Supported Solutions

 * Cisco Secure Endpoint (AMP)
 * Cisco Orbital
 * Cisco Webex

### Design

  * Identify where user exists in local account db using Orbital (user account monitoring query)
  * Identify where user is currently logged in using Orbital (Logged_In Users query)
  * Search for User activity in Cisco Secure Endpoint telemetry
  * Notify with results in Cisco Webex and/or mail
  * Create casebook with hostname(s)

![Screenshot - wkf](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___Hunt_User_WKF.png)


### Prerequisites

* Cisco Secure EP Essential or Premier subscription
* Cisco Secure EP API key. [Documentation](https://console.amp.cisco.com/help/en/wwhelp/wwhimpl/js/html/wwhelp.htm)
* Cisco Teams Bot for SecureX and a Cisco Teams Room (optional). [Documentation](https://developer.webex.com/docs/bots)
* Email Target (optional)


### Installation steps

1. Logon to SecureX via: https://sign-on.security.cisco.com/. 
> **NOTE:** If you don't have a SecureX Account, please follow the [Quick Start Guide](https://www.cisco.com/c/en/us/td/docs/security/secure-sign-on/sso-quick-start-guide/sso-qsg-welcome.html).
2. Go to Menu "Orchestration" 
  ![Install___SXO_Menu](/Images/Install___SXO_Menu.jpg)

3. Set up or Verify Targets, Account Keys and Variables

* Go to "Account Keys" and create or verify the following accounts. If they already exist under a different name, use them in next step.

  * Cisco Secure Endpoint - Account Keys
    * **Account Key Type* set to **HTTP Basic Authentication**
    * **Display Name** set to **AMP_Credentials**
    * **username**: **Cisco SecureEP API : 3rd Party API Client ID**
    * **Password**: **Cisco Secure EP API : API Key**
    * **Authentication option**: **Basic**
    
 * Cisco Orbital - Account Keys (if use)
    * **Account Key Type* set to **HTTP Basic Authentication**
    * **Display Name** set to **Orbital_Credentials**
    * **username**: **SecureX API with Orbital Right : Client ID**
    * **Password**: **SecureX API with Orbital Right : Client Password**
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

  * Cisco Orbital - Target 
    * **Target Type** set to **HTTP Endpoint**
    * **Display Name** set to **Orbital_Target_**
    * **No Account Key** set to **false**
    * **Default Account keys** set to **Orbital_Credentials**
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
    * **ORBITAL - QUERY ALL ENDPOINTS** (should already exist, if not import it from Cisco Security Github)

  ![image](https://user-images.githubusercontent.com/41740851/111790249-4bb33200-88c2-11eb-981c-2ab6a4cc10b0.png)

 
5. Import the Workflow

* Go to Workflows and **IMPORT** the following workflow from **SX-AO**

  * **Hunt-Search-User-Orbital**

6. Open and edit the imported workflow 

*  Adjust following variables to fit with your needs*

  * **Webex Room** set to the **Webex room name used for notification**. Remember to add you BOT to this room
  
    ![Install___SXO_ImportAtomic](/Images/readme___Hunt_User_Variable.png)

* Enable and fill the second block **Set Webex Bot Token** in the first group **admin**

  * **Variable to update** set to Global Variable **Webex Bot Token** (step3)
  
![image](/Images/readme___Hunt_User_Webex_Token.png)

* Validate the workflow

### Trigger the workflow

* Trigger : **manual** or **Respond Action** (Observable type : user)

![Screenshot - respond](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___Hunt_User_Respond.png)

### Author and Contact
Ivan Berlinson (Cisco) - <ivberlin@cisco.com>