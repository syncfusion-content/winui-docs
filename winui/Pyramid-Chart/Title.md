---
layout: post
title: Title in WinUI Chart control | Syncfusion
description: Learn here all about title with Syncfusion WinUI Chart(SfPyramidChart) control and its customization.
platform: WinUI
control: SfPyramidChart
documentation: ug
---

# Chart title in WinUI Chart (SfPyramidChart)

`Header` property is used to define the title for the chart.

{% tabs %}   

{% highlight xaml %}

<chart:SfPyramidChart x:Name="chart" Header="The Food Comparison Pyramid">
 . . .           
</chart:SfPyramidChart>

{% endhighlight %}

{% highlight C# %}

SfPyramidChart chart = new SfPyramidChart();
chart.Header = "The Food Comparison Pyramid";
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %} 

![Title support in WinUI chart](Title_Images/WinUI_chart_title.png)

## Customization

The pyramid chart provides support to add any `UIElement` as a title. The following code example defines `TextBlock` as chart header.

{% tabs %}   

{% highlight xaml %}

 <chart:SfPyramidChart>

    <chart:SfPyramidChart.Header>
        <Border BorderThickness="2" BorderBrush="Black" Margin="10" CornerRadius="5">
            <TextBlock FontSize="14" Text="The Food Comparison Pyramid" Margin="5"/>
        </Border>
    </chart:SfPyramidChart.Header>
            
</chart:SfPyramidChart>

{% endhighlight %}

{% highlight C# %}

    SfPyramidChart chart = new SfPyramidChart();
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
        Text = "The Food Comparison Pyramid",
        Margin = new Thickness(5),
        FontSize = 14
    };

    border.Child = textBlock;
    chart.Header = border;
    . . . 
    this.Content = chart;

{% endhighlight %}

{% endtabs %} 

![Title customization support in WinUI chart](Title_Images/WinUI_chart_title_customization.png)

## Alignment

The title text content can be aligned horizontally to the left, center or right of the chart using the [HorizontalHeaderAlignment]() property of the `SfPyramidChart`.

{% tabs %}   

{% highlight xaml %}

<chart:SfPyramidChart x:Name="chart" 
                Header="The Food Comparison Pyramid"
                HorizontalHeaderAlignment="Left"
                Palette="BlueChrome"
                ItemsSource="{Binding Data}" 
                XBindingPath="FoodName"
                YBindingPath="Calories">
            
</chart:SfPyramidChart>

{% endhighlight %}

{% highlight C# %}

public sealed partial class MainPage : Page
{
    public MainPage()
    {
        this.InitializeComponent();
        SfPyramidChart chart = new SfPyramidChart();
        chart.Header = "The Food Comparison Pyramid";
        chart.HorizontalHeaderAlignment = HorizontalAlignment.Left;
        chart.Palette = ChartColorPalette.BlueChrome;
        chart.SetBinding(SfPyramidChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
        chart.XBindingPath = "FoodName";
        chart.YBindingPath = "Calories";
        . . . 
        this.Content = chart;
    }
}

{% endhighlight %}

{% endtabs %} 

![Title text alignment support in WinUI chart](Title_images/WinUI_chart_title_alignment.png)

