---
layout: post
title: Tree Lines in WinUI TreeView control | Syncfusion®
description: Learn here all about Tree Lines support in Syncfusion® WinUI TreeView(SfTreeView) control with customization support and more.
platform: WinUI
control: TreeView
documentation: ug
---

# Tree Lines in WinUI TreeView

The [TreeView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html) allows you to show the tree lines for TreeView nodes by setting the [ShowLines](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ShowLines) property to `true`. The default value is `false`.

{% tabs %}
{% highlight xaml %}
<treeView:SfTreeView Name="treeView" ShowLines="True" />
{% endhighlight %}
{% highlight c# %}
treeView.ShowLines = true;
{% endhighlight %}
{% endtabs %}

![WinUI TreeView with TreeLines](TreeLines_images/winui-treeview-treelines.jpg)

## Enable tree lines for root nodes

The `TreeView` also supports showing tree lines for root nodes by setting the [ShowRootLines](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ShowRootLines) property to `true`. The default value is `false`.

{% tabs %}
{% highlight xaml %}
<treeView:SfTreeView Name="treeView"    
                       ShowLines="True"
                       ShowRootLines="True" />
{% endhighlight %}
{% highlight c# %}
treeView.ShowLines = true;
treeView.ShowRootLines = true;
{% endhighlight %}
{% endtabs %}

![WinUI TreeView displays TreeLines for Root Nodes](TreeLines_images/winui-treeview-rootnode-tree-lines.jpg)

## Customizing the tree lines

### Customizing the line color
The `TreeView` allows you to change the color of tree lines by using the [LineStroke](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_LineStroke) property. The default value is a brush based on the system `BaseMediumLow` color.

{% tabs %}
{% highlight xaml %}
<treeView:SfTreeView Name="treeView"    
                       ShowLines="True"
                       ShowRootLines="True"
                       LineStroke="DeepSkyBlue" />
{% endhighlight %}
{% highlight c# %}
treeView.ShowLines = true;
treeView.ShowRootLines = true;
treeView.LineStroke = new SolidColorBrush(Colors.DeepSkyBlue);
{% endhighlight %}
{% endtabs %}

![Customizing TreeLines in WinUI TreeView](TreeLines_images/winui-treeview-treelines-customization.jpg)

### Customizing the line thickness
The `TreeView` allows you to change the thickness of tree lines by using the [LineStrokeThickness](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_LineStrokeThickness) property. The default value is `1`.

{% tabs %}
{% highlight xaml %}
<treeView:SfTreeView Name="treeView"           
                       ShowLines="True"
                       ShowRootLines="True"
                       LineStrokeThickness="1.5" />        
{% endhighlight %}
{% highlight c# %}
treeView.ShowLines = true;
treeView.ShowRootLines = true;
treeView.LineStrokeThickness = 1.5;
{% endhighlight %}
{% endtabs %}

