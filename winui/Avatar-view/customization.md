---
layout: post
title: Customization in WinUI AvatarView control | Syncfusion
description: Learn about the various customization features in the WinUI AvatarView control, including border, background, gradient, font, and more.
platform: WinUI
control: AvatarView
documentation: ug
---

# Customization in WinUI AvatarView 

The `AvatarView` control offers a range of customization options, including modifying its border, background, and more.

## Border

Customize the `AvatarView` control border using the `BorderBrush` and `BorderThickness` properties.

**BorderBrush**

Customize the border color of the AvatarView control by using the `BorderBrush` property.

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
avatarView.AvatarSize = AvatarSize.ExtraLarge;
avatarView.AvatarCharacter = AvatarCharacter.Avatar16;
avatarView.BorderBrush = new SolidColorBrush(Colors.Red);

{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with custom BorderBrush](avatarview_images/winui_avatarview_borderbrush.png)

**BorderThickness**

Customize the border thickness of the AvatarView control by using the `BorderThickness` property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfAvatarView   AvatarShape="Custom"
                           AvatarSize="ExtraLarge"
                           BorderBrush="Black" 
                           BorderThickness="4">
</syncfusion:SfAvatarView>

{% endhighlight %}
{% highlight c# %}

SfAvatarView avatarView = new SfAvatarView();
avatarView.AvatarShape = AvatarShape.Custom;
avatarView.AvatarSize = AvatarSize.ExtraLarge;
avatarView.BorderThickness = new Thickness(4);
avatarView.BorderBrush = new SolidColorBrush(Colors.Black);

{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with custom BorderThickness](avatarview_images/winui_avatarview_borderthickness.png)

## Background

Customize the background of the AvatarView control by using the `Background` property.

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

## Gradient background

Use the `LinearGradientBrush` or `RadialGradientBrush` for the Background property to specify a range of colors to apply the gradient background for the AvatarView as shown in the following code example.

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

![WinUI AvatarView control with Gradient Background](avatarview_images/winui_avatarview_gradient.png)

## Font

Customize the font of initials in the `AvatarView` control by using the `FontFamily` and `Foreground` properties.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfAvatarView  ContentType="Initials" 
                          AvatarName="Alex"
                          AvatarSize="ExtraLarge"
                          FontFamily="Segoe UI Variable Static Display"
                          Foreground="#FF69531C"
                          Background="#FFF2E9C8">
</syncfusion:SfAvatarView>
  
{% endhighlight %}
{% highlight c# %}

SfAvatarView avatarView = new SfAvatarView();
avatarView.ContentType = AvatarContentType.Initials;
avatarView.AvatarName = "Alex";
avatarView.AvatarSize = AvatarSize.ExtraLarge;
avatarView.FontFamily = new FontFamily("Segoe UI Variable Static Display");
avatarView.Foreground = new SolidColorBrush(Color.FromArgb(0xFF, 0x69, 0x53, 0x1C));
avatarView.Background = new SolidColorBrush(Color.FromArgb(0xFF, 0xF2, 0xE9, 0xC8));

{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with custom font](avatarview_images/winui_avatarview_font.png)