---
layout: post
title: Legend in WinUI Chart Control | Syncfusion
description: This section explains how to configure the legend and its features, such as title, icons, labels, and template in WinUI Chart (SfPolarChart).
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Legend in WinUI Chart (SfPolarChart)

The legend contains a list of series in the chart. The information provided in each legend item helps identify the corresponding series in the chart.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    ...
    <chart:SfPolarChart.Legend>
        <chart:ChartLegend/>
    </chart:SfPolarChart.Legend>
    
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.Legend = new ChartLegend();
...

{% endhighlight %}

{% endtabs %}

![Legend support in WinUI Chart](Legend_images/WinUI_Chart_Legend.png)

## Title

The polar chart provides support to add any `UIElement` as a title for the legend. The [Header](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_Header) property of [ChartLegend](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html) is used to define the title for the legend.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    <chart:SfPolarChart.Legend>
        <chart:ChartLegend>
            <chart:ChartLegend.Header>
                <TextBlock Text="Plant Details" 
                           HorizontalAlignment="Center"
                           FontWeight="Bold"
                           Foreground="Blue"/>
            </chart:ChartLegend.Header>
        </chart:ChartLegend>
    </chart:SfPolarChart.Legend>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
ChartLegend legend = new ChartLegend();

TextBlock textBlock = new TextBlock()
{
    Text = "Plant Details",
    HorizontalTextAlignment = TextAlignment.Center,
    Foreground = new SolidColorBrush(Colors.Blue),
    FontWeight = FontWeights.Bold,
};

legend.Header = textBlock;
chart.Legend = legend;
...

{% endhighlight %}

{% endtabs %}

![Legend title in WinUI Chart](Legend_images/WinUI_Chart_chart_Legend_Header.png)

## Icon

The legend icon represents a symbol associated with each legend item. The appearance of the legend icon can be customized using the following properties:
* [IconWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_IconWidth) - Gets or sets the double value that represents the legend icon's width.
* [IconHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_IconHeight) - Gets or sets the double value that represents the legend icon's height.
* [IconVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_IconVisibility) - Gets or sets the visibility of the legend icon.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    <chart:SfPolarChart.Legend>
        <chart:ChartLegend IconWidth="15"
			   IconHeight="15" 
			   IconVisibility="Visible">
        </chart:ChartLegend>
    </chart:SfPolarChart.Legend>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.Legend = new ChartLegend()
{
    IconWidth = 15,
    IconHeight = 15,
    IconVisibility = Visibility.Visible,
};
...

{% endhighlight %}

{% endtabs %}

![Legend icon in WinUI Chart](Legend_images/WinUI_Chart_chart_Legend_Customize.png)

## Item Spacing

The [ItemMargin](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_ItemMargin) property of the [ChartLegend](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html) is used to provide spacing between each legend item.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    <chart:SfPolarChart.Legend>
        <chart:ChartLegend ItemMargin="10"/>
    </chart:SfPolarChart.Legend>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.Legend = new ChartLegend()
{
    ItemMargin = new Thickness(10)
};
...

{% endhighlight %}

{% endtabs %}

![Legend item spacing support in WinUI Chart](Legend_images/WinUI_Chart_Legend_item_spacing.png)

## Checkbox for Legend

The polar chart provides support to enable the checkbox for each legend item to show or hide the corresponding series. By default, the value of [CheckBoxVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_CheckBoxVisibility) property is `Collapsed`.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    <chart:SfPolarChart.Legend>
        <chart:ChartLegend CheckBoxVisibility="Visible"/>
    </chart:SfPolarChart.Legend>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.Legend = new ChartLegend()
{
   CheckBoxVisibility = Visibility.Visible
};
...

{% endhighlight %}

{% endtabs %}

![Checkbox support for legend in WinUI Chart](Legend_images/WinUI_Chart_Legend_CheckBox.png)

## Toggle Series Visibility

By enabling the [ToggleSeriesVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_ToggleSeriesVisibility) property, the visibility of the series can be controlled by tapping the legend item. By default, the value of [ToggleSeriesVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_ToggleSeriesVisibility) property is `False`.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    <chart:SfPolarChart.Legend>
        <chart:ChartLegend ToggleSeriesVisibility="True"/>
    </chart:SfPolarChart.Legend>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();

chart.Legend = new ChartLegend()
{
   ToggleSeriesVisibility = true
};
...

{% endhighlight %}

{% endtabs %}

![ToggleSeriesVisibility support for legend in WinUI Chart](Legend_images/WinUI_Chart_Legend_ToggleSeriesVisibility.png)

# Placement

By using the [Placement](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_Placement) property, legends can be docked to the left, right, top, or bottom of the chart area. By default, the chart legend is docked at the top of the chart.

To display the legend on the right, set the [Placement](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_Placement) to [Right](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.LegendPlacement.html#Syncfusion_UI_Xaml_Charts_LegendPlacement_Right) as in the following code sample.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    <chart:SfPolarChart.Legend>
        <chart:ChartLegend ItemMargin="10" Placement="Right"/>
    </chart:SfPolarChart.Legend>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.Legend = new ChartLegend()
{
   Placement = LegendPlacement.Right,
   ItemMargin = new Thickness(10),
};
...

{% endhighlight %}

{% endtabs %}

![Positioning the legend at right in WinUI Chart](Legend_images/WinUI_Chart_Legend_Dock_Right.png)

## Background Customization

The legend's background appearance can be customized using the following properties:
* [BorderThickness](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_BorderThickness) - used to change the stroke width of the legend.
* [BorderBrush](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_BorderBrush) - used to change the stroke color of the legend.
* [Background](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_Background) - used to change the background color of the legend.
* [CornerRadius](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_CornerRadius) - used to change the corner radius of the legend.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    <chart:SfPolarChart.Legend>
        <chart:ChartLegend Background="LightGray"
                           BorderBrush="Black" 
                           BorderThickness="1" 
                           CornerRadius="5">
        </chart:ChartLegend>
    </chart:SfPolarChart.Legend>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.Legend = new ChartLegend()
{
    Background = new SolidColorBrush(Colors.LightGray),
    BorderBrush = new SolidColorBrush(Colors.Black),
    BorderThickness = new Thickness(1),
    CornerRadius = new CornerRadius(5)
};
...

{% endhighlight %}

{% endtabs %}

## Template

Customize each legend item by using the [ItemTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_ItemTemplate) property in [ChartLegend](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html), as shown in the following code sample.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart x:Name="chart">
    <chart:SfPolarChart.Resources>
        <DataTemplate x:Key="labelTemplate">
            <StackPanel Margin="10" Orientation="Vertical">
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
    </chart:SfPolarChart.Resources>
    ...
    <chart:SfPolarChart.Legend>
        <chart:ChartLegend ItemTemplate="{StaticResource labelTemplate}"/>
    </chart:SfPolarChart.Legend>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.Legend = new ChartLegend()
{
   ItemTemplate = chart.Resources["labelTemplate"] as DataTemplate
};
...

{% endhighlight %}

{% endtabs %}

![Legend ItemTemplate support in WinUI Chart](Legend_images/WinUI_Chart_Legend_Item_customizing.png)

