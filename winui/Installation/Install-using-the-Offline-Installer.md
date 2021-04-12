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

The steps below show how to install the Essential Studio WinUI platform.

1.	Open the Syncfusion WinUI platform offline installer file by double-clicking it. The Installer Wizard automatically opens and extracts the package

    ![Installer extraction wizard](Platform_images/Step-by-Step-Installation_img1.png)

    N> The Installer wizard extracts the syncfusionessentialwinui_(version).exe dialog, which displays the package's unzip operation.

2.	To unlock the Syncfusion offline installer, you have two options:

   
    * *Login To Install*
   
    * *Use Unlock Key*
   
   
   
    **Login To Install**
   
    You must enter your Syncfusion email address and password. If you don't already have a Syncfusion account, you can sign up for one by clicking **"Create an account"**. If you have forgotten your password, click on **"Forgot Password"** to create a new one. Once you've entered your Syncfusion email and password, click Next.

    ![Login credentials](Platform_images/Step-by-Step-Installation_img2.png)   


    **Use Unlock Key**
   
    Unlock keys are used to unlock the Syncfusion offline installer, and they are platform and version specific. You should use either Syncfusion licensed or trial Unlock key to unlock Syncfusion WinUI installer.
   
    The trial unlock key is only valid for 30 days, and the installer will not accept an expired trial key. 
   
    To learn how to generate an unlock key for both trial and licensed products, see [this](https://www.syncfusion.com/kb/2326) Knowledge Base article.

    ![Product key](Platform_images/Step-by-Step-Installation_img3.png)   


3.	After reading the License Terms and Privacy Policy, check the **“I agree to the License Terms and Privacy Policy”** check box. Click the Next button.


4.	Change the install and sample locations here. You can also change the Additional settings. Click Install to install with the default settings.


    ![Advanced options](Platform_images/Step-by-Step-Installation_img4.png)

    **Additional Settings**
    
	* Select the **Install Demos** check box to install Syncfusion samples, or leave the check box clear, when you do not want to install Syncfusion samples.
    * Select the **Create Desktop Shortcut** checkbox to create the desktop shortcut for Syncfusion Control Panel.
	* Select the **Create Start Menu Shortcut** checkbox to create the start menu shortcut for Syncfusion Control Panel.



5.	If any previous versions of the current platform is installed, in the same Advanced Options screen, click Next to select the versions to be uninstalled, then click Proceed


    ![Advanced options](Platform_images/Step-by-Step-Installation_img7.png)
	
	
	N> From the 2021 Volume 1 release, Syncfusion has added the option to uninstall previous versions from 18.1 while installing the new version.
	

6.	Click Proceed. A confirmation window will appear to confirm the removal of the selected products. Continue by clicking the Continue button

	![Uninstalling wizard](Platform_images/Step-by-Step-Installation_img10.png)
	
	
	N> If any version is selected to uninstall, a confirmation screen will appear; if continue is selected, the Progress screen will display the uninstall and install progress, respectively. If none of the versions are chosen to be uninstalled, only the installation progress will be displayed.
	
	
	![Uninstalling wizard](Platform_images/Step-by-Step-Installation_img8.png)


	![Installing wizard](Platform_images/Step-by-Step-Installation_img5.png)
	
	
	N> When the package is installed, the Completed screen appears. If a version is chosen to be uninstalled, the completed screen will show both the install and uninstall status.

    
	![Installation completed](Platform_images/Step-by-Step-Installation_img9.png)


7.  After installing, click the **Launch Control Panel** link to open the Syncfusion Control Panel.


8.  Click the Finish button. Your system has been installed with the Syncfusion Essential Studio WinUI platform.

## Installing in silent mode

The Syncfusion Essential Studio WinUI Installer supports installation and uninstallation via the command line. The sections that follow demonstrate this ability.

### Command Line Installation

To install through the Command Line in Silent mode, follow the steps below.

1.	Run the Syncfusion WinUI installer by double-clicking it. The Installer Wizard automatically opens and extracts the package.
2.	The file syncfusionessentialwinui_(version).exe file will be extracted into the Temp directory.
3.	Run %temp%. The Temp folder will be opened. The syncfusionessentialwinui_(version).exe file will be located in one of the folders.
4.	Copy the extracted syncfusionessentialwinui_(version).exe file in local drive.
5.	Exit the Wizard.
6.	Run Command Prompt in administrator mode and enter the following arguments.


   **Arguments:** “installer file path\SyncfusionEssentialStudio(platform)_(version).exe” /Install silent /PIDKEY:“(product unlock key)” [/log “{Log file path}”] [/InstallPath:{Location to install}] [/InstallSamples:{true/false}] [/CreateShortcut:{true/false}] [/CreateStartMenuShortcut:{true/false}]


   N> [..] – Arguments inside the square brackets are optional.

   **Example:** “D:\Temp\syncfusionessentialwinui_x.x.x.x.exe” /Install silent /PIDKEY:“product unlock key” /log “C:\Temp\EssentialStudio_Platform.log” /InstallPath:C:\Syncfusion\x.x.x.x /InstallSamples:true /CreateShortcut:true /CreateStartMenuShortcut:true

	
7. Essential Studio for WinUI is installed.

   N> x.x.x.x should be replaced with the Essential Studio version and the Product Unlock Key needs to be replaced with the Unlock Key for that version.
   

### Command Line Uninstallation

Syncfusion Essential WinUI can be uninstalled silently using the Command Line. The steps below demonstrate this.

1.	Run the Syncfusion WinUI installer by double-clicking it. The Installer Wizard automatically opens and extracts the package.
2.	The file syncfusionessentialwinui_(version).exe file will be extracted into the Temp directory.
3.	Run %temp%. The Temp folder will be opened. The syncfusionessentialwinui_(version).exe file will be located in one of the folders.
4.	Copy the extracted syncfusionessentialwinui_(version).exe file in local drive.
5.	Exit the Wizard.
6.	Run Command Prompt in administrator mode and enter the following arguments.

   
   **Arguments:** “Copied installer file path\syncfusionessentialwinui_(version).exe” /uninstall silent 

   **Example:** “D:\Temp\syncfusionessentialwinui_x.x.x.x.exe" /uninstall silent


8. Essential Studio for WinUI is uninstalled.

   
   
