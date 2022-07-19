---
layout: post
title: Compact Sizing in WinUI Controls | Syncfusion
description: Learn here about Compact Sizing support in Syncfusion WinUI Project Reunion controls and more details. 
platform: WinUI
control: Compact Sizing
documentation: ug
---

# Compact Sizing in WinUI Controls

There are two types of spacing support for controls in WinUI.
1. [Standard](https://docs.microsoft.com/en-us/windows/apps/design/style/spacing#fluent-standard-sizing) - to accommodate both touch and pointer input.
2. [Compact](https://docs.microsoft.com/en-us/windows/apps/design/style/spacing#fluent-compact-sizing) - designed primarily to accommodate pointer input.

Compact sizing enables dense, information-rich groups of controls and can help with the following:
* Browsing large amounts of content.
* Maximizing visible content on a page.
* Navigating and interacting with controls and content.

## Examples of compact sizing

Compact sizing is implemented through a unique resource dictionary that can be specified in your application at either the page level or a specific layout. The resource dictionary is available in the WinUI Nuget package.

The following examples show how the Compact style can be applied for the window and an individual Grid control.

### Window level

{% tabs %}
{% highlight xaml %}

<Window.Resources>
      <ResourceDictionary Source="ms-appx:///Microsoft.UI.Xaml/DensityStyles/Compact.xaml" />
      <ResourceDictionary Source="ms-appx:///Syncfusion.Core.WinUI/Themes/DensityStyles/Compact.xaml" />
</Window.Resources>

{% endhighlight %}
{% endtabs %}

### Grid level

{% tabs %}
{% highlight xaml %}

<Grid>
    <Grid.Resources>
        <ResourceDictionary Source="ms-appx:///Microsoft.UI.Xaml/DensityStyles/Compact.xaml" />
        <ResourceDictionary Source="ms-appx:///Syncfusion.Core.WinUI/Themes/DensityStyles/Compact.xaml" />
    </Grid.Resources>
</Grid>

{% endhighlight %}
{% endtabs %}