# Lab 2(B): Monitoring using Azure Monitor for AVD

### Estimated Duration: 20 Minutes

## **Overview**

In this exercise, We'll be reviewing monitoring data of the AVD environment using Azure Insights which you had configured in part A of Exercise 2.

## Exercise 1: Exploring Insights for AVD

### Task 1: Access AVD using the browser and Remote client

   
1. Navigate to **Your Own PC/computer/workstation**, go to **Start** search for **Remote desktop** and open the application with the exact icon as shown below.

   ![ws name.](media/137.png)
   
1. Click on the *ellipses* and select **Unsubscribe**. Click on **Continue** for any warning.

   ![ws name.](media/lb16.png)

   >**NOTE**: We need to unsubscribe from the feed because in Exercise 4 we subscribed to the AVD feed using a different user.

1. Click on the **Subscribe** button.

   ![ws name.](media/a49.png)

1. Enter the user credentials to access the workspace.

   - Username: *Paste the username*  **<inject key="Avd User 02" />** *then click on* **Next**.
   
   - Password: *Paste the password*  **<inject key="AVD User Password" />** *and click on* **Sign in**.

      ![ws name.](media/password2.png)

      >**NOTE**: If there's a dialog box saying ***Help us protect your account***, then select the **Skip for now** option.

      ![](media/login2.png)
    
1. Make sure to **uncheck** *Allow my organization to manage my device* and click on **No, sign in to this app only** if you are directed to the tab.

   ![ws name.](media/ex4t1s9.png)

1. In the AVD client, double-click on the **Session Desktop** to access it. 

   ![ws name.](media-2/avddesktop.png)

1. Enter your **credentials** to access the application and click on **Submit**.

   - Username: *Paste the username*  **<inject key="Avd User 02" />** then click on **Next**.*
   - Password: *Paste the* **<inject key="AVD User Password" />** *and click on* **OK**.* 
   
   ![ws name.](media/lb37.png)
  
1. The virtual Desktop will launch as shown below. 

   ![ws name.](media/sessiondesktop1.1.png)
   
   >**NOTE**: **DO NOT** close the session or the AVD Remote client. Keep it running.


### Task 2: Exploring Insights data

>**NOTE**: While performing this exercise, you might see that data is not loaded as expected. In such a scenario, Please refresh the **Insights** page until the data is loaded.
   
1. Now, Navigate to Azure Virtual Desktop and select **Insights** under **Monitoring** blade in the Azure Portal.

   ![ws name.](media-2/Lab2(a)-ex2-step2.png)
   
1. In **Insights** page, **Click** on **Overview** tab *(1)*. Here on the **gs-avd-hp** host pool, you'll be able to monitor the status and health of the session hosts (3).

   ![ws name.](media-1/new-avd-lab13-18.jpg)
   
1. **Click** on **Users** *(1)* tab, In **UPN to search for** blank paste **<inject key="Avd User 01" />** *(2)* and wait for the data to load. This tab gives an overview of the user's usage. Scroll down and explore different information loaded.

   ![ws name.](media-1/new-avd-lab13-23.jpg)
   
1. **Click** on the **Utilization** tab, This tab gives information about session summary, core info, and more information about the utilization of resources.

   ![ws name.](media-1/new-avd-lab13-20.jpg)
   
1. **Click** on **Clients** *(1)* tab, Here you'll be able to monitor the number of users *(2)* connected to AVD using the browser and remote client application.

   ![ws name.](media-1/new-avd-lab13-22.jpg)
   
1. Spend some time on the page to explore different monitoring abilities offered by Azure Insights.

### You have successfully completed the Hands-on Lab.

By completing this **Azure Virtual Desktop (AVD)** hands-on lab, you have gained valuable, practical experience in deploying and managing a secure, scalable virtual desktop environment. Starting with creating host pools and configuring FSLogix profile containers, you learned to publish applications, assign access to users, and validate connectivity through both browser and desktop clients. You also explored monitoring and diagnostics with Log Analytics and Azure Monitor, optimized performance and costs through load balancing, auto-scaling, and Start VM on Connect, and implemented advanced security measures such as MFA, Conditional Access, AppLocker, and app masking. This comprehensive journey equips you with the knowledge and skills to confidently design, manage, and secure enterprise-grade virtual desktop solutions using Azure Virtual Desktop.
