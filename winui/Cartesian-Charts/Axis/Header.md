---
layout: post
title: Header for axis in WinUI Cartesian Chart control | Syncfusion
description: This section explains about chart axis header, header style, header template and customization header apperance of chart axis in WPF chart.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Header in Chart Axis WPF Chart

## Header

In chart axis you can define any object as header using [Header]() property. The following code example demonstrates the defining header in primary and secondary axis. 

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:CategoryAxis Header="Category"/>
</chart:SfCartesianChart.PrimaryAxis>
<chart:SfCartesianChart.SecondaryAxis>
    <chart:NumericalAxis Header="Values"/>
</chart:SfCartesianChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis() { Header = "Category" };
chart.SecondaryAxis = new NumericalAxis() { Header = "Values" };

{% endhighlight %}

{% endtabs %}

![Header support for ChartAxis in WinUI](Axis_Images/WinUI_Chart_Axis_Header.png)

## Style for header

[HeaderStyle]() property is used to provide style for the axis header. The following code example explains header style customization.

{% tabs %}

{% highlight xaml %}

<chart:CategoryAxis Header="Category">
    <chart:CategoryAxis.HeaderStyle>
        <chart:LabelStyle FontFamily="Algerian" FontSize="13" Foreground="Blue"/>
    </chart:CategoryAxis.HeaderStyle>
</chart:CategoryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis() { Header = "Category" };
chart.PrimaryAxis.HeaderStyle = new LabelStyle()
{
    FontFamily = new FontFamily("Calibri"),
    FontSize = 13,
    Foreground = new SolidColorBrush(Colors.Blue),
};

{% endhighlight %}

{% endtabs %}

![Axis header style in WinUI Cartesian chart](Axis_Images/WinUI_Chart_Axis_Header_styles.png)

## Customization of header by HeaderTemplate

Default appearance of the header can be customized using [HeaderTemplate]() property. The following code snippet demonstrates the header customization.

{% tabs %}

{% highlight xaml %}

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

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{
    HeaderTemplate = chart.Resources["headerTemplate"] as DataTemplate
};

{% endhighlight %}

{% endtabs %}

![HeaderTemplate support for ChartAxis in WinUI](Axis_images/WinUI_Chart_Axis_Header_template.png)