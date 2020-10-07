---
layout: post
title: Theme support for Syncfusion WinUI Controls
description: Explains about the supported themes and learn how to configure themes for Syncfusion WinUI controls.
platform: winui
control: Themes
documentation: ug
---

# Themes for Syncfusion WinUI Controls

The theme affects the colors of the control's background, foreground, border brush and padding, margin, font etc.

## Supported themes

Syncfusion WinUI controls supports Light, Dark application themes and High contrast themes. 

**Light theme**

![Light theme for WinUI controls](themes-images/light.png)

**Dark Theme**

![Dark theme for WinUI controls](themes-images/dark.png)

## Applying the theme at application level

We can change the theme for the whole application using the `RequestedTheme` property available in App.xaml 

{% tabs %}
{% highlight xaml %}

    <Application
        x:Class="DemoApp.App"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinUIDemoApp" RequestedTheme="Dark">
    </Application>

{% endhighlight %}

{% highlight c# %}

    sealed partial class App : Application

    {
        public App()
        {
            this.RequestedTheme = ApplicationTheme.Dark;
            this.InitializeComponent();
        }
    }

{% endhighlight %}
{% endtabs %}

N> When the `RequestedTheme` property is not set, application will use the user's system settings. When the user set High contrast theme, the system will override the `RequestedTheme`.

## Applying themes for controls

Themes can also be applied for framework element individually irrespective of the Application level themes. It can be set using the `RequestedTheme` property available in UIElements. When the `RequestedTheme` property is set to `Default` it uses the `Application.RequestedTheme` value for the elements.

{% tabs %}
{% highlight xaml %}

    <syncfusion:SfDataGrid x:Name="datagrid" RequestedTheme="Dark"/>

{% endhighlight %}

{% highlight c# %}

        public MainPage()
        {
            this.datagrid.RequestedTheme = ElementTheme.Dark;
            this.InitializeComponent();
        }

{% endhighlight %}
{% endtabs %}

N> When the RequestedTheme value is set on a FrameworkElement, it will inherit to any elements that are nested within the element.






