---
layout: post
title: Alignment and positioning of WinUI Badge control | Syncfusion
description: This section describes about how to align and positioning the Badge control into WinUI application and its basic features.
platform: WinUI
control: SfBadge
documentation: ug
---

# Alignment and positioning of WinUI Badge (SfBadge)

This section explains the alignment and positioning functionalities available in the WinUI [Badge](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBadge.html) control.

## Structure of Badge control

![Structure of WinUI Badge control](Getting-Started_images/Structure.png)

## Alignment of Badge

you can align the `Badge` either horizontally or vertically by using the `HorizontalAlignment` or `VerticalAlignment` properties. The default value of `HorizontalAlignment` property is `Right` and `VerticalAlignment` property is `Top`.

<table>

<tr>
<td class="invisible" ></td>
<th style="text-align:center" colspan = "4">HorizontalAlignment</th>
</tr>

<tr>
<th>VerticalAlignment</th>
<td>Left</td>
<td>Center</td>
<td>Right</td>
<td>Stretch</td>
</tr>

<tr>
<td>Top</td>
<td><img src="Getting-Started_images/Left-top.png" alt="Left-Top alignment of Badge"/></td>
<td><img src="Getting-Started_images/Center-Top.png" alt="Center-Top alignment of Badge"/></td>
<td><img src="Getting-Started_images/Right-Top.png" alt="Right-Top alignment of Badge"/></td>
<td><img src="Getting-Started_images/Stretch-Top.png" alt="Stretch-Top alignment of Badge"/></td>
</tr>

<tr>
<td>Center</td>
<td><img src="Getting-Started_images/Left-center.png" alt="Left-center alignment of Badge"/></td>
<td><img src="Getting-Started_images/Center-Center.png" alt="Center-Center alignment of Badge"/></td>
<td><img src="Getting-Started_images/Right-Center.png" alt="Right-Center alignment of Badge"/></td>
<td><img src="Getting-Started_images/Stretch-Center.png" alt="Stretch-Center alignment of Badge"/></td>
</tr>

<tr>
<td>Bottom</td>
<td><img src="Getting-Started_images/Left-Bottom.png" alt="Left-Bottom alignment of Badge"/></td>
<td><img src="Getting-Started_images/Center-Bottom.png" alt="Center-Bottom alignment of Badge"/></td>
<td><img src="Getting-Started_images/Right-Bottom.png" alt="Right-Bottom alignment of Badge"/></td>
<td><img src="Getting-Started_images/Stretch-Bottom.png" alt="Stretch-Bottom alignment of Badge"/></td>
</tr>

<tr>
<td>Stretch</td>
<td><img src="Getting-Started_images/Left-Stretch.png" alt="Left-Stretch alignment of Badge"/></td>
<td><img src="Getting-Started_images/Center-Stretch.png" alt="Center-Stretch alignment of Badge"/></td>
<td><img src="Getting-Started_images/Right-Stretch.png" alt="Right-Stretch alignment of Badge"/></td>
<td><img src="Getting-Started_images/Stretch-Stretch.png" alt="Stretch-Stretch alignment of Badge"/></td>
</tr>
</table>

{% tabs %}
{% highlight XAML %}

<syncfusion:BadgeContainer Name="badgeContainer"  >
    <syncfusion:BadgeContainer.Badge>
        <syncfusion:SfBadge HorizontalAlignment="Left"
                            VerticalAlignment="Center"
                            Content="99+"
                            Name="badge"/>
    </syncfusion:BadgeContainer.Badge>
    <syncfusion:BadgeContainer.Content>
        <Button Content="Inbox">
        </Button>
    </syncfusion:BadgeContainer.Content>
</syncfusion:BadgeContainer>

{% endhighlight %}
{% highlight C# %}

badge.HorizontalAlignment = HorizontalAlignment.Left;
badge.VerticalAlignment = VerticalAlignment.Center;
badge.Content = "99+";

{% endhighlight %}
{% endtabs %}

![Alignment of the Badge control is changed](Getting-Started_images/Alignment.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-badge-control-examples/blob/master/Samples/Badge_Features)

## Positioning of Badge

You can change the horizontal or vertical position of the `Badge` either inside, outside or in the middle by using the [HorizontalAnchor](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBadge.html#Syncfusion_UI_Xaml_Notifications_SfBadge_HorizontalAnchor) and [VerticalAnchor](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBadge.html#Syncfusion_UI_Xaml_Notifications_SfBadge_VerticalAnchor) properties. The default value of `HorizontalAnchor` and `VerticalAnchor` properties is `Center`.

{% tabs %}
{% highlight XAML %}

<syncfusion:BadgeContainer Name="badgeContainer"  >
    <syncfusion:BadgeContainer.Badge>
        <syncfusion:SfBadge HorizontalAnchor="Outside"
                            VerticalAnchor="Center"
                            Content="99+"
                            Name="badge"/>
    </syncfusion:BadgeContainer.Badge>
    <syncfusion:BadgeContainer.Content>
        <Button Content="Inbox">
        </Button>
    </syncfusion:BadgeContainer.Content>
</syncfusion:BadgeContainer>

{% endhighlight %}
{% highlight C# %}

badge.HorizontalAnchor = BadgeAnchor.Outside;
badge.VerticalAnchor = BadgeAnchor.Center;
badge.Content = "99+";

{% endhighlight %}
{% endtabs %}

![Position of the Badge control is changed](Getting-Started_images/Anchor.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-badge-control-examples/blob/master/Samples/Badge_Features)

## Badge content alignment

you can place the `Badge` content either horizontally or vertically by using the `HorizontalContentAlignment` or `VerticalContentAlignment` properties. The default value of `HorizontalContentAlignment` and `VerticalContentAlignment` properties is `Center`.

{% tabs %}
{% highlight XAML %}

<syncfusion:BadgeContainer Name="badgeContainer"  >
    <syncfusion:BadgeContainer.Badge>
        <syncfusion:SfBadge HorizontalContentAlignment="Right"
                            VerticalContentAlignment="Top"
                            Content="99+"
                            Name="badge"/>
    </syncfusion:BadgeContainer.Badge>
    <syncfusion:BadgeContainer.Content>
        <Button Content="Inbox">
        </Button>
    </syncfusion:BadgeContainer.Content>
</syncfusion:BadgeContainer>

{% endhighlight %}
{% highlight C# %}

badge.HorizontalContentAlignment = HorizontalAlignment.Right;
badge.VerticalContentAlignment = VerticalAlignment.Top;
badge.Content = "99+";

{% endhighlight %}
{% endtabs %}

![Alignment of the Badge content is changed](Getting-Started_images/Content_Alignment.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-badge-control-examples/blob/master/Samples/Badge_Features)