---
layout: post
title: Title in WinUI Funnel Chart control | Syncfusion
description: Learn here all about title with Syncfusion WinUI Funnel Chart(SfFunnelChart) control with key features.
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Chart title in WinUI Funnel Chart (SfFunnelChart)

You can define and customize the Chart title using header property of SfFunnelChart. This allows you to use any object (.Net object) as content for chart header.

{% tabs %}   

{% highlight xaml %}

 <chart:SfFunnelChart>

    <chart:SfFunnelChart.Header>
        <Border BorderThickness="2" BorderBrush="Black" Margin="10" CornerRadius="5">
            <TextBlock FontSize="14" Text="PRODUCT SALES" Margin="5"/>
        </Border>
    </chart:SfFunnelChart.Header>
            
</chart:SfFunnelChart>

{% endhighlight %}

{% highlight C# %}

    SfFunnelChart chart = new SfFunnelChart();
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
        Text = "PRODUCT SALES",
        Margin = new Thickness(5),
        FontSize = 14
    };

    border.Child = textBlock;
    . . . 
    this.Content = chart;

{% endhighlight %}

{% endtabs %} 

## Title Alignment

You can align the title text content horizontally to the left, center or right of the chart using the [HorizontalHeaderAlignment]() property of the title.

{% tabs %}   

{% highlight xaml %}

 <chart:SfFunnelChart x:Name="chart" 
                HorizontalHeaderAlignment="Right"
                ShowTooltip="True"
                Palette="BlueChrome"
                Height="388" Width="500" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">
                
            <chart:SfFunnelChart.Header>
                <Border BorderThickness="2" BorderBrush="Black" Margin="10" CornerRadius="5">
                    <TextBlock FontSize="14" Text="PRODUCT SALES" Margin="5"/>
                </Border>
            </chart:SfFunnelChart.Header>

            <chart:SfFunnelChart.DataContext>
                <model:ChartViewModel />
            </chart:SfFunnelChart.DataContext>

            <chart:SfFunnelChart.Legend>
                <chart:ChartLegend />
            </chart:SfFunnelChart.Legend>

            <chart:SfFunnelChart.DataLabelSettings>
                <chart:FunnelDataLabelSettings Visible="True" />
            </chart:SfFunnelChart.DataLabelSettings>
            
</chart:SfFunnelChart>

{% endhighlight %}

{% highlight C# %}

public sealed partial class MainPage : Page
{
    public MainPage()
    {
        this.InitializeComponent();
            
        SfFunnelChart chart = new SfFunnelChart();
        ChartViewModel viewModel = new ChartViewModel();
        chart.DataContext = viewModel;
        chart.SetBinding(SfFunnelChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
        chart.HorizontalHeaderAlignment = HorizontalAlignment.Right;
        chart.Palette = ChartColorPalette.BlueChrome;
        chart.XBindingPath = "Category";
        chart.YBindingPath = "Value";
        chart.Height = 388;
        chart.Width = 500;

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
            Text = "PRODUCT SALES",
            Margin = new Thickness(5),
            FontSize = 14
        };

        border.Child = textBlock;
        chart.Header = border;
        chart.Legend = new ChartLegend();
        chart.ShowTooltip = true;
        chart.DataLabelSettings = new FunnelDataLabelSettings() { Visible = true };

        this.Content = chart;
    }
}

{% endhighlight %}

{% endtabs %} 

![Title WinUI Chart](Title_images/WinUI_FunnelChart_TitleAlignment.png)