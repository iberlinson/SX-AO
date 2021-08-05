# 🧽 Cisco Secure EP - Remove Inactive Endpoints


### 1. Problem Statement

* Your list of computers in Cisco Secure Endpoint may be polluted with inactive endpoints that are not seen connected over a long period of time. The reasons can be multiple (duplication, laptop update, deleted virtual machine ...) and they consume "seats" in your license

### 2. Solution

* Use SecureX Orchestration to : 
  * Identify endpoint with a last seen value over a given number of days (default 45)
  * Remove them from your computer list automatically or with a 2-Tiers approval
  * Notify
  
* This workflow can be trigger by a schedule to execute every day or X days

![Screenshot - Notification Webex](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___EP_Removal_Webex.png)
![Screenshot - Approval](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___EP_Removal_Approval.png)

  
### 3. Design Overview

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
 

### 4. Prerequisites

* Cisco Secure EP API key. [Documentation](https://console.amp.cisco.com/help/en/wwhelp/wwhimpl/js/html/wwhelp.htm)
* Cisco Teams Bot for SecureX and a Cisco Teams Room (optional). [Documentation](https://developer.webex.com/docs/bots)

* Atomic Actions : Webex-Teams-Send-Simple-Adaptive-Card from [SX-AO Atomics](https://github.com/iberlinson/SX-AO/tree/main/Atomics)


### 5. Notes
* Please test this properly before implementing in a production environment. 


**Author(s)**
Ivan Berlinson (Cisco)