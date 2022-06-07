---
layout: post
title: Getting Started with WinUI Chart control | Syncfusion
description: Learn here all about getting started with Syncfusion WinUI Chart (SfChart) control, its elements, and more.
platform: WinUI
control: Chart
documentation: ug
---

# Getting Started with WinUI Chart

This section explains you the steps required to populate the chart with data, header, add data labels, legend, and tooltips. This section covers only the minimal features that you need to learn to get started with the chart.

## Creating an application with WinUI chart
1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop).
2.	Add reference to [Syncfusion.Chart.WinUI](https://www.nuget.org/packages/Syncfusion.Chart.WinUI/) NuGet. 
3.	Import the control namespace `Syncfusion.UI.Xaml.Charts` in XAML or C# to initialize the control.
4.	Initialize `SfChart` control.

{% tabs %} 

{% highlight xaml %}

<Page
    x:Class="SfChart_GettingStarted.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:SfChart_GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:syncfusion="using:Syncfusion.UI.Xaml.Charts"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d" Height="350" Width="525"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
    <Grid>
        <syncfusion:SfChart />            
    </Grid>
</Page>
 
{% endhighlight %}

{% highlight C# %} 

using Syncfusion.UI.Xaml.Charts;

namespace SfChart_GettingStarted
{
    public sealed partial class MainPage : Page
    {
        public MainPage()
        {
            InitializeComponent();
            
            SfChart chart = new SfChart();      
            Root_Chart.Children.Add(chart);
        }
    }   
}

{% endhighlight %}

{% endtabs %}

## Initialize chart axis
`Chart` supports default axes, so that these axes ([PrimaryAxis](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfChart.html#Syncfusion_UI_Xaml_Charts_SfChart_PrimaryAxis) and [SecondaryAxis](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfChart.html#Syncfusion_UI_Xaml_Charts_SfChart_SecondaryAxis)) will get generated automatically based on the data binded to the chart.

Axes will be explicitly specified for the customization purpose. The initialization of an empty chart with two axes as shown in the following code sample.

{% tabs %} 

{% highlight xaml %} 

<syncfusion:SfChart> 
      <syncfusion:SfChart.PrimaryAxis> 
           <syncfusion:CategoryAxis /> 
      </syncfusion:SfChart.PrimaryAxis> 
      <syncfusion:SfChart.SecondaryAxis> 
           <syncfusion:NumericalAxis/> 
      </syncfusion:SfChart.SecondaryAxis>
</syncfusion:SfChart>

{% endhighlight %}

{% highlight C# %} 

SfChart chart = new SfChart();
CategoryAxis primaryAxis = new CategoryAxis();
chart.PrimaryAxis = primaryAxis;    
NumericalAxis secondaryAxis = new NumericalAxis();
chart.SecondaryAxis = secondaryAxis;

{% endhighlight %}

{% endtabs %} 

Run the project and check if you get the following output to ensure you have configured your project properly to add a chart.

![Initializing WinUI Chart](Getting-Started_Images/img1.png)

## Initialize view model

Now, let us define a simple data model that represents a data point in the chart.

{% tabs %}  

{% highlight c# %}

public class Person   
{   
    public string Name { get; set; }

    public double Height { get; set; }
}

{% endhighlight %} 

{% endtabs %} 


Next, create a view model class and initialize a list of `Person` objects as follows.

{% tabs %}  

{% highlight c# %}

public class ViewModel  
{
      public List<Person> Data { get; set; }      

      public ViewModel()       
      {
            Data = new List<Person>()
            {
                new Person { Name = "David", Height = 180 },
                new Person { Name = "Michael", Height = 170 },
                new Person { Name = "Steve", Height = 160 },
                new Person { Name = "Joel", Height = 182 }
            }; 
       }
 }

{% endhighlight %} 

{% endtabs %} 

Set the `ViewModel` instance as the `DataContext` of your window; this is done to bind properties of `ViewModel` to  the chart.
 
N> If you prefer to set the 'DataContext' in XAML, add the namespace of the 'ViewModel' class to your XAML Page.

{% tabs %} 

{% highlight xaml %} 

<Page
    x:Class="SfChart_GettingStarted.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:SfChart_GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:syncfusion="using:Syncfusion.UI.Xaml.Charts"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d" Height="350" Width="525"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

    <Page.DataContext>
        <local:ViewModel></local:ViewModel>
    </Page.DataContext>
</Page>

{% endhighlight %}

{% highlight C# %} 

this.DataContext = new ViewModel();

{% endhighlight %}

{% endtabs %} 

## Populate chart with data

As we are going to visualize the comparison of heights in the data model, add [ColumnSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ColumnSeries.html) to [Series](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfChart.html#Syncfusion_UI_Xaml_Charts_SfChart_Series) property of chart, and then bind the `Data` property of the above `ViewModel` to the `ColumnSeries.ItemsSource` as follows.

N> You need to set [XBindingPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_XBindingPath) and [YBindingPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.XyDataSeries.html#Syncfusion_UI_Xaml_Charts_XyDataSeries_YBindingPath) properties, so that chart would fetch values from the respective properties in the data model to plot the series.

{% tabs %}   

{% highlight xaml %}

<syncfusion:SfChart>
    <syncfusion:SfChart.PrimaryAxis>
        <syncfusion:CategoryAxis Header="Name" />
    </syncfusion:SfChart.PrimaryAxis>
    <syncfusion:SfChart.SecondaryAxis>
        <syncfusion:NumericalAxis Header="Height(in cm)"/>
    </syncfusion:SfChart.SecondaryAxis>    
    <syncfusion:ColumnSeries  ItemsSource="{Binding Data}"
                              XBindingPath="Name"
                              YBindingPath="Height">
    </syncfusion:ColumnSeries>

 </syncfusion:SfChart> 

{% endhighlight %}

{% highlight C# %}

SfChart chart = new SfChart();

//Adding horizontal axis to the chart 
CategoryAxis primaryAxis = new CategoryAxis();
primaryAxis.Header = "Name";   
chart.PrimaryAxis = primaryAxis;

//Adding vertical axis to the chart 
NumericalAxis secondaryAxis = new NumericalAxis();
secondaryAxis.Header = "Height(in cm)";  
chart.SecondaryAxis = secondaryAxis;

//Initialize the two series for SfChart
ColumnSeries series = new ColumnSeries();

series.ItemsSource = (new ViewModel()).Data;
series.XBindingPath = "Name";            
series.YBindingPath = "Height";         
            
//Adding Series to the Chart Series Collection
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %} 

## Add a title

The header of the chart acts as the title to provide quick information to the user about the data being plotted in the chart. You can set the title using the [Header](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_Header) property of the chart as follows.

{% tabs %} 

{% highlight xaml %}

<Grid>
   <syncfusion:SfChart Header="Chart"> 
   </syncfusion:SfChart> 
</Grid>

{% endhighlight %}

{% highlight C# %} 

chart.Header = "Chart";

{% endhighlight %}

{% endtabs %}  


## Enable data labels

The [ShowDataLabels](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataMarkerSeries.html#Syncfusion_UI_Xaml_Charts_DataMarkerSeries_ShowDataLabels) property of series can be used to enable the data labels to improve the readability of the chart. The label visibility is set to `False` by default.

{% tabs %} 

{% highlight xaml %}

<syncfusion:SfChart>
    . . . 
    <syncfusion:ColumnSeries ShowDataLabels="True">
    </syncfusion:ColumnSeries>

</syncfusion:SfChart>

{% endhighlight %}

{% highlight C# %}

SfChart chart = new SfChart();
. . .
ColumnSeries series = new ColumnSeries();
series.ShowDataLabels = true;
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}   

## Enable legend

You can enable legend using the [Legend](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartBase.html#Syncfusion_UI_Xaml_Charts_ChartBase_Legend) property as follows.

{% tabs %} 

{% highlight xaml %}

<syncfusion:SfChart>
	...
    <syncfusion:SfChart.Legend>
        <syncfusion:ChartLegend/>
    </syncfusion:SfChart.Legend>
    ...
</syncfusion:SfChart>

{% endhighlight %}

{% highlight C# %} 

chart.Legend = new ChartLegend (); 

{% endhighlight %}

{% endtabs %}  

Additionally, you need to set label for each series using the [Label](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_Label) property of ChartSeries, which will be displayed in corresponding legend.

{% tabs %} 

{% highlight xaml %}

<syncfusion:SfChart>
	...
      <syncfusion:ColumnSeries Label="Heights" ItemsSource="{Binding Data}" XBindingPath="Name" YBindingPath="Height" />
	...
</syncfusion:SfChart>

{% endhighlight %}

{% highlight C# %} 

ColumnSeries series = new ColumnSeries (); 
series.ItemsSource = (new ViewModel()).Data;
series.XBindingPath = "Name"; 
series.YBindingPath = "Height"; 
series.Label = "Heights";

{% endhighlight %}

{% endtabs %}  

## Enable tooltip

Tooltips show information about the segment when you click on it. You can enable the tooltip by setting series [ShowTooltip](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_ShowTooltip) property to true.

{% tabs %} 

{% highlight xaml %}

<syncfusion:SfChart>
	...
   <syncfusion:ColumnSeries ShowTooltip="True" ItemsSource="{Binding Data}" XBindingPath="Name" YBindingPath="Height"/>
	...
</syncfusion:SfChart> 

{% endhighlight %}

{% highlight C# %} 

ColumnSeries series = new ColumnSeries();
series.ItemsSource = (new ViewModel()).Data;
series.XBindingPath = "Name";          
series.YBindingPath = "Height";
series.ShowTooltip = true;

{% endhighlight %}

{% endtabs %}

The following code example gives you the complete code of above configurations.

{% tabs %} 

{% highlight xaml %}

<Page
    x:Class="SfChart_GettingStarted.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:SfChart_GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:syncfusion="using:Syncfusion.UI.Xaml.Charts"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d" Height="350" Width="525"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <!--Setting DataContext-->
    <Page.DataContext>
        <local:ViewModel></local:ViewModel>
    </Page.DataContext>

    <Grid>
        <syncfusion:SfChart Header="Chart">
            <!--Initialize the horizontal axis for SfChart-->
            <syncfusion:SfChart.PrimaryAxis>
                <syncfusion:CategoryAxis Header="Name" />
            </syncfusion:SfChart.PrimaryAxis>
            <syncfusion:SfChart.SecondaryAxis>
                <syncfusion:NumericalAxis Header="Height(in cm)"/>
            </syncfusion:SfChart.SecondaryAxis>

            <!--Adding Legend to the SfChart-->
            <syncfusion:SfChart.Legend>
                <syncfusion:ChartLegend />
            </syncfusion:SfChart.Legend>

            <!--Initialize the series for SfChart-->
            <syncfusion:ColumnSeries  ItemsSource="{Binding Data}"
                                      XBindingPath="Name"
                                      YBindingPath="Height"
                                      Label="Heights"
                                      ShowTooltip="True"
                                      ShowDataLabels="True">
                   <!--Add data label to the series-->     
                        <syncfusion:ColumnSeries.DataLabelSettings>
                            <syncfusion:CartesianDataLabelSettings Position="Inner"/>
                        </syncfusion:ColumnSeries.DataLabelSettings>
                    </syncfusion:ColumnSeries>               
            </syncfusion:ColumnSeries>          

        </syncfusion:SfChart>
    </Grid>
</Page>

 
{% endhighlight %}

{% highlight C# %} 

using Syncfusion.UI.Xaml.Charts;

namespace SfChart_GettingStarted
{
    public sealed partial class MainPage : Page
    {
        public MainPage()
        {
            InitializeComponent();
            
            SfChart chart = new SfChart() { Header = "Chart", Height = 300, Width = 500 };

            //Adding horizontal axis to the chart 
            CategoryAxis primaryAxis = new CategoryAxis();
            primaryAxis.Header = "Name";
            primaryAxis.FontSize = 14;
            chart.PrimaryAxis = primaryAxis;

            //Adding vertical axis to the chart 
            NumericalAxis secondaryAxis = new NumericalAxis();
            secondaryAxis.Header = "Height(in cm)";
            secondaryAxis.FontSize = 14;
            chart.SecondaryAxis = secondaryAxis;

            //Adding Legends for the chart
            ChartLegend legend = new ChartLegend();
            chart.Legend = legend;

            //Initializing column series
            ColumnSeries series = new ColumnSeries();
            series.ItemsSource = (new ViewModel()).Data;
            series.XBindingPath = "Name";            
            series.YBindingPath = "Height";
            series.ShowTooltip = true;
            series.Label = "Heights"; 
            series.ShowDataLabels = true;
            series.DataLabelSettings = new CartesianDataLabelSettings()
            {
                Position = DataLabelPosition.Inner,
            };

            //Adding Series to the Chart Series Collection
            chart.Series.Add(series);
            Root_Chart.Children.Add(chart);    
        }
    }   
}

{% endhighlight %}

{% endtabs %}

The following chart is created as a result of the previous codes.

![Getting Started WinUI Chart](Getting-Started_images/img3.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/GettingStartedChartWinUI).

N> For groundbreaking feature representations, please visit our [WinUI Charts](https://www.syncfusion.com/winui-controls/charts) feature tour page. You can also explore our [WinUI Charts example](https://github.com/syncfusion/winui-demos/tree/master/chart), which shows how to render various chart types as well as to configure with built-in support for creating stunning visual effects.