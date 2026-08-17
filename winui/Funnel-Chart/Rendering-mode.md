---
layout: post
title: Rendering Mode in WinUI Funnel Chart | Syncfusion®
description: Rendering mode in the WinUI Funnel Chart controls how funnel segments are displayed, enabling different visual representations of data.
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Rendering mode in WinUI funnel charts

The [Mode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_Mode) property defines the rendering mode of the funnel chart, which defines where to bind your values (to height or width). The default value of the [Mode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_Mode) property is [ValueIsHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartFunnelMode.html#Syncfusion_UI_Xaml_Charts_ChartFunnelMode_ValueIsHeight).  The following example demonstrates [ValueIsHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartFunnelMode.html#Syncfusion_UI_Xaml_Charts_ChartFunnelMode_ValueIsHeight) and [ValueIsWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartFunnelMode.html#Syncfusion_UI_Xaml_Charts_ChartFunnelMode_ValueIsWidth) of funnel mode.

## Rendering with height

[ValueIsHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartFunnelMode.html#Syncfusion_UI_Xaml_Charts_ChartFunnelMode_ValueIsHeight) is used to render the funnel chart segments based on the height for data point values.

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart 
    x:Name="chart"
    ItemsSource="{Binding Data}"
    XBindingPath="Category"
    YBindingPath="Value"
    Mode="ValueIsHeight">
</chart:SfFunnelChart>
 
{% endhighlight %}

{% highlight C# %}

SfFunnelChart chart = new SfFunnelChart();

chart.SetBinding(SfFunnelChart.ItemsSourceProperty,new Binding() 
{ 
    Path = new PropertyPath("Data") 
});

chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.Mode = ChartFunnelMode.ValueIsHeight;

// Configure additional chart elements
this.Content = chart;


{% endhighlight %}

{% endtabs %}

![Rendering mode with height in WinUI Chart](Rendering-mode_Images/winui-chart_value-is-height.png)

## Rendering with width

[ValueIsWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartFunnelMode.html#Syncfusion_UI_Xaml_Charts_ChartFunnelMode_ValueIsWidth) is used to render the funnel chart segments based on the width for data point values.

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart 
    x:Name="chart"
    ItemsSource="{Binding Data}"
    XBindingPath="Category"
    YBindingPath="Value"
    Mode="ValueIsWidth">
</chart:SfFunnelChart>  
 
{% endhighlight %}

{% highlight C# %}

SfFunnelChart chart = new SfFunnelChart();

chart.SetBinding(SfFunnelChart.ItemsSourceProperty, new Binding() 
{
    Path = new PropertyPath("Data") 
});

chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.Mode = ChartFunnelMode.ValueIsWidth;

// Configure additional chart elements
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Rendering mode with width in WinUI Chart](Rendering-mode_Images/winui-chart_value-is-width.png)
