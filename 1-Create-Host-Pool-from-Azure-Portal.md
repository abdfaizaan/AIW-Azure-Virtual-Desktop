# Lab 1: Create Host Pool using Getting Started Wizard

## **Scenario**

Contoso is planning to set up its infrastructure on Azure. As a first step, Contoso needs you to provision a host pool which is the main component of AVD. The creation of a host pool also includes session hosts, a default application group, and a workspace.

## **Overview**

A Host Pool is a collection of Azure virtual machines that register to Azure Virtual Desktop as session hosts when you run the Azure Virtual Desktop agent. All session host virtual machines in a host pool should be sourced from the same image for a consistent user experience. To start host pool creation, we will login to the Azure portal.
 
## Microsoft Entra Domain Services

1. In the **Azure portal**, search for and select **Microsoft Entra Domain Services**.

   ![](media/i21a.png)

1. From the list, locate and **copy the name** of your Domain Service.

   ![](media/i21b.png)

1. In the **LabVM**, in the Windows Search bar type **Powershell (1)** and select **Windows PowerShell ISE (2)**. Right click on it, then **Run as Administrator (3)**.

    ![](media/i21.png)

1. **Login to Azure:** Use the command to sign into your Azure account via device code authentication. Paste the generated URL **(1)** in the browser and enter the device code **(2)** when prompted.

    ```
    az login --use-device-code
    ```

   >**Note:** If you're experiencing issues while running the az login command, please execute the following command first
   
   ```
   Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi; Start-Process msiexec.exe -ArgumentList '/i AzureCLI.msi /quiet' -NoNewWindow -Wait; Remove-Item .\AzureCLI.msi
   ```

   ```
   https://microsoft.com/devicelogin
   ```

   ![](media/i30.png)

1. After running the command, Azure will display a code and a URL. Copy the URL, paste it into your web browser, and then provide the code. Click **Next** to proceed.

   ![](media/Active-aks2u.png)

1. Once the browser opens the Azure login page, choose your Azure account and click **Continue**.

   ![](media/Active-aks3.png)

1. Click on **Continue**, if prompted **Are you trying to sign in to Microsoft Azure CLI**.

   ![](media/i31.png)   
 
   ![](media/Active-aks5.png)

1. After successfully logging in, you'll be authenticated. Now, switch back to PowerShell to run the below command.

   >**Note:** Replace `<domain-service-name>` with the name of your **Microsoft Entra Domain Services** instance.

   ```
   Update-AzADDomainService -Name <domain-service-name> -ResourceGroupName "AVD-RG" -DomainSecuritySettingTlsV1 Disabled
   ```

   >**Note:** The process may take up to 10 minutes to complete. Once finished, proceed to the next step.

1. Once the command completes, navigate back to your Domain Service and refresh the page. You should now see that the service is running.

   >**Note:** If the service is still not running, please wait for 5 minutes and refresh the page again.

   ![ws name.](media/2avd1a.png)

## Exercise 1: Create Host Pool using Getting Started Wizard

In this exercise, we will be creating the Host pool.

1. On the **Azure portal** search for **Azure Virtual Desktop** **(1)** in the search bar and select **Azure Virtual Desktop** **(2)** from the suggestions.

   ![ws name.](media/2avd1.png)

1. On the Azure Virtual Destop Page, **Click** on the **Create a host pool**.

   ![ws name.](media/2avd2n.png)

1. On **Create a host pool** page, provide the information as mentioned below,

   **A. Project Details:**

   - Subscription: **Leave it as default (1)**
   - Resource Group prefix: Enter ***AVD-HostPool-RG-avd (2)***
   - Host pool name: **GS-AVD-HP (3)**
   - Location: Select **<inject key="Region" enableCopy="false"/> (4)** from the drop-down list.
   - Preferred app group type: **Desktop (5)**

      ![ws name.](media/projdetail.png)

      >**Note**: The region you selected in the lab might be different from the region mentioned in the screenshot.

1. In the **Host pool details** section, enter the required information and then click **Next: Session hosts > (10)** to proceed.

   - Host pool type: **Pooled (6)**
   - Create Session Host Configuration: **No (7)**
   - Load balancing algorithm: **Breadth-first (8)**
   - Max session limit: **16 (9)**

      ![ws name.](media/projdetailab.png)

1. On the **Session hosts** section, enter the required information as follow:

   - Add virtual machines: **Yes (1)**
   - Resource Group prefix: Enter ***AVD-HostPool-RG-avd (2)***
   - Name prefix: **AVD-HP01-SH (3)**
   - Virtual machine type: **Azure virtual machine (4)**
   - Virtual machine location: Select **<inject key="Region" enableCopy="false"/> (5)** from the drop-down list.
   - Availability options: **No infrastructure redundancy required (6)**
   - Security type: **Trusted launch virtual machines (7)**

      ![ws name.](media/projdetailb.png)

      >**Note**: The region you selected in the lab might be different from the region mentioned in the screenshot.

1. In the **Image**, click on **See all images** to choose the required images.

   ![ws name.](media/projdetailc.png)

1. In the Search bar Search for **Windows multi-session (1)**, then under **Windows multi-session + Microsoft 365 Apps** choose **Select (2)** and then select **Windows 11 Enterprise multi-session + Microsoft 365 Apps, Version 22H2** *(choose from dropdown)*

   ![ws name.](media/projdetaild.png)
   ![ws name.](media/projdetaile.png)

1. Virtual machine size: **Standard D4s v4**. *Click on **Change Size**, then select **D4s_v4** and click on **Select** as shown below*

   ![ws name.](media/2avd18.png)

1. Provide the information as mentioned below:
   
   - Number of VMs: **2 (1)**
   - OS disk type: **Standard HDD (2)**
   - OS disk size: **Resize to 128 GiB (P10) (3)**

      ![ws name.](media/projdetailf.png)

1. On the **Network and security** section, enter the required information as follow:

   - Virtual Network: **aadds-vnet (1)** *(choose from dropdown)*
   - Subnet: **sessionhosts-subnet(10.0.1.0/24) (2)** *(choose from dropdown)*
   - Network security group type: **Basic (3)**

      ![ws name.](media/projdetailg.png)

1. Enter the required details for **Domain to join** and **Virtual machine administrator account** as specified below, then click **Next: Workspace > (8)**

   - Select which directory you would like to join: **Active Directory (1)**
   - AD domain join UPN: **<inject key="AzureAdUserEmail" /> (2)**
   - Password: *Paste the password* **<inject key="AzureAdUserPassword" /> (3)**
   - Confirm password: **<inject key="AzureAdUserPassword" /> (4)**
   - User name: **odl_user_<inject key="DeploymentID" enableCopy="false"/>(5)**
   - Password: *Paste the password* **<inject key="AzureAdUserPassword" /> (6)**
   - Confirm password: **<inject key="AzureAdUserPassword" /> (7)**

      ![ws name.](media/projdetailh.png)

1. In the **Workspace section**, select **Yes (1)** for **Register desktop app group**.  

2. For **To this workspace**, click on **Create new (2)**.

3. Enter **GS-AVD-WS (3)** as the workspace name.

4. Click **OK (4)** to confirm.

   ![ws name.](media/projdetaili.png)

1. Click on **Review + Create**, then click **Create**.

   ![ws name.](media-1/L1E1S6n.png)

   >**NOTE**: Usually it takes 20 minutes to get deployed successfully. Sometimes it might take up to 90 minutes.
   
1. Once the deployment succeeds, it will look similar to the image shown below:

   ![ws name.](media-1/subscription.png)

1. Navigate to **AVD-HostPool-RG-avd** resource group and select **GS-AVD-HP** host pool.

   ![](media-2/hostpool.png)
   
1. It will take you to the **Host pool**. The resources created are as follows,

    - **Host Pool**: 1 (GS-AVD-HP)
    - **Session Host**: 2 (AVD-HP01-SH-0, AVD-HP01-SH-1)
    - **Application Group**: 1 (GS-AVD-HP-DAG)
    - **Application**: 1 (SessionDesktop)
    - **Workspace**: 1 (GS-AVD-WS)

      ![ws name.](media-1/L1E1S9.png)

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
- If you receive a success message, you can proceed to the next task.
- If not, carefully read the error message and retry the step, following the instructions in the lab guide.
- If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

<validation step="97d211ae-121b-445b-a278-054cda35de33" />   
   
* Click on the **Next** button present in the bottom-right corner of this lab guide.
   
   
