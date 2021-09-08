## Create New GitHub Repo
Add GitHub Repo to your SXO instance to import the SXO Workflows.

1. Go to Admin in the left-hand menu
  ![Install___SXO_MenuAdmin](/Images/Install___SXO_MenuAdmin.jpg)
2. Go to Git Repositories and a **New Git Repository** 
  ![Install___SXO_MenuGit](/Images/Install___SXO_MenuGit.jpg)
3. Use the following **DISPLAY NAME**: **SXO-Workflows** and the following details:
  * **DEFAULT ACCOUNT KEYS**: **Git_Credentials**
  * **PROTOCOL** set to **HTTPS**
  * **REST API REPOSITORY**: **api.github.com/repos/iberlinson/SXO-Workflows-and-Atomics**
  * **BRANCH**: **main**
  * **Code Path**: **Workflows**
  * Leave all other fields on default/empty and click **SUBMIT**.
  * ![Install___SXO_GitRepo](/Images/Install___SXO_GitRepo.jpg)

4. Repeat the step and add an additional Repository for the required Atomic Actions
  Use the following **DISPLAY NAME**: **SXO-Atomics** and the following details:
  * **DEFAULT ACCOUNT KEYS**: **Git_Credentials**
  * **PROTOCOL** set to **HTTPS**
  * **REST API REPOSITORY**: **api.github.com/repos/iberlinson/SXO-Workflows-and-Atomics**
  * **BRANCH**: **main**
  * **Code Path**: **Atomics**
  * Leave all other fields on default/empty and click **SUBMIT**.
  * ![Install___SXO_GitRepoAtomic](/Images/Install___SXO_GitRepoAtomic.jpg)
