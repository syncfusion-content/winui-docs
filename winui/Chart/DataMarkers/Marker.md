---
layout: post
title: Data Marker in WinUI Chart control | Syncfusion
description: Learn here all about Data Marker feature of Syncfusion WinUI Chart control and more details.Data Marker is used to mark the data points.
platform: WinUI
control: Chart
documentation: ug
---

# Data Marker in WinUI Chart

Data Marker is used to mark the data points with built-in available shapes.

## Define Data Marker

To enable the marker in data markers you have to set the [`ShowMarker`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_ShowMarker) property as True. By default, there is no marker displayed, you have to add the desired marker using MarkerType property.

The following code example demonstrates the column series with [`Diamond`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSymbol.html) marker:


{% tabs %}

{% highlight xaml %}

<syncfusion:ColumnSeries.DataMarker>
    <syncfusion:ChartDataMarker ShowMarker="True" MarkerInterior="#1E88E5" MarkerType="Diamond">
    </syncfusion:ChartDataMarker>
</syncfusion:ColumnSeries.DataMarker> 

{% endhighlight %}

{% highlight c# %}

ChartDataMarker datamarker = new ChartDataMarker()
{
    ShowMarker = true,
    MarkerType = ChartSymbol.Diamond,
    MarkerInterior = "#1E88E5"          
};

{% endhighlight %}

{% endtabs %}

![Marker support in WinUI Chart](DataMarkers_images/marker.png)


### Customizing Marker

Chart provides support more customization for markers in data markers. 

* [`MarkerHeight`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_MarkerHeight)- used to change the height of the marker.
* [`MarkerWidth`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_MarkerWidth)- used to change the width of the marker.
* [`MarkerInterior`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_MarkerInterior)- used to change the color of marker.
* [`MarkerStroke`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_MarkerStroke)- used to change the stroke color of marker.
* [`MarkerTemplate`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_MarkerTemplate)- used to customize the appearance of marker.

{% tabs %}

{% highlight xaml %}

<syncfusion:ChartDataMarker ShowMarker="True" MarkerStroke="#0D47A1" MarkerHeight="10" MarkerWidth="10" MarkerInterior="#1E88E5" MarkerType="Ellipse">
</syncfusion:ChartDataMarker>

{% endhighlight %}

{% highlight c# %}

ChartDataMarker datamarker = new ChartDataMarker()
{
    ShowMarker = true,
    MarkerStroke = "#0D47A1",
    MarkerInterior = "#1E88E5",
    MarkerHeight = 10,
    MarkerWidth = 10,
    MarkerType = ChartSymbol.Ellipse
};

{% endhighlight %}

{% endtabs %}

![Marker customization support in WinUI Chart](DataMarkers_images/custom_marker.png)

**MarkerTemplate**

The following code example demonstrates how to use MarkerTemplate.

{% tabs %}

{% highlight xaml %}

<Page.Resources>
    <DataTemplate x:Key="markerTemplate">
        <Grid>
            <Grid Name="backgroundGrid" Width="24" Height="24" Visibility="Visible">
                <Ellipse Fill="#1E88E5" Name="Fill" Visibility="Visible" />
            </Grid>
            <Path Stretch="Uniform" Fill="#FF0F0E0E" Width="24" Height="24" Margin="0,0,0,0" RenderTransformOrigin="0.5,0.5"
                        Data="M23.9296875,10.6165618896484L20.759765625,11.2200794219971 18.09375,
                        13.0306243896484 16.283203125,15.6966400146484 15.6796875,18.8665618896484 16.283203125,
                        22.0423431396484 18.09375,24.7259368896484 20.759765625,26.5540618896484 23.9296875,27.1634368896484 271025371551514,
                        26.5540618896484 29.77734375,24.7259368896484 31.5966796875,22.0423431396484 32.203125,18.8665618896484 315966796875,
                        15.6966400146484 29.77734375,13.0306243896484 27.1025371551514,11.2200794219971 23.9296875,10.6165618896484zM25.265625,
                        7.35874938964844L26.6953125,9.86656188964844 29.3671875,8.64781188964844 29.765625,11.4837493896484 327421875,
                        11.2728118896484 32.015625,14.1790618896484 34.921875,14.9759368896484 33.1875,17.4134368896484 35.578125,
                        19.1478118896484 33.140625,20.7884368896484 34.640625,23.3665618896484 31.8046875,23.9759368896484 32.3203125,
                        26.9759368896484 29.4375,26.5540618896484 28.921875,29.4837493896484 26.25,27.9603118896484 24.75,
                        30.4681243896484 22.8046875,28.2181243896484 20.5078125,30.0228118896484 19.5703125,27.1634368896484 16640625,
                        28.0306243896484 16.875,25.1009368896484 13.875,24.7728118896484 15.140625,22.1478118896484 12.421875,
                        20.7415618896484 14.5546875,18.6790618896484 12.4921875,16.5228118896484 15.2578125,15.3040618896484 14203125,
                        12.5384368896484 17.1328125,12.3978118896484 17.1328125,9.42124938964844 19.921875,10.4056243896484 21.046875,
                        7.61656188964844 23.296875,9.49156188964844 25.265625,7.35874938964844z">
                <Path.RenderTransform>
                    <TransformGroup>
                        <TransformGroup.Children>
                            <RotateTransform Angle="0" />
                            <ScaleTransform ScaleX="1" ScaleY="1" />
                        </TransformGroup.Children>
                    </TransformGroup>
                </Path.RenderTransform>
            </Path>
        </Grid>
    </DataTemplate>
</Page.Resources>
<Grid>
    <chart:SfChart  Width="400" Height="300">
    ...
            
        <syncfusion:ColumnSeries ItemsSource="{Binding Demands}" XBindingPath="Category" YBindingPath="Value">
            <syncfusion:ColumnSeries.DataMarker>
                    <syncfusion:ChartDataMarker ShowMarker="True" DataMarkerPosition="Top" MarkerTemplate="{StaticResource markerTemplate}">
                    </syncfusion:ChartDataMarker>
            </syncfusion:ColumnSeries.DataMarker>
         </syncfusion:ColumnSeries>

    ...
    </chart:SfChart>
</Grid>
        
{% endhighlight %}

{% highlight c# %}

ChartDataMarker datamarker = new ChartDataMarker()
{
    ShowMarker  = true,
    DataMarkerPosition = DataMarkerPosition.Top,
    MarkerTemplate = chart.Resources["markerTemplate"] as DataTemplate,
};

{% endhighlight %}

{% endtabs %}

![Template support for marker in WinUI Chart](DataMarkers_images/markertemplate.png)
