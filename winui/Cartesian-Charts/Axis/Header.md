---
layout: post
title: Header for axis in WinUI Chart control | Syncfusion
description: This section explains about chart axis header, header style, header template and its customization in WinUI chart (SfCartesianChart).
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Axis Title in WinUI Chart (SfCartesianChart)

The [Header]() property is used to set the title for the chart axis. It accepts any `UIElement` as content of axis title. 

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.PrimaryAxis>
    <chart:CategoryAxis Header="Category"/>
</chart:SfCartesianChart.PrimaryAxis>
<chart:SfCartesianChart.SecondaryAxis>
    <chart:NumericalAxis Header="Values"/>
</chart:SfCartesianChart.SecondaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new CategoryAxis() { Header = "Category" };
chart.SecondaryAxis = new NumericalAxis() { Header = "Values" };

{% endhighlight %}

{% endtabs %}

![Header support for ChartAxis in WinUI Chart](Axis_Images/WinUI_Chart_Axis_Header.png)

## Style

The [HeaderStyle]() property is used to provide style for the axis header.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:CategoryAxis Header="Category">
    <chart:CategoryAxis.HeaderStyle>
        <chart:LabelStyle FontFamily="Algerian" FontSize="13" Foreground="Blue"/>
    </chart:CategoryAxis.HeaderStyle>
</chart:CategoryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new CategoryAxis() { Header = "Category" };
chart.PrimaryAxis.HeaderStyle = new LabelStyle()
{
    FontFamily = new FontFamily("Calibri"),
    FontSize = 13,
    Foreground = new SolidColorBrush(Colors.Blue),
};

{% endhighlight %}

{% endtabs %}

![Axis header style in WinUI Chart](Axis_Images/WinUI_Chart_Axis_Header_styles.png)

## Template

The appearance of the header can be customized using the [HeaderTemplate]() property.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.Resources>
    <DataTemplate x:Key="headerTemplate">
        <Border BorderBrush="Blue" CornerRadius="5" BorderThickness="1">
            <TextBlock Text="Category" FontSize="12" FontStyle="Italic" FontWeight="Bold" Margin="3"/>
        </Border>
    </DataTemplate>
</chart:SfCartesianChart.Resources>
. . .
<chart:SfCartesianChart.PrimaryAxis>
    <chart:CategoryAxis HeaderTemplate="{StaticResource headerTemplate}">
    </chart:CategoryAxis>
</chart:SfCartesianChart.PrimaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new CategoryAxis()
{
    HeaderTemplate = chart.Resources["headerTemplate"] as DataTemplate
};

{% endhighlight %}

{% endtabs %}

![HeaderTemplate support for ChartAxis in WinUI Chart](Axis_images/WinUI_Chart_Axis_Header_template.png)