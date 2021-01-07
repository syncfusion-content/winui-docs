---
layout: post
title: Pie and Doughnut Charts | SfChart | WinUI | Syncfusion
description: This section explains Pie and Doughnut Charts and its properties for customization in WinUI Charts (SfChart)
platform: WinUI
control: SfChart
documentation: ug
---

# Pie and Doughnut Charts in WinUI Chart (SfChart)

## Pie

[`PieSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PieSeries.html#) is divided into sectors, illustrating numerical proportion. The following code example illustrates the PieSeries.

{% tabs %}

{% highlight xaml %}

<chart:PieSeries XBindingPath="Category" ItemsSource="{Binding Data}" YBindingPath="Value"/>

{% endhighlight %}

{% highlight c# %}

PieSeries series = new PieSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Category",

    YBindingPath = "Value"

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Pie chart type in WinUI](Series_images/pie_chart.png)

The rendering size of the PieSeries can be controlled using [`CircularCoefficient`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PieSeries.html#Syncfusion_UI_Xaml_Charts_PieSeries_CircularCoefficient) property as in below code example.

{% tabs %}

{% highlight xaml %}

<chart:PieSeries CircularCoefficient="0.9" XBindingPath="Category" ItemsSource="{Binding Data}" YBindingPath="Value"/>

{% endhighlight %}

{% highlight c# %}

PieSeries series = new PieSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Category",

    YBindingPath = "Value",

    CircularCoefficient = 0.9

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![CircularCoefficient support in WinUI Chart](Series_images/pie_circularcoefficient.png)

### Group small data points into “others”
The small segments in the pie chart can be grouped into the “others” category using the [`GroupTo`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CircularSeriesBase.html#Syncfusion_UI_Xaml_Charts_CircularSeriesBase_GroupTo) and [`GroupMode`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CircularSeriesBase.html#Syncfusion_UI_Xaml_Charts_CircularSeriesBase_GroupMode) properties of PieSeries.

 The [`GroupMode`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CircularSeriesBase.html#Syncfusion_UI_Xaml_Charts_CircularSeriesBase_GroupMode) property is used to specify the grouping type based on slice [`Angle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PieGroupMode.html), actual data point [`Value`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PieGroupMode.html), or [`Percentage`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PieGroupMode.html), and the [`GroupTo`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CircularSeriesBase.html#Syncfusion_UI_Xaml_Charts_CircularSeriesBase_GroupTo) property is used to set the limit to group data points into a single slice. The grouped segment is labeled as “Others” in legend and toggled as other segment. The default value of the [`GroupTo`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CircularSeriesBase.html#Syncfusion_UI_Xaml_Charts_CircularSeriesBase_GroupTo) property is `double.NAN`, and the default value of the [`GroupMode`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CircularSeriesBase.html#Syncfusion_UI_Xaml_Charts_CircularSeriesBase_GroupMode) property is Value.

**Pie series without grouping**

![Pie series without grouping feature](Series_images/nongrouping_pie.png)

**Pie series with grouping (Mode - Value)**

{% tabs %}

{% highlight xaml %}

<chart:PieSeries ItemsSource="{Binding Data}" XBindingPath="Country" YBindingPath="Count" GroupMode="Value" GroupTo="1000">
    <chart:PieSeries.DataMarker>
        <chart:ChartDataMarker ShowConnectorLine="True" 
                                  ConnectorHeight="80" 
                                  ShowLabel="True" 
                                  LabelTemplate="{StaticResource DataLabelTemplate}"  
                                  SegmentLabelContent="LabelContentPath">
        </chart:ChartDataMarker>
    </chart:PieSeries.DataMarker>
</chart:PieSeries>

{% endhighlight %}

{% highlight c# %}

pieSeries.GroupMode = PieGroupMode.Value;
pieSeries.GroupTo = 1000;
ChartDataMarker datamarker = new ChartDataMarker()
{
    ShowConnectorLine = true,
    ShowLabel = true,
    ConnectorHeight = 80,
    LabelTemplate = this.RootGrid.Resources["DataLabelTemplate"] as DataTemplate,
    SegmentLabelContent = LabelContent.LabelContentPath,

pieSeries.DataMarker = datamarker;

{% endhighlight %}

{% endtabs %}

![Pie series with grouping feature in value mode](Series_images/pie_groupmode_value.png)

**Pie series with grouping (Mode - Angle)**

{% tabs %}

{% highlight xaml %}

<chart:PieSeries ItemsSource="{Binding Data}" XBindingPath="Country" YBindingPath="Count" GroupMode="Angle" GroupTo="30">
    <chart:PieSeries.DataMarker>
        <chart:ChartDataMarker ShowConnectorLine="True" 
                                  ConnectorHeight="80" 
                                  ShowLabel="True" 
                                  LabelTemplate="{StaticResource DataLabelTemplate}"  
                                  SegmentLabelContent="LabelContentPath">
        </chart:ChartDataMarker>
    </chart:PieSeries.DataMarker>
</chart:PieSeries>

{% endhighlight %}

{% highlight c# %}

pieSeries.GroupMode = PieGroupMode.Angle;
pieSeries.GroupTo = 30;

ChartDataMarker datamarker = new ChartDataMarker()
{
        ShowConnectorLine = true,
        ShowLabel = true,
        ConnectorHeight = 80,
        LabelTemplate = this.RootGrid.Resources["DataLabelTemplate"] as DataTemplate,
        SegmentLabelContent = LabelContent.LabelContentPath,
};

pieSeries.DataMarker = datamarker;

{% endhighlight %}

{% endtabs %}

![Pie series with grouping feature in angle mode](Series_images/pie_groupmode_angle.png)

**Pie series with grouping (Mode - Percentage)**

{% tabs %}

{% highlight xaml %}

<chart:PieSeries ItemsSource="{Binding Data}" XBindingPath="Country" YBindingPath="Count" GroupMode="Percentage" GroupTo="10">
    <chart:PieSeries.DataMarker>
        <chart:ChartDataMarker ShowConnectorLine="True" 
                                  ConnectorHeight="80" 
                                  ShowLabel="True" 
                                  LabelTemplate="{StaticResource DataLabelTemplate}"  
                                  SegmentLabelContent="LabelContentPath">
        </chart:ChartDataMarker>
    </chart:PieSeries.DataMarker>
</chart:PieSeries>


{% endhighlight %}

{% highlight c# %}

pieSeries.GroupMode = PieGroupMode.Percentage;
pieSeries.GroupTo = 10;

ChartDataMarker datamarker = new ChartDataMarker()
{
        ShowConnectorLine = true,
        ShowLabel = true,
        ConnectorHeight = 80,
        LabelTemplate = this.RootGrid.Resources["DataLabelTemplate"] as DataTemplate,
        SegmentLabelContent = LabelContent.LabelContentPath,
};

pieSeries.DataMarker = datamarker;

{% endhighlight %}

{% endtabs %}

![Pie series with grouping feature in percentage mode](Series_images/pie_groupmode_value.png)

## Doughnut

[`DoughnutSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DoughnutSeries.html#) is similar to PieSeries. It is used to show the relationship between parts of data and whole data. 

The DoughnutSeries can be added to chart as in below code example:

{% tabs %}

{% highlight xaml %}

<chart:DoughnutSeries XBindingPath="Category" ItemsSource="{Binding Data}" YBindingPath="Value"/>

{% endhighlight %}

{% highlight c# %}

DoughnutSeries series = new DoughnutSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Category",

    YBindingPath = "Value"
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Doughnut chart type in WinUI](Series_images/doughnut_chart.png)

The Doughnut also having coefficient property, [`DoughnutCoefficient`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DoughnutSeries.html#Syncfusion_UI_Xaml_Charts_DoughnutSeries_DoughnutCoefficient) which defines the inner circle. Also it has [`DoughnutSize`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DoughnutSeries.html#Syncfusion_UI_Xaml_Charts_DoughnutSeries_DoughnutSize), used to define the size for this series like [`CircularCoefficient`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PieSeries.html#Syncfusion_UI_Xaml_Charts_PieSeries_CircularCoefficient) in PieSeries.

{% tabs %}

{% highlight xaml %}

<chart:DoughnutSeries DoughnutCoefficient="0.7" XBindingPath="Category" ItemsSource="{Binding Data}" YBindingPath="Value"/>

{% endhighlight %}

{% highlight c# %}

DoughnutSeries series = new DoughnutSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Category",

    YBindingPath = "Value",

    DoughnutCoefficient = 0.7
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![DoughnutCoefficient support in WinUI Chart](Series_images/doughnut_coefficient.png)

**Size**

The size of doughnut series can be customized by using its [`DoughnutSize`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DoughnutSeries.html#Syncfusion_UI_Xaml_Charts_DoughnutSeries_DoughnutSizeProperty) property. The following code illustrates how to use the property in series.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart>

<syncfusion:DoughnutSeries DoughnutSize="0.8"/>
       
<syncfusion:DoughnutSeries DoughnutSize="0.8"/>

</syncfusion:SfChart>


{% endhighlight %}

{% highlight c# %}

DoughnutSeries doughnut = new DoughnutSeries();

doughnut.DoughnutSize = 0.8;

chart.Series.Add(doughnut);

DoughnutSeries doughnut1 = new DoughnutSeries();

doughnut1.DoughnutSize = 0.8;

chart.Series.Add(doughnut1);

{% endhighlight %}

{% endtabs %}

![DoughnutSize support in WinUI Chart](Series_images/doughnut_size.png)

**Hole Size**

[`DoughnutHoleSize`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DoughnutSeries.html#Syncfusion_UI_Xaml_Charts_DoughnutSeries_DoughnutHoleSizeProperty) is an attachable property. It gets or sets the double value, which is used to customize the doughnut hole size. Its value ranges from 0 to 1, and it can be set as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<Chart:SfChart Chart:DoughnutSeries.DoughnutHoleSize="0.2">
    
</chart:SfChart>

{% endhighlight %}

{% highlight c# %}

SfChart chart = new SfChart();

DoughnutSeries.SetDoughnutHoleSize(chart, 0.2);

{% endhighlight %}

{% endtabs %}

![DoughnutHoleSize support in WinUI Chart](Series_images/doughnut_holesize.png)


## Semi Pie and Doughnut

By using custom [`StartAngle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CircularSeriesBase.html#Syncfusion_UI_Xaml_Charts_CircularSeriesBase_StartAngle) and [`EndAngle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CircularSeriesBase.html#Syncfusion_UI_Xaml_Charts_CircularSeriesBase_EndAngle) properties, you can draw pie series in different shapes such as semicircular or quarter circular series.

{% tabs %}

{% highlight xaml %}

<syncfusion:PieSeries StartAngle="180" EndAngle="360" XBindingPath="Utilization" YBindingPath="ResponseTime" ItemsSource="{Binding Data}"/>

{% endhighlight %}

{% highlight c# %}

PieSeries series = new PieSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Utilization",

    YBindingPath = "ResponseTime",

    StartAngle = 180,

    EndAngle = 360

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Semi pie support in WinUI Chart](Series_images/semi_pie_chart.png)

{% tabs %}

{% highlight xaml %}

<syncfusion:DoughnutSeries StartAngle="180" EndAngle="360" XBindingPath="Utilization" YBindingPath="ResponseTime" ItemsSource="{Binding Data}"/>

{% endhighlight %}

{% highlight c# %}

DoughnutSeries series = new DoughnutSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Utilization",

    YBindingPath = "ResponseTime",

    StartAngle = 180,

    EndAngle = 360

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Semi doughnut support in WinUI Chart](Series_images/semi_doughnut_chart.png)

## Stacked doughnut

Doughnut segments can be separated as individual circles using the [`IsStackedDoughnut`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DoughnutSeries.html#Syncfusion_UI_Xaml_Charts_DoughnutSeries_IsStackedDoughnut) property. The following properties are used to customize the stacked doughnut chart:

* [`CapStyle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DoughnutSeries.html#Syncfusion_UI_Xaml_Charts_DoughnutSeries_CapStyle) - Specifies the shapes of the start and end points of a circular segment. The supported values are [`BothFlat`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DoughnutCapStyle.html), [`BothCurve`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DoughnutCapStyle.html), [`StartCurve`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DoughnutCapStyle.html), and [`EndCurve`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DoughnutCapStyle.html). The default value of the this property is BothFlat.

* [`SegmentSpacing`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DoughnutSeries.html#Syncfusion_UI_Xaml_Charts_DoughnutSeries_SegmentSpacing) - Changes the spacing between two individual segments. The default value of spacing is 0, and the value ranges from 0 to 1. Here, 1 represents 100%, and 0 represents 0% of the available space.

* [`MaximumValue`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DoughnutSeries.html#Syncfusion_UI_Xaml_Charts_DoughnutSeries_SegmentSpacing) - Represents the entire span of an individual circle. The default value of the this property is double.NaN.

* [`TrackColor`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DoughnutSeries.html#Syncfusion_UI_Xaml_Charts_DoughnutSeries_TrackColor) - Changes the color of the track area.

* [`TrackBorderColor`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DoughnutSeries.html#Syncfusion_UI_Xaml_Charts_DoughnutSeries_TrackBorderColor) - Changes the color of the track border.

* [`TrackBorderWidth`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DoughnutSeries.html#Syncfusion_UI_Xaml_Charts_DoughnutSeries_TrackBorderWidth) - Changes the width of the track border.

{% tabs %}

{% highlight xaml %}

<chart:SfChart>
    …
    <chart:DoughnutSeries IsStackedDoughnut="True" CapStyle="BothCurve" SegmentSpacing="0.2" MaximumValue="100" XBindingPath="Category" YBindingPath="Expenditure" ItemsSource="{Binding ExpenditureData}">
    </chart:DoughnutSeries>

</chart:SfChart>

{% endhighlight %}

{% highlight c# %}

SfChart chart = new SfChart();

DoughnutSeries doughnutSeries = new DoughnutSeries()
{
    IsStackedDoughnut = true,
    CapStyle = DoughnutCapStyle.BothCurve,
    SegmentSpacing = 0.2,
    MaximumValue = 100,
    XBindingPath = "Category",
    YBindingPath = "Expenditure",
    ItemsSource = new ViewModel().ExpenditureData
};

chart.Series.Add(doughnutSeries);

{% endhighlight %}

{% endtabs %}

![Stacked doughnut chart in WinUI](Series_images/stackeddoughnut_chart.png)

## Explode Segments

The following properties are used to explode the individual segments in Pie and Doughnut.

* [`ExplodeAll`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.AccumulationSeriesBase.html#Syncfusion_UI_Xaml_Charts_AccumulationSeriesBase_ExplodeAll)  - Used to explode all the segments of these series.

* [`ExplodeIndex`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.AccumulationSeriesBase.html#Syncfusion_UI_Xaml_Charts_AccumulationSeriesBase_ExplodeIndex) - Used to explode any specific segment.

* [`ExplodeRadius`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CircularSeriesBase.html#Syncfusion_UI_Xaml_Charts_CircularSeriesBase_ExplodeRadius) - Used to define the explode distance.

* [`ExplodeOnMouseClick`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.AccumulationSeriesBase.html#Syncfusion_UI_Xaml_Charts_AccumulationSeriesBase_ExplodeOnMouseClick) - Used to explode the segment when segment is clicked.

**Explode** **Index**

{% tabs %}

{% highlight xaml %}

<syncfusion:PieSeries x:Name="PieSeries" ItemsSource="{Binding Data}"    

ExplodeIndex="2" ExplodeRadius="10" XBindingPath="Utilization" 

YBindingPath="ResponseTime" />

{% endhighlight %}

{% highlight c# %}

PieSeries series = new PieSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Utilization",

    YBindingPath = "ResponseTime",

    ExplodeIndex = 2,

    ExplodeRadius = 10

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Exploding a segment of accumlation series in WinUI Chart](Series_images/pie_exploderadius.png)

N> We have defined ExplodeRadius as 30, by default its value is zero. So you need to define explode, when you set ExplodeIndex or ExplodeAll.

**Explode** **All**

{% tabs %}

{% highlight xaml %}

<chart:PieSeries  ExplodeAll="True" ExplodeRadius="15"

XBindingPath="Category" ItemsSource="{Binding Data}" 

YBindingPath="Value">

{% endhighlight %}

{% highlight c# %}

PieSeries series = new PieSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Category",

    YBindingPath = "Value",

    ExplodeAll = true,

    ExplodeRadius = 15

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Exploding all the segments of accumulation series in WinUI Chart](Series_images/pie_explodeall.png)