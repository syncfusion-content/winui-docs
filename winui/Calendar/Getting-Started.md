---
layout: post
title: Getting started with WinUI Calendar control | Syncfusion
description: This section describes about how to add the SfCalendar control into WinUI application and its basic features.
platform: WinUI
control: SfCalendar
documentation: ug
---

# Getting Started with WinUI Calendar (SfCalendar)

This section explains the steps required to add the [Calendar](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html) control and its date selection options. This section covers only basic features needed to get started with Syncfusion `Calendar` control.

## Structure of Calendar control

![Structure of WinUI Calendar control](Getting-Started_images/Structure.png)

## Creating an application with WinUI Calendar

1. Create a simple project using the instructions given in the [Getting Started with your first WinUI app](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp) documentation.
2. Add reference to [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Calendar` in XAML or C# code.
4. Initialize the `SfCalendar` control.

{% tabs %}
{% highlight xaml %}

<Page
    x:Class="GettingStarted.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:calendar="using:Syncfusion.UI.Xaml.Calendar"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid Name="grid">
        <!--Adding Calendar control -->
        <calendar:SfCalendar Name="sfCalendar"/>
    </Grid>
</Page>

{% endhighlight %}
{% highlight C# %}

using Syncfusion.UI.Xaml.Calendar;

namespace GettingStarted
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainPage : Page
    {
        public MainPage()
        {
            this.InitializeComponent();
            // Creating an instance of the Calendar control
            SfCalendar sfCalendar = new SfCalendar();

            grid.Children.Add(sfCalendar);
        }
    }
}

{% endhighlight %}
{% endtabs %}

![Calendar control added in the application](Getting-Started_images/Calendar_Added.png)

## Select the date programmatically

You can set or change the selected date programmatically by using [SelectedDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectedDate) property. If you not assign any value for the `SelectedDate` property, `Calendar` will automatically assign the current system date as `SelectedDate`.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar Name="sfCalendar" />

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar= new SfCalendar();
sfCalendar.SelectedDate = new DateTimeOffset(new DateTime(2021, 01, 06));

{% endhighlight %}
{% endtabs %}

![Calendar displaying the selected date](Getting-Started_images/Selecteddate.png)

## Select multiple dates

By default, `Calendar` control allows you to select single date at a time. If you want to select multiple dates from different month, year or decade or from century, use the [SelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectionMode) property value as `Multiple`. You can gets the selected dates from the [SelectedDates](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectedDates) collection.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar Name="sfCalendar" 
                     SelectionMode="Multiple" />

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar= new SfCalendar();
sfCalendar.SelectionMode = CalendarSelectionMode.Multiple;

{% endhighlight %}
{% endtabs %}

![Calendar allows you to select multiple dates](Getting-Started_images/multipledate_selection.png)

## Restrict date selection

You can restrict the users from selecting a date within the particular range by specifying [MinDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_MinDate) and [MaxDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_MaxDate) properties in `Calendar` control. The default value of `MinDate` property is `1/1/1920 12:00:00 AM +00:00` and `MaxDate` property is `12/31/2120 11:59:59 PM +00:00`.

{% tabs %}
{% highlight xaml %}

<calendar:Calendar x:Name="sfCalendar"/>

{% endhighlight  %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
 sfCalendar.MinDate = new DateTimeOffset(new DateTime(2021, 01, 5));
 sfCalendar.MaxDate = new DateTimeOffset(new DateTime(2021, 01, 27));

{% endhighlight  %}
{% endtabs %}

![Calendar restrict the date selection with particular range](Getting-Started_images/MinMaxdate.png)

## Selected date changed notification

You will be notified when selected date changed in `Calendar` by using [SelectedDateChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectedDateChanged) event. The [SelectedDateChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SelectedDateChangedEventArgs.html) event contains the old and newly selected date in the [OldDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SelectedDateChangedEventArgs.html#Syncfusion_UI_Xaml_Calendar_SelectedDateChangedEventArgs_OldDate), [NewDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SelectedDateChangedEventArgs.html#Syncfusion_UI_Xaml_Calendar_SelectedDateChangedEventArgs_NewDate) properties.

* `OldDate` - Gets a date which is previously selected.
* `NewDate` - Gets a date which is currently selected.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendar SelectedDateChanged="SfCalendar_SelectedDateChanged" 
                     Name="sfCalendar"/>

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.SelectedDateChanged += SfCalendar_SelectedDateChanged;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows:

{% tabs %}
{% highlight C# %}

private void SfCalendar_SelectedDateChanged(object sender, SelectedDateChangedEventArgs e)
{
    var oldDate = e.OldDate;
    var newDate = e.NewDate;
}

{% endhighlight %}
{% endtabs %}

## Disable/block all weekends

You can prevent the users from selecting weekend days or any other dates by handling the [ItemPrepared](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_ItemPrepared) event and setting [ItemInfo.IsBlackout](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.CalendarItemPreparedEventArgs.html#Syncfusion_UI_Xaml_Calendar_CalendarItemPreparedEventArgs_ItemInfo) property value as `true` for that specific dates.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar x:Name="sfCalendar" ItemPrepared="SfCalendar_ItemPrepared"/>

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.ItemPrepared += SfCalendar_ItemPrepared;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows:

{% tabs %}
{% highlight C# %}

private void SfCalendar_ItemPrepared(object sender, CalendarItemPreparedEventArgs e)
{
    //Block all weekend days
    if (e.ItemInfo.ItemType == CalendarItemType.Day &&
        (e.ItemInfo.Date.DayOfWeek == DayOfWeek.Saturday ||
        e.ItemInfo.Date.DayOfWeek == DayOfWeek.Sunday))
    {
        e.ItemInfo.IsBlackout = true;
    }
}

{% endhighlight %}
{% endtabs %}

![Calendar restrict the weekend dates from selection](Getting-Started_images/blockweekend.png)

## Navigate between views

You can select a date from different year, decade, or century easily by navigating to year, decade, or century view. Initially month view is loaded. If you want to change the initial view, use [DisplayMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_DisplayMode) property.


You can restrict navigation within a minimum and maximum views by using [MinDisplayMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_MinDisplayMode) and [MaxDisplayMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_MaxDisplayMode) properties. This will be useful when your date range is smaller and you don’t want to show century view.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar x:Name="sfCalendar"
                     MinDisplayMode="Month"
                     MaxDisplayMode="Century"
                     DisplayMode="Month"/>

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.MinDisplayMode = CalendarDisplayMode.Month;
sfCalendar.MaxDisplayMode = CalendarDisplayMode.Century;
sfCalendar.DisplayMode = CalendarDisplayMode.Month;

{% endhighlight %}
{% endtabs %}

![Navigation between month and century view in WinUI Calendar](Getting-Started_images/view-navigation.gif)

## First day of week

By default, Sunday is shown as the first day of the week. If you want to change the first day of week, use the [FirstDayOfWeek](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_FirstDayOfWeek) property value. The default value of `FirstDayOfWeek` property is `Sunday`.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar x:Name="sfCalendar" 
                     FirstDayOfWeek="Monday"/>

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.FirstDayOfWeek = DayOfWeek.Monday;

{% endhighlight %}
{% endtabs %}

![WinUI Calendar weekdays start from Monday](Getting-Started_images/first-day-of-week.png)

## Date formatting

You can use different date formats such as abbreviated or full name for a day, month, week names or header name of month and year by using the [DateFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_DateFormat), [MonthFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_MonthFormat), [DayOfWeekFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_DayOfWeekFormat) and [HeaderFormatInMonthView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_HeaderFormatInMonthView) properties.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar DateFormat="{}{day.integer(2)}"
                     MonthFormat="{}{month.full}"
                     DayOfWeekFormat="{}{dayofweek.abbreviated(3)}"
                     HeaderFormatInMonthView="{}{month.abbreviated} {year.abbreviated}‎"
                     x:Name="sfCalendar"/>

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.DateFormat = "{day.integer(2)}";
sfCalendar.MonthFormat = "{month.full}";
sfCalendar.DayOfWeekFormat = "{dayofweek.abbreviated(3)}";
sfCalendar.HeaderFormatInMonthView = "{month.abbreviated} {year.abbreviated}‎";

{% endhighlight %}
{% endtabs %}

![Displaying full month and abbreviated year format in WinUI Calendar.](Getting-Started_images/dateformat.gif)

## Number of weeks in a view

If you want to increase or decrease the number of weeks shown in a month view, use the [NumberOfWeeksInView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_NumberOfWeeksInView) property. The default value of `NumberOfWeeksInView` property is `6`.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar NumberOfWeeksInView="3"
                     x:Name="sfCalendar"/>

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.NumberOfWeeksInView = 3;

{% endhighlight %}
{% endtabs %}

![Show particular weeks in WinUI Calendar.](Getting-Started_images/weeks-in-view.png)

## Hide days that is out of scope

By default, out of scope view days are disabled. If you want to hide the days that are out of the scope of current view, use the [OutOfScopeVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_OutOfScopeVisibility) property value as `Hidden`. The default value of `OutOfScopeVisibility` property is `Disabled`.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar OutOfScopeVisibility="Hidden"
                     x:Name="sfCalendar"/>

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.OutOfScopeVisibility = OutOfScopeVisibility.Hidden;

{% endhighlight %}
{% endtabs %}

![Display only the current month dates in WinUI Calendar.](Getting-Started_images/disableoutofscope.png)

## Calendar types

The `Calendar` control supports nine different calendar types, such as Gregorian, Julian, Hebrew, etc. You can change the calendar type by using [CalendarIdentifier](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_CalendarIdentifier) property. The default value of `CalendarIdentifier` property is `GregorianCalendar`.

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

## Culture support

If you want to localize the calendar, use the `Language` property. The default value of `Language` property is `en-US`.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar Language="fr"
                     x:Name="sfCalendar"/>

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.Language = "fr";

{% endhighlight %}
{% endtabs %}

![Displaying french cultured WinUI Calendar.](Getting-Started_images/Language.png)