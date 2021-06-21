---
layout: post
title: Appearance in WinUI Circular Chart control | Syncfusion
description: This section explains about how to apply palettes and gradient in the Syncfusion WinUI Circular Chart (SfCircularChart) control
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Appearance in WinUI Circular Chart (SfCircularChart)

The appearance of [SfCircularChart]() can be customize by using the predefined palettes, custom palettes and gradient that allows to enrich the application.

## Palettes

Circular series provides options to apply different kinds of palettes. We have some predefined palette such as

* Metro
* AutumnBrights
* FloraHues
* Pineapple
* TomatoSpectrum
* RedChrome
* PurpleChrome
* BlueChrome
* GreenChrome
* Elite
* LightCandy
* SandyBeach

### Applying palette

Each palette applies a set of predefined brushes to the pie or doughnut series in a predefined order. [Metro]() palette is the default palette.

{% tabs %}

{% highlight xaml %}

<chart:PieSeries ItemsSource="{Binding Data}" 
                 XBindingPath="Product" 
                 YBindingPath="SalesRate">
</chart:PieSeries>


{% endhighlight %}

{% highlight c# %}

PieSeries series = new PieSeries() { Label = "Continents" };
. . .
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Predefined palette in WinUI Circular Chart](Appearance_images/WinUI_Circular_chart_Predefined_palette.png)

The following code example defined [`Palette`]() as [`GreenChrome`]().

{% tabs %}

{% highlight xaml %}

<chart:PieSeries Palette="GreenChrome"
                 ItemsSource="{Binding Data}" 
                 XBindingPath="Product" 
                 YBindingPath="SalesRate">

</chart:PieSeries>

{% endhighlight %}

{% highlight c# %}

PieSeries series = new PieSeries();
series.Palette = ChartColorPalette.GreenChrome;
. . .
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Palette support in WinUI Circular Chart](Appearance_images/WinUI_Circular_chart_GreenChrome_palette.png)

## Custom palette

[SfCircularChart]() provides support to define own brushes for chart with preferred order by using [CustomBrushes]() property of [ChartColorModel]() and [Palette]() value as [Custom]() as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<chart:PieSeries Palette="Custom">
    <chart:PieSeries.ColorModel>
        <chart:ChartColorModel>
            <chart:ChartColorModel.CustomBrushes>
                <SolidColorBrush Color="#4dd0e1"/>
                <SolidColorBrush Color="#26c6da"/>
                <SolidColorBrush Color="#00bcd4"/>
                <SolidColorBrush Color="#00acc1"/>
                <SolidColorBrush Color="#0097a7"/>
                <SolidColorBrush Color="#00838f"/>
            </chart:ChartColorModel.CustomBrushes>
        </chart:ChartColorModel>
    </chart:PieSeries.ColorModel>
</chart:PieSeries>

{% endhighlight %}

{% highlight c# %}

PieSeries series = new PieSeries();
series.Palette = ChartColorPalette.Custom;

ChartColorModel colorModel = new ChartColorModel();
colorModel.CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 77, 208, 225)));
colorModel.CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 38, 198, 218)));
colorModel.CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 188, 212)));
colorModel.CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 172, 193)));
colorModel.CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 151, 167)));
colorModel.CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 131, 143)));

series.ColorModel = colorModel;

{% endhighlight %}

{% endtabs %}

![Custom palette in WinUI Circular Chart](Appearance_images/WinUI_Circular_chart_Custom_palette.png)

## Applying gradient brushes

Gradient for the Circular chart can be set by using the [ColorModel]() property of the Circular series with the help of `LinearGradientBrush` or `RadialGradientBrush`.

The following code sample and screenshot illustrates how to apply the gradient brushes for chart using the [ColorModel]() property.

{% tabs %}

{% highlight xaml %}

<chart:PieSeries Palette="Custom">
    <chart:PieSeries.ColorModel>
        <chart:ChartColorModel>
                <chart:ChartColorModel.CustomBrushes>
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
                </chart:ChartColorModel.CustomBrushes>
            </chart:ChartColorModel>
    </chart:PieSeries.ColorModel>
</chart:PieSeries>


{% endhighlight %}

{% highlight c# %}

PieSeries series = new PieSeries();
series.Palette = ChartColorPalette.Custom;

ChartColorModel colorModel = new ChartColorModel();
LinearGradientBrush gradientColor1 = new LinearGradientBrush();
GradientStop stop1 = new GradientStop() { Offset = 1, Color = Color.FromArgb(255, 255, 231, 199) };
GradientStop stop2 = new GradientStop() { Offset = 0, Color = Color.FromArgb(255, 252, 182, 159) };
gradientColor1.GradientStops.Add(stop1);
gradientColor1.GradientStops.Add(stop2);
series.ColorModel = colorModel;

{% endhighlight %}

{% endtabs %}

![Gradient support in WinUI Circular Chart](Appearance_images/WinUI_Circular_Chart_Gradient_color.png)

## Segment color binding

The color of the each segment can be set by binding their corresponding model property from the `ItemsSource` collection to its [SegmentColorPath]() property of Circular series as follows.

{% tabs %}

{% highlight xaml %}

<chart:PieSeries ItemsSource="{Binding Data}" 
                 XBindingPath="Product" SegmentColorPath="SegmentColor"
                 YBindingPath="SalesRate"/>

{% endhighlight %}

{% highlight c# %}

public class ChartViewModel
{
    public List<Sales> Data { get; set; }

    public ChartViewModel()
    {
        Data = new List<Sales>()
        {
            new Sales(){Product = "iPad", SalesRate = 22, SegmentColor = new SolidColorBrush(Color.FromArgb(255, 152, 251, 152))},
            new Sales(){Product = "iPhone", SalesRate = 35, SegmentColor = new SolidColorBrush(Color.FromArgb(255, 255, 105, 180))},
            new Sales(){Product = "MacBook", SalesRate = 15, SegmentColor = new SolidColorBrush(Color.FromArgb(255, 255, 165, 0))},
            new Sales(){Product = "Mac", SalesRate = 8, SegmentColor = new SolidColorBrush(Color.FromArgb(255, 238, 130, 238))},
            new Sales(){Product = "Others", SalesRate = 10, SegmentColor = new SolidColorBrush(Color.FromArgb(255, 0, 255, 255))},
        };
    }
}

PieSeries series = new PieSeries();
series.XBindingPath = "Product";
series.YBindingPath = "SalesRate";
series.SegmentColorPath = "SegmentColor";
. . .
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Segment color binding support in WinUI Circular Chart](Appearance_images/WinUI_Circular_chart_ColorValuePath.png)

