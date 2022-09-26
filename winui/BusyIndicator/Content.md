---
layout: post
title: Content in WinUI BusyIndicator control | Syncfusion
description: Learn here all about showing the loading progress of the content with Syncfusion WinUI BusyIndicator Control.
platform: WinUI
control: SfBusyIndicator
documentation: ug
---

# Content in WinUI BusyIndicator

The BusyIndicator control provides option to set the content that indicates the busy status of the control to the users by using the `BusyContent` property.

{% tabs %}
{% highlight xaml %}

<notification:SfBusyIndicator IsActive="True"
     AnimationType="DottedCircle"
     BusyContent="Loading">
</notification:SfBusyIndicator>

{% endhighlight %}
{% highlight C# %}

SfBusyIndicator busyIndicator = new SfBusyIndicator();
busyIndicator.IsActive = true;
busyIndicator.AnimationType = BusyIndicatorAnimationType.DottedCircle;
busyIndicator.BusyContent = "Loading";

{% endhighlight %}
{% endtabs %}

![BusyIndicator content in WinUI](BusyIndicator_videos/winui_busyindicator_content.jpg)

## BusyContentPosition

{% tabs %}
{% highlight xaml %}

<notification:SfBusyIndicator IsActive="True"
     AnimationType="DottedCircle"
     BusyContent="Loading"
     BusyContentPosition="Top">
</notification:SfBusyIndicator>

{% endhighlight %}
{% highlight C# %}

SfBusyIndicator busyIndicator = new SfBusyIndicator();
busyIndicator.IsActive = true;
busyIndicator.AnimationType = BusyIndicatorAnimationType.DottedCircle;
busyIndicator.BusyContent = "Loading";
busyIndicator.BusyContentPosition = BusyIndicatorContentPosition.Top;

{% endhighlight %}
{% endtabs %}

![BusyIndicator BusyContentPosition in WinUI](BusyIndicator_videos/winui_busyindicator_contentposition.jpg)

## BusyContentTemplate

{% tabs %}
{% highlight xaml %}

<notification:SfBusyIndicator IsActive="True" AnimationType="DottedCircle">
    <notification:SfBusyIndicator.BusyContentTemplate>
        <DataTemplate>
            <TextBlock Text="Loading..." FontSize="18" FontStyle="Italic" FontWeight="Bold" Foreground="Red"/>
        </DataTemplate>
    </notification:SfBusyIndicator.BusyContentTemplate>
</notification:SfBusyIndicator>

{% endhighlight %}
{% endtabs %}

![BusyIndicator BusyContentTemplate in WinUI](BusyIndicator_videos/winui_busyindicator_contenttemplate.jpg)