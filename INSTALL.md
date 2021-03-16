# How to install and setup the workflows in SecureX Orchestration (SXO)

1. Logon to SecureX via: https://sign-on.security.cisco.com/. 
> **NOTE:** If you don't have a SecureX Account, please follow the [Quick Start Guide](https://www.cisco.com/c/en/us/td/docs/security/secure-sign-on/sso-quick-start-guide/sso-qsg-welcome.html).
2. Go to Menu "Orchestration" 
  ![SecureX_Menu](/Images/Install___SXO_Menu.jpg)


## Create New GitHub Repo
Add GitHub Repo to your SXO instance to import the SXO Workflows.

1. Go to Admin in the left-hand menu
  ![git_1_Menu](/Images/Install___SXO_MenuAdmin.jpg)
2. Go to Git Repositories and a **New Git Repository** 
  ![git_2_NewRep](/Images/Install___SXO_MenuGit.jpg)
3. Use the following **DISPLAY NAME**: **CiscoSecureX-UnifiedAlerting** and the following details:
  * **DEFAULT ACCOUNT KEYS**: **Git_Credentials**
  * **PROTOCOL** set to **HTTPS**
  * **REST API REPOSITORY**: **api.github.com/repos/iberlinson/SX-AO**
  * **BRANCH**: **main**
  * **Code Path**: **Hack-a-Thon**
  * Leave all other fields on default/empty and click **SUBMIT**.
  * ![git_2_RepData](/Images/Install___SXO_GitRepo.jpg)
  
