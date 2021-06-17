---
layout: post
title: Header in WinUI Circular Chart control | Syncfusion
description: Learn all about Header support in Syncfusion WinUI Circular Charts (SfCircularChart) control, its elements and more details.
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Header in WinUI Circular Charts (SfCircularChart)

[Header]() property is used to define the title for the chart. This allows you to add any object (.Net object) as content for chart title. 

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart Header="Circular Chart Header">
. . .
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
chart.Header = "Circular Chart Header";

{% endhighlight %}

{% endtabs %}

![WinUI Circular Chart with Header](Header_Images/WinUI_Circular_chart_Header.png)


Header can be positioned left or right side of the chart using [HorizontalHeaderAlignment]() property.

Also you can add more customization for the header as below: 

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart.Header>
    <Border BorderThickness="0.5" BorderBrush="Black" Margin="10" CornerRadius="5">
        <TextBlock Text="Circular Chart Header"
                   Margin="5" 
                   HorizontalTextAlignment="Center"
                   FontFamily="Verdana" FontSize="14" 
                   Foreground="Blue">
        </TextBlock>
    </Border>
</chart:SfCircularChart.Header>

{% endhighlight %}

{% highlight c# %}

Border border = new Border()
{
    BorderBrush = new SolidColorBrush(Colors.Black),
    Margin = new Thickness(10),
    CornerRadius = new CornerRadius(5)
};

TextBlock textBlock = new TextBlock()
{
    Text = "Circular Chart Header",
    HorizontalTextAlignment = TextAlignment.Center,
    FontFamily = new FontFamily("Verdana"),
    Foreground = new SolidColorBrush(Colors.Blue),
    FontSize = 25,
};

border.Child = textBlock;
chart.Header = border;

{% endhighlight %}

{% endtabs %}

![Customizing Header of WinUI Circular Chart](Header_Images/WinUI_Circular_chart_Header_customization.png)