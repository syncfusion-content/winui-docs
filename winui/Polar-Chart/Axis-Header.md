---
layout: post
title: Axis title in WinUI Chart control | Syncfusion
description: Learn here all about the chart axis title of Syncfusion WinUI Chart (SfPolarChart) control and its customization.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Axis Title in WinUI Chart (SfPolarChart)

The [Header](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_Header) property is used to define the title for the chart axis. It accepts any `UIElement` as content for the chart axis header.

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

N> Polar chart supports title for secondary axis only.

![Axis title in WinUI Chart](Axis_Images/WinUI_Chart_AxisHeader.png)

## Style

The [`HeaderStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_HeaderStyle) property is used to provide style for the axis header.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
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
</chart:SfPolarChart>

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

![Axis header style in WinUI Chart](Axis_Images/WinUI_Chart_Axis_HeaderStyle.png)

## Template

The appearance of the header can be customized using the [`HeaderTemplate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_HeaderTemplate) property.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
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
</chart:SfPolarChart>

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

![Axis HeaderTemplate support in WinUI Chart](Axis_Images/WinUI_Chart_AxisHeader_Template.png)