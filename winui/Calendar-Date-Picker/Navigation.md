---
layout: post
title: View Navigation in WinUI Calendar Date Picker control | Syncfusion
description: Learn here all about how to navigate within views in Syncfusion WinUI Calendar Date Picker control and more.
platform: WinUI
control: SfCalendarDatePicker
documentation: ug
---

# View navigation in WinUI Calendar Date Picker

You can easily navigate to the month, year, decade, or century views to select different dates by clicking the header button in dropdown calendar. Initially month view is loaded when dropdown is opened. You can also change the view programmatically by using [DisplayMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_DisplayMode) property.

## Navigate between views

You can restrict navigation within a minimum and maximum views by using [MinDisplayMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_MinDisplayMode) and [MaxDisplayMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_MaxDisplayMode) properties. This will be useful when your date range is smaller and you don’t want to show century view. By default, the value of `MinDisplayMode` is **Month** and `MaxDisplayMode` is **Century**.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDatePicker x:Name="sfCalendarDatePicker"
                               MinDisplayMode="Month"
                               MaxDisplayMode="Decade"
                               DisplayMode="Month"/>

{% endhighlight %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.MinDisplayMode = CalendarDisplayMode.Month;
sfCalendarDatePicker.MaxDisplayMode = CalendarDisplayMode.Decade;
sfCalendarDatePicker.DisplayMode = CalendarDisplayMode.Month;

{% endhighlight %}
{% endtabs %}

![date-picker-view-navigation-in-winui-calendar-date-picker](Navigation_images/date-picker-view-navigation-in-winui-calendar-date-picker.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Restriction)

## Selection based on view restriction

You can restrict users to select date within specific views (example : choosing validity date for credit card) in `Calendar Date Picker` control using the `MinDisplayMode` and `MaxDisplayMode` properties.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDatePicker x:Name="sfCalendarDatePicker" 
                             MinDisplayMode="Year"
                             MaxDisplayMode="Decade"
                             FormatString="MM/yyyy"
                             />

{% endhighlight %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.MinDisplayMode = CalendarDisplayMode.Year;
sfCalendarDatePicker.MaxDisplayMode = CalendarDisplayMode.Decade;
sfCalendarDatePicker.FormatString = "MM/yyyy";

{% endhighlight %}
{% endtabs %}

![date-picker-restrict-date-selection-in-winui-calendar-date-picker](Navigation_images/date-picker-restrict-date-selection-in-winui-calendar-date-picker.gif)

You can navigate between elements in the dropdown calendar of `Calendar Date Picker` control by keyboard keys or by mouse interaction. The keyboard keys to navigate and select are listed below.

* **Tab** or **Shift+Tab** - To navigate between date cell and elements in header.
* **UpArrow**,**DownArrow**,**LeftArrow** and **RightArrow** - To navigate between calendar date or month or decade cells.
* **Space** or **Enter** - To select a cell.
* **Ctrl + UpArrow** and **ctrl + DownArrow** - To navigate between views (Example: Navigate from month to year view).
* **PageUp** and **PageDown** - To navigate within views (Example: Navigate between months).
* **Home** or **End** - To navigate to the first cells or last cell of current view.
* **Alt + DownArrow** - To open the dropdown calendar.