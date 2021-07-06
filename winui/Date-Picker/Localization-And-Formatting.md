---
layout: post
title: Localization and Formatting in WinUI Date Picker control | Syncfusion
description: This section describes how to localize and formats the Date Picker (SfDatePicker) control into WinUI application.
platform: WinUI
control: SfDatePicker
documentation: ug
---

# Localization and Formatting in WinUI Date Picker

This section describes how to localize and format the WinUI [Date Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html) control using [`CalendarIdentifier`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_CalendarIdentifier) and `Language` properties and to change the display formats.

## Change the type of calendar

The `Date Picker` control supports different type of calendar such as Gregorian, Julian, Hebrew, etc. You can change the calendar type by using `CalendarIdentifier` property. The default value of `CalendarIdentifier` property is `GregorianCalendar`.

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

<editors:SfDatePicker CalendarIdentifier="HebrewCalendar"
                      x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.CalendarIdentifier = "HebrewCalendar";

{% endhighlight %}
{% endtabs %}

![WinUI DatePicker displays Hebrew Calendar](Dropdown-Date-Spinner_images/winui-datepicker-hebrew-calendar.png)

N> `Date Picker` control updates the flow direction visually based on the `CalendarIdentifier` property value.

N> When `CalendarIdentifier` and `FlowDirection` properties are set, `FlowDirection` property have higher precedence.

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/tree/main/Samples/Localization)

## Change flow direction

You can change the flow direction of the `Date Picker` layout from right to left by setting the `FlowDirection` property value as `RightToLeft`. The default value of `FlowDirection` property is `LeftToRight`.

{% tabs %}
{% highlight XAML %}

<editors:SfDatePicker FlowDirection="RightToLeft" 
                      x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.FlowDirection = FlowDirection.RightToLeft;

{% endhighlight %}
{% endtabs %}

![Changing Flow Direction of WinUI DatePicker](Dropdown-Date-Spinner_images/winui-datepicker-flowdirection.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/blob/main/Samples/ViewAndItemCustomization)

## Change the language

You can localize the `Date Picker` using the `Language` property. The default value of `Language` property is **en-US**.

{% tabs %}
{% highlight xaml %}

<editors:SfDatePicker Language="ar-SA"
                      x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.Language = "ar";

{% endhighlight %}
{% endtabs %}

![WinUI DatePicker with Localization](Dropdown-Date-Spinner_images/winui-datepicker-localization.png)

N> `Date Picker` control updates the flow direction visually based on the `Language` property value.

N> When `Language` and `FlowDirection` properties are set, `FlowDirection` property have higher precedence.

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/tree/main/Samples/Localization)

## Change editor display format

 You can edit and display the selected date with various formatting like date, month and year formats by using the [`FormatString`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_FormatString) property. The default value of `FormatString` property is `d`.

{% tabs %}
{% highlight xaml %}

<editors:SfDatePicker x:Name="sfDatePicker" 
                      FormatString="M"/>

{% endhighlight  %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.FormatString= "M";

{% endhighlight  %}
{% endtabs %}

![Changing Month Format in WinUI DatePicker](Getting-Started_images/winui-datepicker-month-format.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/blob/main/Samples/DateRestriction)

## Change date format for Spinner

You can allow the user to select the pair of date, month and year spinner or any single spinner cell from the dropdown date spinner by using the [`DropDownFormatString`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_DropDownFormatString) property. The default value of `DropDownFormatString` property is `d`.

{% tabs %}
{% highlight xaml %}

<editors:SfDatePicker x:Name="sfDatePicker" 
                      DropDownFormatString="dd/MM"/>

{% endhighlight  %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.DropDownFormatString = "dd/MM";

{% endhighlight  %}
{% endtabs %}

![WinUI DatePicker displays Date and Month Spinner](Getting-Started_images/winui-datepicker-spinner.png)

Here, you can only able to select the date and month value from the dropdown spinner.

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/blob/main/Samples/DateRestriction)

## Edit date using mask mode

By default ‘Mask’ editing is enabled, which ensure that it contains only valid value. As soon as in input is given, the value is validated and correction is done immediately. Once input is completed for a field, cursor moves to next field automatically.

Based on the `FormatString` and your input values, date, month and year field values are automatically corrected. 

For example,

|    Default Masking   |    Input     |     Output      |
|:---------------------|:-------------|:---------------:|
| If you enter `29` into the date field and `2(Feb)` in the month field, the year field value automatically changed to the upcoming leap year. | 29 (in date field) | <img src="Getting-Started_images/winui-datepicker-leapyear.png" alt="WinUI DatePicker displays Corrects Year Field based on Date"/> |
| If you try to enter values between `13-19` the month field, it will add last input digit(3-9) in the month field and move the cursor to the next field. | 18 (in month field)  | <img src="Getting-Started_images/winui-datepicker-month-editing.png" alt="WinUI DatePicker displays Corrects Month Field based on Input"/> |
| If you try to enter input in month field that is greater than `19`, it will add first digit in month field and last digit added into next field. | 58 (in month field) | <img src="Getting-Started_images/winui-datepicker-month-edit.png" alt="WinUI DatePicker displays Corrects Month Field based on Input"/> |

{% tabs %}
{% highlight xaml %}

<editors:SfDatePicker EditMode="Mask"
                      x:Name="sfDatePicker" />

{% endhighlight  %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.EditMode = DateTimeEditingMode.Mask;

{% endhighlight  %}
{% endtabs %}

![WinUI DatePicker with Editing](Getting-Started_images/winui-datepicker-editing.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/blob/main/Samples/DateRestriction)

## Edit date using free form editing

If you want to perform the validation after the user completely entering their date inputs, use the [`EditMode`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_EditMode) property value as `Normal`. Then the entered date value is validated with the `FormatString` property value by pressing the `Enter` key or lost focus. If entered value is not suit with `FormatString` property, the previously selected date value sets to `SelectedDate` property.

{% tabs %}
{% highlight xaml %}

<editors:SfDatePicker EditMode="Normal"
                      x:Name="sfDatePicker" />

{% endhighlight  %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.EditMode = DateTimeEditingMode.Normal;

{% endhighlight  %}
{% endtabs %}

![WinUI DatePicker with Editing](Getting-Started_images/winui-datepicker-normal-edit.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/blob/main/Samples/DateRestriction)

## Hide clear button in the editor

By default, the clear button `X` will be displayed in the editor of the `Date Picker` control, which can be used to clear the entered input. You can hide the clear button in `Date Picker` control using the [ShowClearButton](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.DateTimePickerBase.html#Syncfusion_UI_Xaml_Editors_DateTimePickerBase_ShowClearButton) property. The default value of `ShowClearButton` property value is **true**.

{% tabs %}
{% highlight XAML %}

<editors:SfDatePicker ShowClearButton="False"
                      Name="sfDatePicker"/>

{% endhighlight %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.ShowClearButton = false;

{% endhighlight %}
{% endtabs %}

![WinUI DatePicker hide clear button](Getting-Started_images/winui-datepicker-hideclearbutton.png)
![WinUI DatePicker hide clear button](Getting-Started_images/winui-datepicker-showclearbutton.png)
