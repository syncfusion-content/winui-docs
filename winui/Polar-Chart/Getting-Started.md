---
layout: post
title: Getting Started with WinUI Polar Chart control | Syncfusion
description: Learn here all about getting started with Syncfusion WinUI Chart(SfPolarChart) control, its elements, and more.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Getting Started with WinUI Polar Chart


## Creating an application with WinUI Polar Chart
1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop) or [WinUI 3 app in UWP for C#](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp).
2. Add reference to [Syncfusion.Chart.WinUI](https://www.nuget.org/packages/Syncfusion.Chart.WinUI/) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Charts`  in XAML or C# to initialize the control.
4. Initialize SfPolarChart control.

{% tabs %} 

{% highlight xaml %}

<Window
   x:Class="ChartDemo.MainWindow"
   ...
   xmlns:chart="using:Syncfusion.UI.Xaml.Charts">

<chart:SfPolarChart/>

 </Window>  
 
{% endhighlight %}

{% highlight C# %} 

using Syncfusion.UI.Xaml.Charts;

...
public sealed partial class MainWindow : Window
{
    
    public MainWindow()
    {
        this.InitializeComponent();
        SfPolarChart chart = new SfPolarChart();
        ...
        this.Content = chart;
    }
}

{% endhighlight %}

{% endtabs %}

## Initialize view model

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


Next, create a view model class and initialize a list of `Sales` objects as follows.

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
    ...
    xmlns:chart="using:Syncfusion.UI.Xaml.Charts"
    xmlns:Model="using:ChartDemo.ViewModel">

    <chart:SfPolarChart>
        <chart:SfPolarChart.DataContext>
            <Model:ChartViewModel/>
        </chart:SfPolarChart.DataContext>
    </chart:SfPolarChart>

</Window>

{% endhighlight %}

{% highlight C# %} 

ChartViewModel viewModel = new ChartViewModel();
chart.DataContext = viewModel;

{% endhighlight %}

{% endtabs %} 

## Initialize chart axis

`Chart`supports default axes, so that these axes ([PrimaryAxis]() and [SecondaryAxis]()) will get generated automatically based upon the data bind to the chart.

Axes will be explicitly specified for it's customization purpose. The initialization of an empty chart with two axes as shown below,

{% tabs %} 

{% highlight xaml %} 

<chart:SfPolarChart> 
      <chart:SfPolarChart.PrimaryAxis> 
           <chart:CategoryAxis /> 
      </chart:SfPolarChart.PrimaryAxis> 
      <chart:SfPolarChart.SecondaryAxis> 
           <chart:NumericalAxis/> 
      </chart:SfPolarChart.SecondaryAxis>
</chart:SfPolarChart>

{% endhighlight %}

{% highlight C# %} 

SfPolarChart chart = new SfPolarChart();
CategoryAxis primaryAxis = new CategoryAxis();
chart.PrimaryAxis = primaryAxis;    
NumericalAxis secondaryAxis = new NumericalAxis();
chart.SecondaryAxis = secondaryAxis;

{% endhighlight %}

{% endtabs %} 

Run the project and check if you get following output to make sure you have configured your project properly to add chart.

## Populate chart with data

Adding [PolarSeries]() to the chart [Series]() collection and binding `Data` to the series [ItemsSource]() property from its `DataContext` for creating our own Product – Sales Polar chart.

N> To plot the series, the [XBindingPath]() and [YBindingPath]() properties must be configured so that the chart may get values from the respective properties in the data model.

{% tabs %}   

{% highlight xaml %}

<chart:SfPolarChart>
. . .
    <chart:SfPolarChart.Series>
        <chart:PolarSeries ItemsSource="{Binding Data}" 
                         XBindingPath="Product" 
                         YBindingPath="SalesRate"/>
    </chart:SfPolarChart.Series>
</chart:SfPolarChart>
 

{% endhighlight %}

{% highlight C# %}

SfPolarChart chart = new SfPolarChart();

ChartViewModel viewModel = new ChartViewModel();
chart.DataContext = viewModel;

PolarSeries series = new PolarSeries();
series.XBindingPath = "Product";
series.YBindingPath = "SalesRate";

series.SetBinding(
    ChartSeriesBase.ItemsSourceProperty, 
    new Binding() 
    { Path = new PropertyPath("Data") });

chart.Series.Add(series);
. . .

{% endhighlight %}

{% endtabs %} 

## Add title

The header of the chart acts as the title to provide quick information to the user about the data being plotted in the chart. You can set title using the [Header]() property of chart as follows.

{% tabs %} 

{% highlight xaml %}

<chart:SfPolarChart Header="PRODUCT SALES"> 
...
</chart:SfPolarChart> 

{% endhighlight %}

{% highlight C# %} 

chart.Header = "PRODUCT SALES";

{% endhighlight %}

{% endtabs %}  


## Enable data labels

The [DataLabelSettings]() property of [PolarSeries]() can be used to enable data labels to improve the readability of the polar chart. The label visibility is set to `False` by default.

{% tabs %} 

{% highlight xaml %}

<chart:PolarSeries>
. . .
    <chart:PolarSeries.DataLabelSettings>
        <chart:PolarDataLabelSettings Visible="True"/>
    </chart:PolarSeries.DataLabelSettings>
</chart:PolarSeries>


{% endhighlight %}

{% highlight C# %} 

series.DataLabelSettings = new CircularChartDataLabelSettings() { Visible = true };

{% endhighlight %}

{% endtabs %}  

## Enable legend

The legend provides information about the data point displayed in the circular chart. The [Legend]() property of the chart was used to enable it.

{% tabs %} 

{% highlight xaml %}

<chart:SfPolarChart>
    . . .
    <chart:SfPolarChart.Legend>
        <chart:ChartLegend/>
    </chart:SfPolarChart.Legend>
</chart:SfPolarChart>


{% endhighlight %}

{% highlight C# %} 

SfPolarChart chart = new SfPolarChart();
. . .
chart.Legend = new ChartLegend();

{% endhighlight %}

{% endtabs %}  

N> Additionally, you need to set label for each series using the [Label]() property of ChartSeries, which will be displayed in corresponding legend.

{% tabs %} 

{% highlight xaml %}

<chart:SfPolarChart>
    . . .
    <chart:PolarSeries  ItemsSource="{Binding Data}" 
                        XBindingPath="Product" 
                        YBindingPath="SalesRate"
                        Label="Sales"/>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight C# %} 

...
PolarSeries series = new PolarSeries();
series.XBindingPath = "Product";
series.YBindingPath = "SalesRate";
series.Label = "Sales";
...

{% endhighlight %}

{% endtabs %}  

//Polar series tooltip whether need or having support confirm first
## Enable tooltip

Tooltips are used to show information about the segment, when mouse over on it. Enable tooltip by setting series [ShowTooltip]() property as true.

{% tabs %} 

{% highlight xaml %}

<chart:PolarSeries ShowTooltip="True">
    . . . 
</chart:PolarSeries>

{% endhighlight %}

{% highlight C# %} 

PolarSeries series = new PolarSeries();
. . .
series.ShowTooltip = true;

{% endhighlight %}

{% endtabs %}

The following code example gives you the complete code of above configurations.

{% tabs %} 

{% highlight xaml %}

<chart:SfPolarChart Header="PRODUCT SALES">
    <chart:SfPolarChart.DataContext>
        <Model:ChartViewModel/>
    </chart:SfPolarChart.DataContext>
    <chart:SfPolarChart.Legend>
        <chart:ChartLegend/>
    </chart:SfPolarChart.Legend>
    <chart:SfPolarChart.Series>
        <chart:PolarSeries ItemsSource="{Binding Data}" Label="Sales"
                         XBindingPath="Product" ShowTooltip="True"
                         YBindingPath="SalesRate">
            <chart:PolarSeries.DataLabelSettings>
                <chart:PolarDataLabelSettings Visible="True"/>
            </chart:PolarSeries.DataLabelSettings>
        </chart:PolarSeries>
    </chart:SfPolarChart.Series>
</chart:SfPolarChart>

{% endhighlight %}

{% highlight C# %} 

using Syncfusion.UI.Xaml.Charts;
. . .
public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        SfPolarChart chart = new SfPolarChart();

        chart.Header = "PRODUCT SALES";
        chart.Legend = new ChartLegend();
        ChartViewModel viewModel = new ChartViewModel();
        chart.DataContext = viewModel;

        PolarSeries series = new PolarSeries();
        series.XBindingPath = "Product";
        series.YBindingPath = "SalesRate";
        series.Label = "Sales";
        series.ShowTooltip = true;

        series.DataLabelSettings = new PolarDataLabelSettings() { Visible = true };

        series.SetBinding(
            ChartSeriesBase.ItemsSourceProperty, 
            new Binding() 
            { Path = new PropertyPath("Data") });

        chart.Series.Add(series);
        this.Content = chart;
    }
}

{% endhighlight %}

{% endtabs %}

The following chart is created as a result of the previous codes.


N> Download demo application from [GitHub]()

