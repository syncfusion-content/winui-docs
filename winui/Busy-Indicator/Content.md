---
layout: post
title: Content in WinUI BusyIndicator control | Syncfusion
description: Learn all about the loading progress content and its customization available in the Syncfusion WinUI BusyIndicator control here.
platform: WinUI
control: SfBusyIndicator
documentation: ug
---

# Content in WinUI BusyIndicator

The [BusyIndicator control](https://www.syncfusion.com/winui-controls/busy-indicator) provides an option to set the custom message that indicates the busy status of the control to the users by using the [BusyContent](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBusyIndicator.html#Syncfusion_UI_Xaml_Notifications_SfBusyIndicator_BusyContent) property.

{% tabs %}
{% highlight xaml %}

<notification:SfBusyIndicator IsActive="True"
     AnimationType="DottedCircle"
     BusyContent="Loading...">
</notification:SfBusyIndicator>

{% endhighlight %}
{% highlight C# %}

SfBusyIndicator busyIndicator = new SfBusyIndicator();
busyIndicator.IsActive = true;
busyIndicator.AnimationType = BusyIndicatorAnimationType.DottedCircle;
busyIndicator.BusyContent = "Loading...";

{% endhighlight %}
{% endtabs %}

![BusyContent in WinUI BusyIndicator control.](BusyIndicator_images/winui_busyindicator_content.jpg)

## Busy content position

The content can be positioned at the top, bottom, right, or left of the indicator by using the [BusyContentPosition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBusyIndicator.html#Syncfusion_UI_Xaml_Notifications_SfBusyIndicator_BusyContentPosition) property. The default value is `Bottom`.

{% tabs %}
{% highlight xaml %}

<notification:SfBusyIndicator IsActive="True"
     AnimationType="DottedCircle"
     BusyContent="Loading..."
     BusyContentPosition="Top">
</notification:SfBusyIndicator>

{% endhighlight %}
{% highlight C# %}

SfBusyIndicator busyIndicator = new SfBusyIndicator();
busyIndicator.IsActive = true;
busyIndicator.AnimationType = BusyIndicatorAnimationType.DottedCircle;
busyIndicator.BusyContent = "Loading...";
busyIndicator.BusyContentPosition = BusyIndicatorContentPosition.Top;

{% endhighlight %}
{% endtabs %}

![BusyContentPosition in WinUI BusyIndicator control.](BusyIndicator_images/winui_busyindicator_contentposition.jpg)

## Busy content template

The [BusyIndicator control](https://www.syncfusion.com/winui-controls/busy-indicator) provides options to customize the content by using the `DataTemplate` with the help of the [BusyContentTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBusyIndicator.html#Syncfusion_UI_Xaml_Notifications_SfBusyIndicator_BusyContentTemplate) property.

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

![BusyContentTemplate in WinUI BusyIndicator control.](BusyIndicator_images/winui_busyindicator_contenttemplate.jpg)
