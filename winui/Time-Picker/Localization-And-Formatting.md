---
layout: post
title: Localization and Formatting in WinUI Time Picker control | Syncfusion
description: This section describes how to localize and formats the Time Picker (SfTimePicker) control into WinUI application.
platform: WinUI
control: SfTimePicker
documentation: ug
---

# Localization and Formatting in WinUI Time Picker

This section describes how to localize and format the WinUI [Time Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html) control using [`CalendarIdentifier`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_CalendarIdentifier) and `Language` properties and to change the display formats.

## Change the type of clock

The `Time Picker` control supports 12 hours and 24 hours formats. You can change the time format by using `ClockIdentifier` property. The default value of `ClockIdentifier` property is `12HourClock`.

You can select the required `ClockIdentifier` value from below formats.

* 12HourClock
* 24HourClock 

{% tabs %}
{% highlight xaml %}

<editors:SfTimePicker ClockIdentifier="24HourClock"
                      x:Name="sfTimePicker"/>

{% endhighlight %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.CalendarIdentifier = "24HourClock";

{% endhighlight %}
{% endtabs %}

![Time Picker calendar type changed to Hebrew](Dropdown-Time-Spinner_images/ClockIdentifier.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/tree/main/Samples/Localization)

## Change flow direction

You can change the flow direction of the `Time Picker` layout from right to left by setting the `FlowDirection` property value as `RightToLeft`. The default value of `FlowDirection` property is `LeftToRight`.

{% tabs %}
{% highlight XAML %}

<editors:SfTimePicker FlowDirection="RightToLeft" 
                      x:Name="sfTimePicker"/>

{% endhighlight %}
{% highlight c# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.FlowDirection = FlowDirection.RightToLeft;

{% endhighlight %}
{% endtabs %}

![Time Picker flow direction changed to right to left](Dropdown-Time-Spinner_images/FlowDirection.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/ViewAndItemCustomization)

## Change the language

You can localize the `Time Picker` using the `Language` property. The default value of `Language` property is **en-US**.

{% tabs %}
{% highlight xaml %}

<editors:SfTimePicker Language="ar-SA"
                      x:Name="sfTimePicker"/>

{% endhighlight %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.Language = "ar";

{% endhighlight %}
{% endtabs %}

![Displaying arabic cultured WinUI Time Picker.](Dropdown-Time-Spinner_images/Language.png)

N> `Time Picker` control updates the flow direction visually based on the `Language` property value.

N> When `Language` and `FlowDirection` properties are set, `FlowDirection` property have higher precedence.

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/tree/main/Samples/Localization)

## Change time display format

 You can edit and display the selected time with various formatting like hour, minutes, seconds and meridiem formats by using the [`FormatString`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_FormatString) property. The default value of `FormatString` property is `hh:mm tt`.

{% tabs %}
{% highlight xaml %}

<editors:SfTimePicker x:Name="sfTimePicker" 
                      FormatString="HH:mm"/>

{% endhighlight %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.FormatString= "HH:mm";

{% endhighlight %}
{% endtabs %}

![Time Picker selected time with hour and meridiem](Getting-Started_images/FormatString.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/TimeRestriction)

## Edit time using mask mode

By default ‘Mask’ editing is enabled, which ensure that it contains only valid value. As soon as in input is given, the value is validated and correction is done immediately. Once input is completed for a field, cursor moves to next field automatically.

Based on the `FormatString` and your input values, hour and minute field values are automatically corrected. 

For example,

|    Default Masking   |    Input     |     Output      |
|:---------------------|:-------------|:---------------:|
| If you try to enter values between `13-19` into the `12HourClock` hour field, it will add last input digit(3-9) in the hour field and move the cursor to the next field. | 15 (in hour field)   | <img src="Getting-Started_images/Hour_Mask_editing.png" alt="Time Picker valid and corrects the hour field based on the input using mask editing"/> |
| If you try to enter input in hour field that is greater than `19`, it will add first digit in hour field and last digit added into next field. | 48 (in hour field)   | <img src="Getting-Started_images/Hour_Mask_editing_1.png" alt="Time Picker valid and corrects the hour field based on the input using mask editing"/> | 
| If you try to enter input in minute field that is greater than `59`, it will add first digit in minute field and move the cursor to the next field. |87 (in minute field) | <img src="Getting-Started_images/Minute_Mask_editing.png" alt="Time Picker valid and corrects the minute field based on the input using mask editing."/> | 

{% tabs %}
{% highlight xaml %}

<editors:SfTimePicker EditMode="Mask"
                      x:Name="sfTimePicker" />

{% endhighlight  %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.EditMode = DateTimeEditingMode.Mask;

{% endhighlight  %}
{% endtabs %}

![Time Picker enables mask editing mode to select time](Getting-Started_images/Mask_Editingmode.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/TimeRestriction)

## Edit time using free form editing

If you want to perform the validation after the user completely entering their time inputs, use the [EditMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_EditMode) property value as `Normal`. Then the entered time value is validated with the `FormatString` property value by pressing the `Enter` key or lost focus. If entered value is not suit with `FormatString` property, the previously selected time value sets to `SelectedTime` property.

{% tabs %}
{% highlight xaml %}

<editors:SfTimePicker EditMode="Normal"
                      x:Name="sfTimePicker" />

{% endhighlight  %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.EditMode = DateTimeEditingMode.Normal;

{% endhighlight  %}
{% endtabs %}

![Time Picker enables free form editing to select time](Getting-Started_images/editmode_Normal.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/TimeRestriction)
