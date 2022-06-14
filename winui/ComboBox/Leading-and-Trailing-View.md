---
layout: post
title: Leading and Trailing View in WinUI ComboBox control | Syncfusion
description: Learn here all about Leading and Trailing View support in Syncfusion WinUI ComboBox control and more.
platform: winui
control: SfComboBox
documentation: ug
---

# Leading  and Trailing View in WinUI ComboBox (SfComboBox)

This section explains about the Leading and Trailing view support available in [ComboBox](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfComboBox.html)

## Leading View in WinUI ComboBox (SfComboBox)

A `Leadingview` appears before the `ComboBox` selection area. Any content, such as an icon, image, button, or other control, is displayed in the `Leadingview`. Its default value is `Null`. When the `Leadingview` is not in use, their `Visibility` gets `Collapsed`. It was achieved by using a `String to Visibility Converter`.

{% tabs %}
{% highlight XAML %}

 <editors:SfComboBox Header="ComboBox with Leading view"
                     PlaceholderText="Search a country"
                     DisplayMemberPath="Country"
                     TextMemberPath="Country"
                     SelectionMode="Single"
                     TextSearchMode="StartsWith"
                     IsEditable="True"
                     ItemsSource="{Binding ContinentList}">
     <editors:SfComboBox.LeadingView>
         <SymbolIcon Symbol="Find"/>
     </editors:SfComboBox.LeadingView>
 </editors:SfComboBox>

{% endhighlight %}
{% endtabs %}

![Leading View in WinUI ComboBox](Leading_and_Trailing_view_images/Leading-View-in-ComboBox.png)

## Trailing View in WinUI ComboBox (SfComboBox)

A `Trailingview` appears after the `AutoComplete` selection area. Any content, such as an icon, image, button, or other control, is displayed in the `Trailingview`. Its default value is `Null`. When the `Trailingview` is not in use, their `Visibility` gets `Collapsed`. It was achieved by using a `String to Visibility Converter`.

{% tabs %}
{% highlight XAML %}

 <editors:SfComboBox Header="ComboBox with Trailing view"
                     PlaceholderText="Search a country"
                     DisplayMemberPath="Country"
                     TextMemberPath="Country"
                     SelectionMode="Single"
                     TextSearchMode="StartsWith"
                     IsEditable="True"
                     ItemsSource="{Binding ContinentList}">
     <editors:SfComboBox.TrailingView>
         <FontIcon Glyph="&#xEBE7;"/>
     </editors:SfComboBox.TrailingView>
 </editors:SfComboBox>

{% endhighlight %}
{% endtabs %}

![Trailing View in WinUI ComboBox](Leading_and_Trailing_view_images/Trailing-View-in-ComboBox.png)

