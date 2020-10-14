---
layout: post
title: Right-to-left in WinUI TreeView | Syncfusion
description: Learn here about Right-to-left FlowDirection support in Syncfusion WinUI TreeView control and more details. 
platform: WinUI
control: TreeView
documentation: ug
---

# Right to left(RTL) in WinUI TreeView 

The [TreeView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html) supports to change the flow of text to the right-to-left direction by setting the [FlowDirection](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.frameworkelement.flowdirection?view=winrt-19041) to `RightToLeft`. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfTreeView x:Name="treeView" FlowDirection="RightToLeft"/>

{% endhighlight %}
{% highlight c# %}

treeView.FlowDirection = FlowDirection.RightToLeft;

{% endhighlight %}
{% endtabs %}

![WinUI TreeView with right to left](RightToLeft_images/RTL_image.jpg)


