---
layout: post
title: Navigation between views in WinUI Calendar control | Syncfusion
description: Learn here all about how to navigate between views and perform selection in the Calendar (SfCalendar) control and more.
platform: WinUI
control: SfCalendar
documentation: ug
---

# Navigate between views in WinUI Calendar (SfCalendar)

You can easily navigate to the month, year, decade, or century views to select different dates by clicking the header button. Initially month view is loaded. You can also change the view programmatically by using [DisplayMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_DisplayMode) property.

## Bring a date into view

You can navigate to the month containing required date using [`SetDisplayDate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SetDisplayDate_System_DateTimeOffset_) method. To navigate to the required date of any month or year, pass the **DateTime** value in `SetDisplayDate` method argument.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2" %}

<calendar:SfCalendar x:Name="calendar" 
                     Loaded="calendar_Loaded">
</calendar:SfCalendar>

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="3" %}

private void calendar_Loaded(object sender, RoutedEventArgs e)
{
    calendar.SetDisplayDate(new DateTimeOffset(new DateTime(2021, 01, 01)));
}

{% endhighlight %}
{% endtabs %}

## Restrict navigation between views

You can restrict navigation within a minimum and maximum views by using [MinDisplayMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_MinDisplayMode) and [MaxDisplayMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_MaxDisplayMode) properties. This will be useful when your date range is smaller and you don’t want to show century view. By default, the value of `MinDisplayMode` is **Month** and `MaxDisplayMode` is **Century**.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2 3 4" %}

<calendar:SfCalendar x:Name="sfCalendar"
                     MinDisplayMode="Month"
                     MaxDisplayMode="Decade"
                     DisplayMode="Month"/>

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2 3 4" %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.MinDisplayMode = CalendarDisplayMode.Month;
sfCalendar.MaxDisplayMode = CalendarDisplayMode.Decade;
sfCalendar.DisplayMode = CalendarDisplayMode.Month;

{% endhighlight %}
{% endtabs %}

![restrict-view-navigation-in-winui-calendar](Images/navigation/restrict-view-navigation-in-winui-calendar.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-examples/blob/main/Samples/Restriction)

## Selection based on view restriction

You can restrict users to select date or dates within specific views (example : choosing valid date for credit card) in `Calendar` control using the `MinDisplayMode` and `MaxDisplayMode` properties.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2 3" %}

<calendar:SfCalendar x:Name="sfCalendar" 
                             MinDisplayMode="Year"
                             MaxDisplayMode="Decade"
                             />

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2 3" %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.MinDisplayMode = CalendarDisplayMode.Year;
sfCalendar.MaxDisplayMode = CalendarDisplayMode.Decade;

{% endhighlight %}
{% endtabs %}

![selection-based-on-view-restriction-in-winui-calendar](Images/navigation/selection-based-on-view-restriction-in-winui-calendar.gif)

## Scrolling within a view

You can navigate within a view using mouse scroll or by navigation button in `Calendar` control. The navigation direction animation can be changed by using the [`NavigationDirection`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_NavigationDirection) property value. By default, the value of `NavigationDirection` property is **Vertical**.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2" %}

<calendar:SfCalendar x:Name="sfCalendar"
                     NavigationDirection="Horizontal"
                     />

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.NavigationDirection = Orientation.Horizontal;

{% endhighlight %}
{% endtabs %}

![change-navigation-buttons-in-winui-calendar](Images/navigation/change-navigation-buttons-in-winui-calendar.png)

When the `NavigationDirection` property is **Vertical**, you can navigate within views by mouse scroll or by navigation buttons. When the `NavigationDirection` property is **Horizontal**, you can navigate by navigation buttons only.

![change-navigation-buttons-direction-in-winui-calendar](Images/navigation/change-navigation-buttons-direction-in-winui-calendar.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-examples/blob/main/Samples/Restriction)

## Navigation by keyboard

You can navigate between elements in `Calendar` control by keyboard keys or by mouse interaction. The keyboard keys to navigate and select are listed below.

* **Tab** or **Shift+Tab** - To navigate between date cell and elements in header.
* **UpArrow**,**DownArrow**,**LeftArrow** and **RightArrow** - To navigate between calendar date or month or decade cells.
* **Space** or **Enter** - To select a cell.
* **Ctrl + UpArrow** and **ctrl + DownArrow** - To navigate between views (Example: Navigate from month to year view).
* **PageUp** and **PageDown** - To navigate within views (Example: Navigate between months).
* **Home** or **End** - To navigate to the first cells or last cell of current view.