---
layout: post
title: Selection in WinUI Calendar control | Syncfusion
description: This section describes about selection of a date or multiple dates in the Calendar (SfCalendar) control in WinUI applications.
platform: WinUI
control: SfCalendar
documentation: ug
---

# Selection in WinUI Calendar

You can change the selected date interactively by clicking on the specific date or you can select programmatically. By default, `Calendar` control allows you to select single date at a time. 

You can change the selection mode by setting the `SelectionMode` property with below values. 

* **None** - Prevents from selecting a date.
* **Single** - Allows to select a single date.
* **Multiple** - Allows to select multiple dates.
* **Range** -  Allows to select range of dates.

## Single selection

You can select a single date interactively by clicking on specific date or by programmatically using [`SelectedDate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectedDate) property. The default value of `SelectedDate` property is **null**.

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

![Calendar displaying the selected date from SelectedDates collection](Selection_images/single-selection-by-collection.png)

N> Based on the `MinDisplayMode` property value, the first date of selected month or selected year or selected decade or selected century is set as selected date. 

## Multiple Selection

You can select one or multiple dates from different month or year or decade or century, by changing the [SelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectionMode) property value to `Multiple`. You can get the selected dates collection from the [SelectedDates](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectedDates) property. The value of `SelectedDate` property is **null**.

N> `SelectedDates` property collection will be empty, if the `SelectionMode` value is **None** and the dates are selected interactively. 

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

N> Based on the `MinDisplayMode` property value, the first date of selected months or selected years or selected decades or selected centuries are updated in `SelectedDates` collection. 

## Select a date range

You can select a range of dates in `Calendar` control by changing the [SelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectionMode) property value to `Range`. You can get the selected dates collection from the [SelectedDates](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectedDates) property. The value of `SelectedDate` property is **null**.

N> `SelectedDates` property collection will be empty, if the `SelectionMode` value is **None** and the dates are selected interactively. 

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

N> Based on the `MinDisplayMode` property value, the first date of months or years or decades or centuries in selected range are updated in `SelectedDates` collection. 

## Today and selected date highlighting

You can highlight the today and selected date with rectangle and circle shapes. You can also customize the selected date cell shape using [SelectionShape](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectionShape) property and use the [SelectionHighlightMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectionHighlightMode) property to update the background of the selected date. The default value of `SelectionShape` property is **Rectangle** and `SelectionHighlightMode` property is **Outline**.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendar SelectionHighlightMode="Filled"
                     SelectionShape="Circle"
                     x:Name="sfCalendar"/>

{% endhighlight %}
{% highlight c# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.SelectionHighlightMode = SelectionHighlightMode.Filled;
sfCalendar.SelectionShape = SelectionShape.Circle;

{% endhighlight %}
{% endtabs %}

![Calendar highlights the today and selected date](Selection_images/selectionshape-selectionhighlight.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-examples/blob/main/Samples/Selection)