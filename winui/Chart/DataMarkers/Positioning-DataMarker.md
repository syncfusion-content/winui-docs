---
layout: post
title: Positioning Data Markers in WinUI Chart control | Syncfusion
description: Learn here all about Positioning Data Markers feature in Syncfusion WinUI Chart(SfChart) control and more.
platform: WinUI
control: Chart
documentation: ug
---

# Alignment of Data Labels in WinUI Chart

The alignment of data labels inside the series is defined using [BarLabelAlignment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.CartesianDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_CartesianDataLabelSettings_BarLabelAlignment) property.

* [Top](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.BarLabelAlignment.html#Syncfusion_UI_Xaml_Charts_BarLabelAlignment_Top) - Positions the data label at the top edge point of a chart segment.
* [Middle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.BarLabelAlignment.html#Syncfusion_UI_Xaml_Charts_BarLabelAlignment_Middle) - Positions the data label at the center point of a chart segment.
* [Bottom](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.BarLabelAlignment.html#Syncfusion_UI_Xaml_Charts_BarLabelAlignment_Bottom) - Positions the data label at the bottom edge point of a chart segment.

N> This behavior varies based on the chart series type.

The following code example explains the positioning of data markers in the middle of the segment.

{% tabs %}

{% highlight xaml %}

<chart:SfChart>
. . .
<chart:ColumnSeries ShowDataLabels="True">
    <chart:ColumnSeries.DataLabelSettings>
        <chart:CartesianDataLabelSettings BarLabelAlignment="Middle"/>
    </chart:ColumnSeries.DataLabelSettings>
</chart:ColumnSeries>
</chart:SfChart>

{% endhighlight %}

{% highlight c# %}

SfChart chart = new SfChart();
ColumnSeries series = new ColumnSeries();
. . .
series.DataLabelSettings = new CartesianDataLabelSettings()
{
    BarLabelAlignment = BarLabelAlignment.Middle,
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

Also, you can define the label alignment using  [HorizontalAlignment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_HorizontalAlignment) and [VerticalAlignment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_VerticalAlignment) properties.

## Position

Other than the above alignment options, Chart providing additional customization option to position the data labels. 

The [Position](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.CartesianDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_CartesianDataLabelSettings_Position) property is used to position the data labels at `Center`, `Inner` and `Outer` position of the actual data point position. By default, labels are positioned based on the series types for better readability.

The following are the values for this property: 

* [`Default`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataLabelPosition.html#Syncfusion_UI_Xaml_Charts_DataLabelPosition_Default)
* [`Auto`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataLabelPosition.html#Syncfusion_UI_Xaml_Charts_DataLabelPosition_Auto)
* [`Inner`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataLabelPosition.html#Syncfusion_UI_Xaml_Charts_DataLabelPosition_Inner)
* [`Outer`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataLabelPosition.html#Syncfusion_UI_Xaml_Charts_DataLabelPosition_Outer)
* [`Center`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataLabelPosition.html#Syncfusion_UI_Xaml_Charts_DataLabelPosition_Center)

The following code sample illustrates the center position of data marker labels,

{% tabs %}

{% highlight xaml %}

 <chart:CartesianDataLabelSettings Position="Center" />

{% endhighlight %}

{% highlight c# %}

CartesianDataLabelSettings dataLabel = new CartesianDataLabelSettings()
{
    Position = DataLabelPosition.Center
}; 

{% endhighlight %}

{% endtabs %}

| Column | Spline |
|--|--|
|![center Column](DataMarkers_images/labelposition_center_column.png)|![center Series](DataMarkers_images/labelposition_center_spline.png)|

The following code sample illustrates the inner position of data marker labels,

{% tabs %}

{% highlight xaml %}

<chart:CartesianDataLabelSettings Position="Inner" />

{% endhighlight %}

{% highlight c# %}

CartesianDataLabelSettings dataLabel = new CartesianDataLabelSettings()
{
    Position = DataLabelPosition.Inner
};  

{% endhighlight %}

{% endtabs %}

| Column | Spline |
|--|--|
|![Inner Column](DataMarkers_images/labelposition_inner_column.png)|![Inner Series](DataMarkers_images/labelposition_inner_spline.png)|


The following code sample illustrates the outer position of data marker labels,

{% tabs %}

{% highlight xaml %}

<chart:CartesianDataLabelSettings Position="Outer" />

{% endhighlight %}

{% highlight c# %}

CartesianDataLabelSettings dataLabel = new CartesianDataLabelSettings()
{
    Position = DataLabelPosition.Outer
};     

{% endhighlight %}

{% endtabs %}

| Column | Spline |
|--|--|
|![Outer Column](DataMarkers_images/labelposition_outer_column.png)|![Outer Series](DataMarkers_images/labelposition_outer_spline.png)|
