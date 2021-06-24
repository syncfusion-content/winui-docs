---
layout: post
title:  Axis title in WinUI Polar Chart control | Syncfusion
description: Learn here all about the chart axis header of Syncfusion WinUI Polar Chart (SfPolarChart) control and its customization in polar chart.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Chart axis title WinUI Polar Chart (SfPolarChart)

`Header` property of chart axis is used to define and customize the chart axis title. It accepts any `UIElement` as content for the chart axis header.

The following code example demonstrates the defining header in primary and secondary axis. 

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    <chart:SfPolarChart.PrimaryAxis>
        <chart:CategoryAxis/>
    </chart:SfPolarChart.PrimaryAxis>
    <chart:SfPolarChart.SecondaryAxis>
        <chart:NumericalAxis Header="Tree"/>
    </chart:SfPolarChart.SecondaryAxis>
...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.PrimaryAxis = new CategoryAxis();
chart.SecondaryAxis = new NumericalAxis()
{
    Header = "Tree" 
};
...

{% endhighlight %}

{% endtabs %}

![Header support for ChartAxis in WinUI Polar Chart](Axis_Images/WinUI_PolarChart_AxisHeader.png)

## Style for header

[`HeaderStyle`]() property is used to provide style for the axis header. The following code example explains header style customization.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.PrimaryAxis>
    <chart:CategoryAxis/>
</chart:SfPolarChart.PrimaryAxis>
<chart:SfPolarChart.SecondaryAxis>
    <chart:NumericalAxis Header="Tree">
        <chart:NumericalAxis.HeaderStyle>
            <chart:LabelStyle FontFamily="Algerian" FontSize="13" Foreground="Black"/>
        </chart:NumericalAxis.HeaderStyle>
    </chart:NumericalAxis>
</chart:SfPolarChart.SecondaryAxis>
...

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
...
LabelStyle style = new LabelStyle()
{
    FontFamily = new FontFamily("Algerian"),
    FontSize = 13,
    Foreground = new SolidColorBrush(Colors.Black)
};

chart.PrimaryAxis = new CategoryAxis();

chart.SecondaryAxis = new NumericalAxis()
{
    Header = "Tree",
    LabelStyle = style
};
...

{% endhighlight %}

{% endtabs %}

![Axis header style for chart axis in WinUI Polar Chart](Axis_Images/WinUI_PolarChart_Axis_HeaderStyle.png)

## Customization of header by HeaderTemplate

Default appearance of the axis header can be customized using [`HeaderTemplate`]() property. The following code snippet demonstrates the header customization.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.Resources>
    <DataTemplate x:Key="headerTemplate">
        <Border BorderBrush="Blue" CornerRadius="5" BorderThickness="1">
            <TextBlock Text="{Binding}" FontSize="12" Margin="3"
                        FontStyle="Italic" FontWeight="Bold"/>
        </Border>
    </DataTemplate>
</chart:SfPolarChart.Resources>

<chart:SfPolarChart.PrimaryAxis>
    <chart:CategoryAxis/>
</chart:SfPolarChart.PrimaryAxis>
<chart:SfPolarChart.SecondaryAxis>
    <chart:NumericalAxis Header="Tree" HeaderTemplate="{StaticResource headerTemplate}">
    </chart:NumericalAxis>
</chart:SfPolarChart.SecondaryAxis>
...

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
...

chart.PrimaryAxis = new CategoryAxis();

chart.SecondaryAxis = new NumericalAxis()
{
    Header = "Tree",
    HeaderTemplate = chart.Resources["headerTemplate"] as DataTemplate
};
...

{% endhighlight %}

{% endtabs %}

![HeaderTemplate support for chart axis in WinUI Polar Chart](Axis_Images/WinUI_PolarChart_AxisHeader_Template.png)