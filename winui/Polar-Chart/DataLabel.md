---
layout: post
title: Data labels in WinUI Chart control | Syncfusion
description: This section explains about how to configure the data labels and its features in Syncfusion WinUI Chart (SfPolarChart) control.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Data label in WinUI Chart (SfPolarChart)

Data labels are used to display values related to a chart segment. Values from data points(x, y) or other custom properties from a data source can be displayed.

Each data label can be represented by the following:

* `Label` - displays the segment label content at the (X, Y) point.
* `Connector line` - used to connect the (X, Y) point and the label element.

## Enable Data Label

The [ShowDataLabels]() property of a series is used to enable the data labels.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    ...
    <chart:PolarAreaSeries ShowDataLabels="True"
                    ItemsSource="{Binding Data}"  
                    XBindingPath="Product" 
                    YBindingPath="SalesRate"/>
    ...
</chart:SfPolarChart>                 

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
PolarAreaSeries series = new PolarAreaSeries();
series.ShowDataLabels = true;
...

{% endhighlight %}

{% endtabs %}

![Data label in WinUI chart](DataLabel_Images/WinUI_PolarChart_data_label.png)

## Context

To customize the content of data labels, need to define [DataLabelSettings]() of series and set [Context]() property of [DataLabelSettings]() to define the value to be displayed as label content.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    <chart:PolarAreaSeries ShowDataLabels="True"
                        ItemsSource="{Binding PlantDetails}" 
                        XBindingPath="Direction"
                        YBindingPath="Tree">
    <chart:PolarAreaSeries.DataLabelSettings>
        <chart:PolarDataLabelSettings Context="Percentage"/>
    </chart:PolarAreaSeries.DataLabelSettings>

    </chart:PolarAreaSeries>
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
...
PolarAreaSeries series = new PolarAreaSeries();
series.ShowDataLabels = true;
series.DataLabelSettings = new PolarDataLabelSettings() {Context = LabelContext.Percentage };
...

{% endhighlight %}

{% endtabs %}

![Data label support in WinUI chart](DataLabel_Images/WinUI_PolarChart_data_label_percentage.png)

## Customization

The following properties are used to customize the data label.

* [`BorderBrush`]()- used to change the border color.
* [`BorderThickness`]()- used to change the thickness of the border.
* [`Margin`]()- used to change the margin size for label.
* [`FontStyle`]()-  used to change font style of the label.
* [`FontSize`]()-  used to change font size of the label.
* [`Foreground`]()- used to change the text color of the label.
* [`FontFamily`]()-  used to change the font family of the label.
* [`Background`]()- used to change the label background color.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    ...
    <chart:PolarAreaSeries ItemsSource="{Binding PlantDetails}" 
                            XBindingPath="Direction" 
                            YBindingPath="Tree" Label="Tree"
                            ShowDataLabels="True">
                <chart:PolarAreaSeries.DataLabelSettings>
                    <chart:PolarDataLabelSettings Foreground="White" FontSize="12" FontFamily="Calibri" BorderBrush="White"                             BorderThickness="1" Margin="1" FontStyle="Italic" Background="#1E88E5">
                    </chart:PolarDataLabelSettings>
                </chart:PolarAreaSeries.DataLabelSettings>
    </chart:PolarAreaSeries>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
...
PolarAreaSeries series = new PolarAreaSeries();
series.ShowDataLabels = true;
series.DataLabelSettings = new PolarDataLabelSettings() 
{ 
    Foreground = new SolidColorBrush(Colors.White),
    BorderBrush = new SolidColorBrush(Colors.White),
    Background = "#1E88E5",
    BorderThickness = new Thickness(1),
    Margin = new Thickness(1),
    FontStyle = FontStyles.Italic,
    FontFamily = new FontFamily("Calibri"),
    FontSize = 12
};
...

{% endhighlight %}

{% endtabs %}

![Data label customization support in WinUI Chart](DataLabel_Images/WinUI_PolarChart_data_label_customize.png)

## Template

The appearance of the data label can be customized using the [`ContentTemplate`]() property of [`PolarDataLabelSettings`]() as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart >
    <chart:SfPolarChart.Resources>
        <DataTemplate x:Key="datalabelTemplate">
                    <Grid>
                        <Ellipse
                                Width="30"
                                Height="30"
                                HorizontalAlignment="Left"
                                VerticalAlignment="Top"
                                Fill="White"
                                Stroke="#0078DE"
                                StrokeThickness="2" />
                        <TextBlock
                                HorizontalAlignment="Center"
                                VerticalAlignment="Center"
                                FontFamily="Segoe UI"
                                FontSize="12"
                                Foreground="#FF585858"
                                Text="{Binding}"
                                TextWrapping="Wrap" />
                    </Grid>
            </StackPanel>
        </DataTemplate>
    </chart:SfPolarChart.Resources>
    ...
    <chart:PolarLineSeries ShowDataLabels="True">
        <chart:PolarLineSeries.DataLabelSettings>
            <chart:PolarDataLabelSettings ContentTemplate="{StaticResource datalabelTemplate}"
                                            Context="DataLabelItem"/>
        </chart:PolarLineSeries.DataLabelSettings>
    </chart:PolarLineSeries>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
...
PolarLineSeries series = new PolarLineSeries();
series.ShowDataLabels = true;

series.DataLabelSettings = new PolarDataLabelSettings() 
{ 
    Context = LabelContext.DataLabelItem,
    ContentTemplate = chart.Resources["datalabelTemplate"] as DataTemplate,
};
...

{% endhighlight %}

{% endtabs %}

![Template support for data label in WinUI Chart](DataLabel_Images/WinUI_PolarChart_DataLabel_LabelTemplate.png)

## Format

The [Format]() property can be used to format the data labels.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart x:Name="chart">
    ...
    <chart:PolarLineSeries ShowDataLabels="True">
        <chart:PolarLineSeries.DataLabelSettings>
            <chart:PolarDataLabelSettings Format="#.0"/>
        </chart:PolarLineSeries.DataLabelSettings>
    </chart:PolarLineSeries>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
. . . 
PolarLineSeries series = new PolarLineSeries();
series.ShowDataLabels = true;

series.DataLabelSettings = new PolarDataLabelSettings() 
{ 
    Format = "#.0",
};
...

{% endhighlight %}

{% endtabs %}

![Label format support for data label in WinUI Chart](DataLabel_Images/WinUI_PolarChart_data_label_format.png)

## Rotation

[Rotation]() property is used to define the angle to which the label has to rotate.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart x:Name="chart">
...
    <chart:PolarLineSeries ShowDataLabels="True"  
                            ItemsSource="{Binding PlantDetails}" 
                            XBindingPath="Direction" 
                            YBindingPath="Tree">
        <chart:PolarLineSeries.DataLabelSettings>
            <chart:PolarDataLabelSettings Rotation="-45"/>
        </chart:PolarLineSeries.DataLabelSettings>
    </chart:PolarLineSeries>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
. . . 
PolarLineSeries series = new PolarLineSeries();
series.ShowDataLabels = true;

series.DataLabelSettings = new PolarDataLabelSettings() 
{ 
    Rotation = -45,
};
...

{% endhighlight %}

{% endtabs %}

![Rotation support for data label in WinUI Chart](DataLabel_Images/WinUI_PolarChart_data_label_Rotation.png)

## Applying Series Interior

The [`UseSeriesPalette`]() property is used to set the [Interior]() of the series to the data label background. 

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart x:Name="chart">
...
    <chart:PolarLineSeries ShowDataLabels="True"  
                            ItemsSource="{Binding PlantDetails}" 
                            XBindingPath="Direction" 
                            YBindingPath="Tree">
        <chart:PolarLineSeries.DataLabelSettings>
            <chart:PolarDataLabelSettings UseSeriesPalette="True"/>
        </chart:PolarLineSeries.DataLabelSettings>
    </chart:PolarLineSeries>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
. . . 
PolarLineSeries series = new PolarLineSeries();
series.ShowDataLabels = true;
series.DataLabelSettings = new PolarDataLabelSettings()
{
    UseSeriesPalette = true,
};
...

{% endhighlight %}

{% endtabs %}

![Applying UseSeriesPalette in WinUI Chart](DataLabel_Images/WinUI_PolarChart_data_label_UseSeriesPalette.png)

## Connector Line

Connector line is used to connect label and data point using a line. [ShowConnectorLine]() property of [PolarDataLabelSettings]() is used to enable the connector line in the polar chart.

The connector line can be customized using the following properties:

* [ConnectorHeight]() - used to set height for connector line.
* [ConnectorLineStyle]() -  used to customize the style of line.
* [ConnectorRotation]() - used to rotate the connector line at any angle.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart x:Name="chart">
...
    <chart:PolarLineSeries ShowDataLabels="True"  
                            ItemsSource="{Binding PlantDetails}" 
                            XBindingPath="Direction" 
                            YBindingPath="Tree">
        <chart:PolarLineSeries.DataLabelSettings>
            <chart:PolarDataLabelSettings ShowConnectorLine="True" ConnectorHeight="25" 
                                          ConnectorRotation="45"/>
        </chart:PolarLineSeries.DataLabelSettings>
    </chart:PolarLineSeries>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
. . . 
PolarLineSeries series = new PolarLineSeries();
series.ShowDataLabels = true;
series.DataLabelSettings = new PolarDataLabelSettings()
{
    ShowConnectorLine = true,
    ConnectorHeight = 25,
    ConnectorRotation = 45,
};
...

{% endhighlight %}

{% endtabs %}

![ConnectorLine in WinUI Chart](DataLabel_Images/WinUI_PolarChart_data_label_ConnectorLine.png)