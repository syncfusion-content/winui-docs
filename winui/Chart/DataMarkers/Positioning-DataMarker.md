---
layout: post
title: Positioning Data Markers in WinUI Chart control | Syncfusion
description: Learn about Positioning Data Markers support in Syncfusion WinUI Chart control and more details.
platform: WinUI
control: Chart
documentation: ug
---

# Positioning Data Markers in WinUI Chart

The positioning of data markers inside the series is defined using [`DataMarkerPosition`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_DataMarkerPosition) property. 

* [`Top`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DataMarkerPosition.html) - Positions the data marker at the top edge point of a chart segment.
* [`Bottom`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DataMarkerPosition.html) - Positions the data marker at the bottom edge point of a chart segment.
* [`TopAndBottom`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DataMarkerPosition.html) - Positions the data marker at the center point of a chart segment.

N> This behavior varies based on the chart series type.

The following code example explains the positioning of data markers in the middle of the segment.

{% tabs %}

{% highlight xaml %}

<syncfusion:ChartDataMarker ShowMarker="True" DataMarkerPosition="TopAndBottom" MarkerInterior="#1E88E5" MarkerType="Ellipse">
</syncfusion:ChartDataMarker>

{% endhighlight %}

{% highlight c# %}

ColumnSeries series = new ColumnSeries();
ChartDataMarker datamarker = new ChartDataMarker()
{
    ShowMarker = true,
    MarkerType = ChartSymbol.Ellipse,
    MarkerInterior = "#1E88E5",
    DataMarkerPosition = DataMarkerPosition.TopAndBottom
};
series.DataMarker = datamarker;

{% endhighlight %}

{% endtabs %}

![TopAndBottom DataMarker](DataMarkers_images/datamarkerposition_topbottom.png)

Also, you can define the label alignment using  [`HorizontalAlignment`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_HorizontalAlignment) and [`VerticalAlignment`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_VerticalAlignment) properties.


## Label Position

Other than the above positioning options, Chart providing additional customization option to position the data markers smartly based on series types using [`LabelPosition`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_LabelPosition) property.

The following are the values for this property: 

* [`Default`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DataMarkerLabelPosition.html#Syncfusion_UI_Xaml_Charts_DataMarkerLabelPosition_Default)
* [`Auto`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DataMarkerLabelPosition.html#Syncfusion_UI_Xaml_Charts_DataMarkerLabelPosition_Auto)
* [`Inner`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DataMarkerLabelPosition.html#Syncfusion_UI_Xaml_Charts_DataMarkerLabelPosition_Inner)
* [`Outer`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DataMarkerLabelPosition.html#Syncfusion_UI_Xaml_Charts_DataMarkerLabelPosition_Outer)
* [`Center`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DataMarkerLabelPosition.html#Syncfusion_UI_Xaml_Charts_DataMarkerLabelPosition_Center)

The following code sample illustrates the center position of data marker labels,

{% tabs %}

{% highlight xaml %}

<chart:ChartDataMarker ShowLabel="True" LabelPosition="Center"/>

{% endhighlight %}

{% highlight c# %}

ChartDataMarker datamarker = new ChartDataMarker()
{
    ShowLabel = true,
    LabelPosition = DataMarkerLabelPosition.Center
};      

{% endhighlight %}

{% endtabs %}

| Column | Spline |
|--|--|
|![center Column](DataMarkers_images/labelposition_center_column.png)|![center Series](DataMarkers_images/labelposition_center_spline.png)|

The following code sample illustrates the inner position of data marker labels,

{% tabs %}

{% highlight xaml %}

<chart:ChartDataMarker ShowLabel="True" LabelPosition="Inner"/>

{% endhighlight %}

{% highlight c# %}

ChartDataMarker datamarker = new ChartDataMarker()
{
    ShowLabel = true,
    LabelPosition = DataMarkerLabelPosition.Inner
};      

{% endhighlight %}

{% endtabs %}

| Column | Spline |
|--|--|
|![Inner Column](DataMarkers_images/labelposition_inner_column.png)|![Inner Series](DataMarkers_images/labelposition_inner_spline.png)|


The following code sample illustrates the outer position of data marker labels,

{% tabs %}

{% highlight xaml %}

<chart:ChartDataMarker ShowLabel="True" LabelPosition="Outer"/>

{% endhighlight %}

{% highlight c# %}

ChartDataMarker datamarker = new ChartDataMarker()
{
    ShowLabel = true,
    LabelPosition = DataMarkerLabelPosition.Outer
};      

{% endhighlight %}

{% endtabs %}

| Column | Spline |
|--|--|
|![Outer Column](DataMarkers_images/labelposition_outer_column.png)|![Outer Series](DataMarkers_images/labelposition_outer_spline.png)|
