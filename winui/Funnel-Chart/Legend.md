---
layout: post
title: Legend in  WinUI Funnel Chart control | Syncfusion
description: How to configure the chart legend and customize the appearance of the legend title, Icons, labels, and ItemTemplate in WinUI Funnel Chart (SfFunnelChart)
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Legend in WinUI Funnel Chart (SfFunnelChart)

The legend contains list of chart series/data points in chart. The information provided in each legend item helps to identify the corresponding data series in chart.

The following code example shows how to enable legend in chart.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart.Legend>
    <chart:ChartLegend/>
</chart:SfFunnelChart.Legend>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.Legend = new ChartLegend();

{% endhighlight %}

{% endtabs %}

N> Legend items ‘Label’ will be the x value of the Funnel chart.

![Legend support in WinUI Funnel Chart](Legend_images/WinUI_Funnel_chart_Legend.png)

## Legend Header

FunnelChart provides support to add any UIElement as a header for legend items. 

Define the [Header]() for legend using the following code example.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart.Legend>
    <chart:ChartLegend>
        <chart:ChartLegend.Header>
            <TextBox Text="Products" 
                HorizontalAlignment="Center"
                FontWeight="Bold"
                Foreground="Blue"/>
        </chart:ChartLegend.Header>
    </chart:ChartLegend>
</chart:SfFunnelChart.Legend>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
ChartLegend legend = new ChartLegend();

TextBlock textBlock = new TextBlock()
{
    Text = "Products",
    HorizontalTextAlignment = TextAlignment.Center,
    Foreground = new SolidColorBrush(Colors.Blue),
    FontWeight = FontWeights.Bold,
};

legend.Header = textBlock;
chart.Legend = legend;

{% endhighlight %}

{% endtabs %}

![Legend header in WinUI Circular Chart](Legend_images/WinUI_Funnel_chart_Legend_Header.png)

## Legend Icon

FunnelSeries is used to define the label for the corresponding series legend item and for FunnelSeries type chart by default values mapped with xValueMapper will be displayed. The appearance of the label can be customized using the below properties.

* [IconWidth]() - Gets or sets the double value that represents the legend icon(s) width.
* [IconHeight]() - Gets or sets the double value that represents that legend icon(s) height.
* [IconVisibility]() - Gets or sets the Visibility of the legend icon.
* [ItemMargin]() - Gets or sets the margin for the legend items.
* [CornerRadius]() - Gets or sets the corner radius of the legend.

The following code example illustrates the customization of legend.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart.Legend>
    <chart:ChartLegend IconWidth="15" IconHeight="15" 
                       IconVisibility="Visible"
                       BorderBrush="Blue" 
                       BorderThickness="2"
                       ItemMargin="5" 
                       CornerRadius="5"
                       Margin="5">
    </chart:ChartLegend>
</chart:SfFunnelChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
    IconWidth = 15,
    IconHeight = 15,
    IconVisibility = Visibility.Visible,
    BorderBrush = new SolidColorBrush(Colors.Blue),
    BorderThickness = new Thickness(2),
    ItemMargin = new Thickness(5),
    CornerRadius = new CornerRadius(5),
    Margin = new Thickness(5)
};

{% endhighlight %}

{% endtabs %}

![Legend customization in WinUI Funnel Chart](Legend_images/WinUI_Funnel_chart_Legend_Customize.png)


## Checkbox for legend

Used to view or collapse the associated data points. By default, the [CheckBoxVisibility]() is `Collapsed`. 

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart.Legend>
    <chart:ChartLegend CheckBoxVisibility="Visible"/>
</chart:SfFunnelChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
   CheckBoxVisibility = Visibility.Visible
};

{% endhighlight %}

{% endtabs %}

![Checkbox support for legend in WinUI Funnel Chart](Legend_images/WinUI_Funnel_chart_Legend_CheckBox.png)


## ToggleSeriesVisibility 

You can control the visibility of the series by tapping the legend item. You can enable this feature by enabling the [ToggleSeriesVisibility]() property. By default, [ToggleSeriesVisibility]() property is `False`.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart.Legend>
    <chart:ChartLegend ToggleSeriesVisibility="True"/>
</chart:SfFunnelChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
   ToggleSeriesVisibility = true
};

{% endhighlight %}

{% endtabs %}

The data point can be collapsed and view it again, by clicking on the respective legend item,

![ToggleSeriesVisibility support for legend in WinUI Funnel Chart](Legend_images/WinUI_Funnel_chart_Legend_ToggleSeriesVisibility.png)

## Positioning the Legend

**Legend Position**

The legends can be placed either [Inside]() or [Outside]() of the chart area (plotting area).
By default, it will be displayed outside and positioned at top (using [DockPosition]()) of the chart area.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart.Legend>
    <chart:ChartLegend Position="Inside"/>
</chart:SfFunnelChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
    Position = LegendPosition.Inside
};

{% endhighlight %}

{% endtabs %}

**Docking**

Legends can be docked left, right, and top or bottom around the chart area using [DockPosition]() property. 
By default, the ChartLegend is docked at the top of the chart as mentioned earlier.

To display the legend at the bottom, you can set the [DockPosition]() as [Right]() as in below code snippet.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart.Legend>
    <chart:ChartLegend ItemMargin="10" DockPosition="Right"/>
</chart:SfFunnelChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
   DockPosition = ChartDock.Right
};

{% endhighlight %}

{% endtabs %}

![Positioning the legend at left in WinUI Circular Chart](Legend_images/WinUI_Funnel_chart_Legend_Dock_Right.png)


**Floating Legends**

To position the legend at any arbitrary location inside chart, need to set [DockPosition]() as `Floating` and provide its relative position using [OffsetX]() and [OffsetY]() properties.
 
Offset specifies x or y distance from origin.

{% tabs %}

{% highlight xaml %}

 <chart:SfFunnelChart.Legend>
    <chart:ChartLegend DockPosition="Floating" Orientation="Vertical" OffsetX="370" OffsetY="300"/>
</chart:SfFunnelChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
    DockPosition = ChartDock.Floating,
    OffsetX = 370,
    OffsetY = 300
};

{% endhighlight %}

{% endtabs %}

![Positioning the legend at floating in WinUI Funnel Chart](Legend_images/WinUI_Funnel_chart_Legend_floating.png)

## Legend Orientation

Orientation of the Legend can be vertical or horizontal. By default the [Orientation]() is [Horizontal](). 

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart.Legend>
    <chart:ChartLegend Orientation="Vertical"/>
</chart:SfFunnelChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
    Orientation = ChartOrientation.Vertical
};

{% endhighlight %}

{% endtabs %}

![Legend orientation support in WinUI Funnel Chart](Legend_images/WinUI_Funnel_chart_Legend_Orientation.png)


## Customization

**ItemTemplate**

Customize each legend item using [ItemTemplate]() property in ChartLegend as in below code snippet:

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart>
    <chart:SfFunnelChart.Resources>
        <DataTemplate x:Key="labelTemplate">
            <StackPanel Margin="10" Orientation="Vertical">
                <Ellipse Height="15" Width="15" Fill="{Binding Interior}" 
                 Stroke="#4a4a4a" StrokeThickness="2"/>
                <TextBlock HorizontalAlignment="Center" FontSize="12"
                           Foreground="Black" 
                           FontWeight="SemiBold" Text="{Binding Label}"/>
            </StackPanel>
        </DataTemplate>
    </chart:SfFunnelChart.Resources>
    . . .
    <chart:SfFunnelChart.Legend>
        <chart:ChartLegend ItemTemplate="{StaticResource labelTemplate}"/>
    </chart:SfFunnelChart.Legend>

</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{

   ItemTemplate = chart.Resources["itemTemplate"] as DataTemplate
};

{% endhighlight %}

{% endtabs %}

![Item template support for legend in WinUI Funnel Chart](Legend_images/WinUI_Funnel_chart_Legend_Item_customizing.png)

