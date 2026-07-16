---
layout: post
title: Axis labels in WinUI Chart control | Syncfusion
description: Learn here all about axis labels and its customization in Syncfusion® WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: axis labels in winui chart, winui sfcartesianchart axis labels, winui chart axis labels customization, syncfusion winui chart axis labels, winui sfcartesianchart axis labels settings.
---

# Axis Labels in WinUI Chart (SfCartesianChart)

Axis labels are used to show the units, measures, or category values of the axis to visualize the data in a user-friendly way. It will be generated based on the range and the values bound to the [XBindingPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeries.html#Syncfusion_UI_Xaml_Charts_ChartSeries_XBindingPath) or [YBindingPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.XyDataSeries.html#Syncfusion_UI_Xaml_Charts_XyDataSeries_YBindingPath) properties of the series.

## Rotation Angle

The [LabelRotation](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelRotation) property is used to define the angle for the label content.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

    <!-- Configure additional chart elements -->
    <chart:SfCartesianChart.XAxes>
        <chart:CategoryAxis LabelRotation="90"/>
    </chart:SfCartesianChart.XAxes>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

// Configure additional chart elements
CategoryAxis primaryAxis = new CategoryAxis()
{
    LabelRotation = 90
};
chart.XAxes.Add(primaryAxis);

{% endhighlight %}

{% endtabs %}

![Axis label rotation angle in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_rotation.png)

## Format

Axis labels can be formatted using predefined formatting types with the [LabelFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.LabelStyle.html#Syncfusion_UI_Xaml_Charts_LabelStyle_LabelFormat) property based on the axis type.

**DateTimeAxis**

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

   <!-- Configure additional chart elements -->
    <chart:SfCartesianChart.XAxes>
        <chart:DateTimeAxis>
            <chart:DateTimeAxis.LabelStyle>
                <chart:LabelStyle LabelFormat="MMM-yy"/>
            </chart:DateTimeAxis.LabelStyle>
        </chart:DateTimeAxis>
    </chart:SfCartesianChart.XAxes>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

// Configure additional chart elements
DateTimeAxis primaryAxis = new DateTimeAxis()
{
    LabelStyle = new LabelStyle() { LabelFormat= "MMM-yy" }
};
chart.XAxes.Add(primaryAxis);

{% endhighlight %}

{% endtabs %}

**NumericalAxis**

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    
    <!-- Configure additional chart elements -->
    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis>
            <chart:NumericalAxis.LabelStyle>
                <chart:LabelStyle LabelFormat="0.00"/>
            </chart:NumericalAxis.LabelStyle>
        </chart:NumericalAxis>
    </chart:SfCartesianChart.YAxes>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

// Configure additional chart elements
NumericalAxis secondaryAxis = new NumericalAxis()
{
    LabelStyle = new LabelStyle() { LabelFormat= "0.00" }
};
chart.YAxes.Add(secondaryAxis);

{% endhighlight %}

{% endtabs %}

![Axis labels formatting support in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_format.png)

## Template

The appearance of the axis labels can be customized by using the [LabelTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelTemplate) property of axis.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.Resources>
        <DataTemplate x:Key="labelTemplate" x:DataType="chart:ChartAxisLabel">
            <Border 
                BorderBrush="Blue"
                CornerRadius="5"
                BorderThickness="1">
                <TextBlock 
                    Text="{Binding Content}"
                    FontSize="12"
                    FontStyle="Italic"
                    FontWeight="Bold" 
                    Margin="3"/>
            </Border>
        </DataTemplate>
    </chart:SfCartesianChart.Resources>
    
    <!-- Configure additional chart elements -->
    <chart:SfCartesianChart.XAxes>
        <chart:CategoryAxis LabelTemplate="{StaticResource labelTemplate}"/>
    </chart:SfCartesianChart.XAxes>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

// The 'labelTemplate' resource is defined in XAML Resources and referenced here.
CategoryAxis primaryAxis = new CategoryAxis()
{
    LabelTemplate = chart.Resources["labelTemplate"] as DataTemplate
};
chart.XAxes.Add(primaryAxis);

{% endhighlight %}

{% endtabs %}

![Axis LabelTemplate support in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_Template.png)

N> The binding context for the `LabelTemplate` is [ChartAxisLabel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxisLabel.html), which provides the necessary data for the axis labels.

## Label Extent

The [LabelExtent](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelExtent) property allows you to set the distance between the axis header and the axis.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

    <!-- Configure additional chart elements --> 
    <chart:SfCartesianChart.XAxes>
        <chart:CategoryAxis Header="Demand" LabelExtent="50"/>
    </chart:SfCartesianChart.XAxes>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

NumericalAxis primaryAxis = new NumericalAxis()
{
    Header = "Demand",
    LabelExtent = 50
};
chart.XAxes.Add(primaryAxis);

{% endhighlight %}

{% endtabs %}

![LabelExtent support for ChartAxis in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_Extent.png)

## Smart Axis Labels

When there are a large number of axis labels, they may overlap with each other. The chart axis provides support to handle overlapping axis labels using the [LabelsIntersectAction](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelsIntersectAction) property. By default, the [LabelsIntersectAction](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelsIntersectAction) value is [Hide](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.AxisLabelsIntersectAction.html#Syncfusion_UI_Xaml_Charts_AxisLabelsIntersectAction_Hide).

| Actions | Description |
|--|--|
| [None](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.AxisLabelsIntersectAction.html#Syncfusion_UI_Xaml_Charts_AxisLabelsIntersectAction_None) | Used to display all the label even if it intersects |
| [Hide](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.AxisLabelsIntersectAction.html#Syncfusion_UI_Xaml_Charts_AxisLabelsIntersectAction_Hide) | Used to hide the labels if it intersects |
| [MultipleRows](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.AxisLabelsIntersectAction.html#Syncfusion_UI_Xaml_Charts_AxisLabelsIntersectAction_MultipleRows) | Used to move the labels to next row if it intersects |
| [Auto](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.AxisLabelsIntersectAction.html#Syncfusion_UI_Xaml_Charts_AxisLabelsIntersectAction_Auto) | Used to rotate the labels if it intersects |

**Hide**

![Smart axis labels support in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_intersection_hide.png)

**MultipleRows**

![Smart axis labels support in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_intersection_Multiline.png)

**Auto**

![Smart axis labels support in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_intersection_Auto.png)

## Edge Labels Drawing Mode

The chart axis provides support to customize the rendering position of the edge labels using the [EdgeLabelsDrawingMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_EdgeLabelsDrawingMode) property. The default value of the [EdgeLabelsDrawingMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_EdgeLabelsDrawingMode) property is [Center](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.EdgeLabelsDrawingMode.html#Syncfusion_UI_Xaml_Charts_EdgeLabelsDrawingMode_Center).

| Action | Description |
|--|--|
| [Center](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.EdgeLabelsDrawingMode.html#Syncfusion_UI_Xaml_Charts_EdgeLabelsDrawingMode_Center) | Positions the label with tick line as center. |
| [Fit](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.EdgeLabelsDrawingMode.html#Syncfusion_UI_Xaml_Charts_EdgeLabelsDrawingMode_Fit) | Positions the gridline inside based on the edge label size. |
| [Hide](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.EdgeLabelsDrawingMode.html#Syncfusion_UI_Xaml_Charts_EdgeLabelsDrawingMode_Hide) | Hides the edge labels. |
| [Shift](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.EdgeLabelsDrawingMode.html#Syncfusion_UI_Xaml_Charts_EdgeLabelsDrawingMode_Shift) | Shifts the edge labels to the left or right so that they come inside the chart area. |

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    
    <!-- Configure additional chart elements -->
    <chart:SfCartesianChart.XAxes>
        <chart:DateTimeAxis EdgeLabelsDrawingMode="Shift"/>
    </chart:SfCartesianChart.XAxes>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

// Configure additional chart elements
DateTimeAxis primaryAxis = new DateTimeAxis()
{
    EdgeLabelsDrawingMode = EdgeLabelsDrawingMode.Shift
};
chart.XAxes.Add(primaryAxis);

{% endhighlight %}

{% endtabs %}

![Axis edge label positioning support in WinUI Chart](Axis_images/WinUI_Chart_Axis_Edge_label_drawing.png)

## Edge Labels Visibility
 
The visibility of the edge labels of the axis can be controlled using the [EdgeLabelsVisibilityMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.RangeAxisBase.html#Syncfusion_UI_Xaml_Charts_RangeAxisBase_EdgeLabelsVisibilityMode) property. The default value of [EdgeLabelsVisibilityMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.RangeAxisBase.html#Syncfusion_UI_Xaml_Charts_RangeAxisBase_EdgeLabelsVisibilityMode) is [Default](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.EdgeLabelsVisibilityMode.html#Syncfusion_UI_Xaml_Charts_EdgeLabelsVisibilityMode_Default), which displays the edge labels based on auto interval calculations.

**Always Visible**

The [AlwaysVisible](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.EdgeLabelsVisibilityMode.html#Syncfusion_UI_Xaml_Charts_EdgeLabelsVisibilityMode_AlwaysVisible) option in [EdgeLabelsVisibilityMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.RangeAxisBase.html#Syncfusion_UI_Xaml_Charts_RangeAxisBase_EdgeLabelsVisibilityMode) is used to view the edge labels even when the chart area is in a zoomed state.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

    <!-- Configure additional chart elements -->
    <chart:SfCartesianChart.XAxes>
        <chart:NumericalAxis EdgeLabelsVisibilityMode="AlwaysVisible"/>
    </chart:SfCartesianChart.XAxes>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

// Configure additional chart elements
NumericalAxis primaryAxis = new NumericalAxis()
{
    EdgeLabelsVisibilityMode = EdgeLabelsVisibilityMode.AlwaysVisible
};
chart.XAxes.Add(primaryAxis);

{% endhighlight %}

{% endtabs %}

**Visible**

[Visible](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.EdgeLabelsVisibilityMode.html#Syncfusion_UI_Xaml_Charts_EdgeLabelsVisibilityMode_Visible) option is used to display the edge labels irrespective of the auto interval calculation until zooming (i.e., in normal state).

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

    <!-- Configure additional chart elements -->
    <chart:SfCartesianChart.XAxes>
        <chart:NumericalAxis EdgeLabelsVisibilityMode="Visible"/>
    </chart:SfCartesianChart.XAxes>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

// Configure additional chart elements
NumericalAxis primaryAxis = new NumericalAxis()
{
    EdgeLabelsVisibilityMode = EdgeLabelsVisibilityMode.Visible
};
chart.XAxes.Add(primaryAxis);

{% endhighlight %}

{% endtabs %}

## See Also

* [How to customize the axis labels of WinUI Chart (SfCartesianChart)](https://support.syncfusion.com/kb/article/13013)