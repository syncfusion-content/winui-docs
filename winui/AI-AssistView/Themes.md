---
layout: post
title: About .NET WinUI AI Assist View control | Syncfusion
description: Learn here all about Theme support in Syncfusion WinUI AI AssistView(SfAIAssistView) control and more.
platform: WinUI
control: SfAIAssistView
documentation: ug
---

# Theme support in WinUI AI AssistView Control

This section explains AIAssistView Control's various themes.

## Set the Themes in AI AssistView Control

The AI AssistView Control provides various themes to be applied by setting the theme name in `RequestedTheme` property in the App.xaml file.

### Dark Theme

{% tabs %}
{% highlight xaml %}

<Application
    x:Class="UI_Customization.App"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:UI_Customization" RequestedTheme="Dark">
</Application>

{% endhighlight %}
{% endtabs %} 

![WinUI AI AssistView Control with Dark Theme](aiassistview_images/winui_aiassistview_dark_theme.png)

### Light Theme

{% tabs %}
{% highlight xaml %}

<Application
    x:Class="UI_Customization.App"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:UI_Customization" RequestedTheme="Light">
</Application>

{% endhighlight %}
{% endtabs %} 

![WinUI AI AssistView Control with Dark Theme](aiassistview_images/winui_aiassistview_light_theme.png)