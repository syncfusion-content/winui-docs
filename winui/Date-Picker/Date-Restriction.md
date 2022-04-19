---
layout: post
title: Date Restriction in WinUI Date Picker control | Syncfusion
description: This section describes how to restrict date selection in Date Picker (SfDatePicker) control in WinUI applications.
platform: WinUI
control: SfDatePicker
documentation: ug
---

# Date Restriction in WinUI Date Picker

This section explains how to restrict the date selection in WinUI [Date Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html) control.

## Limit the available dates

You can restrict the users from selecting a date within the particular range by specifying [`MinDate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_MinDate) and [`MaxDate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_MaxDate) properties in `Date Picker` control. The default value of `MinDate` property is `1/1/1921` and `MaxDate` property is `12/31/2121`.

{% tabs %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2 3" %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.MinDate = new DateTimeOffset(new DateTime(2020,12,18));
sfDatePicker.MaxDate = new DateTimeOffset(new DateTime(2020,12,20));

{% endhighlight  %}
{% endtabs %}

![change-minimum-and-maximum-dates-in-winui-date-picker](Images/getting-started/change-minimum-and-maximum-dates-in-winui-date-picker.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/blob/main/Samples/DateRestriction)

## Disable dates using BlackoutDates

If you want to block particular dates from the date selection, add that dates into the [`BlackoutDates`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_BlackoutDates) collection. You can add more block out dates to the `BlackoutDates` collection. The default value of `BlackoutDates` property is `null`.

{% tabs %}
{% highlight c# tabtitle="ViewModel.cs" %}

public class ViewModel
{       
    public DateTimeOffsetCollection BlockedDates { get; set; }
    public ViewModel()
    {
        BlockedDates = new DateTimeOffsetCollection();
        BlockedDates.Add(new DateTimeOffset(new DateTime(2018, 1, 28)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 1, 26)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 1, 29)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 1, 31)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2023, 1, 28)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2024, 1, 28)));
    }
}

{% endhighlight  %}
{% endtabs %}

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="3 5" %}

<editors:SfDatePicker  
                      x:Name="sfDatePicker"
                      BlackoutDates="{Binding BlockedDates}">
    <editors:SfDatePicker.DataContext>
        <local:ViewModel/>
    </editors:SfDatePicker.DataContext>
</editors:SfDatePicker>

{% endhighlight  %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="3" %}

sfDatePicker.DataContext = new ViewModel();
sfDatePicker.BlackoutDates = (sfDatePicker.DataContext as ViewModel).BlockedDates;;

{% endhighlight  %}
{% endtabs %}

![change-black-out-dates-disabled-dates-in-winui-date-picker](Images/getting-started/change-black-out-dates-disabled-dates-in-winui-date-picker.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/blob/main/Samples/ViewAndItemCustomization)

## Disable dates dynamically (disable weekends)

If you want to block all weekend dates or any dates from the date selection, handle the [`DateFieldItemPrepared`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_DateFieldItemPrepared) event and use the [`DateTimeFieldItemPreparedEventArgs.ItemInfo.IsEnabled`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.DateTimeFieldItemPreparedEventArgs.html#Syncfusion_UI_Xaml_Editors_DateTimeFieldItemPreparedEventArgs_ItemInfo) property value as `true`.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2" %}

<editors:SfDatePicker x:Name="sfDatePicker" 
                      DateFieldItemPrepared = "SfDatePicker_DateFieldItemPrepared"/>

{% endhighlight  %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="1" %}

sfDatePicker.DateFieldItemPrepared += SfDatePicker_DateFieldItemPrepared;

{% endhighlight  %}
{% endtabs %}

You can handle the event as follows,

{% tabs %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="7" %}

private void SfDatePicker_DateFieldItemPrepared(object sender, DateTimeFieldItemPreparedEventArgs e)
{
    //Restrict the weekend days
    if (e.ItemInfo.DateTime.Value.DayOfWeek == DayOfWeek.Saturday ||
            e.ItemInfo.DateTime.Value.DayOfWeek == DayOfWeek.Sunday)
    {
        e.ItemInfo.IsEnabled = false;
    }
}

{% endhighlight  %}
{% endtabs %}

![change-black-out-dates-to-weekend-dates-in-winui-date-picker](Images/getting-started/change-black-out-dates-to-weekend-dates-in-winui-date-picker.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/blob/main/Samples/DateRestriction)

## Select date as you scroll spinner

If you want to hide the submit button and select the date directly from the dropdown date spinner without clicking the `Ok` button, use the [`ShowSubmitButtons`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_ShowSubmitButtons) property value as `false`. The default value of `ShowSubmitButtons` property is `true`.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="3" %}

<editors:SfDatePicker 
                      x:Name="sfDatePicker"
                      ShowSubmitButtons="False"/>

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.ShowSubmitButtons = false;

{% endhighlight %}
{% endtabs %}

![show-or-hide-submit-buttons-in-winui-date-picker](Images/getting-started/show-or-hide-submit-buttons-in-winui-date-picker.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/blob/main/Samples/ViewAndItemCustomization)

## Cancel a date that is being changed

The [`SelectedDateChanging`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_SelectedDateChanging) event will be triggered, as soon as a date is selected but before `SelectedDate` property is updated. If the change is considered invalid, it can be canceled. The `SelectedDateChanging` event contains the following properties.

* `OldDate` - Gets a date which is previously selected.
* `NewDate` - Gets a date which is currently selected.
* `Cancel` - Gets or sets whether to cancel the selected date value update.

Users are restricted to select a blackout date from dropdown, however user can give text input through editor. As selecting a blackout date leads to crash, we can cancel the change using `SelectedDateChanging` event.

N> `SelectedDateChanging` event is called before the `SelectedDateChanged` event when a date is selected.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="3" %}

<editor:SfDatePicker Height="35" 
                     Width="150" 
                     SelectedDateChanging="SfDatePicker_DateChanging" />

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.SelectedDateChanging += SfDatePicker_DateChanging;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows:

{% tabs %}
{% highlight C# tabtitle="MainWindow.xaml.cs" %}

 private void SfDatePicker_DateChanging(object sender, Syncfusion.UI.Xaml.Editors.DateChangingEventArgs e)
{
    var OldDate = e.OldDate;
    var NewDate = e.NewDate;

    //Cancel Selected date update
    e.Cancel = true;
}

{% endhighlight %}
{% endtabs %}