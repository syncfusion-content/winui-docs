---
layout: post
title:  Crosshair in WinUI Chart control | Syncfusion
description: Learn here all about crosshair and its customziation in Syncfusion® WinUI Chart (SfCartesianChart) control
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: crosshair in winui chart, winui sfcartesianchart crosshair, winui chart crosshair customization, syncfusion winui chart crosshair, winui sfcartesianchart crosshair settings.
---

# Crosshair in WinUI Chart (SfCartesianChart)

ChartCrossHairBehavior allows you to view the data values at the current mouse pointer or touch contact point. By moving the crosshair lines horizontally, you can identify the corresponding X values, and by moving them vertically, you can identify the Y values.

## Define Crosshair

To add the crosshair in the chart, create an instance [ChartCrosshairBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartCrosshairBehavior.html) and set it to the [CrosshairBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_CrosshairBehavior) property of the chart.

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.CrosshairBehavior>
        <chart:ChartCrosshairBehavior/>
    </chart:SfCartesianChart.CrosshairBehavior>
    ...
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
ChartCrosshairBehavior behavior = new ChartCrosshairBehavior();
chart.CrosshairBehavior = behavior;
...

{% endhighlight %}

{% endtabs %}

![Crosshair support in WinUI chart](Crosshair_images/WinUI_Chart_Crosshair.png)

To view the crosshair label in the particular axis, you have to enable the [ShowTrackballLabel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ShowTrackballLabel) property in that axis as in the following code snippet.

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.XAxes>
        <chart:CategoryAxis ShowTrackballLabel="True"/>
    </chart:SfCartesianChart.XAxes>
    . . .
    <chart:SfCartesianChart.CrosshairBehavior>
        <chart:ChartCrosshairBehavior/>
    </chart:SfCartesianChart.CrosshairBehavior>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
ChartCrosshairBehavior behavior = new ChartCrosshairBehavior();
chart.CrosshairBehavior = behavior;

CategoryAxis primaryAxis = new CategoryAxis()
{
    ShowTrackballLabel = true
};
chart.XAxes.Add(primaryAxis);
...

{% endhighlight %}

{% endtabs %}

![Crosshair ShowTrackballLabel support in WinUI chart](Crosshair_images/WinUI_Chart_Crosshair_ShowTrackballLabel.png)


## Horizontal and Vertical Line style

When you add [ChartCrossHairBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartCrosshairBehavior.html) to a chart in WinUI, horizontal and vertical crosshair lines will appear to indicate the current pointer position. These lines help you track the corresponding X and Y values on the chart. You can customize the appearance of these lines using the [HorizontalLineStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartCrosshairBehavior.html#Syncfusion_UI_Xaml_Charts_ChartCrosshairBehavior_HorizontalLineStyle) and [VerticalLineStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartCrosshairBehavior.html#Syncfusion_UI_Xaml_Charts_ChartCrosshairBehavior_VerticalLineStyle) properties.

### HorizontalLineStyle

The following code snippet demonstrates how to customize the line style for the horizontal line in the crosshair.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart x:Name="chart">
    <chart:SfCartesianChart.Resources>
        <ResourceDictionary>
            <Style TargetType="Line" x:Key="horizontalLineStyle">
                <Setter Property="Stroke" Value="Red"></Setter>
                <Setter Property="StrokeThickness" Value="2"></Setter>
                <Setter Property="StrokeDashArray" Value="5,2"></Setter>
            </Style>
        </ResourceDictionary>
    </chart:SfCartesianChart.Resources>


    <chart:SfCartesianChart.CrosshairBehavior>
        <chart:ChartCrosshairBehavior HorizontalLineStyle="{StaticResource horizontalLineStyle}"/>
    </chart:SfCartesianChart.CrosshairBehavior>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

ChartCrossHairBehavior crosshair = new ChartCrossHairBehavior()
{
    HorizontalLineStyle = chart.Resources["horizontalLineStyle"] as Style
};

chart.Behaviors.Add(crosshair);

{% endhighlight %}

{% endtabs %}

![Crosshair HorizontalLineStyle support in WinUI chart](Crosshair_images/WinUI_Chart_Crosshair_HorizontalLineStyle.png)

### VerticalLineStyle

The following code snippet demonstrates how to customize the line style for the vertical line in the crosshair.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart x:Name="chart">
    <chart:SfCartesianChart.Resources>
        <ResourceDictionary>
            <Style TargetType="Line" x:Key="verticalLineStyle">
                 <Setter Property="Stroke" Value="Red"></Setter>
                 <Setter Property="StrokeThickness" Value="2"></Setter>
                 <Setter Property="StrokeDashArray" Value="5,2"></Setter>
            </Style>
        </ResourceDictionary>
    </chart:SfCartesianChart.Resources>


    <chart:SfCartesianChart.CrosshairBehavior>
        <chart:ChartCrosshairBehavior VerticalLineStyle="{StaticResource verticalLineStyle}"/>
    </chart:SfCartesianChart.CrosshairBehavior>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

ChartCrossHairBehavior crosshair = new ChartCrossHairBehavior()
{
    VerticalLineStyle = chart.Resources["verticalLineStyle"] as Style
};

chart.Behaviors.Add(crosshair);

{% endhighlight %}

{% endtabs %}

![Crosshair VerticalLineStyle support in WinUI chart](Crosshair_images/WinUI_Chart_Crosshair_VerticalLineStyle.png)


## Horizontal and Vertical Axis label

When you add [ChartCrossHairBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartCrosshairBehavior.html) to a chart in WinUI, horizontal and vertical crosshair lines will appear to indicate the current pointer position. Along these lines, axis labels are displayed to indicate the corresponding X and Y values. You can customize the appearance of these labels using the [HorizontalAxisLabelAlignment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartCrosshairBehavior.html#Syncfusion_UI_Xaml_Charts_ChartCrosshairBehavior_HorizontalAxisLabelAlignment) and [VerticalAxisLabelAlignment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartCrosshairBehavior.html#Syncfusion_UI_Xaml_Charts_ChartCrosshairBehavior_VerticalAxisLabelAlignment) properties.

Axis Label can be aligned by Near, Far, Center, Auto and None Options.

* `Auto` - Axis label is aligned in Near/Far positions based on the movement of vertical line.
* `Far` - Axis label is positioned far from the position of vertical line in cross hair.
* `Near` - Axis label is near to the position of crosshair line.
* `Center` - Axis label is aligned to the center of the line.

### HorizontalAxisLabelAlignment

The Horizontal axis label is displayed when the vertical line in contact with x axis.The label can be aligned using [HorizontalAxisLabelAlignment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartCrosshairBehavior.html#Syncfusion_UI_Xaml_Charts_ChartCrosshairBehavior_HorizontalAxisLabelAlignment) property. By default the axis label will positioned in center.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.CrosshairBehavior>
    <chart:ChartCrosshairBehavior HorizontalAxisLabelAlignment="Far"/>
</chart:SfCartesianChart.CrosshairBehavior>


{% endhighlight %}

{% highlight c# %}

ChartCrossHairBehavior crosshair = new ChartCrossHairBehavior()
{
    HorizontalAxisLabelAlignment = ChartAlignment.Far
};

chart.Behaviors.Add(crosshair);

{% endhighlight %}

{% endtabs %}

![Crosshair HorizontalAxisLabelAlignment support in WinUI chart](Crosshair_images/WinUI_Chart_Crosshair_HorizontalAxisLabelAlignment.png)

### VerticalAxisLabelAlignment

The Vertical axis label is displayed when the horizontal line in contact with x axis.The label can be aligned using [VerticalAxisLabelAlignment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartCrosshairBehavior.html#Syncfusion_UI_Xaml_Charts_ChartCrosshairBehavior_VerticalAxisLabelAlignment) property. By default the axis label will positioned in `center`.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.CrosshairBehavior>
    <chart:ChartCrosshairBehavior VerticalAxisLabelAlignment="Far"/>
</chart:SfCartesianChart.CrosshairBehavior>


{% endhighlight %}

{% highlight c# %}

ChartCrossHairBehavior crosshair = new ChartCrossHairBehavior()
{
    VerticalAxisLabelAlignment = ChartAlignment.Far
};

chart.Behaviors.Add(crosshair);

{% endhighlight %}

{% endtabs %}

![Crosshair VerticalAxisLabelAlignment support in WinUI chart](Crosshair_images/WinUI_Chart_Crosshair_VerticalAxisLabelAlignment.png)

## Template

The default appearance of the crosshair axis labels can be customized by using the [CrosshairLabelTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_CrosshairLabelTemplate) property of chart axis. The following example demonstrates how to set the CrosshairLabelTemplate.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.Resources>
        <DataTemplate x:Key="xaxesCrossHairTemplate" x:DataType="chart:ChartPointInfo">
            <Border Background="Orange" CornerRadius="4" BorderThickness="1" BorderBrush="Black">
                <TextBlock Margin="2" Text="{Binding ValueX}"/>
            </Border>
        </DataTemplate>

        <DataTemplate x:Key="yaxesCrossHairTemplate" x:DataType="chart:ChartPointInfo">
            <Border Background="Orange" CornerRadius="4" BorderThickness="1" BorderBrush="Black">
                <TextBlock Margin="2" Text="{Binding ValueY}"/>
            </Border>
        </DataTemplate>
    </chart:SfCartesianChart.Resources>
    . . .

    <chart:SfCartesianChart.XAxes>
        <chart:CategoryAxis ShowTrackballLabel="True" CrosshairLabelTemplate="{StaticResource xaxesCrossHairTemplate}" />
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis ShowTrackballLabel="True" CrosshairLabelTemplate="{StaticResource yaxesCrossHairTemplate}"/>
    </chart:SfCartesianChart.YAxes>

    <chart:SfCartesianChart.CrosshairBehavior>
        <chart:ChartCrosshairBehavior />
    </chart:SfCartesianChart.CrosshairBehavior>
    ...
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
ChartCrosshairBehavior behavior = new ChartCrosshairBehavior();
chart.CrosshairBehavior = behavior;

CategoryAxis primaryAxis = new CategoryAxis()
{
    ShowTrackballLabel = true,
    CrosshairLabelTemplate = chart.Resources["xaxesCrossHairTemplate"] as DataTemplate
};
chart.XAxes.Add(primaryAxis);

NumericalAxis secondaryAxis = new NumericalAxis()
{
    ShowTrackballLabel = true,
    CrosshairLabelTemplate = chart.Resources["yaxesCrossHairTemplate"] as DataTemplate
};
chart.XAxes.Add(secondaryAxis);
...

{% endhighlight %}

{% endtabs %}

![Crosshair Template support in WinUI chart](Crosshair_images/WinUI_Chart_Crosshair_Template.png)
