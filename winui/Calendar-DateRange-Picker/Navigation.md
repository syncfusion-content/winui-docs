---
layout: post
title: View Navigation in WinUI Calendar DateRange Picker control |Syncfusion
description: Learn here all about how to navigate between views the Calendar DateRange Picker (SfCalendarDateRangePicker) control.
platform: WinUI
control: SfCalendarDateRangePicker
documentation: ug
---

# View navigation in WinUI Calendar DateRange Picker

## Navigate between views

You can easily navigate to the month, year, decade, or century views to select different date ranges in the drop-down calendar by clicking the header button. Initially, month view is loaded in the drop-down calendar.

![Navigation between views in WinUI Calendar DateRange Picker](Navigate-Between-Views_images/winui-calendar-daterange-picker-views-navigation.gif)

## Restrict navigation between views

You can restrict navigation within a minimum and maximum views by using the [`MinDisplayMode`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_MinDisplayMode) and [`MaxDisplayMode`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_MaxDisplayMode) properties. This will be useful when your date range is smaller and you do not want to show decade and century views.

By default, the value of `MinDisplayMode` property is **Month** and `MaxDisplayMode` property is **Century**.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDateRangePicker x:Name="sfCalendarDateRangePicker"
                               MinDisplayMode="Month"
                               MaxDisplayMode="Year"
                               />

{% endhighlight %}
{% highlight C# %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.MinDisplayMode = CalendarDisplayMode.Month;
sfCalendarDateRangePicker.MaxDisplayMode = CalendarDisplayMode.Year;

{% endhighlight %}
{% endtabs %}

N> When the `MinDisplayMode` property value is **Year** and the `MinDate` value is **15/01/2021**, selecting the month of minimum date will set the starting date value from the minimum date, i.e. from *January 15, 2021*.

![WinUI Calendar DateRange Picker Restrict View Navigation](Getting-Started_images/winui-calendar-daterange-picker-restrict-view-navigation.gif)

N> Download demo from [Github](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-daterange-picker-examples/tree/main/Samples/Restriction).

## Selection based on view restriction

You can restrict users from selecting date ranges within specific views (example: choosing manufactured and expiry date of product) in `Calendar DateRange Picker` control using the `MinDisplayMode` and `MaxDisplayMode` properties.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDateRangePicker x:Name="sfCalendarDateRangePicker"
                                    FormatString="{}{0:MM/yyyy} - {1:MM/yyyy}"
                                    MinDisplayMode="Year"
                                    MaxDisplayMode="Decade"
                               />

{% endhighlight %}
{% highlight C# %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.MinDisplayMode = CalendarDisplayMode.Year;
sfCalendarDateRangePicker.MaxDisplayMode = CalendarDisplayMode.Decade;
sfCalendarDateRangePicker.FormatString = "{0:MM/yyyy}-{1:MM/yyyy}";

{% endhighlight %}
{% endtabs %}

![WinUI Calendar DateRange Picker Selection based on View Restriction](Navigate-Between-Views_images/winui-calendar-daterange-picker-selection-based-on-view-restriction.gif)

N> Download demo from [Github](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-daterange-picker-examples/tree/main/Samples/Restriction).

## Navigation by keyboard

You can navigate between elements in the drop-down calendar of `Calendar DateRange Picker` control by keyboard keys or by mouse interaction. The following are the list of keyboard keys to navigate and select.

* **Tab** or **Shift+Tab** - To navigate between date cell and elements in the header.
* **UpArrow**,**DownArrow**,**LeftArrow**, and **RightArrow** - To navigate between calendar date, month, or decade cells.
* **Space** or **Enter** - To select a cell.
* **Ctrl + UpArrow** and **ctrl + DownArrow** - To navigate between views (Example: Navigate from month to year view).
* **PageUp** and **PageDown** - To navigate within views (Example: Navigate between months).
* **Home** or **End** - To navigate to the first or last cell of the current view.
* **Alt + DownArrow** - To open the drop-down calendar.