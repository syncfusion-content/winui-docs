---
layout: post
title: Editing in WinUI ComboBox control | Syncfusion
description: Learn here all about Editable modes support in Syncfusion WinUI ComboBox (multi-select ComboBox) control and more.
platform: winui
control: SfComboBox
documentation: ug
---

# Editing in WinUI ComboBox (SfComboBox)

The [ComboBox](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfComboBox.html) control supports both editable and non-editable text boxes for selecting an item from a data source. To enable editing functionality, set [IsEditable](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfComboBox.html#Syncfusion_UI_Xaml_Editors_SfComboBox_IsEditable) property as `true`. The default value is `false`.

## Editable ComboBox

In editable mode, the `ComboBox` allows users to edit in the text box and it automatically appends the remaining letters to the entered text when it is valid. If the [IsTextSearchEnabled](https://help.syncfusion.com/cr/winui/Syncfusion.UIXaml_Editors.Xaml.Editors.SfComboBox.html#Syncfusion_UI__SfComboBox_IsTextSearchEnabled) property is set as `false`, the matched suitable text will not append to the entered text and will not automatically display suggestions in a drop-down list based on the input.

N> `SelectedItem` will be updated, once the control has lost focus or the `Enter` or `Tab` key is pressed. If the edit text is empty, the previously SelectedItem will not be cleared. If the [SelectionChangeTrigger](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfComboBox.html#Syncfusion_UI_Xaml_Editors_SfComboBox_SelectionChangeTrigger) property is set as `Always`, the `SelectedItem` will be updated immediately during input changing. 

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox x:Name="comboBox"
                    Width="250"
                    IsEditable="true"
                    ItemsSource="{Binding SocialMedias}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name">
</editors:SfComboBox>

{% endhighlight %}

{% highlight C# %}

comboBox.IsEditable = true;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox choose item using editing](Editing_images/winui-combobox-edit-mode.gif)

## Non-editable ComboBox

Non-editable mode prevents users from editing and instead allows them to select from drop-down list.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox x:Name="comboBox"
                    Width="250"
                    IsEditable="false"
                    ItemsSource="{Binding SocialMedias}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name">
</editors:SfComboBox>

{% endhighlight %}

{% highlight C# %}

comboBox.IsEditable = false;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox choose item using keyboard](Editing_images/winui-combobox-non-edit-mode.gif)


## Open a drop-down programmatically

In `ComboBox` control, the drop-down can be opened or closed programmatically by using the [IsDropDownOpen](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownListBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownListBase_IsDropDownOpen) property. The default value of `IsDropDownOpen` property is `false`. The following example shows how to open the drop-down when pressing alphabet keys in `ComboBox` control.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox x:Name="comboBox"
                    Width="250"
                    IsEditable="true"
                    PreviewKeyDown="OnEditingComboBoxPreviewKeyDown"
                    ItemsSource="{Binding SocialMedias}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name">
</editors:SfComboBox>

{% endhighlight %}

{% highlight C# %}

private void OnEditingComboBoxPreviewKeyDown(object sender, KeyRoutedEventArgs eventArgs)
{
    // Opening drop down when pressing alphabet keys.
    if (!comboBox.IsDropDownOpen && (int)eventArgs.Key >= 65 && (int)eventArgs.Key <= 90)
    {
        comboBox.IsDropDownOpen = true;
    }
}

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox opening drop down programmatically](Editing_images/winui-combobox-open-dropdown-programmatically.gif)

## Handle invalid input 

The [InputSubmitted](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfComboBox.html#Syncfusion_UI_Xaml_Editors_SfComboBox_InputSubmitted) event is triggered, when entered text is submitted that does not correspond to an item in the drop-down list. [ComboBoxInputSubmittedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.ComboBoxInputSubmittedEventArgs.html) has following members, which provide information for InputSubmitted event.

`Text:` Gets the text entered in ComboBox.

`Item:` This property can be used to add the item to the selected item(s) or set to the selected item that is assigned. 
If no item is assigned, then in single selection, entered text gets assigned to the selected item. In multiple selection, no text will be added to the selected items.

`Handled:` When set to `true`, the framework will not automatically update the selected item or selected item(s) of the ComboBox to the new value.

**Example 1:** By using the following code sample, a dialogue box will be displayed when submitting input that does not contain in the drop-down list.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox x:Name="comboBox"
                    Width="250"
                    IsEditable="true"
                    ItemsSource="{Binding SocialMedias}"
                    InputSubmitted="OnEditingComboBoxInputSubmitted"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name">
</editors:SfComboBox>

{% endhighlight %}

{% highlight C# %}

comboBox.InputSubmitted += OnEditingComboBoxInputSubmitted;

{% endhighlight %}
{% endtabs %}

The InputSubmitted event can be handled as follows.

{% tabs %}
{% highlight C# %}

/// <summary>
/// Occurs when the user submits some text that does not correspond to an item in the `ComboBox` drop-down list.
/// </summary>
private async void OnEditingComboBoxInputSubmitted(object sender, Syncfusion.UI.Xaml.Editors.ComboBoxInputSubmittedEventArgs e)
{
    var cd = new ContentDialog
    {
        Content = "Enter a social media from the list.",
        CloseButtonText = "Close"
    };

    cd.XamlRoot = this.Content.XamlRoot;
    var result = await cd.ShowAsync();
}

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox invalid input submission](Editing_images/winui-combobox-invalid-input-submission.png)

**Example 2:** The following example demonstrates how to add invalid item to selected items in multiple selection mode.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox IsEditable="true"
                    SelectionMode="Multiple"
                    MultiSelectionDisplayMode="Token"  
                    ItemsSource="{Binding SocialMedias}"
                    InputSubmitted="OnEditingComboBoxInputSubmitted"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name">
</editors:SfComboBox>

{% endhighlight %}

{% highlight C# %}

/// <summary>
/// Occurs when the user submits some text that does not correspond to an item in the `ComboBox` drop-down list.
/// </summary>
private async void OnEditingComboBoxInputSubmitted(object sender, Syncfusion.UI.Xaml.Editors.ComboBoxInputSubmittedEventArgs e)
{
    e.Item = new SocialMedia() { Name = e.Text, ID = comboBox.Items.Count };
}

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox invalid input submission in token mode](Editing_images/winui-combobox-invalid-input-submission-in-token-mode.png)

N> You can refer more information about multi-selection token mode from [this](https://help.syncfusion.com/winui/combobox/selection#multiple-selection) link.