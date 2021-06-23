---
layout: post
title: Data Markers in WinUI Cartesian Chart control | Syncfusion
description: This section explains about how to configure the data labels and its features in WinUI Cartesian Chart (SfCartesianChart).
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Data labels in WinUI Cartesian Chart

Data labels are used to display values related to a chart segment. Values from data point(x, y) or other custom properties from a data source can be displayed. 

Each data label can be represented by the following:

* Label - displays the segment label content at the (X, Y) point.
* Connector line - used to connect the (X, Y) point and the label element.

## Enable data label 

[ShowDataLabels]() property of series is used to enable the data labels. The following code example illustrates how to achieve this.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Series>
    <chart:ColumnSeries ItemsSource="{Binding Data}" 
                     XBindingPath="Category"
                     YBindingPath="Value" ShowDataLabels="True">
    </chart:ColumnSeries>
</chart:SfCartesianChart.Series>

{% endhighlight %}

{% highlight c# %}

ColumnSeries series = new ColumnSeries()
{
    ItemsSource = viewModel.Data,
    XBindingPath = "Category",
    YBindingPath = "Value",
    ShowDataLabels = true
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Data label in WinUI Cartesian chart](DataMarkers_images/datamarker_label_overview.png) 

## Data label context

To customize the content of data labels, need to define [DataLabelSettings]() of series and set [Context]() property of [CartesianDataLabelSettings]() to define the value to be displayed as label content.

The following code example demonstrates about define the value to be displayed as data label content.

{% tabs %}

{% highlight xaml %}

<chart:ColumnSeries.DataLabelSettings>
    <chart:CartesianDataLabelSettings Context="YValue"/>
</chart:ColumnSeries.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}
        
series.DataLabelSettings = new CartesianDataLabelSettings()
{
    Context = LabelContext.YValue
};

{% endhighlight %}

{% endtabs %}

| SegmentLabelContent values | Description | Output |
|---|--|---|
| DateTime | Displays LabelContent.DateTime value | ![ DateTime label in WinUI Cartesian chart](DataMarkers_images/labelcontent_datetime.png) |
|DataLabelItem | Displays the y value|![ LabelContentPath label in WinUI Cartesian chart](DataMarkers_images/labelcontent_labelcontentpath.png)|
| Percentage | Displays the percentage value of series point among other points |![ Percentage label in WinUI Cartesian chart](DataMarkers_images/labelcontent_percentage.png) |
| XValue | Displays the X value of series point|![ XValue label in WinUI Cartesian chart](DataMarkers_images/labelcontent_xvalue.png) |
| YValue | Displays the Y value of series point| ![ YValue label in WinUI Cartesian chart](DataMarkers_images/labelcontent_yvalue.png) |

## Data Label customization

The following properties are used to customize the data label.

* [BorderBrush]()- used to change the border color.
* [BorderThickness]()- used to change the thickness of the border.
* [Margin]()- used to change the margin size for label.
* [FontStyle]()-  used to change font style of the label.
* [FontSize]()-  used to change font size of the label.
* [Foreground]()- used to change the color of the label.
* [FontFamily]()-  used to change the font family of the label.
* [Background]()- used to change the label background color.

The following code example demonstrates the customization of label using the above properties:

{% tabs %}

{% highlight xaml %}

<chart:ColumnSeries.DataLabelSettings>
    <chart:CartesianDataLabelSettings Position="Outer" Foreground="White" 
                                      FontSize="11" FontFamily="Calibri" 
                                      BorderBrush="Black" BorderThickness="1" 
                                      Margin="1" FontStyle="Italic" Background="#1E88E5" />
</chart:ColumnSeries.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}

series.DataLabelSettings = new CartesianDataLabelSettings()
{
    Position = DataLabelPosition.Outer,
    Foreground = new SolidColorBrush(Colors.White),
    BorderBrush = new SolidColorBrush(Colors.Black),
    Background = new SolidColorBrush(Colors.LightBlue),
    BorderThickness = new Thickness(1),
    Margin = new Thickness(1),
    FontStyle = FontStyle.Italic,
    FontFamily = new FontFamily("Calibri"),
    FontSize = 11
};

{% endhighlight %}

{% endtabs %}

![Label customization in WinUI Cartesian chart](DataMarkers_images/datamarker_custom_Label.png)

## Label template

The appearance of the data label can be customized using [`ContentTemplate`]() property of [`CartesianDataLabelSettings`]() as in the below code example:

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Resources>
    <DataTemplate x:Key="dataMarkerTemplate">
        <StackPanel Orientation="Vertical">
            <Path Grid.Row="0"  Stretch="Uniform" Fill="#1E88E5"                              
               Width="15" Height="15" Margin="0,0,0,0"                              
               RenderTransformOrigin="0.5,0.5"
               Data="M22.5,15.8899993896484L37.5,                                
               30.8899993896484 7.5,30.8899993896484 22.5,15.8899993896484z">
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
</chart:SfCartesianChart.Resources>
. . . 
<chart:ColumnSeries.DataLabelSettings>
    <chart:CartesianDataLabelSettings Position="Outer" ContentTemplate="{StaticResource dataMarkerTemplate}"/>
</chart:ColumnSeries.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}

series.DataLabelSettings = new CartesianDataLabelSettings()
{
    Position = DataLabelPosition.Outer,
    ContentTemplate = chart.Resources["dataMarkerTemplate"] as DataTemplate
};

{% endhighlight %}

{% endtabs %}

![Label template in WinUI Cartesian chart](DataMarkers_images/datamarker_labeltemplate.png)

## Label Format

[Format]() property allows to provide formatting for the labels.

The following code example demonstrates the y value having three decimal digits.

{% tabs %}

{% highlight xaml %}

<chart:ColumnSeries.DataLabelSettings>
    <chart:CartesianDataLabelSettings Format="#.000" />
</chart:ColumnSeries.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}

series.DataLabelSettings = new CartesianDataLabelSettings()
{
    Format = "#.000"
};

{% endhighlight %}

{% endtabs %}

In the following image, you can see the decimal position will be rounded off to two digits by default.

![Label format in WinUI Cartesian chart](DataMarkers_images/datamarker_labelformat.png)

## Label Rotation

[Rotation]() property is used to define the angle to which the label has to rotate. The following code demonstrates the label rotating angle.

{% tabs %}

{% highlight xaml %}

<chart:ColumnSeries.DataLabelSettings>
    <chart:CartesianDataLabelSettings Rotation="45" Position="Outer" />
</chart:ColumnSeries.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}

series.DataLabelSettings = new CartesianDataLabelSettings()
{
    Rotation = 45,
    Position = DataLabelPosition.Outer,
};

{% endhighlight %}

{% endtabs %}

![Label rotation in WinUI Cartesian chart](DataMarkers_images/label_rotation.png)

## Alignment

The alignment of data markers inside the series is defined using [BarLabelAlignment]() property. 

* [Top]() - Positions the data marker at the top edge point of a chart segment.
* [Middle]() - Positions the data marker at the center point of a chart segment.
* [Bottom]() - Positions the data marker at the bottom edge point of a chart segment.

N> This behavior varies based on the chart series type.

The following code example explains the positioning of data markers in the middle of the segment.

{% tabs %}

{% highlight xaml %}

<chart:ColumnSeries.DataLabelSettings>
    <chart:CartesianDataLabelSettings BarLabelAlignment="Middle"/>
</chart:ColumnSeries.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}

series.DataLabelSettings = new CartesianDataLabelSettings()
{
    BarLabelAlignment = BarLabelAlignment.Middle,
};

{% endhighlight %}

{% endtabs %}

![Label alignment in WinUI Cartesian chart](DataMarkers_images/WinUI_BarAlignment_Middle.png)

Also, you can define the label alignment using  [HorizontalAlignment]() and [VerticalAlignment]() properties.

## Position

Other than the above alignment options, Chart providing additional customization option to position the data markers smartly based on series types using [Position]() property.

The following are the values for this property: 

* [Default]()
* [Auto]()
* [Inner]()
* [Outer]()
* [Center]()

The following code sample illustrates the center position of data marker labels,

{% tabs %}

{% highlight xaml %}

<chart:ColumnSeries.DataLabelSettings>
    <chart:CartesianDataLabelSettings Position="Center"/>
</chart:ColumnSeries.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}

series.DataLabelSettings = new CartesianDataLabelSettings()
{
    Position = DataLabelPosition.Center,
};    

{% endhighlight %}

{% endtabs %}

| Column | Spline |
|--|--|
|![center Column](DataMarkers_images/labelposition_center_column.png)|![center Series](DataMarkers_images/labelposition_center_spline.png)|

The following code sample illustrates the inner position of data marker labels,

{% tabs %}

{% highlight xaml %}

<chart:ColumnSeries.DataLabelSettings>
    <chart:CartesianDataLabelSettings Position="Inner"/>
</chart:ColumnSeries.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}

series.DataLabelSettings = new CartesianDataLabelSettings()
{
    Position = DataLabelPosition.Inner,
};       

{% endhighlight %}

{% endtabs %}

| Column | Spline |
|--|--|
|![Inner Column](DataMarkers_images/labelposition_inner_column.png)|![Inner Series](DataMarkers_images/labelposition_inner_spline.png)|

The following code sample illustrates the outer position of data marker labels,

{% tabs %}

{% highlight xaml %}

<chart:ColumnSeries.DataLabelSettings>
    <chart:CartesianDataLabelSettings Position="Outer"/>
</chart:ColumnSeries.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}

series.DataLabelSettings = new CartesianDataLabelSettings()
{
    Position = DataLabelPosition.Outer,
};    

{% endhighlight %}

{% endtabs %}

| Column | Spline |
|--|--|
|![Outer Column](DataMarkers_images/labelposition_outer_column.png)|![Outer Series](DataMarkers_images/labelposition_outer_spline.png)|

## Connector Line

Connector line is used to connect label and data point using a line. [ShowConnectorLine]() property of [CartesianDataLabelSettings]() is used to enable the connector line in the cartesian chart. 

The connector line can be customized using the below properies.

* [ConnectorHeight]() - used to set height for connector line.
* [ConnectorLineStyle]() - used to customize the style of line.
* [ConnectorType]() - used to connector line type.

The following code example shows the customization of connector line:

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Resources>
    <Style TargetType="Path" x:Key="lineStyle">
        <Setter Property="StrokeDashArray" Value="10,7,5"/>
        <Setter Property="Stroke" Value="Black"/>
    </Style>
</chart:SfCartesianChart.Resources>
. . .
<chart:ColumnSeries.DataLabelSettings>
    <chart:CartesianDataLabelSettings Position="Outer" 
                                      ConnectorHeight="40"
                                      ShowConnectorLine="True"
                                      ConnectorLineStyle="{StaticResource lineStyle}" />
</chart:ColumnSeries.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}

series.DataLabelSettings = new CartesianDataLabelSettings()
{
    Position = DataLabelPosition.Outer,
    ConnectorHeight = 40,
    ConnectorLineStyle = chart.Resources["LineStyle"] as Style,
};

{% endhighlight %}

{% endtabs %}

![Connector line for Label in WinUI Cartesian chart](DataMarkers_images/connectorline.png)

## Applying Series Brush

[UseSeriesPalette]() property is used to set the interior of the series to the data marker background. 

{% tabs %}

{% highlight xaml %}

<chart:ColumnSeries.DataLabelSettings>
    <chart:CartesianDataLabelSettings  UseSeriesPalette="True"/>
</chart:ColumnSeries.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}

series.DataLabelSettings = new CartesianDataLabelSettings()
{
    UseSeriesPalette = true,
};

{% endhighlight %}

{% endtabs %}

![Applying UseSeriesPalette for Label in WinUI Cartesian chart](DataMarkers_images/useseriespalette_true.png)