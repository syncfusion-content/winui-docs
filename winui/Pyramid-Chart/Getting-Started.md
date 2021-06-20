---
layout: post
title: Getting started with WinUI Pyramid Chart control | Syncfusion
description: This section explains about getting started with Syncfusion WinUI Pyramid Chart(SfPyramidChart) control
platform: WinUI
control: SfPyramidChart
documentation: ug
---

# Getting started with WinUI Pyramid Chart

This section explains you the steps required to populate the Chart with data, header, add data labels, legend and tooltips to the Chart. This section covers only the minimal features that you need to learn to get started with the Pyramid Chart.

## Creating an application with WinUI Pyramid Chart

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop) or [WinUI 3 app in UWP for C#](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp).
2. Add reference to [Syncfusion.Chart.WinUI](https://www.nuget.org/packages/Syncfusion.Chart.WinUI/) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Charts` in XAML or C# to initialize the control.
4. Initialize `SfPyramidChart` control.

{% tabs %} 

{% highlight xaml %}

<Window>
    x:Class="ChartDemo.MainWindow"

    . . .
    xmlns:chart="using:Syncfusion.UI.Xaml.Charts">
    <chart:SfPyramidChart/>

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
        SfPyramidChart chart = new SfPyramidChart();
        . . .
        this.Content = chart;
    }
}   

{% endhighlight %}

{% endtabs %}

## Initialize view model

Now, let us define a simple data model that represents a data point in the chart.

{% tabs %}  

{% highlight c# %}

public class Model
{
    public string FoodName { get; set; }

    public double Calories { get; set; }
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
            new Model(){FoodName = "Sweet Treats", Calories = 250},
            new Model(){FoodName = "Cheese", Calories = 402},
            new Model(){FoodName = "Vegetables", Calories = 65},
            new Model(){FoodName = "Fish", Calories = 206},
            new Model(){FoodName = "Fruits", Calories = 52},
            new Model(){FoodName = "Rice", Calories = 130},
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
    xmlns:Model="using:ChartDemo.ViewModel">

    <chart:SfPyramidChart>
        <chart:SfPyramidChart.DataContext>
            <Model:ChartViewModel/>
        </chart:SfPyramidChart.DataContext>
    </chart:SfPyramidChart>

</Window>

{% endhighlight %}

{% highlight C# %} 

ChartViewModel viewModel = new ChartViewModel();
chart.DataContext = viewModel;

{% endhighlight %}

{% endtabs %} 

## Add title

The title of the chart provide quick information to the user about the data being plotted in the chart. The title cane be set by using the [Header]() property of the pyramid chart as follows.

{% tabs %} 

{% highlight xaml %}

<chart:SfPyramidChart Header="Calories in food">
    
. . .

</chart:SfPyramidChart>

{% endhighlight %}

{% highlight C# %}

SfPyramidChart chart = new SfPyramidChart();

. . .

chart.Header = "Calories in food";

{% endhighlight %}

{% endtabs %}  

## Enable data labels

The [DataLabelSettings]() property of [PyramidChart]() can be used to enable data labels to improve the readability of the pyramid chart. By default, the label visibility is set to `False`.

{% tabs %} 

{% highlight xaml %}

<chart:SfPyramidChart>
. . .
    <chart:SfPyramidChart.DataLabelSettings>
        <chart:PyramidDataLabelSettings Visible="True" />
    </chart:SfPyramidChart.DataLabelSettings>
</chart:SfPyramidChart>

{% endhighlight %}

{% highlight C# %}

SfPyramidChart chart = new SfPyramidChart();

. . .

chart.DataLabelSettings = new PyramidDataLabelSettings() { Visible = true };

{% endhighlight %}

{% endtabs %}  

## Enable legend

The legend provides information about the data point displayed in the pyramid chart. The [Legend]() property of the chart was used to enable it.

{% tabs %} 

{% highlight xaml %}

<chart:SfPyramidChart>
    . . .
    <chart:SfPyramidChart.Legend>
        <chart:ChartLegend/>
    </chart:SfPyramidChart.Legend>
</chart:SfPyramidChart>

{% endhighlight %}

{% highlight C# %}

SfPyramidChart chart = new SfPyramidChart();
. . .
chart.Legend = new ChartLegend();

{% endhighlight %}

{% endtabs %} 

{% tabs %} 

## Enable tooltip

Tooltips are used to display information about a segment, when the mouse is moved over it. Enable tooltip by setting [ShowTooltip]() property as true.

{% tabs %} 

{% highlight xaml %}

<chart:SfPyramidChart ShowTooltip="True">
    . . . 
</chart:SfPyramidChart>

{% endhighlight %}

{% highlight C# %}

SfPyramidChart chart = new SfPyramidChart();
. . .
chart.ShowTooltip = true;

{% endhighlight %}

{% endtabs %}

The following code example gives you the complete code of above configurations.

{% tabs %} 

{% highlight xaml %}

<chart:SfPyramidChart x:Name="chart" 
                    Header="The Food Comparison Pyramid"
                    ShowTooltip="True"
                    Palette="BlueChrome"
                    ItemsSource="{Binding Data}" 
                    XBindingPath="FoodName"
                    YBindingPath="Calories">

    <chart:SfPyramidChart.DataContext>
        <model:ChartViewModel />
    </chart:SfPyramidChart.DataContext>

    <chart:SfPyramidChart.Legend>
        <chart:ChartLegend />
    </chart:SfPyramidChart.Legend>

    <chart:SfPyramidChart.DataLabelSettings>
        <chart:PyramidDataLabelSettings Visible="True" />
    </chart:SfPyramidChart.DataLabelSettings>

</chart:SfPyramidChart>
 
{% endhighlight %}

{% highlight C# %}

using Syncfusion.UI.Xaml.Charts;

. . .

public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        SfPyramidChart chart = new SfPyramidChart();
        ChartViewModel viewModel = new ChartViewModel();
        chart.DataContext = viewModel;
        chart.SetBinding(SfPyramidChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
        chart.XBindingPath = "FoodName";
        chart.YBindingPath = "Calories";
        chart.Header = "The Food Comparison Pyramid";
        chart.Legend = new ChartLegend();
        chart.ShowTooltip = true;
        chart.DataLabelSettings = new PyramidDataLabelSettings() { Visible = true };

        this.Content = chart;
    }
}

{% endhighlight %}

{% endtabs %}

N> To plot the chart, the [XBindingPath]() and [YBindingPath]() properties must be configured so that the chart may get values from the respective properties in the data model.

The following chart is created as a result of the previous codes.

![Getting started for WinUI Pyramid Chart](Getting-Started_images/WinUI_PyramidChart.png)

N> Download demo application from [GitHub]().

