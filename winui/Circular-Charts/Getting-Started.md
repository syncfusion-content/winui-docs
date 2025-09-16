---
layout: post
title: Getting Started with WinUI Circular Chart control | Syncfusion
description: Learn here all about getting started with Syncfusion® WinUI Circular Chart (SfCircularChart) control, its elements, and more.
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Getting Started with WinUI Circular Charts (SfCircularChart)

This section explains how to populate the circular chart with data, headers, data labels, legends, tooltips, and essential aspects for getting started with the chart.

## Creating an Application with WinUI Chart (SfCircularChart)

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://learn.microsoft.com/en-us/windows/apps/winui/winui3/create-your-first-winui3-app).
2. Add a reference to the [Syncfusion.Chart.WinUI](https://www.nuget.org/packages/Syncfusion.Chart.WinUI/) NuGet package.
3. Import the control namespace `Syncfusion.UI.Xaml.Charts` in XAML or C# to initialize the control.
4. Initialize the [SfCircularChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCircularChart.html) control.

{% capture codesnippet1 %}
{% tabs %} 

{% highlight xaml %}

<Window
    x:Class="ChartDemo.MainWindow"
    . . .
    xmlns:chart="using:Syncfusion.UI.Xaml.Charts">

    <chart:SfCircularChart/>
</Window>
 
{% endhighlight %}

{% highlight C# %}

using Syncfusion.UI.Xaml.Charts;
. . .
public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        this.InitializeComponent();
        SfCircularChart chart = new SfCircularChart();
        . . .
        this.Content = chart;
    }
}   
{% endhighlight %}

{% endtabs %}
{% endcapture %}
{{ codesnippet1 | OrderList_Indent_Level_1 }}

## Initialize the ViewModel

Define a simple data model that represents a data point in the chart.

{% tabs %}  

{% highlight c# %}

public class Sales
{
    public string Product { get; set; }

    public double SalesRate { get; set; }
}

{% endhighlight %} 

{% endtabs %} 

Next, create a ViewModel class and initialize a list of `Sales` objects.

{% tabs %}  

{% highlight c# %}

public class ChartViewModel
{
    public List<Sales> Data { get; set; }

    public ChartViewModel()
    {
        Data = new List<Sales>()
        {
            new Sales() { Product = "iPad", SalesRate = 25 },
            new Sales() { Product = "iPhone", SalesRate = 35 },
            new Sales() { Product = "MacBook", SalesRate = 15 },
            new Sales() { Product = "Mac", SalesRate = 5 },
            new Sales() { Product = "Others", SalesRate = 10 },
        };
    }
}

{% endhighlight %} 

{% endtabs %} 

Create a `ChartViewModel` instance and set it as the chart's `DataContext` to enable property binding from the `ChartViewModel` class.

N> Add the namespace of the `ChartViewModel` class to your XAML Page if you prefer to set the `DataContext` in XAML.

{% tabs %} 

{% highlight xaml %} 

<Window
    . . .
    xmlns:chart="using:Syncfusion.UI.Xaml.Charts"
    xmlns:model="using:ChartDemo.ViewModel">

    <chart:SfCircularChart>
        <chart:SfCircularChart.DataContext>
            <model:ChartViewModel/>
        </chart:SfCircularChart.DataContext>
    </chart:SfCircularChart>
</Window>

{% endhighlight %}

{% highlight C# %} 

ChartViewModel viewModel = new ChartViewModel();
chart.DataContext = viewModel;

{% endhighlight %}

{% endtabs %} 

## Populate the Chart with Data

Add [PieSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.PieSeries.html) to the chart's [Series](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCircularChart.html) collection and bind `Data` to the series [ItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeries.html) property from its `DataContext` to create a Product-Sales Pie chart.

N> To plot the series, configure the [XBindingPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeries.html) and [YBindingPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.XyDataSeries.html) properties to retrieve values from the respective properties in the data model.

{% tabs %}   

{% highlight xaml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Series>
        <chart:PieSeries ItemsSource="{Binding Data}" 
                         XBindingPath="Product" 
                         YBindingPath="SalesRate"/>
    </chart:SfCircularChart.Series>
</chart:SfCircularChart>

{% endhighlight %}

{% highlight C# %}

SfCircularChart chart = new SfCircularChart();

ChartViewModel viewModel = new ChartViewModel();
chart.DataContext = viewModel;

PieSeries series = new PieSeries();
series.SetBinding(PieSeries.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
series.XBindingPath = "Product";
series.YBindingPath = "SalesRate";

chart.Series.Add(series);
. . .

{% endhighlight %}

{% endtabs %} 

## Add a Title

The header of the chart acts as a title to provide quick insights into the data being plotted. You can set a title using the [Header](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartBase.html) property of the circular chart.

{% tabs %} 

{% highlight xaml %}

<chart:SfCircularChart Header="PRODUCT SALES">
    . . .
</chart:SfCircularChart>

{% endhighlight %}

{% highlight C# %}

SfCircularChart chart = new SfCircularChart();
. . .
chart.Header = "PRODUCT SALES";

{% endhighlight %}

{% endtabs %}  

## Enable Data Labels

The [ShowDataLabels](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeries.html) property of [ChartSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeries.html) can be used to enable data labels, enhancing the readability of the circular chart. By default, label visibility is set to `False`.

{% tabs %} 

{% highlight xaml %}
<chart:SfCircularChart>
. . .
    <chart:PieSeries ShowDataLabels="True"
                     ItemsSource="{Binding Data}" 
                     XBindingPath="Product" 
                     YBindingPath="SalesRate"/>
</chart:SfCircularChart>

{% endhighlight %}

{% highlight C# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();
series.ShowDataLabels = true;

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %} 

## Enable a Legend

The legend provides information about the data points displayed in the circular chart. The [Legend](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartBase.html) property of the chart is used to enable it.

{% tabs %} 

{% highlight xaml %}

<chart:SfCircularChart>
    . . .
    <chart:SfCircularChart.Legend>
        <chart:ChartLegend/>
    </chart:SfCircularChart.Legend>
</chart:SfCircularChart>

{% endhighlight %}

{% highlight C# %}

SfCircularChart chart = new SfCircularChart();
. . .
chart.Legend = new ChartLegend();

{% endhighlight %}

{% endtabs %} 

## Enable Tooltips

Tooltips display information about a segment when hovered over. Enable tooltips by setting the series [EnableTooltip](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeries.html) property to `True`.

{% tabs %} 

{% highlight xaml %}

<chart:SfCircularChart>
. . .
    <chart:PieSeries EnableTooltip="True"/>
</chart:SfCircularChart>

{% endhighlight %}

{% highlight C# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();
series.EnableTooltip = true;

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

The following code example gives you the complete code of above configurations.

{% tabs %} 

{% highlight xaml %}

<chart:SfCircularChart Header="PRODUCT SALES">
    <chart:SfCircularChart.DataContext>
        <model:ChartViewModel/>
    </chart:SfCircularChart.DataContext>
    <chart:SfCircularChart.Legend>
        <chart:ChartLegend/>
    </chart:SfCircularChart.Legend>
    <chart:SfCircularChart.Series>
        <chart:PieSeries ItemsSource="{Binding Data}"
						 ShowDataLabels="True"
                         XBindingPath="Product"
						 EnableTooltip="True"
                         YBindingPath="SalesRate">
        </chart:PieSeries>
    </chart:SfCircularChart.Series>
</chart:SfCircularChart>
 
{% endhighlight %}

{% highlight C# %}

using Syncfusion.UI.Xaml.Charts;
. . .
public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        SfCircularChart chart = new SfCircularChart();

        chart.Header = "PRODUCT SALES";
        chart.Legend = new ChartLegend();
        ChartViewModel viewModel = new ChartViewModel();
        chart.DataContext = viewModel;

        PieSeries series = new PieSeries();
        series.SetBinding(PieSeries.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
        series.XBindingPath = "Product";
        series.YBindingPath = "SalesRate";
        series.EnableTooltip = true;
        series.ShowDataLabels = true;

        chart.Series.Add(series);
        this.Content = chart;
    }
}

{% endhighlight %}

{% endtabs %}

![Pie chart in WinUI Chart](Getting-Started_Images/WinUI_pie_chart.png)

N> Download the demo application from [GitHub](https://github.com/SyncfusionExamples/GettingStartedChartWinUI/tree/main/CircularChartGettingStarted)
