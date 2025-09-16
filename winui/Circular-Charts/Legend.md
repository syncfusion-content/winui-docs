---
layout: post
title: Legend in WinUI Chart control | WinUI | Syncfusion
description: This sections explains how to configure the legend and its features title, icons, labels, and template in WinUI Chart (SfCircularChart).
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Legend in WinUI Charts (SfCircularChart)

The legend contains a list of series data points in the chart. Each legend item helps to identify the corresponding data series in the chart.

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

N> The x-values of data points in the circular chart serve as the legend items' labels.

![Legend support in WinUI Pie Chart](Legend_Images/WinUI_pie_chart_legend.png)

## Title

The circular chart supports adding any `UIElement` as a title for the legend. The [Header](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_Header) property of [ChartLegend](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html) is used to define the title for the legend as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Legend>
        <chart:ChartLegend>
            <chart:ChartLegend.Header>
                <TextBlock Text="Products" 
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

![Legend header in WinUI Pie Chart](Legend_Images/WinUI_pie_chart_legend_title.png)

## Icon

A legend icon represents a symbol associated with each legend item. The [LegendIcon](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeries.html#Syncfusion_UI_Xaml_Charts_ChartSeries_LegendIcon) property of the series is used to set the icon type for legend items. By default, the legend icon is the [SeriesType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegendIcon.html#Syncfusion_UI_Xaml_Charts_ChartLegendIcon_SeriesType).

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
series.LegendIcon = ChartLegendIcon.Rectangle;

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Legend icon in WinUI Pie Chart](Legend_Images/WinUI_pie_chart_legend_icon.png)

The appearance of the legend icon can be customized using the following properties:

- [IconWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_IconWidth) - Specifies the width of the legend icon.
- [IconHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_IconHeight) - Specifies the height of the legend icon.
- [IconVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_IconVisibility) - Specifies the visibility of the legend icon.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
<chart:SfCircularChart.Legend>
    <chart:ChartLegend IconWidth="10" 
					   IconHeight="5" 
                       IconVisibility="Visible">
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
};

{% endhighlight %}

{% endtabs %}

**Custom Legend Icon**

The circular chart provides support for adding a custom icon to the legend using the [LegendIconTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeries.html#Syncfusion_UI_Xaml_Charts_ChartSeries_LegendIconTemplate) property of the series, as in the following example:

{% tabs %}

{% highlight xaml %}

<Grid x:Name="grid">
    <Grid.Resources>
        <DataTemplate x:Key="iconTemplate">
            <Ellipse Height="15"
					 Width="15"
					 Fill="White" 
					 Stroke="#4a4a4a" 
					 StrokeThickness="2"/>
        </DataTemplate>
    </Grid.Resources>
<chart:SfCircularChart>
    <chart:SfCircularChart.Legend>
        <chart:ChartLegend IconWidth="15"
						   IconHeight="15"/>
    </chart:SfCircularChart.Legend>

    <chart:PieSeries LegendIconTemplate="{StaticResource iconTemplate}"
                     ItemsSource="{Binding Data}"/>
</chart:SfCircularChart>
</Grid>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();
series.LegendIconTemplate = grid.Resources["iconTemplate"] as DataTemplate;
. . .
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Customizing legend icons in WinUI Pie Chart](Legend_Images/WinUI_pie_chart_legend_custom_icon.png)

## Item Spacing

The [ItemMargin](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_ItemMargin) property of the [ChartLegend](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html) is used to provide spacing between each legend item.

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

![Legend item spacing support in WinUI Pie Chart](Legend_Images/WinUI_pie_chart_legend_item_spacing.png)

## Checkbox for Legend

The circular chart supports enabling a checkbox for each legend item to toggle the visibility of the associated data points. By default, the value of the [CheckBoxVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_CheckBoxVisibility) property is `Collapsed`. 

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

![Checkbox support for legend in WinUI Pie Chart](Legend_Images/WinUI_pie_chart_legend_checkbox.png)

A data point can be collapsed by unchecking the checkbox:

![Checkbox support for legend in WinUI Pie Chart](Legend_Images/WinUI_pie_chart_legend_checkbox_uncheck.png)

## Toggle Series Visibility 

The visibility of segments can be controlled by tapping the legend item when the [ToggleSeriesVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_ToggleSeriesVisibility) property is enabled. By default, this property is set to `False`.

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

![ToggleSeriesVisibility support for legend in WinUI Pie Chart](Legend_Images/WinUI_pie_chart_legend_item_toggle.png)

## Placement

Legends can be docked on the left, right, top, or bottom of the chart area using the [Placement](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_Placement) property. By default, the chart legend is docked at the top of the chart.

To display the legend on the left, set the [Placement](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_Placement) property to [Left](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.LegendPlacement.html#Syncfusion_UI_Xaml_Charts_LegendPlacement_Left) as shown in the following code sample.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
<chart:SfCircularChart.Legend>
    <chart:ChartLegend ItemMargin="10"
					   Placement="Left"/>
</chart:SfCircularChart.Legend>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
chart.Legend = new ChartLegend()
{
    ItemMargin = new Thickness(10),
    Placement = LegendPlacement.Left
};

{% endhighlight %}

{% endtabs %}

![Positioning the legend at left in WinUI Pie Chart](Legend_Images/WinUI_pie_chart_legend_dock_left.png)

## Background Customization 

The legend's background appearance can be customized using the following properties:

- [`BorderThickness`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_BorderThickness) - Changes the stroke width of the legend.
- [`BorderBrush`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_BorderBrush) - Changes the stroke color of the legend.
- [`Background`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_Background) - Changes the background color of the legend.
- [`CornerRadius`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_CornerRadius) - Changes the corner radius of the legend.

{% tabs %}

{% highlight xaml %}
<chart:SfCircularChart>
. . .
<chart:SfCircularChart.Legend>
    <chart:ChartLegend Background="Gray"
					   BorderBrush="Black" 
					   BorderThickness="1" 
                       CornerRadius="5" >
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
    CornerRadius = new CornerRadius(5)
};

{% endhighlight %}

{% endtabs %}

## Template

Customize each legend item by using the [ItemTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html#Syncfusion_UI_Xaml_Charts_ChartLegend_ItemTemplate) property in [ChartLegend](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartLegend.html), as shown in the code snippet below:

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
<chart:SfCircularChart>
    . . .
    <chart:SfCircularChart.Legend>
        <chart:ChartLegend ItemTemplate="{StaticResource labelTemplate}"/>
    </chart:SfCircularChart.Legend>

</chart:SfCircularChart>
</Grid>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
chart.Legend = new ChartLegend()
{

   ItemTemplate = grid.Resources["itemTemplate"] as DataTemplate
};

{% endhighlight %}

{% endtabs %}

![Item template support for legend in WinUI Pie Chart](Legend_Images/WinUI_pie_chart_legend_template.png)

