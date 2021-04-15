---
layout: post
title: Date Navigations in WinUI Scheduler control | Syncfusion
description: Learn here all about Date Navigations feature of Syncfusion WinUI Scheduler(SfScheduler) control and more.
platform: winui
control: Scheduler
documentation: ug
---

# Date Navigations in WinUI Scheduler

## Range for visible dates

Visible dates can be restricted between certain range of dates, using [MaximumDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_MaximumDate) and [MinimumDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_MinimumDate) properties in SfScheduler. It is applicable in all the scheduler views.

### Minimum display date

[MinimumDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_MinimumDate) will restrict date navigations features of backward, also cannot swipe the control using touch gesture beyond the minimum date range. The dates before the minimum date will be disabled in the schedule.

{% tabs %}
{% highlight c# %}
this.Schedule.MinimumDate = new DateTime(2021, 03, 05, 10, 0, 0);
{% endhighlight %}
{% endtabs %}

### Maximum display date

[MaximumDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_MaximumDate) will restrict date navigations features of forward, and also cannot swipe the control using touch gesture beyond the maximum date range. The dates beyond the maximum date will be disabled in the schedule.

{% tabs %}
{% highlight c# %}
this.Schedule.MaximumDate = new DateTime(2021, 05, 05, 10, 0, 0);
{% endhighlight %}
{% endtabs %}

## Programmatic date navigation

You can programmatically navigate the dates in scheduler by using the [DisplayDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_DisplayDate) property of SfScheduler.

{% tabs %}
{% highlight c# %}
this.Schedule.DisplayDate = new DateTime(2021, 04, 07, 9, 0, 0);
{% endhighlight %}
{% endtabs %}

N> Date navigation before the minimum date will be reset to the scheduler minimum date and date navigation beyond the maximum date will be reset to the scheduler maximum date.

## Programmatic date selection

You can programmatically select the dates in scheduler by using the [SelectedDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_SelectedDate) property of SfScheduler.

{% tabs %}
{% highlight c# %}
this.Schedule.SelectedDate = new DateTime(2021, 04, 07, 10, 0, 0);
{% endhighlight %}
{% endtabs %}

N> Selection before minimum dates and beyond maximum dates using the `SelectedDate` is not possible.

## Programmatically change to adjacent dates

By default, the date can be navigated to next and previous views using touch gesture, by swiping the control from right to left and left to right direction. The view can be also changed programmatically using the `Forward` and `Backward` methods available in SfScheduler.

### Forward

You can use the [Forward](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_Forward) method of Scheduler for viewing the next immediate visible dates in the scheduler. It will move to next month if the scheduler view is month, similarly it will move to next week for week view and next day for day view.

{% tabs %}
{% highlight xaml %}
<scheduler:SfScheduler x:Name="Schedule"  
                       ViewType="Week">
</scheduler:SfScheduler>

<Button x:Name="Forward"
        Content="Forward"
        Click="Forward_Click">
</Button>
{% endhighlight %}
{% highlight c#%}
private void Forward_Click(object sender, RoutedEventArgs e)
{
    this.Schedule.Forward();
}
{% endhighlight %}
{% endtabs %}

### Backward

You can use the [Backward](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_Backward) method of Scheduler for viewing the previous immediate visible dates in the scheduler. It will move to previous month if the scheduler view is month, similarly it will move to previous week for week view and previous day for day view.

{% tabs %}
{% highlight xaml %}
<scheduler:SfScheduler x:Name="Schedule"  
                       ViewType="Week">
</scheduler:SfScheduler>

<Button x:Name="Backward"
        Content="Backward"
        Click="Backward_Click">
</Button>
{% endhighlight %}
{% highlight c#%}
private void Backward_Click(object sender, RoutedEventArgs e)
{
    this.Schedule.Backward();
}
{% endhighlight %}
{% endtabs %}