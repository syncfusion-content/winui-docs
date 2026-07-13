---
layout: post
title: Compact Sizing in WinUI Controls | Syncfusion
description: Learn about Compact Sizing support in Syncfusion WinUI controls and more details.
platform: WinUI
control: Compact Sizing
documentation: ug
---

# Compact Sizing in WinUI Controls

Compact sizing reduces the spacing and padding of controls to enable dense, information-rich layouts. It is useful for applications that target pointer (mouse) input rather than touch, where more content can fit within the same screen area.

There are two types of spacing support for controls in WinUI:

1. [Standard](https://docs.microsoft.com/en-us/windows/apps/design/style/spacing#fluent-standard-sizing) - to accommodate both touch and pointer input.
2. [Compact](https://docs.microsoft.com/en-us/windows/apps/design/style/spacing#fluent-compact-sizing) - designed primarily to accommodate pointer input.

Compact sizing enables dense, information-rich groups of controls and can help with the following:

* Browsing large amounts of content.
* Maximizing visible content on a page.
* Navigating and interacting with controls and content.

## Prerequisites

To use compact sizing with Syncfusion<sup>&reg;</sup> WinUI controls, ensure the following prerequisites are met:

* Install [Visual Studio 2022](https://visualstudio.microsoft.com/vs/) version 17.8 or later with the **WinUI 3** workload.
* Install the **[Microsoft.UI.Xaml](https://www.nuget.org/packages/Microsoft.UI.Xaml)** NuGet package for base control compact styles.
* Install the **[Syncfusion.Core.WinUI](https://www.nuget.org/packages/Syncfusion.Core.WinUI)** NuGet package for Syncfusion control compact styles.
* Target **Windows 10 version 1903 (build 18362)** or later for WinUI 3 projects.

## Examples of compact sizing

Compact sizing is implemented through a unique resource dictionary that can be specified in your application at either the page level or a specific layout. Two resource dictionaries are required:

* **`Microsoft.UI.Xaml`** - Provides compact styles for the built-in WinUI controls.
* **`Syncfusion.Core.WinUI`** - Provides compact styles for Syncfusion WinUI controls.

The following examples show how the Compact style can be applied at the window level and for an individual Grid control.

### Window level

Applying compact sizing at the window level affects all controls within that window. Add the resource dictionaries to the `Window.Resources` collection.

{% tabs %}
{% highlight xaml %}

<Window.Resources>
      <ResourceDictionary Source="ms-appx:///Microsoft.UI.Xaml/DensityStyles/Compact.xaml" />
      <ResourceDictionary Source="ms-appx:///Syncfusion.Core.WinUI/Themes/DensityStyles/Compact.xaml" />
</Window.Resources>

{% endhighlight %}
{% endtabs %}

### Grid level

Applying compact sizing at the grid level limits the effect to only the controls within that `Grid`. Add the resource dictionaries to the `Grid.Resources` collection. Controls outside the `Grid` continue to use standard sizing.

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

## Limitations and troubleshooting

If compact sizing is not working as expected, check the following:

* **Controls do not appear compact** — Ensure both the `Microsoft.UI.Xaml` and `Syncfusion.Core.WinUI` compact resource dictionaries are merged in the resource scope (window, page, or layout level).
* **Resource dictionary not found** — Verify that the corresponding NuGet packages (`Microsoft.UI.Xaml` and `Syncfusion.Core.WinUI`) are installed and that the package version matches the resource path.
* **Custom styles ignore compact sizing** — Custom control styles that hard-code `Padding`, `Margin`, `Width`, or `Height` values will not respond to compact resource dictionaries. Use theme resource keys instead.
* **Compact sizing affects only the target scope** — Applying the dictionaries at the `Grid` level does not affect sibling controls outside the `Grid`. To apply compact sizing app-wide, set the dictionaries on the window or in `App.xaml`.

## See also

* [Themes for Syncfusion WinUI Controls](./themes.md)
* [Accessibility for Syncfusion WinUI Controls](./accessibility.md)
* [Right-to-Left (RTL) support for Syncfusion WinUI Controls](./right-to-left.md)
* [Localization for Syncfusion WinUI Controls](./localization.md)
* [Fluent spacing and sizing guidance](https://learn.microsoft.com/en-us/windows/apps/design/style/spacing)