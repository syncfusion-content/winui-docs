---
layout: post
title: Legend in WinUI Chart control | Syncfusion
description: This sections explains about how to configure the legend and its features title, icons, labels, and template in WinUI Chart control.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Legend in WinUI Chart (SfCartesianChart)

The legend contains a list of series data points in the chart. The information provided in each legend item helps you to identify the corresponding series in the chart. This allows us to specify the `Label` for each series which is to be displayed in legend label.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.Legend>
        <chart:ChartLegend/>
    </chart:SfCartesianChart.Legend>

    <chart:SplineSeries  Label="Spline"
                         ItemsSource="{Binding Data}" 
                         XBindingPath="Year"
                         YBindingPath="India">
    </chart:SplineSeries>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
ChartLegend legend = new ChartLegend();
chart.Legend = legend;

SplineSeries series = new SplineSeries();
series.ItemsSource = (new ViewModel()).Data;
series.XBindingPath = "Year";
series.YBindingPath = "India";
series.Label = "Spline";
chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Legend support in WinUI Chart](Legend_images/WinUI_chart_legend.png)

## Title

Cartesian chart provides support to add any `UIElement` as a title for legend. [Header]() property of `ChartLegend` is used to define the title for legend as the following code example.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.Legend>
        <chart:ChartLegend>
            <chart:ChartLegend.Header>
                <TextBox Text="Foods" 
                HorizontalAlignment="Center"
                FontWeight="Bold"
                Foreground="Blue"/>
            </chart:ChartLegend.Header>
        </chart:ChartLegend>
    </chart:SfCartesianChart.Legend>
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
ChartLegend legend = new ChartLegend();
. . .
TextBlock textBlock = new TextBlock()
{
    Text = "Foods",
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

![Legend title in WinUI Chart](Legend_images/WinUI_chart_legend_header.png)

## Icon

Legend icon represents a symbol associated with the each legend item. `LegendIcon` property of series is used to set the icon type for legend item. By default, the legend icon is [`SeriesType`]().

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.Legend>
        <chart:ChartLegend/>
    </chart:SfCartesianChart.Legend>

    <chart:SplineSeries  LegendIcon="Circle"
                         Label="Gold"
                         ItemsSource="{Binding Data}" 
                         XBindingPath="Year"
                         YBindingPath="India">
    </chart:SplineSeries>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
ChartLegend legend = new ChartLegend();
chart.Legend = legend;

SplineSeries series = new SplineSeries();
series.ItemsSource = (new ViewModel()).Data;
series.XBindingPath = "Year";
series.YBindingPath = "India";
series.Label = "Gold";
series.LegendIcon = ChartLegendIcon.Circle;
chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Legend icon in WinUI Chart](Legend_images/WinUI_chart_legend_icon.png)

The appearance of the legend icon can be customized using the below properties.

* [IconWidth]() - Gets or sets the double value that represents the legend icon(s) width.
* [IconHeight]() - Gets or sets the double value that represents the legend icon(s) height.
* [IconVisibility]() - Gets or sets the visibility of the legend icon.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Legend>
    <chart:ChartLegend IconWidth="15" IconHeight="15" 
                       IconVisibility="Visible">
    </chart:ChartLegend>
</chart:SfCartesianChart.Legend>

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

![Legend icon in WinUI Chart](Legend_images/WinUI_chart_legend_customize.png)

### Custom Icon

Cartesian chart provides support to add custom icon for the legend using [LegendIconTemplate]() property of series as in below example.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart >
     <chart:SfCartesianChart.Resources>
        <DataTemplate x:Key="iconTemplate">
            <Ellipse Height="10" Width="10" Fill="White" 
                     Stroke="#4a4a4a" StrokeThickness="2"/>
        </DataTemplate>
    </chart:SfCartesianChart.Resources>
    . . .   
    <chart:SfCartesianChart.Legend>
        <chart:ChartLegend />
    </chart:SfCartesianChart.Legend>
    . . .
    <chart:SfCartesianChart.Series>
        <chart:ColumnSeries  ItemsSource="{Binding Data}" Label="Gold" LegendIconTemplate="{StaticResource iconTemplate}" XBindingPath="Year" YBindingPath="India"/>
    </chart:SfCartesianChart.Series>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
chart.Legend = new ChartLegend();
. . .
ColumnSeries series = new ColumnSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Year",
    YBindingPath = "India",
    IconTemplate = chart.Resources["iconTemplate"] as DataTemplate
    Label = "Gold";
};

chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Custom legend icon in WinUI Chart](Legend_images/WinUI_chart_custom_legend_icon.png)

## Icon Visibility

The [VisibilityOnLegend]() property of series is used to enable/disable the visibility of legend icon as shown in below example.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart >
   . . .  
    <chart:SfCartesianChart.Legend>
        <chart:ChartLegend />
    </chart:SfCartesianChart.Legend>

    <chart:SfCartesianChart.Series>
        <chart:ColumnSeries  ItemsSource="{Binding Data}" Label="Gold" VisibilityOnLegend="Visible"
        XBindingPath="Year" YBindingPath="India"/>

        <chart:SplineSeries  ItemsSource="{Binding Data}" Label="Silver" VisibilityOnLegend="Collapsed"
        XBindingPath="Year" YBindingPath="America"/>
    </chart:SfCartesianChart.Series>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
 . . .
chart.Legend = new ChartLegend();

ColumnSeries columnSeries = new ColumnSeries()
{
    Label = "Gold",
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Year",
    YBindingPath = "India",
    VisibilityOnLegend = Visibility.Visible
};
SplineSeries splineSeries = new SplineSeries()
{
    Label = "Silver",
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Year",
    YBindingPath = "America",
    VisibilityOnLegend = Visibility.Collapsed
};

chart.Series.Add(splineSeries);
chart.Series.Add(columnSeries);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Legend icon visibility support in WinUI Chart](Legend_images/WinUI_chart_series_icon_visibility.png)

## Item spacing

[ItemMargin]() property of the `ChartLegend` is used to provide spacing between each legend items.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Legend>
    <chart:ChartLegend ItemMargin="10"/>
</chart:SfCartesianChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
    ItemMargin = new Thickness(10)
};

{% endhighlight %}

{% endtabs %}

![Legend item spacing support in WinUI Chart](Legend_images/WinUI_chart_legend_item_spacing.png)

## Checkbox for Legend

Cartesian chart provides support to enable the checkbox for each legend item to visible or collapse the associated series. By default, the value of [CheckBoxVisibility]() property is `Collapsed`. 

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Legend>
    <chart:ChartLegend CheckBoxVisibility="Visible"/>
</chart:SfCartesianChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
   CheckBoxVisibility = Visibility.Visible
};

{% endhighlight %}

{% endtabs %}

![Checkbox support for legend in WinUI Chart](Legend_images/WinUI_chart_legend_checkBox.png)

The series can be collapsed by unchecking the checkbox as below:

![Checkbox support for legend in WinUI Chart](Legend_images/WinUI_chart_legend_checkBox_uncheck.png)

## Toggle Series Visibility 

The visibility of the series can be control by tapping the legend item by enabling the [ToggleSeriesVisibility]() property. By default, the value of [ToggleSeriesVisibility]() property is `False`.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Legend>
    <chart:ChartLegend ToggleSeriesVisibility="True"/>
</chart:SfCartesianChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
   ToggleSeriesVisibility = true
};

{% endhighlight %}

{% endtabs %}

![ToggleSeriesVisibility support for legend in WinUI Chart](Legend_images/WinUI_chart_legend_toggleSeriesVisibility.png)

By clicking on disabled legend item, we can view the associated `series`, 

![ToggleSeriesVisibility support for legend in WinUI Chart](Legend_images/WinUI_chart_legend_toggleSeriesVisibility1.png)

## Position

The legends can be placed either inside or outside of the chart area (plotting area). By default, it will be displayed outside and positioned at top (using [DockPosition]()) of the chart area.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Legend>
    <chart:ChartLegend Position="Inside"/>
</chart:SfCartesianChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
    Position = LegendPosition.Inside
};

{% endhighlight %}

{% endtabs %}

![Positioning support for legend in WinUI Chart](Legend_images/WinUI_chart_legend_position.png)

### Docking the Legend Position

By using the [DockPosition]() property, legends can be docked to the left, right, and top or bottom of the chart area. By default, the chart legend is docked at the top of the chart as mentioned earlier.

To display the legend at the bottom, you can set the [DockPosition]() as [Bottom]() as shown in the following code sample.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Legend>
    <chart:ChartLegend DockPosition="Bottom"/>
</chart:SfCartesianChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
   DockPosition = ChartDock.Bottom
};

{% endhighlight %}

{% endtabs %}

![Positioning the legend at right in WinUI Chart](Legend_images/WinUI_chart_legend_dockPosition.png)

### Floating Legends

To position the legend at any arbitrary location within the chart, you need to set [DockPosition]() as `Floating` and provide its relative position by using the [OffsetX]() and [OffsetY]() properties.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Legend>
    <chart:ChartLegend DockPosition="Floating" Orientation="Vertical" OffsetX="30" OffsetY="45" ItemMargin="3"/>
</chart:SfCartesianChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
    DockPosition = ChartDock.Floating,
    Orientation = ChartOrientation.Vertical,
    OffsetX = 30,
    OffsetY = 45,
    ItemMargin = new Thickness(3)
};

{% endhighlight %}

{% endtabs %}

![Floating legend support in WinUI Chart](Legend_images/WinUI_chart_legend_floating.png)

## Orientation

Orientation of the legend items can be aligned vertically or horizontally by setting the [Orientation]() property of legend. By default, the value of [Orientation]() property is [Horizontal]().

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Legend>
    <chart:ChartLegend Orientation="Vertical"/>
</chart:SfCartesianChart.Legend>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
    Orientation = ChartOrientation.Vertical
};

{% endhighlight %}

{% endtabs %}

![Legend orientation support in WinUI Chart](Legend_images/WinUI_chart_legend_orientation.png)

## Background customization 

The legend background appearance can be customized by using the following properties:

[BorderThickness]() - used to change the stroke width of the legend.
[BorderBrush]() - used to change the stroke color of the legend.
[Background]() - used to change the background color of the legend.
[Opacity]() - used to control the transparency of the legend icon shape.
[CornerRadius]() - used to change the corner radius of the legend.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Legend>
    <chart:ChartLegend Background="LightGray" BorderBrush="Black" 
                       BorderThickness="1" CornerRadius="5" 
                       Opacity="0.9" >
    </chart:ChartLegend>
</chart:SfCartesianChart.Legend>

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

{% endhighlight %}

{% endtabs %}

## Template

Customize each legend item by using the [ItemTemplate]() property in `ChartLegend`, as shown in the following code sample.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.Resources>
        <DataTemplate x:Key="labelTemplate">
            <StackPanel Margin="10" Orientation="Vertical">
                <Ellipse Height="15" Width="15" Fill="{Binding Interior}" 
                 Stroke="#4a4a4a" StrokeThickness="2"/>
                <TextBlock HorizontalAlignment="Center" FontSize="12"
                           Foreground="Black" 
                           FontWeight="SemiBold" Text="{Binding Label}"/>
            </StackPanel>
        </DataTemplate>
    </chart:SfCartesianChart.Resources>
    . . .
    <chart:SfCartesianChart.Legend>
        <chart:ChartLegend ItemTemplate="{StaticResource labelTemplate}"/>
    </chart:SfCartesianChart.Legend>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

chart.Legend = new ChartLegend()
{
   ItemTemplate = chart.Resources["itemTemplate"] as DataTemplate
};

{% endhighlight %}

{% endtabs %}

![Legend ItemTemplate support in WinUI Chart](Legend_images/WinUI_chart_legend_itemTemplate.png)
