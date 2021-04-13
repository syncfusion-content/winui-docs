---
layout: post
title: Installation and Deployment process for Syncfusion WinUI products
description: this section provides information regarding the Syncfusion WinUI Offline installer and steps for installing it
platform: winui
control: Installation and Deployment
documentation: ug

---

# Installation using Offline Installer

## Installing with UI   

The following procedure illustrates how to install Essential Studio WinUI platform.

1. Close all the running Visual Studio instances.

2. Double-click the Syncfusion WinUI platform installer file. The Installer Wizard opens and extracts the package automatically.

   ![Installer extraction wizard](Platform_images/Step-by-Step-Installation_img1.png)

   N> The Installer wizard extracts the syncfusionessentialwinui_(version).exe dialog, displaying the unzip operation of the package.

3. You have two options to unlock the Syncfusion installer:

   
* *Login To Install*
   
* *Use Unlock Key*
   
   
   
   **Login To Install**
   
   You should enter your Syncfusion Direct-Trac login credentials. If you don't have Syncfusion Direct-Trac login credentials, then you can click on Sign Up to a create new account. Else if you forgot your password, click on Reset Password to create new password. Here Email address and Password is validated and the Platform Selection window opens.

   ![Login credentials](Platform_images/Step-by-Step-Installation_img2.png)   


   **Use Unlock Key**
   
   You should use the Syncfusion License/Trial key. Trial key is valid for 30 days and the installer won't accept the expired trial key. Licensed customer can generate key from [here](https://www.syncfusion.com/kb/2326).

   ![Product key](Platform_images/Step-by-Step-Installation_img3.png)   


4. After reading the License Terms and Conditions, check the **I agree to the License Terms and Conditions** check box.


5. Click Next. Select the Installation, Samples Folder and Advanced Options screen opens. If there is no previous version installed for current platform, click Install to install in the displayed default location.


    ![Advanced options](Platform_images/Step-by-Step-Installation_img4.png)


    * Select the **Install Demos** check box to install Syncfusion samples, or leave the check box clear, when you do not want to install Syncfusion samples.
    * Select the **Create Desktop Shortcut** checkbox to create the desktop shortcut for Syncfusion Control Panel.
	* Select the **Create Start Menu Shortcut** checkbox to create the start menu shortcut for Syncfusion Control Panel.



6.  If any previous version installed for current platform, Click Next in the same Advanced Options screen to select the versions to be uninstalled.


    ![Advanced options](Platform_images/Step-by-Step-Installation_img7.png)
	
	
	N> From the 2021 Volume 1 release, Syncfusion has provided option to uninstall the previous versions from 18.1 while installing the new version.
	

7.	Click Proceed.

	![Uninstalling wizard](Platform_images/Step-by-Step-Installation_img10.png)
	
	
	N> If any version is selected to uninstall, pop up screen will appear for confirmation, if continue is selected, the Progress screen will display the uninstall progress and install progress respectively. If none of the version is selected to uninstall, install progress alone will be progressed.
	
	
	![Uninstalling wizard](Platform_images/Step-by-Step-Installation_img8.png)


	![Installing wizard](Platform_images/Step-by-Step-Installation_img5.png)
	
	
	N> The Completed screen is displayed once the WinUI platform is installed. If any version is selected to uninstall, The completed screen will display both install and uninstall status.

    
	![Installation completed](Platform_images/Step-by-Step-Installation_img9.png)


8. Click the **Launcher Control Panel** link to launch the [Syncfusion Control Panel](https://help.syncfusion.com/common/essential-studio/utilities#dashboard ) after installing.


9. Click Finish. Syncfusion WinUI platform is installed in your system.

## Installing in silent mode

The Syncfusion Essential Studio Platform Installer supports installing/uninstalling through Command Line. The following sections illustrate this ability. 

### Command Line Installation

Follow the steps below to install through Command Line in Silent mode.

1. Double-click the Syncfusion Essential Studio platform installer file. The Installer Wizard opens and extracts the package automatically. 
2. The syncfusionessentialwinui_(version).exe file is extracted into the Temp folder.
3. Run %temp%. The Temp folder will open. The syncfusionessentialwinui_(version).exe file is available in one of the folders.
4. Copy the extracted syncfusionessentialwinui_(version).exe file in local drive.
5. Cancel the Wizard.
6. Open the Command Prompt in administrator mode and pass the following arguments.

   
   **Arguments:** “installer file path\SyncfusionEssentialStudio(platform)_(version).exe” /Install silent /PIDKEY:“(product unlock key)” [/log “{Log file path}”] [/InstallPath:{Location to install}] [/InstallSamples:{true/false}] [/CreateShortcut:{true/false}] [/CreateStartMenuShortcut:{true/false}]


   N> [..] – Arguments inside the square brackets are optional.

   **Example:** “D:\Temp\syncfusionessentialwinui_x.x.x.x.exe” /Install silent /PIDKEY:“product unlock key” /log “C:\Temp\EssentialStudio_Platform.log” /InstallPath:C:\Syncfusion\x.x.x.x /InstallSamples:true /CreateShortcut:true /CreateStartMenuShortcut:true

	
7. Essential Studio for WinUI is installed.

   N> x.x.x.x needs to be replaced with the Essential Studio version and the Product Unlock Key needs to be replaced with the Unlock Key for that version.
   

### Command Line Uninstallation

Syncfusion Essential Studio supports uninstalling through Command Line in Silent mode. The following steps illustrate this. 

1. When you do not have the extracted installer (syncfusionessentialwinui_(version).exe) then follow the steps from 2 to 7.
2. Double-click the Syncfusion Essential Studio platform installer file. The Installer Wizard opens and extracts the package automatically.
3. The syncfusionessentialwinui_(version).exe file is extracted into the Temp folder.
4. Run %temp%. The Temp folder will open. The syncfusionessentialwinui_(version).exe file is available in one of the folders.
5. Copy the syncfusionessentialwinui_(version).exe file in local drive. 
6. Cancel the Wizard.
7. Open the Command Prompt in administrator mode and pass the following arguments.
   
   **Arguments:** “Copied installer file path\syncfusionessentialwinui_(version).exe” /uninstall silent 

   **Example:** “D:\Temp\syncfusionessentialwinui_x.x.x.x.exe" /uninstall silent


8. Essential Studio for WinUI is uninstalled.

   N> x.x.x.x needs to be replaced with the Essential Studio version installed in your machine.
   
   
