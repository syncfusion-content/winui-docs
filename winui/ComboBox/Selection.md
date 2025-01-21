---
layout: post
title: Selection in WinUI ComboBox control | Syncfusion
description: Learn here all about Selection modes support in Syncfusion WinUI ComboBox (multi-select ComboBox) control and more.
platform: winui
control: SfComboBox
documentation: ug
---

# Selection in WinUI ComboBox (SfComboBox)

The [ComboBox](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfComboBox.html) allows user to select single or multiple items from the drop-down list. The selection mode can be set by using the [SelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownListBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownListBase_SelectionMode) property. There are two different selection modes: `Single`, and `Multiple`.

## Single selection

The `ComboBox` allows user to select a single item from the drop-down list.

### UI Selection 

The selected item can be changed interactively by selecting from the drop-down list or entering the value using keyboard and clicking the `Enter` key or losing the control focus. The selected item can be retrieved from the [SelectedItem](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownListBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownListBase_SelectedItem) or [SelectedIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfComboBox.html#Syncfusion_UI_Xaml_Editors_SfComboBox_SelectedIndex) property of `ComboBox` control.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox IsEditable="True"
                    ItemsSource="{Binding SocialMedias}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name" />

{% endhighlight %}
{% endtabs %}

![Single selection in WinUI ComboBox](Selection_images/winui-combobox-single-selection.gif)

### Programmatic selection 

The selected item can be changed programmatically by using the `SelectedItem` or `SelectedIndex` property of `ComboBox` control. 

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox x:Name="comboBox"
                    IsEditable="True"
                    ItemsSource="{Binding SocialMedias}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name"
                    SelectedIndex="2" />

{% endhighlight %}

{% highlight c# %}

comboBox.SelectedIndex = 2;

{% endhighlight %}
{% endtabs %}

![Single selection in WinUI ComboBox programmatically](Selection_images/winui-combobox-single-selection-programmatically.png)

### Decide when to update selected item

The [SelectionChangeTrigger](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfComboBox.html#Syncfusion_UI_Xaml_Editors_SfComboBox_SelectionChangeTrigger) property of the `ComboBox` can be used to update the selected item when the user commits a selection or each time the user navigates to a new selection in the `ComboBox`. The default value is `Committed`. The available SelectionChangeTrigger modes are:

* **Committed** - Selected item is updated when the user commits a selection in the `ComboBox`.
* **Always** - Selected item is updated when each time the user navigates to a new selection in the `ComboBox`.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox IsEditable="True"
                    Width="250"
                    Margin="0,0,0,250"
                    ItemsSource="{Binding SocialMedias}"
                    SelectionChangeTrigger="Always"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name"
                    SelectionChanged="OnComboBoxSelectionChanged" />

{% endhighlight %}

{% highlight C# %}

private async  void OnComboBoxSelectionChanged(object sender, ComboBoxSelectionChangedEventArgs e)
{
    var cd = new ContentDialog
    {
        Content = "Selected item was changed.",
        CloseButtonText = "Close"
    };

    cd.XamlRoot = this.Content.XamlRoot;
    var result = await cd.ShowAsync();
}

{% endhighlight %}
{% endtabs %}

The following screenshot demonstrates, while typing `f` in ComboBox control `Facebook` will be set as selected item.

![Updates selected item each time the user navigates to a new selection in ComboBox](Selection_images/winui-combobox-selection-change-trigger-always.png)

N> You can refer more information about `SelectionChanged` event from [this](https://help.syncfusion.com/winui/combobox/selection#selection-changed-event) link.

## Multiple selection

The `ComboBox` allows user to select multiple values from the drop-down list. The multi-select `ComboBox` mode can be enabled by setting the `SelectionMode` property as `Multiple`. 

There are two different display modes to perform multiple selection in ComboBox: `Delimiter`, and `Token`. The multiple selection display modes will be briefly explained in the upcoming section.

### Programmatic selection 

The selected items can be changed programmatically by using the `SelectedItems` property of ComboBox control.  

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox x:Name="comboBox"
                    ItemsSource="{Binding SocialMedias}"
                    SelectionMode="Multiple"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name" />

{% endhighlight %}

{% highlight c# %}

SocialMediaViewModel socialMediaViewModel = (this.comboBox.DataContext as SocialMediaViewModel);
ObservableCollection<SocialMedia> socialMediasList = socialMediaViewModel.SocialMedias;
this.comboBox.SelectedItems.Add(socialMediasList[0]);
this.comboBox.SelectedItems.Add(socialMediasList[2]);
this.comboBox.SelectedItems.Add(socialMediasList[3]);
this.comboBox.SelectedItems.Add(socialMediasList[5]);

{% endhighlight %}
{% endtabs %}

![Multiple selection in WinUI ComboBox programmatically](Selection_images/winui-combobox-multiple-selection-programmatically.png)

### How to hide the check box

The checkbox that is displayed in a drop-down list can be hidden by using the [IsMultiSelectCheckBoxEnabled](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownListBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownListBase_IsMultiSelectCheckBoxEnabled) property of ComboBox control. The default value of `IsMultiSelectCheckBoxEnabled` property is `true`.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox x:Name="comboBox"
                    IsMultiSelectCheckBoxEnabled="False"
                    ItemsSource="{Binding SocialMedias}"
                    SelectionMode="Multiple"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name" />

{% endhighlight %}

{% highlight C# %}

comboBox.IsMultiSelectCheckBoxEnabled = false;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox hide the checkbox in drop down list](Selection_images/winui-combobox-multi-select-checkbox-enabled.png)

### Multiple selection display

Display multiple selected items with token representation or simply divide them with a delimiter text. The multiple selection display mode can be set by using the [MultiSelectionDisplayMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfComboBox.html#Syncfusion_UI_Xaml_Editors_SfComboBox_MultiSelectionDisplayMode) property. The default value of `MultiSelectionDisplayMode` property is `Delimiter`. 

#### Delimiter

When selecting the multiple items, the selected items can be separated from each other with a desired character given for a delimiter. 

N> The `IsEditable` property has no effect when `MultiSelectionDisplayMode` is `Delimiter`.

##### UI selection 

The selected items can be changed interactively by using keyboard or by selecting from a drop-down list. The selected items can be retrieved from the [SelectedItems](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownListBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownListBase_SelectedItems) property of ComboBox control.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox ItemsSource="{Binding SocialMedias}"
                    SelectionMode="Multiple"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name" />
    
{% endhighlight %}
{% endtabs %}

![Multiple selection in WinUI ComboBox](Selection_images/winui-combobox-multiple-selection-delimiter.gif)

##### Separate items using delimiter

The ComboBox supports various delimiter characters to separate the selected items. The delimiter character can be set by using the [DelimiterText](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownListBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownListBase_DelimiterText) property. The default delimiter character is `,`.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox x:Name="comboBox"
                    DelimiterText="-"
                    ItemsSource="{Binding SocialMedias}"
                    SelectionMode="Multiple"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name" />

{% endhighlight %}

{% highlight C# %}

comboBox.DelimiterText = "-";

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox seperate the selected items using delimiter text](Selection_images/winui-combobox-delimiter-text.png)

#### Token

Selected items will be displayed with a customizable token representation and the users can remove each tokenized item by clicking the close button. Token mode supports both editable and non-editable text boxes for selecting items from a data source.

##### UI selection 

The selected items can be changed interactively by using keyboard or by selecting from a drop-down list. The selected items can be retrieved from the [SelectedItems](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownListBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownListBase_SelectedItems) property of ComboBox control.

{% tabs %}
{% highlight xaml %}

<StackPanel>
    <editors:SfComboBox x:Name="comboBox"
                        ItemsSource="{Binding SocialMedias}"
                        SelectionMode="Multiple"
                        MultiSelectionDisplayMode="Token"
                        DisplayMemberPath="Name"
                        TextMemberPath="Name" />

    <CheckBox Margin="20,0,0,0"
              IsChecked="{Binding ElementName=comboBox, Path=IsEditable, Mode=TwoWay}"
              Content="IsEditable" />
</StackPanel>

{% endhighlight %}
{% endtabs %}

![Multiple selection in WinUI ComboBox](Selection_images/winui-combobox-multiple-selection-token.gif)

N> Refer more information about customization of `ComboBoxTokenItem` from [this](https://help.syncfusion.com/winui/combobox/ui-customization#styling-comboboxtokenitem) link.

## Auto-append UI

The ComboBox control provides auto-append support with the selection of text as well as text alone. The auto-append UI can be defined by using the `AutoAppendType` property. There are two types of auto-append UI: The `TextWithSelection` and `Text.` When the auto-append UI is set to `Text,` the appended text appears with a faded foreground, similar to Windows 11.

#### Auto-append UI as TextWithSelection

When entering a text in the text box selection area, if the `AutoAppendType` property is `TextWithSelection,` the appended text appears with the selection.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox AppendType="TextWithSelection">
</editors:SfComboBox>

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox control with auto-append UI as TextWithSelection](Selection_images/winui-combobox-auto-append-textwithselection.png)

#### Auto-append UI as Text

When entering a text in the text box selection area, if the `AutoAppendType` property is `Text,` the appended text appears in a fading foreground.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox AutoAppendType="Text">
</editors:SfComboBox>

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox control with auto-append UI as Text](Selection_images/winui-combobox-auto-append-text.png)

## Selection changed notification

When selecting an item from the drop-down list, the [SelectionChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownListBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownListBase_SelectionChanged) event is triggered. The `SelectionChanged` event contains the newly selected and removed items in the AddedItems and RemovedItems properties. The `SelectionChanged` contains the following properties:

 * `AddedItems` - Contains the items that were selected.
 * `RemovedItems` - Contains the items that were unselected.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox x:Name="comboBox"
                    Width="250"
                    TextMemberPath="Name"
                    DisplayMemberPath="Name"
                    ItemsSource="{Binding SocialMedias}"
                    SelectionChanged="OnComboBoxSelectionChanged" />

{% endhighlight %}

{% highlight C# %}

comboBox.SelectionChanged += OnComboBoxSelectionChanged;

{% endhighlight %}
{% endtabs %}

The SelectionChanged event can be handled as follows.

{% tabs %}
{% highlight C# %}

private async  void OnComboBoxSelectionChanged(object sender, ComboBoxSelectionChangedEventArgs e)
{
    var cd = new ContentDialog
    {
        Content = "Selected item was changed.",
        CloseButtonText = "Close"
    };

    cd.XamlRoot = this.Content.XamlRoot;
    var result = await cd.ShowAsync();
}

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox selection change notification](Selection_images/winui-combobox-selection-change-notification.png)
