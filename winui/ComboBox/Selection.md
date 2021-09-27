---
layout: post
title: Selection in WinUI ComboBox control | Syncfusion
description: Learn here all about Selection modes support in Syncfusion WinUI ComboBox(SfComboBox) control and more.
platform: winui
control: SfComboBox
documentation: ug
---

# Selection in WinUI ComboBox

The SfComboBox allows you to select single or multiple items in the drop-down list. The selection mode can be set by using the `SelectionMode` property. There are two different selection modes: `Single`, `Multiple`.

## Single selection

The SfComboBox allows you to select a single item from the dropdown list.

### UI Selection 

The selected item can be changed interactively by selecting from the dropdown list or enter the value using keyboard. The selected item can be retrieved from the `SelectedItem` or `SelectedIndex` properties of ComboBox control.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox
    IsEditable="True"
    Width="250"
    ItemsSource="{Binding SocialMedias}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"
    x:Name="sfComboBox" />

{% endhighlight %}
{% endtabs %}

![Single selection in WinUI ComboBox](Selection_images/winui-combobox-single-selection.gif)

### Programmatic Selection 

The selected item can be changed programmatically by using `SelectedItem` or `SelectedIndex` properties of ComboBox control. 

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox
    Width="250"
    IsEditable="True"
    ItemsSource="{Binding SocialMedias}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"
    SelectedIndex="2"
    x:Name="sfComboBox" />

{% endhighlight %}

{% highlight c# %}

sfComboBox.SelectedIndex = 2;

{% endhighlight %}
{% endtabs %}

![Single selection in WinUI ComboBox programmatically](Selection_images/winui-combobox-single-selection-programmatically.png)

## Multiple selection

The SfComboBox allows you to select multiple values from the drop-down list. The multi-select combo box mode can be enabled by setting the `SelectionMode` property as `Multiple`.

### UI Selection 

The selected items can be changed interactively by using keyboard or select from dropdown list. The selected items can be retrieved from the `SelectedItems` property of ComboBox control.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox
    Width="250"
    ItemsSource="{Binding SocialMedias}"
    SelectionMode="Multiple"
    DisplayMemberPath="Name"
    TextMemberPath="Name"
    x:Name="sfComboBox" />

{% endhighlight %}
{% endtabs %}

![Multiple selection in WinUI ComboBox](Selection_images/winui-combobox-multiple-selection.gif)

### Programmatic Selection 

The selected items can be changed programmatically by using `SelectedItems` property of ComboBox control.  

{% tabs %}
{% highlight c# %}

ObservableCollection<SocialMedia> socialMediasList = (this.sfComboBox.DataContext as SocialMediaViewModel).SocialMedias;
this.sfComboBox.SelectedItems.Add(socialMediasList[0]);
this.sfComboBox.SelectedItems.Add(socialMediasList[3]);
this.sfComboBox.SelectedItems.Add(socialMediasList[4]);
this.sfComboBox.SelectedItems.Add(socialMediasList[7]);

{% endhighlight %}
{% endtabs %}

![Multiple selection in WinUI ComboBox programmatically](Selection_images/winui-combobox-multiple-selection-programmatically.png)

### Separate items using delimiter

The SfComboBox supports various delimiter characters to separate the selected items displayed in a multi-select ComboBox. The delimiter character can be set by using the `DelimiterText` property. The default delimiter character is **,**.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox
    Width="250"
    DelimiterText="-"
    ItemsSource="{Binding SocialMedias}"
    SelectionMode="Multiple"
    DisplayMemberPath="Name"
    TextMemberPath="Name"
    x:Name="sfComboBox"/>

{% endhighlight %}

{% highlight C# %}

sfComboBox.DelimiterText = "-";

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox seperate the selected items using delimiter text](Selection_images/winui-combobox-delimiter-text.png)

### How to hide the check box?

The checkbox that is displayed in a dropdown list can be hide by using the `IsMultiSelectCheckBoxEnabled` property of ComboBox control. The default value of `IsMultiSelectCheckBoxEnabled` property is **true**.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox
    Width="250"
    IsMultiSelectCheckBoxEnabled="False"
    ItemsSource="{Binding SocialMedias}"
    SelectionMode="Multiple"
    DisplayMemberPath="Name"
    TextMemberPath="Name"
    x:Name="sfComboBox"/>

{% endhighlight %}

{% highlight C# %}

sfComboBox.IsMultiSelectCheckBoxEnabled = false;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox hide the checkbox in dropdown list](Selection_images/winui-combobox-multi-select-checkbox-enabled.png)

## Selection changed event

When selecting an item from the drop-down list, the `SelectionChanged` event will be called. The `SelectionChanged` event contains the newly selected and removed items in the AddedItems and RemovedItems properties. The `SelectionChanged` contains the following properties.

 * `AddedItems` - Contains the items that were selected.
 * `RemovedItems` - Contains the items that were unselected.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox x:Name="sfComboBox"
                    Width="250"
                    TextMemberPath="Name"
                    DisplayMemberPath="Name"
                    ItemsSource="{Binding SocialMedias}"
                    SelectionChanged="OnSfComboBoxSelectionChanged" />

{% endhighlight %}

{% highlight C# %}
sfComboBox.SelectionChanged += OnSfComboBoxSelectionChanged;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows.

{% tabs %}
{% highlight C# %}

private async  void OnSfComboBoxSelectionChanged(object sender, ComboBoxSelectionChangedEventArgs e)
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
