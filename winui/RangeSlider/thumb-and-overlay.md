---
layout: post
title: Thumb and Thumb Overlay in WinUI RangeSlider control | Syncfusion
description: Learn about Thumb and Thumb Overlay support in Syncfusion WinUI RangeSlider(SfRangeSlider) control and more.
platform: WinUI
control: SfRangeSlider
documentation: ug
---

# Thumb and Thumb Overlay in WinUI RangeSlider (Range Slider)

This section explains how to customize the thumb and thumb overlay in the RangeSlider.

Thumb - It is one of the elements of RangeSlider, which is used to drag and change the selected values of the RangeSlider.
Thumb overlay - It is rendered around the thumb and it will be displayed, while interacting with thumb.

## Thumb Type

You can change the thumb type using the [`ThumbType`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ThumbType) property. The default value of [`ThumbType`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ThumbType) is [`ThumbType.Circle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.ThumbType.html#Syncfusion_UI_Xaml_Sliders_ThumbType_Circle).


{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ThumbType="Rectangle" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ThumbType = ThumbType.Oval;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with thumb type customization](images/thumb-and-overlay/slider-thumbtype.png)

## Thumb Height and Width

You can change the thumb height and width of the range slider using the [`ThumbHeight`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ThumbHeight) and [`ThumbWidth`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ThumbWidth) properties respectively. The default values of both properties are 22.

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ThumbHeight="30"
                      ThumbWidth="30"
                      ActiveTrackHeight="8"
                      InactiveTrackHeight="8" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ThumbHeight = 30;
sfRangeSlider.ThumbWidth = 30;
sfRangeSlider.ActiveTrackHeight = 8;
sfRangeSlider.InactiveTrackHeight = 8;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with thumb height and width customization](images/thumb-and-overlay/slider-thumbHeightWidth.png)

## Thumb Background

You can change the thumb background of the range slider using the [`ThumbBackground`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ThumbBackground) property.

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ThumbBackground="#2A934D" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ThumbBackground = new SolidColorBrush(ColorHelper.FromArgb(255, 42, 147, 77));;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with thumb background customization](images/thumb-and-overlay/slider-thumbbackground.png)

## Thumb Hover Background

You can change the thumb hover background of the range slider using the `SyncfusionSliderThumbBackgroundPointerOver` resource key.

{% tabs %}

{% highlight xaml %}

<Page.Resources>
    <SolidColorBrush x:Key="SyncfusionSliderThumbBackgroundPointerOver">#009688</SolidColorBrush>
</Page.Resources>

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ThumbBackground="#33b35c" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ThumbBackground = new SolidColorBrush(ColorHelper.FromArgb(255, 42, 147, 77));
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with thumb hover background customization](images/thumb-and-overlay/slider-thumbhoverbackground.png)

## Thumb Pressed Background

You can change the thumb pressed background of the range slider using the `SyncfusionSliderThumbBackgroundPressed` resource key.

{% tabs %}

{% highlight xaml %}

<Page.Resources>
    <SolidColorBrush x:Key="SyncfusionSliderThumbBackgroundPointerOver">#009688</SolidColorBrush>
    <SolidColorBrush x:Key="SyncfusionSliderThumbBackgroundPressed">#288e49</SolidColorBrush>
</Page.Resources>

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ThumbBackground="#33b35c" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ThumbBackground = new SolidColorBrush(ColorHelper.FromArgb(255, 42, 147, 77));
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with thumb pressed background customization](images/thumb-and-overlay/slider-thumbpressedbackground.png)

## Thumb Style

The [`ThumbStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ThumbStyle) property allows you to define the style for the thumb as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<coreconverters:FormatStringConverter x:Key="FormatStringConverter" />

<Style x:Name="thumbStyle"
       TargetType="Thumb">
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="Thumb">
                <Grid>
                    <Ellipse Height="{TemplateBinding Height}"
                             Width="{TemplateBinding Width}"
                             Fill="WhiteSmoke"
                             Stroke="{TemplateBinding Background}"
                             StrokeThickness="2" />
                    <TextBlock Text="{Binding Converter={StaticResource FormatStringConverter},
                                              ConverterParameter='N0'}"
                               FontSize="14"
                               Margin="0,0,0,2"
                               HorizontalTextAlignment="Center"
                               VerticalAlignment="Center" />
                </Grid>
            </ControlTemplate>
        </Setter.Value>
    </Setter>
</Style>
    
<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ShowToolTip="False"
                      ThumbHeight="30"
                      ThumbWidth="30"
                      ThumbStyle="{StaticResource thumbStyle}" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ShowToolTip = false;
sfRangeSlider.ThumbHeight = 30;
sfRangeSlider.ThumbHeight = 30;
sfRangeSlider.ThumbStyle = this.Resources["thumbStyle"] as Style;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with thumb style customization](images/thumb-and-overlay/slider-thumbstyle.png)

N> Its DataContext is current value of thumb.

## Thumb Overlay Radius

The [`ThumbOverlayRadius`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ThumbOverlayRadius) property allows you to define the radius for the overlay as shown in the following code example. The default value of [`ThumbOverlayRadius`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ThumbOverlayRadius) property is 0.

{% tabs %}

{% highlight xaml %}

<Style x:Name="thumbStyle"
       TargetType="Thumb">
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="Thumb">
                <Grid>
                    <Ellipse Fill="{ThemeResource SystemAccentColorDark1}" />
                </Grid>
            </ControlTemplate>
        </Setter.Value>
    </Setter>
</Style>

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ShowToolTip="False"
                      ThumbOverlayRadius="20" 
                      ThumbStyle="{StaticResource thumbStyle}" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ShowToolTip = false;
sfRangeSlider.ThumbOverlayRadius = 20;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with overlay radius customization](images/thumb-and-overlay/slider-thumboverlayradius.png)

## Thumb Overlay Fill

The [`ThumbOverlayFill`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ThumbOverlayFill) property allows you to define the fill color for the overlay as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<Style x:Name="thumbStyle"
       TargetType="Thumb">
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="Thumb">
                <Grid>
                    <Ellipse Fill="{ThemeResource SystemAccentColorDark1}" />
                </Grid>
            </ControlTemplate>
        </Setter.Value>
    </Setter>
</Style>

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ThumbOverlayFill="Red" 
                      ThumbOverlayRadius="10" 
                      ThumbStyle="{StaticResource thumbStyle}" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ThumbOverlayFill = new SolidColorBrush(Colors.Red);
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with overlay fill customization](images/thumb-and-overlay/slider-thumboverlayfill.png)

N> Overlay effects displayed with 0.3 opacity.

## Events

### ThumbDragStarted

The [`ThumbDragStarted`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ThumbDragStarted) event raised when the thumb drag is started.

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ThumbDragStarted="SfRangeSlider_ThumbDragStarted" />

{% endhighlight %}

{% highlight c# %}

private void SfRangeSlider_ThumbDragStarted(object sender, DragStartedEventArgs e)
{
    //Perform action here.
}

{% endhighlight %}

{% endtabs %}

### ThumbDragCompleted

The [`ThumbDragCompleted`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ThumbDragCompleted) event raised when the thumb drag is completed.

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ThumbDragCompleted="SfRangeSlider_ThumbDragCompleted" />

{% endhighlight %}

{% highlight c# %}

private void SfRangeSlider_ThumbDragCompleted(object sender, DragCompletedEventArgs e)
{
    //Perform action here.
}

{% endhighlight %}

{% endtabs %}
