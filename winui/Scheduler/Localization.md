---
layout: post
title: Localization in WinUI Scheduler control | Syncfusion
description: Learn here all about how to set calender types and language to localize the scheduler (SfScheduler) control, its elements, and more.
platform: winui
control: SfScheduler
documentation: ug
---

# Calendar Types in WinUI Scheduler (SfScheduler)
This section describes how to localize the scheduler control by using `Language` and `CalendarIdentifier` properties in `SfScheduler.`

## Types of Calendar
The Scheduler control supports different types of calendars such as Gregorian, Korean, Hebrew, and more. You can change the calendar types by using the `CalendarIdentifier` property in Scheduler. The default value of the `CalendarIdentifier` property is `GregorianCalendar.`

<table>
<tr>
<th>Supported Calendars</th>
<th>UnSupported Calendars</th>
</tr>
<tr>
<td>

* GregorianCalendar
* HebrewCalendar
* HijriCalendar
* KoreanCalendar
* TaiwanCalendar
* ThaiCalendar
* UmAlQuraCalendar
* PersianCalendar
* JulianCalendar</td>
<td>

* JapaneseCalendar
* Lunar type calendars
</td>
</tr>
</table>

N> 
* When the `CalendarIdentifier` and `FlowDirection` properties are set, the `FlowDirection` property is given higher precedence. If you want to override this behavior set the `FlowDirection` after `CalendarIdentifier.`
* The scheduler uses the `CalendarIdentifier` property to determine which calendar to use to localize and format the header date, view header day, and date, time ruler, and DatePicker, and TimePicker in the appointment editor.
* By default, the scheduler uses the `GregorianCalendar` for the app’s preferred language.
* If the scheduler is localized with the `CalendarIdentifier,` it will display in the app’s preferred language. For example, if you specify a `KoreanCalendar` and the app language is "en-us," the scheduler will display in English because there are translations applied for the Korean calendar.

{% tabs %}
{% highlight xaml %}
<scheduler:SfScheduler x:Name="Schedule"
                       CalendarIdentifier="HijriCalendar" />
{% endhighlight %}
{% highlight c# %}
this.Schedule.CalendarIdentifier = "HijriCalendar";
{% endhighlight %}
{% endtabs %}

![Hijri Calendar](Localization_Images/CalendarTypes.png)

### DateTime values in Calendar Types
You can give all the DateTime values such as `DisplayDate,` `SelectedDate,` `BlackoutDates,` Appointment `StartTime,` and `EndTime,` `SpecialTimeRegion` Start and End time values in two ways when the calendar identifier is specified other than `GregorianCalendar.`

* A `DateTime` instance without specifying calendar type. A scheduler will handle the `DateTime` value for the specified calendar type.

* A `DateTime` instance with specified calendar type. If calendar type is mentioned then the date should be respective to that calendar so that the date value will be converted to Gregorian DateTime and the scheduler will handle that DateTime.

## Change the language
You can localize the scheduler using the `Language` property. The default value of Language property is `en-US`.

{% tabs %}
{% highlight xaml %}
<scheduler:SfScheduler x:Name="Schedule"
                       Language="fr-FR" />
{% endhighlight %}
{% highlight c# %}
this.Schedule..Language = "fr-FR";
{% endhighlight %}
{% endtabs %}

![Hijri Calendar](Localization_Images/Language.png)