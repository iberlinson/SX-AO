# 🛎 Umbrella Security Events - Notifications

> **NOTE:** This is sample code and needs to be tested properly before using in production!

## Index

1. [Use Case](#use-case)
2. [Currently Supported Solutions](#currently-supported-solutions)
3. [Design](#design)
4. [Prerequisites](#prerequisites)
5. [Installation steps](#installation-steps)
6. [Author and Contact](author-and-contact)

### Use Case

* Receive a near real time notification on a new domain blobked by Umbrella
* Use SecureX Orchestration to periodically : 
  * Get new security event from last check
  * Notify in Webex Teams on new domains blocked seen for the first time in the organization
  * Generate a statistiv table with number of hits for each domain and current notification status
* This workflow can be trigger by a schedule to execute every X minutes
* A control mechnism avoid simultaneous multiples runs of the workflow to limit risk of duplicate notification for the same domain.

![Screenshot - Notification Webex](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___Umbrella_notification_Webex.png)


### Currently Supported Solutions

 * **Cisco Umbrella - Reporting V1 - Security Reports**
 * **Cisco Webex**

### Design

  * 1. Check if an other instance of the workflow is currently running (global variable "running state" : "True/False")
       1. Yes - Completed
       2. No - Run the workflow and set Global Variable "running state" to "True"
    2. Admin Tasks
       1. Webex : Get Bot Token from Global Variable and Search for notification room
       2. Date : Calculate current date and get Last event date from global variable
    3. Query Umbrella Security Activity Report (start date = Last event date / to-date = current date)
    4. New security Events ?
       1. No - Completed
       2. Yes - continue workflow execution
    5. For each entries in the security report, check if the domain exists in the Global statistics table
       1. if No :
          1. Notify in Webex Teams
          2. Add the domain to statistics table with Notified.= True and Hits = 1
       2. If yes and Notified = False (notifcation enable for the domain)
          1. Notify in Webex Teams
          2. Update row in statistics table with Notified.= True and Hits = Hits + 1
       3. If yes and Notified = True (notification disable)
          1. Update row in statistics table with Notified.= True and Hits = Hits + 1
    6. Admin
       1. Store last security event date in global variable
       2. Set running state to False

 ![Screenshot - WKF2](https://github.com/iberlinson/SX-AO/blob/main/Images/readme___Umbrella_Notification_WKF.png)


### Prerequisites

* Cisco Umbrella Reporting V1 API. [Documentation](https://docs.umbrella.com/umbrella-api/docs/reporting-api-authentication)
* Cisco Teams Bot API. [Documentation](https://developer.webex.com/docs/bots)

### Installation steps

1. **Logon to SecureX** via: https://sign-on.security.cisco.com/. 
> **NOTE:** If you don't have a SecureX Account, please follow the [Quick Start Guide](https://www.cisco.com/c/en/us/td/docs/security/secure-sign-on/sso-quick-start-guide/sso-qsg-welcome.html).

2. **Go to Menu "Orchestration"**

   

   ![Install___SXO_Menu](/Images/Install___SXO_Menu.jpg)

   

3. **Set up or Verify Targets, Account Keys and Variables**

* Go to **"Account Keys"** and create or verify the following account. If it already exists under a different name, use it in next step.

  * Cisco Umbrella Reporting API V1 - Account Keys

    * **Account Key Type* set to **HTTP Basic Authentication**
    
    * **Display Name** set to **Cisco Umbrella Reporting API**
    
    * **username**: **Umbrella Reporting API - 3rd Party API Client ID**
    
    * **Password**: **Umbrella Reporting API : API Key**
    
    * **Authentication option**: **Basic**
    
      

* Go to **"Targets"** and create the following accounts. If they already exists under a different display name and you can't rename or duplicate them, you will have to modify Target Criteria in the workflow.

  

  * **Cisco Umbrella Reporting V1**- Target 

    * **Target Type** set to **HTTP Endpoint**

    * **Dislay Name** set to **Cisco Umbrella Reporting v1**

    * **No Account Key** set to **false**

    * **Default Account keys** set to **Cisco Umbrella Reporting API**

    * **Protocol** set to **HTTPS**

    * **Host** set to **reports.api.umbrella.com**

    * **Port** set to **443**

    * **Path** is empty

      

  * **Cisco Webex** - Target

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
    
      
    
4. **Import the Workflow**

   

* Go to Workflows and **IMPORT** the following workflow from **SX-AO** (or import manually)

  * **Umbrella-Notification-Security-Events**

5. **Open and edit the imported workflow** 

* Adjust following **variables** to fit with your needs

  * **Webex Room Name** set to the **Webex room name used for notification**. Remember to add your BOT to this room
  * **Umbrella Organization ID ** 

![image](/Images/readme___Umbrella_Notification_Variables.png)

* In the workflow, navigate and edit to the action **Get Webex Token** in the second group called **Admin**

    * **Variable to update** set to Global Variable **Webex Bot Token** (step3)

      

  ![image](/Images/readme___Umbrella_Notification_Webex_Token.png)

  

6. * **Validate** the workflow

     

7. At first run the workflow will use the date 2022-01-17T01:00:00-00:00. If you want to change this behavior you have to edit the global variable **"AO-Umbrella-Notification-lastevent_date"**

   

   ![image](/Images/readme___Umbrella_Notification_Lasteventdate.png)

   

8. Enable the trigger to schedule the workflow execution every minutes

   

   ![image](/Images/readme___Umbrella_Notification_trigger.png)

### Author and Contact
Ivan Berlinson (Cisco) - <ivberlin@cisco.com>