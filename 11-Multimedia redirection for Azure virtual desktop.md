# Lab 10: Multimedia redirection for Azure virtual desktop

### Estimated Duration: 20 Minutes

## **Overview**

In this lab, We'll be implementing MS Teams for AVD. Microsoft Teams on Azure Virtual Desktop supports chat and collaboration. With media optimizations, it also supports calling and meeting functionality. With media optimization for Microsoft Teams, the Remote Desktop client handles audio and video locally for Teams calls and meetings.


## Exercise 1: Multimedia redirection for Azure virtual desktop

1. Navigate to the Azure portal, then search for **Azure Virtual Desktop** in the search bar and select **Azure Virtual Desktop** from the suggestions.

   ![ws name.](media/w1.png)
   
1. Select **Host pools** from the side blade and select **GS-AVD-HP**.

   ![ws name.](media-2/avdhp.png)
   
1. Under Settings, Select **RDP Properties** **(1)** and select **Device redirection** **(2)**. Select the following options.
   
   - Microphone redirection: Select **Enable audio capture from the local devices and redirection to an audio application in the remote session** **(3)** from the dropdown.
   - Audio output location: Select **Play sounds on the remote computer** **(4)** from the dropdown
   - Camera redirection: Select **Redirect cameras** **(5)** from the dropdown.
   - Leave the rest of the properties as **default**.
   - click on **Save** **(6)**.

      ![ws name.](media-2/rdpproperties.png)

1. On your PC, search for **Remote Desktop** and open the remote desktop application with the exact icon as shown below.

   ![ws name.](./media/remote.png)
   
1. The AVD desktop client will launch, then double-click on the SessionDesktop application to access it.

   ![ws name.](media/ex4t2s2.png)
   
1. A window saying *Starting your app*, will appear. Wait for a few seconds, then enter your password to access the Application.

    - Password: **<inject key="AzureAdUserPassword" />**

      ![ws name.](media/ch14.png)

1. After the desktop has loaded, search for **Teams (1)** and click **Open (2)**, as shown in the screenshot below.

   ![ws name.](./media/teamsopenn.png)

1. In the Everyone together in Teams pane, click on Sign in as **<inject key="AzureAdUserEmail" />**.

   ![ws name.](./media/teamsopena.png)
   
1. Enter password: **<inject key="AzureAdUserPassword" />**

   ![ws name.](media/lab11-teams-signin.png)
   >**Note:** After you log in to Microsoft Teams, if a pop-up appears showing “What’s New in Teams”, click on “Continue” and then select “Got it” to proceed.
   
1. After the Teams application is launched, click on the **three dots** **(1)** then, click on **Settings** **(2)**.

   ![ws name.](media/avdv215n.png)

   >**Note:** If you receive any notification to restart Teams, click on the **Restart now** option.

   ![ws name.](media/avdv215na.png)   

1. Click on **About (1)** at the bottom. You will see a message stating **You have Microsoft Teams Version x.x.x, which is AVD SlimCore Media Optimized (2)**.

   ![ws name.](media-1/TeamsAVDn.png)
   
   >**Note**: If you see a message saying **AVD SlimCore Media not connected**. Please skip the step and continue with the lab.
   
1. Click on **Devices (1)** and explore the media devices connected to your local desktop **(2)**.

   ![ws name.](media/avdv218n.png)
   
   >**Note**: If you are not able to select other audio devices. Please skip the step and continue with the lab.
   
1. Navigate to the **Calendar (1)** in the side panel. Click on **Meet now (2)**, keep the **Meeting name (3)** as default, and select **Start meeting (4)**.

   ![ws name.](media/teams15na.png)
   
1. Make sure both **Audio** **(1)**, and **Video** **(2)** are enabled. Click on **Join now** **(3)**.

   ![ws name.](media/teams14n.png)
   >**Note:** If a pop-up appears stating “To give you the best Teams experience on a virtual desktop, we need to restart the app,” simply click “Cancel” to dismiss 
   
   >**Note**: If the audio is not working. Please skip the step and continue with the lab as this is an expected issue.
   
1. Click on **Allow access** on the Windows Security alert prompt.

   ![ws name.](media/teams16.png)
   
   >**NOTE**: If the **Invite People to join you** prompt appears, close the tab and continue.
  
1. Now, you should be able to see yourself as the video is On.

   ![](./media/camn.png)

1. Click on the **Next** button present in the bottom-right corner of this lab guide.
