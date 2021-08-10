---
layout: post
title: Legend in WinUI Chart control | Syncfusion
description: This sections explains about how to configure the legend and its features title, icons, labels, and template in WinUI Chart (SfFunnelChart).
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Legend in WinUI Chart (SfFunnelChart)

The legend contains a list of series data points in the chart. The information provided in each legend item helps you to identify the corresponding data series in the chart.

N> The x-value of data points in the funnel chart will be the legend items ‘Label’.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart">
. . .
    <chart:SfFunnelChart.Legend>
        <chart:ChartLegend/>
    </chart:SfFunnelChart.Legend>
. . .
 </chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.Legend = new ChartLegend();
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Legend support in WinUI Chart](Legend_images/winui-chart_legend.png)

## Title

The funnel chart provides support to add any `UIElement` as a title for legend. [Header](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_Header) property of [ChartLegend](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html) is used to define the title for the legend as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart">
. . .
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
. . .
</chart:SfFunnelChart>

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
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Legend title in WinUI Chart](Legend_images/winui-chart_Legend_header.png)

## Icon

The legend icon represents a symbol associated with each legend item. The appearance of the legend icon can be customized using the following properties:

* [IconWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_IconWidth) - Gets or sets the double value that represents the legend icon(s) width.
* [IconHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_IconHeight) - Gets or sets the double value that represents the legend icon(s) height.
* [IconVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_IconVisibility) - Gets or sets the visibility of the legend icon.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart">
. . .
    <chart:SfFunnelChart.Legend>
        <chart:ChartLegend IconWidth="15" IconHeight="15" 
                       IconVisibility="Visible">
        </chart:ChartLegend>
    </chart:SfFunnelChart.Legend>
. . .
</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.Legend = new ChartLegend()
{
    IconWidth = 15,
    IconHeight = 15,
    IconVisibility = Visibility.Visible,
};
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Legend icon in WinUI Chart](Legend_images/winui-chart_Legend_customize.png)

## Item spacing

[ItemMargin](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_ItemMargin) property of the [ChartLegend](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html) is used to provide spacing between each legend items.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart">
. . .
    <chart:SfFunnelChart.Legend>
        <chart:ChartLegend ItemMargin="10"/>
    </chart:SfFunnelChart.Legend>
. . .
</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.Legend = new ChartLegend()
{
    ItemMargin = new Thickness(10)
};
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Legend item spacing support in WinUI Chart](Legend_images/winui-chart_legend_item_spacing.png)

## Checkbox for Legend

Funnel chart provides support to enable the checkbox for each legend item to visible or collapse the associated data points. By default, the value of [CheckBoxVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_CheckBoxVisibility) property is `Collapsed`. 

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart">
. . .
    <chart:SfFunnelChart.Legend>
        <chart:ChartLegend CheckBoxVisibility="Visible"/>
    </chart:SfFunnelChart.Legend>
. . .
</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.Legend = new ChartLegend()
{
   CheckBoxVisibility = Visibility.Visible
};
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Checkbox support for legend in WinUI Chart](Legend_images/winui-chart_Legend_checkbox.png)

## Toggle Series Visibility 

By enabling the [ToggleSeriesVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_ToggleSeriesVisibility) property, the visibility of the segment can be controlled by tapping the legend item. By default, the value of [ToggleSeriesVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_ToggleSeriesVisibility) property is `False`.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart">
. . .
    <chart:SfFunnelChart.Legend>
        <chart:ChartLegend ToggleSeriesVisibility="True"/>
    </chart:SfFunnelChart.Legend>
. . .
</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.Legend = new ChartLegend()
{
   ToggleSeriesVisibility = true
};
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![ToggleSeriesVisibility support for legend in WinUI Chart](Legend_images/winui-chart_legend_toggle-series-visibility.png)

## Position

The legends can be placed either inside or outside of the chart area (plotting area). By default, it will be displayed outside and positioned at top (using [Position](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_Position)) of the chart area.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart">
. . .
    <chart:SfFunnelChart.Legend>
        <chart:ChartLegend Position="Inside"/>
    </chart:SfFunnelChart.Legend>
. . .
</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.Legend = new ChartLegend()
{
    Position = LegendPosition.Inside
};
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Position support for legend in WinUI Chart](Legend_images/winui-chart_legend_position.png)

### Docking the Legend Position

By using the [DockPosition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_DockPosition) property, legends can be docked to the left, right, and top or bottom of the chart area. By default, the chart legend is docked at the top of the chart as mentioned earlier.

To display the legend at the right, you can set the [DockPosition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_DockPosition) as [Right](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartDock.html#Syncfusion_UI_Xaml_Charts_ChartDock_Right) as shown in the following code sample.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart">
. . .
    <chart:SfFunnelChart.Legend>
        <chart:ChartLegend ItemMargin="10" DockPosition="Right"/>
    </chart:SfFunnelChart.Legend>
. . .
</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.Legend = new ChartLegend()
{
   DockPosition = ChartDock.Right,
   ItemMargin = new Thickness(10),
};
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Positioning the legend at right in WinUI Chart](Legend_images/winui-chart_Legend_dock_right.png)

## Floating Legends

To position the legend at any arbitrary location within the chart, you need to set [DockPosition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_DockPosition) as `Floating` and provide its relative position by using the [OffsetX](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_OffsetX) and [OffsetY](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_OffsetY) properties.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart">
. . .
    <chart:SfFunnelChart.Legend>
        <chart:ChartLegend DockPosition="Floating" Orientation="Vertical" OffsetX="370" OffsetY="300"/>
    </chart:SfFunnelChart.Legend>
. . .
</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.Legend = new ChartLegend()
{
    DockPosition = ChartDock.Floating,
    Orientation = ChartOrientation.Vertical,
    OffsetX = 370,
    OffsetY = 300
};
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Floating legend support in WinUI Chart](Legend_images/winui-chart_legend_floating.png)

## Orientation

Orientation of the legend items can be aligned vertically or horizontally by setting the [Orientation](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_Orientation) property of legend. By default, the value of [Orientation](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_Orientation) property is [Horizontal](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartOrientation.html#Syncfusion_UI_Xaml_Charts_ChartOrientation_Horizontal).

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart">
. . .
    <chart:SfFunnelChart.Legend>
        <chart:ChartLegend Orientation="Vertical"/>
    </chart:SfFunnelChart.Legend>
. . .
</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.Legend = new ChartLegend()
{
    Orientation = ChartOrientation.Vertical
};
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Legend orientation support in WinUI Chart](Legend_images/winui-chart_legend_orientation.png)

## Background customization 

The legend background appearance can be customized by using the following properties:

`BorderThickness` - used to change the stroke width of the legend.
`BorderBrush` - used to change the stroke color of the legend.
`Background` - used to change the background color of the legend.
`Opacity` - used to control the transparency of the legend icon shape.
`CornerRadius` - used to change the corner radius of the legend.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart">
. . .
    <chart:SfFunnelChart.Legend>
        <chart:ChartLegend Background="Gray" BorderBrush="Black" BorderThickness="1" CornerRadius="5" Opacity="0.9" >
    </chart:ChartLegend>
    </chart:SfFunnelChart.Legend>
. . .
</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.Legend = new ChartLegend()
{
    Background = new SolidColorBrush(Colors.Gray),
    BorderBrush = new SolidColorBrush(Colors.Black),
    BorderThickness = new Thickness(1),
    Opacity = 0.9,
    CornerRadius = CornerRadiusHelper.FromUniformRadius(5)
};
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

## Template

Customize each legend item by using the `ItemTemplate` property in [ChartLegend](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html), as shown in the following code sample.

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

SfFunnelChart chart = new SfFunnelChart();
chart.Legend = new ChartLegend()
{

   ItemTemplate = chart.Resources["itemTemplate"] as DataTemplate
};
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Legend ItemTemplate support in WinUI Chart](Legend_images/winui-chart_legend_item_customizing.png)
