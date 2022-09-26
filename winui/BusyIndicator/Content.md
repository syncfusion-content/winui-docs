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

![WinUI BusyIndicator control with BusyContent](BusyIndicator_videos/winui_busyindicator_content.jpg)

## BusyContentPosition

The BusyIndicator control provides options to set the `BusyContent` at the Top, Bottom, Left and Right of the Busy Indicator. The `BusyContent` can be set using the `BusyContentPosition` property.

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

![WinUI BusyIndicator control with BusyContentPosition](BusyIndicator_videos/winui_busyindicator_contentposition.jpg)

## BusyContentTemplate

The BusyIndicator control provides options to set the `BusyContent` section as to change the template by using the `BusyContentTemplate` property.

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

![WinUI BusyIndicator control with BusyContentTemplate](BusyIndicator_videos/winui_busyindicator_contenttemplate.jpg)