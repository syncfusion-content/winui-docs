---
layout: post
title: Customization in WinUI Shadow control | Syncfusion
description: Learn here all about the customization features such as color, opacity, position, and blur radius in Syncfusion WinUI Shadow control.
platform: winui-controls
control: SfShadow
documentation: ug
---

# Customization in WinUI Shadow

This section explains the customization features available in the WinUI [Shadow] control.

## Applying Color for shadow

If you want to change the color of the shadow other than the default Color value, use the `Color` property. The default value of `Color` property is `Black` color with 25% alpha value.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfShadow>
    <Button Height="50" width="100" Content="Button"         
         CornerRadius="5">
    </Button>
</syncfusion:SfShadow>

{% endhighlight %}
{% highlight C# %}

   // Creating an instance of the Shadow control.
   SfShadow shadow = new SfShadow();
   shadow.Color = Color.FromArgb(125, 255, 0, 0);
   
   Button button = new Button();
   shadow.Content = button;
   shadow.Height = 50;
   shadow.width = 100;
   shadow.Content = "Button";

{% endhiglight %}
{% endtabs %}

![Color customization in shadow control in WinUI](Shadow_images/winui_shadow_color.png)

## Applying BlurRadius for shadow

If you want to change the blur radius of the shadow other than the default value, use the `BlurRadius` property. The default value of `BlurRadius` property is 8.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfShadow>
    <Button Height="50" width="100" Content="Button"         
         CornerRadius="5">
    </Button>
</syncfusion:SfShadow>

{% endhighlight %}
{% highlight C# %}

   SfShadow shadow = new SfShadow();
   shadow.BlurRadius = 10;
   
   Button button = new Button();
   shadow.Content = button;
   shadow.Height = 50;
   shadow.width = 100;
   shadow.Content = "Button";

{% endhiglight %}
{% endtabs %}

![BlurRadius customization in shadow control in WinUI](Shadow_images/winui_shadow_blurradius.png)

## Applying Offset for shadow

 If you want to change the offsetX position of the shadow other than the default value, use the `OffsetX` and `OffsetY` property. The default value of `OffsetX` and `OffsetY` property is 4.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfShadow>
    <Button Height="50" width="100" Content="Button"         
         CornerRadius="5">
    </Button>
</syncfusion:SfShadow>

{% endhighlight %}
{% highlight C# %}

   SfShadow shadow = new SfShadow();
   shadow.OffsetX = 12;
   shadow.OffsetY = 12;
   
   Button button = new Button();
   shadow.Content = button;
   shadow.Height = 50;
   shadow.width = 100;
   shadow.Content = "Button";

{% endhiglight %}
{% endtabs %}

![OffsetX and OffsetY position customization in shadow control in WinUI](Shadow_images/winui_shadow_offset.png)

## Applying CornerRadius for shadow

If you want to change the corner radius of the shadow other than the default value, use the `CornerRadius` property. The default value of `CornerRadius` property is 0.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfShadow>
    <Button Height="50" width="100" Content="Button"         
         CornerRadius="5">
    </Button>
</syncfusion:SfShadow>

{% endhighlight %}
{% highlight C# %}

   SfShadow shadow = new SfShadow();
   shadow.ShadowCornerRadius = 5;
   
   Button button = new Button();
   shadow.Content = button;
   shadow.Height = 50;
   shadow.width = 100;
   shadow.Content = "Button";

{% endhiglight %}
{% endtabs %}

![CornerRadius customization in shadow control in WinUI](Shadow_images/winui_shadow_cornerradius.png)