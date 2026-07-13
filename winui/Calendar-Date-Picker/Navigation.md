---
layout: post
title: View Navigation in WinUI Calendar Date Picker control | Syncfusion
description: Learn here all about how to navigate within views in Syncfusion WinUI Calendar Date Picker control and more.
platform: WinUI
control: SfCalendarDatePicker
documentation: ug
---

# View navigation in WinUI Calendar Date Picker

You can easily navigate to the month, year, decade, or century views to select different dates by clicking the header button in the drop-down calendar. Initially, the month view is loaded when the drop-down is opened. You can also change the view programmatically by using the [DisplayMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_DisplayMode) property.

## Navigate between views

You can restrict navigation within a minimum and maximum view by using the [MinDisplayMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_MinDisplayMode) and [MaxDisplayMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_MaxDisplayMode) properties. This will be useful when your date range is smaller and you do not want to show the century view. By default, the value of `MinDisplayMode` is **Month** and `MaxDisplayMode` is **Century**.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="5 6 7" %}

<Window
    ...
     xmlns:calendar="using:Syncfusion.UI.Xaml.Calendar">
    <calendar:SfCalendarDatePicker x:Name="sfCalendarDatePicker"
                                   MinDisplayMode="Month"
                                   MaxDisplayMode="Decade"
                                   DisplayMode="Month"/>
</Window>

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="4 5 6" %}

using Syncfusion.UI.Xaml.Calendar;

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.MinDisplayMode = CalendarDisplayMode.Month;
sfCalendarDatePicker.MaxDisplayMode = CalendarDisplayMode.Decade;
sfCalendarDatePicker.DisplayMode = CalendarDisplayMode.Month;

{% endhighlight %}
{% endtabs %}

![date-picker-view-navigation-in-winui-calendar-date-picker](Navigation_images/date-picker-view-navigation-in-winui-calendar-date-picker.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Restriction).

## Selection based on view restriction

You can restrict users from selecting a date within specific views (example: choosing a validity date for a credit card) in the `Calendar Date Picker` control using the `MinDisplayMode` and `MaxDisplayMode` properties.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="5 6 7" %}

<Window
    ...
     xmlns:calendar="using:Syncfusion.UI.Xaml.Calendar">
    <calendar:SfCalendarDatePicker x:Name="sfCalendarDatePicker"
                                 MinDisplayMode="Year"
                                 MaxDisplayMode="Decade"
                                 DisplayDateFormat="MM/yyyy"
                                 />
</Window>

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="4 5 6" %}

using Syncfusion.UI.Xaml.Calendar;

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.MinDisplayMode = CalendarDisplayMode.Year;
sfCalendarDatePicker.MaxDisplayMode = CalendarDisplayMode.Decade;
sfCalendarDatePicker.DisplayDateFormat = "MM/yyyy";

{% endhighlight %}
{% endtabs %}

![date-picker-restrict-date-selection-in-winui-calendar-date-picker](Navigation_images/date-picker-restrict-date-selection-in-winui-calendar-date-picker.gif)

You can navigate between elements in the drop-down calendar of the `Calendar Date Picker` control using keyboard shortcuts or mouse interaction. The following is the list of keyboard shortcuts to navigate and select.

* **Tab** or **Shift+Tab** - To navigate between date cells and elements in the header.
* **UpArrow**, **DownArrow**, **LeftArrow**, and **RightArrow** - To navigate between calendar date, month, or decade cells.
* **Space** or **Enter** - To select a cell.
* **Ctrl + UpArrow** and **Ctrl + DownArrow** - To navigate between views (Example: Navigate from month to year view).
* **PageUp** and **PageDown** - To navigate within views (Example: Navigate between months).
* **Home** or **End** - To navigate to the first or last cell of the current view.
* **Alt + DownArrow** - To open the drop-down calendar.