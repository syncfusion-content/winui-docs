---
layout: post
title: Header in WinUI Scheduler control | Syncfusion
description: Learn here all about to customize header height, date format and appearance of Syncfusion WinUI Scheduler (SfScheduler) control and more. 
platform: winui
control: SfScheduler
documentation: ug
---

# Header in WinUI Scheduler (SfScheduler)

Change the header height, date format, and appearance of SfScheduler.

## Header height

Change the scheduler header height by using the [HeaderHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_HeaderHeight) property of SfScheduler. By default, the header height is `50.`

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2" %}
<scheduler:SfScheduler x:Name="Schedule" 
                       HeaderHeight="100">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" %}
this.Schedule.HeaderHeight = 100;
{% endhighlight %}
{% endtabs %}

![change-header-height-in-winui-scheduler-timeslot-view](Header_Images/header-height-in-winui-scheduler.png)

## Header date format

Change the Scheduler header date format of scheduler by using the [HeaderDateFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_HeaderDateFormat) property of SfScheduler. By default, the header date format is `MMMM yyyy.`

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2" %}
<scheduler:SfScheduler x:Name="Schedule" 
                       HeaderDateFormat="MMM-yyyy">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" %}
this.Schedule.HeaderDateFormat = "MMM-yyyy";
{% endhighlight %}
{% endtabs %}

![customize-header-date-format-in-winui-scheduler-timeslot-view](Header_Images/customize-header-date-format-in-winui-scheduler.png)

## Appearance customization

The scheduler header appearance can be achieved by using the `HeaderTemplate` property or style the header appearance using the `SchedulerHeaderControl` in the scheduler. Change the background color, textStyle, borderBrush, and more by setting the style property for `SchedulerHeaderControl.`

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="3 4 5 6 7 8 9" %}
<Grid>
    <Grid.Resources>
        <Style TargetType="scheduler:SchedulerHeaderControl">
            <Setter Property="Background" Value="#f08a5d"/>
            <Setter Property="Foreground" Value="White"/>
            <Setter Property="FontStyle" Value="Italic"/>
            <Setter Property="BorderBrush" Value="BlueViolet"/>
            <Setter Property="BorderThickness" Value="2"/>
        </Style>
    </Grid.Resources>

    <scheduler:SfScheduler x:Name="Schedule">
    </scheduler:SfScheduler>
</Grid>
{% endhighlight %}
{% endtabs %}

![customize-the-scheduler-header-appearance-in-winui-scheduler-timeslot-view](Header_Images/customize-the-scheduler-header-appearance-in-winui-scheduler.png)

#### Customize header appearance using DataTemplate

Customize the header appearance of scheduler by using the [HeaderTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_HeaderTemplate) property of SfScheduler.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2 3 4 5 6 7 8 9" %}
<scheduler:SfScheduler x:Name="Schedule">
    <scheduler:SfScheduler.HeaderTemplate>
        <DataTemplate>
                <TextBlock FontStyle="Italic"
                           Foreground="#8551F2"
                           FontSize="25"
                           Text="{Binding}"/>
        </DataTemplate>
    </scheduler:SfScheduler.HeaderTemplate>
</scheduler:SfScheduler>
{% endhighlight %}
{% endtabs %}


![customize-the-scheduler-header-appearance-using data-template-in-winui-scheduler-timeslot-view](Header_Images/customize-the-scheduler-header-appearance-using-data-template-in-winui-scheduler.png)