---
layout: post
title: Dividers in WinUI Slider control | Syncfusion
description: Learn here all about Dividers feature of Syncfusion WinUI Slider(SfSlider) control with height, width support and more.
platform: WinUI
control: SfSlider
documentation: ug
---

# Dividers in WinUI Slider

This section explains how to show the dividers in the slider.

## Show Dividers

The [`ShowDividers`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowDividers) property is used to render the dividers on the track. The default value of the [`ShowDividers`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowDividers) property is false. Dividers are shapes used to represent the major interval points of the track.

For example, if [`Minimum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Minimum) is 0, [`Maximum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Maximum) is 100, and [`Interval`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Interval) is 10, the slider will render the dividers at 0, 10, 20 and so on.

{% tabs %}

{% highlight xaml %}

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDividers="True" />

{% endhighlight %}

{% highlight c# %}

using Syncfusion.UI.Xaml.Sliders;

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.Interval = 10;
sfSlider.ShowDividers = true;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with dividers](images/dividers/slider-showDividers.png)

## Dividers Height and Width

You can change the divider height and width of the slider using the [`DividerHeight`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DividerHeight) and [`DividerWidth`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DividerWidth) properties respectively.

{% tabs %}

{% highlight xaml %}

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDividers="True"
                 DividerHeight="4"
                 DividerWidth="4" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.Interval = 10;
sfSlider.ShowDividers = true;
sfSlider.DividerHeight = 4;
sfSlider.DividerWidth = 4;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with divider height and width customization](images/dividers/slider-dividerHeightWidth.png)

## Divider Stroke Thickness and Stroke

You can change the divider stroke thickness of the slider using the [`DividerStrokeThickness`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DividerStrokeThickness) property. The default value of [`DividerStrokeThickness`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DividerStrokeThickness) is 0. Also, you can change the divider stroke of the slider using the [`DividerStroke`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DividerStroke) property.

{% tabs %}

{% highlight xaml %}

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDividers="True"
                 DividerHeight="10"
                 DividerWidth="10"
                 DividerStrokeThickness="2"
                 DividerStroke="Red" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.Interval = 10;
sfSlider.ShowDividers = true;
sfSlider.DividerHeight = 10;
sfSlider.DividerWidth = 10;
sfSlider.DividerStrokeThickness = 2;
sfSlider.DividerStroke = new SolidColorBrush(Colors.Red);
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with divider stroke customization](images/dividers/slider-dividerstroke.png)

## Divider Fill

You can change the divider fill of the slider using the [`DividerFill`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DividerFill) property. The default value of [`DividerFill`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DividerFill) is null.

{% tabs %}

{% highlight xaml %}

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDividers="True"
                 DividerHeight="10"
                 DividerWidth="10"
                 DividerFill="#ff7979" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.Interval = 10;
sfSlider.ShowDividers = true;
sfSlider.DividerHeight = 10;
sfSlider.DividerWidth = 10;
sfSlider.DividerFill = new SolidColorBrush(ColorHelper.FromArgb(255, 255, 121, 121));
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with divider fill customization](images/dividers/slider-dividerfill.png)

## Divider Template

### Setting a Template for Dividers

The [`DividerTemplate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DividerTemplate) property allows you to define the data template for the dividers as shown in the following code sample. The default value of [`DividerHeight`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DividerHeight) and [`DividerWidth`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DividerWidth) is 2.

{% tabs %}

{% highlight xaml %}

<DataTemplate x:Key="DividerTemplate">
    <Rectangle Height="{Binding DividerHeight}"
               Width="{Binding DividerWidth}"
               Fill="{ThemeResource SystemAltHighColor}"
               Stroke="{ThemeResource SystemAccentColorDark1}"
               StrokeThickness="{Binding DividerStrokeThickness}" />
</DataTemplate>

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDividers="True"
                 DividerHeight="10"
                 DividerWidth="10"
                 DividerStrokeThickness="2"
                 DividerTemplate="{StaticResource DividerTemplate}">
</slider:SfSlider>

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowDividers = true;
sfSlider.DividerHeight = 10;
sfSlider.DividerWidth = 10;
sfSlider.DividerStrokeThickness = 2;
sfSlider.DividerTemplate = this.Resources["DividerTemplate"] as DataTemplate;
sfSlider.Value = 50;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with divider template customization](images/dividers/slider-dividerTemplate.png)

N> The DataContext of the divider template is [`SliderBase`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html?tabs=tabid-1).

### Setting an Active Template for Dividers

The [`ActiveDividerTemplate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ActiveDividerTemplate) property allows you to define the data template for the active divider, i.e., the divider that is currently under the thumb, as shown in the following code sample.

{% tabs %}

{% highlight xaml %}

<DataTemplate x:Key="ActiveDividerTemplate">
    <Rectangle Height="10"
               Width="10"
               Fill="{ThemeResource SystemAltHighColor}"
               Stroke="{ThemeResource SystemAccentColorDark1}"
               StrokeThickness="2" />
</DataTemplate>

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDividers="True"
                 DividerHeight="5"
                 DividerWidth="5"
                 ActiveDividerTemplate="{StaticResource ActiveDividerTemplate}">
</slider:SfSlider>

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowDividers = true;
sfSlider.DividerHeight = 5;
sfSlider.DividerWidth = 5;
sfSlider.ActiveDividerTemplate = this.Resources["ActiveDividerTemplate"] as DataTemplate;
sfSlider.Value = 50;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with active divider template customization](images/dividers/slider-activeDividerTemplate.png)
