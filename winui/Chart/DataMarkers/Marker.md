---
layout: post
title: Data Marker in WinUI Chart control | Syncfusion
description: Learn here all about Data Marker feature of Syncfusion WinUI Chart control with customizing marker support.
platform: WinUI
control: Chart
documentation: ug
---

# Data Marker in WinUI Chart

To enable the marker symbol, you have to set the [ContentTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_ContentTemplate) property of [CartesianDataLabelSettings](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.CartesianDataLabelSettings.html).

The following code example demonstrates how to define marker symbol using [ContentTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_ContentTemplate).

{% tabs %}

{% highlight xaml %}

<Page.Resources>
    <DataTemplate x:Key="contentTemplate">
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
<chart:SfChart>
. . .
    <chart:ColumnSeries ShowDataLabels="True">
       <chart:ColumnSeries.DataLabelSettings>
           <chart:CartesianDataLabelSettings Position="Default" ContentTemplate="{StaticResource contentTemplate}"/>
        </chart:ColumnSeries.DataLabelSettings>
    </chart:ColumnSeries>
</chart:SfCartesianChart>

</Grid>
        
{% endhighlight %}

{% highlight c# %}

SfChart chart = new SfChart();
ColumnSeries series = new ColumnSeries();
. . .
series.DataLabelSettings = new CartesianDataLabelSettings()
{
    Position = DataLabelPosition.Default,
    ContentTemplate = chart.Resources["contentTemplate"] as DataTemplate
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Data marker symbol in WinUI Chart](DataMarkers_images/markertemplate.png)
