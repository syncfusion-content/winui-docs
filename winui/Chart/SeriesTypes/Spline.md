---
layout: post
title: Spline in WinUI Chart control | Syncfusion
description: Learn here all about Spline support in Syncfusion WinUI Chart (SfChart) control with Area, Type support and more.
platform: WinUI
control: SfChart
documentation: ug
---

# Spline in WinUI Chart

## Spline

[`SplineSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineSeries.html#) resembles line series, but the difference between them is that instead of connecting the data points with line segments, the data points are connected by smooth Bezier curves.

{% tabs %}

{% highlight xaml %}

<chart:SplineSeries XBindingPath="Year" ItemsSource="{Binding Data}" YBindingPath="Value1"/>

<chart:SplineSeries XBindingPath="Year" ItemsSource="{Binding Data}" YBindingPath="Value2"/>

{% endhighlight %}

{% highlight c# %}

SplineSeries series1 = new SplineSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Year",

    YBindingPath = "Value1",

};

SplineSeries series2 = new SplineSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Year",

    YBindingPath = "Value2",

};

chart.Series.Add(series1);

chart.Series.Add(series2);

{% endhighlight %}

{% endtabs %}

![Spline chart type in WinUI](Series_images/spline_chart.png)

**Dashed Lines**

The [`StrokeDashArray`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineSeries.html#Syncfusion_UI_Xaml_Charts_SplineSeries_StrokeDashArray) property of the [`SplineSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineSeries.html#) is used to render spline series with dashes.

{% tabs %}

{% highlight xaml %}

<chart:SplineSeries XBindingPath="Year" ItemsSource="{Binding Data}" YBindingPath="Value1" StrokeDashArray="5,3"/>

<chart:SplineSeries XBindingPath="Year" ItemsSource="{Binding Data}" YBindingPath="Value2" StrokeDashArray="5,3"/>

{% endhighlight %}

{% highlight c# %}

SplineSeries series1 = new SplineSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Year",

    YBindingPath = "Value1",

};

SplineSeries series2 = new SplineSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Year",

    YBindingPath = "Value2",

};

DoubleCollection doubleCollection = new DoubleCollection();
doubleCollection.Add(5);
doubleCollection.Add(3);

series1.StrokeDashArray = doubleCollection;
series2.StrokeDashArray = doubleCollection;

chart.Series.Add(series1);
chart.Series.Add(series2);

{% endhighlight %}

{% endtabs %}

![Spline chart type with StrokeDashArray in WinUI](Series_images/spline_strokedash.png)

## Spline Area

[`SplineAreaSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineAreaSeries.html#) connects a series of data points using smooth Bezier line curves, with the underlying areas filled. 

{% tabs %}

{% highlight xaml %}

<chart:SplineAreaSeries ItemsSource="{Binding Products}" XBindingPath="ProdName" YBindingPath="Price"/>

{% endhighlight %}

{% highlight c# %}

SplineAreaSeries series = new SplineAreaSeries()
{

    ItemsSource = new ViewModel().Products,

    XBindingPath = "ProdName",

    YBindingPath = "Price",

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![SplineArea chart type in WinUI](Series_images/splinearea_chart.png)

## SplineType

The [`Spline`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineSeries.html) and [`SplineArea`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineAreaSeries.html) series support various spline types. The spline type of the series can be changed by using the [`SplineType`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineSeries.html#Syncfusion_UI_Xaml_Charts_SplineSeries_SplineTypeProperty) property. The following spline types are supported by Spline and SplineArea series:

       * Natural
       * Monotonic
       * Cardinal
       * Clamped

**Natural**

The following code illustrates how to set the [`SplineType`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineSeries.html#Syncfusion_UI_Xaml_Charts_SplineSeries_SplineType) value as [`Natural`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineType.html).

{% tabs %}

{% highlight xaml %}

<chart:SplineSeries SplineType="Natural">

</chart:SplineSeries>

{% endhighlight %}

{% highlight c# %}

SplineSeries series = new SplineSeries();

series.SplineType = SplineType.Natural;

{% endhighlight %}

{% endtabs %}

![Natural spline support in WinUI Chart](Series_images/spline_chart_natural.png)       

**Cardinal**

The following code illustrates how to set the [`SplineType`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineSeries.html#Syncfusion_UI_Xaml_Charts_SplineSeries_SplineType) value as [`Cardinal`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineType.html).

{% tabs %}

{% highlight xaml %}

<chart:SplineSeries SplineType="Cardinal">

</chart:SplineSeries>

{% endhighlight %}

{% highlight c# %}

SplineSeries series = new SplineSeries();

series.SplineType = SplineType.Cardinal;

{% endhighlight %}

{% endtabs %}

![Cardinal spline support in WinUI Chart](Series_images/spline_chart_cardinal.png)

**Monotonic**

The following code illustrates how to set the [`SplineType`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineSeries.html#Syncfusion_UI_Xaml_Charts_SplineSeries_SplineTypeProperty) value as Monotonic.

{% tabs %}

{% highlight xaml %}

<chart:SplineSeries SplineType="Monotonic">

</chart:SplineSeries>

{% endhighlight %}

{% highlight c# %}

SplineSeries series = new SplineSeries();

series.SplineType = SplineType.Monotonic;

{% endhighlight %}

{% endtabs %}

![Monotonic spline support in WinUI Chart](Series_images/spline_chart_monotonic.png)

**Clamped**

The following code illustrates how to set the [`SplineType`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineSeries.html#Syncfusion_UI_Xaml_Charts_SplineSeries_SplineTypeProperty) value as Clamped.

{% tabs %}

{% highlight xaml %}

<chart:SplineSeries SplineType="Clamped">

</chart:SplineSeries>

{% endhighlight %}

{% highlight c# %}

SplineSeries series = new SplineSeries();

series.SplineType = SplineType.Clamped;

{% endhighlight %}

{% endtabs %}

![Clamped spline support in WinUI Chart](Series_images/spline_chart_clamped.png)
