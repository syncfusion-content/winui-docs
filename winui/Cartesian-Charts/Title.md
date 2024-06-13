---
layout: post
title: Title in WinUI Chart control | Syncfusion
description: Learn here all about title with Syncfusion WinUI Chart (SfCartesianChart) control and its customization.
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: chart title in winui chart, winui sfcartesianchart chart title, winui chart title customization, syncfusion winui chart title, winui sfcartesianchart title configuration.
---

# Chart Title in WinUI Chart (SfCartesianChart)

[Header](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartBase.html#Syncfusion_UI_Xaml_Charts_ChartBase_Header) property is used to define the title for the chart.

{% tabs %}   

{% highlight xaml %}

<chart:SfCartesianChart x:Name="chart" Header="Chart Area Header">
 . . .           
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight C# %}

SfCartesianChart chart = new SfCartesianChart();
chart.Header = "Chart Area Header";
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %} 

![Title support in WinUI chart](Title_images/WinUI_chart_title.png)

## Customization

Chart provides support to add any `UIElement` as a title. The following code example defines `TextBlock` as chart header.

{% tabs %}   

{% highlight xaml %}

 <chart:SfCartesianChart>

    <chart:SfCartesianChart.Header>
        <Border BorderThickness="2" 
                BorderBrush="Black" 
                Margin="10" 
                CornerRadius="5">
            <TextBlock FontSize="14"
					   Text="Chart Area Header"
					   Margin="5"/>
        </Border>
    </chart:SfCartesianChart.Header>
            
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight C# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
Border border = new Border()
{
    BorderThickness = new Thickness(2),
    BorderBrush = new SolidColorBrush(Colors.Black),
    Margin = new Thickness(10),
    CornerRadius = new CornerRadius(5),
};

TextBlock textBlock = new TextBlock()
{
    Text = "Chart Area Header",
    Margin = new Thickness(5),
    FontSize = 14
};

border.Child = textBlock;
chart.Header = border;
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %} 

![Title customization support in WinUI chart](Title_images/WinUI_chart_title_customization.png)

## Alignment

The title text content can be aligned horizontally to the left, center or right of the chart using the [HorizontalHeaderAlignment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartBase.html#Syncfusion_UI_Xaml_Charts_ChartBase_HorizontalHeaderAlignment) property of the [SfCartesianChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html).

{% tabs %}   

{% highlight xaml %}

<chart:SfCartesianChart x:Name="chart" 
						HorizontalHeaderAlignment="Left">
. . .
    <chart:SfCartesianChart.Header>
        <Border BorderThickness="2" 
                BorderBrush="Black" 
                Margin="0, 0, 0, 10" 
                CornerRadius="5">
            <TextBlock FontSize="14" 
					   Text="Chart Area Header"
					   Margin="5"/>
        </Border>
    </chart:SfCartesianChart.Header>
. . . 
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight C# %}

SfCartesianChart chart = new SfCartesianChart();
chart.HorizontalHeaderAlignment = HorizontalAlignment.Left;
. . .
Border border = new Border()
{
    BorderThickness = new Thickness(2),
    BorderBrush = new SolidColorBrush(Colors.Black),
    Margin = new Thickness(0,0,0,10),
    CornerRadius = new CornerRadius(5),
};

TextBlock textBlock = new TextBlock()
{
    Text = "Chart Area Header",
    Margin = new Thickness(5),
    FontSize = 14
};

border.Child = textBlock;
chart.Header = border;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %} 

![Title text alignment support in WinUI chart](Title_images/WinUI_chart_title_alignment.png)
