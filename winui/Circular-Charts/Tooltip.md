---
layout: post
title: Tooltip in WinUI Chart control | Syncfusion
description: This section explains about how to enable tooltip and its customization in Syncfusion WinUI Chart (SfCircularChart) control
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Tooltip in WinUI Chart (SfCircularChart)

Tooltip is used to display any information over segments. It appears at center of the segment when the mouse hovers over any chart segment. It is set to display the metadata of the hovered segment or data point.

## Define Tooltip

To define the tooltip in the chart, set the [ShowTooltip]() property of series to true. The default value of [ShowTooltip]() property is false.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
    <chart:PieSeries ShowTooltip="True"
                     ItemsSource="{Binding Data}" 
                     ShowDataLabels="True" 
                     Palette="BlueChrome"
                     XBindingPath="Product" 
                     YBindingPath="SalesRate">
    </chart:PieSeries>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries() { Label = "Continents" };
series.ShowTooltip = true;
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Tooltip support in WinUI chart](Tooltip_Images/WinUI_pie_chart_tooltip.png)

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

<chart:SfCircularChart>
. . .
<chart:SfCircularChart.Behaviors>
    <chart:ChartTooltipBehavior/>
</chart:SfCircularChart.Behaviors>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
ChartTooltipBehavior tooltip = new ChartTooltipBehavior();
chart.Behaviors.Add(tooltip);

{% endhighlight %}

{% endtabs %}

## Background Style

The tooltip's fill and stroke color can be customized by using the [Style]() property. To define a [Style]() for tooltip, specify the style of `TargetType` as `Path`.

{% tabs %}

{% highlight xml %}

<chart:SfCircularChart>
. . .
<chart:SfCircularChart.Resources>
    <Style TargetType="Path" x:Key="style">
        <Setter Property="Stroke" Value="Black"/>
        <Setter Property="Fill" Value="Gray"/>
    </Style>
</chart:SfCircularChart.Resources>

<chart:SfCircularChart.Behaviors>
    <chart:ChartTooltipBehavior Style="{StaticResource style}"/>
</chart:SfCircularChart.Behaviors>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
Style style = new Style(typeof(Path));
style.Setters.Add(new Setter(Path.StrokeProperty, new SolidColorBrush(Colors.Black)));
style.Setters.Add(new Setter(Path.FillProperty, new SolidColorBrush(Colors.Gray)));
. . .
ChartTooltipBehavior tooltip = new ChartTooltipBehavior();
tooltip.Style = style;
. . . 
chart.Behaviors.Add(tooltip);

{% endhighlight %}

{% endtabs %}

![Tooltip background style in WinUI Chart](Tooltip_Images/WinUI_pie_chart_tooltip_background_customization.png)

## Label Style

The tooltip label style can be customized by using the [LabelStyle]() property. To define a [Style]() for the tooltip label, specify the style of `TargetType` as `TextBlock`.

{% tabs %}

{% highlight xml %}

<chart:SfCircularChart>
. . .
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

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
Style labelStyle = new Style(typeof(TextBlock));
labelStyle.Setters.Add(new Setter(TextBlock.FontSizeProperty, 14d));
labelStyle.Setters.Add(new Setter(TextBlock.FontStyleProperty, FontStyles.Italic));
labelStyle.Setters.Add(new Setter(TextBlock.ForegroundProperty, new SolidColorBrush(Colors.Red)));
...
ChartTooltipBehavior tooltip = new ChartTooltipBehavior();
tooltip.LabelStyle = labelStyle;
. . .
chart.Behaviors.Add(tooltip);

{% endhighlight %}

{% endtabs %}

![Tooltip label style in WinUI chart](Tooltip_Images/WinUI_pie_chart_tooltip_label_customization.png)

## Template

Circular chart provides support to customize the appearance of the tooltip by using the [`TooltipTemplate`]() property. 

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Resources>
        <DataTemplate x:Key="tooltipTemplate">
            <StackPanel Orientation="Horizontal">
                <TextBlock Text="{Binding Item.Product}" Foreground="Black" FontWeight="Medium" FontSize="12" HorizontalAlignment="Center" VerticalAlignment="Center"/>
                <TextBlock Text=" : " Foreground="Black" FontWeight="Medium" FontSize="12" HorizontalAlignment="Center" VerticalAlignment="Center"/>
                <TextBlock Text="{Binding Item.SalesRate}" Foreground="Black" FontWeight="Medium" FontSize="12" HorizontalAlignment="Center" VerticalAlignment="Center"/>
            </StackPanel>
        </DataTemplate>
    </chart:SfCircularChart.Resources>

    <chart:SfCircularChart.Series>
        <chart:PieSeries ShowTooltip="True"
                 ItemsSource="{Binding Data}" 
                 Palette="BlueChrome"
                 XBindingPath="Product" 
                 YBindingPath="SalesRate"
                 TooltipTemplate="{StaticResource tooltipTemplate}"/>
    </chart:SfCircularChart.Series>
    . . .
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();
series.ShowTooltip = true;
series.TooltipTemplate = chart.Resources["tooltipTemplate"] as DataTemplate;
. . .     
{% endhighlight %}

{% endtabs %}

![Tooltip template in WinUI Circular Chart](Tooltip_Images/WinUI_pie_chart_tooltip_template.png)

