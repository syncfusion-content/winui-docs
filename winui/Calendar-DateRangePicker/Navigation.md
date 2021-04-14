---
layout: post
title: View navigation in WinUI Calendar DateRangePicker control|Syncfusion
description: This section describes how to navigate between views the Calendar DateRangePicker (SfCalendarDateRangePicker) control.
platform: WinUI
control: SfCalendarDateRangePicker
documentation: ug
---

# View navigation in dropdown calendar of Calendar DateRangePicker

## Navigate between views

You can easily navigate to the month, year, decade, or century views to select different date ranges in the dropdown calendar by repeatedly clicking the header button. Initially, month view is loaded in dropdown calendar.

![Navigation between views in WinUI Calendar DateRangePicker](Navigate-Between-Views_images/View-navigation.gif)

## Restrict navigation between views

You can restrict navigation within a minimum and maximum views by using [`MinDisplayMode`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_MinDisplayMode) and [`MaxDisplayMode`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_MaxDisplayMode) properties. This will be useful when your date range is smaller and you don’t want to show century, decade and year view.

By default, the value of `MinDisplayMode` property is `Month` and `MaxDisplayMode` property is `Century`.

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

![Navigation between month and century view in WinUI Calendar DateRangePicker](Getting-Started_images/Restrict_View_Navigation.gif)

## Selection based on view restriction

You can restrict users to select date range within specific views (example : choosing manufactured and expiry date of product) in `Calendar DateRangePicker` control using the `MinDisplayMode` and `MaxDisplayMode` properties.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar x:Name="sfCalendar" FormatString="{}{0:MM/yyyy} - {1:MM/yyyy}"
                             MinDisplayMode="Year"
                             MaxDisplayMode="Decade"
                             />

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.MinDisplayMode = CalendarDisplayMode.Year;
sfCalendar.MaxDisplayMode = CalendarDisplayMode.Decade;

{% endhighlight %}
{% endtabs %}

![Selection within restriction in WinUI Calendar DateRangePicker](Navigate-Between-Views_images/product-manufacture-expiry-date.gif)
