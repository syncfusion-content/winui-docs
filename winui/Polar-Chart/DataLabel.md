---
layout: post
title: Data labels in WinUI Polar Chart control | Syncfusion
description: This section explains about how to add and customize the data labels in Syncfusion WinUI Polar Chart (SfPolarChart) control.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Data label in WinUI Polar Chart (SfPolarChart)

Chart data labels are used to display values related to a chart segment. Values from data point(x, y) or other custom properties from a data source can be displayed. 
Each data label can be represented by the following:

* Label - Displays the segment label content at the (X, Y) point.
* ConnectorLine - Line used to connect the (X, Y) point and the label element.

[ShowDataLabels]() property of series used to display the data labels, The following code example illustrates how to achieve this.

% tabs %}

{% highlight xaml %}

<chart:PolarLineSeries ShowDataLabels="True"
                 ItemsSource="{Binding Data}"  
                 XBindingPath="Product" 
                 YBindingPath="SalesRate"/>


{% endhighlight %}

{% highlight c# %}

PolarLineSeries series = new PolarLineSeries();
series.ShowDataLabels = true;
...

{% endhighlight %}

{% endtabs %}


## Define data label

To customize the content of data labels, need to define [DataLabelSettings]() of series.

[Context]() property of [DataLabelSettings]() allows to define the value to be displayed as label content.

The following code example demonstrates about define the percentage value to be displayed as label.

{% tabs %}

{% highlight xaml %}
<chart:PolarLineSeries ShowDataLabels="True">
. . .
<chart:PolarLineSeries.DataLabelSettings>
    <chart:PolarDataLabelSettings Context="Percentage"/>
</chart:PolarLineSeries.DataLabelSettings>

</chart:PolarLineSeries>

{% endhighlight %}

{% highlight c# %}
        
PolarLineSeries series = new PolarLineSeries();
series.ShowDataLabels = true;
series.DataLabelSettings = new PolarDataLabelSettings() {Context = LabelContext.Percentage };
...

{% endhighlight %}

{% endtabs %}

| Context values | Description |
|---|--|
| DataLabelItem | Displays the y value|
| Percentage | Displays the percentage value of series point among other points|
| XValue | Displays the X value of series point|
| YValue | Displays the Y value of series point|


## Data label customization

The following properties are used to customize the data label.

* [`BorderBrush`]()- used to change the border color.
* [`BorderThickness`]()- used to change the thickness of the border.
* [`Margin`]()- used to change the margin of the label.
* [`FontStyle`]()-  used to change font style of the label.
* [`FontSize`]()-  used to change font size of the label.
* [`Foreground`]()- used to change the text color of the label.
* [`FontFamily`]()-  used to change the font family of the label.
* [`Background`]()- used to change the label background color.

The following code example demonstrates the customization of data label using the above properties:

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.DataLabelSettings>
    <chart:PolarDataLabelSettings Foreground="White" FontSize="16" FontFamily="Calibri" BorderBrush="White" BorderThickness="1" Margin="1" FontStyle="Italic" Background="#1E88E5" />
</chart:SfPolarChart.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}

...
PolarLineSeries series = new PolarLineSeries();
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
    FontSize = 16
};


{% endhighlight %}

{% endtabs %}


## Label Template

The appearance of the data label can be customized by using [`ContentTemplate`]() property of [`PolarDataLabelSettings`]() as follows.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart >
    <chart:SfPolarChart.Resources>
        <DataTemplate x:Key="datalabelTemplate">
            <StackPanel Margin="10" Orientation="Vertical">
                <Ellipse Height="15" Width="15" Fill="{Binding Interior}" 
                 Stroke="#4a4a4a" StrokeThickness="2"/>
                <TextBlock HorizontalAlignment="Center" FontSize="12"
                           Foreground="Black" 
                           FontWeight="SemiBold" Text="{Binding Item.Product}"/>
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

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
...
PolarLineSeries series = new PolarLineSeries();
series.ShowDataLabels = true;

series.DataLabelSettings = new PolarDataLabelSettings() 
{ 
    Position = CircularSeriesLabelPosition.Outside,
    Context = LabelContext.DataLabelItem,
    ContentTemplate = chart.Resources["datalabelTemplate"] as DataTemplate,
};
...

{% endhighlight %}

{% endtabs %}



## Label format

The [Format]() property can be used to format the data labels. The following code example demonstrates the how to format data labels with three decimal digits.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart x:Name="chart">
...
    <chart:PolarLineSeries ShowDataLabels="True">
        <chart:PolarLineSeries.DataLabelSettings>
            <chart:PolarDataLabelSettings Format="#.0"/>
    </chart:PolarLineSeries.DataLabelSettings>

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


## Label rotation

The [`Rotation`]() property is used to rotate the data labels based on the value as angle.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart x:Name="chart">
...
    <chart:PolarLineSeries ShowDataLabels="True">
        <chart:PolarLineSeries.DataLabelSettings>
            <chart:PolarDataLabelSettings Rotation="45" BorderBrush="White" BorderThickness="1" Background="#1E88E5"/>
    </chart:PolarLineSeries.DataLabelSettings>

</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
. . . 
PolarLineSeries series = new PolarLineSeries();
series.ShowDataLabels = true;

series.DataLabelSettings = new PolarDataLabelSettings() 
{ 
    Rotation = 45,
    BorderBrush = new SolidColorBrush(Colors.White),
    Background = "#1E88E5",
    BorderThickness = new Thickness(1)
};
...

{% endhighlight %}

{% endtabs %}

## Applying Series Brush

[`UseSeriesPalette`]() property is used to set the interior of the series to the data label background. 

{% tabs %}

{% highlight xaml %}

<chart:PolarLineSeries.DataLabelSettings>
    <chart:PolarDataLabelSettings UseSeriesPalette="True"/>
</chart:PolarLineSeries.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}

series.DataLabelSettings = new CircularDataLabelSettings()
{
    UseSeriesPalette = true,
};

{% endhighlight %}

{% endtabs %}


