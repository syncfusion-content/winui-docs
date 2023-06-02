---
layout: post
title: AutoScrollingDelta feature in WinUI Chart control | Syncfusion
description: Learn here all about axis AutoScrollingDelta feature in Syncfusion WinUI Chart (SfCartesianChart) control and more.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Auto Scrolling in WinUI Chart (SfCartesianChart)

Axis provides support to auto scrolling the live data added in the chart with specific range of data visible at start or end.

## AutoScrollingDelta

The [AutoScrollingDelta]() property is used to set the specified range of data visible in the chart. It always shows the recently added data points at the end, and the scrolling will be reset to the end of the range whenever a new point is added. The default value of AutoScrollingDelta is `double.NaN`.

By adding [ChartZoomPanBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior__ctor) to the chart, you can scroll to see the previous data points using [EnablePanning](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior_EnablePanning) property.


{% tabs %}

{% highlight xaml %}

    <chart:SfCartesianChart  x:Name="chart" >
    ...
    <chart:SfCartesianChart.XAxes>
        <chart:NumericalAxis   AutoScrollingDelta="3"  />
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes>

    <chart:SfCartesianChart.ZoomPanBehavior>
        <chart:ChartZoomPanBehavior  EnablePanning="True"  />
    </chart:SfCartesianChart.ZoomPanBehavior>
    ...
    </chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

    SfCartesianChart chart = new SfCartesianChart();
    ...
    NumericalAxis numericalAxis = new NumericalAxis()
    {
        AutoScrollingDelta = 3,
        AutoScrollingMode = ChartAutoScrollingMode.Start
    };

    NumericalAxis numericalAxis1 = new NumericalAxis() { };

    ChartZoomPanBehavior zoomPanBehavior = new ChartZoomPanBehavior()
    {
        EnablePanning = true,
    };

    chart.XAxes.Add(numericalAxis);
    chart.YAxes.Add(numericalAxis1);
    chart.ZoomPanBehavior = zoomPanBehavior;
    ...
    this.Content = chart;
{% endhighlight %}

{% endtabs %}

## AutoScrollingMode

[AutoScrollingMode]() property can be used to determine whether the axis should be scrolled from start position or end position. The default value of AutoScrollingMode is `ChartAutoScrollingMode.End`.

{% tabs %}

{% highlight xaml %}

    <chart:SfCartesianChart  x:Name="chart" >
    ...
    <chart:SfCartesianChart.XAxes>
        <chart:NumericalAxis   AutoScrollingDelta="3" 
                               AutoScrollingMode="Start" />
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes>

    <chart:SfCartesianChart.ZoomPanBehavior>
        <chart:ChartZoomPanBehavior  EnablePanning="True"  />
    </chart:SfCartesianChart.ZoomPanBehavior>
    ...
    </chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

    SfCartesianChart chart = new SfCartesianChart();
    ...
    NumericalAxis numericalAxis = new NumericalAxis()
    {
        AutoScrollingDelta = 3,
    };

    NumericalAxis numericalAxis1 = new NumericalAxis() { };

    ChartZoomPanBehavior zoomPanBehavior = new ChartZoomPanBehavior()
    {
        EnablePanning = true,
    };

    chart.XAxes.Add(numericalAxis);
    chart.YAxes.Add(numericalAxis1);
    chart.ZoomPanBehavior = zoomPanBehavior;
    ...
    this.Content = chart;
{% endhighlight %}

{% endtabs %}


## AutoScrollingDeltaType

In [DateTimeAxis](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html), you can apply auto scrolling delta value in [Auto](), [Years](), [Months](), [Days](), [Hours](), [Minutes](), [Seconds]() and [Milliseconds]() by setting AutoScrollingDeltaType property. The default value of this property is `DateTimeIntervalType.Auto`, and the delta will be calculated automatically based on range.

{% tabs %}

{% highlight xaml %}

    <chart:SfCartesianChart  x:Name="chart" >
    ...
    <chart:SfCartesianChart.XAxes>
        <chart:DateTimeAxis 
                        AutoScrollingDelta="4"  
                        AutoScrollingDeltaType="Months" >
            <chart:DateTimeAxis.LabelStyle>
                <chart:LabelStyle LabelFormat="MMM-yy" />
            </chart:DateTimeAxis.LabelStyle>
        </chart:DateTimeAxis>
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes>

    <chart:SfCartesianChart.ZoomPanBehavior>
        <chart:ChartZoomPanBehavior  EnablePanning="True"  />
    </chart:SfCartesianChart.ZoomPanBehavior>
    ...
    </chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

    SfCartesianChart chart = new SfCartesianChart();
    ...
    DateTimeAxis primaryAxis = new DateTimeAxis()
    {
        AutoScrollingDelta = 4,
        AutoScrollingDeltaType = DateTimeIntervalType.Months,
        LabelStyle = new LabelStyle()
        {
            LabelFormat = "MMM-yy"
        }
    };

    NumericalAxis numericalAxis1 = new NumericalAxis() { };

    ChartZoomPanBehavior zoomPanBehavior = new ChartZoomPanBehavior()
    {
        EnablePanning = true,
    };

    chart.XAxes.Add(primaryAxis);
    chart.YAxes.Add(numericalAxis1);
    chart.ZoomPanBehavior = zoomPanBehavior;
    ...
    this.Content = chart;
{% endhighlight %}

{% endtabs %}



