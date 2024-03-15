---
layout: post
title: Preset Items in WinUI Calendar DateRange Picker control|Syncfusion
description: Learn here all about how to show preset items in WinUI Calendar DateRange Picker (SfCalendarDateRangePicker) control and more.
platform: winui
control:  SfCalendarDateRangePicker
documentation: ug
---

# Show preset items in drop-down calendar of Calendar DateRange Picker

## Show preset items in drop-down

You can show a collection of preset items in dropdown of `Calendar DateRange Picker` control using the [`Preset`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_Preset) and [`PresetTemplate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_PresetTemplate) properties. Bind the collection of preset items to be displayed in the `Preset` property and set the required template in the `PresetTemplate` property.

{% tabs %}
{% highlight c# tabtitle="ViewModel.cs" %}

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
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="3 7 8 9 10 11 12" %}

<Grid>
    <Grid.DataContext>
        <local:ViewModel x:Name="viewModel" />
    </Grid.DataContext>
    <calendar:SfCalendarDateRangePicker  x:Name="sfCalendarDateRangePicker" Height="35" Width="200"
                                        Preset="{x:Bind viewModel.PresetCollection, Mode=TwoWay}" >
        <calendar:SfCalendarDateRangePicker.PresetTemplate>
            <DataTemplate>
                <ListBox ItemsSource="{Binding}" SelectionChanged="ListBox_SelectionChanged" />
            </DataTemplate>
        </calendar:SfCalendarDateRangePicker.PresetTemplate>
    </calendar:SfCalendarDateRangePicker>
</Grid>

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" %}

private void ListBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
{
    ListBox listBox = sender as ListBox;
    DateTimeOffset todayDate = DateTimeOffset.Now;

    if (listBox.SelectedItem.ToString() == "This Week")
    {
        DateTimeOffset startdate = DateTimeOffset startdate = todayDate.AddDays(-(todayDate.DayOfWeek - (DayOfWeek)sfCalendarDateRangePicker.FirstDayOfWeek));
        sfCalendarDateRangePicker.SelectedRange = new DateTimeOffsetRange(startdate, startdate.AddDays(6));
    }
    else if (listBox.SelectedItem.ToString() == "This Month")
    {
        DateTimeOffset startdate = todayDate.AddDays(-(todayDate.Date.Day - 1));
        int daysToAdd = DateTime.DaysInMonth(startdate.Year, startdate.Month) - 1;
        DateTimeOffset lastDateInMonth = startdate.AddDays(daysToAdd);
        sfCalendarDateRangePicker.SelectedRange = new DateTimeOffsetRange(startdate, lastDateInMonth);
    }
    else if (listBox.SelectedItem.ToString() == "Last Month")
    {
        DateTimeOffset startdate = todayDate.AddMonths(-1).AddDays(-(todayDate.Date.Day - 1));
        int daysToAdd = DateTime.DaysInMonth(startdate.Year, startdate.Month) - 1;
        DateTimeOffset lastDateInMonth = startdate.AddDays(daysToAdd);
        sfCalendarDateRangePicker.SelectedRange = new DateTimeOffsetRange(startdate, lastDateInMonth);
    }
    else if (listBox.SelectedItem.ToString() == "This Year")
    {
        DateTimeOffset startdate = todayDate.AddMonths(-(todayDate.Month - 1)).AddDays(-(todayDate.Date.Day - 1));
        int daysToAdd = DateTime.DaysInMonth(startdate.Year, startdate.Month) - 1;
        DateTimeOffset lastDateInLastMonth = startdate.AddMonths(11).AddDays(daysToAdd);
        sfCalendarDateRangePicker.SelectedRange = new DateTimeOffsetRange(startdate, lastDateInLastMonth);
    }
    else
    {
        sfCalendarDateRangePicker.SelectedRange = null;
    }
}

{% endhighlight %}
{% endtabs %}

![present--item-template-in-winui-calendar-date-range-picker](Images/preset-items/present--item-template-in-winui-calendar-date-range-picker.png)

## Hide calendar on selecting a preset item

You can hide the calendar in the drop-down when user selects any preset items in drop-down other than **CustomRange** using the `ShowCalendar` property. When a user wants to select a custom range of dates, the calendar is added to the drop-down of the 'Calendar DateRange Picker' control after selecting the **CustomRange** preset item.
{% tabs %}
{% highlight c# tabtitle="MainWindow.xaml.cs" %}

privateprivate void ListBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
{
    ListBox listBox = sender as ListBox;
    sfCalendarDateRangePicker.ShowCalendar = false;
    DateTimeOffset todayDate = DateTimeOffset.Now;

    if (listBox.SelectedItem.ToString() == "This Week")
    {
        DateTimeOffset startdate = todayDate.AddDays(-(todayDate.DayOfWeek - sfCalendarDateRangePicker.FirstDayOfWeek));
        sfCalendarDateRangePicker.SelectedRange = new DateTimeOffsetRange(startdate, startdate.AddDays(6));
    }
    else if (listBox.SelectedItem.ToString() == "This Month")
    {
        DateTimeOffset startdate = todayDate.AddDays(-(todayDate.Date.Day - 1));
        int daysToAdd = DateTime.DaysInMonth(startdate.Year, startdate.Month) - 1;
        DateTimeOffset lastDateInMonth = startdate.AddDays(daysToAdd);
        sfCalendarDateRangePicker.SelectedRange = new DateTimeOffsetRange(startdate, lastDateInMonth);
    }
    else if (listBox.SelectedItem.ToString() == "Last Month")
    {
        DateTimeOffset startdate = todayDate.AddMonths(-1).AddDays(-(todayDate.Date.Day - 1));
        int daysToAdd = DateTime.DaysInMonth(startdate.Year, startdate.Month) - 1;
        DateTimeOffset lastDateInMonth = startdate.AddDays(daysToAdd);
        sfCalendarDateRangePicker.SelectedRange = new DateTimeOffsetRange(startdate, lastDateInMonth);
    }
    else if (listBox.SelectedItem.ToString() == "This Year")
    {
        DateTimeOffset startdate = todayDate.AddMonths(-(todayDate.Month - 1)).AddDays(-(todayDate.Date.Day - 1));
        int daysToAdd = DateTime.DaysInMonth(startdate.Year, startdate.Month) - 1;
        DateTimeOffset lastDateInLastMonth = startdate.AddMonths(11).AddDays(daysToAdd);
        sfCalendarDateRangePicker.SelectedRange = new DateTimeOffsetRange(startdate, lastDateInLastMonth);
    }
    else
    {
        sfCalendarDateRangePicker.SelectedRange = null;
        sfCalendarDateRangePicker.ShowCalendar = true;
    }
}

{% endhighlight %}
{% endtabs %}

N> Download demo from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-daterange-picker-examples/tree/main/Samples/PresetItems).