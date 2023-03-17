---
layout: post
title: Customization in WinUI AvatarView control | Syncfusion
description: Learn all about the customization features such as BorderThickness, BorderBrush, Background, FontSize and GradientBackground in WinUI AvatarView control here.
platform: WinUI
control: AvatarView
documentation: ug
---

# Customization in WinUI AvatarView 

The `AvatarView` control offers a range of customization options, including the ability to modify its colors, background, and more. You can utilize the following properties to customize this control:

## Border

Personalize the border of `AvatarView` control by adjusting the border brush and border thickness properties to achieve the desired look.

### BorderBrush

To set the color of the border surrounding your `AvatarView`, you can use the `BorderBrush` property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfAvatarView  ContentType="AvatarCharacter" 
                          AvatarCharacter="Avatar16"
                          AvatarSize="ExtraLarge"
                          BorderBrush="Red">
</syncfusion:SfAvatarView>

{% endhighlight %}
{% highlight c# %}

SfAvatarView avatarView = new SfAvatarView();
avatarView.ContentType = AvatarContentType.AvatarCharacter;
avatarView.AvatarShape = AvatarShape.Circle;
avatarView.AvatarSize = AvatarSize.ExtraLarge;
avatarView.AvatarCharacter = AvatarCharacter.Avatar16;
avatarView.BorderBrush = new SolidColorBrush(Colors.Red);

{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with custom BorderBrush](avatarview_images/winui_borderbrush_avatarview.png)

### Border Thickness

You can customize the thickness of the AvatarView control by using the `BorderThickness` property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfAvatarView   AvatarShape="Custom"
                           Width="100"
                           Height="100"
                           CornerRadius="50"
                           BorderBrush="Black" 
                           BorderThickness="4">
</syncfusion:SfAvatarView>

{% endhighlight %}
{% highlight c# %}

SfAvatarView avatarView = new SfAvatarView();
avatarView.AvatarShape = AvatarShape.Custom;
avatarView.Height = 100;
avatarView.Width = 100;
avatarView.BorderThickness = new Thickness(4);
avatarView.CornerRadius = new CornerRadius(50);
avatarView.BorderBrush = new SolidColorBrush(Colors.Black);

{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with custom BorderThickness](avatarview_images/winui_borderthickness_avatarview.png)

### Background

You can customize the background of the AvatarView control by using the `Background` property.
{% tabs %}
{% highlight xaml %}

<syncfusion:SfAvatarView ContentType="Initials"
                         AvatarSize="ExtraLarge"
                         AvatarName="Alex"
                         InitialsType="DoubleCharacter"
                         Background="Bisque">
</syncfusion:SfAvatarView>

{% endhighlight %}
{% highlight c# %}
          
SfAvatarView avatarView = new SfAvatarView();
avatarView.AvatarName = "Alex";
avatarView.ContentType = AvatarContentType.Initials;
avatarView.AvatarSize = AvatarSize.ExtraLarge;
avatarView.InitialsType = AvatarInitialsType.DoubleCharacter;
avatarView.Background = new SolidColorBrush(Colors.Bisque);

{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with custom background](avatarview_images/winui_double_character_initialstype_avatarview.png)

### Gradients

You can use the `LinearGradientBrush` in the `Background` property to specify a range of colors for your AvatarView, as shown in the following code example.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfAvatarView  ContentType="Initials" 
                          AvatarName="Alex"
                          AvatarSize="ExtraLarge"
                          InitialsType="DoubleCharacter">
            <syncfusion:SfAvatarView.Background>
                <LinearGradientBrush StartPoint="0,0"
                                     EndPoint="1,0">
                    <GradientStop Color="#2F9BDF" Offset="0"/>
                    <GradientStop Color="#51F1F2" Offset="1"/>
                </LinearGradientBrush>
            </syncfusion:SfAvatarView.Background>
</syncfusion:SfAvatarView>
  

{% endhighlight %}
{% highlight c# %}

SfAvatarView avatarView = new SfAvatarView();
avatarView.AvatarShape = AvatarShape.Circle;
avatarView.ContentType = AvatarContentType.Initials;
avatarView.AvatarSize = AvatarSize.ExtraLarge;
avatarView.InitialsType = AvatarInitialsType.DoubleCharacter;
avatarView.AvatarName = "Alex";
avatarView.Background = new LinearGradientBrush()
{
    StartPoint = new Point(0, 0),
    EndPoint = new Point(1, 0),
    GradientStops = new GradientStopCollection()
    {
        new GradientStop() { Color =  Color.FromArgb(255, 47, 155, 223), Offset = 0 },
        new GradientStop() { Color = Color.FromArgb(255, 81, 241, 242), Offset = 1 }
    }
};

{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with LinearGradientBrush](avatarview_images/winui_gradient_avatarview.png)