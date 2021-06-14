---
layout: post
title: Getting Started with WinUI Funnel Chart control | Syncfusion
description: Learn here all about getting started with Syncfusion WinUI Funnel Chart(SfFunnelChart) control, its elements, and more.
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Getting Started with WinUI Chart

## Creating an application with WinUI Chart
1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop) or [WinUI 3 app in UWP for C#](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp).
2.	Add reference to [Syncfusion.Chart.WinUI](https://www.nuget.org/packages/Syncfusion.Chart.WinUI/) NuGet. 
3.	Import the control namespace `Syncfusion.UI.Xaml.Charts`  in XAML or C# to initialize the control.
4.	Initialize SfChart control.

{% tabs %} 

{% highlight xaml %}

 
{% endhighlight %}

{% highlight C# %} 

{% endhighlight %}

{% endtabs %}

## Initialize view model

Now, let us define a simple data model that represents a data point in chart.

{% tabs %}  

{% highlight c# %}


{% endhighlight %} 

{% endtabs %} 


Next, create a view model class and initialize a list of `Person` objects as follows.

{% tabs %}  

{% highlight c# %}

public class ViewModel  
{

      public ViewModel()       
      {
           
       }
 }

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

{% endtabs %} 

## Populate chart with data

As we are going to visualize the comparison of heights in the data model, add [ColumnSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ColumnSeries.html) to [Series](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfChart.html#Syncfusion_UI_Xaml_Charts_SfChart_Series) property of chart, and then bind the `Data` property of the above `ViewModel` to the `ColumnSeries.ItemsSource` as follows.

N> You need to set [XBindingPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_XBindingPath) and [YBindingPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.XyDataSeries.html#Syncfusion_UI_Xaml_Charts_XyDataSeries_YBindingPath) properties, so that chart would fetch values from the respective properties in the data model to plot the series.

{% tabs %}   

{% highlight xaml %}


{% endhighlight %}

{% highlight C# %}


{% endhighlight %}

{% endtabs %} 

## Add title

The header of the chart acts as the title to provide quick information to the user about the data being plotted in the chart. You can set title using the [Header](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_Header) property of chart as follows.

{% tabs %} 

{% highlight xaml %}


{% endhighlight %}

{% highlight C# %} 


{% endhighlight %}

{% endtabs %}  


## Enable data markers

## Enable legend

You can enable legend using the [Legend](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartBase.html#Syncfusion_UI_Xaml_Charts_ChartBase_Legend) property as follows.

{% tabs %} 

{% highlight xaml %}

{% endhighlight %}

{% highlight C# %} 

{% endhighlight %}

{% endtabs %}  

## Enable tooltip

Tooltips are used to show information about the segment, when you click the segment. You can enable tooltip by setting series [ShowTooltip](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_ShowTooltip) property to true.

{% tabs %} 

{% highlight xaml %}


{% endhighlight %}

{% highlight C# %} 

{% endhighlight %}

{% endtabs %}

The following code example gives you the complete code of above configurations.

{% tabs %} 

{% highlight xaml %}
 
{% endhighlight %}

{% highlight C# %} 

{% endhighlight %}

{% endtabs %}

The following chart is created as a result of the previous codes.

N> Download demo application from [GitHub]()

