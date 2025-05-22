---
layout: post
title: Legend in WinUI Chart Control | Syncfusion
description: This section explains how to configure the legend and its features—title, icons, labels, and template—in the WinUI Chart (SfFunnelChart).
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Legend in WinUI Chart (SfFunnelChart)

The legend provides a list of series data points in the chart. Each legend item helps identify the corresponding data series in the chart.

N> The x-value of data points in the funnel chart will be the legend item 'Label'.

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

The funnel chart allows adding any `UIElement` as a title for the legend. The [Header](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_Header) property of [ChartLegend](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html) is used to define the legend's title, as shown in the following code example.

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

The legend icon represents a symbol associated with each legend item. Customize the appearance of the legend icon using the following properties:

* [IconWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_IconWidth) - Sets the width of the legend icon(s).
* [IconHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_IconHeight) - Sets the height of the legend icon(s).
* [IconVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_IconVisibility) - Sets the visibility of the legend icon.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart">
. . .
    <chart:SfFunnelChart.Legend>
        <chart:ChartLegend IconWidth="15" 
						   IconHeight="15" 
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

## Item Spacing

Use the [ItemMargin](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_ItemMargin) property of the [ChartLegend](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html) to provide spacing between legend items.

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

The funnel chart supports enabling a checkbox for each legend item to show or collapse the associated data points. By default, the [CheckBoxVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_CheckBoxVisibility) property is set to `Collapsed`.

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

Enable the [ToggleSeriesVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_ToggleSeriesVisibility) property to control the visibility of the segment by tapping the legend item. By default, this property is set to `False`.

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

## Placement

Utilize the [Placement](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_Placement) property to dock the legends to the left, right, top, or bottom of the chart area. By default, the chart legend is docked at the top. 

To display the legend on the right, set the [Placement](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_Placement) to [Right](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.LegendPlacement.html#Syncfusion_UI_Xaml_Charts_LegendPlacement_Right).

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart">
. . .
    <chart:SfFunnelChart.Legend>
        <chart:ChartLegend ItemMargin="10"
						   Placement="Right"/>
    </chart:SfFunnelChart.Legend>
. . .
</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.Legend = new ChartLegend()
{
   Placement = LegendPlacement.Right,
   ItemMargin = new Thickness(10),
};
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Positioning the legend at right in WinUI Chart](Legend_images/winui-chart_Legend_dock_right.png)

## Background Customization

Customize the legend's background appearance using the following properties:

- [BorderThickness](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_BorderThickness) - Changes the stroke width of the legend.
- [BorderBrush](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_BorderBrush) - Changes the stroke color of the legend.
- [Background](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_Background) - Changes the background color of the legend.
- [CornerRadius](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_CornerRadius) - Changes the corner radius of the legend.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart">
. . .
    <chart:SfFunnelChart.Legend>
        <chart:ChartLegend Background="Gray" 
						   BorderBrush="Black"
						   BorderThickness="1"
						   CornerRadius="5" >
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
    CornerRadius = new CornerRadius(5)
};
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

## Template

Customize each legend item using the [ItemTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_ItemTemplate) property in the [ChartLegend](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html), as shown in the following code sample.

{% tabs %}

{% highlight xaml %}

<Grid x:Name="grid">
    <Grid.Resources>
        <DataTemplate x:Key="labelTemplate">
            <StackPanel Margin="10"
						Orientation="Vertical">
                <Ellipse Height="15"
						 Width="15"
						 Fill="{Binding Interior}" 
						 Stroke="#4a4a4a"
						 StrokeThickness="2"/>
                <TextBlock HorizontalAlignment="Center"
						   FontSize="12"
                           Foreground="Black" 
                           FontWeight="SemiBold"
						   Text="{Binding Label}"/>
            </StackPanel>
        </DataTemplate>
    </Grid.Resources>
<chart:SfFunnelChart>
. . .
    <chart:SfFunnelChart.Legend>
        <chart:ChartLegend ItemTemplate="{StaticResource labelTemplate}"/>
    </chart:SfFunnelChart.Legend>

</chart:SfFunnelChart>
</Grid>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.Legend = new ChartLegend()
{

   ItemTemplate = grid.Resources["labelTemplate"] as DataTemplate
};
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Legend ItemTemplate support in WinUI Chart](Legend_images/winui-chart_legend_item_customizing.png)
