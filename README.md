# SX-AO

* Repository for workflows and Atomic Actions

  * **NOTE:** If you don't have a SecureX Account, please follow the [Quick Start Guide](https://www.cisco.com/c/en/us/td/docs/security/secure-sign-on/sso-quick-start-guide/sso-qsg-welcome.html).
  * Detailed instructions to add iberlinson/SX-A0 repositories to you Securex Instance can be found [HERE](https://github.com/iberlinson/SX-AO/blob/main/repositories.md)
  * How to import a workflow : [HERE](https://ciscosecurity.github.io/sxo-05-security-workflows/importing)
  * SecureX Orchestration Documentation : [HERE](https://ciscosecurity.github.io/sxo-05-security-workflows/)
  * **Atomics Readme** [Here](https://github.com/iberlinson/SX-AO/blob/main/Atomics_readme.md)
  
### 1. 🛎 RT-Monitoring-SecureEP-Umbrella-Notification-Incident

* Continuous monitoring of Umbrella and/or Secure EP Security events (loop)
* Near real time Incident creation and update (grouped by endpoint hostname, **no duplicate event**)
* Near real time notification on new or updated incident (**no duplicate notification for same event occurring multiple times**)
* Statistic tables

[Screenshot - Notification Webex](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___RT_Webex.png)
[Screenshot - Incident](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___RT_Incident.png)

* **Use Case** : Detailed informations about the Use Case can be found [HERE](https://github.com/iberlinson/SX-AO/blob/main/RT_Monitoring_USECASE.md)
* **Installation** : Detailed installation instructions can be found [HERE](https://github.com/iberlinson/SX-AO/blob/main/RT_Monitoring_INSTALL.md)

### 2. 🔦 Hunt - Search User - Orbital
 * Search for a given user via :
   * Orbital (Account (Monitoring and Logged_In)
   * Secure Endpoint - User Activity (telemetry)*
 * Notify in Cisco Webex about result

[Screenshot - Notification Webex](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___Hunt_User_Webex.png)
[Screenshot - Casebook](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___Hunt_User_casebook.png)
 
 * **Use Case and Installation** : Detailed informations about the workflow can be found [HERE](https://github.com/iberlinson/SX-AO/blob/main/Hunt_User_readme.md)
 
### 3. 🧽 Cisco Secure EP - Remove Inactive Endpoints
 * Cisco Seucre Endpoint
 * Identify and Remove from computers list endpoints with a last seen over a given number of days (default : 45 days)
 * Include 2 Tiers approval and Notification in Cisco Webex
 
[Screenshot - Notification Webex](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___EP_Removal_Webex.png)
[Screenshot - Approval](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___EP_Removal_Approval.png)

* **Use Case and Installation** : Detailed informations about the workflow can be found [HERE](https://github.com/iberlinson/SX-AO/blob/main/SecureEP_Remove_InactiveEP_readme.md)
