---
layout: post
title: Restrict selection in WinUI CalendarDateRangePicker control|Syncfusion
description: This section describes about how to restrict the date range selection in Calendar DateRangePicker control.
platform: WinUI
control: SfCalendarDateRangePicker
documentation: ug
---

# Restrict or limit date range selection in Calendar DateRangePicker

## Limit date range

You can allow the users to select a date range within the particular range by specifying `MinDate` and `MaxDate` properties. The default value of `MinDate` property is `1/1/1920 12:00:00 AM +00:00` and `MaxDate` property is `12/31/2120 11:59:59 PM +00:00`.

N> Dates that appear outside minimum and maximum date rage will be disabled (blackout).

{% tabs %}
{% highlight xaml %}

<calendar:Calendar x:Name="sfCalendarDateRangePicker"/>

{% endhighlight  %}
{% highlight C# %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.MinDate = new DateTimeOffset(new DateTime(2021, 03, 06));
sfCalendarDateRangePicker.MaxDate = new DateTimeOffset(new DateTime(2021, 03, 24));

{% endhighlight %}
{% endtabs %}

![Calendar DateRangePicker restrict the date selection with particular range](Getting-Started_images/MinMaxdate.png)

N> The `MinDate` property value should not be greater than the `MaxDate` property value.

## Block dates using BlackoutDates

If you want to block particular dates from the date selection, add those dates into the `BlackoutDates` collection. You can add more block out dates to the `BlackoutDates` collection. The default value of `BlackoutDates` property is `null`.

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
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 3, 12)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 3, 23)));
        BlockedDates.Add(new DateTimeOffset(new DateTime(2021, 3, 26)));
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

<calendar:SfCalendarDateRangePicker BlackoutDates="{Binding BlockedDates}" 
                     x:Name="sfCalendarDateRangePicker">
    <calendar:SfCalendarDateRangePicker.DataContext>
        <local:ViewModel/>
    </calendar:SfCalendarDateRangePicker.DataContext>
</calendar:SfCalendarDateRangePicker>

{% endhighlight  %}
{% highlight C# %}

sfCalendarDateRangePicker.DataContext = new ViewModel();
sfCalendarDateRangePicker.BlackoutDates = (sfCalendarDateRangePicker.DataContext as ViewModel).BlockedDates;

{% endhighlight  %}
{% endtabs %}

![Calendar DateRangePicker blocks the particular dates in dropdown calendar](Getting-Started_images/BlackoutDates.png)

## Disable/block all weekends

You can prevent the users from selecting weekend days or any other dates by handling the `ItemPrepared` event and setting `ItemInfo.IsBlackout` property value as `true` for those specific dates.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDateRangePicker x:Name="sfCalendarDateRangePicker"
                                    ItemPrepared="SfCalendarDateRangePicker_ItemPrepared"/>

{% endhighlight %}
{% highlight C# %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.ItemPrepared += SfCalendarDateRangePicker_ItemPrepared;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows:

{% tabs %}
{% highlight C# %}

private void SfCalendarDateRangePicker_ItemPrepared(object sender, ItemPreparedEventArgs e)
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

![Calendar DateRangePicker restrict the weekend dates from selection](Getting-Started_images/blockweekend.png)

N> Blackout dates will not be added in `SelectedRange` property if blackout dates is highlighted in dropdown selected range.

## Limit duration of selected range

You can limit the duration of selected range in `Calendar DateRangePicker` value by using `MinDatesCountInRange` and `MaxDatesCountInRange` properties.

{% tabs %}
{% highlight C# %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.MaxDatesCountInRange = 10;
sfCalendarDateRangePicker.MinDatesCountInRange = 5;

{% endhighlight  %}
{% endtabs %}

![Calendar DateRangePicker with end range value restriction](Getting-Started_images/Selection-By-DayCount.png)

