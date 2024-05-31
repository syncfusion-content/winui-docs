---
layout: post
title: Axis labels in WinUI Chart control | Syncfusion
description: Learn here all about the chart axis lables and its customization in Syncfusion WinUI Chart (SfPolarChart) control.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Axis labels in WinUI Chart

The axis labels are used to show the units, measures, or category values of the axis to visualize the data. It will be generated based on the range and values binded to the series in the chart.

## Rotation

The [LabelRotation](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelRotation) property is used to define the angle for the label content.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    ...
    <chart:SfPolarChart.SecondaryAxis>
        <chart:NumericalAxis LabelRotation="30"/>
    </chart:SfPolarChart.SecondaryAxis>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
...
chart.PrimaryAxis = new CategoryAxis();
chart.SecondaryAxis = new NumericalAxis()
{
    LabelRotation = 30,
}
...

{% endhighlight %}

{% endtabs %}

![Chart axis label rotation support in WinUI chart](Axis_Images/WinUI_Chart_LabelRotationAngle.png)

## Format

Axis labels can be formatted by predefined formatting types by using the [LabelFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.LabelStyle.html#Syncfusion_UI_Xaml_Charts_LabelStyle_LabelFormat) property based on the axis types.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
            
    <chart:SfPolarChart.PrimaryAxis>
        <chart:CategoryAxis/>
    </chart:SfPolarChart.PrimaryAxis>
                
    <chart:SfPolarChart.SecondaryAxis>
        <chart:NumericalAxis>
            <chart:NumericalAxis.LabelStyle>
                <chart:LabelStyle LabelFormat="0.0" />
            </chart:NumericalAxis.LabelStyle>
        </chart:NumericalAxis>
    </chart:SfPolarChart.SecondaryAxis>
    ...

</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();

chart.PrimaryAxis = new CategoryAxis();

chart.SecondaryAxis = new NumericalAxis()
{
    LabelStyle = new LabelStyle() { LabelFormat= "0.0" }
};
...

{% endhighlight %}

{% endtabs %}

![Axis label formart support in WinUI Chart](Axis_Images/WinUI_Chart_Numerical_LabelFormat.png)

## Template

The appearance of the axis labels can be customized by using the [LabelTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelTemplate) property of axis.

{% tabs %}

{% highlight xaml %}

<Grid x:Name="grid">
    <Grid.Resources>
        <DataTemplate x:Key="labelTemplate">
            <Border Background="Blue"
					CornerRadius="5"
					BorderThickness="1">
                <TextBlock Text="{Binding Content}"
						   Foreground="White"
						   FontStyle="Italic" 
						   FontSize="10"
						   FontWeight="Bold" 
						   Margin="3"/>
            </Border>
        </DataTemplate>
    </Grid.Resources>
    <chart:SfPolarChart x:Name="chart">
    ...
        <chart:SfPolarChart.PrimaryAxis>
            <chart:CategoryAxis LabelTemplate="{StaticResource labelTemplate}"/>
        </chart:SfPolarChart.PrimaryAxis>

        <chart:SfPolarChart.SecondaryAxis>
            <chart:NumericalAxis/>
        </chart:SfPolarChart.SecondaryAxis>
    ...
    </chart:SfPolarChart>
</Grid>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();

chart.PrimaryAxis = new CategoryAxis()
{
    LabelTemplate = grid.Resources["labelTemplate"] as DataTemplate
};

chart.SecondaryAxis = new NumericalAxis();
...

{% endhighlight %}

{% endtabs %}

![LabelTemplate support for ChartAxis in WinUI Chart](Axis_Images/WinUI_Chart_AxisLabelTemplate.png)

