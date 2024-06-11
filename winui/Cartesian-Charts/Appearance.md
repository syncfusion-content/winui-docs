---
layout: post
title: Appearance in WinUI Chart control | Syncfusion
description: This section explains about how to apply palettes and gradient in the Syncfusion WinUI Chart(SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: appearance in winui chart, winui sfcartesianchart appearance, winui chart appearance customization, syncfusion winui chart appearance, winui sfcartesianchart appearance configuration.
---

# Appearance in WinUI Chart (SfCartesianChart)

The appearance of [SfCartesianChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html) can be customized by using the predefined brushes, custom brushes and gradient, which allows to enrich the application.

## Applying PaletteBrushes for Chart

By default, chart applies a set of predefined brushes to the series in a predefined order. [SfCartesianChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html) provides [PaletteBrushes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_PaletteBrushes) property for applying various kinds of custom palettes brushes.

### Predefined PaletteBrushes

Currently, Chart supports only one predefined palette and it is the default palette for SfCartesianChart. The following screenshot shows the default appearance of multiple series.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart x:Name="chart">

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Predefined PaletteBrushes in WinUI Chart](Appearance_images/WinUI_chart_predefined_palette.png)

### Custom PaletteBrushes

[SfCartesianChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html) provides support to define own brushes for the chart with preferred order by using the [PaletteBrushes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_PaletteBrushes) property, as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart x:Name="chart" PaletteBrushes="{Binding CustomBrushes}">
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
List<Brush> CustomBrushes = new List<Brush>();
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 38, 198, 218)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 172, 193)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 151, 167)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 131, 143)));

this.chart.PaletteBrushes = CustomBrushes;
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Custom PaletteBrushes in WinUI Chart](Appearance_images/WinUI_chart_custom_paletteBrushes.png)

## Applying PaletteBrushes for Series

Cartesian chart provides support to set the palette to series for applying predefined brushes to the segment. The following code example shows you how to set the [PaletteBrushes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeries.html#Syncfusion_UI_Xaml_Charts_ChartSeries_PaletteBrushes) for the series.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Resources>
    <BrushCollection x:Key="customBrushes">
        <SolidColorBrush Color="#26c6da"/>
        <SolidColorBrush Color="#00bcd4"/>
        <SolidColorBrush Color="#00acc1"/>
        <SolidColorBrush Color="#0097a7"/>
        <SolidColorBrush Color="#00838f"/>
    </BrushCollection>
</chart:SfCartesianChart.Resources>

<chart:SfCartesianChart.Series>
    <chart:ColumnSeries ItemsSource="{Binding Data}"  
                        XBindingPath="Demand" 
                        YBindingPath="Year2010" 
                        PaletteBrushes="{StaticResource customBrushes}">        
    </chart:ColumnSeries>
</chart:SfCartesianChart.Series>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
List<Brush> CustomBrushes = new List<Brush>();
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 38, 198, 218)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 188, 212)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 172, 193)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 151, 167)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 131, 143)));

ColumnSeries series = new ColumnSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2010",
    PaletteBrushes = CustomBrushes,
};
. . .
chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Custom PaletteBrushes in WinUI Chart](Appearance_images/WinUI_chart_custom_palette.png)

## Applying Gradient

Gradient for the chart can be set by using the [PaletteBrushes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeries.html#Syncfusion_UI_Xaml_Charts_ChartSeries_PaletteBrushes) property with the help of `LinearGradientBrush` or `RadialGradientBrush`.

The following code sample and screenshot illustrates how to apply the gradient brushes for the series using the [PaletteBrushes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeries.html#Syncfusion_UI_Xaml_Charts_ChartSeries_PaletteBrushes) property.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Resources>
    <BrushCollection x:Key="customBrushes">
        <LinearGradientBrush>
            <GradientStop Offset="1" Color="#FFE7C7" />
            <GradientStop Offset="0" Color="#FCB69F" />
        </LinearGradientBrush>
        <LinearGradientBrush>
            <GradientStop Offset="1" Color="#fadd7d" />
            <GradientStop Offset="0" Color="#fccc2d" />
        </LinearGradientBrush>
        <LinearGradientBrush>
            <GradientStop Offset="1" Color="#DCFA97" />
            <GradientStop Offset="0" Color="#96E6A1" />
        </LinearGradientBrush>
        <LinearGradientBrush>
            <GradientStop Offset="1" Color="#DDD6F3" />
            <GradientStop Offset="0" Color="#FAACA8" />
        </LinearGradientBrush>
        <LinearGradientBrush>
            <GradientStop Offset="1" Color="#A8EAEE" />
            <GradientStop Offset="0" Color="#7BB0F9" />
        </LinearGradientBrush>
    </BrushCollection>
</chart:SfCartesianChart.Resources>

<chart:SfCartesianChart.Series>
    <chart:ColumnSeries ItemsSource="{Binding Data}"  
                        XBindingPath="Demand" 
                        YBindingPath="Year2010" 
                        PaletteBrushes="{StaticResource customBrushes}">        
    </chart:ColumnSeries>
</chart:SfCartesianChart.Series>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
...
List<Brush> CustomBrushes = new List<Brush>();
LinearGradientBrush gradientColor1 = new LinearGradientBrush();
GradientStop stop1 = new GradientStop() 
{
    Offset = 1, 
    Color = Color.FromArgb(255, 255, 231, 199) 
};

GradientStop stop2 = new GradientStop() 
{
    Offset = 0, 
    Color = Color.FromArgb(255, 252, 182, 159)
};

gradientColor1.GradientStops.Add(stop1);
gradientColor1.GradientStops.Add(stop2);

LinearGradientBrush gradientColor2 = new LinearGradientBrush();
stop1 = new GradientStop() 
{
    Offset = 1, 
    Color = Color.FromArgb(255, 250, 221, 125) 
};

stop2 = new GradientStop() 
{
    Offset = 0, 
    Color = Color.FromArgb(255, 252, 204, 45) 
};

gradientColor2.GradientStops.Add(stop1);
gradientColor2.GradientStops.Add(stop2);

...
CustomBrushes.Add(gradientColor1);
CustomBrushes.Add(gradientColor2);
...
ColumnSeries series = new ColumnSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2010",
    PaletteBrushes = CustomBrushes,
};
chart.Series.Add(series);
. . .            
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Gradient support in WinUI Chart](Appearance_images/WinUI_chart_gradient_color.png)