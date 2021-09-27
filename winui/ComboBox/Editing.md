---
layout: post
title: Editing in WinUI ComboBox control | Syncfusion
description: Learn here all about Editing support in Syncfusion WinUI ComboBox(SfComboBox) control.
platform: winui
control: SfComboBox
documentation: ug
---

# Editing in WinUI ComboBox

The combo box control supports both editable and non-editable text box to choose selected item in given data source. To enable editing functionality, set the `IsEditable` property as `true`. The default value is false.

## Editable combo box

In editable mode, the combo box allows users to edit in the text box that shows the suggestions in drop-down list based on the input.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox x:Name="sfComboBox"
                    Width="250"
                    IsEditable="true"
                    ItemsSource="{Binding SocialMedias}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name">
</editors:SfComboBox>

{% endhighlight %}

{% highlight C# %}

sfComboBox.IsEditable = true;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox choose item using editing](Editing_images/winui-combobox-edit-mode.gif)

## Non-editable combo box

Non-editable mode prevents users from typing and allows them to select from drop-down list.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox x:Name="sfComboBox"
                    Width="250"
                    IsEditable="false"
                    ItemsSource="{Binding SocialMedias}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name">
</editors:SfComboBox>

{% endhighlight %}

{% highlight C# %}

sfComboBox.IsEditable = false;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox choose item using keyboard](Editing_images/winui-combobox-non-edit-mode.gif)

## Hide clear button in the editor

By default, the clear button `X` will be displayed in the editor of the `ComboBox` control, which can be used to clear the entered input. Hide the clear button in `ComboBox` control using the `ShowClearButton` property. The default value of `ShowClearButton` property value is **true**.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox x:Name="sfComboBox"
                    Width="250"
                    IsEditable="true"
                    ShowClearButton="false"
                    ItemsSource="{Binding SocialMedias}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name">
</editors:SfComboBox>

{% endhighlight %}

{% highlight C# %}

sfComboBox.ShowClearButton = false;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox hide clear button](Editing_images/winui-combobox-hideclearbutton.png)

N> `ShowClearButton` property does not have effect in non-editable mode.

## Open Dropdown programmatically

In SfComboBox control, the drop down can be opened or closed programmatically by using the `IsDropDownOpen` property. The default value of `IsDropDownOpen` property is false. Below example shows, opening drop down when pressing alphabet keys in SfComboBox control.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox x:Name="sfComboBox"
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
    if (!sfComboBox.IsDropDownOpen && (int)eventArgs.Key >= 65 && (int)eventArgs.Key <= 90)
    {
        this.sfComboBox.IsDropDownOpen = true;
    }
}

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox opening drop down programmatically](Editing_images/winui-combobox-open-dropdown-programmatically.gif)

## Handle invalid input 

when submitting some text that does not correspond to an item in the ComboBox dropdown list, the `TextSubmitted` event will be called. Using the following code snippet, a dialogue box will be displayed when submitting input that does not contain in drop down list.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox x:Name="sfComboBox"
                    Width="250"
                    IsEditable="true"
                    ItemsSource="{Binding SocialMedias}"
                    TextSubmitted="OnEditingComboBoxTextSubmitted"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name">
</editors:SfComboBox>

{% endhighlight %}

{% highlight C# %}

sfComboBox.TextSubmitted += OnEditingComboBoxTextSubmitted;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows.

{% tabs %}
{% highlight C# %}

/// <summary>
/// Occurs when the user submits some text that does not correspond to an item in the ComboBox dropdown list.
/// </summary>
private async void OnEditingComboBoxTextSubmitted(object sender, Syncfusion.UI.Xaml.Editors.ComboBoxInputSubmittedEventArgs e)
{
    var cd = new ContentDialog
    {
        Content = "Enter a game from the list.",
        CloseButtonText = "Close"
    };


    cd.XamlRoot = this.Content.XamlRoot;
    var result = await cd.ShowAsync();
}

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox invalid input submission](Editing_images/winui-combobox-invalid-input-submission.png)