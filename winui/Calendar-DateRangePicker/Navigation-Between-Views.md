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

## Restrict view navigation

You can restrict navigation within a minimum and maximum views by using `MinDisplayMode` and `MaxDisplayMode` properties. This will be useful when your date range is smaller and you don’t want to show century, decade and year view.

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

