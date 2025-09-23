---
layout: post
title: AutoScrollingDelta Feature in WinUI Chart Control | Syncfusion
description: Learn all about the axis AutoScrollingDelta feature in Syncfusion® WinUI Chart (SfCartesianChart) control and more.
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: auto scrolling in WinUI chart, WinUI SfCartesianChart auto scrolling, WinUI chart auto scrolling customization, Syncfusion WinUI chart auto scrolling, WinUI SfCartesianChart auto scrolling settings.
---

# Auto Scrolling in WinUI Chart (SfCartesianChart)

The axis supports auto-scrolling live data added to the chart, with a specific range of data visible either at the start or the end.

## AutoScrollingDelta

The [AutoScrollingDelta](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_AutoScrollingDelta) property is used to set the specified range of data visible in the chart. It always shows the most recently added data points at the end, and the scrolling is reset to the end of the range whenever a new point is added. The default value of AutoScrollingDelta is `double.NaN`.

By adding the [ChartZoomPanBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior__ctor) to the chart, you can scroll to see the previous data points using the [EnablePanning](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior_EnablePanning) property.

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

![AutoScrollingDelta support WinUI Chart](Axis_Images/winui_chart_axis_auto-scrolling-delta.png)

## AutoScrollingMode

The [AutoScrollingMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_AutoScrollingMode) property determines whether the axis should be scrolled from the start or the end positions. The default value of AutoScrollingMode is `ChartAutoScrollingMode.End`.

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

![AutoScrollingMode support WinUI Chart](Axis_Images/winui_chart_axis_auto-scrolling-mode.png)

## AutoScrollingDeltaType

In the [DateTimeAxis](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html), apply auto-scrolling delta values in [Auto](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeIntervalType.html#Syncfusion_UI_Xaml_Charts_DateTimeIntervalType_Auto), [Years](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeIntervalType.html#Syncfusion_UI_Xaml_Charts_DateTimeIntervalType_Years), [Months](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeIntervalType.html#Syncfusion_UI_Xaml_Charts_DateTimeIntervalType_Months), [Days](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeIntervalType.html#Syncfusion_UI_Xaml_Charts_DateTimeIntervalType_Days), [Hours](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeIntervalType.html#Syncfusion_UI_Xaml_Charts_DateTimeIntervalType_Hours), [Minutes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeIntervalType.html#Syncfusion_UI_Xaml_Charts_DateTimeIntervalType_Minutes), [Seconds](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeIntervalType.html#Syncfusion_UI_Xaml_Charts_DateTimeIntervalType_Seconds), and [Milliseconds](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DateTimeIntervalType.html#Syncfusion_UI_Xaml_Charts_DateTimeIntervalType_Milliseconds) by setting the AutoScrollingDeltaType property. The default value of this property is `DateTimeIntervalType.Auto`, and the delta is calculated automatically based on the range.

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

![DateTimeAxis AutoScrollingDetlaType support WinUI Chart](Axis_Images/winui_chart_datetime-axis_auto-scrolling-mode.png)


