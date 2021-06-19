---
layout: post
title: Tooltip in WinUI Chart control | Syncfusion
description: Learn here all about Tooltip feature of Syncfusion WinUI funnel Chart control. It is set to display the metadata of the particular segment or data point.
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Tooltip in WinUI Funnel Chart (SfFunnelChart)

The Tooltip feature allows you to display any information over a [`ChartSeries`](). It appears at the data point position when the mouse hovers over any chart segment. It is set to display the metadata of the particular segment or data point.

## Define Tooltip

Chart provides tooltip support for all the series. It is used to show information about the segment, when you tap on the segment. The tooltip will be visible if you enable [`ShowTooltip`]() property as in the below code snippet.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart" 
                ShowTooltip="True"
                Palette="BlueChrome"
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">          

</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.Palette = ChartColorPalette.BlueChrome;
chart.SetBinding(SfFunnelChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.ShowTooltip = true;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Tooltip support in WinUI funnel chart](Tooltip_images/WinUI_FunnelChart_Tooltip.png)

## Customizing tooltip

The [ChartTooltipBehavior]() is commonly used for all series to customize the tooltip. For customizing the tooltip, you can create an instance [ChartTooltipBehavior]() and add it to the SfChart Behaviors collection.

The following properties are used to customize and configure tooltip which is available in the `ChartTooltipBehavior.`

* [EnableAnimation]() - Used to enable the animation when showing the tooltip.
* [Style]() - Used to customize the fill and stroke of the tooltip.
* [LabelStyle]() - Used to customize the tooltip label.
* [HorizontalOffset]() - Used to position the tooltip at a distance from the data point or cursor position horizontally.
* [VerticalOffset]() - Used to position the tooltip at a distance from the data point or cursor position vertically.
* [HorizontalAlignment]() - Used to align the tooltip label at left, right and center of the data point position or cursor position horizontally.
* [VerticalAlignment]() - Used to align the tooltip label at top, center and bottom of the data point position or cursor position vertically.
* [ShowDuration]() - Used to set the amount of time that the tooltip remains visible in milliseconds.
* [InitialShowDelay]() - Used to delay in milliseconds to show the tooltip once the user interacts with series.

{% tabs %}

{% highlight xml %}

<chart:SfFunnelChart.Behaviors>
    <chart:ChartTooltipBehavior/>
</chart:SfFunnelChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();

ChartTooltipBehavior behavior = new ChartTooltipBehavior();

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}


### Customizing the tooltip background

The tooltip's fill and stroke color can be customized using the [Style]() property. To define a [Style]() for tooltip, specify the style of `TargetType` as `Path.`

The following code example explains applying the style for tooltip.

{% tabs %}

{% highlight xml %}

<chart:SfFunnelChart.Resources>
    <Style TargetType="Path" x:Key="style">
        <Setter Property="Stroke" Value="Black"/>
        <Setter Property="Fill" Value="Gray"/>
    </Style>
</chart:SfFunnelChart.Resources>

<chart:SfFunnelChart.Behaviors>
    <chart:ChartTooltipBehavior Style="{StaticResource style}"/>
</chart:SfFunnelChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
Style style = new Style(typeof(Path));
style.Setters.Add(new Setter(Path.StrokeProperty, new SolidColorBrush(Colors.Black)));
style.Setters.Add(new Setter(Path.FillProperty, new SolidColorBrush(Colors.Gray)));
...
ChartTooltipBehavior tooltipBehavior = new ChartTooltipBehavior();
tooltipBehavior.Style = style;
chart.Behaviors.Add(tooltipBehavior);

{% endhighlight %}

{% endtabs %}

![Tooltip background style customization in WinUI funnel chart](Tooltip_images/WinUI_FunnelChart_background_style_customization_Tooltip.png)

### Customizing the tooltip label style

The tooltip label style can be customized using the [LabelStyle]() property. To define a [Style]() for the tooltip label, specify the style of `TargetType` as `TextBlock.`

The following code example explains applying the style for a tooltip label.

{% tabs %}

{% highlight xml %}

<chart:SfFunnelChart.Resources>
    <Style TargetType="TextBlock" x:Key="labelStyle">
        <Setter Property="FontSize" Value="14"/>
        <Setter Property="Foreground" Value="Yellow"/>
    </Style>
</chart:SfFunnelChart.Resources>

<chart:SfFunnelChart.Behaviors>
    <chart:ChartTooltipBehavior LabelStyle="{StaticResource labelStyle}"/>
</chart:SfFunnelChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
Style labelStyle = new Style(typeof(TextBlock));
labelStyle.Setters.Add(new Setter(TextBlock.FontSizeProperty, 14d));
labelStyle.Setters.Add(new Setter(TextBlock.ForegroundProperty, new SolidColorBrush(Colors.Yellow)));
...
ChartTooltipBehavior tooltipBehavior = new ChartTooltipBehavior();
tooltipBehavior.LabelStyle = labelStyle;
chart.Behaviors.Add(tooltipBehavior);

{% endhighlight %}

{% endtabs %}

![Tooltip label style customization in WinUI funnel chart](Tooltip_images/WinUI_FunnelChart_Label_style_customization_Tooltip.png)

## Customizing tooltip using ChartTooltip attached properties

### Aligning the Tooltip

The tooltip can be aligned with respect to the cursor position using the [`HorizontalAlignment`]() and [`VerticalAlignment`]() properties.

**HorizontalAlignment**

The following code example explains the positioning of tooltip to the left of the cursor.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart" 
                ShowTooltip="True" 
                Palette="BlueChrome" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">

    <chart:SfFunnelChart.Behaviors>
        <chart:ChartTooltipBehavior HorizontalAlignment="Left"/>
    </chart:SfFunnelChart.Behaviors>

</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
ChartTooltipBehavior tooltipBehavior = new ChartTooltipBehavior();
tooltipBehavior.HorizontalAlignment = HorizontalAlignment.Left;
chart.Behaviors.Add(tooltipBehavior);

{% endhighlight %}

{% endtabs %}

![Tooltip alignment support in WinUI Funnel Chart](Tooltip_images/WinUI_FunnelChart_Tooltip_horizontal_alignment.png)

N> By default the horizontal alignment is center for the tooltip.

**VerticalAlignment**

The following code example explains the positioning of tooltip to the bottom of the cursor.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart" 
                ShowTooltip="True" 
                Palette="BlueChrome" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">

    <chart:SfFunnelChart.Behaviors>
        <chart:ChartTooltipBehavior VerticalAlignment="Bottom"/>
    </chart:SfFunnelChart.Behaviors>

</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
ChartTooltipBehavior tooltipBehavior = new ChartTooltipBehavior();
tooltipBehavior.VerticalAlignment = VerticalAlignment.Bottom;
chart.Behaviors.Add(tooltipBehavior);

{% endhighlight %}

{% endtabs %}

![Tooltip alignment support in WinUI Funnel Chart](Tooltip_images/WinUI_FunnelChart_Tooltip_vertical_alignment.png)

**VerticalOffset and HorizontalOffset**

The tooltip can be positioned at a particular distance from the cursor horizontally using the [`HorizontalOffset`]() and vertically using [`VerticalOffset`]() properties.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart" 
                ShowTooltip="True" 
                Palette="BlueChrome" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">

        <chart:SfFunnelChart.Behaviors>
            <chart:ChartTooltipBehavior HorizontalOffset="40" VerticalOffset="40"/>
        </chart:SfFunnelChart.Behaviors>

</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
ChartTooltipBehavior tooltipBehavior = new ChartTooltipBehavior();
tooltipBehavior.HorizontalOffset = 40;
tooltipBehavior.VerticalOffset = 40;
chart.Behaviors.Add(tooltipBehavior);

{% endhighlight %}

{% endtabs %}

![VerticalOffset and HorizontalOffset support for tooltip in WinUI Funnel Chart](Tooltip_images/WinUI_FunnelChart_Tooltip_Offset.png)

### Tooltip duration

The attached property [`ShowDuration`]() in [`ChartTooltip`]() sets the duration time for tooltip to be displayed in milliseconds.

The following code example demonstrates the duration of the tooltip set as 5 seconds.

{% tabs %}

{% highlight xml %}

<chart:SfFunnelChart x:Name="chart" 
                ShowTooltip="True" 
                Palette="BlueChrome" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">

    <chart:SfFunnelChart.Behaviors>
        <chart:ChartTooltipBehavior ShowDuration="5000"/>
    </chart:SfFunnelChart.Behaviors>

</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
ChartTooltipBehavior tooltipBehavior = new ChartTooltipBehavior();
tooltipBehavior.ShowDuration = 5000;
chart.Behaviors.Add(tooltipBehavior);

{% endhighlight %}

{% endtabs %}

N> The tooltip by default will be displayed for 1000 milliseconds.

**Show delay**

Tooltip also has support to delay the time to display by setting the [`SetInitialShowDelay`]() property in milliseconds.

The following code example demonstrates the tooltip will be delayed for 1 second at the before display.

{% tabs %}

{% highlight xml %}

<chart:SfFunnelChart x:Name="chart" 
                ShowTooltip="True" 
                Palette="BlueChrome" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">

    <chart:SfFunnelChart.Behaviors>
        <chart:ChartTooltipBehavior InitialShowDelay="1000"/>
    </chart:SfFunnelChart.Behaviors>

</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
ChartTooltipBehavior tooltipBehavior = new ChartTooltipBehavior();
tooltipBehavior.InitialShowDelay = 1000;
chart.Behaviors.Add(tooltipBehavior);

{% endhighlight %}

{% endtabs %}

### Animation for Tooltip

You can also provide animation effects for tooltip by setting the [`EnableAnimation`]() property to true as shown in the following code snippet.

{% tabs %}

{% highlight xml %}

<chart:SfFunnelChart x:Name="chart" 
                ShowTooltip="True" 
                Palette="BlueChrome" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">

    <chart:SfFunnelChart.Behaviors>
        <chart:ChartTooltipBehavior EnableAnimation="True"/>
    </chart:SfFunnelChart.Behaviors>

</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
ChartTooltipBehavior tooltipBehavior = new ChartTooltipBehavior();
tooltipBehavior.EnableAnimation = true;
chart.Behaviors.Add(tooltipBehavior);

{% endhighlight %}

{% endtabs %}

### Customizing the Appearance

The [`TooltipTemplate`]() property allows you to customize the default appearance of the tooltip as explained in the following code snippet.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart" 
                ShowTooltip="True" 
                Palette="BlueChrome" TooltipTemplate="{StaticResource tooltipTemplate}"
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">

    <chart:SfFunnelChart.Resources>
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
    </chart:SfFunnelChart.Resources>

    <chart:SfFunnelChart.Behaviors>
        <chart:ChartTooltipBehavior Style="{StaticResource style}"/>
    </chart:SfFunnelChart.Behaviors>

</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.Palette = ChartColorPalette.BlueChrome;
chart.SetBinding(SfFunnelChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.TooltipTemplate = chart.Resources["tooltipTemplate"] as DataTemplate;
chart.ShowTooltip = true;
. . .
this.Content = chart;
        
{% endhighlight %}

{% endtabs %}

![Tooltip customization in WinUI Funnel Chart](Tooltip_images/WinUI_FunnelChart_Tooltip_customization.png)

