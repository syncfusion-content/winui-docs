---
layout: post
title: Selection in WinUI Calendar control | Syncfusion
description: Learn here all about selection of a date or multiple dates in the Calendar (SfCalendar) control and more.
platform: WinUI
control: SfCalendar
documentation: ug
---

# Selection in WinUI Calendar (SfCalendar)

You can change the selected date interactively by clicking on the specific date or you can select programmatically. By default, `Calendar` control allows you to select single date at a time. 

If you want to restrict date selection or select multiple dates, set [`SelectionMode`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectionMode) property value from below values.

* **None** - Prevents from selecting a date.
* **Single** - Allows to select a single date.
* **Multiple** - Allows to select multiple dates.
* **Range** -  Allows to select range of dates.

## Single selection

You can select a single date interactively by clicking on specific date or by programmatically using [`SelectedDate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectedDate) property.By default, value of `SelectedDate` property is **null** and `SelectedDates` collection is empty.

{% tabs %}
{% highlight C# %}

SfCalendar sfCalendar= new SfCalendar();
sfCalendar.SelectedDate = new DateTimeOffset(new DateTime(2021, 01, 06));

{% endhighlight %}
{% endtabs %}

![Calendar displaying the selected date](Getting-Started_images/Selecteddate.png)

If [`SelectedDates`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectedDates) collection is used instead of `SelectedDate` property, the first date value in `SelectedDates` collection will be set as selected date and the same value changes upon selection by interaction.

{% tabs %}
{% highlight xaml %}
<Page.DataContext>
    <local:ViewModel x:Name="viewModel" />
</Page.DataContext>
<Grid>
    <calendar:SfCalendar x:Name="calendar"
                        SelectionMode="Single" 
                        SelectedDates="{x:Bind viewModel.SelectedDates, Mode=TwoWay}"
                        />
</Grid>

{% endhighlight %}
{% highlight C# %}

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

N> If `SelectedDate` property is used to select a date when `SelectionMode` property value is **Single**. The`SelectedDates` collection property will have only `SelectedDate` property value. 

![Calendar displaying the selected date from SelectedDates collection](Selection_images/single-selection-by-collection.png)

## Multiple Selection

You can select one or multiple dates from different month or year or decade or century, by changing the [SelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectionMode) property value to `Multiple`. You can get the selected dates collection from the [SelectedDates](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectedDates) property. By default,the value of `SelectedDate` property is **null** and `SelectedDates` collection is empty.

N> `SelectedDates` property collection will be empty, if the `SelectionMode` value is **None**. 

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

N> If `SelectedDate` property is used to select a date when `SelectionMode` property value is **Multiple**. The`SelectedDates` collection property will have only `SelectedDate` property value. 

N> The `SelectedDate` property value will be same as the first date value in `SelectedDates` collection and changes with it.

![Calendar allows you to select multiple dates](Getting-Started_images/multipledate_selection.png)

## Select a date range

You can select a range of dates in `Calendar` control by changing the [SelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectionMode) property value to `Range`. You can get the selected range of dates from the [SelectedRange](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectedDates) property. By default, the value of `SelectedDate` property is **null** and `SelectedDates` collection is empty.

N> The `SelectedDates` collection will be empty and `SelectedDate` property value will be **null** when a date range is selected.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar Name="sfCalendar" 
                     SelectionMode="Range" />

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar= new SfCalendar();
sfCalendar.SelectionMode = CalendarSelectionMode.Range;

{% endhighlight %}
{% endtabs %}

![Date range selection in WinUI Calendar](Getting-Started_images/date-range-selection.png)

## Highlight today and selected dates

You can highlight the today and selected date using [SelectionHighlightMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectionHighlightMode) property to update the background and border of the dates. The default value of `SelectionHighlightMode` property is **Outline**.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendar SelectionHighlightMode="Filled"
                     x:Name="sfCalendar"/>

{% endhighlight %}
{% highlight c# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.SelectionHighlightMode = SelectionHighlightMode.Filled;

{% endhighlight %}
{% endtabs %}

![Highlight today and selected dates in WinUI Calendar](Selection_images/selectionhighlightmode.png)

## Change shape of today and selected date

 You can customize the today and selected date cell shape using [SelectionShape](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectionShape) property to customize the shape of date cells border. The default value of `SelectionShape` property is **Rectangle**.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendar SelectionShape="Circle"
                     x:Name="sfCalendar"/>

{% endhighlight %}
{% highlight c# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.SelectionShape = SelectionShape.Circle;

{% endhighlight %}
{% endtabs %}

![Calendar highlights the today and selected date](Selection_images/selectionshape.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-examples/blob/main/Samples/Selection)

