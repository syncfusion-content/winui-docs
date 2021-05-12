---
layout: post
title: Labels in WinUI Slider control | Syncfusion
description: Learn here all about Labels feature of Syncfusion WinUI Slider(SfSlider) control with label placement and more.
platform: WinUI
control: SfSlider
documentation: ug
---

# Labels in WinUI Slider

This section explains about how to show the labels in the slider.

## Show Labels

The [`ShowLabels`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowLabels) property is used to render the labels on [`Interval`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Interval). The default value of [`ShowLabels`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowLabels) property is false.

{% tabs %}

{% highlight xaml %}

<slider:SfSlider ShowLabels="True"
                 Value="50" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowLabels = true;
sfSlider.Value = 50;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![WinUI Slider with Labels](images/labels/winui-slider-labels.png)

## Maximum number of labels per 100 logical pixels

By default, a maximum of three labels are displayed for each 100 logical pixels in slider. The maximum number of labels that should present within 100 logical pixels length can be customized using the [`MaximumLabelsCount`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_MaximumLabelsCount) property of the slider. This property is applicable only for automatic range calculation and will not work, if you set value for [`Interval`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Interval) property of a RangeSlider.

{% tabs %}

{% highlight xaml %}

<slider:SfSlider Value="50"
                 MaximumLabelsCount="1"
                 ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.MaximumLabelsCount = 1;
sfSlider.Value = 50;
sfSlider.ShowLabels = true;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![WinUI Slider displays Maximum Labels Count](images/labels/winui-slider-maximum-labels-count.png)

## Label Placement

The [`labelPlacement`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_LabelPlacement) property is used to place the labels either before or after the track. The default value of the [`labelPlacement`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_LabelPlacement) property is [`Placement.After`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.Placement.html#Syncfusion_UI_Xaml_Sliders_Placement_After).

{% tabs %}

{% highlight xaml %}

<slider:SfSlider ShowLabels="True"
                 Value="50"
                 LabelPlacement="Before" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowLabels = true;
sfSlider.Value = 50;
sfSlider.LabelOffset = Placement.Before;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Customizing Labels Position of WinUI Slider](images/labels/winui-slider-label-position.png)

## Label Offset

You can adjust the space between ticks and labels of the slider using the [`LabelOffset`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_LabelOffset) property. The default value of [`LabelOffset`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_LabelOffset) property is 5.

{% tabs %}

{% highlight xaml %}

<slider:SfSlider ShowTicks="True"
                 ShowLabels="True"
                 Value="50"
                 LabelOffset="10" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowTicks = true;
sfSlider.ShowLabels = true;
sfSlider.LabelOffset = 10;
sfSlider.Value = 50;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![customizing Label offset of WinUI Slider](images/labels/winui-slider-label-offset.png)

## Label Template

**Setting a Template for Labels**

The [`LabelTemplate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_LabelTemplate) property allows you to define the data template for the label’s as shown in the following code sample.

{% tabs %}

{% highlight xaml %}

<DataTemplate x:Key="TrackLabelTemplate">
    <Grid CornerRadius="5"
          Background="{ThemeResource SystemBaseLowColor}">
        <TextBlock Text="{Binding Text}"
                   Margin="6" />
    </Grid>
</DataTemplate>

<slider:SfSlider ShowLabels="True"
                 LabelOffset="15"
                 LabelTemplate="{StaticResource TrackLabelTemplate}"
                 Value="50" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowLabels = true;
sfSlider.LabelOffset = 15;
sfSlider.LabelTemplate = this.Resources["TrackLabelTemplate"] as DataTemplate;
sfSlider.Value = 50;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Customizing Label Template of WinUI Slider](images/labels/winui-slider-label-template.png)

N> Its DataContext is [`SliderLabelInfo`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderLabelInfo.html?tabs=tabid-1).

**Setting Active Template for Labels**

The [`ActiveLabelTemplate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ActiveLabelTemplate) property allows you to define the data template for the active label’s as shown in the following code sample.

{% tabs %}

{% highlight xaml %}

<DataTemplate x:Key="ActiveTrackLabelTemplate">
    <TextBlock Text="{Binding Text}"
               Foreground="{ThemeResource SystemAccentColor}" />
</DataTemplate>

<slider:SfSlider ShowLabels="True"
                 LabelOffset="10"
                 ActiveLabelTemplate="{StaticResource ActiveTrackLabelTemplate}"
                 Value="50" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowLabels = true;
sfSlider.LabelOffset = 10;
sfSlider.ActiveLabelTemplate = this.Resources["ActiveTrackLabelTemplate"] as DataTemplate;
sfSlider.Value = 50;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Customizing Active Label Template of WinUI Slider](images/labels/winui-slider-active-label-template.png)

N> Its DataContext is [`SliderLabelInfo`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderLabelInfo.html?tabs=tabid-1).

**Formating Track Labels using Label Template**

By adding `Converters` in [`LabelTemplate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_LabelTemplate), you can customize the format of the track labels or display the custom text.

{% tabs %}

{% highlight xaml %}

<DataTemplate x:Key="LabelTemplate">
    <TextBlock Text="{Binding Value,
                              Converter={StaticResource FormatStringConverter},
                              ConverterParameter='N2'}" />
</DataTemplate>


<slider:SfSlider ShowLabels="True"
                 Interval="20"
                 LabelOffset="15"
                 LabelTemplate="{StaticResource LabelTemplate}"
                 Value="50" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowLabels = true;
sfSlider.Interval = 20;
sfSlider.LabelOffset = 15;
sfSlider.LabelTemplate = this.Resources["TLabelTemplate"] as DataTemplate;
sfSlider.Value = 50;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Customizing Label Format of WinUI Slider](images/labels/winui-slider-label-format.png)

N> Its DataContext is [`SliderLabelInfo`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderLabelInfo.html?tabs=tabid-1).
