---
layout: post
title: Spline and Spline Area Charts| SfChart | WinUI | Syncfusion
description: This section explains Spline and Spline Area Charts and its properties for customization in WinUI Charts (SfChart)
platform: WinUI
control: SfChart
documentation: ug
---

# Spline and Spline Area Charts in WinUI Chart (SfChart)

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

![Spline chart type in WinUI](Series_images/spline.png)

**Dashed Lines**

[`StrokeDashArray`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineSeries.html#Syncfusion_UI_Xaml_Charts_SplineSeries_StrokeDashArray) property of the [`SplineSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineSeries.html#) is used to render spline series with dashes.

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

![Spline chart type with StrokeDashArray in WinUI](Series_images/splinestrokedash.png)

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

![SplineArea chart type in WinUI](Series_images/splinearea.png)

## SplineType

[`Spline`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineSeries.html) and [`SplineArea`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineAreaSeries.html) series provide support for various spline type. The spline type of the series can be changed by using its [`SplineType`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SplineSeries.html#Syncfusion_UI_Xaml_Charts_SplineSeries_SplineTypeProperty) property. The following spline types are supported by Spline and SplineArea series:

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

![Natural spline support in WinUI Chart](Series_images/spline_natural.png)       

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

![Cardinal spline support in WinUI Chart](Series_images/spline_cardinal.png)

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

![Monotonic spline support in WinUI Chart](Series_images/spline_monotonic.png)

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

![Clamped spline support in WinUI Chart](Series_images/spline_clamped.png)