---
layout: post
title: Localize calendar in WinUI CalendarDateRangePicker control|Syncfusion
description: This section describes how to apply localization to dropdown calendar in Calendar DateRangePicker (SfCalendarDateRangePicker) control.
platform: WinUI
control: SfCalendarDateRangePicker
documentation: ug
---

# Localize dropdown calendar in WinUI Calendar DateRangePicker

The `Calendar DateRangePicker` control supports different type of calendars such as Gregorian, Julian, Hebrew, etc. You can change the calendar type by using `CalendarIdentifier` property. The default value of `CalendarIdentifier` property is `GregorianCalendar`.

You can select the required `CalendarIdentifier` value from below types.
 * JulianCalendar
 * GregorianCalendar
 * HebrewCalendar
 * HijriCalendar
 * KoreanCalendar
 * TaiwanCalendar
 * ThaiCalendar
 * UmAlQuraCalendar
 * PersianCalendar

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDateRangePicker CalendarIdentifier="HebrewCalendar"
                               x:Name="sfCalendarDateRangePicker"/>

{% endhighlight %}
{% highlight C# %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.CalendarIdentifier = "HebrewCalendar";

{% endhighlight %}
{% endtabs %}

![Displaying Hebrew-type WinUI Calendar DateRangePicker.](Getting-Started_images/Hebrew-calendarIdentifier.png)

## Culture support

If you want to localize the drop-down calendar, use the `Language` property. The default value of `Language` property is `en-US`.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDateRangePicker Language="ar-AR"
                               x:Name="sfCalendarDateRangePicker"/>

{% endhighlight %}
{% highlight C# %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.Language = "ar-AR";

{% endhighlight %}
{% endtabs %}

![Displaying arabic cultured WinUI Calendar DateRangePicker.](Getting-Started_images/LanguageView.png)