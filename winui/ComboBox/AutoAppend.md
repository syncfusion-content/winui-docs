---
layout: post
title: Auto-append support in WinUI ComboBox control | Syncfusion
description: Learn here all about Auto-append support in Syncfusion WinUI ComboBox control and more.
platform: winui
control: SfComboBox
documentation: ug
---

# Auto-append in WinUI ComboBox (SfComboBox)

This section explains about the auto-append support available in [ComboBox](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfComboBox.html). The ComboBox control provides auto-append support with selection of text as well as text alone, as in Windows 11.

## Auto-append support 

The below code shows how to include the `Auto-append` in ComboBox.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox ItemsSource="{Binding Countries}"
		    AutoAppendType="Text">
</editors:SfComboBox>

{% endhighlight %}
{% endtabs %}

![WinUI Combobox control with auto-append](AutoAppend_images/ComboBox-with-auto-append.png)