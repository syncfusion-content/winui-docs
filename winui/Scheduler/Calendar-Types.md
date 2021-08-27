---
layout: post
title: Calendar Types in WinUI Scheduler control | Syncfusion
description: Learn here all about how to change the calendar types in the scheduler (SfScheduler) control, its elements, and more.
platform: winui
control: SfScheduler
documentation: ug
---

# Calendar Types in WinUI Scheduler (SfScheduler)
This section describes how to change the calendar types of scheduler control using the `CalendarIdentifier.`

## Types of Calendar
The Scheduler control supports different types of calendars such as Gregorian, Korean, Hebrew, and more. You can change the calendar types by using the `CalendarIdentifier` property in Scheduler. The default value of the `CalendarIdentifier` property is `GregorianCalendar.`

You can select the required `CalendarIdentifier` value from the following types.

* GregorianCalendar
* HebrewCalendar
* HijriCalendar
* KoreanCalendar
* TaiwanCalendar
* ThaiCalendar
* UmAlQuraCalendar
* PersianCalendar
* JulianCalendar

N> 
* Japanese and Lunar type calendars are not supported in the `Scheduler` control.
* When the `CalendarIdentifier` and `FlowDirection` properties are set, the `FlowDirection` property is given higher precedence. If you want to override this behavior set the `FlowDirection` after `CalendarIdentifier.`

{% tabs %}
{% highlight xaml %}
<scheduler:SfScheduler x:Name="Schedule"
                       CalendarIdentifier="HebrewCalendar" />
{% endhighlight %}
{% highlight c# %}
this.Schedule.CalendarIdentifier = "HebrewCalendar";
{% endhighlight %}
{% endtabs %}

![Hebrew Calendar](Calendar-Types_Images/CalendarTypes.png)

## DateTime Formats and Language in Calendar Types
The scheduler uses the `CalendarIdentifier` to determine which calendar to use to  localize and format the string content of header DatePicker, view header day and date, time ruler and DatePicker and TimePicker in appointment editor.

N> 
* By default scheduler uses the `GregorianCalendar` for the app’s preferred language.
* If the scheduler is localized with `CalendarIdentifier`, it will display in the app’s preferred language. For example, if you specify a `KoreanCalendar` and the app language is "en-us", the DatePicker will display in English because there are translations for the Korean calendar.

## DateTime values in Calendar Types
You can give all the DateTime values such as `DisplayDate,` `SelectedDate,` `BlackoutDates,` Appointment `StartTime,` and `EndTime,` `SpecialTimeRegion` Start and End time values in two ways when the calendar identifier is specified other than `GregorianCalendar.`

* A `DateTime` instance without specifying calendar type. A scheduler will handle the `DateTime` value for the specified calendar type.

* A `DateTime` instance with specified calendar type. If calendar type is mentioned then the date should be respective to that calendar so that the date value will be converted to Gregorian DateTime and the scheduler will handle that DateTime.