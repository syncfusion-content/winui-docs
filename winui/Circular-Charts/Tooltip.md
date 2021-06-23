---
layout: post
title: Tooltip in WinUI Circular Chart control | Syncfusion
description: This section explains about how to enable tooltip and its customization in Syncfusion WinUI Circular Chart (SfCircularChart) control
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Tooltip in WinUI Circular Chart (SfCircularChart)

Tooltip is used to display any information over segments. It appears at center of the segment when the mouse hovers over any chart segment. It is set to display the metadata of the hovered segment or data point.

## Define tooltip

To define the tooltip in the chart, set the [ShowTooltip]() property of series to true. The default value of [ShowTooltip]() property is false.

{% tabs %}

{% highlight xaml %}

<chart:PieSeries ShowTooltip="True"
                 ItemsSource="{Binding Data}" 
                 ShowDataLabels="True" 
                 Palette="BlueChrome"
                 XBindingPath="Product" 
                 YBindingPath="SalesRate">

</chart:PieSeries>


{% endhighlight %}

{% highlight c# %}

PieSeries series = new PieSeries() { Label = "Continents" };
series.ShowTooltip = true;
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Tooltip support in WinUI Circular chart](Tooltip_images/WinUI_Circular_chart_Tooltip.png)

## Customization

The [ChartTooltipBehavior]() is used to customize the tooltip. For customizing the tooltip, create an instance [ChartTooltipBehavior]() and add it to the `Behaviors` collection of [SfCircularChart](). The following properties are used to customize the tooltip:

* [Style]() - Used to customize the fill and stroke of the tooltip.
* [LabelStyle]() - Used to customize the tooltip label.
* [HorizontalAlignment]() - Used to align the tooltip label at the left, right and center of the data point position or cursor position horizontally.
* [VerticalAlignment]() - Used to align the tooltip label at the top, center and bottom of the data point position or cursor position vertically.
* [HorizontalOffset]() - Used to position the tooltip at a distance from the data point or cursor position horizontally.
* [VerticalOffset]() - Used to position the tooltip at a distance from the data point or cursor position vertically.
* [ShowDuration]() - Used to set the amount of time that the tooltip remains visible in milliseconds.
* [EnableAnimation]() - Used to enable the animation when showing the tooltip.
* [InitialShowDelay]() - Used to delay the display of the tooltip in milliseconds after the user interacts with the series.

{% tabs %}

{% highlight xml %}

<chart:SfCircularChart.Behaviors>
    <chart:ChartTooltipBehavior/>
</chart:SfCircularChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();

ChartTooltipBehavior tooltip = new ChartTooltipBehavior();
chart.Behaviors.Add(tooltip);

{% endhighlight %}

{% endtabs %}

### Background style customization

The tooltip's fill and stroke color can be customized by using the [Style]() property. To define a [Style]() for tooltip, specify the style of `TargetType` as `Path`.

The following code example explains how to apply the style for tooltip background.

{% tabs %}

{% highlight xml %}

<chart:SfCircularChart.Resources>
    <Style TargetType="Path" x:Key="style">
        <Setter Property="Stroke" Value="Black"/>
        <Setter Property="Fill" Value="Gray"/>
    </Style>
</chart:SfCircularChart.Resources>

<chart:SfCircularChart.Behaviors>
    <chart:ChartTooltipBehavior Style="{StaticResource style}"/>
</chart:SfCircularChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
Style style = new Style(typeof(Path));
style.Setters.Add(new Setter(Path.StrokeProperty, new SolidColorBrush(Colors.Black)));
style.Setters.Add(new Setter(Path.FillProperty, new SolidColorBrush(Colors.Gray)));
. . .
ChartTooltipBehavior tooltip = new ChartTooltipBehavior();
tooltip.Style = style;
chart.Behaviors.Add(tooltip);

{% endhighlight %}

{% endtabs %}

![Tooltip background style customization in WinUI Circular chart](Tooltip_images/WinUI_Circular_chart_Tooltip_Customization.png)

### Label style customization

The tooltip label style can be customized by using the [LabelStyle]() property. To define a [Style]() for the tooltip label, specify the style of `TargetType` as `TextBlock`.

The following code example explains how to apply the style for a tooltip label.

{% tabs %}

{% highlight xml %}

<chart:SfCircularChart.Resources>
    <Style TargetType="TextBlock" x:Key="labelStyle">
        <Setter Property="FontSize" Value="14"/>
        <Setter Property="Foreground" Value="Red"/>
        <Setter Property="FontStyle" Value="Italic"/>
    </Style>
</chart:SfCircularChart.Resources>

<chart:SfCircularChart.Behaviors>
    <chart:ChartTooltipBehavior LabelStyle="{StaticResource labelStyle}"/>
</chart:SfCircularChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
Style labelStyle = new Style(typeof(TextBlock));
labelStyle.Setters.Add(new Setter(TextBlock.FontSizeProperty, 14d));
labelStyle.Setters.Add(new Setter(TextBlock.FontStyleProperty, FontStyles.Italic));
labelStyle.Setters.Add(new Setter(TextBlock.ForegroundProperty, new SolidColorBrush(Colors.Red)));
...
ChartTooltipBehavior tooltip = new ChartTooltipBehavior();
tooltip.LabelStyle = labelStyle;
chart.Behaviors.Add(tooltip);

{% endhighlight %}

{% endtabs %}

![Tooltip label style customization in WinUI Circular chart](Tooltip_images/WinUI_Circular_chart_Tooltip_LabelStyle_Customization.png)

### Tooltip alignment

The tooltip can be aligned with respect to the cursor position using the [`HorizontalAlignment`]() and [`VerticalAlignment`]() properties.

**HorizontalAlignment**

Tooltip can be positioned horizontally left, right, or center to cursor position. The following code example explains the positioning of tooltip to the left of the cursor.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart x:Name="chart" >

    <chart:SfCircularChart.Behaviors>
        <chart:ChartTooltipBehavior HorizontalAlignment="Left"/>
    </chart:SfCircularChart.Behaviors>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
ChartTooltipBehavior tooltip = new ChartTooltipBehavior();
tooltip.HorizontalAlignment = HorizontalAlignment.Left;
chart.Behaviors.Add(tooltip);

{% endhighlight %}

{% endtabs %}

**VerticalAlignment**

Tooltip can be positioned vertically top, bottom, or center to cursor position. The following code example explains the positioning of tooltip to the bottom of the cursor.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart x:Name="chart" >

    <chart:SfCircularChart.Behaviors>
        <chart:ChartTooltipBehavior VerticalAlignment="Bottom"/>
    </chart:SfCircularChart.Behaviors>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
ChartTooltipBehavior tooltip = new ChartTooltipBehavior();
tooltip.VerticalAlignment = VerticalAlignment.Bottom;
chart.Behaviors.Add(tooltip);

{% endhighlight %}

{% endtabs %}

### Tooltip offset

The tooltip can be positioned at a particular distance from the cursor by using the [HorizontalOffset]() and [VerticalOffset]() properties.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart x:Name="chart" >

        <chart:SfCircularChart.Behaviors>
            <chart:ChartTooltipBehavior HorizontalOffset="40" VerticalOffset="40"/>
        </chart:SfCircularChart.Behaviors>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
ChartTooltipBehavior tooltip = new ChartTooltipBehavior();
tooltip.HorizontalOffset = 40;
tooltip.VerticalOffset = 40;
chart.Behaviors.Add(tooltip);

{% endhighlight %}

{% endtabs %}

### Tooltip duration

The [ShowDuration]() property is used to specify the duration time in milliseconds for which tooltip will be displayed.

The following code example demonstrates the duration of the tooltip set as 5 seconds.

{% tabs %}

{% highlight xml %}

<chart:SfCircularChart x:Name="chart" >

    <chart:SfCircularChart.Behaviors>
        <chart:ChartTooltipBehavior ShowDuration="5000"/>
    </chart:SfCircularChart.Behaviors>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
ChartTooltipBehavior tooltip = new ChartTooltipBehavior();
tooltip.ShowDuration = 5000;
chart.Behaviors.Add(tooltip);

{% endhighlight %}

{% endtabs %}

N> By default, the tooltip will be displayed for 1000 milliseconds.

### Tooltip animation

Animation for tooltip can be set by using the [`EnableAnimation`]() property as shown in the following code sample.

{% tabs %}

{% highlight xml %}

<chart:SfCircularChart x:Name="chart">

    <chart:SfCircularChart.Behaviors>
        <chart:ChartTooltipBehavior EnableAnimation="True"/>
    </chart:SfCircularChart.Behaviors>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
ChartTooltipBehavior tooltip = new ChartTooltipBehavior();
tooltip.EnableAnimation = true;
chart.Behaviors.Add(tooltipBehavior);

{% endhighlight %}

{% endtabs %}

### Tooltip template

Circular chart provides support to customize the appearance of the tooltip by using the [`TooltipTemplate`]() property. 

The following code example explains how to display both x-value and y-value in tooltip using a template.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart.Resources>
    <DataTemplate x:Key="tooltipTemplate">
        <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding Item.Product}" Foreground="Black" FontWeight="Medium" FontSize="12" HorizontalAlignment="Center" VerticalAlignment="Center"/>
            <TextBlock Text=" : " Foreground="Black" FontWeight="Medium" FontSize="12" HorizontalAlignment="Center" VerticalAlignment="Center"/>
            <TextBlock Text="{Binding Item.SalesRate}" Foreground="Black" FontWeight="Medium" FontSize="12" HorizontalAlignment="Center" VerticalAlignment="Center"/>
        </StackPanel>
    </DataTemplate>
</chart:SfCircularChart.Resources>

<chart:SfCircularChart.Behaviors>
    <chart:ChartTooltipBehavior Style="{StaticResource style}"/>
</chart:SfCircularChart.Behaviors>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

PieSeries series = new PieSeries() { Label = "Continents" };
series.ShowTooltip = true;
series.TooltipTemplate = chart.Resources["tooltipTemplate"] as DataTemplate;
. . .     
{% endhighlight %}

{% endtabs %}

![Tooltip template in WinUI Circular Chart](Tooltip_images/WinUI_Circular_chart_Tooltip_Template_Customization.png)

