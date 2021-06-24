---
layout: post
title: Tooltip in WinUI Chart control | Syncfusion
description: This section explains about how to enable tooltip and its customization in Syncfusion WinUI Chart (SfPyramidChart) control.
platform: WinUI
control: SfPyramidChart
documentation: ug
---

# Tooltip in WinUI Chart (SfPyramidChart)

Tooltip is used to display any information over segments. It appears at the data point position when the mouse hovers over any chart segment. It is set to display the metadata of the hovered segment or data point.

## Define tooltip

To define the tooltip in the chart, set the [ShowTooltip]() property to true. The default value of [ShowTooltip]() property is false.

{% tabs %}

{% highlight xaml %}

<chart:SfPyramidChart x:Name="chart" 
                ShowTooltip="True"
                Palette="BlueChrome"
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">          

</chart:SfPyramidChart>

{% endhighlight %}

{% highlight c# %}

SfPyramidChart chart = new SfPyramidChart();
chart.Palette = ChartColorPalette.BlueChrome;
chart.SetBinding(SfPyramidChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.ShowTooltip = true;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Tooltip support in WinUI chart](Tooltip_images/WinUI_chart_tooltip.png)

The [ChartTooltipBehavior]() is used to customize the tooltip. For customizing the tooltip, create an instance [ChartTooltipBehavior]() and add it to the `Behaviors` collection of [`SfPyramidChart`](). The following properties are used to customize the tooltip:

* [Style]() - Used to customize the fill and stroke of the tooltip.
* [LabelStyle]() - Used to customize the tooltip label.
* [HorizontalAlignment]() - Used to align the tooltip label at the left, right, and center of the data point position or cursor position horizontally.
* [VerticalAlignment]() - Used to align the tooltip label at the top, center, and bottom of the data point position or cursor position vertically.
* [HorizontalOffset]() - Used to position the tooltip at a distance from the data point or cursor position horizontally.
* [VerticalOffset]() - Used to position the tooltip at a distance from the data point or cursor position vertically.
* [ShowDuration]() - Used to set the amount of time that the tooltip remains visible in milliseconds.
* [EnableAnimation]() - Used to enable the animation when showing the tooltip.
* [InitialShowDelay]() - Used to delay the display of the tooltip in milliseconds after the user interacts with the series.

{% tabs %}

{% highlight xml %}

<chart:SfPyramidChart.Behaviors>
    <chart:ChartTooltipBehavior/>
</chart:SfPyramidChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

SfPyramidChart chart = new SfPyramidChart();

ChartTooltipBehavior behavior = new ChartTooltipBehavior();

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}

## Background style

The tooltip's fill and stroke color can be customized by using the [Style]() property. To define a [Style]() for tooltip, specify the style of `TargetType` as `Path`.

The following code example explains how to apply the style for tooltip background.

{% tabs %}

{% highlight xml %}

<chart:SfPyramidChart x:Name="chart" 
                ShowTooltip="True">          
. . . 
    <chart:SfPyramidChart.Resources>
        <Style TargetType="Path" x:Key="style">
            <Setter Property="Stroke" Value="Black"/>
            <Setter Property="Fill" Value="Gray"/>
        </Style>
    </chart:SfPyramidChart.Resources>

    <chart:SfPyramidChart.Behaviors>
        <chart:ChartTooltipBehavior Style="{StaticResource style}"/>
    </chart:SfPyramidChart.Behaviors>
. . . 
</chart:SfPyramidChart>

{% endhighlight %}

{% highlight c# %}

SfPyramidChart chart = new SfPyramidChart();
chart.ShowTooltip = true;
Style style = new Style(typeof(Path));
style.Setters.Add(new Setter(Path.StrokeProperty, new SolidColorBrush(Colors.Black)));
style.Setters.Add(new Setter(Path.FillProperty, new SolidColorBrush(Colors.Gray)));
...
ChartTooltipBehavior tooltipBehavior = new ChartTooltipBehavior();
tooltipBehavior.Style = style;
chart.Behaviors.Add(tooltipBehavior);

{% endhighlight %}

{% endtabs %}

![Tooltip background style in WinUI chart](Tooltip_images/WinUI_chart_tooltip_background_style.png)

## Label style

The tooltip label style can be customized by using the [LabelStyle]() property. To define a [Style]() for the tooltip label, specify the style of `TargetType` as `TextBlock`.

The following code example explains how to apply the style for a tooltip label.

{% tabs %}

{% highlight xml %}

<chart:SfPyramidChart x:Name="chart" ShowTooltip="True">          
. . . 
    <chart:SfPyramidChart.Resources>
        <Style TargetType="TextBlock" x:Key="labelStyle">
            <Setter Property="FontSize" Value="14"/>
            <Setter Property="Foreground" Value="Red"/>
            <Setter Property="FontStyle" Value="Italic"/>
        </Style>
    </chart:SfPyramidChart.Resources>

    <chart:SfPyramidChart.Behaviors>
        <chart:ChartTooltipBehavior LabelStyle="{StaticResource labelStyle}"/>
    </chart:SfPyramidChart.Behaviors>
. . . 
</chart:SfPyramidChart>

{% endhighlight %}

{% highlight c# %}

SfPyramidChart chart = new SfPyramidChart();
Style labelStyle = new Style(typeof(TextBlock));
labelStyle.Setters.Add(new Setter(TextBlock.FontSizeProperty, 14d));
labelStyle.Setters.Add(new Setter(TextBlock.FontStyleProperty, FontStyles.Italic));
labelStyle.Setters.Add(new Setter(TextBlock.ForegroundProperty, new SolidColorBrush(Colors.Red)));
...
ChartTooltipBehavior tooltipBehavior = new ChartTooltipBehavior();
tooltipBehavior.LabelStyle = labelStyle;
chart.Behaviors.Add(tooltipBehavior);

{% endhighlight %}

{% endtabs %}

![Tooltip label style in WinUI chart](Tooltip_images/WinUI_chart_tooltip_label_style.png)

## Template

The pyramid chart provides support to customize the appearance of the tooltip by using the [`TooltipTemplate`]() property. 

{% tabs %}

{% highlight xaml %}

<chart:SfPyramidChart x:Name="chart" 
                ShowTooltip="True" 
                Palette="BlueChrome" TooltipTemplate="{StaticResource tooltipTemplate}"
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">

    <chart:SfPyramidChart.Resources>
        <DataTemplate x:Key="tooltipTemplate">
            <StackPanel Orientation="Horizontal">
                <TextBlock Text="{Binding Item.Category}" Foreground="Black" FontWeight="Medium" FontSize="12" HorizontalAlignment="Center" VerticalAlignment="Center"/>
                <TextBlock Text=" : " Foreground="Black" FontWeight="Medium" FontSize="12" HorizontalAlignment="Center" VerticalAlignment="Center"/>
                <TextBlock Text="{Binding Item.Value}" Foreground="Black" FontWeight="Medium" FontSize="12" HorizontalAlignment="Center" VerticalAlignment="Center"/>
            </StackPanel>
        </DataTemplate>

        <Style TargetType="Path" x:Key="style">
            <Setter Property="Stroke" Value="Black"/>
            <Setter Property="Fill" Value="LightGreen"/>
            <Setter Property="StrokeThickness" Value="2"/>
        </Style>
    </chart:SfPyramidChart.Resources>

    <chart:SfPyramidChart.Behaviors>
        <chart:ChartTooltipBehavior Style="{StaticResource style}"/>
    </chart:SfPyramidChart.Behaviors>

</chart:SfPyramidChart>

{% endhighlight %}

{% highlight c# %}

SfPyramidChart chart = new SfPyramidChart();
chart.Palette = ChartColorPalette.BlueChrome;
chart.SetBinding(SfPyramidChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.TooltipTemplate = chart.Resources["tooltipTemplate"] as DataTemplate;
chart.ShowTooltip = true;
. . .
this.Content = chart;
        
{% endhighlight %}

{% endtabs %}

![Tooltip template in WinUI Chart](Tooltip_images/WinUI_chart_tooltip_template.png)

