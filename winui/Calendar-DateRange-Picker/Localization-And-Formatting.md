---
layout: post
title: Localization and Formatting in Calendar DateRange Picker | Syncfusion
description: This section describes how to localize and change the formats in drop-down calendar of Calendar DateRange Picker (SfCalendarDateRangePicker) control.
platform: WinUI
control: SfCalendarDateRangePicker
documentation: ug
---

# Localization and Formatting in WinUI Calendar DateRange Picker

## Types of Calendar

The `Calendar DateRange Picker` control supports different type of calendars such as Gregorian, Julian, Hebrew, etc. You can change the calendar type by using the [`CalendarIdentifier`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_CalendarIdentifier) property. The default value of `CalendarIdentifier` property is **GregorianCalendar**.

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

N> Japanese and Lunar type calendars are not supported in `Calendar` control.

N> When both the `CalendarIdentifier` and the `FlowDirection` properties are set, `FlowDirection` property is given higher precedence.

N> The `Calendar DateRange Picker` control visually updates the flow direction based on the `CalendarIdentifier` property value.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2" %}

<calendar:SfCalendarDateRangePicker x:Name="sfCalendarDateRangePicker"
                                    CalendarIdentifier="HebrewCalendar"/>

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.CalendarIdentifier = "HebrewCalendar";

{% endhighlight %}
{% endtabs %}

![calendar-types-hebrew-calendar-in-winui-calendar-date-range-picker](Images/getting-started/calendar-types-hebrew-calendar-in-winui-calendar-date-range-picker.png)

N> Download demo from [Github](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-daterange-picker-examples/tree/main/Samples/Formatting).

## Change the language

If you want to localize the drop-down calendar, use the `Language` property. The default value of `Language` property is **en-US**.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="3" %}

<calendar:SfCalendarDateRangePicker 
                               x:Name="sfCalendarDateRangePicker"
                               Language="ar-AR"/>

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.Language = "ar-AR";

{% endhighlight %}
{% endtabs %}

![calendar-types-arabic-calendar-in-winui-calendar-date-range-picker](Images/getting-started/calendar-types-arabic-calendar-in-winui-calendar-date-range-picker.png)

N> Download demo from [Github](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-daterange-picker-examples/tree/main/Samples/Formatting).

## Change editor display format

You can modify and display the selected date range with various formatting like date, month, and year formats by using the [`DisplayDateFormat`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_DisplayDateFormat) property. The default value of `DisplayDateFormat` property is **{0:d}-{1:d}**.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2" %}

<calendar:SfCalendarDateRangePicker x:Name="sfCalendarDateRangePicker" 
                                    DisplayDateFormat="{}{0:D} - {1:D}" />
   
{% endhighlight  %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.DisplayDateFormat= "{0:D}-{1:D}";

{% endhighlight  %}
{% endtabs %}

![change-display-date-format-in-winui-calendar-date-range-picker](Images/getting-started/change-display-date-format-in-winui-calendar-date-range-picker.png)

N> Download demo from [Github](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-daterange-picker-examples/tree/main/Samples/Formatting).

## Change calendar display format

You can use different date formats such as abbreviated or full name for a day, month, week names or header name of month and year in drop-down calendar by using the [`DayFormat`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_DayFormat), [`MonthFormat`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_MonthFormat), [`DayOfWeekFormat`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_DayOfWeekFormat), and [`MonthHeaderFormat`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_MonthHeaderFormat) properties.

N> Refer to this [DateTimeFormatter](https://docs.microsoft.com/en-us/uwp/api/windows.globalization.datetimeformatting.datetimeformatter?view=winrt-19041) page to get more date formats.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2 3 4 5" %}

<calendar:SfCalendarDateRangePicker x:Name="sfCalendarDateRangePicker" 
                                    DayFormat="{}{day.integer(2)}"
                                    MonthFormat="{}{month.full}"
                                    DayOfWeekFormat="{}{dayofweek.abbreviated(3)}"
                                    MonthHeaderFormat="{}{month.abbreviated} {year.abbreviated}‎"
                                    />

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2 3 4 5" %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.DayFormat = "{day.integer(2)}";
sfCalendarDateRangePicker.MonthFormat = "{month.full}";
sfCalendarDateRangePicker.DayOfWeekFormat = "{dayofweek.abbreviated(3)}";
sfCalendarDateRangePicker.MonthHeaderFormat = "{month.abbreviated} {year.abbreviated}‎";

{% endhighlight %}
{% endtabs %}

![change-display-date-formatting-in-winui-calendar-date-range-picker](Images/getting-started/change-display-date-formatting-in-winui-calendar-date-range-picker.gif)

N> Download demo from [Github](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-daterange-picker-examples/tree/main/Samples/Formatting).

## First day of week

By default, **Sunday** is shown as the first day of the week in the `Calendar DateRange Picker` controls' drop-down calendar. You can change the first day of week by changing the [`FirstDayOfWeek`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_FirstDayOfWeek) property value. 

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2" %}

<calendar:SfCalendarDateRangePicker x:Name="sfCalendarDateRangePicker" 
                                    FirstDayOfWeek="Monday"/>

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.FirstDayOfWeek = FirstDayOfWeek.Monday;

{% endhighlight %}
{% endtabs %}

![change-first-day-of-week-in-winui-calendar-date-range-picker](Images/drop-down-calendar/change-first-day-of-week-in-winui-calendar-date-range-picker.png)

## Change flow direction

By default, flow direction is changed automatically based on selected `CalendarIdentifier` value in `Calendar DateRange Picker` control. However, you can override it by explicitly specifying the `FlowDirection` property value. The default value of `FlowDirection` property is **LeftToRight**.

N> When `CalendarIdentifier` and `FlowDirection` properties are set, `FlowDirection` property is given higher precedence.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="3" %}

<calendar:SfCalendarDateRangePicker 
                               x:Name="sfCalendarDateRangePicker"
                               FlowDirection="RightToLeft" />

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.FlowDirection = FlowDirection.RightToLeft;

{% endhighlight %}
{% endtabs %}

![change-flow-direction-in-winui-calendar-date-range-picker](Images/drop-down-calendar/change-flow-direction-in-winui-calendar-date-range-picker.png)

N> Download demo from [Github](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-daterange-picker-examples/tree/main/Samples/Formatting).
