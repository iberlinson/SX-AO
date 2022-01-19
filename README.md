# SX-AO

## Repository for Cisco SecureX Orchestration Workflows and Atomic Actions

  * **NOTE:** 
    * If you don't have a SecureX Account, please follow the [Quick Start Guide](https://www.cisco.com/c/en/us/td/docs/security/secure-sign-on/sso-quick-start-guide/sso-qsg-welcome.html).
    * Detailed instructions to add iberlinson/SX-AO repositories to you Securex Instance can be found [HERE](https://github.com/iberlinson/SX-AO/blob/main/repositories.md)
    * How to import a workflow : [HERE](https://ciscosecurity.github.io/sxo-05-security-workflows/importing)
    * SecureX Orchestration Documentation : [HERE](https://ciscosecurity.github.io/sxo-05-security-workflows/)

## Available Atomics Actions

* List and Readme [Here](https://github.com/iberlinson/SX-AO/blob/main/Atomics_readme.md)*

## Available Use Cases (Workflows)  

* 🛎 **Cisco Umbrella : Notification on Security Events (Umbrella-Notification-Security-Events)**

  * Receive a near real time notification in Webex Teams or via Email on a new domain blobked by Umbrella

    * Use SecureX Orchestration to periodically : 
      * Get new security event from last check
      * Notify in Webex Teams on new domains blocked seen for the first time in the organization
      * Maintain a statistic table with number of hits for each domain and current notification status

  * This workflow can be trigger by a schedule to execute every X minutes

    * [Screenshot - Notification Webex](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___Umbrella_Notification_Webex.png)

  * **Use Case and Installations** : Detailed informations about the workflow can be found [HERE](https://github.com/iberlinson/SX-AO/blob/main/Umbrella_notification_readme.md)

    

* 🔦 **Hunt - Search User** 
  
  * Search for a given user via :
    * Orbital (Account (Monitoring and Logged_In)
    * Secure Endpoint - User Activity (telemetry)
    
  * Notify in Cisco Webex or/and via Email about result
  
  * Create Casebook if user found
  
    * [Screenshot - Notification Webex](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___Hunt_User_Webex2.png)
    
  * **Use Case and Installation** : Detailed informations about the workflow can be found [HERE](https://github.com/iberlinson/SX-AO/blob/main/Hunt_User_readme.md)
  
    
  
* **🧽 Cisco Secure EP - Remove Inactive Endpoints**
  * Cisco Seucre Endpoint : Identify and Remove from computers list endpoints with a last seen over a given number of days (default : 45 days)
    * Include 2-Tiers approval and Notification in Cisco Webex

    * [Screenshot - Notification Webex](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___EP_Removal_Webex.png)
    * [Screenshot - Approval](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___EP_Removal_Approval.png)

  * **Use Case and Installation** : Detailed informations about the workflow can be found [HERE](https://github.com/iberlinson/SX-AO/blob/main/SecureEP_Remove_InactiveEP_V2_readme.md)

    
  
* **TG-Feeds-to-Umbrella-BlockList-2-Tiers-approval**
  * Download Threat Grid Curated feed and push domain to Cisco Umbrella Destinations Lists.
    * Include 2-Tiers approval and Notification in Cisco Webex
  
    * [Screenshot - Notification Webex](https://github.com/iberlinson/SX-AO/blob/main/Images/Readme_TGFeed_umbrella___notification.png)
    * [Screenshot - Approval](https://github.com/iberlinson/SX-AO/blob/main/Images/Readme_TGFeed_umbrella___approval.png)
    * [Screenshot - Destinations-List](https://github.com/iberlinson/SX-AO/blob/main/Images/Readme_TGFeed_umbrella___DestinationList.png)

  * **Use Case and Installation** : Detailed informations about the workflow can be found [HERE](https://github.com/iberlinson/SX-AO/blob/main/TGFeed_Umbrella___readme.md)
  
    

* **🛎 RT-Monitoring-SecureEP-Umbrella-Notification-Incident**

  * Continuous monitoring of Umbrella and/or Secure EP Security events (loop)

  * Near real time Incident creation and update (grouped by endpoint hostname, **no duplicate event**)

  * Near real time notification on new or updated incident (**no duplicate notification for same event occurring multiple times**)

  * Statistic tables

    * [Screenshot - Notification Webex](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___RT_Webex.png)
    * [Screenshot - Incident](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___RT_Incident.png)

  * **Use Case and Installations** : Detailed informations about the workflow can be found [HERE](https://github.com/iberlinson/SX-AO/blob/main/RT_Monitoring_USECASE.md)

    
