---
layout: post
title: Header in WinUI Polar Chart control | Syncfusion
description: Learn all about Header support in Syncfusion WinUI Polar Chart(SfPolarChart) control, its elements and more details.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Header in WinUI Polar Charts (SfPolarChart)

[Header]() property is used to define the title for the chart. This allows to add any object (.Net object) as content for chart title.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart Header="Polar Chart Header">
. . .
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.Header = "Polar Chart Header";
...

{% endhighlight %}

{% endtabs %}

![WinUI Polar Chart with Header]()

Header can be positioned left or right side of the chart using [HorizontalHeaderAlignment]() property.

Also you can add more customization for the header as below: 

% tabs %}

{% highlight xaml %}

<chart:SfPolarChart.Header>
    <Border BorderThickness="0.5" BorderBrush="Black" Margin="10" CornerRadius="5">
        <TextBlock Text="Polar Chart Header"
                   Margin="5" 
                   HorizontalTextAlignment="Center"
                   FontFamily="Verdana" FontSize="14" 
                   Foreground="Blue">
        </TextBlock>
    </Border>
</chart:SfPolarChart.Header>

{% endhighlight %}

{% highlight c# %}

...
Border border = new Border()
{
    BorderBrush = new SolidColorBrush(Colors.Black),
    Margin = new Thickness(10),
    CornerRadius = new CornerRadius(5)
};

TextBlock textBlock = new TextBlock()
{
    Text = "Polar Chart Header",
    HorizontalTextAlignment = TextAlignment.Center,
    FontFamily = new FontFamily("Verdana"),
    Foreground = new SolidColorBrush(Colors.Blue),
    FontSize = 25,
};

border.Child = textBlock;
chart.Header = border;

{% endhighlight %}

{% endtabs %}

![Customizing Header of WinUI Polar Chart]()

