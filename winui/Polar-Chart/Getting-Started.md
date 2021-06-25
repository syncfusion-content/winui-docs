---
layout: post
title: Getting Started with WinUI Chart control | Syncfusion
description: Learn here all about getting started with the Syncfusion WinUI Chart (SfPolarChart) control and its elements, and more.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Getting Started with WinUI Chart (SfPolarChart)

This section explains how to populate the polar chart with data, header, data labels, legend, and tooltips, as well as the essential aspects for getting started with the chart.

## Creating an application with WinUI Chart

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop) or [WinUI 3 app in UWP for C#](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp).
2. Add reference to [Syncfusion.Chart.WinUI](https://www.nuget.org/packages/Syncfusion.Chart.WinUI/) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Charts`  in XAML or C# to initialize the control.
4. Initialize [SfPolarChart]() control.

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

## Initialize View Model

Now, let us define a simple data model that represents a data point in chart.

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
    public ObservableCollection<Model> Data { get; set; }

    public ChartViewModel()
    {
        Data = new ObservableCollection<Model>()
        {
            new Model(){ Category = "North", Value = 80 },
            new Model(){ Category = "NorthWest", Value = 87.5 },
            new Model(){ Category = "West", Value = 79 },
            new Model(){ Category = "SouthWest", Value = 83 },
            new Model(){ Category = "South", Value = 77.5 },
            new Model(){ Category = "SouthEast", Value = 90 },
            new Model(){ Category = "East", Value = 77.5 },
            new Model(){ Category = "NorthEast", Value = 85 },
        };
    }
}

{% endhighlight %} 

{% endtabs %} 

Create a `ChartViewModel` instance and set it as the chart's `DataContext`. This enables property binding from the `ChartViewModel` class.
 
N> If you prefer to set `DataContext` in XAML, add the namespace of the `ViewModel` class to your XAML Page.

{% tabs %} 

{% highlight xaml %} 

<Window
    ...
    xmlns:chart="using:Syncfusion.UI.Xaml.Charts"
    xmlns:model="using:ChartDemo.ViewModel">

    <chart:SfPolarChart>
        <chart:SfPolarChart.DataContext>
            <model:ChartViewModel/>
        </chart:SfPolarChart.DataContext>
    </chart:SfPolarChart>

</Window>

{% endhighlight %}

{% highlight C# %} 

ChartViewModel viewModel = new ChartViewModel();
chart.DataContext = viewModel;
...

{% endhighlight %}

{% endtabs %} 

## Initialize Chart Axis

[ChartAxis]() is used to locate the data points inside the chart area. The [PrimaryAxis]() and [SecondaryAxis]() properties of the chart is used to initialize the axis for the chart.

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

## Populate Chart with Data

Adding [PolarAreaSeries]() to the polar chart [Series]() collection and binding `Data` to the series [ItemsSource]() property from its `DataContext` for creating polar chart.

N> To plot the series, the [XBindingPath]() and [YBindingPath]() properties must be configured so that the chart may get values from the respective properties in the data model.

{% tabs %}   

{% highlight xaml %}

<chart:SfPolarChart>
    <chart:SfPolarChart.PrimaryAxis> 
        <chart:CategoryAxis /> 
    </chart:SfPolarChart.PrimaryAxis> 
    <chart:SfPolarChart.SecondaryAxis> 
        <chart:NumericalAxis/> 
    </chart:SfPolarChart.SecondaryAxis>
    <chart:SfPolarChart.Series>
        <chart:PolarAreaSeries ItemsSource="{Binding Data}" 
                         XBindingPath="Category" 
                         YBindingPath="Value"/>
    </chart:SfPolarChart.Series>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight C# %}

SfPolarChart chart = new SfPolarChart();

ChartViewModel viewModel = new ChartViewModel();
chart.DataContext = viewModel;

CategoryAxis primaryAxis = new CategoryAxis();
chart.PrimaryAxis = primaryAxis;    
NumericalAxis secondaryAxis = new NumericalAxis();
chart.SecondaryAxis = secondaryAxis;

PolarAreaSeries series = new PolarAreaSeries();
series.XBindingPath = "Category";
series.YBindingPath = "Value";

series.SetBinding(
    ChartSeriesBase.ItemsSourceProperty, 
    new Binding() 
    { Path = new PropertyPath("Data") });

chart.Series.Add(series);
. . .

{% endhighlight %}

{% endtabs %} 

## Add Title

The title of the chart provide quick information to the user about the data being plotted in the chart. The [Header]() property is used to set title for polar chart as follows.

{% tabs %} 

{% highlight xaml %}

<chart:SfPolarChart Header="Polar Chart"> 
...
</chart:SfPolarChart> 

{% endhighlight %}

{% highlight C# %}

SfPolarChart chart = new SfPolarChart();
chart.Header = "Polar Chart";
...

{% endhighlight %}

{% endtabs %}  

## Enable Data Labels

The [ShowDataLabels]() property of series can be used to enable the data labels to improve the readability of the chart. The label visibility is set to `False` by default.

{% tabs %} 

{% highlight xaml %}

<chart:SfPolarChart>
    ...
    <chart:PolarAreaSeries ShowDataLabels="True"
                        ItemsSource="{Binding Data}" 
                        XBindingPath="Category" 
                        YBindingPath="Value">
    </chart:PolarAreaSeries>
</chart:SfPolarChart>

{% endhighlight %}

{% highlight C# %}

SfPolarChart chart = new SfPolarChart();
PolarAreaSeries series = new PolarAreaSeries();
series.ShowDataLabels = true;
...

{% endhighlight %}

{% endtabs %}  

## Enable Legend

The legend provides information about the data point displayed in the polar chart. The [Legend]() property of the chart was used to enable it.

{% tabs %} 

{% highlight xaml %}

<chart:SfPolarChart>
    ...
    <chart:SfPolarChart.Legend>
        <chart:ChartLegend/>
    </chart:SfPolarChart.Legend>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight C# %}

SfPolarChart chart = new SfPolarChart();
. . .
chart.Legend = new ChartLegend();

{% endhighlight %}

{% endtabs %}  

N> Additionally, set label for each series using the [Label]() property of chart series, which will be displayed in corresponding legend.

{% tabs %} 

{% highlight xaml %}

<chart:SfPolarChart>
    . . .
    <chart:PolarAreaSeries  ItemsSource="{Binding Data}" 
                        XBindingPath="Product" 
                        YBindingPath="SalesRate"
                        Label="Sales"/>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight C# %}

SfPolarChart chart = new SfPolarChart();
...
PolarAreaSeries series = new PolarAreaSeries();
series.XBindingPath = "Product";
series.YBindingPath = "SalesRate";
series.Label = "Sales";
...

{% endhighlight %}

{% endtabs %}  

The following code example gives you the complete code of above configurations.

{% tabs %} 

{% highlight xaml %}

<chart:SfPolarChart Header="Polar Chart">
    <chart:SfPolarChart.DataContext>
        <model:ChartViewModel/>
    </chart:SfPolarChart.DataContext>
    <chart:SfPolarChart.PrimaryAxis> 
           <chart:CategoryAxis /> 
      </chart:SfPolarChart.PrimaryAxis> 
      <chart:SfPolarChart.SecondaryAxis> 
           <chart:NumericalAxis/> 
      </chart:SfPolarChart.SecondaryAxis>
    <chart:SfPolarChart.Legend>
        <chart:ChartLegend/>
    </chart:SfPolarChart.Legend>
    <chart:SfPolarChart.Series>
        <chart:PolarAreaSeries ItemsSource="{Binding Data}" 
                         XBindingPath="Category"
                         YBindingPath="Value"
                         Label="Sales">
        </chart:PolarAreaSeries>
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

        chart.Header = "Polar Chart";
        chart.Legend = new ChartLegend();
        ChartViewModel viewModel = new ChartViewModel();
        chart.DataContext = viewModel;
        
        CategoryAxis primaryAxis = new CategoryAxis();
        chart.PrimaryAxis = primaryAxis;    
        NumericalAxis secondaryAxis = new NumericalAxis();
        chart.SecondaryAxis = secondaryAxis;

        PolarAreaSeries series = new PolarAreaSeries();
        series.XBindingPath = "Category";
        series.YBindingPath = "Value";
        series.Label = "Sales";

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

![Getting Started WinUI Chart](Getting-Started_images/WinUI_Chart.png)

N> Download demo application from [GitHub]()
