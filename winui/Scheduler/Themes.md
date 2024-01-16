---
layout: post
title: Themes in WinUI Scheduler control | Syncfusion
description: Learn here all about to use various themes in Syncfusion WinUI Scheduler (SfScheduler) control and more.
platform: winui
control: SfScheduler
documentation: ug
---

# Themes in WinUI Scheduler (SfScheduler)
 The WinUI Scheduler allows you to apply different themes to customize its appearance for a better user exoerience.

Refer to the following link for guidance on applying themes: [Themes for Syncfusion WinUI controls](https://help.syncfusion.com/winui/common/themes) 

You can find the scheduler keys for all themes in this [theme resource file.](https://github.com/syncfusion/winui-controls-theme-resource-files/tree/master/Syncfusion.Scheduler.WinUI)

## Customize scheduler theme appearance using ThemeResource

You can customize the default appearance of themes by overriding key values. Adjust the values of specific keys as required.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

<scheduler:SfScheduler>
     <scheduler:SfScheduler.Resources
         <ResourceDictionary>
             <ResourceDictionary.ThemeDictionaries>                 
                 <ResourceDictionary x:Key="Dark">
                      <SolidColorBrush x:Key="SyncfusionMonthCellBackground" Color="Beige" />
                      <SolidColorBrush x:Key="SyncfusionMonthCellForeground" Color="Purple" />
                 </ResourceDictionary>               
             </ResourceDictionary.ThemeDictionaries>
         </ResourceDictionary>
    </scheduler:SfScheduler.Resources>
</scheduler:SfScheduler>

{% endhighlight %}
{% endtabs %}

![customize-themes-in-winui-scheduler](Themes_Images/customize-theme-in-winui-sfscheduler)


N> The HighContrast theme settings within the scheduler will be universally applied to all pre-existing high contrast themes on the computer.
