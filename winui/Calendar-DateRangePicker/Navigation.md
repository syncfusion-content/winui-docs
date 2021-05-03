---
layout: post
title: View navigation in WinUI CalendarDateRangePicker control|Syncfusion
description: This section describes how to navigate between views the Calendar DateRange Picker (SfCalendarDateRangePicker) control.
platform: WinUI
control: SfCalendarDateRangePicker
documentation: ug
---

# View navigation in dropdown calendar of Calendar DateRange Picker

## Navigate between views

You can easily navigate to the month, year, decade, or century views to select different date ranges in the dropdown calendar by clicking the header button. Initially, month view is loaded in the dropdown calendar.

![Navigation between views in WinUI Calendar DateRange Picker](Navigate-Between-Views_images/View-navigation.gif)

## Restrict navigation between views

You can restrict navigation within a minimum and maximum views by using [`MinDisplayMode`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_MinDisplayMode) and [`MaxDisplayMode`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_MaxDisplayMode) properties. This will be useful when your date range is smaller and you don’t want to show decade and century views.

By default, the value of `MinDisplayMode` property is **Month** and `MaxDisplayMode` property is **Century**.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDateRangePicker x:Name="sfCalendarDateRangePicker"
                               MinDisplayMode="Month"
                               MaxDisplayMode="Year"
                               />

{% endhighlight %}
{% highlight C# %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.MinDisplayMode = CalendarDisplayMode.Month;
sfCalendarDateRangePicker.MaxDisplayMode = CalendarDisplayMode.Year;

{% endhighlight %}
{% endtabs %}

N> When `MinDisplayMode` property value is **Year** and `MinDate` value is **15/01/2021**, selecting the month of minimum date will set the starting date value from the minimum date i.e.. from *January 15, 2021*.

![Navigation between month and century view in WinUI Calendar DateRange Picker](Getting-Started_images/Restrict_View_Navigation.gif)

## Selection based on view restriction

You can restrict users to select date range within specific views (example : choosing manufactured and expiry date of product) in `Calendar DateRange Picker` control using the `MinDisplayMode` and `MaxDisplayMode` properties.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDateRangePicker x:Name="sfCalendarDateRangePicker"
                                    FormatString="{}{0:MM/yyyy} - {1:MM/yyyy}"
                                    MinDisplayMode="Year"
                                    MaxDisplayMode="Decade"
                               />

{% endhighlight %}
{% highlight C# %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.MinDisplayMode = CalendarDisplayMode.Year;
sfCalendarDateRangePicker.MaxDisplayMode = CalendarDisplayMode.Decade;
sfCalendarDateRangePicker.FormatString = "{0:MM/yyyy}-{1:MM/yyyy}";

{% endhighlight %}
{% endtabs %}

![Selection within restriction in WinUI Calendar DateRange Picker](Navigate-Between-Views_images/product-manufacture-expiry-date.gif)

## Navigation by keyboard

You can navigate between elements in the dropdown calendar of `Calendar DateRange Picker` control by keyboard keys or by mouse interaction. The keyboard keys to navigate and select are listed below.

* **Tab** or **Shift+Tab** - To navigate between date cell and elements in header.
* **UpArrow**,**DownArrow**,**LeftArrow** and **RightArrow** - To navigate between calendar date or month or decade cells.
* **Space** or **Enter** - To select a cell.
* **Ctrl+UpArrow** and **ctrl+DownArrow** - To navigate between views(Navigate from month to year view).
* **PageUp** and **PageDown** - To navigate within views(Navigate between months).
* **Home** or **End** - To navigate to the first cells or last cell of current view.
* **Alt+DownArrow** - To open the dropdown calendar.