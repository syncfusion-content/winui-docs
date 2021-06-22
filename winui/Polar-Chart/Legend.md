---
layout: post
title: Legend in WinUI Polar Chart control | Syncfusion
description: This sections explains about how to configure the legend and its features title, icons, labels, and template in WinUI Polar Chart (SfPolarChart).
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Legend in WinUI Polar Chart (SfPolarChart)

The legend contains list of series in the chart. The information provided in each legend item helps to identify the corresponding series in the chart.

The following code example shows how to enable legend in the chart.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.Legend>
    <chart:ChartLegend/>
</chart:SfPolarChart.Legend>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.Legend = new ChartLegend();

{% endhighlight %}

{% endtabs %}

![Legend support in WinUI Polar Chart](Legend_images/WinUI_PolarChart_Legend.png)

## Legend title

Polar chart provides support to add any `UIElement` as a title for legend. [Header]() property of `ChartLegend` is used to define the title for the legend as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.Legend>
    <chart:ChartLegend>
        <chart:ChartLegend.Header>
            <TextBox Text="Plant Details" 
                HorizontalAlignment="Center"
                FontWeight="Bold"
                Foreground="Blue"/>
        </chart:ChartLegend.Header>
    </chart:ChartLegend>
</chart:SfPolarChart.Legend>

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

{% endhighlight %}

{% endtabs %}

![Legend title in WinUI Polar Chart](Legend_images/WinUI_PolarChart_chart_Legend_Header.png)

## Legend icon

The legend icon represents a symbol associated with each legend item. The appearance of the legend icon can be customized using the following properties:

* [IconWidth]() - Gets or sets the double value that represents the legend icon(s) width.
* [IconHeight]() - Gets or sets the double value that represents that legend icon(s) height.
* [IconVisibility]() - Gets or sets the visibility of the legend icon.

The following code example illustrates the customization of legend icon.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.Legend>
    <chart:ChartLegend IconWidth="15" IconHeight="15" 
                       IconVisibility="Visible">
    </chart:ChartLegend>
</chart:SfPolarChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
    IconWidth = 15,
    IconHeight = 15,
    IconVisibility = Visibility.Visible,
};

{% endhighlight %}

{% endtabs %}

![Legend icon in WinUI Polar Chart](Legend_images/WinUI_PolarChart_chart_Legend_Customize.png)

## Legend item spacing

`ItemMargin` property of the `ChartLegend` is used to provide spacing between each legend items.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.Legend>
    <chart:ChartLegend ItemMargin="10"/>
</chart:SfPolarChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
    ItemMargin = new Thickness(10)
};

{% endhighlight %}

{% endtabs %}

![Legend item spacing support in WinUI Polar Chart](Legend_images/WinUI_PolarChart_Legend_item_spacing.png)

## Checkbox for legend

Polar chart provides support to enable the checkbox for each legend item to visible or collapse the corresponding series. By default, the value of [CheckBoxVisibility]() property is `Collapsed`. 

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.Legend>
    <chart:ChartLegend CheckBoxVisibility="Visible"/>
</chart:SfPolarChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
   CheckBoxVisibility = Visibility.Visible
};

{% endhighlight %}

{% endtabs %}

![Checkbox support for legend in WinUI Polar Chart](Legend_images/WinUI_PolarChart_Legend_CheckBox.png)

## Toggle series visibility 

By enabling the [ToggleSeriesVisibility]() property, the visibility of the series can be controlled by tapping the legend item. By default, the value of [ToggleSeriesVisibility]() property is `False`.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.Legend>
    <chart:ChartLegend ToggleSeriesVisibility="True"/>
</chart:SfPolarChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
   ToggleSeriesVisibility = true
};

{% endhighlight %}

{% endtabs %}

![ToggleSeriesVisibility support for legend in WinUI Polar Chart](Legend_images/WinUI_PolarChart_Legend_ToggleSeriesVisibility.png)

## Positioning the legend

The legends can be placed either inside or outside of the chart area (plotting area). By default, it will be displayed outside and positioned at top (using [DockPosition]()) of the chart area.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.Legend>
    <chart:ChartLegend Position="Inside"/>
</chart:SfPolarChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
    Position = LegendPosition.Inside
};

{% endhighlight %}

{% endtabs %}

![Position support for legend in WinUI Polar Chart](Legend_images/WinUI_PolarChart_Legend_Position.png)

**Docking the legend position**

By using the [DockPosition]() property, legends can be docked to the left, right, and top or bottom of the chart area. By default, the chart legend is docked at the top of the chart as mentioned earlier.

To display the legend at the right, you can set the [DockPosition]() as [Right]() as in below code snippet.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.Legend>
    <chart:ChartLegend ItemMargin="10" DockPosition="Right"/>
</chart:SfPolarChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
   DockPosition = ChartDock.Right,
   ItemMargin = new Thickness(10),
};

{% endhighlight %}

{% endtabs %}

![Positioning the legend at right in WinUI Polar Chart](Legend_images/WinUI_PolarChart_Legend_Dock_Right.png)

**Floating legends**

To position the legend at any arbitrary location within the chart, you need to set [DockPosition]() as `Floating` and provide its relative position by using the [OffsetX]() and [OffsetY]() properties.

{% tabs %}

{% highlight xaml %}

 <chart:SfPolarChart.Legend>
    <chart:ChartLegend DockPosition="Floating" Orientation="Vertical" OffsetX="330" OffsetY="180"/>
</chart:SfPolarChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
    DockPosition = ChartDock.Floating,
    Orientation = ChartOrientation.Vertical,
    OffsetX = 330,
    OffsetY = 180
};

{% endhighlight %}

{% endtabs %}

![Floating legend support in WinUI Polar Chart](Legend_images/WinUI_PolarChart_Legend_floating.png)

## Legend Orientation

Orientation of the legend items can aligned vertically or horizontally by setting [`Orientation`]() property of legend. By default, the value of [Orientation]() property is [Horizontal](). 

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.Legend>
    <chart:ChartLegend Orientation="Vertical"/>
</chart:SfPolarChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
    Orientation = ChartOrientation.Vertical
};

{% endhighlight %}

{% endtabs %}

![Legend orientation support in WinUI Polar Chart](Legend_images/WinUI_PolarChart_Legend_Orientation.png)

## Legend background customization 

The legend background appearance can be customized by using the following properties:

[BorderThickness]() - used to change the stroke width of the legend.
[BorderBrush]() - used to change the stroke color of the legend.
[Background]() - used to change the background color of legend.
[Opacity]() - used to control the transparency of the legend icon shape.
[CornerRadius]() - used to change the corner radius of the legend.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.Legend>
    <chart:ChartLegend Background="LightGray" BorderBrush="Black" 
                       BorderThickness="1" CornerRadius="5" 
                       Opacity="0.9">
    </chart:ChartLegend>
</chart:SfPolarChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
    Background = new SolidColorBrush(Colors.LightGray),
    BorderBrush = new SolidColorBrush(Colors.Black),
    BorderThickness = new Thickness(1),
    Opacity = 0.9,
    CornerRadius = CornerRadiusHelper.FromUniformRadius(5)
};

{% endtabs %}

![Legend background customization in WinUI Polar Chart](Legend_images/WinUI_PolarChart_Legend_background_customizing.png)

## Legend template customization

Customize each legend item by using the [ItemTemplate]() property in `ChartLegend`, as shown in the following code sample.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    <chart:SfPolarChart.Resources>
        <DataTemplate x:Key="labelTemplate">
            <StackPanel Margin="10" Orientation="Vertical">
                <Ellipse Height="15" Width="15" Fill="{Binding Interior}" 
                 Stroke="#4a4a4a" StrokeThickness="2"/>
                <TextBlock HorizontalAlignment="Center" FontSize="12"
                           Foreground="Black" 
                           FontWeight="SemiBold" Text="{Binding Label}"/>
            </StackPanel>
        </DataTemplate>
    </chart:SfPolarChart.Resources>
    . . .
    <chart:SfPolarChart.Legend>
        <chart:ChartLegend ItemTemplate="{StaticResource labelTemplate}"/>
    </chart:SfPolarChart.Legend>

</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
   ItemTemplate = chart.Resources["itemTemplate"] as DataTemplate
};

{% endhighlight %}

{% endtabs %}

![Legend ItemTemplate support in WinUI Polar Chart](Legend_images/WinUI_PolarChart_Legend_Item_customizing.png)

