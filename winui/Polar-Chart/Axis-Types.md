---
layout: post
title:  Axis types in WinUI Chart control | Syncfusion
description: Learn here all about the axis types and its features in  Syncfusion® WinUI Chart (SfPolarChart) control.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Types of Axis in WinUI Chart (SfPolarChart) 

Polar chart supports the following types of chart axis.

* CategoryAxis
* NumericalAxis
* DateTimeAxis
* LogarithmicAxis

## Category Axis

The [CategoryAxis](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.CategoryAxis.html) is an indexed based axis that plots values based on the index of the data point collection. The points are equally spaced here.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>

    <chart:SfPolarChart.PrimaryAxis>
        <chart:CategoryAxis/>
    </chart:SfPolarChart.PrimaryAxis>

    <chart:SfPolarChart.SecondaryAxis>
        <chart:NumericalAxis/>
    </chart:SfPolarChart.SecondaryAxis>
...

</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.PrimaryAxis = new CategoryAxis();
chart.SecondaryAxis = new NumericalAxis();
...

{% endhighlight %}

{% endtabs %}

![CategoryAxis support in WinUI Chart](Axis_Images/WinUI_Chart_CategoryAxis.png)

## Numerical Axis

The [NumericalAxis](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalAxis.html) is used to plot the numerical values to the chart. [NumericalAxis](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalAxis.html) can be defined for both [PrimaryAxis](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPolarChart.html#Syncfusion_UI_Xaml_Charts_SfPolarChart_PrimaryAxis) and [SecondaryAxis](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPolarChart.html#Syncfusion_UI_Xaml_Charts_SfPolarChart_SecondaryAxis).

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>

    <chart:SfPolarChart.PrimaryAxis>
        <chart:NumericalAxis/>
    </chart:SfPolarChart.PrimaryAxis>
    
    <chart:SfPolarChart.SecondaryAxis>
        <chart:NumericalAxis/>
    </chart:SfPolarChart.SecondaryAxis>
    ...
    
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
...
chart.PrimaryAxis = new NumericalAxis();
chart.SecondaryAxis = new NumericalAxis();
...

{% endhighlight %}

{% endtabs %}

![Numerical Axis support in WinUI Chart](Axis_Images/WinUI_Chart_NumericalAxis.png)

### Customizing the range

[Maximum](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_Maximum) and [Minimum](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_Minimum) properties of axis is used for setting the maximum and minimum value of the axis range respectively.

N> If  minimum or maximum value is set, the other value is calculated by default internally.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    <chart:SfPolarChart.SecondaryAxis>
        <chart:NumericalAxis Minimum="10"
			     Maximum="90"
			     Interval="20" />
    </chart:SfPolarChart.SecondaryAxis>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
...
chart.SecondaryAxis = new NumericalAxis()
{
    Maximum = 90,
    Minimum = 10,
    Interval = 20,
};
...

{% endhighlight %}

{% endtabs %}

![Numerical axis range in WinUI Chart](Axis_Images/WinUI_Chart_NumericalAxis_AxisRange.png)

## DateTime Axis

The [DateTimeAxis](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html) is used to plot the chart with `DateTime` values.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
            
    <chart:SfPolarChart.PrimaryAxis>
        <chart:DateTimeAxis Interval="1"
			    IntervalType="Months">
        <chart:DateTimeAxis.LabelStyle>
            <chart:LabelStyle LabelFormat="MMM/dd" />
        </chart:DateTimeAxis.LabelStyle>
    </chart:DateTimeAxis>
    </chart:SfPolarChart.PrimaryAxis>
            
    <chart:SfPolarChart.SecondaryAxis>
        <chart:NumericalAxis/>
    </chart:SfPolarChart.SecondaryAxis>
    ...

</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();

chart.PrimaryAxis = new DateTimeAxis()
{
    Interval = 1,
    IntervalType = DateTimeIntervalType.Months,
    LabelStyle = new LabelStyle() { LabelFormat="MMM/dd" },
};

chart.SecondaryAxis = new NumericalAxis();
...

{% endhighlight %}

{% endtabs %}

![DateTimeAxis support in WinUI Chart](Axis_Images/WinUI_Chart_DateTimeAxis.png)

## Logarithmic Axis

The Logarithmic axis uses a logarithmic scale, and it is very useful in visualizing data when the given data range has a big difference. It can be defined for both PrimaryAxis and SecondaryAxis.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
. . .
<chart:SfPolarChart.SecondaryAxis>
    <chart:LogarithmicAxis />
</chart:SfPolarChart.SecondaryAxis>

</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
. . .
LogarithmicAxis secondaryAxis = new LogarithmicAxis()
chart.SecondaryAxis.Add(secondaryAxis);

{% endhighlight %}

{% endtabs %}

![LogarithmicAxis in WinUI Chart](Axis_Images/WinUI_Chart_LogarithmicAxis.png)

### Interval

The Axis interval can be customized using the [Interval]() property of the axis. By default, the interval is calculated based on the minimum and maximum values of the provided data, with a default value of `1`.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
. . .
<chart:SfPolarChart.SecondaryAxis>
    <chart:LogarithmicAxis Interval="10" />
</chart:SfPolarChart.SecondaryAxis>

</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
. . .
LogarithmicAxis secondaryAxis = new LogarithmicAxis()
{
    Interval = 10,
};

chart.SecondaryAxis.Add(secondaryAxis);

{% endhighlight %}
{% endtabs %}

### Customizing the Range

The range of the logarithmic axis can be customized using the [Minimum]() and [Maximum]() properties of the LogarithmicAxis. By default, the range is automatically calculated to align with the provided data.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
. . .
<chart:SfPolarChart.SecondaryAxis>
    <chart:LogarithmicAxis Minimum="100" Maximum="10000" />
</chart:SfPolarChart.SecondaryAxis>

</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
. . .
LogarithmicAxis secondaryAxis = new LogarithmicAxis()
{
    Minimum = 100,
    Maximum = 10000,
};

chart.SecondaryAxis.Add(secondaryAxis);

{% endhighlight %}
{% endtabs %}

### Customizing the Logarithmic base

The logarithmic axis base can be customized using the [LogarithmicBase]() property. The default base value is `10`.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
. . .
<chart:SfPolarChart.SecondaryAxis>
    <chart:LogarithmicAxis LogarithmicBase="2" />
</chart:SfPolarChart.SecondaryAxis>

</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
. . .
LogarithmicAxis secondaryAxis = new LogarithmicAxis()
{
    LogarithmicBase = 2,
};

chart.SecondaryAxis.Add(secondaryAxis);

{% endhighlight %}
{% endtabs %}

![LogarithmicAxis base customization support in WinUI Chart](Axis_Images/WinUI_Chart_LogarithmicAxis_LogarithmicBase.png)

## Events
### ActualRangeChanged

The [ActualRangeChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ActualRangeChanged) event is triggered when the actual range of the axis is changed. The argument contains the following information:

* [ActualMinimum](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ActualRangeChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_ActualRangeChangedEventArgs_ActualMinimum) - used to get the actual minimum value of the axis.
* [ActualMaximum](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ActualRangeChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_ActualRangeChangedEventArgs_ActualMaximum) - used to get the actual maximum value of the axis.

### LabelCreated

The [LabelCreated](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelCreated) event is triggered when the axis label is created. The argument contains the following information:

* [Label](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxisLabelEventArgs.html#Syncfusion_UI_Xaml_Charts_ChartAxisLabelEventArgs_Label) - Used to get or set the text of axis label.
* [Position](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxisLabelEventArgs.html#Syncfusion_UI_Xaml_Charts_ChartAxisLabelEventArgs_Position) - Used to get the position of label.
* [LabelStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxisLabelEventArgs.html#Syncfusion_UI_Xaml_Charts_ChartAxisLabelEventArgs_LabelStyle) - Used to customize the appearance of axis labels.
