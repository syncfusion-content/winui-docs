---
layout: post
title: Axis labels in WinUI Chart control | Syncfusion
description: Learn here all about axis labels and its customization in Syncfusion WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Axis Labels in WinUI Chart (SfCartesianChart)

Axis labels are used to show the units or measures or category value of axis to visualize the data user friendly. It will be generated based on the range and the values binded to [XBindingPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_XBindingPath) or [YBindingPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.XyDataSeries.html?tabs=tabid-1#Syncfusion_UI_Xaml_Charts_XyDataSeries_YBindingPath) properties of series.

## Position 

The [LabelPosition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelPosition) property is used to position the axis label either inside or outside of the chart plotting area. By default, [LabelPosition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelPosition) is [Outside](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.AxisElementPosition.html#Syncfusion_UI_Xaml_Charts_AxisElementPosition_Outside).

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.PrimaryAxis>
    <chart:CategoryAxis LabelPosition="Inside"/>
</chart:SfCartesianChart.PrimaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new CategoryAxis()
{
    LabelPosition = AxisElementPosition.Inside
};

{% endhighlight %}

{% endtabs %}

![Axis label position in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_inside_position.png)

## Rotation Angle

The [LabelRotationAngle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelRotationAngle) property is used to define the angle for the label content.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.PrimaryAxis>
    <chart:CategoryAxis LabelRotationAngle="90"/>
</chart:SfCartesianChart.PrimaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new CategoryAxis()
{
    LabelRotationAngle = 90
};

{% endhighlight %}

{% endtabs %}

![Axis label rotation angle in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_rotation.png)

## Custom Axis Labels

Chart axis allows user to define the own axis labels. [Content](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxisLabel.html#Syncfusion_UI_Xaml_Charts_ChartAxisLabel_Content) and [Position](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxisLabel.html#Syncfusion_UI_Xaml_Charts_ChartAxisLabel_Position) property of [ChartAxisLabel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxisLabel.html) used to defines the label for axis using the [CustomLabels](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_CustomLabels) property as in the below code sample.

N> Also directly bind the collection of labels to the [LabelSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelSource) property for defining custom labels.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.PrimaryAxis>
    <chart:CategoryAxis>
        <chart:CategoryAxis.CustomLabels>
            <chart:ChartAxisLabel Position="0" Content="0-1"/>
            <chart:ChartAxisLabel Position="1" Content="1-2"/>
            <chart:ChartAxisLabel Position="2" Content="2-3"/>
            <chart:ChartAxisLabel Position="3" Content="3-4"/>
            <chart:ChartAxisLabel Position="4" Content="4-5"/>
            <chart:ChartAxisLabel Position="5" Content="5-5"/>
        </chart:CategoryAxis.CustomLabels>
    </chart:CategoryAxis>
</chart:SfCartesianChart.PrimaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

CategoryAxis axis = new CategoryAxis();

axis.CustomLabels.Add(new ChartAxisLabel() { Position = 0, Content = "0-1" });
axis.CustomLabels.Add(new ChartAxisLabel() { Position = 1, Content = "1-2" });
axis.CustomLabels.Add(new ChartAxisLabel() { Position = 2, Content = "2-3" });
axis.CustomLabels.Add(new ChartAxisLabel() { Position = 3, Content = "3-4" });
axis.CustomLabels.Add(new ChartAxisLabel() { Position = 4, Content = "4-5" });
axis.CustomLabels.Add(new ChartAxisLabel() { Position = 5, Content = "5-5" });

chart.PrimaryAxis = axis;

{% endhighlight %}

{% endtabs %}

![Axis label customization support in WinUI](Axis_images/WinUI_Chart_Axis_Custom_labels.png)

## Format

Axis labels can be formatted by predefined formatting types by using the [LabelFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelFormat) property based on the axis types.

**DateTimeAxis**

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.PrimaryAxis>
    <chart:DateTimeAxis LabelFormat="MMM-yy"/>
</chart:SfCartesianChart.PrimaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new DateTimeAxis()
{
    LabelFormat = "MMM-yy",
};

{% endhighlight %}

{% endtabs %}

**NumericalAxis**

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.SecondaryAxis>
    <chart:NumericalAxis LabelFormat="0.00"/>
</chart:SfCartesianChart.SecondaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.SecondaryAxis = new NumericalAxis()
{
    LabelFormat = "0.00"
};

{% endhighlight %}

{% endtabs %}

![Axis labels formatting support in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_format.png)

## Template

The appearance of the axis labels can be customized by using the [LabelTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelTemplate) property of axis.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.Resources>
    <DataTemplate x:Key="labelTemplate">
        <Border BorderBrush="Blue" CornerRadius="5" BorderThickness="1">
            <TextBlock Text="{Binding Content}" FontSize="12" FontStyle="Italic" FontWeight="Bold" Margin="3"/>
        </Border>
    </DataTemplate>
</chart:SfCartesianChart.Resources>
. . .
<chart:SfCartesianChart.PrimaryAxis>
    <chart:CategoryAxis LabelTemplate="{StaticResource labelTemplate}"/>
</chart:SfCartesianChart.PrimaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new CategoryAxis()
{
    LabelTemplate = chart.Resources["labelTemplate"] as DataTemplate
};

{% endhighlight %}

{% endtabs %}

![Axis LabelTemplate support in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_Template.png)

## Label Extent

The [LabelExtent](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelExtent) property allows to set the distance between the axis header and the axis.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.PrimaryAxis>
    <chart:CategoryAxis Header="Demand" LabelExtent="50"/>
</chart:SfCartesianChart.PrimaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
chart.PrimaryAxis = new NumericalAxis()
{
    Header = "Demand",
    LabelExtent = 50
};

{% endhighlight %}

{% endtabs %}

![LabelExtent support for ChartAxis in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_Extent.png)

## Smart Axis Labels

When there are more number of axis labels, they may overlap with each other. Chart axis provides support to handle the overlapping axis labels using the [LabelIntersectAction](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelIntersectAction) property. By default the [LabelIntersectAction](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelIntersectAction) value is [Hide](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.AxisLabelIntersectAction.html#Syncfusion_UI_Xaml_Charts_AxisLabelIntersectAction_Hide).

| Actions | Description |
|--|--|
| None | Used to display all the label even if it intersects |
| Hide | Used to hide the labels if it intersects |
| MultipleRows | Used to move the labels to next row if it intersects |
| Auto | Used to rotate the labels if it intersects |

**Hide**

![Smart axis labels support in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_intersection_hide.png)

**MultipleRows**

![Smart axis labels support in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_intersection_Multiline.png)

**Auto**

![Smart axis labels support in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_intersection_Auto.png)

## Edge Labels Drawing Mode

Chart axis provides support to customize the rendering position of the edge labels using the [EdgeLabelsDrawingMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_EdgeLabelsDrawingMode) property. [EdgeLabelsDrawingMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_EdgeLabelsDrawingMode) property default value is `Center`.

| Action | Description |
|--|--|
| Center | Positions the label with tick line as center. |
| Fit | Position the gridline inside based on the edge label size |
| Hide | Hides the edge labels. |
| Shift | Shifts the edge labels to the left or right so that it comes inside the chart area. |

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.PrimaryAxis>
    <chart:DateTimeAxis EdgeLabelsDrawingMode="Shift"/>
</chart:SfCartesianChart.PrimaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . . 
chart.PrimaryAxis = new DateTimeAxis()
{
    EdgeLabelsDrawingMode = EdgeLabelsDrawingMode.Shift
};

{% endhighlight %}

{% endtabs %}

![Axis edge label positioning support in WinUI Chart](Axis_images/WinUI_Chart_Axis_Edge_label_drawing.png)

## Edge Labels Visibility
 
The visibility of the edge labels of the axis can be controlled using the [EdgeLabelsVisibilityMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_EdgeLabelsVisibilityMode) property. The default value of [EdgeLabelsVisibilityMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_EdgeLabelsVisibilityMode) is `Default`, which displays the edge label based on auto interval calculations.

**Always Visible**

[AlwaysVisible](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.EdgeLabelsVisibilityMode.html#Syncfusion_UI_Xaml_Charts_EdgeLabelsVisibilityMode_AlwaysVisible) option in [EdgeLabelsVisibilityMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_EdgeLabelsVisibilityMode) is used to view the edge labels even in chart area zoomed state.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis EdgeLabelsVisibilityMode="AlwaysVisible"/>
</chart:SfCartesianChart.PrimaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new NumericalAxis()
{
    EdgeLabelsVisibilityMode = EdgeLabelsVisibilityMode.AlwaysVisible
};

{% endhighlight %}

{% endtabs %}

**Visible**

[Visible](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.EdgeLabelsVisibilityMode.html#Syncfusion_UI_Xaml_Charts_EdgeLabelsVisibilityMode_Visible) option is used to display the edge labels irrespective of the auto interval calculation until zooming (i.e., in normal state).

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis EdgeLabelsVisibilityMode="Visible"/>
</chart:SfCartesianChart.PrimaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new NumericalAxis()
{
    EdgeLabelsVisibilityMode = EdgeLabelsVisibilityMode.Visible
};

{% endhighlight %}

{% endtabs %}