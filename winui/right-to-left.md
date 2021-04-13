---
layout: post
title: Right-to-left in WinUI controls | Syncfusion
description: Learn here about Right-to-left FlowDirection support in Syncfusion WinUI control and more details. 
platform: WinUI
control: TreeView
documentation: ug
---

# Right to left(RTL) in WinUI controls 

Syncfusion WinUI controls support to changing the text flow to the right-to-left direction by setting the [FlowDirection](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.frameworkelement.flowdirection?view=winrt-19041) to `RightToLeft`. 

The example below shows a treeview control with RTL direction.

{% tabs %}
{% highlight xaml %}

<treeView:SfTreeView x:Name="treeView" FlowDirection="RightToLeft"/>

{% endhighlight %}
{% highlight c# %}

treeView.FlowDirection = FlowDirection.RightToLeft;

{% endhighlight %}
{% endtabs %}

![WinUI TreeView with right to left](Common-images/winui-control-right-to-left-direction.png)