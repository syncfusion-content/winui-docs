---
layout: post
title:  Trackball in WinUI Chart control | Syncfusion
description: Learn here all about trackball and its customziation in Syncfusion WinUI Chart (SfCartesianChart) control
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Trackball in WinUI Chart (SfCartesianChart)

The trackball allows you to track a data point closer to the cursor position. The x values are determined from the position of the vertical line in the axis and y values are determined from the points touching the vertical line in the series.

## Define Trackball

To add trackball in the chart, create an instance [ChartTrackballBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html) and add it to the [Behaviors](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartBase.html#Syncfusion_UI_Xaml_Charts_ChartBase_Behaviors) collection of the chart.

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.Behaviors>
        <chart:ChartTrackballBehavior/>
    </chart:SfCartesianChart.Behaviors>
    ...
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
ChartTrackballBehavior behavior = new ChartTrackballBehavior();
chart.Behaviors.Add(behavior);
...

{% endhighlight %}

{% endtabs %}

![Trackball support in WinUI chart](Trackball_images/WinUI_chart_trackball.png)

To view the trackball label in the particular axis, you have to enable the [ShowTrackballInfo](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ShowTrackballInfo) property in that axis as in the following code snippet.

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.PrimaryAxis>
        <chart:CategoryAxis ShowTrackballInfo="True"/>
    </chart:SfCartesianChart.PrimaryAxis>
    . . .
    <chart:SfCartesianChart.Behaviors>
        <chart:ChartTrackballBehavior/>
    </chart:SfCartesianChart.Behaviors>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
ChartTrackballBehavior behavior = new ChartTrackballBehavior();
chart.Behaviors.Add(behavior);

chart.PrimaryAxis = new CategoryAxis()
{
    ShowTrackballInfo = true
};
...

{% endhighlight %}

{% endtabs %}

The default appearance of the Trackball in primary axis (CategoryAxis).

![Axis trackball support in WinUI chart](Trackball_images/WinUI_chart_axis_trackball.png)

The Trackball is composed of the following parts:

1. Line
2. Symbol
3. Axis label
4. Series label

## Trackball Line

The trackball line is visible, when you initialize the [ChartTrackballBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html). If you want to collapse the visibility of the trackball line, then you have to set [ShowLine](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_ShowLine) to `false`.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.Behaviors>
        <chart:ChartTrackballBehavior ShowLine="False"/>
    </chart:SfCartesianChart.Behaviors>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

ChartTrackballBehavior behavior = new ChartTrackballBehavior()
{
    ShowLine = false
};

chart.Behaviors.Add(behavior);
...

{% endhighlight %}

{% endtabs %}

![Trackball line in WinUI chart](Trackball_images/WinUI_chart_trackball_line.png)

### Customization of trackball line

By using the [LineStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_LineStyle) property, you can customize the appearance of trackball line.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart Height="388"  Width="500" Palette="BlueChrome">
. . .
    <chart:SfCartesianChart.Resources>
        <Style TargetType="Line" x:Key="lineStyle">
            <Setter Property="StrokeDashArray" Value="5,2"/>
            <Setter Property="Stroke" Value="Red"/>
            <Setter Property="StrokeThickness" Value="2"/>
        </Style>
    </chart:SfCartesianChart.Resources>
    . . .
    <chart:SfCartesianChart.Behaviors>
        <chart:ChartTrackballBehavior LineStyle="{StaticResource lineStyle}"/>
    </chart:SfCartesianChart.Behaviors>
. . .   
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
ChartTrackballBehavior Trackball = new ChartTrackballBehavior()
{
    LineStyle = chart.Resources["lineStyle"] as Style
};

chart.Behaviors.Add(Trackball);
...

{% endhighlight %}

{% endtabs %}

![Trackball line customization in WinUI chart](Trackball_images/WinUI_chart_trackball_line_customization.png)

## Symbol

By default, the trackball symbol is displayed as ellipse. To change the default style of the symbol by using the [ChartTrackballStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_ChartTrackballStyle) property.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart Height="388"  Width="500" Palette="BlueChrome">
. . 
    <chart:SfCartesianChart.Resources>
        <Style TargetType="chart:ChartTrackballControl" x:Key="trackballStyle">
            <Setter Property="Background" Value="Red"></Setter>
        </Style>
    </chart:SfCartesianChart.Resources>
    . . .
    <chart:SfCartesianChart.Behaviors>
        <chart:ChartTrackballBehavior ChartTrackballStyle="{StaticResource trackballStyle}"/>
    </chart:SfCartesianChart.Behaviors>
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

ChartTrackballBehavior Trackball = new ChartTrackballBehavior()
{
    ChartTrackballStyle = chart.Resources["trackballStyle"] as Style
};

chart.Behaviors.Add(Trackball);
...

{% endhighlight %}

{% endtabs %}

![Trackball symbol in WinUI chart](Trackball_images/WinUI_chart_trackball_symbol_customization.png)

## Axis Label

The axis label will be viewed when the [ShowTrackballInfo](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ShowTrackballInfo) property is set to true. The default value of [ShowTrackballInfo](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ShowTrackballInfo) is `false`.

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.PrimaryAxis>
        <chart:CategoryAxis ShowTrackballInfo="True"/>
    </chart:SfCartesianChart.PrimaryAxis>
    . . .
    <chart:SfCartesianChart.Behaviors>
        <chart:ChartTrackballBehavior/>
    </chart:SfCartesianChart.Behaviors>
    . . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new CategoryAxis()
{
    ShowTrackballInfo = true
};
...
ChartTrackballBehavior behavior = new ChartTrackballBehavior();
chart.Behaviors.Add(behavior);
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Trackball axis label in WinUI chart](Trackball_images/WinUI_chart_trackball_axis_label.png)

### Axis label alignment 

The alignment of the axis label can be defined using the [AxisLabelAlignment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_AxisLabelAlignment) property. By default, the axis label will positioned in center.

* `Auto` - used to align in Near/Far positions based on the trackball movement.
* `Far` - used to align in far from the position of trackball.
* `Near` -used to align in near to the position of trackball.
* `Center` - used to align to the center of the trackball.

### Customization of axis label

The appearance of the axis label can be customized by using the [TrackballLabelTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_TrackballLabelTemplate) property in the chart axis as in the below code snippet.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

    <chart:SfCartesianChart.Resources>
        <DataTemplate x:Key="labelTemplate">
            <Border CornerRadius="4" BorderThickness="1" BorderBrush="Black"
                    Background="LightGreen" Padding="6,0,6,6">
                <TextBlock Foreground="Black" Text="{Binding ValueX}" FontSize="15"/>
            </Border>
        </DataTemplate>
    </chart:SfCartesianChart.Resources>

    <chart:SfCartesianChart.PrimaryAxis>
        <chart:CategoryAxis ShowTrackballInfo="True" TrackballLabelTemplate="{StaticResource labelTemplate}"/>
    </chart:SfCartesianChart.PrimaryAxis>
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

chart.PrimaryAxis = new NumericalAxis()
{
    ShowTrackballInfo = true,
    TrackballLabelTemplate = chart.Resources["labelTemplate"] as DataTemplate
};

{% endhighlight %}

{% endtabs %}

![Customization support for Trackball axis label in WinUI chart](Trackball_images/WinUI_chart_trackball_axis_label_customization.png)

## Series Label

When the mouse hovered in the chart area, you can view the label displayed over the series in addition the axis label.

**ShowTrackballInfo**

The [ShowTrackballInfo](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ShowTrackballInfo) property is used to enable or disable the label for corresponding series. By default, [ShowTrackballInfo](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ShowTrackballInfo) property is `true`.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.Series>
        <chart:SplineSeries ItemsSource="{Binding Data}" 
                            XBindingPath="Demand" 
                            YBindingPath="Year2010"/>
        <chart:SplineSeries ItemsSource="{Binding Data}" 
                            XBindingPath="Demand" 
                            YBindingPath="Year2011" ShowTrackballInfo="False"/>
        <chart:SplineSeries ItemsSource="{Binding Data}" 
                            XBindingPath="Demand" 
                            YBindingPath="Year2012">
    </chart:SfCartesianChart.Series>
    ...
</chart:SfCartesianChart>
 
{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
SplineSeries series1 = new SplineSeries();
chart.Series.Add(series1);
SplineSeries series2 = new SplineSeries()
{
    ShowTrackballInfo = false
};
chart.Series.Add(series2);
SplineSeries series3 = new SplineSeries();
chart.Series.Add(series3);
...

{% endhighlight %}

{% endtabs %}

![Trackball series label in WinUI chart](Trackball_images/WinUI_chart_trackball_series_label.png)

**Alignment of series label**

The trackball label displayed over the series can be aligned using the [LabelHorizontalAlignment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_LabelHorizontalAlignment) and [LabelVerticalAlignment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_LabelVerticalAlignment) properties. By default, the [LabelHorizontalAlignment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_LabelHorizontalAlignment) is `Left` and [LabelVerticalAlignment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_LabelVerticalAlignment) is `Top`.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.Behaviors>
        <chart:ChartTrackballBehavior LabelHorizontalAlignment="Center" LabelVerticalAlignment="Center"/>
    </chart:SfCartesianChart.Behaviors>
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
ChartTrackballBehavior behavior = new ChartTrackballBehavior()
{
    LabelHorizontalAlignment = ChartAlignment.Center,
    LabelVerticalAlignment = ChartAlignment.Center
};

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}

![Alignment support for Trackball series label in WinUI Chart](Trackball_images/WinUI_chart_trackball_label_alignment.png)

## Label Display Mode

When there is a multiple series, the trackball series label will be displayed only for the nearest point. If you want to display all the y values with respect to the x value then the [LabelDisplayMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_LabelDisplayMode) property is set to [FloatAllPoints](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.TrackballLabelDisplayMode.html#Syncfusion_UI_Xaml_Charts_TrackballLabelDisplayMode_FloatAllPoints).

**FloatAllPoints**

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.Behaviors>
        <chart:ChartTrackballBehavior LabelDisplayMode="FloatAllPoints"/>
    </chart:SfCartesianChart.Behaviors>
    ...
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
ChartTrackballBehavior behavior = new ChartTrackballBehavior()
{
    LabelDisplayMode = TrackballLabelDisplayMode.FloatAllPoints
};

chart.Behaviors.Add(behavior);
...

{% endhighlight %}

{% endtabs %}

![LabelDisplayMode support for Trackball in WinUI Chart](Trackball_images/WinUI_chart_trackball_float_all_points.png)

**NearestPoint**

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.Behaviors>
        <chart:ChartTrackballBehavior LabelDisplayMode="NearestPoint"/>
    </chart:SfCartesianChart.Behaviors>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
ChartTrackballBehavior behavior = new ChartTrackballBehavior()
{
    LabelDisplayMode = TrackballLabelDisplayMode.NearestPoint
};

chart.Behaviors.Add(behavior);
...

{% endhighlight %}

{% endtabs %}

![LabelDisplayMode support for Trackball in WinUI Chart](Trackball_images/WinUI_chart_trackball_nearest_point.png)

**GroupAllPoints**

[ChartTrackballBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html) supports to group the multiple trackball points, and allows to display the trackball points in a single trackball label. It can be achieved by setting the [LabelDisplayMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_LabelDisplayMode)) property of [ChartTrackballBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html) as [GroupAllPoints](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.TrackballLabelDisplayMode.html#Syncfusion_UI_Xaml_Charts_TrackballLabelDisplayMode_GroupAllPoints).

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.Behaviors>
        <chart:ChartTrackballBehavior LabelDisplayMode="GroupAllPoints"/>
    </chart:SfCartesianChart.Behaviors>
    ...
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
ChartTrackballBehavior behavior = new ChartTrackballBehavior()
{
    LabelDisplayMode = TrackballLabelDisplayMode.GroupAllPoints
};

chart.Behaviors.Add(behavior);
...

{% endhighlight %}

{% endtabs %}

The following screenshot illustrates the trackball label for multiple series, when the [LabelDisplayMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_LabelDisplayMode) property value is `GroupAllPoints`.

![LabelDisplayMode support for Trackball in WinUI Chart](Trackball_images/WinUI_chart_trackball_group_all_points.png)

## Template

[TrackballLabelTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_TrackballLabelTemplate) property is used to customize the appearance of series label in trackball.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.Resources>
        <DataTemplate x:Key="labelTemplate">
            <Border CornerRadius="5" BorderThickness="1" 
                        BorderBrush="Black" Background="LightGreen" Padding="5">
                <TextBlock Foreground="Black" Text="{Binding ValueY}"/>
            </Border>
        </DataTemplate>
    </chart:SfCartesianChart.Resources>
    . . .
    <chart:SfCartesianChart.Behaviors>
        <chart:ChartTrackballBehavior />
    </chart:SfCartesianChart.Behaviors>

    <chart:SfCartesianChart.Series>
        <chart:ColumnSeries ItemsSource="{Binding Data}" 
                            XBindingPath="Demand" 
                            YBindingPath="Year2010"
                            TrackballLabelTemplate="{StaticResource labelTemplate}">
        </chart:ColumnSeries>
    </chart:SfCartesianChart.Series>
    ...
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
ChartTrackballBehavior Trackball = new ChartTrackballBehavior();
chart.Behaviors.Add(Trackball);

ColumnSeries series = new ColumnSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2010",
    TrackballLabelTemplate = chart.Resources["labelTemplate"] as DataTemplate,
};

chart.Series.Add(series);
...

{% endhighlight %}

{% endtabs %}

![Trackball templte support for Trackball in WinUI Chart](Trackball_images/WinUI_chart_trackball_label_template.png)

### Applying Series Interior

Interior color of the series is applied to the series label by setting [UseSeriesPalette](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_UseSeriesPalette) to true as shown in the following code snippet.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.Behaviors>
        <chart:ChartTrackballBehavior UseSeriesPalette="True"/>
    </chart:SfCartesianChart.Behaviors>
    ...
</chart:SfCartesianChart>
{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
ChartTrackballBehavior behavior = new ChartTrackballBehavior()
{
     UseSeriesPalette = true
};

chart.Behaviors.Add(behavior);
...

{% endhighlight %}

{% endtabs %}

![Applying interior color to series label in WinUI Chart](Trackball_images/WinUI_chart_trackball_label_series_palette.png)

