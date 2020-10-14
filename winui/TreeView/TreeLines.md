---
layout: post
title: TreeLines in WinUI TreeView control | Syncfusion
description: Learn here about how to show the tree lines for TreeViewNodes in Syncfusion WinUI TreeView control and more details.
platform: WinUI
control: TreeView
documentation: ug
---

# Tree line for WinUI TreeView

The [TreeView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html) allows to show the tree lines for treeview nodes by enabling the [ShowLines](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ShowLines) property as `true`. The default value is `false`.

{% tabs %}
{% highlight xaml %}
<Syncfusion:SfTreeView Name="treeView" ShowLines="True" />
{% endhighlight %}
{% highlight c# %}
treeView.ShowLines = true;
{% endhighlight %}
{% endtabs %}

![TreeLines for WinUI TreeView](TreeLines_images/ShowLines_image.jpg)

## Enable tree line for root nodes

The `TreeView` also supports to show the tree lines for root nodes by enabling the [ShowRootLines](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ShowRootLines) property as `true`. The default value is `false`.

{% tabs %}
{% highlight xaml %}
<Syncfusion:SfTreeView Name="treeView"    
                       ShowLines="True"
                       ShowRootLines="True" />
{% endhighlight %}
{% highlight c# %}
treeView.ShowLines = true;
treeView.ShowRootLines = true;
{% endhighlight %}
{% endtabs %}

![TreeLines for WinUI TreeView](TreeLines_images/ShowRootLines_image.jpg)

## Customizing the tree lines

### Customizing the line color
The `TreeView` allows to change the color of tree lines by using the [LineStroke](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_LineStroke) property. The default value is `SystemBaseMediumLowColor`.

{% tabs %}
{% highlight xaml %}
<Syncfusion:SfTreeView Name="treeView"    
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

![TreeLines for WinUI TreeView](TreeLines_images/LineStroke_image.jpg)

### Customizing the line thickness
The `TreeView` allows to change the thickness of tree lines by using the [LineStrokeThickness](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_LineStrokeThickness) property. The default value is `1`.

{% tabs %}
{% highlight xaml %}
<Syncfusion:SfTreeView Name="treeView"           
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

