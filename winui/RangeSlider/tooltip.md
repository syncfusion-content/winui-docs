---
layout: post
title: ToolTip in WinUI RangeSlider control | Syncfusion
description: Learn about ToolTip support in Syncfusion WinUI RangeSlider(SfRangeSlider) control with placement and more.
platform: WinUI
control: SfRangeSlider
documentation: ug
---

# ToolTip in WinUI RangeSlider (Range Slider)

This section explains how to add tooltips to the RangeSlider.

N> Refer to the [getting started](https://help.syncfusion.com/winui/rangeslider/getting-started) documentation for information on installing the NuGet package, adding namespace references, and adding the `SfRangeSlider` control to your application.

## Show Tooltip

You can enable tooltips for the thumbs using the [`ShowToolTip`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowToolTip) property of the RangeSlider. The tooltip is used to indicate the current selection value during interaction. The default value of the [`ShowToolTip`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowToolTip) property is true.

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ShowToolTip="True" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ShowToolTip = true;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with tooltip](images/tooltip/slider-tooltip.png)

## Tooltip Options

You can display a tooltip for either the active thumb or both thumbs (RangeStart and RangeEnd) using the [`ToolTipOption`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SfRangeSlider.html#Syncfusion_UI_Xaml_Sliders_SfRangeSlider_ToolTipOption) property of the RangeSlider. The default value of the [`ToolTipOption`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SfRangeSlider.html#Syncfusion_UI_Xaml_Sliders_SfRangeSlider_ToolTipOption) property is [`ToolTipOption.BothThumb`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.TooltipOption.html#Syncfusion_UI_Xaml_Sliders_TooltipOption_BothThumb). The available values are:

* [`ToolTipOption.ActiveThumb`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.TooltipOption.html#Syncfusion_UI_Xaml_Sliders_TooltipOption_ActiveThumb) – Displays the tooltip only on the active thumb.
* [`ToolTipOption.BothThumb`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.TooltipOption.html#Syncfusion_UI_Xaml_Sliders_TooltipOption_BothThumb) – Displays the tooltip on both thumbs.

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ToolTipOption="ActiveThumb" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ToolTipOption = ToolTipOption.ActiveThumb;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with tooltip option customization](images/tooltip/slider-tooltipoption.png)

## Tooltip Text Format

The [`ToolTipFormat`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipFormat) property allows you to customize the tooltip text using standard .NET numeric format strings. The default value of the [`ToolTipFormat`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipFormat) property is `N2`.

N> Refer to [standard numeric format strings](https://learn.microsoft.com/en-us/dotnet/standard/base-types/standard-numeric-format-strings) for the list of supported format specifiers (for example, `N`, `C`, `P`).

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ShowToolTip="True"
                      ToolTipFormat="c" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ShowToolTip = true;
sfRangeSlider.ToolTipFormat = "c";
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with tooltip format customization](images/tooltip/slider-tooltipformat.png)

## Tooltip Style

The [`ToolTipStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipStyle) property allows you to define the style for the range slider tooltip, as shown in the following code example. The default value of the [`ToolTipStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipStyle) property is null.

N> The `ToolTipStyle` only takes effect when the [`ShowToolTip`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowToolTip) property is set to true. The `slider:` prefix refers to the `Syncfusion.UI.Xaml.Sliders` namespace.

{% tabs %}

{% highlight xaml %}

<Style x:Key="ToolTipStyle"
       TargetType="slider:SliderToolTip">
    <Setter Property="Background"
            Value="#1257eb" />
    <Setter Property="Foreground"
            Value="White" />
</Style>

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ShowToolTip="True"
                      ToolTipStyle="{StaticResource ToolTipStyle}" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ShowToolTip = true;
sfRangeSlider.ToolTipStyle = this.Resources["ToolTipStyle"] as Style;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with tooltip style](images/tooltip/slider-tooltipstyle.png)

## Tooltip Template

The [`ToolTipTemplate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipTemplate) property allows you to define the data template for the range slider tooltip as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<DataTemplate x:Key="ToolTipTemplate">
    <StackPanel Orientation="Horizontal">
        <TextBlock Text="{Binding RangeStartValue}" />
        <TextBlock Text=":"
                   Margin="5,0,5,0" />
        <TextBlock Text="{Binding RangeEndValue}" />
    </StackPanel>
</DataTemplate>

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ShowToolTip="True"
                      ToolTipTemplate="{StaticResource ToolTipTemplate}" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ShowToolTip = true;
sfRangeSlider.ToolTipTemplate = this.Resources["ToolTipTemplate"] as DataTemplate;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with tooltip template](images/tooltip/slider-tooltiptemplate.png)

N> The tooltip template's DataContext is [`RangeSliderToolTipInfo`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.RangeSliderToolTipInfo.html), which exposes the `RangeStartValue` and `RangeEndValue` properties for binding.
