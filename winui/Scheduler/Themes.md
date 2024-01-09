---
layout: post
title: Themes in WinUI Scheduler control | Syncfusion
description: Learn here all about to use various themes in Syncfusion WinUI Scheduler(SfScheduler) control and more.
platform: winui
control: SfScheduler
documentation: ug
---

# Themes in WinUI Scheduler (SfScheduler)
Theming plays a crucial role in enhancing the visual appeal and user experience of applications. The WinUI SfScheduler  allows you to customize its appearance by applying different themes. This section provides instructions on how to apply the themes and customize them.



## Applying Themes

The SfScheduler supports the following built-in themes:

1. Light Theme
2. Dark Theme
3. High Contrast Theme

### Light theme

SfScheduler has individual resource dictionaries for the themes mentioned above. To define a light theme, use a resource dictionary and assign a key "Light" to it and include the theme keys within it. 

{% tabs %}
{% highlight MainWindow.xaml %}

 <scheduler:SfScheduler>

     <scheduler:SfScheduler.Resources>
         
         <ResourceDictionary>
             <ResourceDictionary.ThemeDictionaries>                 
                 <ResourceDictionary x:Key="Light">
                     <SolidColorBrush x:Key="SyncfusionSchedulerBorderBrush" Color="{StaticResource DividerStrokeColorDefault}"  />
                     <SolidColorBrush x:Key="SyncfusionSchedulerBackground" Color="{StaticResource ControlSolidFillColorDefault}"  />
                     <Thickness x:Key="SyncfusionSchedulerBorderThickness">1</Thickness>
                     ....
                 </ResourceDictionary>               
             </ResourceDictionary.ThemeDictionaries>
         </ResourceDictionary>
         
     </scheduler:SfScheduler.Resources>

 </scheduler:SfScheduler>
{% endhighlight %}
{% endtabs %}



### Dark theme

For dark theme use the resource dictionary with the key  "Dark" and the necessary theme keys in it.

{% tabs %}
{% highlight MainWindow.xaml %} 

<scheduler:SfScheduler>

     <scheduler:SfScheduler.Resources>
         
         <ResourceDictionary>
             <ResourceDictionary.ThemeDictionaries>                 
                 <SolidColorBrush x:Key="SyncfusionSchedulerHeaderControlBackground" Color="{ThemeResource SystemColorWindowColor}" />
                 <SolidColorBrush x:Key="SyncfusionViewHeaderControlBackground" Color="{ThemeResource SystemColorWindowColor}" />
                <Thickness x:Key="SyncfusionSchedulerHeaderControlBorderThickness">0</Thickness>
                     ....
                 </ResourceDictionary>               
             </ResourceDictionary.ThemeDictionaries>
         </ResourceDictionary>
         
     </scheduler:SfScheduler.Resources>

 </scheduler:SfScheduler>
{% endhighlight %}
{% endtabs %}



### HighContrast theme

You can use HighContrast theme with the key "HighContrast" for the resource dictionary along with its theme keys.

{% tabs %}
{% highlight MainWindow.xaml %} 

<scheduler:SfScheduler>

     <scheduler:SfScheduler.Resources>
         
         <ResourceDictionary>
             <ResourceDictionary.ThemeDictionaries>                 
                 <SolidColorBrush x:Key="SyncfusionViewHeaderControlBackground" Color="{ThemeResource SystemColorWindowColor}" />
                 <SolidColorBrush x:Key="SyncfusionMonthViewHeaderForeground" Color="{ThemeResource SystemColorButtonTextColor}" />
                <Thickness x:Key="SyncfusionMonthViewHeaderBorderThickness">0,1,0,1</Thickness>
                     ....
                 </ResourceDictionary>               
             </ResourceDictionary.ThemeDictionaries>
         </ResourceDictionary>
         
     </scheduler:SfScheduler.Resources>

 </scheduler:SfScheduler>
{% endhighlight %}
{% endtabs %}

## Customize themes

You can cutomize the default appearance of themes by overriding the key values. You can modify the values of the specific keys as needed.

{% tabs %}
{% highlight MainWindow.xaml %}

 <scheduler:SfScheduler>

     <scheduler:SfScheduler.Resources>
         
         <ResourceDictionary>
             <ResourceDictionary.ThemeDictionaries>                 
                 <ResourceDictionary x:Key="Light">
                     <SolidColorBrush x:Key="SyncfusionMonthCellBackground" Color="LightCyan" />
                     <SolidColorBrush x:Key="SyncfusionMonthCellForeground" Color="Purple" />
                     ....
                 </ResourceDictionary>               
             </ResourceDictionary.ThemeDictionaries>
         </ResourceDictionary>
         
     </scheduler:SfScheduler.Resources>

 </scheduler:SfScheduler>
{% endhighlight %}
{% endtabs %}