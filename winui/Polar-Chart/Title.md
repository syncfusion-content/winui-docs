---
layout: post
title: Title in WinUI Chart control | Syncfusion
description: Learn here all about the title in Syncfusion WinUI Chart (SfPolarChart) control and its customization.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Chart Title in WinUI Chart (SfPolarChart)

`Header` property of `SfPolarChart` is used to define and customize the chart title. It accepts any `UIElement` as content for the chart header.

{% tabs %}

{% highlight xaml %}

 <chart:SfPolarChart>
    <chart:SfPolarChart.Header>
        <Border BorderThickness="2" BorderBrush="Black" Margin="10" CornerRadius="5">
            <TextBlock FontSize="14" Text="Polar Chart" Margin="5"/>
        </Border>
    </chart:SfPolarChart.Header>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
. . .
Border border = new Border()
{
    BorderThickness = new Thickness(2),
    BorderBrush = new SolidColorBrush(Colors.Black),
    Margin = new Thickness(10),
    CornerRadius = new CornerRadius(5)
};

TextBlock textBlock = new TextBlock()
{
    Text = "Polar Chart",
    Margin = new Thickness(5),
    FontSize = 14
};

border.Child = textBlock;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Title customization support in WinUI chart](Title_images/WinUI_PolarChart_TitleCustomization.png)

## Alignment

The title text content can be aligned horizontally to the left, center or right of the chart using the [HorizontalHeaderAlignment]() property of the `SfPolarChart`.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart HorizontalHeaderAlignment="Left">
    <chart:SfPolarChart.Header>
        <Border BorderThickness="2" BorderBrush="Black" Background="LightBlue" Margin="10" CornerRadius="5">
            <TextBlock Text="Polar Chart"
                    Margin="5" 
                    HorizontalTextAlignment="Center"
                    FontSize="14" 
                    Foreground="Blue">
            </TextBlock>
        </Border>
    </chart:SfPolarChart.Header>
    ...
 </chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.HorizontalHeaderAlignment = HorizontalAlignment.Left;
...
Border border = new Border()
{
    BorderThickness = new Thickness(2),
    BorderBrush = new SolidColorBrush(Colors.Black),
    Background = new SolidColorBrush(Colors.LightBlue),
    Margin = new Thickness(10),
    CornerRadius = new CornerRadius(5)
};

TextBlock textBlock = new TextBlock()
{
    Text = "Polar Chart",
    HorizontalTextAlignment = TextAlignment.Center,
    Foreground = new SolidColorBrush(Colors.Blue),
    FontSize = 14,
};

border.Child = textBlock;
chart.Header = border;
...

{% endhighlight %}

{% endtabs %}

![Title text alignment support in WinUI chart](Title_images/WinUI_PolarChart_TitleAlignment.png)