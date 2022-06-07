---
layout: post
title: Radar and Polar in WinUI Chart control | Syncfusion
description: Learn here all about Radar and Polar support in Syncfusion WinUI Chart(SfChart) control with draw type polar and more.
platform: WinUI
control: SfChart
documentation: ug
---

# Radar and Polar in WinUI Chart

## Radar

[`RadarSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.RadarSeries.html#) represents a collection of data displayed by quantitative variables represented by axes starting from the same point. The relative position and angle of the axes are not uniform. 

The following code example illustrates the use of radar series:

{% tabs %}

{% highlight xaml %}

<chart:RadarSeries ItemsSource="{Binding PlantDetails}" 

XBindingPath="Direction"

YBindingPath="Tree">

</chart:RadarSeries>        

{% endhighlight %}

{% highlight c# %}

RadarSeries series = new RadarSeries()
{

    ItemsSource = new ViewModel().PlantDetails,

    XBindingPath = "Direction",

    YBindingPath = "Tree",

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Radar chart type in WinUI](Series_images/radar_chart.png)


## Polar

[`PolarSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PolarSeries.html#) displays data points that are grouped by category on a 360-degree circle. The following code example shows how to use polar series.

{% tabs %}

{% highlight xaml %}

<chart:PolarSeries 

ItemsSource="{Binding PlantDetails}"  

XBindingPath="Direction"

YBindingPath="Tree" />                 

{% endhighlight %}

{% highlight c# %}

PolarSeries series = new PolarSeries()
{

    ItemsSource = new ViewModel().PlantDetails,

    XBindingPath = "Direction",

    YBindingPath = "Tree",

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Polar chart type in WinUI](Series_images/polar_chart.png)


The Radar and Polar charts have the following properties in common:

* [`IsClosed`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PolarRadarSeriesBase.html#Syncfusion_UI_Xaml_Charts_PolarRadarSeriesBase_IsClosed)
* [`DrawType`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PolarRadarSeriesBase.html#Syncfusion_UI_Xaml_Charts_PolarRadarSeriesBase_DrawType)
* [`PolarAngle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPolarAngle.html)

### IsClosed

This property is used to draw the closed path as follows.

{% tabs %}

{% highlight xaml %}

<chart:PolarSeries x:Name="series1" 

ItemsSource="{Binding PlantDetails}"  

Label="Amount Spent" DrawType="Line" IsClosed="False" 

XBindingPath="Direction" YBindingPath="Tree" 

StrokeThickness="2" />

{% endhighlight %}

{% highlight c# %}

PolarSeries series = new PolarSeries()
{

    ItemsSource = new ViewModel().PlantDetails,

    XBindingPath = "Direction",

    YBindingPath = "Tree",

    IsClosed = false,

    DrawType = ChartSeriesDrawType.Line,

    Label = "Amount Spent",

    StrokeThickness = 2,

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Closed polar series in WinUI Chart](Series_images/polar_isclosed_false.png)

### DrawType

This property defines type of curve, whether it is [`Line`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeriesDrawType.html) or [`Area`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeriesDrawType.html).

**DrawType** **as** **Area**

{% tabs %}

{% highlight xaml %}

<chart:PolarSeries x:Name="series1" 

ItemsSource="{Binding PlantDetails}"  

DrawType="Area" IsClosed="True" 

XBindingPath="Direction" YBindingPath="Tree" />

{% endhighlight %}

{% highlight c# %}

PolarSeries series = new PolarSeries()
{

    ItemsSource = new ViewModel().PlantDetails,

    XBindingPath = "Direction",

    YBindingPath = "Tree",

    IsClosed = True,

    DrawType = ChartSeriesDrawType.Area,

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Draw type support for polar series in WinUI Chart](Series_images/polar_drawtype_area.png)

**DrawType** **as** **Line**

{% tabs %}

{% highlight xaml %}

<chart:PolarSeries

ItemsSource="{Binding PlantDetails}"  

DrawType="Line" IsClosed="True" 

XBindingPath="Direction" YBindingPath="Tree" 

StrokeThickness="2" />

{% endhighlight %}

{% highlight c# %}

PolarSeries series = new PolarSeries()
{

    ItemsSource = new ViewModel().PlantDetails,

    XBindingPath = "Direction",

    YBindingPath = "Tree",

    IsClosed = True,

    DrawType = ChartSeriesDrawType.Line,

    StrokeThickness = 2,

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Draw type support for polar series in WinUI Chart](Series_images/polar_drawtype_line.png)

### Polar angle

[`Chart axis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html) provides support to render polar and radar series on 0,90,180 and 270 degrees. It can be achieved by its `PolarAngle` property. The 'PolarAngle' is a type of 'ChartPolarAngle,' and its default value is 'Rotate270.' Other supported values of 'PolarAngle' include 'Rotate0,' 'Rotate90,' and 'Rotate180.' Both the primary and secondary axes can be rotated individually based on their `PolarAngle` value.

**Rotate0**

The following sample explains how the axes of the series have been rotated when the `PolarAngle` value is [`Rotate0`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPolarAngle.html).

{% tabs %}

{% highlight xaml %}

<chart:SfChart.PrimaryAxis>

<chart:CategoryAxis PolarAngle="Rotate0"/>

</chart:SfChart.PrimaryAxis>

<chart:SfChart.SecondaryAxis>

<chart:NumericalAxis PolarAngle="Rotate0"/>

</chart:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

 chart.PrimaryAxis = new CategoryAxis()
 {

    PolarAngle = ChartPolarAngle.Rotate0

 };

chart.SecondaryAxis = new NumericalAxis()
{

    PolarAngle = ChartPolarAngle.Rotate0

};

{% endhighlight %}

{% endtabs %}

![Rotation support for polar series in WinUI Chart](Series_images/polarangle_rotate0.png)


**Rotate90**

The following sample explains how the axes of the series have been rotated when the `PolarAngle` value is [`Rotate90`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPolarAngle.html).

{% tabs %}

{% highlight xaml %}

<chart:SfChart.PrimaryAxis>

<chart:CategoryAxis PolarAngle="Rotate90"/>

</chart:SfChart.PrimaryAxis>

<chart:SfChart.SecondaryAxis>

<chart:NumericalAxis PolarAngle="Rotate90"/>

</chart:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

 chart.PrimaryAxis = new CategoryAxis()
 {

    PolarAngle = ChartPolarAngle.Rotate90

 };

chart.SecondaryAxis = new NumericalAxis()
{

    PolarAngle = ChartPolarAngle.Rotate90
            
};

{% endhighlight %}

{% endtabs %}

![Rotation support for polar series in WinUI Chart](Series_images/polarangle_rotate90.png)


**Rotate180**

The following sample explains how the axes of the series have been rotated when the `PolarAngle` value is [`Rotate180`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPolarAngle.html).

{% tabs %}

{% highlight xaml %}

<chart:SfChart.PrimaryAxis>

<chart:CategoryAxis PolarAngle="Rotate180"/>

</chart:SfChart.PrimaryAxis>

<chart:SfChart.SecondaryAxis>

<chart:NumericalAxis PolarAngle="Rotate180"/>

</chart:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

 chart.PrimaryAxis = new CategoryAxis()
 {

    PolarAngle = ChartPolarAngle.Rotate180

 };

chart.SecondaryAxis = new NumericalAxis()
{

    PolarAngle = ChartPolarAngle.Rotate180
            
};

{% endhighlight %}

{% endtabs %}

![Rotation support for polar series in WinUI Chart](Series_images/polarangle_rotate180.png)


**Rotate270**

The following sample explains how the axes of the series have been rotated when the `PolarAngle` value is [`Rotate270`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPolarAngle.html).

{% tabs %}

{% highlight xaml %}

<chart:SfChart.PrimaryAxis>

<chart:CategoryAxis PolarAngle="Rotate270"/>

</chart:SfChart.PrimaryAxis>

<chart:SfChart.SecondaryAxis>

<chart:NumericalAxis PolarAngle="Rotate270"/>

</chart:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

 chart.PrimaryAxis = new CategoryAxis()
 {

    PolarAngle = ChartPolarAngle.Rotate270

 };

chart.SecondaryAxis = new NumericalAxis()
{

    PolarAngle = ChartPolarAngle.Rotate270
            
};

{% endhighlight %}

{% endtabs %}

![Rotation support for polar series in WinUI Chart](Series_images/polarangle_rotate270.png)
