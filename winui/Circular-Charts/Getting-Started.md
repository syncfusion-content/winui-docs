---
layout: post
title: Getting Started with WinUI Circular Chart control | Syncfusion
description: Learn here all about getting started with Syncfusion® WinUI Circular Chart (SfCircularChart) control, its elements, and more.
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Getting Started with WinUI Circular Charts (SfCircularChart)

This section explains how to populate the circular chart with data, header, data labels, legend, and tooltips, as well as the essential aspects for getting started with the chart.

## Creating an application with WinUI Chart (SfCircularChart)

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://learn.microsoft.com/en-us/windows/apps/winui/winui3/create-your-first-winui3-app).
2. Add reference to [Syncfusion.Chart.WinUI](https://www.nuget.org/packages/Syncfusion.Chart.WinUI/) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Charts` in XAML or C# to initialize the control.
4. Initialize [SfCircularChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCircularChart.html?tabs=tabid-1%2Ctabid-4%2Ctabid-6%2Ctabid-8%2Ctabid-10%2Ctabid-12) control.

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

## Initialize View Model

Now, let us define a simple data model that represents a data point in chart.

{% tabs %}  

{% highlight c# %}

public class Sales
{
    public string Product { get; set; }

    public double SalesRate { get; set; }
}

{% endhighlight %} 

{% endtabs %} 

Next, create a view model class and initialize a list of `Model` objects as follows.

{% tabs %}  

{% highlight c# %}

public class ChartViewModel
{
    public List<Sales> Data { get; set; }

    public ChartViewModel()
    {
        Data = new List<Sales>()
        {
            new Sales(){Product = "iPad", SalesRate = 25},
            new Sales(){Product = "iPhone", SalesRate = 35},
            new Sales(){Product = "MacBook", SalesRate = 15},
            new Sales(){Product = "Mac", SalesRate = 5},
            new Sales(){Product = "Others", SalesRate = 10},
        };
    }
}

{% endhighlight %} 

{% endtabs %} 

Create a `ViewModel` instance and set it as the chart's `DataContext`. This enables property binding from `ViewModel` class.

N> Add namespace of `ViewModel` class to your XAML Page if you prefer to set `DataContext` in XAML.

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

## Populate Chart with Data

Adding [PieSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.PieSeries.html?tabs=tabid-1%2Ctabid-19%2Ctabid-17%2Ctabid-21%2Ctabid-7) to the chart [Series](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCircularChart.html?tabs=tabid-1%2Ctabid-4%2Ctabid-6%2Ctabid-8%2Ctabid-10%2Ctabid-12#Syncfusion_UI_Xaml_Charts_SfCircularChart_Series) collection and binding `Data` to the series [ItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeries.html#Syncfusion_UI_Xaml_Charts_ChartSeries_ItemsSource) property from its `DataContext` for creating our own Product – Sales Pie chart.

N> To plot the series, the [XBindingPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeries.html?tabs=tabid-24%2Ctabid-22%2Ctabid-4%2Ctabid-11%2Ctabid-6%2Ctabid-18%2Ctabid-8%2Ctabid-13%2Ctabid-15%2Ctabid-17%2Ctabid-1%2Ctabid-3%2Ctabid-10%2Ctabid-20#Syncfusion_UI_Xaml_Charts_ChartSeries_XBindingPath) and [YBindingPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.XyDataSeries.html?tabs=tabid-1#Syncfusion_UI_Xaml_Charts_XyDataSeries_YBindingPath) properties must be configured so that the chart may get values from the respective properties in the data model.

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

## Add Title

The header of the chart acts as the title to provide quick information to the user about the data being plotted in the chart. You can set title using the [Header](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartBase.html?tabs=tabid-5%2Ctabid-7%2Ctabid-1%2Ctabid-3#Syncfusion_UI_Xaml_Charts_ChartBase_Header) property of circular chart as follows.

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

The [ShowDataLabels](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeries.html?tabs=tabid-24%2Ctabid-22%2Ctabid-4%2Ctabid-11%2Ctabid-6%2Ctabid-18%2Ctabid-8%2Ctabid-13%2Ctabid-15%2Ctabid-17%2Ctabid-1%2Ctabid-3%2Ctabid-10%2Ctabid-20#Syncfusion_UI_Xaml_Charts_ChartSeries_ShowDataLabels) property of [ChartSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeries.html?tabs=tabid-24%2Ctabid-22%2Ctabid-4%2Ctabid-11%2Ctabid-6%2Ctabid-18%2Ctabid-8%2Ctabid-13%2Ctabid-15%2Ctabid-17%2Ctabid-1%2Ctabid-3%2Ctabid-10%2Ctabid-20) can be used to enable data labels to improve the readability of the circular chart. The label visibility is set to `False` by default.

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

## Enable Legend

The legend provides information about the data point displayed in the circular chart. The [Legend](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartBase.html?tabs=tabid-5%2Ctabid-7%2Ctabid-1%2Ctabid-3#Syncfusion_UI_Xaml_Charts_ChartBase_Legend) property of the chart was used to enable it.

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

## Enable Tooltip

Tooltips are used to show information about the segment, when mouse over on it. Enable tooltip by setting series [EnableTooltip](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeries.html?tabs=tabid-24%2Ctabid-22%2Ctabid-4%2Ctabid-11%2Ctabid-6%2Ctabid-18%2Ctabid-8%2Ctabid-13%2Ctabid-15%2Ctabid-17%2Ctabid-1%2Ctabid-3%2Ctabid-10%2Ctabid-20#Syncfusion_UI_Xaml_Charts_ChartSeries_EnableTooltip) property as true.

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

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/GettingStartedChartWinUI/tree/main/CircularChartGettingStarted)
