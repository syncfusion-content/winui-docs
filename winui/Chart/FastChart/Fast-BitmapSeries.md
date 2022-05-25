---
layout: post
title: Fast Bitmap Series in WinUI Chart control | Syncfusion
description: Learn here all about Fast Bitmap Series feature of Syncfusion WinUI Chart (SfChart) control and more.
platform: WinUI
control: SfChart
documentation: ug
---

# Fast Bitmap Series in WinUI Chart

A fast bitmap series is a special kind of series that can render a collection with a huge number of data points using `WriteableBitmap.` 

## FastLineBitmap Chart

[`FastLineBitmapSeries`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastLineBitmapSeries.html) displays a series of line segments rendered using `WriteableBitmap.` The advantage of FastLineBitmapSeries is that it can render a million data points in a fraction of seconds.

The following code example shows how to use the fast line bitmap series.

{% tabs %}

{% highlight xaml %}

<chart:FastLineBitmapSeries ItemsSource="{Binding Data}"

XBindingPath="XValue" YBindingPath="YValue"/>

{% endhighlight %}

{% highlight c# %}

FastLineBitmapSeries series = new FastLineBitmapSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "XValue",

    YBindingPath = "YValue"

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![FastLineBitmap chart type in WinUI](FastChart_images/fastlinebitmap_chart.png)

N> As it was rendered using bitmap, there may be some jagged lines at the edges. This can be reduced using the [`EnableAntiAliasing`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastLineBitmapSeries.html#Syncfusion_UI_Xaml_Charts_FastLineBitmapSeries_EnableAntiAliasing) property.

{% tabs %}

{% highlight xaml %}

<chart:FastLineBitmapSeries EnableAntiAliasing="True" ItemsSource="{Binding Data}"

XBindingPath="XValue" YBindingPath="YValue"/>

{% endhighlight %}

{% highlight c# %}

FastLineBitmapSeries series = new FastLineBitmapSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "XValue",

    YBindingPath = "YValue",

    EnableAntiAliasing = true

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![AntiAliasing support for fast line bitmap chart in WinUI](FastChart_images/fastlinebitmap_chart_antialiasing.png)


## FastColumnBitmap Chart

[`FastColumnBitmapSeries`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastColumnBitmapSeries.html) is used to improve the performance of the column series.

{% tabs %}

{% highlight xaml %}

<chart:FastColumnBitmapSeries ItemsSource="{Binding Data}" 

XBindingPath="XValue" YBindingPath="YValue"/>

{% endhighlight %}

{% highlight c# %}

FastColumnBitmapSeries series = new FastColumnBitmapSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "XValue",

    YBindingPath = "YValue"

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![FastColumnBitmap chart type in WinUI](FastChart_images/fastcolumnbitmap_chart.png)


## FastBarBitmap Chart

[`FastBarBitmapSeries`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastBarBitmapSeries.html) is used to improve the performance of the bar series.

{% tabs %}

{% highlight xaml %}

<chart:FastBarBitmapSeries ItemsSource="{Binding Data}" 

XBindingPath="XValue" YBindingPath="YValue"/>

{% endhighlight %}

{% highlight c# %}

FastBarBitmapSeries series = new FastBarBitmapSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "XValue",

    YBindingPath = "YValue"

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![FastBarBitmap chart type in WinUI](FastChart_images/fastbarbitmap_chart.png)


## FastScatterBitmap Chart

[`FastScatterBitmapSeries`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastScatterBitmapSeries.html) is used to render a large number of scatter points. The [`ScatterHeight`]() and [`ScatterWidth`]() are also available as in [`ScatterSeries`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ScatterSeries.html). [`ShapeType`]() is used to change the rendering shape of a fast scatter bitmap series. The available shapes are [`Cross`](), [`Diamond`](), [`Ellipse`](), [`Hexagon`](), [`InvertedTriangle`](), [`Pentagon`](), [`Plus`](), [`Rectangle`](), and [`Triangle`]().

{% tabs %}

{% highlight xaml %}

<chart:FastScatterBitmapSeries ItemsSource="{Binding Data}"                         

XBindingPath="XValue" YBindingPath="YValue" 

ScatterHeight="7" ScatterWidth="7"/>

{% endhighlight %}

{% highlight C# %}

FastScatterBitmapSeries series = new FastScatterBitmapSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "XValue",

    YBindingPath = "YValue",

    ScatterHeight = 7,

    ScatterWidth = 7

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![FastScatterBitmap chart type in WinUI](FastChart_images/fastscatterbitmap_chart.png)


## FastStepLineBitmap Chart

[`FastStepLineBitmapSeries`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastStepLineBitmapSeries.html) is the high-performance version of step line series.

{% tabs %}

{% highlight xaml %}

<chart:FastStepLineBitmapSeries ItemsSource="{Binding Data}"

XBindingPath="XValue" YBindingPath="YValue" />

{% endhighlight %}

{% highlight c# %}

FastStepLineBitmapSeries series = new FastStepLineBitmapSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "XValue",

    YBindingPath = "YValue"

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![FastStepLineBitmap chart type in WinUI](FastChart_images/faststeplinebitmap_chart.png)

The anti-aliasing mode can be enabled using the [`EnableAntiAliasing`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastLineBitmapSeries.html#Syncfusion_UI_Xaml_Charts_FastLineBitmapSeries_EnableAntiAliasing) property of FastStepLineBitmapSeries as shown in the following code sample.

{% tabs %}

{% highlight xaml %}

<chart:FastStepLineBitmapSeries EnableAntiAliasing="True" ItemsSource="{Binding Data}"

XBindingPath="XValue" YBindingPath="YValue" />

{% endhighlight %}

{% highlight c# %}

FastStepLineBitmapSeries series = new FastStepLineBitmapSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "XValue",

    YBindingPath = "YValue",

    EnableAntiAliasing = true

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![AntiAliasing support for FastStepLineBitmap chart type in WinUI](FastChart_images/faststeplinebitmap_chart_antialiasing.png)
