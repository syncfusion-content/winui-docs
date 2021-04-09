---
layout: post
title: Change date format in WinUI CalendarDateRangePicker control|Syncfusion
description: This section describes about how to add the CalendarDateRangePicker (SfCalendarDateRangePicker) control into WinUI application and its basic features.
platform: WinUI
control: SfCalendarDateRangePicker
documentation: ug
---

# Customize editor and dropdown date format in Calendar DateRangePicker 

## Change date display format

You can modify and display the selected date range with various formatting like date, month and year formats by using the `FormatString` property. The default value of `FormatString` property is `{0:d}-{1:d}`.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDateRangePicker x:Name="sfCalendarDateRangePicker" >
    <calendar:SfCalendarDateRangePicker.FormatString>
        <x:String>{0:D} - {1:D}</x:String>
    </calendar:SfCalendarDateRangePicker.FormatString>
</calendar:SfCalendarDateRangePicker>

{% endhighlight  %}
{% highlight C# %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.FormatString= "{0:D}-{1:D}";

{% endhighlight  %}
{% endtabs %}

![Calendar DateRangePicker selected date with month format](Getting-Started_images/FormatString.png)

## Change date format for drop down calendar

You can use different date formats such as abbreviated or full name for a day, month, week names or header name of month and year in drop-down calendar by using the `DateFormat`, `MonthFormat`, `DayOfWeekFormat` and `MonthHeaderFormat` properties.

N> Refer [DateTimeFormatter](https://docs.microsoft.com/en-us/uwp/api/windows.globalization.datetimeformatting.datetimeformatter?view=winrt-19041) page to get more date formats.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDateRangePicker DateFormat="{}{day.integer(2)}"
                                    MonthFormat="{}{month.full}"
                                    DayOfWeekFormat="{}{dayofweek.abbreviated(3)}"
                                    MonthHeaderFormat="{}{month.abbreviated} {year.abbreviated}‎"
                                    x:Name="sfCalendarDateRangePicker"/>

{% endhighlight %}
{% highlight C# %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.DateFormat = "{day.integer(2)}";
sfCalendarDateRangePicker.MonthFormat = "{month.full}";
sfCalendarDateRangePicker.DayOfWeekFormat = "{dayofweek.abbreviated(3)}";
sfCalendarDateRangePicker.MonthHeaderFormat = "{month.abbreviated} {year.abbreviated}‎";

{% endhighlight %}
{% endtabs %}

![Displaying full month and abbreviated year format in WinUI Calendar DateRangePicker.](Getting-Started_images/dateformat.gif)