---
layout: post
title: Legend in WinUI Chart control | WinUI | Syncfusion
description: This sections explains about how to configure the legend and its features title, icons, labels, and template in WinUI Chart (SfCircularChart).
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Legend in WinUI Charts (SfCircularChart)

The legend contains list of series data points in the chart. The information provided in each legend item helps to identify the corresponding data series in the chart.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart.Legend>
    <chart:ChartLegend/>
</chart:SfCircularChart.Legend>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
chart.Legend = new ChartLegend();

{% endhighlight %}

{% endtabs %}

N> The x-value of data points in the circular chart will be the legend items ‘Label’.

![Legend support in WinUI Pie Chart](Legend_images/WinUI_Circular_chart_Legend.png)

## Title

Circular chart provides support to add any `UIElement` as a title for legend. [Header]() property of `ChartLegend` is used to define the title for legend as the following code example.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Legend>
        <chart:ChartLegend>
            <chart:ChartLegend.Header>
                <TextBox Text="Products" 
                         HorizontalAlignment="Center"
                         FontWeight="Bold"
                         Foreground="Blue"/>
            </chart:ChartLegend.Header>
    </chart:ChartLegend>
</chart:SfCircularChart.Legend>
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
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

![Legend header in WinUI Pie Chart](Legend_images/WinUI_Circular_chart_Legend_Header.png)

## Icon

Legend icon represents a symbol associated with the each legend item. `LegendIcon` property of series is used to set the icon type for legend item. By default, the legend icon is [`SeriesType`]().

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
<chart:SfCircularChart.Legend>
    <chart:ChartLegend/>
</chart:SfCircularChart.Legend>


<chart:SfCircularChart.Series>
    <chart:PieSeries LegendIcon="Rectangle"
                     ItemsSource="{Binding Data}"  
                     XBindingPath="Product" 
                     YBindingPath="SalesRate">
    </chart:PieSeries>
</chart:SfCircularChart.Series>
. . .
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}


SfCircularChart chart = new SfCircularChart();
. . .
chart.Legend = new ChartLegend();

PieSeries series = new PieSeries();
series.LegendIcon = ChartLegendIcon.Circle;

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Legend icon in WinUI Pie Chart](Legend_images/WinUI_Circular_chart_Legend_LegendIcon.png)

The appearance of the legend icon can be customized using the below properties.

* [IconWidth]() - Gets or sets the double value that represents the legend icon(s) width.
* [IconHeight]() - Gets or sets the double value that represents that legend icon(s) height.
* [IconVisibility]() - Gets or sets the Visibility of the legend icon.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
<chart:SfCircularChart.Legend>
    <chart:ChartLegend IconWidth="10" IconHeight="5" 
                       IconVisibility="Visible"
                       BorderBrush="Blue" 
                       BorderThickness="1"
                       ItemMargin="5" 
                       CornerRadius="5">
    </chart:ChartLegend>
</chart:SfCircularChart.Legend>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
chart.Legend = new ChartLegend()
{
    IconWidth = 10,
    IconHeight = 5,
    IconVisibility = Visibility.Visible,
    BorderBrush = new SolidColorBrush(Colors.Blue),
    BorderThickness = new Thickness(1),
    ItemMargin = new Thickness(5),
    CornerRadius = new CornerRadius(5)
};

{% endhighlight %}

{% endtabs %}

![Legend customization in WinUI Pie Chart](Legend_images/WinUI_Circular_chart_Legend_Customize.png)

**Custom legend icon**

Circular chart provides support to add custom icon for the legend using [LegendIconTemplate]() property of series as in below example.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
    <chart:SfCircularChart.Resources>
        <DataTemplate x:Key="iconTemplate">
            <Ellipse Height="15" Width="15" Fill="White" 
                 Stroke="#4a4a4a" StrokeThickness="2"/>
        </DataTemplate>
    </chart:SfCircularChart.Resources>

    <chart:SfCircularChart.Legend>
        <chart:ChartLegend IconWidth="15" IconHeight="15"/>
    </chart:SfCircularChart.Legend>
    
    <chart:PieSeries 
        LegendIconTemplate="{StaticResource iconTemplate}"
        ItemsSource="{Binding Data}"/>
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();
series.LegendIconTemplate = chart.Resources["iconTemplate"] as DataTemplate;
. . .
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Customizing legend icons in WinUI Pie Chart](Legend_images/WinUI_Circular_chart_Custom_Icon.png)

## Item spacing

`ItemMargin` property of the `ChartLegend` is used to provide spacing between each legend items.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
<chart:SfCircularChart.Legend>
    <chart:ChartLegend ItemMargin="10"/>
</chart:SfCircularChart.Legend>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
chart.Legend = new ChartLegend()
{
    ItemMargin = new Thickness(10)
};

{% endhighlight %}

{% endtabs %}

![Legend item spacing support in WinUI Pie Chart](Legend_images/WinUI_Circular_chart_Legend_Icon_spacing.png)

## Checkbox for Legend

Circular chart provides support to enable the checkbox for each legend item to visible or collapse the associated data points. By default, the value of [CheckBoxVisibility]() property is `Collapsed`.  

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Legend>
        <chart:ChartLegend CheckBoxVisibility="Visible"/>
    </chart:SfCircularChart.Legend>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
chart.Legend = new ChartLegend()
{
   CheckBoxVisibility = Visibility.Visible
};

{% endhighlight %}

{% endtabs %}

![Checkbox support for legend in WinUI Pie Chart](Legend_images/WinUI_Circular_chart_Legend_CheckBox.png)

The data point can be collapsed by unchecking the checkbox as below:

![Checkbox support for legend in WinUI Pie Chart](Legend_images/WinUI_Circular_chart_Legend_LegendIcon_collapsed.png)

## Toggle Series Visibility 

The visibility of the segment can be control by tapping the legend item by enabling the [ToggleSeriesVisibility]() property. By default, the value of [ToggleSeriesVisibility]() property is `False`.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Legend>
        <chart:ChartLegend ToggleSeriesVisibility="True"/>
    </chart:SfCircularChart.Legend>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
chart.Legend = new ChartLegend()
{
   ToggleSeriesVisibility = true
};

{% endhighlight %}

{% endtabs %}

![ToggleSeriesVisibility support for legend in WinUI Pie Chart](Legend_images/WinUI_Circular_chart_Legend_ToggleSeriesVisibility.png)

## Position

The legends can be placed either inside or outside of the chart area (plotting area). By default, it will be displayed outside and positioned at top (using [DockPosition]()) of the chart area.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Legend>
        <chart:ChartLegend Position="Inside"/>
    </chart:SfCircularChart.Legend>
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
chart.Legend = new ChartLegend()
{
    Position = LegendPosition.Inside
};

{% endhighlight %}

{% endtabs %}

**Docking**

Legends can be docked left, right, and top or bottom around the chart area using [DockPosition]() property. By default, the chart legend is docked at the top of the chart as mentioned earlier.

To display the legend at the left, set the [DockPosition]() as [Left]() as in below code snippet.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
<chart:SfCircularChart.Legend>
    <chart:ChartLegend ItemMargin="10" DockPosition="Left"/>
</chart:SfCircularChart.Legend>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
chart.Legend = new ChartLegend()
{
   DockPosition = ChartDock.Left
};

{% endhighlight %}

{% endtabs %}

![Positioning the legend at left in WinUI Pie Chart](Legend_images/WinUI_Circular_chart_Legend_Dock_Left.png)

**Floating legends**

To position the legend at any arbitrary location inside chart, need to set [DockPosition]() as `Floating` and provide its relative position by using [OffsetX]() and [OffsetY]() properties.
 
Offset specifies x or y distance from origin.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Legend>
        <chart:ChartLegend DockPosition="Floating" OffsetX="330" OffsetY="160"/>
    </chart:SfCircularChart.Legend>
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
chart.Legend = new ChartLegend()
{
    DockPosition = ChartDock.Floating,
    OffsetX = 330,
    OffsetY = 160
};

{% endhighlight %}

{% endtabs %}

![Positioning the legend at floating in WinUI Pie Chart](Legend_images/WinUI_Circular_chart_Legend_floating.png)

## Orientation

Orientation of the legend items can aligned vertically or horizontally by setting [`Orientation`]() property of legend. By default, the value of [Orientation]() property is [Horizontal](). 

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Legend>
        <chart:ChartLegend Orientation="Vertical"/>
    </chart:SfCircularChart.Legend>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
chart.Legend = new ChartLegend()
{
    Orientation = ChartOrientation.Vertical
};

{% endhighlight %}

{% endtabs %}

![Legend orientation support in WinUI Pie Chart](Legend_images/WinUI_Circular_chart_Legend_Orientation.png)

## Background Customization 

The legend background appearance can be customized by using the below properties.

[BorderThickness]() - used to change the stroke width of the legend.
[BorderBrush]() - used to change the stroke color of the legend.
[Background]() - used to change the background color of legend.
[Opacity]() - used to control the transparency of the legend icon shape.
[CornerRadius]() - used to change the corner radius of the legend.

{% tabs %}

{% highlight xaml %}
<chart:SfCircularChart>
. . .
<chart:SfCircularChart.Legend>
    <chart:ChartLegend Background="Gray" BorderBrush="Black" 
                       BorderThickness="1" CornerRadius="5" 
                       Opacity="0.9" >
    </chart:ChartLegend>
</chart:SfCircularChart.Legend>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
chart.Legend = new ChartLegend()
{
    Background = new SolidColorBrush(Colors.Gray),
    BorderBrush = new SolidColorBrush(Colors.Black),
    BorderThickness = new Thickness(1),
    Opacity = 0.9,
    CornerRadius = CornerRadiusHelper.FromUniformRadius(5)
};

{% endhighlight %}

{% endtabs %}

![Legend background customization in WinUI Pie Chart](Legend_images/WinUI_Circular_chart_Legend_background_customizing.png)

## Template

Customize each legend item by using [ItemTemplate]() property in `ChartLegend` as in below code snippet:

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
    <chart:SfCircularChart.Resources>
        <DataTemplate x:Key="labelTemplate">
            <StackPanel Margin="10" Orientation="Vertical">
                <Ellipse Height="15" Width="15" Fill="{Binding Interior}" 
                 Stroke="#4a4a4a" StrokeThickness="2"/>
                <TextBlock HorizontalAlignment="Center" FontSize="12"
                           Foreground="Black" 
                           FontWeight="SemiBold" Text="{Binding Label}"/>
            </StackPanel>
        </DataTemplate>
    </chart:SfCircularChart.Resources>
    . . .
    <chart:SfCircularChart.Legend>
        <chart:ChartLegend ItemTemplate="{StaticResource labelTemplate}"/>
    </chart:SfCircularChart.Legend>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
chart.Legend = new ChartLegend()
{

   ItemTemplate = chart.Resources["itemTemplate"] as DataTemplate
};

{% endhighlight %}

{% endtabs %}

![Item template support for legend in WinUI Pie Chart](Legend_images/WinUI_Circular_chart_Legend_Item_customizing.png)

