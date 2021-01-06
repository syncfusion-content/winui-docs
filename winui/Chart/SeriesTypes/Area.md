---
layout: post
title: Area and Step Area Charts| SfChart | WinUI | Syncfusion
description: This section explains Area and Step Area Charts and its properties for customization in WinUI Charts (SfChart)
platform: WinUI
control: SfChart
documentation: ug
---

# Area Charts in WinUI Chart (SfChart)

## Area 
[`AreaSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.AreaSeries.html#) is rendered using a collection of line segments connected to form a closed loop area, filled with the specified color.

The following code example initializes the AreaSeries:

{% tabs %}

{% highlight xaml %}

<chart:AreaSeries XBindingPath="XValue" YBindingPath="YValue" ItemsSource="{Binding Data}"/>   

{% endhighlight %}

{% highlight c# %}

AreaSeries series = new AreaSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "XValue",

    YBindingPath = "YValue",

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Area chart type in WinUI](Series_images/area.png)

## Step Area

[`StepAreaSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.StepAreaSeries.html#) is similar to AreaSeries but it does not use the shortest distance to connect two data points using Bezier curves. Instead, this ChartSeries uses vertical and horizontal lines to connect the data points in a series forming a step-like progression.

{% tabs %}

{% highlight xaml %}

<chart:StepAreaSeries ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue"/>

{% endhighlight %}

{% highlight c# %}

StepAreaSeries series = new StepAreaSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "XValue",

    YBindingPath = "YValue",

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![StepArea chart type in WinUI](Series_images/steparea.png)

## Closed Area

If you wish to draw the open area series (Area with stroke only at top), SfChart provides [`IsClosed`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.AreaSeries.html#Syncfusion_UI_Xaml_Charts_AreaSeries_IsClosed) property. By default, this property is true.

{% tabs %}

{% highlight xaml %}

<chart:AreaSeries IsClosed="False" XBindingPath="XValue" 

YBindingPath="YValue" ItemsSource="{Binding Data}" /> 

{% endhighlight %}

{% highlight c# %}

AreaSeries series = new AreaSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "XValue",

    YBindingPath = "YValue",

    IsClosed = true,

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Closed area chart type in WinUI](Series_images/closedarea.png)