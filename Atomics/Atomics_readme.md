# Atomics Action


### Cisco Umbrella
* **Cisco-Umbrella-Get-Last-security-event-Table** [link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Cisco-Umbrella-Get-Last-security-event-Table__definition_workflow_01MTBS3PX08T13DnyQkuNld9GvrU538PXoI)
  * Get Security event from Cisco Umbrella Reporting API from a starting date (input variable)
  * Output :
    * Table with Category, Hostname, Obsevable
    * Last event date
    * Raw json output
    
### Cisco Secure Endpoint
*  **Cisco-Secure-EP-Get-critical-cloud-IOC** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Cisco-Secure-EP-Get-critical-cloud-IOC__definition_workflow_01MD6BCBYALHW20xugDSlrpXdDCz5RJkUoL)*
  * Get Cisco Secure EP detection events (filter on eventid) from a starting date (input variable)
  * Output
    * Table with Event Description, Target Endpoint Hostname, Observable
    * Last event date
    * Raw json output
    
### SecureX Threat Response
* **CTR-Get Incident Details**[Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/CTR-Get-Incident-Details__definition_workflow_01MUZKOII7TH77AMxE0a7QyA5SPUR670m5z)
  * Get content of an Incident ID in SecureX (private CTIA)
  * Output :
    * Raw Json answer

* **CTR Update Incident** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/CTR-Update-Incident__definition_workflow_01MU6L38WDI011Gi239oxMLUnIwKdExKqGl)*
  * Update an existing incident in SecureX
    * Input : 
      * Field to Update
      * New value
      * Incident ID      

###TheHive (http://thehive-project.org/)
* **Create Incident** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Create-TheHive-Case__definition_workflow_01MKXD2ZOHC0G6MZ8JD9DIDdTGq2V3NXFck)
  * Create an incident in TheHive
    * Input : Title, description, observable type and value
    * Output : TheHive Case ID*
	  
* **TheHive - add Observables to TheHive Case 🐝** [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/TheHive-Add-Observables-to-Case__definition_workflow_01JAKPQGRCHIZ6uVQlRw3zrZc8Lq9ukFuyl)
  * Update an existing incident in TheHive with a new observable
    * Input : Observable Type and Value, TheHive Case ID


### NumVerify (https://numverify.com/)

* **Verify a phone number** (Atomic-NumVerify-ValidatePhoneNumber) [Link](https://github.com/iberlinson/SX-AO/tree/main/Atomics/Atomic-NumVerify-ValidatePhoneNumber__definition_workflow_01MXMBOXTJ9T13zB0Yg1VsLG9NRM7n9cpU4)
  * output : Valid, Carrier, Line Type, Country
  
### YouTube
* **Search a video** 
  * Search on youtube video based on a keyword
  * Output : Video Title, Video ID
  

### Notes
* Please test this properly before implementing in a production environment. 

**Authors**
Ivan Berlinson, Sven Kutzer (Cisco)