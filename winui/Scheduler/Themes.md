---
layout: post
title: Themes in WinUI Scheduler control | Syncfusion
description: Learn here all about to use various themes in Syncfusion WinUI `Scheduler`(`SfScheduler`) control and more.
platform: winui
control: SfScheduler
documentation: ug
---

# Themes in WinUI Scheduler (SfScheduler)
 The WinUI Scheduler allows you to apply different themes to customize its appearance for a better user exoerience.

Refer to the following link for guidance on applying themes: [Themes for Syncfusion WinUI controls](https://help.syncfusion.com/winui/common/themes) 

The following are some of the keys for WinUI SfScheduler control:

<table>
    <tr>
        <td><b>Key</b></td>
        <td><b>Description</b></td>
    </tr>
    <tr>
        <td>SyncfusionSchedulerBorderBrush</td>
        <td>Border color of the SfScheduler control.</td>
    </tr>
    <tr>
        <td>SyncfusionSchedulerBackground</td>
        <td>Background color of the SfScheduler control.</td>
    </tr>
    <tr>
        <td>SyncfusionSchedulerBorderThickness</td>
        <td>Thickness of the border for the SfScheduler control</td>
    </tr>
    <tr>
        <td>SyncfusionSchedulerHeaderControlBackground</td>
        <td>Background color of the header in SfScheduler.</td>
    </tr>
    <tr>
        <td>SyncfusionSchedulerHeaderControlForeground</td>
        <td>Foreground color of the header in SfScheduler.</td>
    </tr>
    <tr>
        <td>SyncfusionSchedulerAllowedViewTypeSelected</td>
        <td>Background color of the selected allowed view button.</td>
    </tr>
    <tr>
        <td>SyncfusionSchedulerAllowedViewTypeSelectedForeground</td>
        <td>Foreground color of the selected allowed view button.</td>
    </tr>
    <tr>
        <td>SyncfusionSchedulerHeaderControlBorderBrush</td>
        <td>Border color of the header in SfScheduler.</td>
    </tr>
    <tr>
        <td>SyncfusionSchedulerHeaderControlBorderThickness</td>
        <td>Thickness of the border for the header in SfScheduler.</td>
    </tr>
    <tr>
        <td>SyncfusionSchedulerAllowedViewNavigationButtonPadding</td>
        <td>Padding for allowed view buttons in SfScheduler.</td>
    </tr>
    <tr>
        <td>SyncfusionSchedulerHeaderAllowedViewButtonCornerRadius</td>
        <td>Corner radius for allowed view buttons in the header of SfScheduler.</td>
    </tr>
    <tr>
        <td>SyncfusionViewHeaderControlBackground</td>
        <td>Background color of the view header of SfScheduler.</td>
    </tr>
    <tr>
        <td>SyncfusionViewHeaderControlBorderBrush</td>
        <td>Border color of the view header of SfScheduler.</td>
    </tr>
    <tr>
        <td>SyncfusionViewHeaderControlBorderThickness</td>
        <td>Thickness of the border for the view header of SfScheduler.</td>
    </tr>    
</table>

You can find the keys for all themes in this [theme resource file.](https://github.com/syncfusion/winui-controls-theme-resource-files/tree/master/Syncfusion.Scheduler.WinUI)

## Customize scheduler theme appearance using ThemeResource

You can customize the default appearance of themes by overriding key values. Adjust the values of specific keys as required.

{% tabs %}
{% highlight MainWindow.xaml %}

 <scheduler:SfScheduler>

     <scheduler:SfScheduler.Resources>
         
         <ResourceDictionary>
             <ResourceDictionary.ThemeDictionaries>                 
                 <ResourceDictionary x:Key="Dark">
                      <SolidColorBrush x:Key="SyncfusionMonthCellBackground" Color="Beige" />
                      <SolidColorBrush x:Key="SyncfusionMonthCellForeground" Color="Purple" />
                     ....
                 </ResourceDictionary>               
             </ResourceDictionary.ThemeDictionaries>
         </ResourceDictionary>
         
     </scheduler:SfScheduler.Resources>

 </scheduler:SfScheduler>
{% endhighlight %}
{% endtabs %}

![customize-themes-in-winui-scheduler](Themes_Images/customize-theme-in-winui-sfscheduler)


N> The HighContrast theme settings within the scheduler will be universally applied to all pre-existing high contrast themes on the computer.
