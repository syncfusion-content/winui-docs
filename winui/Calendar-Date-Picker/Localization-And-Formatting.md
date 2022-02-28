---
layout: post
title: Localization and Formatting in WinUI Calendar Date Picker | Syncfusion
description: Learn here all about how to localize and customize the format of Syncfusion WinUI Calendar Date Picker (SfCalendarDatePicker) control and more.
platform: WinUI
control: SfCalendarDatePicker
documentation: ug
---

# Localization and Formatting in WinUI Calendar Date Picker

This section describes how to change the display formats and to localize [Calendar Date Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html) control using the [`CalendarIdentifier`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_CalendarIdentifier) and `Language` properties.

## Types of calendar

The `Calendar Date Picker` control supports different type of calendars such as Gregorian, Julian, Hebrew, etc. You can change the calendar type by using the [CalendarIdentifier](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_CalendarIdentifier) property. The default value of `CalendarIdentifier` property is **GregorianCalendar**.

You can select the required `CalendarIdentifier` value from the following types:

 * JulianCalendar
 * GregorianCalendar
 * HebrewCalendar
 * HijriCalendar
 * KoreanCalendar
 * TaiwanCalendar
 * ThaiCalendar
 * UmAlQuraCalendar
 * PersianCalendar

N> Japanese and Lunar type calendars are not supported in `Calendar Date Picker` control.

N> When both the `CalendarIdentifier` and `FlowDirection` properties are set, the `FlowDirection` property is given higher precedence.

N> The `Calendar Date Picker` control updates the flow direction visually based on the `CalendarIdentifier` property value.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDatePicker CalendarIdentifier="HebrewCalendar"
                               x:Name="sfCalendarDatePicker"/>

{% endhighlight %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.CalendarIdentifier = "HebrewCalendar";

{% endhighlight %}
{% endtabs %}

N> The value in `Calendar Date Picker` control textbox is updated based on `CalendarIdentifier` property calendar type.

![WinUI CalendarDatePicker displays Hebrew Calendar](Getting-Started_images/winui-calendar-datepicker-with-herbew-type.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Formatting).

## Change the language

If you want to localize the drop-down calendar, use the `Language` property. The default value of `Language` property is **en-US**.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDatePicker Language="ar-AR"
                               x:Name="sfCalendarDatePicker"/>

{% endhighlight %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.Language = "ar-AR";

{% endhighlight %}
{% endtabs %}

![WinUI CalendarDatePicker with Localization](Getting-Started_images/winui-calendar-datepicker-localization.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Formatting).


## Change editor display format

 You can edit and display the selected date with various formatting like date, month, and year formats by using the [DisplayDateFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_DisplayDateFormat) property. The default value of `DisplayDateFormat` property is **d**.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDatePicker x:Name="sfCalendarDatePicker" 
                               DisplayDateFormat="M"/>

{% endhighlight  %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.DisplayDateFormat= "M";

{% endhighlight  %}
{% endtabs %}

![WinUI CalendarDatePicker with Month Format](Getting-Started_images/winui-calendar-datepicker-month-format.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Formatting)

## Change calendar display format

You can use different date formats such as an abbreviated or full names for a day, month, week names, or header name of month and year in drop-down calendar by using the [DayFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_DayFormat), [MonthFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_MonthFormat), [DayOfWeekFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_DayOfWeekFormat), and [HeaderFormatInMonthView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_HeaderFormatInMonthView) properties.

N> Refer to this [DateTimeFormatter](https://docs.microsoft.com/en-us/uwp/api/windows.globalization.datetimeformatting.datetimeformatter?view=winrt-19041) page to get more date formatting.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDatePicker DayFormat="{}{day.integer(2)}"
                               MonthFormat="{}{month.full}"
                               DayOfWeekFormat="{}{dayofweek.abbreviated(3)}"
                               HeaderFormatInMonthView="{}{month.abbreviated} {year.abbreviated}‎"
                               x:Name="sfCalendarDatePicker"/>

{% endhighlight %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.DayFormat = "{day.integer(2)}";
sfCalendarDatePicker.MonthFormat = "{month.full}";
sfCalendarDatePicker.DayOfWeekFormat = "{dayofweek.abbreviated(3)}";
sfCalendarDatePicker.HeaderFormatInMonthView = "{month.abbreviated} {year.abbreviated}‎";

{% endhighlight %}
{% endtabs %}

![Changing Calendar display Format in WinUI CalendarDatePicker](Getting-Started_images/winui-calendar-datepicker-format.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Formatting).

## First day of week

You can change the first day of week in drop-down calendar using the [FirstDayOfWeek](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_FirstDayOfWeek) property value. The default value of `FirstDayOfWeek` property is **Sunday**.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDatePicker x:Name="sfCalendarDatePicker" 
                               FirstDayOfWeek="Monday"/>

{% endhighlight %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.FirstDayOfWeek = DayOfWeek.Monday;

{% endhighlight %}
{% endtabs %}

![Changing Week Day in WinUI CalendarDatePicker](Getting-Started_images/winui-calendar-datepicker-week-day.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Selection).

## Number of weeks in a view

If you want to increase or decrease the number of weeks shown in a month view in drop-down calendar, use the [NumberOfWeeksInView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_NumberOfWeeksInView) property. The default value of `NumberOfWeeksInView` property is `6`.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDatePicker NumberOfWeeksInView="4"
                               x:Name="sfCalendarDatePicker"/>

{% endhighlight %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.NumberOfWeeksInView = 4;

{% endhighlight %}
{% endtabs %}

![WinUI CalendarDatePicker displays Specific Weeks](Getting-Started_images/winui-calendar-datepicker-weeks.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Selection).
