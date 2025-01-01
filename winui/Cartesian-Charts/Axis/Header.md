---
layout: post
title: Header for axis in WinUI Chart control | Syncfusion
description: This section explains about chart axis header, header style, header template and its customization in WinUI chart (SfCartesianChart).
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: axis title in winui chart, winui sfcartesianchart axis title, winui chart axis title customization, syncfusion winui chart axis title, winui sfcartesianchart axis title configuration.
---

# Axis Title in WinUI Chart (SfCartesianChart)

The [Header](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_Header) property is used to set the title for the chart axis. It accepts any `UIElement` as content of axis title. 

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.XAxes>
    <chart:CategoryAxis Header="Category"/>
</chart:SfCartesianChart.XAxes>
<chart:SfCartesianChart.YAxes>
    <chart:NumericalAxis Header="Values"/>
</chart:SfCartesianChart.YAxes>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.XAxes.Add(new CategoryAxis() { Header = "Category" });
chart.YAxes.Add(new NumericalAxis() { Header = "Values" });

{% endhighlight %}

{% endtabs %}

![Header support for ChartAxis in WinUI Chart](Axis_Images/WinUI_Chart_Axis_Header.png)

## Style

The [HeaderStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_HeaderStyle) property is used to provide style for the axis header.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.XAxes>
    <chart:CategoryAxis Header="Category">
        <chart:CategoryAxis.HeaderStyle>
            <chart:LabelStyle FontFamily="Algerian"
							  FontSize="13"
							  Foreground="Blue"/>
        </chart:CategoryAxis.HeaderStyle>
    </chart:CategoryAxis>
</chart:SfCartesianChart.XAxes>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
CategoryAxis primaryAxis = new CategoryAxis() { Header = "Category" };
primaryAxis.HeaderStyle = new LabelStyle()
{
    FontFamily = new FontFamily("Calibri"),
    FontSize = 13,
    Foreground = new SolidColorBrush(Colors.Blue),
};
chart.XAxes.Add(primaryAxis);

{% endhighlight %}

{% endtabs %}

![Axis header style in WinUI Chart](Axis_Images/WinUI_Chart_Axis_Header_styles.png)

## Template

The appearance of the header can be customized using the [HeaderTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_HeaderTemplate) property.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.Resources>
    <DataTemplate x:Key="headerTemplate">
        <Border BorderBrush="Blue"
				CornerRadius="5"
				BorderThickness="1">
            <TextBlock Text="Category"
					   FontSize="12"
					   FontStyle="Italic" 
					   FontWeight="Bold"
					   Margin="3"/>
        </Border>
    </DataTemplate>
</chart:SfCartesianChart.Resources>
. . .
<chart:SfCartesianChart.XAxes>
    <chart:CategoryAxis HeaderTemplate="{StaticResource headerTemplate}">
    </chart:CategoryAxis>
</chart:SfCartesianChart.XAxes>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
CategoryAxis primaryAxis = new CategoryAxis()
{
    HeaderTemplate = chart.Resources["headerTemplate"] as DataTemplate
};
chart.XAxes.Add(primaryAxis);

{% endhighlight %}

{% endtabs %}

![HeaderTemplate support for ChartAxis in WinUI Chart](Axis_images/WinUI_Chart_Axis_Header_template.png)