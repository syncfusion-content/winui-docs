---
layout: post
title: Legend in WinUI Circular Chart control | WinUI | Syncfusion
description: How to configure the chart legend and customize the appearance of the legend title, Icons, labels, and ItemTemplate in WinUI Circular Chart (SfCircularChart)
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Legend in WinUI Circular Charts (SfCircularChart)

[Legend]() provides metadata which helps for identifying corresponding data points in chart. 

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

N> Legend items ‘Label’ will be the x value of the Circular chart.

![Legend support in WinUI Circular Chart](Legend_images/WinUI_Circular_chart_Legend.png)

## Legend Header

Chart provides support to add any UIElement as a header for legend items. 

Define the [Header]() for legend using the following code example.

{% tabs %}

{% highlight xaml %}

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

![Legend header in WinUI Circular Chart](Legend_images/WinUI_Circular_chart_Legend_Header.png)

## Legend Icon

Represents the symbol associated with each legend item. By default, the legend icon is [`SeriesType`](). This can be customized using the [`LegendIcon`]() property of series.

{% tabs %}

{% highlight xaml %}

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

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend();

PieSeries series = new PieSeries();
series.LegendIcon = ChartLegendIcon.Circle;

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Legend icon in WinUI Circular Chart](Legend_images/WinUI_Circular_chart_Legend_LegendIcon.png)

The following properties are used to customize the legend.

* [IconWidth]() - Gets or sets the double value that represents the legend icon(s) width.
* [IconHeight]() - Gets or sets the double value that represents that legend icon(s) height.
* [IconVisibility]() - Gets or sets the Visibility of the legend icon.
* [ItemMargin]() - Gets or sets the margin for the legend items.
* [CornerRadius]() - Gets or sets the corner radius of the legend.

The following code example illustrates the customization of legend.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart.Legend>
    <chart:ChartLegend IconWidth="10" IconHeight="5" 
                       IconVisibility="Visible"
                       BorderBrush="Blue" 
                       BorderThickness="1"
                       ItemMargin="5" 
                       CornerRadius="5">
    </chart:ChartLegend>
</chart:SfCircularChart.Legend>

{% endhighlight %}

{% highlight c# %}

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

![Legend customization in WinUI Circular Chart](Legend_images/WinUI_Circular_chart_Legend_Customize.png)

**Custom Legend Icon**

Can possible to add custom icon for the legend using [IconTemplate]() property of series as in below example.

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
        IconTemplate="{StaticResource iconTemplate}"
        ItemsSource="{Binding Data}"/>
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();
series.IconTemplate = chart.Resources["iconTemplate"] as DataTemplate;
. . .
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Customizing legend icons in WinUI Circular Chart](Legend_images/WinUI_Circular_chart_Custom_Icon.png)

## Checkbox for legend

Used to view or collapse the associated data points. By default, the [CheckBoxVisibility]() is `Collapsed`. 

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart.Legend>
    <chart:ChartLegend CheckBoxVisibility="Visible"/>
</chart:SfCircularChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
   CheckBoxVisibility = Visibility.Visible
};

{% endhighlight %}

{% endtabs %}

![Checkbox support for legend in WinUI Circular Chart](Legend_images/WinUI_Circular_chart_Legend_CheckBox.png)


The data point can be collapsed by unchecking the checkbox as below:

![Checkbox support for legend in WinUI Circular Chart](Legend_images/WinUI_Circular_chart_Legend_LegendIcon_collapsed.png)


## ToggleSeriesVisibility 

[ToggleSeriesVisibility]() is used to view or collapse the associated data point, by clicking on its legend item. By default, [ToggleSeriesVisibility]() property is `False`.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart.Legend>
    <chart:ChartLegend ToggleSeriesVisibility="True"/>
</chart:SfCircularChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
   ToggleSeriesVisibility = true
};

{% endhighlight %}

{% endtabs %}

The data point can be collapsed and view it again, by clicking on the respective legend item,

![ToggleSeriesVisibility support for legend in WinUI Circular Chart](Legend_images/WinUI_Circular_chart_Legend_ToggleSeriesVisibility.png)

## Positioning the Legend

**Legend Position**

This allows to position the legends [Inside]() or [Outside]() of the chart area (plotting area). 
By default, it will be displayed outside and positioned at top (using [DockPosition]()) of the chart area.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart.Legend>
    <chart:ChartLegend Position="Inside"/>
</chart:SfCircularChart.Legend>

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

To display the legend at the bottom, you can set the [DockPosition]() as [Left]() as in below code snippet.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart.Legend>
    <chart:ChartLegend ItemMargin="10" DockPosition="Left"/>
</chart:SfCircularChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
   DockPosition = ChartDock.Left
};

{% endhighlight %}

{% endtabs %}

![Positioning the legend at left in WinUI Circular Chart](Legend_images/WinUI_Circular_chart_Legend_Dock_Left.png)


**Floating Legends**

To position the legend at any arbitrary location inside chart, need to set [DockPosition]() as `Floating` and provide its relative position using [OffsetX]() and [OffsetY]() properties.
 
Offset specifies x or y distance from origin.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart.Legend>
    <chart:ChartLegend DockPosition="Floating" OffsetX="330" OffsetY="160"/>
</chart:SfCircularChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
    DockPosition = ChartDock.Floating,
    OffsetX = 330,
    OffsetY = 160
};

{% endhighlight %}

{% endtabs %}

![Positioning the legend at floating in WinUI Circular Chart](Legend_images/WinUI_Circular_chart_Legend_floating.png)

## Legend Orientation

Orientation of the Legend can be vertical or horizontal. By default the [Orientation]() is [Horizontal](). 

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart.Legend>
    <chart:ChartLegend Orientation="Vertical"/>
</chart:SfCircularChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
    Orientation = ChartOrientation.Vertical
};

{% endhighlight %}

{% endtabs %}

![Legend orientation support in WinUI Chart](Legend_images/WinUI_Circular_chart_Legend_Orientation.png)


## Customization

**ItemTemplate**

Customize each legend item using [ItemTemplate]() property in ChartLegend as in below code snippet:

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart x:Name="chart">

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

chart.Legend = new ChartLegend()
{

   ItemTemplate = chart.Resources["itemTemplate"] as DataTemplate
};

{% endhighlight %}

{% endtabs %}

![Item template support for legend in WinUI Circular Chart](Legend_images/WinUI_Circular_chart_Legend_Item_customizing.png)