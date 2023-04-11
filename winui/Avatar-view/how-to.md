---
layout: post
title: States in WinUI AvatarView control | Syncfusion
description: Learn about how to set the different states of badge for the WinUI AvatarView control(SfAvatarView).
platform: WinUI
control: AvatarView
documentation: ug
---

# How to use badge for WinUI AvatarView

The [SfAvatarView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html) control supports various [SfBadge](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBadge.html) states to notify users of new or unread messages, notifications, or status updates.

The following code explains how to set [SfBadge](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBadge.html) for [SfAvatarView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html).

{% tabs %}
{% highlight xaml %}

<notification:BadgeContainer>
      <notification:BadgeContainer.Content>
            <core:SfAvatarView AvatarSize="ExtraLarge"/>
      </notification:BadgeContainer.Content>
      <notification:BadgeContainer.Badge>
            <notification:SfBadge Shape="None" 
                                  HorizontalPosition="0.85"
                                  VerticalPosition="0.85">
                  <Viewbox Height="27" Width="27">
                        <Grid Height="13" Width="13">
                              <Ellipse x:Name="ellipse"
                                       Fill="LimeGreen"
                                       Stroke="{ThemeResource ApplicationPageBackgroundThemeBrush}"
                                       StrokeThickness="1">
                              </Ellipse>
                              <TextBlock x:Name="badgeTextBlock"
                                         FontFamily="{StaticResource SymbolThemeFontFamily}"
                                         Text="&#xE930;"
                                         Foreground="{ThemeResource ApplicationPageBackgroundThemeBrush}"
                                         HorizontalAlignment="Center"
                                         VerticalAlignment="Center">
                              </TextBlock>
                        </Grid>
                  </Viewbox> 
            </notification:SfBadge>
      </notification:BadgeContainer.Badge>
</notification:BadgeContainer>

{% endhighlight %}
{% highlight C# %}

BadgeContainer badgeContainer = new BadgeContainer();
badgeContainer.Content = new SfAvatarView() { AvatarSize = AvatarSize.ExtraLarge };
SfBadge badge = new SfBadge();
badgeContainer.Badge = badge;
badge.Shape = BadgeShape.None;
badge.HorizontalPosition = 0.85;
badge.VerticalPosition = 0.85;
Viewbox viewBox = new Viewbox() { Height = 27, Width = 27 };
Grid grid = new Grid() { Height = 13, Width = 13 };

Ellipse ellipse = new Ellipse();
ellipse.Fill = new SolidColorBrush(Colors.LimeGreen);
ellipse.Stroke = (Brush)Application.Current.Resources["ApplicationPageBackgroundThemeBrush"];
ellipse.StrokeThickness = 1;

TextBlock textBlock = new TextBlock();
textBlock.FontFamily = new FontFamily("Segoe MDL2 Assets");
textBlock.Text = "\xE930";
textBlock.Foreground = (Brush)Application.Current.Resources["ApplicationPageBackgroundThemeBrush"];
textBlock.HorizontalAlignment = HorizontalAlignment.Center;
textBlock.VerticalAlignment = VerticalAlignment.Center;

grid.Children.Add(ellipse);
grid.Children.Add(textBlock);
viewBox.Child = grid;
badge.Content = viewBox;
this.Content = badgeContainer;

{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with Badge](avatarview_images/winui_avatarview_with_badge.png)