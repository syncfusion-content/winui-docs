---
layout: post
title: Getting started with WinUI Calendar DateRangePicker control|Syncfusion
description: This section describes about how to add the Calendar DateRangePicker (SfCalendarDateRangePicker) control into WinUI application and its basic features.
platform: WinUI
control: SfCalendarDateRangePicker
documentation: ug
---

# Getting Started with WinUI Calendar DateRangePicker

This section explains the steps required to add the `Calendar DateRangePicker` control and its date range selection options. 

## Structure of Calendar DateRangePicker control

![Structure of WinUI Calendar DateRangePicker control](Getting-Started_images/OriginalStructure.png)

## Creating an application with WinUI Calendar DateRangePicker

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop) or [WinUI 3 app in UWP for C#](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp).
2. Add reference to [Syncfusion.Calendar.WinUI](https://www.nuget.org/packages/Syncfusion.Calendar.WinUI) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Calendar` in XAML or C# code.
4. Initialize the `Calendar DateRangePicker` control.

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
        <!--Adding CalendarDateRangePicker control -->
        <calendar:SfCalendarDateRangePicker Name="sfCalendarDateRangePicker"/>
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
            SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();

            grid.Children.Add(sfCalendarDateRangePicker);
        }
    }
}

{% endhighlight %}
{% endtabs %}

![CalendarDateRangePicker control added in the application](Getting-Started_images/Overview_img1.png)

## Select the date range programmatically

You can set or change the selected date range programmatically by using `SelectedRange` property. By default, the `SelectedRange` property value is `null`.

{% tabs %}
{% highlight C# %}

SfCalendarDateRangePicker sfCalendarDateRangePicker= new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.SelectedRange = new DateTimeOffsetRange(new DateTimeOffset(new DateTime(2021, 03,10)), new DateTimeOffset(new DateTime(2021, 03, 22)));

{% endhighlight %}
{% endtabs %}

![Calendar DateRangePicker displaying the selected range dates](Getting-Started_images/SelectedRange.png)

## Select date range interactively

You can change the selected date range interactively by selecting from drop down calendar. You can get the selected date range from the `SelectedRange` property.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDateRangePicker Name="sfCalendarDateRangePicker" />

{% endhighlight %}
{% highlight C# %}

SfCalendarDateRangePicker sfCalendarDateRangePicker= new SfCalendarDateRangePicker();

{% endhighlight %}
{% endtabs %}

![Calendar DateRangePicker displaying selected date range](Getting-Started_images/CalendarDateRangePicker_Interactive.gif)

## Setting watermark text

You can prompt the user with any information by using the `PlaceHolderText` property. This watermark text will be displayed only when the `SelectedRange` property value is `null`. 

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDateRangePicker PlaceHolderText="Select the Date"
                               SelectedRange="{x:Null}"
                               Name="sfCalendarDateRangePicker" />

{% endhighlight %}
{% highlight C# %}

SfCalendarDateRangePicker sfCalendarDateRangePicker= new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.PlaceHolderText = "Select the Date";
sfCalendarDateRangePicker.SelectedRange = null;

{% endhighlight %}
{% endtabs %}

![Calendar DateRangePicker displaying watermark text](Getting-Started_images/PlaceHolderText.png)

## Selected range changed notification

You will be notified when selected range changed in `Calendar DateRangePicker` by using `SelectedDateRangeChanged` event. The `SelectedDateRangeChanged` event contains the old and new start value of range in `RangeStartNewValue` and `RangeStartOldValue` properties and old and new end value of range in `RangeEndNewValue` and `RangeEndOldValue` properties.

* `RangeStartOldValue` - Gets a date which is previously selected as start value in range.
* `RangeStartNewValue` - Gets a date which is currently selected as start value in range.
* `RangeEndOldValue` - Gets a date which is previously selected as end value in range.
* `RangeEndNewValue` - Gets a date which is currently selected as end value in range.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendarDateRangePicker SelectedDateChanged="SfCalendarDateRangePicker_SelectedDateChanged" 
                               Name="sfCalendarDateRangePicker"/>

{% endhighlight %}
{% highlight C# %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.SelectedDateChanged += SfCalendarDateRangePicker_SelectedDateChanged;

{% endhighlight %}
{% endtabs %}

You can handle the event as shown below.

{% tabs %}
{% highlight C# %}

private void SfCalendarDateRangePicker_SelectedDateChanged(object sender, SelectedDateChangedEventArgs e)
{
    var StartOldValue = e.RangeStartOldValue;
    var StartNewValue = e.RangeStartNewValue;
    var EndOldValue = e.RangeEndOldValue;
    var EndNewValue = e.RangeEndNewValue;
}

{% endhighlight %}
{% endtabs %}

## Restrict date range selection
You can restrict users to select date range within specified minimum and maximum dates, or disable dates by setting blackoutdates or by setting selection range duration.

## Navigate in dropdown calendar
You can navigate between month, year, decade and century views in dropdown calendar fo `Calendar DateRangePicker` control and even restrict navigation and range selection within specific views.