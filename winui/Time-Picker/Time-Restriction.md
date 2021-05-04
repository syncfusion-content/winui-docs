---
layout: post
title: Time Restriction in WinUI Time Picker control | Syncfusion
description: This section describes how to restrict time selection in Time Picker (SfTimePicker) control in WinUI applications.
platform: WinUI
control: SfTimePicker
documentation: ug
---

# Time Restriction in WinUI Time Picker

This section explains how to restrict the time selection in WinUI [Time Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html) control.

## Limit the available times

You can restrict the users from selecting a time within the particular range by specifying [`MinTime`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_MinTime) and [`MaxTime`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_MaxTime) properties in `Time Picker` control. The default value of `MinTime` property is `1/1/1921 10:37:16 PM` and `MaxTime` property is `12/31/2121 10:37:16 PM}`.

{% tabs %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.MinTime = new DateTimeOffset(new DateTime(DateTime.Now.Year, DateTime.Now.Month, DateTime.Now.Day, 4, 00, 00));
sfTimePicker.MaxTime = new DateTimeOffset(new DateTime(DateTime.Now.Year, DateTime.Now.Month, DateTime.Now.Day, 6, 59, 59));

{% endhighlight  %}
{% endtabs %}

![Time Picker restrict the time selection with particular range](Getting-Started_images/MinMaxTime.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/TimeRestriction)

## Disable times using BlackoutTimes

If you want to block particular times from the time selection, then add that times into the [`BlackoutTimes`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_BlackoutTimes) collection. You can add more block out times to the `BlackoutTimes` collection. The default value of `BlackoutTimes` property is `null`.

{% tabs %}
{% highlight c# %}

public class ViewModel
{       
    public DateTimeOffset? SelectedTime { get; set; }
    public DateTimeOffsetCollection BlackoutTimes { get; set; }
    public ViewModel()
    {
        SelectedTime = DateTimeOffset.Now.Date;
        BlackoutTimes = new DateTimeOffsetCollection();
        BlackoutTimes.Add(new DateTimeOffset(DateTimeOffset.Now.Year, DateTimeOffset.Now.Month, DateTimeOffset.Now.Day, 0, 3, 0, DateTimeOffset.Now.Offset));
        BlackoutTimes.Add(new DateTimeOffset(DateTimeOffset.Now.Year, DateTimeOffset.Now.Month, DateTimeOffset.Now.Day, 0, 58, 0, DateTimeOffset.Now.Offset));
        BlackoutTimes.Add(new DateTimeOffset(DateTimeOffset.Now.Year, DateTimeOffset.Now.Month, DateTimeOffset.Now.Day, 1, 0, 0, DateTimeOffset.Now.Offset));
        BlackoutTimes.Add(new DateTimeOffset(DateTimeOffset.Now.Year, DateTimeOffset.Now.Month, DateTimeOffset.Now.Day, 3, 0, 0, DateTimeOffset.Now.Offset));
        BlackoutTimes.Add(new DateTimeOffset(DateTimeOffset.Now.Year, DateTimeOffset.Now.Month, DateTimeOffset.Now.Day, 9, 0, 0, DateTimeOffset.Now.Offset));
        BlackoutTimes.Add(new DateTimeOffset(DateTimeOffset.Now.Year, DateTimeOffset.Now.Month, DateTimeOffset.Now.Day, 10, 0, 0, DateTimeOffset.Now.Offset));
    }
}

{% endhighlight  %}
{% endtabs %}

{% tabs %}
{% highlight xaml %}

<editors:SfTimePicker SelectedTime="{Binding SelectedTime}" 
                      BlackoutTimes="{Binding BlackoutTimes}"
                      x:Name="sfTimePicker">
    <editors:SfTimePicker.DataContext>
        <local:ViewModel/>
    </editors:SfTimePicker.DataContext>
</editors:SfTimePicker>

{% endhighlight  %}
{% highlight C# %}

sfTimePicker.DataContext = new ViewModel();
sfTimePicker.SelectedTime = (sfTimePicker.DataContext as ViewModel).SelectedTime;
sfTimePicker.BlackoutTimes = (sfTimePicker.DataContext as ViewModel).BlackoutTimes;

{% endhighlight  %}
{% endtabs %}

![Time Picker blocks the particular times from selection](Getting-Started_images/Blackouttimes.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/ViewAndItemCustomization)

## Select time as you scroll spinner

If you want to hide the submit button and select the time directly from the dropdown time spinner without clicking the `Ok` button, use the [`ShowSubmitButtons`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_ShowSubmitButtons) property value as `false`. The default value of `ShowSubmitButtons` property is `true`.

{% tabs %}
{% highlight XAML %}

<editors:SfTimePicker ShowSubmitButtons="False"
                      x:Name="sfTimePicker"/>

{% endhighlight %}
{% highlight c# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.ShowSubmitButtons = false;

{% endhighlight %}
{% endtabs %}

![Time Picker hides the dropdown time spinner submit and cancel buttons](Getting-Started_images/ShowSubmitButtons.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/ViewAndItemCustomization)

## Cancel a time that is being changed

The [`TimeChanging`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_TimeChanging) event will be triggered as soon as a date is selected but before [`SelectedTime`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_SelectedTime) property is updated. If the change is considered invalid, it can be canceled. The `TimeChanging` event contains the following properties.

* `OldTime` - Gets a time which is previously selected.
* `NewTime` - Gets a time which is currently selected.
* `Cancel` - Gets or sets whether to cancel the selected time value update.

Users are restricted to select a blackout time from dropdown, however user can give text input through editor. As selecting a blackout time leads to crash, we can cancel the change using `TimeChanging` event.

N> `TimeChanging` event is called before the [`TimeChanged`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_TimeChanged) event when a time is selected.

{% tabs %}
{% highlight XAML %}

<editor:SfTimePicker Height="35" Width="150" TImeChanging="SfTimePicker_TimeChanging" />

{% endhighlight %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.TimeChanging += SfTimePicker_TimeChanging;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows:

{% tabs %}
{% highlight C# %}

 private void SfTimePicker_TimeChanging(object sender, Syncfusion.UI.Xaml.Editors.TimeChangingEventArgs e)
{
    var OldTime = e.OldTime;
    var NewTime = e.NewTime;

    //Cancel Selected time update
    e.Cancel = true;
}

{% endhighlight %}
{% endtabs %}

