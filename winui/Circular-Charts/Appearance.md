---
layout: post
title: Appearance in WinUI Chart control | Syncfusion
description: This section explains about how to apply palettes and gradient in the Syncfusion WinUI Chart (SfCircularChart) control
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Appearance in WinUI Chart (SfCircularChart)

The appearance of [SfCircularChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCircularChart.html) can be customized by using the predefined palettes, custom palettes and gradient, which allows to enrich the application.

## Default PaletteBrushes

Default palette applies a set of predefined brushes to the series in a predefined order.

{% tabs %}

{% highlight xaml %}

<chart:PieSeries ItemsSource="{Binding Data}" 
                 XBindingPath="Product" 
                 YBindingPath="SalesRate">
</chart:PieSeries>


{% endhighlight %}

{% highlight c# %}

PieSeries series = new PieSeries() { ItemsSource= new ViewModel().Data, XBindingPath="Product", YBindingPath="SalesRate" };
. . .
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Predefined palette in WinUI Chart](Appearance_images/winui_pie_chart_predefined_palette.png)

## Custom PaletteBrushes

[SfCircularChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCircularChart.html) provides support to define own brushes for chart with preferred order by using the [PaletteBrushes]() property, as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Resources>
            <BrushCollection x:Key="customBrushes">
                <SolidColorBrush Color="#4dd0e1"/>
                <SolidColorBrush Color="#26c6da"/>
                <SolidColorBrush Color="#00bcd4"/>
                <SolidColorBrush Color="#00acc1"/>
                <SolidColorBrush Color="#0097a7"/>
                <SolidColorBrush Color="#00838f"/>
            </BrushCollection>
    </chart:SfCircularChart.Resources>

<chart:PieSeries ItemsSource="{Binding Data}" 
                 XBindingPath="Product" 
                 YBindingPath="SalesRate"
                 PaletteBrushes="{StaticResource customBrushes}" />
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();

List<Brush> CustomBrushes = new List<Brush>();
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 77, 208, 225)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 38, 198, 218)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 188, 212)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 172, 193)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 151, 167)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 131, 143)));

series.PaletteBrushes = CustomBrushes;
. . .
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Custom PaletteBrushes in WinUI Chart](Appearance_images/winui_pie_chart_custom_palette.png)

## Applying Gradient

Gradient for the circular chart can be set by using the [PaletteBrushes]() property of the series with the help of `LinearGradientBrush` or `RadialGradientBrush`.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Resources>
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
    </chart:SfCircularChart.Resources>

<chart:PieSeries ItemsSource="{Binding Data}" 
                 XBindingPath="Product" 
                 YBindingPath="SalesRate"
                 PaletteBrushes="{StaticResource customBrushes}" />
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();

List<Brush> customBrushes = new List<Brush>();
LinearGradientBrush gradientColor1 = new LinearGradientBrush();
GradientStop stop1 = new GradientStop() { Offset = 1, Color = Color.FromArgb(255, 255, 231, 199) };
GradientStop stop2 = new GradientStop() { Offset = 0, Color = Color.FromArgb(255, 252, 182, 159) };
gradientColor1.GradientStops.Add(stop1);
gradientColor1.GradientStops.Add(stop2);

customBrushes.Add(gradientColor1);

series.PaletteBrushes = customBrushes;
. . .
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Gradient support in WinUI Chart](Appearance_images/winui_pie_chart_gradient.png)
