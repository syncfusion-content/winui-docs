---
layout: post
title: Searching in WinUI ComboBox control | Syncfusion
description: Learn how to perform searching operation in Syncfusion WinUI ComboBox (multi-select ComboBox) control and more.
platform: winui
control: SfComboBox
documentation: ug
---

# Searching in WinUI ComboBox (SfComboBox)

The [ComboBox](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfComboBox.html) control provides rich text searching functionality. The [TextSearchMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfComboBox.html#Syncfusion_UI_Xaml_Editors_SfComboBox_TextSearchMode) and [IsTextSearchEnabled](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfComboBox.html#Syncfusion_UI_Xaml_Editors_SfComboBox_IsTextSearchEnabled) properties of the `ComboBox` can be used to regulate how the control behaves when it receives user input. The default value of `IsTextSearchEnabled` is `true`.

N> The [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI) NuGet package is required to use the `SfComboBox` control. Refer to [Getting Started](https://help.syncfusion.com/winui/combobox/getting-started) for setup details and sample data. Add `using Syncfusion.UI.Xaml.Editors;` in C# to access the `ComboBoxTextSearchMode` enum.

## Search based on member path

The [TextMemberPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownListBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownListBase_TextMemberPath) and [DisplayMemberPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownListBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownListBase_DisplayMemberPath) properties of the `ComboBox` control specify the property path by which the searching must be done when custom data is bound to the `ItemsSource` property.

`TextMemberPath` - Specifies the property path, by which the searching must be done when user input is received in the selection box portion of the `ComboBox` control. The default value is `String.Empty`. When `TextMemberPath` is `null` or `string.Empty`, searching will be performed based on `DisplayMemberPath`. 

`DisplayMemberPath` - Specifies the property path, by which the searching must be done when user input is received in the drop-down portion of the `ComboBox` control. The default value is `String.Empty`.

N> `TextMemberPath` and `DisplayMemberPath` will be effective for the collection item that holds two or more properties in it.

N> When both the `TextMemberPath` and `DisplayMemberPath` properties have a `null` or `string.Empty` value, searching will be performed based on the class name with namespace of the item.

## Edit mode Searching based on TextMemberPath

In edit mode, searching will be performed based on the `TextMemberPath` property while entering the text into the selection box. When `TextMemberPath` is `null` or `string.Empty`, searching will be performed based on `DisplayMemberPath`. 

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox x:Name="comboBox"
                    Width="250"
                    IsTextSearchEnabled="true"
                    IsEditable="true"
                    ItemsSource="{Binding SocialMedias}"
                    TextMemberPath="ID"
                    DisplayMemberPath="Name" />

{% endhighlight %}

{% highlight c# %}

comboBox.TextMemberPath = "ID";

{% endhighlight %}
{% endtabs %}

For example, after typing `4` in the selection box.

![WinUI ComboBox text searching based on TextMemberPath](Searching_images/winui-combobox-textmemberpath-searching.png)

## Non-Editable mode Searching based on DisplayMemberPath

In non-editable mode, searching will be performed based on the `DisplayMemberPath` property when user input is received in drop-down. 

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox x:Name="comboBox"
                    Width="250"
                    IsTextSearchEnabled="true"
                    ItemsSource="{Binding SocialMedias}"
                    TextMemberPath="Name"
                    DisplayMemberPath="ID" />

{% endhighlight %}

{% highlight c# %}

comboBox.DisplayMemberPath = "ID";

{% endhighlight %}
{% endtabs %}

For example, after typing `4` in the drop-down.

![WinUI ComboBox text searching based on DisplayMemberPath](Searching_images/winui-combobox-displaymemberpath-searching.png)

## Auto appending of text

The `ComboBox` control provides support to auto append the text based on data source when end-user edits. If the `IsTextSearchEnabled` property is set as `false`, the matched suitable text will not append with the entered text.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox x:Name="comboBox"
                    Width="250"
                    IsEditable="true"
                    ItemsSource="{Binding SocialMedias}"
                    TextMemberPath="Name"
                    DisplayMemberPath="Name" />

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox auto append text based on data source when user edits](Searching_images/winui-combobox-auto-append-text.png)

N> Auto appending of text is supported only in `Editable` mode and `TextSearchMode` property should be `StartsWith`.

## Diacritic aware search

The [IgnoreDiacritic](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.DropDownListBase.html?tabs=tabid-1#Syncfusion_UI_Xaml_Editors_DropDownListBase_IgnoreDiacritic) property allows string comparison and search operations to treat characters with diacritical marks as equivalent to their base characters. The default value of `IgnoreDiacritic` is `false`. This is useful for search indexing and user-friendly matching across languages. The following code example demonstrates how to enable diacritic-aware matching by setting `IgnoreDiacritic` to `true`.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox x:Name="comboBox"
                    Width="250"
                    IsEditable="true"
                    ItemsSource="{Binding SocialMedias}"
                    TextMemberPath="Name"
                    DisplayMemberPath="Name"
                    IgnoreDiacritic = "false" />

{% endhighlight %}

{% highlight c# %}

comboBox.IgnoreDiacritic = "false";

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox search the items based on diacritic characters in the edit field](Searching_images/winui-combobox-diacriticimage.png)

## Search modes

The `TextSearchMode` property of the `ComboBox` can be used to regulate how the control behaves when it receives user input. The default text searching type is `StartsWith`, ignoring accent and it is case insensitive. The available text search modes are:

* StartsWith
* Contains

### Search with beginning text

Searches the matching items based on the starting text, and the first item which fits the user input in the drop-down list will be highlighted.

The following examples show how to perform text searching functionality in single selection mode.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox x:Name="comboBox"
                    Width="250"
                    TextSearchMode="StartsWith"
                    ItemsSource="{Binding SocialMedias}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name" />

{% endhighlight %}

{% highlight c# %}

comboBox.TextSearchMode = ComboBoxTextSearchMode.StartsWith;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox search the items based on provided input in single selection mode](Searching_images/winui-combobox-searching-start-text-single-selection-mode.gif)

The following examples show how to perform text searching functionality in multiple selection mode.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox x:Name="comboBox"
                    Width="250"
                    SelectionMode="Multiple"
                    TextSearchMode="StartsWith"
                    ItemsSource="{Binding SocialMedias}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name" />

{% endhighlight %}

{% highlight c# %}

comboBox.TextSearchMode = ComboBoxTextSearchMode.StartsWith;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox search the items based on provided input in multiple selection mode](Searching_images/winui-combobox-searching-start-text-multiple-selection-mode.gif)

### Search with contains text

Searches the matching items containing specific text, and the first item which fits the user input in the drop-down list will be highlighted.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox x:Name="comboBox"
                    Width="250"
                    IsEditable="True"
                    TextSearchMode="Contains"
                    ItemsSource="{Binding SocialMedias}"
                    TextMemberPath="Name"
                    DisplayMemberPath="Name" />

{% endhighlight %}

{% highlight c# %}

comboBox.TextSearchMode = ComboBoxTextSearchMode.Contains;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox search the items based on provided input in editable mode](Searching_images/winui-combobox-searching-contains-text-editable-mode.gif)

N> Auto-appending of the first suggested item text to the typed input is not supported in `Contains` mode.

### Custom searching

The ComboBox control provides support to apply your own custom search logic to highlight the item in the drop-down based on your search criteria by using the [SearchBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfComboBox.html#Syncfusion_UI_Xaml_Editors_SfComboBox_SearchBehavior) property. The default value of `SearchBehavior` is `null`.

Now, let us create a custom searching class to apply our own search logic to ComboBox control by the following steps:

**Step 1:** Create a class that implements the [IComboBoxSearchBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.IComboBoxSearchBehavior.html) interface.

{% tabs %}
{% highlight c# %}

/// <summary>
/// Represents a custom searching behavior for `ComboBox` control. 
/// </summary>
public class StringLengthSearchingBehavior : IComboBoxSearchBehavior
{
   
}

{% endhighlight %}
{% endtabs %}

**Step 2:** Then, implement the [GetHighlightIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.IComboBoxSearchBehavior.html#Syncfusion_UI_Xaml_Editors_IComboBoxSearchBehavior_GetHighlightIndex_Syncfusion_UI_Xaml_Editors_SfComboBox_Syncfusion_UI_Xaml_Editors_ComboBoxSearchInfo_) method of IComboBoxSearchBehavior interface to calculate the highlight index depending on the filtered items list and text entered in the ComboBox control that needs to be highlighted in drop-down. The `GetHighlightIndex` method contains the following arguments:

* [source](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfComboBox.html) - The owner of the search behavior, which holds information about ItemsSource, Items properties, and so on.
* [searchInfo](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.ComboBoxSearchInfo.html) - Contains details about the filtered items list and the text entered in ComboBox control. You may compute the index that has to be highlighted in the drop-down list using these details. The `ComboBoxSearchInfo` members include:
  * `Text` - The text entered in the ComboBox control.
  * `FilteredItems` - The list of items filtered based on the entered text.

The following example demonstrates how to highlight the first item that fully matches the typed length entered in the ComboBox control.

{% tabs %}
{% highlight c# %}

/// <summary>
/// Represents a custom searching behavior for `ComboBox` control. 
/// </summary>
public class StringLengthSearchingBehavior : IComboBoxSearchBehavior
{
    private int charLength;

    /// <summary>
    /// Return the highlight index that fully matches the typed length entered in the ComboBox control.
    /// </summary>
    public int GetHighlightIndex(SfComboBox source, ComboBoxSearchInfo searchInfo)
    {
        if (int.TryParse(searchInfo.Text, out this.charLength)) 
        {
           var fullMatch = searchInfo.FilteredItems.OfType<SocialMedia>().FirstOrDefault(i => i.Name.Length == charLength); 
           if (fullMatch != null)
           {
              return searchInfo.FilteredItems.IndexOf(fullMatch); 
           }
        }
       
        return -1;
    }
}

{% endhighlight %}
{% endtabs %}

**Step 3:** Apply custom searching to the ComboBox control by using the `SearchBehavior` property. 

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox IsEditable="True"
                    ItemsSource="{Binding SocialMedias}"
                    TextMemberPath="Name"
                    DisplayMemberPath="Name">
        <editors:SfComboBox.SearchBehavior>
            <local:StringLengthSearchingBehavior/>
        </editors:SfComboBox.SearchBehavior>
</editors:SfComboBox>

{% endhighlight %}
{% endtabs %}

For example, after typing `9` in the selection box, the first item that fully matches the typed length will be highlighted.

![WinUI ComboBox highlight the first item that fully matches the typed length](Searching_images/winui-combobox-custom-searching.png)

## How to disable searching

To disable searching and auto-appending text functionalities, set the `IsTextSearchEnabled` property as `false`. The default value is `true`.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox x:Name="comboBox"
                    Width="250"
                    IsTextSearchEnabled="false"
                    IsEditable="true"
                    ItemsSource="{Binding SocialMedias}"
                    TextMemberPath="Name"
                    DisplayMemberPath="Name" />

{% endhighlight %}

{% highlight c# %}

comboBox.IsTextSearchEnabled = false;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox text searching functionality is disabled](Searching_images/winui-combobox-disable-text-searching.png)

