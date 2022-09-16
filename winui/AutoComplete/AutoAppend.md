---
layout: post
title: Auto-append support in WinUI AutoComplete control | Syncfusion
description: Learn here all about Auto-append support in Syncfusion WinUI AutoComplete control into WinUI application.
platform: winui
control: SfAutoComplete
documentation: UG
---

# Auto-append in WinUI AutoComplete(SfAutoComplete)

This section explains about the auto-append support available in [AutoComplete](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfAutoComplete.html).The AutoComplete control provides auto-append support with selection of text as well as text alone, as in Windows 11.

## Auto-append support 

The below code shows how to include the `Auto-append` in AutoComplete.

{% tabs %}
{% highlight XAML %}

<editors:SfAutoComplete ItemsSource="{Binding Countries}"
                        AppendType="Text">
</editors:SfAutoComplete>

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete control with auto-append](AutoAppend_Images/AutoComplete-with-auto-append.png)