# How to install and setup the workflows in SecureX Orchestration (SXO)

1. Logon to SecureX via: https://sign-on.security.cisco.com/. 
> **NOTE:** If you don't have a SecureX Account, please follow the [Quick Start Guide](https://www.cisco.com/c/en/us/td/docs/security/secure-sign-on/sso-quick-start-guide/sso-qsg-welcome.html).
2. Go to Menu "Orchestration" 
  ![Install___SXO_Menu](/Images/Install___SXO_Menu.jpg)


## Create New GitHub Repo
Add GitHub Repo to your SXO instance to import the SXO Workflows.

1. Go to Admin in the left-hand menu
  ![Install___SXO_MenuAdmin](/Images/Install___SXO_MenuAdmin.jpg)
2. Go to Git Repositories and a **New Git Repository** 
  ![Install___SXO_MenuGit](/Images/Install___SXO_MenuGit.jpg)
3. Use the following **DISPLAY NAME**: **CiscoSecureX-UnifiedAlerting** and the following details:
  * **DEFAULT ACCOUNT KEYS**: **Git_Credentials**
  * **PROTOCOL** set to **HTTPS**
  * **REST API REPOSITORY**: **api.github.com/repos/iberlinson/SX-AO**
  * **BRANCH**: **main**
  * **Code Path**: **Hack-a-Thon**
  * Leave all other fields on default/empty and click **SUBMIT**.
  * ![Install___SXO_GitRepo](/Images/Install___SXO_GitRepo.jpg)

4. Repeat the step and add an additional Repository for the required Atomic Actions
  Use the following **DISPLAY NAME**: **CiscoSecureX-UnifiedAlerting_AtomicActions** and the following details:
  * **DEFAULT ACCOUNT KEYS**: **Git_Credentials**
  * **PROTOCOL** set to **HTTPS**
  * **REST API REPOSITORY**: **api.github.com/repos/iberlinson/SX-AO**
  * **BRANCH**: **main**
  * **Code Path**: **Atomics**
  * Leave all other fields on default/empty and click **SUBMIT**.
  * ![Install___SXO_GitRepoAtomic](/Images/Install___SXO_GitRepoAtomic.jpg)


## Import SXO Atomic Actions from Github
1. Go to Workflows select "Atomic Actions" and **IMPORT** the Workflows

**This step is a pre-requirement to successful import the workflow in the next step!**
  ![Install___SXO_ImportAtomic](/Images/Install___SXO_ImportAtomic.jpg)
2. Import the following 
  *	**Cisco-Secure-EP-Get-critical-cloud-IOC**
  *	**Webex - Simple adaptive card**
  *	**Create TheHive case** ( if you are not planing to integrate TheHive, just add a random value as Bearer Token )
  *	**CTR - Get Incident Details**
  *	**CTR - Update Incident**
  *	**Cisco Umbrella- Get Last security event Table**
  ![image](https://user-images.githubusercontent.com/41740851/111790249-4bb33200-88c2-11eb-981c-2ab6a4cc10b0.png)


## Import SXO Workflow from Github
1. Go to Workflows and **IMPORT** the Workflows
  * **Hack-a-Thon-Umbrella-AlertingV2-Incident-Aggregation**
  * **Hack-a-Thon-SecureEP-AlertingV2-Incident-Aggregation**
  * **Hack-a-Thon-Admin-Remove-All-detection-stats**
  ![image](https://user-images.githubusercontent.com/41740851/111790428-78674980-88c2-11eb-8ccc-e5ce3c1a116f.png)
2. Update the missing informations, like 
  * AMP Credentials
  * CTR Credentials
  * Webex Access Token - [click here to see how you can create a presistent Access Token](https://github.com/iberlinson/SX-AO/blob/main/WebexAccessToken.md)
  * ...
  
  
