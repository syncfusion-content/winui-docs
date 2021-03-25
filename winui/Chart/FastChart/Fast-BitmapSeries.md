---
layout: post
title: Fast Chart | SfChart | WinUI | Syncfusion
description: Fast chart support which render collection of data points using WritableBitmap in WinUI Charts (SfChart)
platform: WinUI
control: SfChart
documentation: ug
---

# Fast Bitmap Series in WinUI Charts (SfChart)

A fast bitmap series is a special kind of series that can render a collection with huge number of data points. A fast bitmap series displays a series of segments rendered using WritableBitmap. 

## FastLineBitmap Chart

[`FastLineBitmapSeries`]() displays a series of line segments rendered using WritableBitmap. The advantage of FastLineBitmapSeries is, its renders a million data point in a fraction of seconds.

The following code example shows how to use the fast line bitmap series:

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

N> As it was rendered using bitmap, there might be some jagged lines at edges. This is can be reduced using [`EnableAntiAliasing`]() property.

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

[`FastColumnBitmapSeries`]() is used to boost up the performance of the column series.

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

[`FastBarBitmapSeries`]() is used to boost up the performance of the bar series.

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

[`FastScatterBitmapSeries`]() used to render high number scatter points. The [`ScatterHeight`]() and [`ScatterWidth`]() also available as in ScatterSeries. [`ShapeType`]() is used to change the rendering shape of fast scatter bitmap series. The available shapes are [`Cross`](), [`Diamond`](), [`Ellipse`](), [`Hexagon`](), [`InvertedTriangle`](), [`Pentagon`](), [`Plus`](), [`Rectangle`]() and [`Triangle`]().

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

[`FastStepLineBitmapSeries`]() is the high performance version of step line series.

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

The anti aliasing mode can be enabled using [`EnableAntiAliasing`]() property of FastStepLineBitmapSeries as in below code snippet:

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