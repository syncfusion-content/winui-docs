---
layout: post
title: Header | WinUI | Scheduler | Syncfusion
description: This section explain about how to customize header height, date format and appearance of Syncfusion WinUI Scheduler (SfScheduler)
platform: winui
control: Scheduler
documentation: ug
---

# Header in WinUI scheduler (SfScheduler)

You can change the header height, date format, and appearance of SfScheduler.

## Header height

You can change the scheduler header height by using the [HeaderHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_HeaderHeight) property of SfScheduler. By default, the header height is `50.`

{% tabs %}
{% highlight xaml %}
<scheduler:SfScheduler x:Name="Schedule" 
                       HeaderHeight="100">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c#%}
this.Schedule.HeaderHeight = 100;
{% endhighlight %}
{% endtabs %}

![change-header-height-in-winui-scheduler-timeslot-view](Header_Images/adding-header-height-in-winui-scheduler.png)

## Header date format

You can change the Scheduler header date format of scheduler by using the [HeaderDateFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_HeaderDateFormat) property of SfScheduler. By default, the header date format is `MMMM yyyy.`

{% tabs %}
{% highlight xaml %}
<scheduler:SfScheduler x:Name="Schedule" HeaderDateFormat="MMM-yyyy">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c#%}
this.Schedule.HeaderDateFormat = "MMM-yyyy";
{% endhighlight %}
{% endtabs %}

![customize-header-date-format-in-winui-scheduler-timeslot-view](Header_Images/adding-customize-header-date-format-in-winui-scheduler.png)

## Appearance customization

You can style Scheduler header appearance using the `SchedulerHeaderControl` in the scheduler. You can change the background color, textStyle, borderBrush, and more by setting the style property for `SchedulerHeaderControl.`

{% tabs %}
{% highlight xaml %}
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

![customize-the-scheduler-header-appearance-in-winui-scheduler-timeslot-view](Header_Images/adding-customize-the-scheduler-header-appearance-in-winui-scheduler.png)

### Customize header appearance using DataTemplate

You can customize the header appearance of scheduler by using the [HeaderTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_HeaderTemplate) property of SfScheduler.

{% tabs %}
{% highlight xaml %}
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


![customize-the-scheduler-header-appearance-using data-template-in-winui-scheduler-timeslot-view](Header_Images/adding-customize-the-scheduler-header-appearance-using-data-template-in-winui-scheduler.png)