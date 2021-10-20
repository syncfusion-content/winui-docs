---
layout: post
title: Getting started with WinUI Chart control | Syncfusion
description: Learn here all about getting started with Syncfusion WinUI Chart(SfFunnelChart) control, its elements, and more.
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Getting Started with WinUI Chart

This section explains how to populate the [WinUI Funnel Chart](https://www.syncfusion.com/winui-controls/charts/winui-funnel-chart) with data, a header, data labels, legend, and tooltips, as well as the essential aspects for getting started with the chart.

## Creating an application with WinUI Chart

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop).
2. Add reference to [Syncfusion.Chart.WinUI](https://www.nuget.org/packages/Syncfusion.Chart.WinUI/) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Charts` in XAML or C# to initialize the control.
4. Initialize [SfFunnelChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html) control.

{% tabs %} 

{% highlight xaml %}

<Window>
    x:Class="ChartDemo.MainWindow"

    . . .
    xmlns:chart="using:Syncfusion.UI.Xaml.Charts">
    <chart:SfFunnelChart/>

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
        SfFunnelChart chart = new SfFunnelChart();
        . . .
        this.Content = chart;
    }
}   

{% endhighlight %}

{% endtabs %}

## Initialize View Model

Now, let us define a simple data model that represents a data point in the chart.

{% tabs %}  

{% highlight c# %}

public class Model
{
    public string Category { get; set; }

    public double Value { get; set; }
}

{% endhighlight %} 

{% endtabs %} 

Next, create a view model class and initialize a list of `Model` objects as follows.

{% tabs %}  

{% highlight c# %}

public class ChartViewModel
{
    public List<Model> Data { get; set; }

    public ChartViewModel()
    {
        Data = new List<Model>()
        {
            new Model(){Category = "Lava", Value = 50},
            new Model(){Category = "HP", Value = 30},
            new Model(){Category = "Moto", Value = 60},
            new Model(){Category = "Sony", Value = 50},
            new Model(){Category = "LG", Value = 45},
        };
    }
}

{% endhighlight %} 

{% endtabs %} 

Create a `ViewModel` instance and set it as the chart's `DataContext`. This enables property binding from the `ViewModel` class.

N> If you prefer to set `DataContext` in XAML, add the namespace of the `ViewModel` class to your XAML Page.

{% tabs %} 

{% highlight xaml %} 

<Window>
    . . .

    xmlns:chart="using:Syncfusion.UI.Xaml.Charts"
    xmlns:model="using:ChartDemo.ViewModel">

    <chart:SfFunnelChart>
        <chart:SfFunnelChart.DataContext>
            <model:ChartViewModel/>
        </chart:SfFunnelChart.DataContext>
    </chart:SfFunnelChart>

</Window>

{% endhighlight %}

{% highlight C# %} 

ChartViewModel viewModel = new ChartViewModel();
chart.DataContext = viewModel;

{% endhighlight %}

{% endtabs %} 

## Add Title

The title of the chart provide quick information to the user about the data being plotted in the chart. You can set the title using the [Header](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartBase.html#Syncfusion_UI_Xaml_Charts_ChartBase_Header) property of the funnel chart as follows.

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart Header="PRODUCT SALES">
    
. . .

</chart:SfFunnelChart>

{% endhighlight %}

{% highlight C# %}

SfFunnelChart chart = new SfFunnelChart();

. . .

chart.Header = "PRODUCT SALES";

{% endhighlight %}

{% endtabs %}  

## Enable Data Labels

The [ShowDataLabels](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_ShowDataLabels) property of [SfFunnelChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html) can be used to enable data labels to improve the readability of the funnel chart. The label visibility is set to `False` by default.

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart ShowDataLabels="True">
. . . 
</chart:SfFunnelChart>

{% endhighlight %}

{% highlight C# %}

SfFunnelChart chart = new SfFunnelChart();

. . .

chart.ShowDataLabels = true;

{% endhighlight %}

{% endtabs %}  

## Enable Legend

The legend provides information about the data point displayed in the funnel chart. The [Legend](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartBase.html#Syncfusion_UI_Xaml_Charts_ChartBase_Legend) property of the chart was used to enable it.

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart>
    . . .
    <chart:SfFunnelChart.Legend>
        <chart:ChartLegend/>
    </chart:SfFunnelChart.Legend>
</chart:SfFunnelChart>

{% endhighlight %}

{% highlight C# %}

SfFunnelChart chart = new SfFunnelChart();
. . .
chart.Legend = new ChartLegend();

{% endhighlight %}

{% endtabs %} 

## Enable Tooltip

Tooltips are used to display information about a segment, when the mouse is moved over it. Enable tooltip by setting funnel chart [ShowTooltip](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_ShowTooltip) property as true.

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart ShowTooltip="True">
    . . . 
</chart:SfFunnelChart>

{% endhighlight %}

{% highlight C# %}

SfFunnelChart chart = new SfFunnelChart();
. . .
chart.ShowTooltip = true;

{% endhighlight %}

{% endtabs %}

The following code example gives you the complete code of above configurations.

N> To plot the chart, the [XBindingPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_XBindingPath) and [YBindingPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_YBindingPath) properties must be configured so that the chart may get values from the respective properties in the data model.

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart" Header="PRODUCT SALES" 
                             ShowTooltip="True"
                             ShowDataLabels="True"
                             Palette="BlueChrome"
                             Height="388" Width="500" 
                             ItemsSource="{Binding Data}" 
                             XBindingPath="Category"
                             YBindingPath="Value">

        <chart:SfFunnelChart.DataContext>
            <model:ChartViewModel />
        </chart:SfFunnelChart.DataContext>

        <chart:SfFunnelChart.Legend>
            <chart:ChartLegend />
        </chart:SfFunnelChart.Legend>
            
</chart:SfFunnelChart>
 
{% endhighlight %}

{% highlight C# %}

using Syncfusion.UI.Xaml.Charts;

. . .

public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        SfFunnelChart chart = new SfFunnelChart();
        ChartViewModel viewModel = new ChartViewModel();
        chart.DataContext = viewModel;
        chart.SetBinding(SfFunnelChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
        chart.XBindingPath = "Category";
        chart.YBindingPath = "Value";
        chart.Header = "PRODUCT SALES";
        chart.Height = 388;
        chart.Width = 500;
        chart.Legend = new ChartLegend();
        chart.ShowTooltip = true;
        chart.ShowDataLabels = true;

        this.Content = chart;
    }
}

{% endhighlight %}

{% endtabs %}

![Getting Started in WinUI Chart](Getting-Started_Images/winui-chart.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/GettingStartedChartWinUI/tree/main/FunnelChartGettingStarted).

N> You can also explore our [WinUI Funnel Chart example](https://github.com/syncfusion/winui-demos/blob/master/chart/Views/Funnel%20And%20Pyramid%20Charts/FunnelChart.xaml) that shows how to easily configure with built-in support for creating stunning visual effects.