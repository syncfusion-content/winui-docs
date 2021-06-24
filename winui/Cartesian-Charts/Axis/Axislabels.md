---
layout: post
title: Axis labels in WinUI Cartesian Chart control | Syncfusion
description: Learn here all about axis labels and its customization in Syncfusion WinUI Cartesian Chart(SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Axis labels in WinUI Cartesian Chart

Axis labels are used to show the units or measures or category value of axis to visualize the data user friendly. It will be generated based on the range and the values binded to [XBindingPath]() or [YBindingPath]() properties of series.

## Axis labels positioning 

The [LabelPosition]() property is used to position the axis label either inside or outside of the chart plotting area. By default, [LabelPosition]() is [Outside]().

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:CategoryAxis LabelPosition="Inside"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{
    LabelPosition = AxisElementPosition.Inside
};

{% endhighlight %}

{% endtabs %}

![Axis label position in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_inside_position.png)

## Rotation angle

The [LabelRotationAngle]() property is used to define the angle for the label content. The following code example illustrates the [LabelRotationAngle]().

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:CategoryAxis LabelRotationAngle="90"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{
    LabelRotationAngle = 90
};

{% endhighlight %}

{% endtabs %}

![Axis label rotation angle in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_rotation.png)

## Custom axis labels

Chart axis allows user to define the own axis labels. [Content]() and [Position]() property of [ChartAxisLabel]() used to defines the label for axis using the [CustomLabels]() property as in the below code sample.

{% tabs %}

{% highlight xaml %}

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

{% endhighlight %}

{% highlight c# %}

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

N> Also directly bind the collection of labels to the [`LabelSource`]() property for defining custom labels.

## Formatting the label

Axis labels can be formatted by predefined formatting types by using the [LabelFormat]() proeprty based on the axis types.

**DateTimeAxis**

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:DateTimeAxis LabelFormat="MMM-yy"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{
    LabelFormat = "MMM-yy",
};

{% endhighlight %}

{% endtabs %}

**NumericalAxis**

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.SecondaryAxis>
    <chart:NumericalAxis LabelFormat="0.00"/>
</chart:SfCartesianChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{
    LabelFormat = "0.00"
};

{% endhighlight %}

{% endtabs %}

![Axis labels formatting support in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_format.png)

## Label template

The appearance of the axis labels can be customized by using the [LabelTemplate]() property of axis.

{% tabs %}

{% highlight xaml %}

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

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{
    LabelTemplate = chart.Resources["labelTemplate"] as DataTemplate
};

{% endhighlight %}

{% endtabs %}

![Axis LabelTemplate support in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_Template.png)

## Label extent

The [LabelExtent]() property allows to set the distance between the axis header and the axis. The following code snippet defines the [LabelExtent]() property.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:CategoryAxis Header="Demand" LabelExtent="50"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{
    Header = "Demand",
    LabelExtent = 50
};

{% endhighlight %}

{% endtabs %}

![LabelExtent support for ChartAxis in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_Extent.png)

## Smart axis labels

When there are more number of axis labels, they may overlap with each other. Chart axis provides support to handle the overlapping axis labels using the [LabelIntersectAction]() property. By default the [LabelIntersectAction]() value is [Hide]().

The following are the options for intersecting action.

| Actions | Description |
|--|--|
| None | Used to display all the label even if it intersects |
| Hide | Used to hide the labels if it intersects |
| MultipleRows | Used to move the labels to next row if it intersects |
| Auto | Used to rotate the labels if it intersects |

**None**

![Smart axis labels support in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_intersection_none.png)

**Hide**

![Smart axis labels support in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_intersection_hide.png)

**MultipleRows**

![Smart axis labels support in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_intersection_Multiline.png)

**Auto**

![Smart axis labels support in WinUI Chart](Axis_images/WinUI_Chart_Axis_label_intersection_Auto.png)


## Edge labels drawing mode

Chart axis provides support to customize the rendering position of the edge labels using the [EdgeLabelsDrawingMode]() property. [EdgeLabelsDrawingMode]() property default value is `Center`.

The following are the customizing options in `EdgeLabelsDrawingMode`.

| Action | Description |
|--|--|
| Center | Positions the label with tick line as center. |
| Fit | Position the gridline inside based on the edge label size |
| Hide | Hides the edge labels. |
| Shift | Shifts the edge labels to the left or right so that it comes inside the chart area. |

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:DateTimeAxis EdgeLabelsDrawingMode="Shift"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{
    EdgeLabelsDrawingMode = EdgeLabelsDrawingMode.Shift
};

{% endhighlight %}

{% endtabs %}

![Axis edge label positioning support in WinUI Chart](Axis_images/WinUI_Chart_Axis_Edge_label_drawing.png)

## Edge labels visibility
 
The visibility of the edge labels of the axis can be controlled using the [EdgeLabelsVisibilityMode]() property. The default value of [EdgeLabelsVisibilityMode]() is `Default`, which displays the edge label based on auto interval calculations.

**Always Visible**

`AlwaysVisible` option in `EdgeLabelsVisibilityMode` is used to view the edge labels even in chart area zoomed state.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis EdgeLabelsVisibilityMode="AlwaysVisible"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{
    EdgeLabelsVisibilityMode = EdgeLabelsVisibilityMode.AlwaysVisible
};

{% endhighlight %}

{% endtabs %}

**Visible**

`Visible` option is used to display the edge labels irrespective of the auto interval calculation until zooming (i.e., in normal state).

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis EdgeLabelsVisibilityMode="Visible"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{
    EdgeLabelsVisibilityMode = EdgeLabelsVisibilityMode.Visible
};

{% endhighlight %}

{% endtabs %}

