# SX-AO

Repository for workflows and AtomicActions

* Detailed instructions to add iberlinson/SX-A0 repositories to you Securex Instance can be found [HERE](https://github.com/iberlinson/SX-AO/blob/main/repositories.md)

### 1. 🛎 RT-Monitoring-SecureEP-Umbrella-Notification-Incident

* Continuous monitoring of Umbrella and/or Secure EP Security events (loop)
* Near real time Incident creation and update (grouped by endpoint hostname, **no duplicate event**)
* Near real time notification on new or updated incident (**no duplicate notification for same event occurring multiple times**)
* Statistic tables

* [Screenshot - Notification Webex](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___RT_Webex.png)
* [Screenshot - Incident](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___RT_Incident.png)

#### Installation
* Detailed installation instructions can be found [HERE](https://github.com/iberlinson/SX-AO/blob/main/INSTALL.md)

### 2. 🔦 Hunt - Search User - Orbital
 * Search for a given user via Orbital (Account (Monitoring and Logged_In)
 * Notify in Cisco Webex about result
 
### 3. 🧽 Cisco Secure EP - Remove unseen Endpoints
 * Cisco Seucre Endpoint
 * Remove from computer list unseen endpoint since a given number of days (default : 45 days)