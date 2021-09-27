---
layout: post
title: Filtering in WinUI ComboBox control | Syncfusion
description: Learn here all about ComboBox Filtering Options in Syncfusion WinUI ComboBox(multiselect combobox) control and more.
platform: winui
control: SfComboBox
documentation: ug
---
# Filtering in WinUI ComboBox

The ComboBox has built-in support to filter data items depending on the text entered in the editing text box. The filter operation starts as soon as you start typing characters in the component.

## Enable filtering

To enable filtering functionality in ComboBox control, set the `IsFilteringEnabled` and `IsEditable` properties as true. The default value is false. The drop down will open automatically as soon as you start typing characters in the ComboBox control.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox x:Name="sfComboBox"
                    Width="250"
                    IsEditable="true"
                    IsFilteringEnabled="true"
                    ItemsSource="{Binding SocialMedias}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name">
</editors:SfComboBox>

{% endhighlight %}

{% highlight C# %}

sfComboBox.IsFilteringEnabled = true;

{% endhighlight %}
{% endtabs %}

N> Filtering will be supported only for editable mode.

## Filter Mode

The string comparison for filtering suggestions can be changed using the `TextSearchMode` property. The default filtering type is `StartsWith`, ignoring accent and it is case insensitive. The available filtering modes are,

* StartsWith
* Contains

### Filter with beginning text

Filter the matching items based on the starting text and the first filtered item will be appended to the typed input and highlighted in the drop down. 

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox x:Name="sfComboBox"
                    Width="250"
                    TextSearchMode="StartsWith"
                    IsEditable="true"
                    IsFilteringEnabled="true"
                    ItemsSource="{Binding SocialMedias}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name">
</editors:SfComboBox>

{% endhighlight %}

{% highlight C# %}

sfComboBox.TextSearchMode = ComboBoxTextSearchMode.StartsWith;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox filter the items based on starting text](Filtering_images/winui-combobox-filtering-start-text.gif)

N> To disable the auto appending the text and highlighting behavior, set `IsTextSearchEnabled` property as false.

### Filter with contains text

Filter the matching items containing specific text and first filtered item will be highlighted in the drop down.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox x:Name="sfComboBox"
                    Width="250"
                    TextSearchMode="Contains"
                    IsEditable="true"
                    IsFilteringEnabled="true"
                    ItemsSource="{Binding SocialMedias}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name">
</editors:SfComboBox>

{% endhighlight %}

{% highlight C# %}

sfComboBox.TextSearchMode = ComboBoxTextSearchMode.Contains;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox filter the items based on contains text](Filtering_images/winui-combobox-filtering-contains-text.gif)

N> Auto appending of first suggested item text to typed input is not supported in this mode.