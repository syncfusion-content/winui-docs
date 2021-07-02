---
layout: post
title: Data label in WinUI Chart control | WinUI | Syncfusion
description: This section explains about how to configure the data labels and its features in WinUI Chart (SfCircularChart).
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Data Label in WinUI Chart (SfCircularChart)

Data labels are used to display values related to a chart segment. Values from data point(x, y) or other custom properties from a data source can be displayed. 

Each data label can be represented by the following:

* Label - displays the segment label content at the (X, Y) point.
* Connector line - used to connect the (X, Y) point and the label element.

## Enable Data Label 

[ShowDataLabels](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataMarkerSeries.html#Syncfusion_UI_Xaml_Charts_DataMarkerSeries_ShowDataLabels) property of series is used to enable the data labels.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
<chart:PieSeries ShowDataLabels="True"
                 ItemsSource="{Binding Data}"  
                 XBindingPath="Product" 
                 YBindingPath="SalesRate"/>
. . .
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();
series.ShowDataLabels = true;
. . .
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Data labels in WinUI chart](DataLabel_Images/WinUI_pie_chart_data_label_overview.png) 

## Context

To customize the content of data labels, need to define [DataLabelSettings](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.CircularSeries.html?tabs=tabid-1#Syncfusion_UI_Xaml_Charts_CircularSeries_DataLabelSettings) of series and set [Context](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_Context) property of [DataLabelSettings](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.CircularSeries.html?tabs=tabid-1#Syncfusion_UI_Xaml_Charts_CircularSeries_DataLabelSettings) to define the value to be displayed as label content.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
<chart:PieSeries ShowDataLabels="True">
    <chart:PieSeries.DataLabelSettings>
        <chart:CircularDataLabelSettings Context="Percentage"/>
    </chart:PieSeries.DataLabelSettings>
</chart:PieSeries>
. . .
</chart:SfCircularChart>
{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();
series.ShowDataLabels = true;
series.DataLabelSettings = new CircularDataLabelSettings() {Context = LabelContext.Percentage };
. . .
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Data labels context in WinUI chart](DataLabel_Images/WinUI_pie_chart_data_label_context.png) 

## Customization

The following properties are used to customize the data label.

* [BorderBrush](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_BorderBrush)- used to change the border color.
* [BorderThickness](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_BorderThickness)- used to change the thickness of the border.
* [Margin](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_Margin)- used to change the margin size for label.
* [FontStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_FontStyle)-  used to change font style of the label.
* [FontSize](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_FontSize)-  used to change font size of the label.
* [Foreground](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_Foreground)- used to change the color of the label.
* [FontFamily](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_FontFamily)-  used to change the font family of the label.
* [Background](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_Background)- used to change the label background color.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
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
. . .
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . . 
PieSeries series = new PieSeries();
series.ShowDataLabels = true;
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

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Data label customization in WinUI Chart](DataLabel_Images/WinUI_pie_chart_data_label_customization.png)

## Template

The appearance of the data label can be customized using [`ContentTemplate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_ContentTemplate) property of [`CircularDataLabelSettings`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.CircularDataLabelSettings.html) as in the below code example:

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart >
    <chart:SfCircularChart.Resources>
        <DataTemplate x:Key="labelTemplate">
            <StackPanel Margin="10" Orientation="Vertical">
                <Ellipse Height="15" Width="15" Fill="Cyan" 
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
        <chart:CircularDataLabelSettings Position="Inside" ContentTemplate="{StaticResource labelTemplate}"
                                         Context="DataLabelItem"/>
    </chart:PieSeries.DataLabelSettings>
</chart:PieSeries>
. . .
</chart:SfCircularChart>
{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();
series.ShowDataLabels = true;
series.DataLabelSettings = new CircularDataLabelSettings()
{
    Position = CircularSeriesLabelPosition.Inside,
    Context = LabelContext.DataLabelItem,
    ContentTemplate = chart.Resources["labelTemplate"] as DataTemplate,
};
. . .
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Template support for data label in WinUI Chart](DataLabel_Images/WinUI_pie_chart_data_label_template.png)

## Position

[SfCircularChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCircularChart.html) providing additional customization option to position the data label smartly based on series types using [Position](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.CircularDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_CircularDataLabelSettings_Position) property.

The following are the values for this property:

[Inside](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.CircularSeriesLabelPosition.html#Syncfusion_UI_Xaml_Charts_CircularSeriesLabelPosition_Inside) - Data labels will be  placed inside over the CircularSeries.

[Outside](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.CircularSeriesLabelPosition.html#Syncfusion_UI_Xaml_Charts_CircularSeriesLabelPosition_Outside) - Data labels will be  placed just outside over the CircularSeries.

[OutsideExtended](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.CircularSeriesLabelPosition.html#Syncfusion_UI_Xaml_Charts_CircularSeriesLabelPosition_OutsideExtended) - Data labels will be placed outside over the CircularSeries at a certain distance.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
<chart:PieSeries ShowDataLabels="True">
    <chart:PieSeries.DataLabelSettings>
        <chart:CircularDataLabelSettings Position="OutsideExtended" ShowConnectorLine="True" Context="Percentage"/>
    </chart:PieSeries.DataLabelSettings>
</chart:PieSeries>
. . .
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();
series.ShowDataLabels = true;
series.DataLabelSettings = new CircularDataLabelSettings()
{
    Position = CircularSeriesLabelPosition.OutsideExtended,
    ShowConnectorLine = true,
    Context = LabelContext.Percentage
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Position support for data label in WinUI Chart](DataLabel_Images/WinUI_pie_chart_data_label_position.png)

## Rotation

[Rotation](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_Rotation) property is used to define the angle to which the label has to rotate. The following code demonstrates the label rotating angle.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
<chart:PieSeries ShowDataLabels="True">
    <chart:PieSeries.DataLabelSettings>
        <chart:CircularDataLabelSettings Position="Outside" Rotation="335"/>
    </chart:PieSeries.DataLabelSettings>
</chart:PieSeries>
. . .
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();
series.ShowDataLabels = true;
series.DataLabelSettings = new CircularDataLabelSettings()
{
    Position = CircularSeriesLabelPosition.Outside,
    Rotation = 335,
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Rotation support for data label in WinUI Chart](DataLabel_Images/WinUI_pie_chart_data_label_rotation.png)

## Connector Line

Connector line is used to connect label and data point using a line. [ShowConnectorLine](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_ShowConnectorLine) property of [CircularDataLabelSettings](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.CircularDataLabelSettings.html) is used to enable the connector line in the circular chart. 

The connector line can be customized using the below properties.

* [ConnectorHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_ConnectorHeight) - used to set height for connector line.
* [ConnectorLineStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_ConnectorLineStyle) - used to customize the style of line.
* [ConnectorType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.CircularDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_CircularDataLabelSettings_ConnectorType) - used to connector line type.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
    <chart:SfCircularChart.Resources>
        <Style TargetType="Path" x:Key="lineStyle">
            <Setter Property="StrokeDashArray" Value="10,7,5"/>
            <Setter Property="Stroke" Value="Black"/>
        </Style>
</chart:SfCircularChart.Resources>
. . . 
<chart:PieSeries ShowDataLabels="True">
    <chart:PieSeries.DataLabelSettings>
        <chart:CircularDataLabelSettings ShowConnectorLine="True" ConnectorHeight="40" ConnectorType="StraightLine" ConnectorLineStyle="{StaticResource lineStyle}"/>
    </chart:PieSeries.DataLabelSettings>
</chart:PieSeries>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();
series.ShowDataLabels = true;
series.DataLabelSettings = new CircularDataLabelSettings()
{
    ShowConnectorLine = true,
    ConnectorHeight = 40,
    ConnectorLineStyle = chart.Resources["lineStyle"] as Style,
};
. . .
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Connector line support for data labels in WinUI chart](DataLabel_Images/WinUI_pie_chart_data_label_connector_line.png)

### Connector Line Type

[ConnectorType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.CircularDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_CircularDataLabelSettings_ConnectorType) property in [CircularDataLabelSettings](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.CircularDataLabelSettings.html) is used to specify the connector line type such as [Line](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ConnectorMode.html#Syncfusion_UI_Xaml_Charts_ConnectorMode_Line) or [Bezier](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ConnectorMode.html#Syncfusion_UI_Xaml_Charts_ConnectorMode_Bezier) or [StraightLine](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ConnectorMode.html#Syncfusion_UI_Xaml_Charts_ConnectorMode_StraightLine).

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
<chart:PieSeries ShowDataLabels="True">
    <chart:PieSeries.DataLabelSettings>
        <chart:CircularDataLabelSettings ConnectorType="Bezier"
                                         Position="Outside"
                                         ShowConnectorLine="True"/>
    </chart:PieSeries.DataLabelSettings>
</chart:PieSeries>

</chart:SfCircularChart>
{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();

PieSeries series = new PieSeries();
series.ShowDataLabels = true;
series.DataLabelSettings = new CircularDataLabelSettings()
{
    ShowConnectorLine = true,
    ConnectorType = ConnectorMode.Bezier, 
    Position = CircularSeriesLabelPosition.Outside,
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

 **Bezier**
 
![Connector line with Bezier type in WinUI Chart](DataLabel_Images/WinUI_piec_chart_data_label_bezier_line.png)

## Applying Series Interior

[`UseSeriesPalette`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDataLabelSettings.html#Syncfusion_UI_Xaml_Charts_ChartDataLabelSettings_UseSeriesPalette) property is used to set the interior of the series to the data label background. 

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
<chart:PieSeries ShowDataLabels="True">
    <chart:PieSeries.DataLabelSettings>
        <chart:CircularDataLabelSettings UseSeriesPalette="True"/>
    </chart:PieSeries.DataLabelSettings>
</chart:PieSeries>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();
series.ShowDataLabels = true;
series.DataLabelSettings = new CircularDataLabelSettings()
{
    UseSeriesPalette = true,
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Applying UseSeriesPalette in WinUI Chart](DataLabel_Images/WinUI_pie_chart_data_label_background.png)
