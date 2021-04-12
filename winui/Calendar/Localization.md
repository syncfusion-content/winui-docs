---
layout: post
title: Localize the WinUI Calendar control | Syncfusion
description: This section describes about how to localize the Calendar (SfCalendar) control.
platform: WinUI
control: SfCalendar
documentation: ug
---

# Localize the WinUI Calendar

This section describes how to localize [Calendar](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html) control using `CalendarIdentifier` and `Language` properties.

## Calendar types

The `Calendar` control supports different type of calendars, such as Gregorian, Julian, Hebrew, etc. You can change the calendar type by using [CalendarIdentifier](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_CalendarIdentifier) property. The default value of `CalendarIdentifier` property is `GregorianCalendar`.

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

<calendar:SfCalendar CalendarIdentifier="HebrewCalendar"
                     x:Name="sfCalendar"/>

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.CalendarIdentifier = "HebrewCalendar";

{% endhighlight %}
{% endtabs %}

![Displaying Hebrew-type WinUI Calendar.](Getting-Started_images/CalendarIdentifier.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-examples/blob/main/Samples/Formatting)

## Culture support

You can localize the calendar using the `Language` property. The default value of `Language` property is `en-US`.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar Language="fr-FR"
                     x:Name="sfCalendar"/>

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.Language = "fr";

{% endhighlight %}
{% endtabs %}

![Displaying french cultured WinUI Calendar.](Getting-Started_images/Language.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-examples/blob/main/Samples/Formatting)
