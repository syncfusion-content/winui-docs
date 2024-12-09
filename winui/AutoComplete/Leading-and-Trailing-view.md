---
layout: post
title: Leading and trailing view in WinUI AutoComplete | Syncfusion®
description: Learn how to add leading and trailing view (front and back view) in Syncfusion® WinUI AutoComplete control and more.
platform: winui
control: SfAutoComplete
documentation: ug
---

# Leading and Trailing View in WinUI AutoComplete (SfAutoComplete)

This section explains about the leading and trailing view support available in [AutoComplete](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfAutoComplete.html). The `LeadingView` appears before the `AutoComplete` selection area and `TrailingView` appears after the `AutoComplete` selection area. Any content, such as an icon, image, button, or control, can be displayed in the `LeadingView` and `TrailingView.`

## Leading View 

The below code shows how to include the `LeadingView` in AutoComplete.

{% tabs %}
{% highlight xaml %}

 <editors:SfAutoComplete Header="AutoComplete with Leading View"
                         PlaceholderText="Search a country">
         <editors:SfAutoComplete.LeadingView>
                <Viewbox Height="16"
                         Width="16"
                         Margin="4,0,0,0">
                    <SymbolIcon Symbol="Find" />
                </Viewbox>
         </editors:SfAutoComplete.LeadingView>
 </editors:SfAutoComplete>

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete control with icon in leading view or front view](Leading_and_Trailing_view_images/Leading-View-in-AutoComplete.png)

## Trailing View 

The below code shows how to include the `TrailingView` in AutoComplete.

{% tabs %}
{% highlight xaml %}

<editors:SfAutoComplete Header="AutoComplete with Trailing View"
                        PlaceholderText="Search a country">
        <editors:SfAutoComplete.TrailingView>
              <Button Style="{ThemeResource AlternateCloseButtonStyle}"
                      Height="30"
                      AllowFocusOnInteraction="False">
                    <Viewbox Height="16"
                             Width="16">
                        <FontIcon Glyph="&#xEBE7;" />
                    </Viewbox>
              </Button>
        </editors:SfAutoComplete.TrailingView>
</editors:SfAutoComplete>

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete control with button in trailing view or back view](Leading_and_Trailing_view_images/Trailing-View-in-AutoComplete.png)

## Leading and Trailing View 

The below code shows how to include both `LeadingView` and `TrailingView` in AutoComplete.

{% tabs %}
{% highlight xaml %}

<editors:SfAutoComplete Header="AutoComplete with Leading and Trailing View"
                        PlaceholderText="Search a country">
        <editors:SfAutoComplete.LeadingView>
                    <editors:SfComboBox Margin="0,4,0,4">
                            <editors:SfComboBoxItem Content="Asia" />
                            <editors:SfComboBoxItem Content="Africa" />
                            <editors:SfComboBoxItem Content="North America"/>
                            <editors:SfComboBoxItem Content="South America" />
                            <editors:SfComboBoxItem Content="Europe" />
                            <editors:SfComboBoxItem Content="All Countries"
                                                    IsSelected="True"/>
                    </editors:SfComboBox>
        </editors:SfAutoComplete.LeadingView>
        <editors:SfAutoComplete.TrailingView>
                    <Viewbox Height="16"
                             Width="16"
                             Margin="0,0,8,0">
                        <SymbolIcon Symbol="Find" />
                    </Viewbox>
        </editors:SfAutoComplete.TrailingView>
</editors:SfAutoComplete>

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete control with combo box in leading view or front view and button in trailing view or back view](Leading_and_Trailing_view_images/Leading-and-Trailing-View-in-AutoComplete.png)