---
layout: post
title: Getting Started with WinUI Chart | Syncfusion
description: This section explains the steps required to add the Chart control and binding data in chart control. This section covers only basic features needed to get started with Syncfusion chart control.
platform: WinUI
control: Chart
documentation: ug
---

# Getting Started with WinUI Chart control

This section explains you the steps required to populate the Chart with data, header, add data labels, legend and tooltips to the Chart. This section covers only the minimal features that you need to learn to get started with the Chart.

## Adding chart reference

Refer to the [Control Dependencies]() section to get the list of NuGet package that needs to be added as a reference to use the control in any application.

Refer to this [documentation]() to find more details about installing nuget packages in a WinUI application.

## Initialize chart

Import the chart namespace as follows in your respective page.

{% tabs %} 

{% highlight xaml %} 

xmlns:syncfusion="using:Syncfusion.UI.Xaml.Charts"

{% endhighlight %}

{% highlight C# %} 

using Syncfusion.UI.Xaml.Charts;

{% endhighlight %}

{% highlight VB %} 

Imports Syncfusion.UI.Xaml.Charts

{% endhighlight %}

{% endtabs %} 

Then initialize an empty chart with two axes as shown below,

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

{% highlight VB %}

Dim chart As New SfChart()

Dim primaryAxis As New CategoryAxis () 

chart.PrimaryAxis = primaryAxis 

Dim secondaryAxis As New NumericalAxis ()  

chart.SecondaryAxis = secondaryAxis

{% endhighlight %}

{% endtabs %} 

Run the project and check if you get following output to make sure you have configured your project properly to add chart.

![Initializing WinUI Chart](Getting-Started_Images/img1.png)

N> `Chart`supports default axes, so that these axes (`PrimaryAxis` and `SecondaryAxis`) will get generated automatically based upon the data bind to the chart, if you didn’t specify the axes explicitly.

## Initialize view model

Now, let us define a simple data model that represents a data point in chart.

{% tabs %}  

{% highlight c# %}

public class Person   
{   
    public string Name { get; set; }

    public double Height { get; set; }
}

{% endhighlight %} 

{% highlight VB %}

Public Class Person

    Public Property Name As String

    Public Property Height As Double

End Class

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


{% highlight VB %}

Public Class ViewModel

    Public Property Data As List(Of Person)

    Public Sub New()
        Data = New List(Of Person)() From
        {
            New Person With {.Name = "David", .Height = 180},
            New Person With {.Name = "Michael", .Height = 170},
            New Person With {.Name = "Steve", .Height = 160},
            New Person With {.Name = "Joel", .Height = 182}
        }
    End Sub
End Class

{% endhighlight %}

{% endtabs %} 

Set the `ViewModel` instance as the `DataContext` of your window; this is done to bind properties of `ViewModel` to  the chart.
 
N> Add namespace of `ViewModel` class to your XAML Page if you prefer to set `DataContext` in XAML.

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

{% highlight VB %} 

Me.DataContext = New ViewModel()

{% endhighlight %}

{% endtabs %} 

## Populate chart with data

As we are going to visualize the comparison of heights in the data model, add `ColumnSeries` to `SfChart.Series` property, and then bind the `Data` property of the above `ViewModel` to the `ColumnSeries.ItemsSource` as follows.

N> You need to set `XBindingPath`and `YBindingPath` properties, so that chart would fetch values from the respective properties in the data model to plot the series.

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

{% highlight VB %}

Dim chart As New SfChart()

'Adding horizontal axis to the chart 

Dim primaryAxis As New CategoryAxis()

primaryAxis.Header = "Name"
chart.PrimaryAxis = primaryAxis


'Adding vertical axis to the chart  

Dim secondaryAxis As New NumericalAxis()

secondaryAxis.Header = "Height(in cm)"

chart.SecondaryAxis = secondaryAxis        

'Initialize the two series for SfChart
Dim series As New ColumnSeries()

series.ItemsSource = New ViewModel().Demands
series.XBindingPath = "Name"
series.YBindingPath = "Height"
        
'Adding Series to the Chart Series Collection

chart.Series.Add(series)

{% endhighlight %}

{% endtabs %} 

## Add title

The header of the chart acts as the title to provide quick information to the user about the data being plotted in the chart. You can set title using the `Header` property of chart as follows.

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

{% highlight VB %}

chart.Header = "Chart"

{% endhighlight %}

{% endtabs %}  


## Enable data markers

You can add data labels to improve the readability of the chart and it can be enabled using `DataMarker` property of `ChartSeries`. By default, there is no label displayed, you have to set `ShowLabel` property of `ChartDataMarker` to True.

{% tabs %} 

{% highlight xaml %}

<syncfusion:SfChart>

	...
  <syncfusion:ColumnSeries > 
        <syncfusion:ColumnSeries.DataMarker>
            <syncfusion:ChartDataMarker LabelPosition="Inner" ShowLabel="True" />
        </syncfusion:ColumnSeries.DataMarker>
  </syncfusion:ColumnSeries>  
	...

</syncfusion:SfChart>

{% endhighlight %}

{% highlight C# %} 

series.DataMarker = new ChartDataMarker (){ ShowLabel = true }; 

{% endhighlight %}

{% highlight VB %} 

series.DataMarker = New ChartDataMarker() With {.ShowLabel = True} 

{% endhighlight %}

{% endtabs %}  

## Enable legend

You can enable legend using the `SfChart.Legend` property as follows.

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

{% highlight VB %} 

chart.Legend = New ChartLegend () 

{% endhighlight %}

{% endtabs %}  

Additionally, you need to set label for each series using the `Label` property of ChartSeries, which will be displayed in corresponding legend.

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

{% highlight VB %} 

Dim series As New ColumnSeries () 
series.ItemsSource = New ViewModel().Data
series.XBindingPath = "Name" 
series.YBindingPath = "Height" 
series.Label = "Heights"

{% endhighlight %}

{% endtabs %}  

## Enable tooltip

Tooltips are used to show information about the segment, when you click the segment. You can enable tooltip by setting series `ShowTooltip` property to true.

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

{% highlight VB %} 

Dim series As New ColumnSeries () 
series.ItemsSource = New ViewModel().Data
series.XBindingPath = "Name" 
series.YBindingPath = "Height" 
series.ShowTooltip = True

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
                                      ShowTooltip="True">
                   <!--Add data marker to the series-->                
                    <syncfusion:ColumnSeries.DataMarker>
                        <syncfusion:ChartDataMarker LabelPosition="Inner" ShowLabel="True" />
                    </syncfusion:ColumnSeries.DataMarker>               
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

            //Setting data marker to the chart series
            series.DataMarker = new ChartDataMarker() { ShowLabel = true };

            //Adding Series to the Chart Series Collection
            chart.Series.Add(series);
            this.Content = chart;
                      
        }
    }   
}

{% endhighlight %}

{% highlight VB %}

Imports Syncfusion.UI.Xaml.Charts
Partial Public Class MainPage
    Inherits Page   
    Public Sub New()
        InitializeComponent()

        Dim chart As New SfChart()
        chart.Header = "Chart"
        chart.Height = 300
        chart.Width = 500

        'Adding horizontal axis to the chart 

        Dim primaryAxis As New CategoryAxis()
        primaryAxis.Header = "Name"
        primaryAxis.FontSize = 14
        chart.PrimaryAxis = primaryAxis

        'Adding vertical axis to the chart  

        Dim secondaryAxis As New NumericalAxis()
        secondaryAxis.Header = "Height(in cm)"
        secondaryAxis.FontSize = 14
        chart.SecondaryAxis = secondaryAxis

        'Adding Legends for the chart
        Dim legend As New ChartLegend()
        chart.Legend = legend

        'Initializing column series
        Dim series As New ColumnSeries()
        series.ItemsSource = New ViewModel().Data
        series.XBindingPath = "Name"
        series.YBindingPath = "Height"
        series.Label = "Heights"
        series.ShowTooltip = True

        'Setting data marker to the chart series
        series.DataMarker = New ChartDataMarker() With {.ShowLabel = True}       

        'Adding Series to the Chart Series Collection

        chart.Series.Add(series)

        Me.Content = chart

    End Sub
End Class

{% endhighlight %}

{% endtabs %}

The following chart is created as a result of the previous codes.

![Getting Started WinUI Chart](Getting-Started_images/img3.png)

You can find the complete getting started sample from this [link](https://www.syncfusion.com/downloads/support/directtrac/general/ze/Chart_GettingStarted-1703269833.zip).

