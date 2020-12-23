---
layout: post
title: DataMarker label in Chart | Syncfusion | WinUI
description: This section describes how to define the data marker label and its properties for customization in WinUI Charts.
platform: WinUI
control: Chart
documentation: ug
---

# Data Label in WinUI Charts (SfChart)

Data points can be easily annotated with labels to help improve the readability of data. 

## Define Data Label 

To enable the Label in data markers you have to set the [`ShowLabel`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_ShowLabel) property of [`ChartDataMarker`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarker.html). 

[`SegmentLabelContent`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_SegmentLabelContent) property allows you to define the value to be displayed as data marker label.

The following code example demonstrates about define the value to be displayed as data marker label.

{% tabs %}

{% highlight xaml %}

            <syncfusion:ChartDataMarker SegmentLabelContent="YValue" ShowLabel="True" LabelPosition="Outer"></syncfusion:ChartDataMarker>

{% endhighlight %}

{% highlight c# %}
        
            ChartDataMarker datamarker = new ChartDataMarker()
            {
               ShowLabel = true,
               SegmentLabelContent=LabelContent.YValue
            };

{% endhighlight %}

{% endtabs %}

| SegmentLabelContent values | Description | Output |
|---|--|---|
| DateTime | Displays LabelContent.DateTime value | ![ DateTime in DataMarker](DataMarkers_images/Datetime.png) |
|LabelContentPath | Displays the y value|![ LabelContentPath in DataMarker](DataMarkers_images/LabelContentPath.png)|
| Percentage | Displays the percentage value of series point among other points |![ Percentage in DataMarker](DataMarkers_images/Percentage.png) |
| XValue | Displays the X value of series point|![ XValue in DataMarker](DataMarkers_images/Xvalue.png) |
| YofTot | Displays the value of Y of total values point|![ YofTot in DataMarker](DataMarkers_images/YofTot.png) |
| YValue | Displays the Y value of series point| ![ YValue in DataMarker](DataMarkers_images/YValue.png) |

## Customizing Labels

The following properties are used to customize the data marker label.

* [`BorderBrush`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_BorderBrush)- used to change the border color.
* [`BorderThickness`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_BorderThickness)- used to change the thickness of the border.
* [`Margin`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_Margin)- used to change the margin size for label.
* [`FontStyle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_FontStyle)-  used to change font family of the label.
* [`FontSize`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_FontSize) -  used to change font size of the label.
* [`Foreground`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_Foreground)- used to change the color of the label.
* [`FontFamily`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_FontFamily)-  used to change the font family of the label.
* [`Background`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_Background)- used to change the label background color.

The following code example demonstrates the customization of label using the above properties:

{% tabs %}

{% highlight xaml %}

        <syncfusion:ColumnSeries.DataMarker>
            <syncfusion:ChartDataMarker LabelPosition="Outer" Foreground="Black" FontSize="11" FontFamily="Calibri" BorderBrush="Black" BorderThickness="1" Margin="1" FontStyle="Italic"  Background="DarkGray" ShowLabel="True">                        
            </syncfusion:ChartDataMarker>
        </syncfusion:ColumnSeries.DataMarker>

{% endhighlight %}

{% highlight c# %}

        ChartDataMarker datamarker = new ChartDataMarker()
        {

                ShowLabel = true,
                LabelPosition = DataMarkerLabelPosition.Outer,
                Foreground = new SolidColorBrush(Colors.Black),
                BorderBrush = new SolidColorBrush(Colors.Black),
                Background = new SolidColorBrush(Colors.DarkGray),
                BorderThickness = new Thickness(1),
                Margin = new Thickness(1),
                FontStyle = FontStyles.Italic,
                FontFamily = new FontFamily("Calibri"),
                FontSize = 11
        };


{% endhighlight %}

{% endtabs %}

![DataMarker label content customization support in WinUI Chart](DataMarkers_images/Custom_Label.png)

## Label Template

The default appearance of the label can be customized using [`LabelTemplate`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_LabelTemplate) property as in the below code example:

{% tabs %}

{% highlight xaml %}

    <Window.Resources>
        <DataTemplate x:Key="dataMarkerTemplate">
            <StackPanel Orientation="Vertical">               
                <Path Grid.Row="0"  Stretch="Uniform" Fill="#FF0F0E0E"                              
                           Width="15" Height="15" Margin="0,0,0,0"                              
                           RenderTransformOrigin="0.5,0.5">
                    <Path.Data>
                        <PathGeometry FillRule="Nonzero" Figures="M22.5,15.8899993896484L37.5,                                
                                              30.8899993896484 7.5,30.8899993896484 22.5,15.8899993896484z" />
                    </Path.Data>
                    <Path.RenderTransform>
                        <TransformGroup>
                            <TransformGroup.Children>
                                <RotateTransform Angle="0" />
                                <ScaleTransform ScaleX="1" ScaleY="1" />
                            </TransformGroup.Children>
                        </TransformGroup>
                    </Path.RenderTransform>
                </Path>
                <TextBlock Grid.Row="1" Text="{Binding}" FontSize="11" Foreground="Black"></TextBlock>
            </StackPanel>
        </DataTemplate>
    </Window.Resources>

     <Grid>
        <chart:SfChart Width="400" Height="300">
         ...
            <syncfusion:ColumnSeries Interior="#777777" ItemsSource="{Binding Demands}" XBindingPath="Category" YBindingPath="Value">
                <syncfusion:ColumnSeries.DataMarker>
                    <syncfusion:ChartDataMarker ShowLabel="True" LabelTemplate="{StaticResource dataMarkerTemplate}"
                        LabelPosition="Outer"></syncfusion:ChartDataMarker>
                </syncfusion:ColumnSeries.DataMarker>
            </syncfusion:ColumnSeries>
        ...
        </chart:SfChart>
    </Grid>

{% endhighlight %}

{% highlight c# %}

        ColumnSeries series = new ColumnSeries()
            {
                ItemsSource = new ViewModel().Demands,
                XBindingPath = "Category",
                YBindingPath = "Value",
                 Interior = new SolidColorBrush(Color.FromRgb(0x77, 0x77, 0x77))
            };

            ChartDataMarker datamarker = new ChartDataMarker()
            {
                ShowLabel = true,
                LabelPosition = DataMarkerLabelPosition.Outer,
                LabelTemplate = this.Resources["dataMarkerTemplate"] as DataTemplate
            };
        series.DataMarker = datamarker;

{% endhighlight %}

{% endtabs %}

![LabelTemplate support for datamarkers in WinUI Chart](DataMarkers_images/label_template.png)

## Label Format

[`SegmentLabelFormat`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_SegmentLabelFormat) property allows you to provide formatting for the labels.

The following code example demonstrates the y value having three decimal digits.

{% tabs %}

{% highlight xaml %}

        <syncfusion:ChartDataMarker ShowLabel="True" SegmentLabelFormat="#.000" DataMarkerPosition="Top">
        </syncfusion:ChartDataMarker>

{% endhighlight %}

{% highlight c# %}

        ChartDataMarker datamarker = new ChartDataMarker()
        {
             ShowLabel = true,
            SegmentLabelFormat = "0.000"
        };

{% endhighlight %}

{% endtabs %}

In the following image, you can see the decimal position will be rounded off to two digits by default.

![Adornments label format support in WinUI Chart](DataMarkers_images/label_format.png)

## Label Rotation

[`LabelRotationAngle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_LabelRotationAngle) property is used to define the angle to which the label has to rotate. The following code demonstrates the label rotating angle.

{% tabs %}

{% highlight xaml %}

        <syncfusion:ColumnSeries.DataMarker>
             <syncfusion:ChartDataMarker LabelPosition="Outer" LabelRotationAngle="45" ShowLabel="True"></syncfusion:ChartDataMarker>
        </syncfusion:ColumnSeries.DataMarker>
{% endhighlight %}

{% highlight c# %}

        ChartDataMarker datamarker = new ChartDataMarker()
        {
                ShowLabel = true,
                LabelRotationAngle = 45,
                LabelPosition = DataMarkerLabelPosition.Outer          
        };
{% endhighlight %}

{% endtabs %}

![DataMarkers label rotation support in WinUI Chart](DataMarkers_images/label_rotation.png)

## Connector Line

This feature is used to connect label and data point using a line. It can be enabled for any chart types but this is often used with Pie and Doughnut chart types. You can add connector line for the data markers using [`ShowConnectorLine`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_ShowConnectorLine) property. 

The connector line can be customized using the below properies.

* [`ConnectorHeight`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_ConnectorHeight)
* [`ConnectorLineStyle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_ConnectorLineStyle) 
* [`ConnectorRotationAngle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_ConnectorRotationAngle)
* [`ConnectorLineStyle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_ConnectorLineStyle)

The following code example shows the customization options for connector line:

{% tabs %}

{% highlight xaml %}

    <Window.Resources>

        <Style TargetType="Path" x:Key="lineStyle">
            <Setter Property="StrokeDashArray" Value="10,7,5"/>
            <Setter Property="Stroke" Value="Black"/>
        </Style>

    </Window.Resources>

    <Grid>
        <chart:SfChart Width="400" Height="400">
         ...

        <syncfusion:PieSeries Interior="#777777" ItemsSource="{Binding Demands}" XBindingPath="Category" YBindingPath="FloatValue" LabelPosition="OutsideExtended">
                <syncfusion:PieSeries.DataMarker>
                    <syncfusion:ChartDataMarker ShowLabel="True" ConnectorLineStyle="{StaticResource lineStyle}" ShowConnectorLine="True" LabelPosition="Outer"></syncfusion:ChartDataMarker>
                </syncfusion:PieSeries.DataMarker>
        </syncfusion:PieSeries>

        ...
        </chart:SfChart>
    </Grid>

{% endhighlight %}

{% highlight c# %}

        PieSeries series = new PieSeries()
        {
                ItemsSource = new ViewModel().Demands,
                XBindingPath = "Category",
                YBindingPath = "FloatValue",
                LabelPosition = CircularSeriesLabelPosition.OutsideExtended,
                Interior = new SolidColorBrush(Color.FromRgb(0x77, 0x77, 0x77))
        };

        ChartDataMarker datamarker = new ChartDataMarker()
        {
                ShowLabel = true,
                ShowConnectorLine = true,
                UseSeriesPalette = true,
                ConnectorLineStyle = this.Resources["lineStyle"] as Style
                LabelPosition = DataMarkerLabelPosition.Outer,
        };
        series.DataMarker = datamarker;

{% endhighlight %}

{% endtabs %}

![Connector line for adornments support in WinUI Chart](DataMarkers_images/connectorline.png)

**Connector Type**

[`ConnectorType`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CircularSeriesBase.html#Syncfusion_UI_Xaml_Charts_CircularSeriesBase_ConnectorType) property in AccumulationSeries is used to specify the connector line type such as [`Line`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ConnectorMode.html) or [`Bezier`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ConnectorMode.html). This property is only for AccumulationSeries like PieSeries, DoughnutSeries, PyramidSeries and FunnelSeries.


{% tabs %}

{% highlight xaml %}

        <chart:PieSeries Interior="#777777" ItemsSource="{Binding Performance}" XBindingPath="ServerLoad"
            YBindingPath="Server1" EnableSmartLabels="True" ConnectorType="Bezier" LabelPosition="OutsideExtended">
                <chart:PieSeries.DataMarker>
                    <chart:ChartDataMarker HorizontalAlignment="Center" VerticalAlignment="Center" ShowConnectorLine="True" 
                             ConnectorHeight="80" ShowLabel="True" />
                </chart:PieSeries.DataMarker>
        </chart:PieSeries>

{% endhighlight %}

{% highlight c# %}

        PieSeries series = new PieSeries()
        {
                ItemsSource = new ServerViewModel().Performance,
                XBindingPath = "Year",
                YBindingPath = "Plastic",
                EnableSmartLabels = true,
                ExplodeAll = true,
                ExplodeRadius = 3,
                ConnectorType=ConnectorMode.Bezier,
                LabelPosition = CircularSeriesLabelPosition.OutsideExtended,
                Interior = new SolidColorBrush(Color.FromRgb(0x77, 0x77, 0x77))
        };

        ChartDataMarker datamarker = new ChartDataMarker()
            {
                ShowLabel = true,
                ShowConnectorLine = true,
                HorizontalAlignment = HorizontalAlignment.Center,
                VerticalAlignment = VerticalAlignment.Center,
                ConnectorHeight= 80
            };

    {% endhighlight %}

{% endtabs %}

 **Line** 
 
 ![Connector Line in WinUI Chart](DataMarkers_images/Line.png) 

 **Bezier**
 
  ![Bezier in WinUI Chart](DataMarkers_images/Bezier.png)

   **Straight Line**

![Connector line with StraightLine type](DataMarkers_images/StraightLine.png)

## Applying Series Brush

[`UseSeriesPalette`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartDataMarkerBase.html#Syncfusion_UI_Xaml_Charts_ChartDataMarkerBase_UseSeriesPalette) property is used to set the interior of the series to the data marker background. 

>N For Accumulation like Pie, Doughnut, Funnel and Pyramid the segment interior color will be reflected in data marker background.

{% tabs %}

{% highlight xaml %}

        <syncfusion:ChartDataMarker ShowLabel="True" UseSeriesPalette="True">

        </syncfusion:ChartDataMarker>

{% endhighlight %}

{% highlight c# %}

        ChartDataMarker datamarker = new ChartDataMarker()
        {
            ShowLabel = true,
            UseSeriesPalette = true
        };

{% endhighlight %}

{% endtabs %}

## Smart Labels

When you have more datapoints in Pie or Doughnut series, the data marker labels might get overlap with each other. Chart provides built-in support to avoid these overlapping by using [`EnableSmartLabels`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CircularSeriesBase.html#Syncfusion_UI_Xaml_Charts_CircularSeriesBase_EnableSmartLabels) property.

The following code example demonstrates the EnableSmartLabels property:

{% tabs %}

{% highlight xaml %}

        <chart:PieSeries Interior="#777777" ItemsSource="{Binding CategoricalData}" ConnectorType="Bezier" XBindingPath="Year"
            YBindingPath="Plastic" EnableSmartLabels="True" LabelPosition="OutsideExtended" ExplodeAll="True" ExplodeRadius="3">
                <chart:PieSeries.DataMarker>
                    <chart:ChartDataMarker ShowLabel="True" HorizontalAlignment="Center" VerticalAlignment="Center" ShowConnectorLine="True"></chart:ChartDataMarker>
                </chart:PieSeries.DataMarker>
        </chart:PieSeries>

{% endhighlight %}

{% highlight c# %}

        PieSeries series = new PieSeries()
        {
                ItemsSource = new ViewModel().CategoricalData,
                XBindingPath = "Year",
                YBindingPath = "Plastic",
                EnableSmartLabels = true,
                ExplodeAll = true,
                ExplodeRadius = 3,
                Palette = ChartColorPalette.Custom,
                LabelPosition = CircularSeriesLabelPosition.OutsideExtended,
                Interior = new SolidColorBrush(Color.FromRgb(0x77, 0x77, 0x77))
        };

            ChartDataMarker datamarker = new ChartDataMarker()
            {
                ShowLabel = true,
                ShowConnectorLine = true,
                UseSeriesPalette = true,
                HorizontalAlignment = HorizontalAlignment.Center,
                VerticalAlignment = VerticalAlignment.Center
            };
            series.DataMarker = datamarker;

{% endhighlight %}

{% endtabs %}

![Smart labels for datamarkers in WinUI Chart](DataMarkers_images/smartlabel.png)

N> For circular series, the data marker position can be changed to [`Inside`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CircularSeriesLabelPosition.html), [`Outside`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CircularSeriesLabelPosition.html) or [`OutsideExtended`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CircularSeriesLabelPosition.html) using the [`LabelPosition`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CircularSeriesBase.html#Syncfusion_UI_Xaml_Charts_CircularSeriesBase_LabelPosition) property.
