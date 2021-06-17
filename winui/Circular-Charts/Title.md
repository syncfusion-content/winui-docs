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


Header can be positioned left or right side of the chart using [`HorizontalHeaderAlignment`](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Charts.ChartBase.html#Syncfusion_UI_Xaml_Charts_ChartBase_HorizontalHeaderAlignment) property.

Also you can add more customization for the header as below: 

{% tabs %}

{% highlight xaml %}

<chart:SfChart.Header>

<Border BorderThickness="0.5" BorderBrush="Black" Margin="10" CornerRadius="5">

<TextBlock FontSize="14" Text="Chart Area Header" Margin="5">

<TextBlock.Effect>

<DropShadowEffect Color="Black" 

Opacity="0.5" />

</TextBlock.Effect>

</TextBlock>

</Border>

</chart:SfChart.Header>

{% endhighlight %}

{% highlight c# %}

SfChart chart = new SfChart();

Border border = new Border()
{

BorderThickness = new Thickness(0.5),

BorderBrush = new SolidColorBrush(Colors.Black),

Margin = new Thickness(10),

CornerRadius = new CornerRadius(5)

};

TextBlock textBlock = new TextBlock()
{

Text = "Chart Area Header",

Margin = new Thickness(5),

FontSize = 14

};

textBlock.Effect = new DropShadowEffect()
{

Color = Colors.Black,

Opacity = 0.5

};

border.Child = textBlock;

chart.Header = border;

{% endhighlight %}

{% endtabs %}

![Customizing Header of WPF Chart](Area_images/wpf-chart-header-customization.jpeg)


N> Here, HorizontalHeaderAlignment is set as ‘Right’.
