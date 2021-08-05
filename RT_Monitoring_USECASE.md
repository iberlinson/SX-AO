# 🛎  RT-Monitoring-SecureEP-Umbrella-Notification-Incident - Use Case


### 1. Problem Statement

* When faced with an attack that generates multiple alerts in multiple consoles, it can be difficult to quickly recognize that these alerts are all part of a common attack campaign.
* Too many alerts can result in “Alert Fatigue” which leads to critical alerts being missed or overlooked
* Management requires a simple monitoring platform to keep them abreast of an evolving situation.

### 2. Solution

* Use SecureX Orchestration to assess, deduplicate and notify multiple alerts
* Organizations need to get timely notification of an attack campaign within a common messaging platform, regardless of:
  * the number of alerts
  * from which product they originate

* This objective is achieved through :

  * Continuous monitoring of Umbrella and/or Secure EP Security events (loop)
  * Near real time Incident creation and update (grouped by endpoint hostname, **no duplicate event**)
  * Near real time notification on new or updated incident (**no duplicate notification for same event occurring multiple times**)
  * Statistic tables
  
* **Design Overview**

![usecase___RT_Monitoring_DesignOverview](/Images/usecase___RT_Monitoring_DesignOverview.png)

* **Continuous Run** 

![usecase___RT_Monitoring_Continuous](/Images/usecase___RT_Monitoring_Continuous.png)

![usecase___RT_Monitoring_Continuous_WKF](/Images/usecase___RT_Monitoring_Continuous_WKF.png)

* **Main Workflow**

 * Collect
 
![usecase___RT_Monitoring_Collect](/Images/usecase___RT_Monitoring_Collect.png)

![usecase___RT_Monitoring_Collect_WKF](/Images/usecase___RT_Monitoring_Collect_WKF.png)

 
### Prerequisites

* Umbrella reporting API Key. [Documentation](https://docs.umbrella.com/umbrella-api/docs/reporting-api-authentication)
* Cisco Secure EP API key. [Documentation](https://console.amp.cisco.com/help/en/wwhelp/wwhimpl/js/html/wwhelp.htm)
* Cisco Teams Bot for SecureX and a Cisco Teams Room. [Documentation](https://developer.webex.com/docs/bots)
* Cisco Threat Response API key. [Documentation](https://securex.us.security.cisco.com/help/integration)


#### Installation
* Detailed installation instructions can be found [HERE](https://github.com/iberlinson/SX-AO/blob/main/RT_Monitoring_INSTALL.md)

