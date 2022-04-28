---
layout: post
title: Localization and Formatting in WinUI Date Picker| Syncfusion
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
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="3" %}

<editors:SfDatePicker 
                      x:Name="sfDatePicker"
                      CalendarIdentifier="HebrewCalendar"/>

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.CalendarIdentifier = "HebrewCalendar";

{% endhighlight %}
{% endtabs %}

![calendar-types-hebrew-calendar-in-winui-date-picker](Images/drop-down-date-spinner/calendar-types-hebrew-calendar-in-winui-date-picker.png)

N> `Date Picker` control updates the flow direction visually based on the `CalendarIdentifier` property value.

N> When `CalendarIdentifier` and `FlowDirection` properties are set, `FlowDirection` property have higher precedence.

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/tree/main/Samples/Localization)

## Change flow direction

You can change the flow direction of the `Date Picker` layout from right to left by setting the `FlowDirection` property value as `RightToLeft`. The default value of `FlowDirection` property is `LeftToRight`.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="3" %}

<editors:SfDatePicker  
                      x:Name="sfDatePicker"
                      FlowDirection="RightToLeft" />

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.FlowDirection = FlowDirection.RightToLeft;

{% endhighlight %}
{% endtabs %}

![change-flow-direction-in-winui-date-picker](Images/drop-down-date-spinner/change-flow-direction-in-winui-date-picker.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/blob/main/Samples/ViewAndItemCustomization)

## Change the language

You can localize the `Date Picker` using the `Language` property. The default value of `Language` property is **en-US**.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="3" %}

<editors:SfDatePicker 
                      x:Name="sfDatePicker"
                      Language="ar-SA"/>

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.Language = "ar-SA";

{% endhighlight %}
{% endtabs %}

![calendar-types-arabic-calendar-with-localization-in-winui-date-picker](Images/drop-down-date-spinner/calendar-types-arabic-calendar-with-localization-in-winui-date-picker.png)

N> `Date Picker` control updates the flow direction visually based on the `Language` property value.

N> When `Language` and `FlowDirection` properties are set, `FlowDirection` property have higher precedence.

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/tree/main/Samples/Localization)

## Change editor display format

You can edit and display the selected date with various formatting like date, month and year formats by using the [`DisplayDateFormat`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_DisplayDateFormat) property. The default value of `DisplayDateFormat` property is `d`.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2" %}

<editors:SfDatePicker x:Name="sfDatePicker" 
                      DisplayDateFormat="MM/dd" />

{% endhighlight  %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.DisplayDateFormat= "MM/dd";

{% endhighlight  %}
{% endtabs %}

![change-display-date-formatting-in-winui-date-picker](Images/getting-started/change-display-date-formatting-in-winui-date-picker.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/blob/main/Samples/DateRestriction)

## Change the field value format in Spinner

You can customize the format of the date, month and year fields in the spinner of the `DatePicker` control by using the [`DayFormat`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_DayFormat), [`MonthFormat`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_MonthFormat) and [`YearFormat`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_YearFormat) properties. By default, the value of `DayFormat` property is `{}{day.integer}`, the value `MonthFormat` property is `{}{month.abbreviated}` and the value of `YearFormat` property is `{}{year.full}`.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="3 4 5" %}

<editor:SfDatePicker HorizontalAlignment="Center"
                    VerticalAlignment="Center"
                    DayFormat="{}{day.integer}"
                    MonthFormat="{}{month.full}"
                    YearFormat="{}{year.abbreviated}"
                    />

{% endhighlight  %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2 3 4" %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.DayFormat = "{day.integer}";
sfDatePicker.MonthFormat = "{month.full}";
sfDatePicker.YearFormat = "{year.abbreviated}";
sfDatePicker.HorizontalAlignment = HorizontalAlignment.Center;
sfDatePicker.VerticalAlignment = VerticalAlignment.Center;

{% endhighlight  %}
{% endtabs %}

![change-display-date-month-year-formatting-in-winui-date-picker](Images/getting-started/change-display-date-month-year-formatting-in-winui-date-picker.png)

## Edit date using mask mode

By default ‘Mask’ editing is enabled, which ensure that it contains only valid value. As soon as in input is given, the value is validated and correction is done immediately. Once input is completed for a field, cursor moves to next field automatically.

Based on the `DisplayDateFormat` and your input values, date, month and year field values are automatically corrected. 

For example,

|    Default Masking   |    Input     |     Output      |
|:---------------------|:-------------|:---------------:|
| If you enter `29` into the date field and `2(Feb)` in the month field, the year field value automatically changed to the upcoming leap year. | 29 (in date field) | <img src="Images/getting-started/winui-datepicker-leap-year.png" alt="WinUI DatePicker displays Corrects Year Field based on Date"/> <img src="Images/getting-started/winui-datepicker-leap-year-with-selection.png" alt="WinUI DatePicker displays Corrects Year Field based on Date"/> |
| If you try to enter values between `13-19` the month field, it will add last input digit(3-9) in the month field and move the cursor to the next field. | 18 (in month field)  | <img src="Images/getting-started/winui-date-picker-month-editing.png" alt="WinUI DatePicker displays Corrects Month Field based on Input"/><img src="Images/getting-started/winui-date-picker-month-editing-with-selection.png" alt="WinUI DatePicker displays Corrects Month Field based on Input"/> |
| If you try to enter input in month field that is greater than `19`, it will add first digit in month field and last digit added into next field. | 58 (in month field) | <img src="Images/getting-started/winui-date-picker-month-edit.png" alt="WinUI DatePicker displays Corrects Month Field based on Input"/><img src="Images/getting-started/winui-date-picker-month-edit-with-selection.png" alt="WinUI DatePicker displays Corrects Month Field based on Input"/> |

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="3" %}

<editors:SfDatePicker 
                      x:Name="sfDatePicker" 
                      EditMode="Mask" />

{% endhighlight  %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.EditMode = DateTimeEditMode.Mask;

{% endhighlight  %}
{% endtabs %}

![change-edit-mode-with-mask-in-winui-date-picker](Images/getting-started/change-edit-mode-with-mask-in-winui-date-picker.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/blob/main/Samples/DateRestriction)

## Edit date using free form editing

If you want to perform the validation after the user completely entering their date inputs, use the [`EditMode`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_EditMode) property value as `Normal`. Then the entered date value is validated with the `DisplayDateFormat` property value by pressing the `Enter` key or lost focus. If entered value is not suit with `DisplayDateFormat` property, the previously selected date value sets to `SelectedDate` property.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="3" %}

<editors:SfDatePicker 
                      x:Name="sfDatePicker"
                      EditMode="Normal" />

{% endhighlight  %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.EditMode = DateTimeEditMode.Normal;

{% endhighlight  %}
{% endtabs %}

![change-edit-mode-with-normal-in-winui-date-picker](Images/getting-started/change-edit-mode-with-normal-in-winui-date-picker.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/blob/main/Samples/DateRestriction)

## Hide clear button in the editor

By default, the clear button `X` will be displayed in the editor of the `Date Picker` control, which can be used to clear the entered input. You can hide the clear button in `Date Picker` control using the [ShowClearButton](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.DateTimePickerBase.html#Syncfusion_UI_Xaml_Editors_DateTimePickerBase_ShowClearButton) property. The default value of `ShowClearButton` property value is **true**.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="3" %}

<editors:SfDatePicker 
                      Name="sfDatePicker"
                      ShowClearButton="False"/>

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.ShowClearButton = false;

{% endhighlight %}
{% endtabs %}

![hide-clear-button-in-winui-date-picker](Images/getting-started/hide-clear-button-in-winui-date-picker.png)

![show-clear-button-in-winui-date-picker](Images/getting-started/show-clear-button-in-winui-date-picker.png)