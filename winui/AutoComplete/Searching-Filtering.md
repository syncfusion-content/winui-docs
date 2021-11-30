---
layout: post
title: Searching in WinUI AutoComplete control | Syncfusion
description: Learn how to perform searching operation in Syncfusion WinUI AutoComplete (multi-select AutoComplete) control and more.
platform: winui
control: SfAutoComplete
documentation: ug
---

# Searching in WinUI AutoComplete (SfAutoComplete)

The [AutoComplete] control provides rich text searching functionality.

## Search based on member path

The [TextMemberPath] and [DisplayMemberPath] properties of `AutoComplete` control specifies the property path, by which the searching must be done when a custom data is bound to the `ItemsSource` property.

`TextMemberPath` - Specifies the property path, by which searching must be done when user input is received in the selection box portion of the `AutoComplete` control. The default value is `String.Empty`.

`DisplayMemberPath` - Specifies the property path, by which searching must be done when user input is received in the drop-down portion of the `AutoComplete` control. The default value is `String.Empty`.

N> `TextMemberPath` and `DisplayMemberPath` will be effective for the collection item that holds two or more properties in it.

## Searching based on TextMemberPath

Searching will be performed based on the `TextMemberPath` property while entering the text into the selection box. If `TextMemberPath` is set to `null`, searching will be disabled.

{% tabs %}
{% highlight xaml %}

<editors:SfAutoComplete x:Name="autoComplete"
    Width="250"
    ItemsSource="{Binding Countries}"
    TextMemberPath="ID"
    DisplayMemberPath="Name" />

{% endhighlight %}

{% highlight C# %}

autoComplete.TextMemberPath = "ID";

{% endhighlight %}
{% endtabs %}

For e.g. After typing `4` in selection box.

![WinUI AutoComplete text searching based on TextMemberPath](Searching_images/winui-autocomplete-textmemberpath-searching.png)

## Searching based on DisplayMemberPath

Searching will be performed based on the `DisplayMemberPath` property while entering the text into the selection box. If `DisplayMemberPath` is `null`, searching will be disabled. 

{% tabs %}
{% highlight xaml %}

<editors:SfAutoComplete x:Name="autoComplete"
    Width="250"
    ItemsSource="{Binding Countries}"
    TextMemberPath="Name"
    DisplayMemberPath="ID" />

{% endhighlight %}

{% highlight C# %}

autoComplete.DisplayMemberPath = "ID";

{% endhighlight %}
{% endtabs %}

For e.g. After typing `Andorra` in drop-down.

![WinUI AutoComplete text searching based on DisplayMemberPath](Searching_images/winui-autocomplete-displaymemberpath-searching.png)

N> If `TextMemberPath` and `DisplayMemberPath` are `null`, searching will be performed based on the class name with namespace of the item.

## Search Mode

The `TextSearchMode` property of the `AutoComplete` can be used to regulate how the control behaves when it receives user input. The default text searching type is `StartsWith`, ignoring accent and it is case insensitive. The available text search modes are,

* StartsWith
* Contains

### Search with beginning text

Search the matching items based on the starting text, and the first item which fits the user input in the drop-down list, will be highlighted.

The following examples show how to perform text searching functionality in single selection mode.

{% tabs %}
{% highlight XAML %}

<editors:SfAutoComplete x:Name="autoComplete"
                    Width="250"
                    TextSearchMode="StartsWith"
                    ItemsSource="{Binding Countries}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name">
</editors:SfAutoComplete>

{% endhighlight %}

{% highlight C# %}

autoComplete.TextSearchMode = AutoCompleteTextSearchMode.StartsWith;

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete search the items based on provided input in single selection mode](Searching_images/winui-autocomplete-searching-start-text-single-selection-mode.png)

The following examples show how to perform text searching functionality in multiple selection mode.

{% tabs %}
{% highlight XAML %}

<editors:SfAutoComplete x:Name="autoComplete"
                    Width="250"
                    SelectionMode="Multiple"
                    TextSearchMode="StartsWith"
                    ItemsSource="{Binding Countries}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name">
</editors:SfAutoComplete>

{% endhighlight %}

{% highlight C# %}

autoComplete.TextSearchMode = AutoCompleteTextSearchMode.StartsWith;

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete search the items based on provided input in multiple selection mode](Searching_images/winui-autocomplete-searching-start-text-multiple-selection-mode.png)

### Search with contains text

Search the matching items containing specific text, and the first item which fits the user input in the drop-down list, will be highlighted.

{% tabs %}
{% highlight xaml %}

<editors:SfAutoComplete x:Name="autoComplete"
    Width="250"
    TextSearchMode="Contains"
    ItemsSource="{Binding Countries}"
    TextMemberPath="Name"
    DisplayMemberPath="Name" />

{% endhighlight %}

{% highlight C# %}

autoComplete.TextSearchMode = AutoCompleteTextSearchMode.Contains;

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete search the items based on provided input when SearchMode as Contains](Searching_images/winui-autocomplete-searching-contains-text.png)


