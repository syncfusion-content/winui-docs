---
layout: post
title: Customization in WinUI AvatarView control | Syncfusion
description: Learn all about the customization features such as Height, Width, BorderBrush, Background, FontSize and CornerRadius in WinUI AvatarView control here.
platform: WinUI
control: AvatarView
documentation: ug
---

# Customization in WinUI AvatarView 

The `AvatarView` control provides options to customize the color, size ect. of the control. The control can be customized using the following properties:

## Colors

Colors in the `AvatarView` can be customized by the border brush and by the background color.

### BorderBrush

The `BorderBrush` property is used for setting color to the border color of `AvatarView`.

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

### Gradients

You can also specify a range of colors using `LinearGradientBrush` in `Background` Property as demonstrated in the following code example.

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

![WinUI AvatarView control with custom Gradient](avatarview_images/winui_gradient_avatarview.png)

## Sizing

In the `AvatarView` control, size of the view can be controlled using width, height, border thickness, and corner radius.

### Width

You can customize the width of the avatar view using the `Width` property only when the AvatarShape is `Custom`.

### Height

You can customize the height of the avatar view using the `Height` property only when the AvatarShape is `Custom`.

### Border Thickness

You can customize the thickness of the avatar view using the `BorderThickness` property.

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

### Corner radius

You can customize the corner radius of the avatar view using the `CornerRadius` property only when the AvatarShape is `Custom`.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfAvatarView  AvatarShape="Custom"
                          ImageSource="Michael.png"
                          BorderBrush="Black"
                          Width="75"
                          Height="75"
                          CornerRadius="0,0,34,34">
</syncfusion:SfAvatarView>

{% endhighlight %}

{% highlight c# %}

Grid mainGrid = new Grid();
SfAvatarView avatarView = new SfAvatarView();
avatarView.Width = 75;
avatarView.Height = 75;
avatarView.CornerRadius = new CornerRadius(0,0,34,34);
avatarView.ImageSource = new BitmapImage(new Uri("ms-appx:///Michael.png"));
avatarView.AvatarShape = AvatarShape.Custom;
avatarView.BorderBrush = new SolidColorBrush(Colors.Black);
mainGrid.Children.Add(avatarView);
page.Content = mainGrid;

{% endhighlight %}

{% endtabs %}

![WinUI AvatarView control with custom CornerRadius](avatarview_images/winui_cornerradius_avatarview.png)