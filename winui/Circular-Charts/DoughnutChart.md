---
layout: post
title: Doughnut chart in WinUI Chart control | Syncfusion
description: Learn here all about doughnut chart and its features in Syncfusion WinUI Chart (SfCircularChart) control.
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Doughnut Chart in WinUI Chart (SfCircularChart)

[DoughnutSeries]() is similar to [PieSeries](). It is used to show the relationship between parts of data and whole data. To render a [DoughnutSeries]() in circular chart, create an instance of the [DoughnutSeries]() and add it to the [Series]() collection property of [SfCircularChart]().

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>

    <chart:SfCircularChart.Series>
        <chart:DoughnutSeries ItemsSource="{Binding Data}" 
                              XBindingPath="Product" 
                              YBindingPath="SalesRate" />
    </chart:SfCircularChart.Series>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();

DoughnutSeries series = new DoughnutSeries();
series.XBindingPath = "Product";
series.YBindingPath = "SalesRate";

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Doughnut series type in WinUI Circular chart](Series_images/doughnut_chart.png)

### Doughnut coefficient

The [DoughnutCoefficient]() property of doughnut series is used to define the inner circle. It also has [DoughnutSize]() property, which is used to define the size for this series, similar to [CircularCoefficient]() in `PieSeries`.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>

    <chart:SfCircularChart.Series>
        <chart:DoughnutSeries ItemsSource="{Binding Data}" DoughnutCoefficient="0.7"
                          XBindingPath="Product" 
                          YBindingPath="SalesRate" />
    </chart:SfCircularChart.Series>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();

DoughnutSeries series = new DoughnutSeries();
series.XBindingPath = "Product";
series.YBindingPath = "SalesRate";
series.DoughnutCoefficient = 0.7;

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Doughnut coefficient support in WinUI Circular Chart](Series_images/doughnut_coefficient.png)

### Doughnut size

The size of doughnut series can be customized by using the [DoughnutSize]() property. The following code illustrates how to use this property in series.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>

    <chart:SfCircularChart.Series>
        <chart:DoughnutSeries DoughnutSize="0.8" />
        <chart:DoughnutSeries DoughnutSize="0.8" />
    </chart:SfCircularChart.Series>

</chart:SfCircularChart>
{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();

DoughnutSeries series1 = new DoughnutSeries();
. . .
series1.DoughnutSize = 0.8;
chart.Series.Add(series1);

DoughnutSeries series2 = new DoughnutSeries();
. . .
series2.DoughnutSize = 0.8;
chart.Series.Add(series2);

{% endhighlight %}

{% endtabs %}

![Doughnut size support in WinUI Circular Chart](Series_images/doughnut_size.png)

## Multiple Doughnut

Added the multiple Doughnut series added in the [SfCircularChart]()

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>

    <chart:SfCircularChart.Series>
         <chart:SfCircularChart.Series>
                <chart:DoughnutSeries ItemsSource="{Binding Data}" 
                         XBindingPath="Product" 
                         YBindingPath="SalesRate1">
                </chart:DoughnutSeries>
                <chart:DoughnutSeries ItemsSource="{Binding Data}" 
                         XBindingPath="Product" 
                         YBindingPath="SalesRate2">
                </chart:DoughnutSeries>
                <chart:DoughnutSeries ItemsSource="{Binding Data}" 
                         XBindingPath="Product" 
                         YBindingPath="SalesRate3">
                </chart:DoughnutSeries>
            </chart:SfCircularChart.Series>
    </chart:SfCircularChart.Series>

</chart:SfCircularChart>
{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();

DoughnutSeries series1 = new DoughnutSeries();
series1.XBindingPath = "Product";
series1.YBindingPath = "SalesRate1";

DoughnutSeries series2 = new DoughnutSeries();
series2.XBindingPath = "Product";
series2.YBindingPath = "SalesRate2";

DoughnutSeries series3 = new DoughnutSeries();
series3.XBindingPath = "Product";
series3.YBindingPath = "SalesRate3";

chart.Series.Add(series1);
chart.Series.Add(series2);
chart.Series.Add(series3);

{% endhighlight %}

{% endtabs %}

![Multiple doughnut series support in WinUI Circular Chart](Series_images/winui-multiple-doughnut-serie.png)

## Semi Doughnut

By using the [StartAngle]() and [EndAngle]() properties, you can draw doughnut series in different shapes such as semi-doughnut or quarter doughnut series.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>

    <chart:SfCircularChart.Series>
        <chart:DoughnutSeries StartAngle="180" EndAngle="360"
                          ItemsSource="{Binding Data}"
                          XBindingPath="Product" 
                          YBindingPath="SalesRate" />
    </chart:SfCircularChart.Series>

</chart:SfCircularChart>
    
{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();

DoughnutSeries series = new DoughnutSeries();
series.XBindingPath = "Product";
series.YBindingPath = "SalesRate";
series.StartAngle = 180;
series.EndAngle = 360;

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Semi doughnut support in WinUI Circular Chart](Series_images/semi_doughnut_chart.png)