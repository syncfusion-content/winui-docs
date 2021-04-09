---
layout: post
title: Show preset items in WinUI CalendarDateRangePicker control|Syncfusion
description: This page explain how to show preset items in dropdown calendar of the WinUI CalendarDateRangePicker (SfCalendarDateRangePicker) control.
platform: winui
control:  SfCalendarDateRangePicker
documentation: ug
---

# Showing preset items in dropdown calendar of Calendar DateRangePicker

You can show collection of preset items in dropdown of `Calendar DateRangePicker` control using `Preset` and `PresetTemplate` properties. Bind the collection of preset items to be displayed in `Preset` property and set the required template in `PresetTemplate` property.

{% tabs %}
{% highlight c# %}

//ViewModel class
class ViewModel
    {
        public ObservableCollection<string> PresetCollection { get; set; }
        public ViewModel()
        {
            PresetCollection = new ObservableCollection<string>();
            PresetCollection.Add("This Week");
            PresetCollection.Add("This Month");
            PresetCollection.Add("Last Month");
            PresetCollection.Add("This Year");
            PresetCollection.Add("Custom Range");
        }
    }

{% endhighlight %}
{% endtabs %}

Add the `Syncfusion.UI.Xaml.Calendar` namespace reference in code-behind.

{% tabs %}
{% highlight XAML %}

<Page
    x:Class="Calendar_WinUI_FT.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:Calendar_WinUI_FT"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" xmlns:calendar="using:Syncfusion.UI.Xaml.Calendar"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Page.DataContext>
        <local:ViewModel x:Name="viewModel" />
    </Page.DataContext>
    <Grid>
        <calendar:SfCalendarDateRangePicker  x:Name="sfCalendar" Height="35" Width="200"
                                            Preset="{x:Bind viewModel.PresetCollection, Mode=TwoWay}" >
            <calendar:SfCalendarDateRangePicker.PresetTemplate>
                <DataTemplate>
                    <ListBox ItemsSource="{Binding}" SelectionChanged="ListBox_SelectionChanged" />
                </DataTemplate>
            </calendar:SfCalendarDateRangePicker.PresetTemplate>
        </calendar:SfCalendarDateRangePicker>
    </Grid>
</Page>



{% endhighlight %}
{% highlight c# %}

 private void ListBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
 {
    ListBox listBox = sender as ListBox;
    this.sfCalendarDateRangePicker.ShowCalendar = false;
    if (listBox.SelectedItem.ToString() == "This Week")
    {
        DateTimeOffset startdate = DateTimeOffset.Now.AddDays(-(DateTimeOffset.Now.DayOfWeek - sfCalendarDateRangePicker.FirstDayOfWeek));
        this.sfCalendarDateRangePicker.SelectedRange = new DateTimeOffsetRange(startdate, startdate.AddDays(6));
    }
    else if (listBox.SelectedItem.ToString() == "This Month")
    {
        DateTimeOffset startdate = DateTimeOffset.Now.AddDays(-(DateTimeOffset.Now.Date.Day - 1));
        this.sfCalendarDateRangePicker.SelectedRange = new DateTimeOffsetRange(startdate, startdate.AddDays(DateTime.DaysInMonth(startdate.Year, startdate.Month) - 1));
    }
    else if (listBox.SelectedItem.ToString() == "Last Month")
    {
        DateTimeOffset startdate = DateTimeOffset.Now.AddMonths(1).AddDays(-(DateTimeOffset.Now.Date.Day - 1));
        this.sfCalendarDateRangePicker.SelectedRange = new DateTimeOffsetRange(startdate, startdate.AddDays(DateTime.DaysInMonth(startdate.Year, startdate.Month) - 1));
    }
    else if (listBox.SelectedItem.ToString() == "This Year")
    {
        DateTimeOffset startdate = DateTimeOffset.Now.AddMonths(-(DateTimeOffset.Now.Month - 1)).AddDays(-(DateTimeOffset.Now.Date.Day - 1));
        this.sfCalendarDateRangePicker.SelectedRange = new DateTimeOffsetRange(startdate, startdate.AddMonths(11).AddDays(DateTime.DaysInMonth(startdate.Year, startdate.Month) - 1));
    }
    else
    {
        this.sfCalendarDateRangePicker.SelectedRange = null;
        this.sfCalendarDateRangePicker.ShowCalendar = true;
    }
 }

{% endhighlight %}
{% endtabs %}

![Calendar DateRangePicker dropdown with preset collection](Dropdown-Calendar_images/PresetCollection.png)

