---
layout: post
title: Data labels in WinUI Circular Chart control | WinUI | Syncfusion
description: This section explains about how to configure the Data Labels and its features applying in WinUI Circular Chart (SfCircularChart).
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Data labels in WinUI Circular Chart

Data labels are used to display values related to a chart segment. Values from data point(x, y) or other custom properties from a data source can be displayed. 

Each data label can be represented by the following:

* Label - Displays the segment label content at the (X, Y) point.
* ConnectorLine - Line used to connect the (X, Y) point and the label element.

## Enable data label 

[ShowDataLabels]() property of series is used to enable the data labels. The following code example illustrates how to achieve this.

{% tabs %}

{% highlight xaml %}

<chart:PieSeries ShowDataLabels="True"
                 ItemsSource="{Binding Data}"  
                 XBindingPath="Product" 
                 YBindingPath="SalesRate"/>

{% endhighlight %}

{% highlight c# %}

PieSeries series = new PieSeries();
series.ShowDataLabels = true;

{% endhighlight %}

{% endtabs %}

![Data labels in WinUI Circular chart](DataLabel_Images/WinUI_Circular_chart_data_label_overview.png) 

## Data label context

To customize the content of data labels, need to define [DataLabelSettings]() of series and set [Context]() property of [DataLabelSettings]() to define the value to be displayed as label content.

The following code example demonstrates about define the percentage value to be displayed as data label content.

{% tabs %}

{% highlight xaml %}
<chart:PieSeries ShowDataLabels="True">
. . .
<chart:PieSeries.DataLabelSettings>
    <chart:CircularDataLabelSettings Context="Percentage"/>
</chart:PieSeries.DataLabelSettings>

</chart:PieSeries>

{% endhighlight %}

{% highlight c# %}
        
PieSeries series = new PieSeries();
series.ShowDataLabels = true;
series.DataLabelSettings = new CircularDataLabelSettings() {Context = LabelContext.Percentage };

{% endhighlight %}

{% endtabs %}

| Context values | Description |
|---|--|
|DataLabelItem | Displays the y value|
| Percentage | Displays the percentage value of series point among other points|
| XValue | Displays the X value of series point|
| YValue | Displays the Y value of series point|

![Data labels context in WinUI Circular chart](DataLabel_Images/WinUI_Circular_chart_data_label_Context.png) 

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

<chart:PieSeries.DataLabelSettings>
    <chart:CircularDataLabelSettings Position="Outside"
                                     Foreground="White"
                                     FontSize="11" 
                                     FontFamily="Calibri" 
                                     BorderBrush="Black" 
                                     BorderThickness="1" Margin="1" 
                                     FontStyle="Italic" Background="#1E88E5"
                                     Context="Percentage"/>
</chart:PieSeries.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}

series.DataLabelSettings = new CircularDataLabelSettings()
{
    Position = CircularSeriesLabelPosition.Outside,
    Foreground = new SolidColorBrush(Colors.White),
    BorderBrush = new SolidColorBrush(Colors.Black),
    Background =new SolidColorBrush(Colors.AliceBlue),
    BorderThickness = new Thickness(1),
    Margin = new Thickness(1),
    FontStyle = FontStyle.Italic,
    FontFamily = new FontFamily("Calibri"),
    FontSize = 11
};

{% endhighlight %}

{% endtabs %}

![Data label customization in WinUI Circular Chart](DataLabel_Images/WinUI_Circular_chart_datalabel_custom_Label.png)

## Label template

The appearance of the data label can be customized using [`ContentTemplate`]() property of [`CircularDataLabelSettings`]() as in the below code example:

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart >
    <chart:SfCircularChart.Resources>
        <local:ChartValueConverter x:Key="valueconvert"/>
        <DataTemplate x:Key="labelTemplate">
            <StackPanel Margin="10" Orientation="Vertical">
                <Ellipse Height="15" Width="15" Fill="{Binding Interior}" 
                 Stroke="#4a4a4a" StrokeThickness="2"/>
                <TextBlock HorizontalAlignment="Center" FontSize="12"
                           Foreground="Black" 
                           FontWeight="SemiBold" Text="{Binding Item.Product}"/>
            </StackPanel>
        </DataTemplate>
    </chart:SfCircularChart.Resources>
...
<chart:PieSeries ShowDataLabels="True">
    <chart:PieSeries.DataLabelSettings>
        <chart:CircularDataLabelSettings Position="Outside" ContentTemplate="{StaticResource labelTemplate}"
                                         Context="DataLabelItem"/>
    </chart:PieSeries.DataLabelSettings>
</chart:PieSeries>

{% endhighlight %}

{% highlight c# %}

series.DataLabelSettings = new CircularDataLabelSettings()
{
    Position = CircularSeriesLabelPosition.Outside,
    Context = LabelContext.DataLabelItem,
    ContentTemplate = chart.Resources["labelTemplate"] as DataTemplate,
};

{% endhighlight %}

{% endtabs %}

![Template support for data label in WinUI Circular Chart](DataLabel_Images/WinUI_Circular_chart_dataLabel_Contenttemplate.png)

## Label rotation

[Rotation]() property is used to define the angle to which the label has to rotate. The following code demonstrates the label rotating angle.

{% tabs %}

{% highlight xaml %}

<chart:PieSeries.DataLabelSettings>
    <chart:CircularDataLabelSettings Position="Outside" Rotation="335"/>
</chart:PieSeries.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}

series.DataLabelSettings = new CircularDataLabelSettings()
{
    Position = CircularSeriesLabelPosition.Outside,
    Rotation = 335,
};

{% endhighlight %}

{% endtabs %}

![Rotation support for data label in WinUI Circular Chart](Datalabel_Images/WinUI_Circular_chart_dataLabel_Label_Rotation.png)

## Connector Line

Connector line is used to connect label and data point using a line. [ShowConnectorLine]() property of [CircularDataLabelSettings]() is used to enable the connector line in the circular chart. 

The connector line can be customized using the below properies.

* [ConnectorHeight]() - used to set height for connector line.
* [ConnectorLineStyle]() - used to customize the style of line.
* [ConnectorType]() - used to connector line type.

The following code example shows the customization of connector line:

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart.Resources>
    <Style TargetType="Path" x:Key="lineStyle">
        <Setter Property="StrokeDashArray" Value="10,7,5"/>
        <Setter Property="Stroke" Value="Black"/>
    </Style>
</chart:SfCircularChart.Resources>
. . . 
<chart:PieSeries.DataLabelSettings>
    <chart:CircularDataLabelSettings 
    ShowConnectorLine="True" ConnectorHeight="40" ConnectorType="StraightLine" ConnectorLineStyle="{StaticResource lineStyle}"/>
</chart:PieSeries.DataLabelSettings>


{% endhighlight %}

{% highlight c# %}

series.DataLabelSettings = new CircularDataLabelSettings()
{
    ShowConnectorLine = true,
    ConnectorHeight = 40,
    ConnectorLineStyle = chart.Resources["lineStyle"] as Style,
};

{% endhighlight %}

{% endtabs %}

![Connector line support for datalabels in WinUI circular chart](DataLabel_Images/WinUI_Circular_chart_data_label_Connector_line.png)

### Connector Type

[ConnectorType]() property in [CircularDataLabelSettings]() is used to specify the connector line type such as [Line]() or [Bezier]() or [StraightLine]().

{% tabs %}

{% highlight xaml %}

<chart:PieSeries.DataLabelSettings>
    <chart:CircularDataLabelSettings ConnectorType="Bezier"
                                     Position="Outside"
                                     ShowConnectorLine="True"/>
</chart:PieSeries.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}

series.DataLabelSettings = new CircularDataLabelSettings()
{
    ShowConnectorLine = true,
    ConnectorType = ConnectorMode.Bezier, 
    Position = CircularSeriesLabelPosition.Outside,
};

{% endhighlight %}

{% endtabs %}

 **Bezier**
 
![Connector line with Bezier type in WinUI Chart](DataLabel_Images/WinUI_Circular_chart_dataLabel_Bezier_line.png)

 **Line** 
 
 ![Connector line with Line type in WinUI Chart](DataLabel_Images/WinUI_Circular_chart_dataLabel_line.png) 

**Straight Line**

![Connector line with StraightLine type in WinUI Chart](DataLabel_Images/WinUI_Circular_chart_dataLabel_Straight_line.png)

## Applying series brush

[`UseSeriesPalette`]() property is used to set the interior of the series to the data label background. 

{% tabs %}

{% highlight xaml %}

<chart:PieSeries.DataLabelSettings>
    <chart:CircularDataLabelSettings UseSeriesPalette="True"/>
</chart:PieSeries.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}

series.DataLabelSettings = new CircularDataLabelSettings()
{
    UseSeriesPalette = true,
};

{% endhighlight %}

{% endtabs %}

![Applying UseSeriesPalette in WinUI Chart](DataLabel_Images/WinUI_Circular_chart_dataLabel_UseSeriesPalette.png)

