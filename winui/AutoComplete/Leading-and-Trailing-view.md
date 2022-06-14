---
layout: post
title: Leading and Trailing View with WinUI AutoComplete | Syncfusion
description: Learn here all about Leading and Trailing View support in Syncfusion WinUI AutoComplete control and more.
platform: WinUI
control: SfAutoComplete
documentation: ug
---

# Leading  and Trailing View in WinUI AutoComplete (SfAutoComplete)

This section explains about the Leading and Trailing view support available in [AutoComplete](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfAutoComplete.html).

## Leading View in WinUI AutoComplete (SfAutoComplete)

A `Leadingview` appears before the `AutoComplete` selection area. Any content, such as an icon, image, button, or other control, is displayed in the `Leadingview`. Its default value is `Null`. When the `Leadingview` is not in use, their `Visibility` gets `Collapsed`. It was achieved by using a `String to Visibility Converter`.

{% tabs %}
{% highlight xaml %}

  <editors:SfAutoComplete Header="Autocomplete with Leading view"
                         PlaceholderText="Search a country"
                         DisplayMemberPath="Country"
                         TextMemberPath="Country"
                         SelectionMode="Single"
                         TextSearchMode="StartsWith"
                         ShowClearButton="True"
                         ItemsSource="{Binding ContinentList}">
     <editors:SfAutoComplete.LeadingView>
         <SymbolIcon Symbol="Find"/>
     </editors:SfAutoComplete.LeadingView>
 </editors:SfAutoComplete>

{% endhighlight %}
{% endtabs %}

![Leading View in WinUI AutoComplete](Leading_and_Trailing_view_images/Leading-View-in-AutoComplete.png)

## Trailing View in WinUI AutoComplete (SfAutoComplete)

A `Trailingview` appears after the `AutoComplete` selection area. Any content, such as an icon, image, button, or other control, is displayed in the `Trailingview`. Its default value is `Null`. When the `Trailingview` is not in use, their `Visibility` gets `Collapsed`. It was achieved by using a `String to Visibility Converter`.

{% tabs %}
{% highlight xaml %}

 <editors:SfAutoComplete Header="Autocomplete with Trailing view"
                         PlaceholderText="Search a country"
                         DisplayMemberPath="Country"
                         TextMemberPath="Country"
                         SelectionMode="Single"
                         TextSearchMode="StartsWith"
                         ShowClearButton="True"
                         ItemsSource="{Binding ContinentList}">
     <editors:SfAutoComplete.TrailingView>
         <FontIcon Glyph="&#xEBE7;"/>
     </editors:SfAutoComplete.TrailingView>
 </editors:SfAutoComplete>

{% endhighlight %}
{% endtabs %}

![Trailing View in WinUI AutoComplete](Leading_and_Trailing_view_images/Trailing-View-in-AutoComplete.png)