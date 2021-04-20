---
layout: post
title: Installation Errors of Essential Studio | WinUI |Syncfusion
description: Learn here some information about the essential studio installation errors and steps for resolving it.
platform: winui
control: Essential Studio
documentation: ug
---

# Common Installation Errors

This article describes the most common installation errors, as well as the causes and solutions to those errors.

* [Unlocking the license installer using the trial key](https://help.syncfusion.com/winui/installation-and-upgrade/installation-errors#unlocking-the-license-installer-using-the-trial-key)
* [License has expired](https://help.syncfusion.com/winui/installation-and-upgrade/installation-errors#license-has-expired)
* [Unable to find a valid license](https://help.syncfusion.com/winui/installation-and-upgrade/installation-errors#unable-to-find-a-valid-license)
* [Unable to find a valid license or trial](https://help.syncfusion.com/winui/installation-and-upgrade/installation-errors#unable-to-find-a-valid-license-or-trial)
* [Unable to install because of another installation](https://help.syncfusion.com/winui/installation-and-upgrade/installation-errors#unable-to-install-because-of-another-installation)
* [Unable to install due to controlled folder access](http://help.syncfusion.com/winui/installation-and-upgrade/installation-errors#unable-to-install-due-to-controlled-folder-access)

## Unlocking the license installer using the trial key

### Problem

**Error Message:** Sorry, the provided unlock key is a trial unlock key and cannot be used to unlock the licensed version of our Essential Studio for WinUI installer.

![Alert Message](Errors/Installation_Errors_img1.png)

### Reason

You are attempting to use a Trial unlock key to unlock the licensed installer.

### Suggested solution

Only a licensed unlock key can unlock a licensed installer. So, to unlock the Licensed installer, use the Licensed unlock key. To generate the licensed unlock key, refer to [this](http://syncfusion.com/kb/2326) article.


## License has expired

### Problem

**Error Message:** Your license for Syncfusion Essential Studio for WinUI has been expired since {date}. Please renew your subscription and try again.

**Online Installer**

![Warning Message](Errors/Installation_Errors_img2.png)

### Reason

This error message will appear if your license has expired.

### Suggested solution

You can renew your subscription [here](https://www.syncfusion.com/sales/products), or you can contact our sales team at <salessupport@syncfusion.com>. You can also extend the 30-day trial period after your license has expired.


## Unable to find a valid license

### Problem

**Error Message:** Sorry, we are unable to find a valid license for Essential Studio for WinUI under your account.

![Alert Message](Errors/Installation_Errors_img3.PNG)

### Reason

The following are possible causes of this error:

* When your trial period expired
* When you don't have a license or an active trial

### Suggested solution

You can renew your subscription [here](https://www.syncfusion.com/sales/products), or you can contact our sales team at <salessupport@syncfusion.com>.

## Unable to find a valid license or trial

### Problem

**Error Message:** Sorry, we are unable to find a license or trial for Essential Studio for WinUI under your account.

![Warning Message](Errors/Installation_Errors_img6.PNG)

### Reason

The following are possible causes of this error:

* You are not the license holder of your license.
* Your account administrator has not yet assigned you a license. Please contact your account administrator or send an email to <clientrelations@syncfusion.com> to have a license assigned to you.

### Suggested solution

Please check your subscription status [here](https://www.syncfusion.com/sales/products), or contact <salessupport@syncfusion.com>. You can also continue the 30-day trial period.

## Unable to install because of another installation

### Problem

**Error Message:** Another installation is in progress. You cannot start this installation without completing all other currently active installations. Click cancel to end this installer or retry to attempt after currently active installation completed to install again.

![Warning Message](Errors/Installation_Errors_img4.png)

### Reason

You are trying to install when another installation is already running in your machine.

### Suggested solution

Open and kill the msiexec process in the task manager and then continue to install Syncfusion. If the problem is still present, restart the computer and try Syncfusion installer. 

1. Open the Windows Task Manager.

2. Browse the Details tab.

3. Select the msiexec.exe and click **End task**.

![Task Manager](Errors/Installation_Errors_img5.png)

## Unable to install due to controlled folder access

### Problem

#### Offline:

**Error Message:** Controlled folder access seems to be enabled in your machine. The provided install or samples location (e.g., Public Documents) is protected by the controlled folder access settings.

![Warning Message](Errors/Installation_Errors_img7.png)

#### Online:

**Error Message:** Controlled folder access seems to be enabled in your machine. The provided install, samples, or download location (e.g., Public Documents) is protected by the controlled folder access settings.

![Warning Message](Errors/Installation_Errors_img8.png)

### Reason

You have enabled controlled folder access settings on your computer.

### Suggested solution

Select a different location to install or deactivate your machine's controlled folder access settings, and then try installing.

