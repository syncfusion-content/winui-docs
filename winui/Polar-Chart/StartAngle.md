---
layout: post
title: Start Angle in WinUI Polar Chart control | Syncfusion
description: Learn all about PolarAngle support in Syncfusion WinUI Polar Chart(SfPolarChart) control, its elements and more details.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Start angle in WinUI Polar Charts (SfPolarChart)

Chart axis provides support to render polar and radar series on 0, 90, 180 and 270 degrees. It can be achieved by the axis [PolarAngle]() property. The [PolarAngle]() is type of [ChartPolarAngle]() and its default value is Rotate270. Rotate0, Rotate90 and Rotate180 are another supported values of [PolarAngle](). Both the primary and secondary axes can be rotated individually based on its [PolarAngle]() value.

### Rotate0

The below code snippet explains how the axes of series has been rotated when [PolarAngle]() value is Rotate0,

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.PrimaryAxis>
    <chart:CategoryAxis PolarAngle="Rotate0"/>
</chart:SfPolarChart.PrimaryAxis>
<chart:SfPolarChart.SecondaryAxis>
    <chart:NumericalAxis PolarAngle="Rotate0"/>
</chart:SfPolarChart.SecondaryAxis>

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

![Rotation support for polar series in WinUI polar chart](PolarAngle_Images/WinUI_PolarChart_Rotate0.png)

### Rotate90

The below code snippet explains how the axes of series has been rotated when [PolarAngle]() value is Rotate90,

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.PrimaryAxis>
    <chart:CategoryAxis PolarAngle="Rotate90"/>
</chart:SfPolarChart.PrimaryAxis>
<chart:SfPolarChart.SecondaryAxis>
    <chart:NumericalAxis PolarAngle="Rotate90"/>
</chart:SfPolarChart.SecondaryAxis>

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

![Rotation support for polar series in WinUI polar chart](PolarAngle_Images/WinUI_PolarChart_Rotate90.png)

### Rotate180

The below code snippet explains how the axes of series has been rotated when [PolarAngle]() value is Rotate180,

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.PrimaryAxis>
    <chart:CategoryAxis PolarAngle="Rotate180"/>
</chart:SfPolarChart.PrimaryAxis>
<chart:SfPolarChart.SecondaryAxis>
    <chart:NumericalAxis PolarAngle="Rotate180"/>
</chart:SfPolarChart.SecondaryAxis>

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

![Rotation support for polar series in WinUI polar chart](PolarAngle_Images/WinUI_PolarChart_Rotate180.png)

### Rotate270

The below code snippet explains how the axes of series has been rotated, when [PolarAngle]() value is Rotate270,

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.PrimaryAxis>
    <chart:CategoryAxis PolarAngle="Rotate270"/>
</chart:SfPolarChart.PrimaryAxis>
<chart:SfPolarChart.SecondaryAxis>
    <chart:NumericalAxis PolarAngle="Rotate270"/>
</chart:SfPolarChart.SecondaryAxis>

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

![Rotation support for polar series in WinUI polar chart](PolarAngle_Images/WinUI_PolarChart_Rotate270.png)