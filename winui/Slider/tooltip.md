---
layout: post
title: Tooltip features in Syncfusion WinUI Slider
description: This article describes about how to show tooltip, and customize its appearance of syncfusion Slider control in WinUI platform.
platform: WinUI
control: SfSlider
documentation: ug
---

# Tooltip features in Flutter slider

This section helps to learn about how to add tooltip in the slider.

## Show tooltip

You can enable tooltip for the thumb using `ShowToolTip` property of slider. It is used to clearly indicate the current selection of the value during interaction. The default value of `ShowToolTip` property is true.

{% tabs %}

{% highlight xml %}

<slider:SfSlider Value="50"
                 ShowToolTip="True" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.ShowToolTip = true;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with tooltip](images/tooltip/slider-tooltip.png)

## Tooltip text format

The `ToolTipFormat` property allows to customize the axis label with the globalized label format. The default value of `ToolTipFormat` property is N2.

{% tabs %}

{% highlight xml %}

<slider:SfSlider Value="50"
                 ShowToolTip="True"
                 ToolTipFormat="c" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.ShowToolTip = true;
sfSlider.ToolTipFormat = "c";
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with tooltip format customization](images/tooltip/slider-tooltipformat.png)

## Tooltip placement

The `ToolTipPlacement` property is used to place the tooltip either before or after the track. The default value of the `ToolTipPlacement` property is `Placement.Before`.

{% tabs %}

{% highlight xml %}

<slider:SfSlider Value="50"
                 ShowToolTip="True"
                 ToolTipPlacement="After" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.ShowToolTip = true;
sfSlider.ToolTipPlacement = Placement.After;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with tooltip placement customization](images/tooltip/slider-tooltipplacement.png)

## Tooltip style

The `ToolTipStyle` property allows you to define the style for the slider tooltip as shown in the following code example. The default value of `ToolTipStyle` property is null.

{% tabs %}

{% highlight xml %}

<Style x:Name="ToolTipStyle"
       TargetType="slider:SliderToolTip">
    <Setter Property="Background"
            Value="#1257eb" />
    <Setter Property="Foreground"
            Value="White" />
</Style>

<slider:SfSlider Value="50"
                 ShowToolTip="True"
                 ToolTipStyle="{StaticResource ToolTipStyle}" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.ShowToolTip = true;
sfSlider.ToolTipStyle = this.Resources["ToolTipStyle"] as Style;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with tooltip style](images/tooltip/slider-tooltipstyle.png)

## Tooltip template

The `ToolTipTemplate` property allows you to define the data template for the slider tooltip as shown in the following code example.

{% tabs %}

{% highlight xml %}

<DataTemplate x:Name="ToolTipTemplate">
    <StackPanel Orientation="Horizontal">
        <TextBlock Text="Current Value : "
                   Margin="0,0,5,0" />
        <TextBlock Text="{Binding ToolTipText}" />
    </StackPanel>
</DataTemplate>

<slider:SfSlider Value="50"
                 ShowToolTip="True"
                 ToolTipTemplate="{StaticResource ToolTipTemplate}" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.ShowToolTip = true;
sfSlider.ToolTipTemplate = this.Resources["ToolTipTemplate"] as DataTemplate;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with tooltip template](images/tooltip/slider-tooltiptemplate.png)

N> Its DataContext is `SliderToolTipInfo`.