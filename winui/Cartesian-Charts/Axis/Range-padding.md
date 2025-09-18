---
layout: post
title: Range Padding in WinUI Chart Control | Syncfusion
description: Learn about axis range padding and its types of features in the Syncfusion® WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: range padding in WinUI chart, WinUI SfCartesianChart range padding, WinUI chart range padding customization, Syncfusion WinUI chart range padding, WinUI SfCartesianChart range padding configuration.
---

# Range Padding in WinUI Chart (SfCartesianChart)

Range padding is used to apply the minimum and maximum extremes of the chart axis range by using the `RangePadding` property. The [NumericalAxis](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalAxis.html) and [DateTimeAxis](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html) have a [RangePadding](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#Syncfusion_UI_Xaml_Charts_DateTimeAxis_RangePadding) property that can be used to add padding to the range of the chart axis.

## Numerical Range Padding

The [RangePadding](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) is used to set the numeric range for the axis. 

The following types are available for [NumericalAxis](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalAxis.html) range padding:

* [Additional](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalPadding.html#Syncfusion_UI_Xaml_Charts_NumericalPadding_Additional) - An additional interval is added to the visible start and end range.
* [None](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalPadding.html#Syncfusion_UI_Xaml_Charts_NumericalPadding_None) - Sets the visible range to the exact minimum and maximum values of the items source.
* [Normal](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalPadding.html#Syncfusion_UI_Xaml_Charts_NumericalPadding_Normal) - The visible range is the actual range calculated from the given items source and series types.
* [Auto](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalPadding.html#Syncfusion_UI_Xaml_Charts_NumericalPadding_Auto) - Automatically chosen based on the orientation of the axis.
* [Round](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalPadding.html#Syncfusion_UI_Xaml_Charts_NumericalPadding_Round) - The visible start and end range are rounded to the nearest interval value.
* [RoundStart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalPadding.html#Syncfusion_UI_Xaml_Charts_NumericalPadding_RoundStart) - The visible start range is rounded to the nearest interval value.
* [RoundEnd](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalPadding.html#Syncfusion_UI_Xaml_Charts_NumericalPadding_RoundEnd) - The visible end range is rounded to the nearest interval value.
* [PrependInterval](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalPadding.html#Syncfusion_UI_Xaml_Charts_NumericalPadding_PrependInterval) - The visible start range is prepended with an additional interval.
* [AppendInterval](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalPadding.html#Syncfusion_UI_Xaml_Charts_NumericalPadding_AppendInterval) - The visible end range is appended with an additional interval.

By default, the [RangePadding](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) value for [XAxes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_XAxes) is [Auto](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalPadding.html#Syncfusion_UI_Xaml_Charts_NumericalPadding_Auto) and for [YAxes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_YAxes) it is [Round](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalPadding.html#Syncfusion_UI_Xaml_Charts_NumericalPadding_Round).

**Additional**

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.XAxes>
        <chart:NumericalAxis RangePadding="Additional"/>
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes>
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

NumericalAxis primaryAxis = new NumericalAxis()
{
    RangePadding = NumericalPadding.Additional,
};
chart.XAxes.Add(primaryAxis);

chart.YAxes.Add(new NumericalAxis());
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![NumericalAxis range padding support in WinUI Chart](Axis_Images/winui_chart_axis_numerical-range-padding_additional.png)

**None**

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.XAxes>
        <chart:NumericalAxis RangePadding="None"/>
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes>
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

NumericalAxis primaryAxis = new NumericalAxis()
{
    RangePadding = NumericalPadding.None,
};
chart.XAxes.Add(primaryAxis);

chart.YAxes.Add(new NumericalAxis());
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![NumericalAxis range padding none in WinUI Chart](Axis_Images/winui_chart_axis_numerical-range-padding_none.png)

**Round**

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.XAxes>
        <chart:NumericalAxis  RangePadding="Round"/>
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes>
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

NumericalAxis primaryAxis = new NumericalAxis()
{
    RangePadding = NumericalPadding.Round,
};
chart.XAxes.Add(primaryAxis);

chart.YAxes.Add(new NumericalAxis());
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![NumericalAxis range padding round in WinUI Chart](Axis_Images/winui_chart_axis_numerical-range-padding_round.png)

## DateTime Range Padding

The [RangePadding](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#Syncfusion_UI_Xaml_Charts_DateTimeAxis_RangePadding) types available in the [DateTimeAxis](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html) are:

* [Auto](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeRangePadding.html#Syncfusion_UI_Xaml_Charts_DateTimeRangePadding_Auto) - Automatically chosen based on the orientation of the axis.
* [Additional](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeRangePadding.html#Syncfusion_UI_Xaml_Charts_DateTimeRangePadding_Additional) - An additional interval is added to the visible start and end range.
* [None](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeRangePadding.html#Syncfusion_UI_Xaml_Charts_DateTimeRangePadding_None) - Sets the visible range to the exact minimum and maximum values of the items source.
* [Round](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeRangePadding.html#Syncfusion_UI_Xaml_Charts_DateTimeRangePadding_Round) - The visible start and end range are rounded to the nearest interval value.
* [RoundStart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeRangePadding.html#Syncfusion_UI_Xaml_Charts_DateTimeRangePadding_RoundStart) - The visible start range is rounded to the nearest interval value.
* [RoundEnd](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeRangePadding.html#Syncfusion_UI_Xaml_Charts_DateTimeRangePadding_RoundEnd) - The visible end range is rounded to the nearest interval value.
* [PrependInterval](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeRangePadding.html#Syncfusion_UI_Xaml_Charts_DateTimeRangePadding_PrependInterval) - The visible start range is prepended with an additional interval.
* [AppendInterval](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeRangePadding.html#Syncfusion_UI_Xaml_Charts_DateTimeRangePadding_AppendInterval) - The visible start range is appended with an additional interval.

**Additional**

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.XAxes>
        <chart:DateTimeAxis RangePadding="Additional">
        <chart:DateTimeAxis.LabelStyle>
            <chart:LabelStyle LabelFormat="MMM-yy" />
        </chart:DateTimeAxis.LabelStyle>
    </chart:DateTimeAxis>
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes>
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

DateTimeAxis primaryAxis = new DateTimeAxis()
{
    RangePadding = DateTimeRangePadding.Additional,
    LabelStyle = new LabelStyle() { LabelFormat= "MMM-yy" }
};
chart.XAxes.Add(primaryAxis);

chart.YAxes.Add(new NumericalAxis());
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![DateTimeAxis range padding support in WinUI Chart](Axis_Images/winui_chart_axis_datetime-range-padding_additional.png)

**None**

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.XAxes>
        <chart:DateTimeAxis RangePadding="None">
        <chart:DateTimeAxis.LabelStyle>
            <chart:LabelStyle LabelFormat="MMM-yy" />
        </chart:DateTimeAxis.LabelStyle>
    </chart:DateTimeAxis>
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes>
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

DateTimeAxis primaryAxis = new DateTimeAxis()
{
    RangePadding = DateTimeRangePadding.None,
    LabelStyle = new LabelStyle() { LabelFormat= "MMM-yy" }
};
chart.XAxes.Add(primaryAxis);

chart.YAxes.Add(new NumericalAxis());
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![DateTimeAxis range padding none in WinUI Chart](Axis_Images/winui_chart_axis_datetime-range-padding_none.png)

**Round**

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.XAxes>
        <chart:DateTimeAxis RangePadding="Round" LabelFormat="MMM-yy"/>
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes>
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

DateTimeAxis primaryAxis = new DateTimeAxis()
{
    RangePadding = DateTimeRangePadding.Round,
    LabelFormat = "MMM-yy"
};
chart.XAxes.Add(primaryAxis);

chart.YAxes.Add(new NumericalAxis());
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![DateTimeAxis range padding round in WinUI Chart](Axis_Images/winui_chart_axis_datetime-range-padding_round.png)
