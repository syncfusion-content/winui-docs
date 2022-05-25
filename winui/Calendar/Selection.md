---
layout: post
title: Selection in WinUI Calendar control | Syncfusion
description: Learn here all about selection of a date or multiple dates in the Calendar (SfCalendar) control and more.
platform: WinUI
control: SfCalendar
documentation: ug
---

# Selection in WinUI Calendar (SfCalendar)

You can change the selected date interactively by clicking on the specific date, or you can select programmatically. By default, `Calendar` control allows you to select single date at a time. 

If you want to restrict date selection or select multiple dates, set the [`SelectionMode`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectionMode) property value from the following values:

* **None** - Prevents from selecting a date.
* **Single** - Allows to select a single date.
* **Multiple** - Allows to select multiple dates.
* **Range** -  Allows to select range of dates.

## Single selection

You can select a single date interactively by clicking on a specific date or by programmatically using [`SelectedDate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectedDate) property. By default, value of `SelectedDate` property is **null** and `SelectedDates` collection is empty.

{% tabs %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendar sfCalendar= new SfCalendar();
sfCalendar.SelectedDate = new DateTimeOffset(new DateTime(2021, 01, 06));

{% endhighlight %}
{% endtabs %}

![date-selection-in-winui-calendar](Images/selection/date-selection-in-winui-calendar.png)

If the [`SelectedDates`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectedDates) collection is used instead of the `SelectedDate` property, the first date value in the `SelectedDates` collection is set as selected date, and this value changes upon selection by interaction.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="3 6 7" %}

<Grid>
    <Grid.DataContext>
        <local:ViewModel x:Name="viewModel" />
    </Grid.DataContext>
    <calendar:SfCalendar x:Name="calendar"
                        SelectionMode="Single" 
                        SelectedDates="{x:Bind viewModel.SelectedDates, Mode=TwoWay}"
                        />
</Grid>

{% endhighlight %}
{% highlight C# tabtitle="ViewModel.cs" %}

public class ViewModel
{
    private DateTimeOffsetCollection selectedDates;

    public DateTimeOffsetCollection SelectedDates
    {
        get { return selectedDates; }
        set { selectedDates = value; }
    }

    public ViewModel()
    {
        SelectedDates = new DateTimeOffsetCollection();

        SelectedDates.Add(new DateTimeOffset(new DateTime(2020, 03, 10)));
        SelectedDates.Add(new DateTimeOffset(new DateTime(2020, 03, 14)));
        SelectedDates.Add(new DateTimeOffset(new DateTime(2020, 03, 15)));
        SelectedDates.Add(new DateTimeOffset(new DateTime(2020, 03, 21)));
        SelectedDates.Add(new DateTimeOffset(new DateTime(2020, 03, 24)));
    }
}

{% endhighlight %}
{% endtabs %}

N> If the `SelectedDate` property is used to select a date and `SelectionMode` property value is **Single**. The`SelectedDates` collection property will have only `SelectedDate` property value. 

![multiple-dates-selection-in-winui-calendar](Images/selection/multiple-dates-selection-in-winui-calendar.png)

## Multiple selection

You can select one or more dates from a different month, year, decade or century by changing the [SelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectionMode) property value to `Multiple`. You can also get the selected dates collection from the [SelectedDates](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectedDates) property. By default, the value of `SelectedDate` property is **null** and `SelectedDates` collection is empty.

N> If the `SelectionMode` value is **None**, the `SelectedDates` property collection will be empty. 

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2" %}

<calendar:SfCalendar Name="sfCalendar" 
                     SelectionMode="Multiple" />

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendar sfCalendar= new SfCalendar();
sfCalendar.SelectionMode = CalendarSelectionMode.Multiple;

{% endhighlight %}
{% endtabs %}

N> If `SelectedDate` property is used to select a date and `SelectionMode` property value is **Multiple**. The`SelectedDates` collection property will have only `SelectedDate` property value. 

N> The `SelectedDate` property value will be same as the first date value in `SelectedDates` collection and changes with it.

![multiple-date-selection-in-winui-calendar](Images/getting-started/multiple-date-selection-in-winui-calendar.png)

## Select a date range

You can select a range of dates in `Calendar` control by changing the [SelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectionMode) property value to `Range`. You can also get the selected range of dates from the [SelectedRange](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectedDates) property. By default, the value of `SelectedDate` property is **null** and `SelectedDates` collection is empty.

N> The `SelectedDates` collection is empty and `SelectedDate` property value is **null**, when a date range is selected.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2" %}

<calendar:SfCalendar Name="sfCalendar" 
                     SelectionMode="Range" />

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendar sfCalendar= new SfCalendar();
sfCalendar.SelectionMode = CalendarSelectionMode.Range;

{% endhighlight %}
{% endtabs %}

![date-range-selection-in-winui-calendar](Images/getting-started/date-range-selection-in-winui-calendar.png)

N> Download demo application from [Github](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-examples/tree/main/Samples/Selection).

## Highlight today and selected date

You can update the background and border of the dates by highlighting the today and selected date with the [SelectionHighlightMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectionHighlightMode) property. The default value of `SelectionHighlightMode` property is **Outline**.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="2" %}

<calendar:SfCalendar x:Name="sfCalendar" 
                     SelectionHighlightMode="Filled"
                     />

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.SelectionHighlightMode = SelectionHighlightMode.Filled;

{% endhighlight %}
{% endtabs %}

![today-selecteddate-customization-in-winui-calendar](Images/selection/today-selecteddate-customization-in-winui-calendar.png)

N> Download demo application from [Github](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-examples/tree/main/Samples/Selection).

## Change shape of today and selected date

 You can customize the today and selected date cell shape using [SelectionShape](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectionShape) property to customize the shape of date cells border. The default value of `SelectionShape` property is **Circle**.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="2" %}

<calendar:SfCalendar x:Name="sfCalendar"
                     SelectionShape="Rectangle"
                     />

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.SelectionShape = SelectionShape.Rectangle;

{% endhighlight %}
{% endtabs %}

![change-shape-of-today-and-selected-date-in-winui-calendar](Images/selection/change-shape-of-today-and-selected-date-in-winui-calendar.png)

<<<<<<< .mine
N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-examples/blob/main/Samples/Selection).

=======
N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-examples/blob/main/Samples/Selection)

>>>>>>> .theirs
