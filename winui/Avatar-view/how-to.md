---
layout: post
title: States in WinUI AvatarView control | Syncfusion
description: Learn about using of the different states that exist in WinUi AvatarView control(SfAvatarView).
platform: WinUI
control: AvatarView
documentation: ug
---

# How to use different states

## Set badge to avatar

The `AvatarView` control provides support for `Badge` to notify users of new or unread messages, notifications, or the status of something.

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
                  <Viewbox Height="26" Width="26">
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
Viewbox viewBox = new Viewbox() { Height = 26, Width = 26 };
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

![WinUI AvatarView control with Badge](avatarview_images/winui_badge_avatarview.png)