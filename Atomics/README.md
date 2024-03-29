# Atomics Action

### Index

1. [Cisco Umbrella](#cisco-umbrella)
2. [Cisco Secure Endpoint](#cisco-secure-endpoint)
3. [Cisco SecureX](#cisco-securex)
4. [Cisco Secure Malware Analytics](#cisco-secure-malware-analytics)
5. [Cisco Webex](#cisco-webex)
6. [Cisco Secure Email](#cisco-secure-email)
7. [TheHive](#thehive)
8. [NumVerify](#numverify)
9. [YouTube](#youtube)
10. [Notes](#notes)

### Cisco Umbrella
* **Cisco-Umbrella-Get-Last-security-event-Table** [link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Cisco-Umbrella-Get-Last-security-event-Table__definition_workflow_01MTBS3PX08T13DnyQkuNld9GvrU538PXoI)
  * Get Security event from Cisco Umbrella Reporting API from a starting date (input variable)
  * Output :
    * Table with Category, Hostname, Obsevable
    * Last event date
    * Raw json output
    
### Cisco Secure Endpoint
* **Cisco-Secure-EP-Get-critical-cloud-IOC** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Cisco-Secure-EP-Get-critical-cloud-IOC__definition_workflow_01MD6BCBYALHW20xugDSlrpXdDCz5RJkUoL)*
  * Get Cisco Secure EP detection events (filter on eventid) from a starting date (input variable)
    * Output :
      * Table with Event Description, Target Endpoint Hostname, Observable
      * Last event date
      * Raw json output
    
* **Secure-EP-Get-Cloud-IOCs-Full-List** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Secure-EP-Get-Cloud-IOCs-Full-List__definition_workflow_01PJ80JRUGROQ6B1VahKDzfASBPS8ocG45x)
  * Query Cisco Secure Endpoint to get the full list of available Talos Cloud IOCs
    * Output :
      * IOCs List with name/id and description (Table And/Or Json format)

* **Secure-EP-Get-SCD-List** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Secure-EP-Get-SCD-List__definition_workflow_01QFIX6DEZDDB46xgD0DPKTZEWe89wzrIqh)
  * Get Cisco Secure Endpoint configured Simple Custom Detection Lists*
    * Input :
      * Output Table Enable : True/False
    * Output :
      * Json Output
      * Table with GUID and name if set to true

* **Secure-EP-Add-Hash-To-SCD** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Secure-EP-Add-Hash-to-SCD__definition_workflow_01QFJBF1JH8631ay3xjpMIsLUFOrFZ0Utf8)
  * Add a hash to a simple custom detection list
    * Input :
      * Observable Type and value
      * SCD GUID
      * Description
      
* **Secure-EP-Remove-Hash-from-SCD** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Secure-EP-Remove-Hash-from-SCD__definition_workflow_01QFK9PNLF68U52dXXQCoOWmKvubDKLvCay)
  * Remove a hash from a simple custom detection list
    * Input :
      * Observable Type and value
      * SCD GUID
      
* **Securee-EP-Get-Inbox** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Secure-EP-Get-Inbox-Unresolved__definition_workflow_01QFKT9QKW6HF54rbS4lW4f6cGLmpQx1itN)
  * Get Endpoints in Inbox (Unresolved)
    * Input :
      * Table Output Enable true/false
    * Output :
      ** Json and Table with hostname and guid(if enable)
      
    
### Cisco SecureX 
* **CTR-Get Incident Details**[Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/CTR-Get-Incident-Details__definition_workflow_01MUZKOII7TH77AMxE0a7QyA5SPUR670m5z)
  * Get content of an Incident ID in SecureX (private CTIA)
    * Output :
      * Raw Json result

* **CTR Update Incident** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/CTR-Update-Incident__definition_workflow_01MU6L38WDI011Gi239oxMLUnIwKdExKqGl)*
  * Update an existing incident in SecureX
    * Input : 
      * Field to Update
      * New value
      * Incident ID 
      
* **SX-TR-Post-Judgement-to-private-Intelligence** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/SX-TR-Post-Judgement-to-private-Intelligence__definition_workflow_01JRJ1YM36RRL5LtoOJpNil5rHHFmw9PlOI)
  * Post a judgement about an observable in your SecureX Private Intelligence
    * Input :
      * Observable Type and Value
      * Disposition Name and Number
      * Reasons
      + Expiration delay in days
      
* **Core-Get-List-Table-with-unique-Values** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Core-Get-List-Table-with-unique-Values__definition_workflow_01JQV4DC02D934XLB7J1u6CcmV9yNotBbE3)
  * From a list of multiple values, get a list or/and a table with only unique values 
    * Input :
      * Input json
      * Column wanted from input json
      * Output Tables : True/False
    * Output :
      * List of unique value
      * Table with unique value if set to True  
   
          
### Cisco Secure Malware Analytics
* **Cisco-Malware-Analytics-TG-Collect-Feed** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Cisco-Malware-Analytics-TG-Collect-Feed__definition_workflow_01QFLDMMVX5L61VvlcUzlpg7Jp7vBMaDeFU)
  * Collect Curated Hourly Feeds from Threat Grid Cloud 
    * Input : 
      * Feed Name and Format
      * Output Table Enable : True/False
    * Output : 
      * Raw feed in selected format
      * Table with parsed data if enable and format JSON

### Cisco Webex
* **Webex-Teams-Send-Simple-Adaptive-Card** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Webex-Teams-Send-Simple-Adaptive-Card__definition_workflow_01MMGML9TZA3Q0R6xzMOaQA1T5d8o4J1x1q) *     
  * **Deprecated version - incorrect field label** - maintain for compatibility with existing workflow*
  * Send a pre-formated adaptive Card in Cisco Webex
    * Input :
      * Button Action Link 
      * Image URL : Url link for the Image/Logo
      * Notification Type
      * Text 2 : Message title
      * Text 1 : Message Text - part 1
      * Title : Message Text - part 2
      * Room ID and Webex Token 
      
* **Webex-Teams-Send-Simple-Adaptive-Card-V2** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Webex-Teams-Send-Simple-Adaptive-Card-V2__definition_workflow_01MXL3QX1CI992DKEA4Anda0qAiNhyIdcCm) *     
  * Send a pre-formated adaptive Card in Cisco Webex
    * Input :
      * Button Text
      * Button Action Link 
      * Image/Logo URL
      * Notification Type
      * Message Title
      * Message Text
      * Room ID and Webex Token
  
      
### Cisco Secure Email
* **Cisco-Secure-Email-Get-Verdict-Update** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Cisco-Secure-Email-Get-Verdict-Update__definition_workflow_01NEP2RIWPFTT3wu6BIzDenNp97Polj1s1X)
  * Query Cisco Secure Email (ESA/CES) for the last X hour(s) AMP File Verdict Update
    * Input :
      * Delay (in hour, min 1)
      * Secure Email JWT Token
      * Output Table enable : True/False
    * Output :
      * Full Json output
      * Table with hash if enable

### TheHive
* **Create Incident** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Create-TheHive-Case__definition_workflow_01MKXD2ZOHC0G6MZ8JD9DIDdTGq2V3NXFck)
  * Create an incident in TheHive
    * Input :
      * Title
      * Description
      * Observable type and value
    * Output :
      * TheHive Case ID
	  
* **TheHive - add Observables to TheHive Case 🐝** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/TheHive-Add-Observables-to-Case__definition_workflow_01JAKPQGRCHIZ6uVQlRw3zrZc8Lq9ukFuyl)
  * Update an existing incident in TheHive with a new observable
    * Input :
      * Observable Type and Value
      * TheHive Case ID


### NumVerify
* **(Atomic-NumVerify-ValidatePhoneNumber** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Atomic-NumVerify-ValidatePhoneNumber__definition_workflow_01MXMBOXTJ9T13zB0Yg1VsLG9NRM7n9cpU4)
  * Verify a phone number using NumVerify
    * Input :
      * Phone number with country code (ex : 33612121212 for the french mobile number +33 (0) 612 121 212)
    * output :
      * Valid, Carrier, Line Type, Country
  
### YouTube
* **Search a video** 
  * Search on youtube video based on a keyword
    * Input :
      * Keyword
    * Output :
      * Video Title and Video ID
  

### Notes
* Please test this properly before implementing in a production environment. 

**Authors** : Ivan Berlinson, Sven Kutzer (Cisco)