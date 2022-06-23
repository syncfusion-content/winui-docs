---
layout: post
title: Funnel and Pyramid in WinUI Chart control | Syncfusion
description: Learn here all about Funnel and Pyramid features of Syncfusion WinUI Chart (SfChart) control and more.
platform: WinUI
control: SfChart
documentation: ug
---

# Funnel and Pyramid in WinUI Chart

## Pyramid

[`PyramidSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PyramidSeries.html#Syncfusion_UI_Xaml_Charts_PyramidSeries) has the form of a triangle with lines dividing it into sections, and each section has a different width. Depending on the Y co-ordinates, this width indicates a level of hierarchy among other categories.

{% tabs %}

{% highlight xaml %}

<chart:PyramidSeries XBindingPath="Category" ItemsSource="{Binding Data}" YBindingPath="Value"/>

{% endhighlight %}

{% highlight c# %}

PyramidSeries series = new PyramidSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Category",

    YBindingPath = "Value"

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Pyramid chart type in WinUI](Series_images/pyramid_chart.png)


The [`PyramidMode`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PyramidSeries.html#Syncfusion_UI_Xaml_Charts_PyramidSeries_PyramidMode) is used to define the rendering mode, such as [`Surface`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPyramidMode.html) or [`Linear`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPyramidMode.html) pyramid segments.

**PyramidMode** **as** **Surface**

{% tabs %}

{% highlight xaml %}

<chart:PyramidSeries XBindingPath="Category" PyramidMode="Surface" ItemsSource="{Binding Data}" YBindingPath="Value"/>

{% endhighlight %}

{% highlight c# %}

PyramidSeries series = new PyramidSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Category",

    YBindingPath = "Value",

    PyramidMode = ChartPyramidMode.Surface

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Pyramid modes in WinUI Chart](Series_images/pyramid_surface.png)


**PyramidMode** **as** **Linear**

{% tabs %}

{% highlight xaml %}

<chart:PyramidSeries XBindingPath="Category" PyramidMode="Linear" ItemsSource="{Binding Data}" YBindingPath="Value"/>

{% endhighlight %}

{% highlight c# %}

PyramidSeries series = new PyramidSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Category",

    YBindingPath = "Value",

    PyramidMode = ChartPyramidMode.Linear

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Pyramid modes in WinUI Chart](Series_images/pyramid_linear.png)

## Funnel

[`FunnelSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.FunnelSeries.html#Syncfusion_UI_Xaml_Charts_FunnelSeries) is similar to [`PyramidSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PyramidSeries.html#Syncfusion_UI_Xaml_Charts_PyramidSeries), displays data in a funnel shape that equals to 100% when totaled. It is a single series, representing data as portions of 100%, and does not use any axes. 

The following code example shows how to use the funnel series:

{% tabs %}

{% highlight xaml %}

<chart:FunnelSeries XBindingPath="Category" ItemsSource="{Binding Data}" YBindingPath="Value"/>

{% endhighlight %}

{% highlight c# %}

FunnelSeries series = new FunnelSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Category",

    YBindingPath = "Value",

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Funnel chart type in WinUI](Series_images/funnel_chart.png)


### Funnel mode

The [`FunnelMode`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.FunnelSeries.html#Syncfusion_UI_Xaml_Charts_FunnelSeries_FunnelMode) defines a rendering mode for the funnel series that specifies where to bind your values (to height or width). The following example demonstrates [`ValueIsHeight`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartFunnelMode.html) and [`ValueIsWidth`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartFunnelMode.html) funnel modes:

**ValueIsHeight**

{% tabs %}

{% highlight xaml %}

<chart:FunnelSeries XBindingPath="Category" ItemsSource="{Binding Data}" FunnelMode="ValueIsHeight" YBindingPath="Value"/>

{% endhighlight %}

{% highlight c# %}

FunnelSeries series = new FunnelSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Category",

    YBindingPath = "Value",

    FunnelMode = ChartFunnelMode.ValueIsHeight

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Funnel modes in WinUI Chart](Series_images/funnel_mode_valueisheight.png)

**ValueIsWidth**

{% tabs %}

{% highlight xaml %}

<chart:FunnelSeries XBindingPath="Category" ItemsSource="{Binding Data}" FunnelMode="ValueIsWidth" YBindingPath="Value"/>

{% endhighlight %}

{% highlight c# %}

FunnelSeries series = new FunnelSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Category",

    YBindingPath = "Value",

    FunnelMode = ChartFunnelMode.ValueIsWidth

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Funnel modes in WinUI Chart](Series_images/funnel_mode_valueiswidth.png)

### Explode segments

The following properties are used to explode the individual segments in Funnel and Pyramid.

* [`ExplodeAll`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.AccumulationSeriesBase.html#Syncfusion_UI_Xaml_Charts_AccumulationSeriesBase_ExplodeAll) - Used to explode all the segments of these series.
* [`ExplodeIndex`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.AccumulationSeriesBase.html#Syncfusion_UI_Xaml_Charts_AccumulationSeriesBase_ExplodeIndex) - Used to explode any specific segment.
* [`ExplodeOffset`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.TriangularSeriesBase.html#Syncfusion_UI_Xaml_Charts_TriangularSeriesBase_ExplodeOffset) - Used to define the explode distance like ExplodeRadius for Pie.
* [`ExplodeOnMouseClick`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.AccumulationSeriesBase.html#Syncfusion_UI_Xaml_Charts_AccumulationSeriesBase_ExplodeOnMouseClick) - Used to explode the segment when the segment is clicked.

**Explode** **Offset**

{% tabs %}

{% highlight xaml %}

<chart:FunnelSeries XBindingPath="Category" ItemsSource="{Binding Data}"   

ExplodeIndex="4"  ExplodeOffset="70" YBindingPath="Value">

</chart:FunnelSeries>

{% endhighlight %}

{% highlight c# %}

FunnelSeries series = new FunnelSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Category",

    YBindingPath = "Value",

    ExplodeIndex = 4,

    ExplodeOffset = 70

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Exploding the segments of accumlation series in WinUI Chart](Series_images/funnel_explode.png)

**Gap** **Ratio**

The gap between each segment is calculated using the [`GapRatio`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.TriangularSeriesBase.html#Syncfusion_UI_Xaml_Charts_TriangularSeriesBase_GapRatio) property, as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<chart:FunnelSeries XBindingPath="Category" ItemsSource="{Binding Data}"     

GapRatio="0.5" YBindingPath="Value">

</chart:FunnelSeries>

{% endhighlight %}

{% highlight c# %}

FunnelSeries series = new FunnelSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Category",

    YBindingPath = "Value",

    GapRatio = 0.5

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Gap ratio between segments in WinUI Chart](Series_images/funnel_gapratio.png)
