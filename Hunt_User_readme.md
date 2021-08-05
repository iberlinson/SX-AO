# 🔦 Hunt - Search User - Orbital


### 1. Use Case

* Identify user activity inside the Organisation using Cisco Secure Endpoint and Orbital

![Screenshot - Notification Webex](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___Hunt_User_Webex.png)
![Screenshot - casebook](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___Hunt_User_casebook.png)


### 2. Trigger

* Trigger : **Respond Action** (Observable type : user)

![Screenshot - respond](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___Hunt_User_Respond.png)

### 2. Workflow Design

  * Identify where user exists in local account db using Orbital (user account monitoring query)
  * Identify where user is currently logged in using Orbital (Logged_In Users query)
  * Search for User activity in Cisco Secure Endpoint telemetry
  * Notify with results in Cisco Webex and/or mail
  * Create casebook with hostname(s)

![Screenshot - wkf](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___Hunt_User_WKF.png)


### 4. Prerequisites

* Cisco Secure EP Essential (Orbital) API key. [Documentation](https://console.amp.cisco.com/help/en/wwhelp/wwhimpl/js/html/wwhelp.htm)
* Cisco Teams Bot for SecureX and a Cisco Teams Room (optional). [Documentation](https://developer.webex.com/docs/bots)
* Email Target (optional)

* **Atomic Actions** : 
  * Webex-Teams-Send-Simple-Adaptive-Card from [SX-AO Atomics](https://github.com/iberlinson/SX-AO/tree/main/Atomics)
  * ORBITAL - QUERY ALL ENDPOINTS (should already exist, if not import it from Cisco Security Github)

### 5. Notes
* Please test this properly before implementing in a production environment. 

**Author(s)**
Ivan Berlinson (Cisco)