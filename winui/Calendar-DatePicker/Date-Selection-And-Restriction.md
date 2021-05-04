---
layout: post
title: Date selection in WinUI Calendar Date Picker control | Syncfusion
description: Learn here all about date selection and restriction in Syncfusion WinUI Calendar Date Picker (SfCalendarDatePicker) control and more.
platform: WinUI
control: SfCalendarDatePicker
documentation: ug
---

# Date selection in WinUI Calendar Date Picker (SfCalendarDatePicker)

This section explains about the date selection in [WinUI Calendar Date Picker](https://www.syncfusion.com/winui-controls/calendar-datepicker) control and how to restrict or limit the users to select date within a range.

## Select the date 

You can set or change the selected date programmatically by using [SelectedDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_SelectedDate) property. By default, `SelectedDate` property value is `null`.

{% tabs %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker= new SfCalendarDatePicker();
sfCalendarDatePicker.SelectedDate = new DateTimeOffset(new DateTime(2021, 01, 06));

{% endhighlight %}
{% endtabs %}

![Calendar Date Picker displaying the selected date](Getting-Started_images/Selecteddate.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Restriction)

You can also change the selected date interactively by selecting a date from dropdown calendar or by entering the date value in editor of `Calendar Date Picker`. You can get the selected date from the `SelectedDate` property.


![Calendar Date Picker displaying selected value](Getting-Started_images/CalendarDatePicker.gif)

## Limit available dates

You can restrict the users from selecting a date within the particular range by specifying [MinDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_MinDate) and [MaxDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_MaxDate) properties. The default value of `MinDate` property is `1/1/1920` and `MaxDate` property is `12/31/2120`.

N> Dates that appears outside the minimum and maximum date range will be disabled (blackout).

{% tabs %}
{% highlight xaml %}

<calendar:Calendar x:Name="sfCalendarDatePicker"/>

{% endhighlight  %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.MinDate = new DateTimeOffset(new DateTime(2021, 01, 5));
sfCalendarDatePicker.MaxDate = new DateTimeOffset(new DateTime(2021, 01, 24));

{% endhighlight %}
{% endtabs %}

N> When `MinDisplayMode` property value is **Year** and `MinDate` value is **15/01/2021**, selecting the month of minimum date will set the starting date value from the minimum date, i.e., from *January 15, 2021*.

N> The `MinDate` property value should not be greater than the `MaxDate` property value.

![Calendar Date Picker restrict the date selection with particular range](Getting-Started_images/MinMaxdate.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Restriction)

## Block dates using BlackoutDates

You can block particular dates from the date selection, by adding respective dates in the [`BlackoutDates`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_BlackoutDates) collection property. The default value of `BlackoutDates` property is **null**.

{% tabs %}
{% highlight c# %}

public class ViewModel
{       
    public DateTimeOffsetCollection BlockedDates { get; set; }
    public ViewModel()
    {
        BlockedDates = new DateTimeOffsetCollection();
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 1, 17)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 1, 4)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 2, 5)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 2, 6)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 1, 9)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 3, 11)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 1, 13)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 4, 14)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 1, 18)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 5, 19)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 1, 26)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 6, 29)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 1, 31)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 1, 27)));
    }
}

{% endhighlight  %}
{% endtabs %}

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDatePicker BlackoutDates="{Binding BlockedDates}" 
                     x:Name="sfCalendarDatePicker">
    <calendar:SfCalendarDatePicker.DataContext>
        <local:ViewModel/>
    </calendar:SfCalendarDatePicker.DataContext>
</calendar:SfCalendarDatePicker>

{% endhighlight  %}
{% highlight C# %}

sfCalendarDatePicker.DataContext = new ViewModel();
sfCalendarDatePicker.BlackoutDates = (sfCalendarDatePicker.DataContext as ViewModel).BlockedDates;

{% endhighlight  %}
{% endtabs %}

![Calendar Date Picker blocks the particular dates from selection](Getting-Started_images/BlackoutDates.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/BlockedDates)

## Disable dates dynamically (All weekend days)

You can prevent the users from selecting any dates or days (example: all weekend days) by handling the [CalendarItemPrepared](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_CalendarItemPrepared) event and setting [ItemInfo.IsBlackout](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.CalendarItemPreparedEventArgs.html#Syncfusion_UI_Xaml_Calendar_CalendarItemPreparedEventArgs_ItemInfo) property value as **true** for those specific dates.

N> You can also change the text to be displayed for specific days or dates in dropdown calendar using `ItemInfo.DisplayText` property.  

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDatePicker x:Name="sfCalendarDatePicker"
                               CalendarItemPrepared="SfCalendarDatePicker_CalendarItemPrepared"/>

{% endhighlight %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.CalendarItemPrepared += SfCalendarDatePicker_CalendarItemPrepared;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows:

{% tabs %}
{% highlight C# %}

private void SfCalendarDatePicker_CalendarItemPrepared(object sender, CalendarItemPreparedEventArgs e)
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

![Calendar Date Picker restrict the weekend dates from selection](Getting-Started_images/blockweekend.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/BlockedDates)

You can also change the text to be displayed for specific days or dates in `Calendar Date Picker` using [ItemInfo.DisplayText](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.CalendarItemInfo.html#Syncfusion_UI_Xaml_Calendar_CalendarItemInfo_DisplayText) property. 

{% tabs %}
{% highlight C# %}

private void SfCalendarDatePicker_CalendarItemPrepared(object sender, CalendarItemPreparedEventArgs e)
{
    //Block all weekend days
    if (e.ItemInfo.ItemType == CalendarItemType.Day &&
        (e.ItemInfo.Date.DayOfWeek == DayOfWeek.Saturday ||
        e.ItemInfo.Date.DayOfWeek == DayOfWeek.Sunday))
    {
        e.ItemInfo.IsBlackout = true;
        e.ItemInfo.DisplayText = "X";
    }
}

{% endhighlight %}
{% endtabs %}

![Calendar Date Picker change display text for dates](Selection-And-Restriction_images/DisplayText_event.png)

## Highlight today and selected dates

You can highlight the today and selected date in dropdown calendar using [SelectionHighlightMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_SelectionHighlightMode) property to update the background and border of the dates. The default value of `SelectionHighlightMode` property is **Outline**.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendarDatePicker SelectionHighlightMode="Filled"
                     x:Name="sfCalendarDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.SelectionHighlightMode = SelectionHighlightMode.Filled;

{% endhighlight %}
{% endtabs %}

![Highlight today and selected dates in WinUI Calendar](Selection-And-Restriction_images/selectionHightlightMode.png)

## Change shape of today and selected date

 You can customize the today and selected date cell shape in dropdown calendar using [SelectionShape](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_SelectionShape) property to customize the shape of date cells border. The default value of `SelectionShape` property is **Rectangle**.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendarDatePicker SelectionShape="Circle"
                     x:Name="sfCalendarDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.SelectionShape = SelectionShape.Circle;

{% endhighlight %}
{% endtabs %}

![Calendar highlights the today and selected date](Selection-And-Restriction_images/selectionshape.png)

