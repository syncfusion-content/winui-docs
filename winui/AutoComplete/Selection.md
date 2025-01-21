---
layout: post
title: Selection in WinUI AutoComplete control | Syncfusion
description: Learn here all about Selection modes support in Syncfusion WinUI AutoComplete (multi-select AutoComplete) control and more.
platform: winui
control: SfAutoComplete
documentation: ug
---

# Selection in WinUI AutoComplete (SfAutoComplete)

The [AutoComplete](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfAutoComplete.html) allows user to select single or multiple items. The selection mode can be set by using the [SelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfAutoComplete.html#Syncfusion_UI_Xaml_Editors_SfAutoComplete_SelectionMode) property. There are two different selection modes: `Single` and `Multiple`.

## Single selection

The `AutoComplete` allows user to select a single item by entering the value using keyboard, then selecting from the drop-down list and clicking the `Enter` key or `Tab` key. The selected item can be retrieved from the [SelectedItem](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.DropDownListBase.html#Syncfusion_UI_Xaml_Editors_DropDownListBase_SelectedItem) property.

{% tabs %}
{% highlight c# %}

//Model.cs
public class SocialMedia
{
    public string Name { get; set; }
    public int ID { get; set; }
}

//ViewModel.cs
public class SocialMediaViewModel
{
    public ObservableCollection<SocialMedia> SocialMedias { get; set; }
    public SocialMediaViewModel()
    {
        this.SocialMedias = new ObservableCollection<SocialMedia>();
        this.SocialMedias.Add(new SocialMedia() { Name = "Facebook", ID = 0 });
        this.SocialMedias.Add(new SocialMedia() { Name = "Google Plus", ID = 1 });
        this.SocialMedias.Add(new SocialMedia() { Name = "Instagram", ID = 2 });
        this.SocialMedias.Add(new SocialMedia() { Name = "LinkedIn", ID = 3 });
        this.SocialMedias.Add(new SocialMedia() { Name = "Skype", ID = 4 });
        this.SocialMedias.Add(new SocialMedia() { Name = "Telegram", ID = 5 });
        this.SocialMedias.Add(new SocialMedia() { Name = "Televzr", ID = 6 });
        this.SocialMedias.Add(new SocialMedia() { Name = "Tik Tok", ID = 7 });
        this.SocialMedias.Add(new SocialMedia() { Name = "Tout", ID = 8 });
        this.SocialMedias.Add(new SocialMedia() { Name = "Tumblr", ID = 9 });
        this.SocialMedias.Add(new SocialMedia() { Name = "Twitter", ID = 10 });
        this.SocialMedias.Add(new SocialMedia() { Name = "Vimeo", ID = 11 });
        this.SocialMedias.Add(new SocialMedia() { Name = "WhatsApp", ID = 12 });
        this.SocialMedias.Add(new SocialMedia() { Name = "YouTube", ID = 13 });
    }
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight xaml %}

<editors:SfAutoComplete
    SelectionMode="Single"
    ItemsSource="{Binding SocialMedias}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"
    Width="250"
    x:Name="autoComplete" />

{% endhighlight %}
{% highlight c# %}

autoComplete.SelectionMode = AutoCompleteSelectionMode.Single;

{% endhighlight %}
{% endtabs %}

![Single selection in WinUI AutoComplete](Selection_images/winui-AutoComplete-single-selection.gif)

## Multiple selection

The `AutoComplete` allows user to select multiple values by beginning to enter the input and selecting items from the drop-down list. The multi-select `AutoComplete` mode can be enabled by setting the `SelectionMode` property as `Multiple`. Selected items will be displayed with a customizable token representation and each tokenized items can be removed by clicking their close button. The selected items can be retrieved from the [SelectedItems](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.DropDownListBase.html#Syncfusion_UI_Xaml_Editors_DropDownListBase_SelectedItems) property.

{% tabs %}
{% highlight xaml %}

<editors:SfAutoComplete
    SelectionMode="Multiple"
    ItemsSource="{Binding SocialMedias}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"    
    Width="250"
    x:Name="autoComplete" />

{% endhighlight %}
{% highlight c# %}

autoComplete.SelectionMode = AutoCompleteSelectionMode.Multiple;

{% endhighlight %}
{% endtabs %}

![Multiple selection in WinUI AutoComplete](Selection_images/winui-autocomplete-multiple-selection.gif)

## Auto-append UI

The AutoComplete control provides auto-append support with the selection of text as well as text alone. The auto-append UI can be defined by using the `AppendType` property. There are two types of auto-append UI: The `TextWithSelection` and `Text.` When the auto-append UI is set to `Text,` the appended text appears with a faded foreground, similar to Windows 11.

#### Auto-append UI as TextWithSelection

When entering a text in the text box selection area, if the `AppendType` property is `TextWithSelection,` the appended text appears with the selection.

{% tabs %}
{% highlight XAML %}

<editors:SfAutoComplete AppendType="TextWithSelection">
</editors:SfAutoComplete>

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete control with auto-append UI as TextWithSelection](Selection_images/winui-autocomplete-auto-append-textwithselection.png)

#### Auto-append UI as Text

When entering a text in the text box selection area, if the `AppendType` property is `Text,` the appended text appears in a fading foreground.

{% tabs %}
{% highlight XAML %}

<editors:SfAutoComplete AppendType="Text">
</editors:SfAutoComplete>

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete control with auto-append UI as Text](Selection_images/winui-autocomplete-auto-append-text.png)

## Selection changed notification

When an item is selected from the drop-down list, the [SelectionChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfAutoComplete.html#Syncfusion_UI_Xaml_Editors_SfAutoComplete_SelectionChanged) event is triggered. The `SelectionChanged` event contains the newly selected and removed items in the `AddedItems` and `RemovedItems` properties. The `SelectionChanged` contains the following properties:

 * [AddedItems](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.AutoCompleteSelectionChangedEventArgs.html#Syncfusion_UI_Xaml_Editors_AutoCompleteSelectionChangedEventArgs_AddedItems) - Contains the items that were selected.
 * [RemovedItems](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.AutoCompleteSelectionChangedEventArgs.html#Syncfusion_UI_Xaml_Editors_AutoCompleteSelectionChangedEventArgs_RemovedItems) - Contains the items that were unselected.

{% tabs %}
{% highlight xaml %}

<editors:SfAutoComplete 
    SelectionChanged="OnSelectionChanged"
    TextMemberPath="Name"
    DisplayMemberPath="Name"
    ItemsSource="{Binding SocialMedias}" 
    Width="250"
    x:Name="autoComplete"/>

{% endhighlight %}

{% highlight C# %}

autoComplete.SelectionChanged += OnSelectionChanged;

{% endhighlight %}
{% endtabs %}

The `SelectionChanged` event can be handled as follows.

{% tabs %}
{% highlight C# %}

private async void OnSelectionChanged(object sender, AutoCompleteSelectionChangedEventArgs e)
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

![SelectionChanged event triggered while selecteditem changed in WinUI AutoComplete.](Selection_images/winui-AutoComplete-selectionchanged.gif)

## Get the selected value

The [SelectedValuePath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.DropDownListBase.html#Syncfusion_UI_Xaml_Editors_DropDownListBase_SelectedValuePath) property allows you to specify a [SelectedValue](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.DropDownListBase.html#Syncfusion_UI_Xaml_Editors_DropDownListBase_SelectedValue) for a `AutoComplete`'s `SelectedItem`. The `SelectedItem` represents an object in the `Items` collection, and the `AutoComplete` displays the value of the selected item's single property. The `SelectedValuePath` property specifies the path to the property that is used to determine the `SelectedValue` property's value. The default value of `SelectedValue` and `SelectedValuePath` is `null`.

For example, when you select any `SocialMedia.Name` in the `AutoComplete,` the `SelectedItem` property returns the `SocialMedia` data item that corresponds to the selected `SocialMedia.Name.` However, because the `SelectedValuePath` of this `AutoComplete` is set to `SocialMedia.ID,` the `SelectedValue` is set to the `SocialMedia.ID.`


{% tabs %}
{% highlight XAML %}

<editors:SfAutoComplete 
    SelectedValuePath="ID"
    x:Name="autoComplete"
    TextMemberPath="Name"   
    DisplayMemberPath="Name"
    ItemsSource="{Binding SocialMedias}" 
    SelectionChanged="OnSelectionChanged"/>

<TextBlock Text="SelectedValue :"/>
<TextBlock x:Name="selectedValue"/>

{% endhighlight %}
{% highlight C# %}

autoComplete.SelectedValuePath = "ID";
autoComplete.SelectionChanged += OnSelectionChanged;

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight C# %}

private void OnSelectionChanged(object sender, AutoCompleteSelectionChangedEventArgs e)
{
    selectedValue.Text = autoComplete.SelectedValue.ToString();
}

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete with selected value](Selection_images/winui-autoComplete-selectedvalue.png)

## Handle invalid input 

When entered text that does not correspond to a drop-down list item is submitted, the [InputSubmitted](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfAutoComplete.html#Syncfusion_UI_Xaml_Editors_SfAutoComplete_InputSubmitted) event is triggered. The members of [AutoCompleteInputSubmittedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.AutoCompleteInputSubmittedEventArgs.html) provide information about the entered text.

[Text](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.AutoCompleteInputSubmittedEventArgs.html#Syncfusion_UI_Xaml_Editors_AutoCompleteInputSubmittedEventArgs_Text) - Gets the text entered in `AutoComplete`.

[Item](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.AutoCompleteInputSubmittedEventArgs.html#Syncfusion_UI_Xaml_Editors_AutoCompleteInputSubmittedEventArgs_Item) - This property can be used to add the item to the selected item(s) or set to selected item which gets assigned.
If no item is assigned, then in single selection, entered text gets assigned to selected item. In multiple selection, no text will be added to selected items.

[Handled](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.AutoCompleteInputSubmittedEventArgs.html#Syncfusion_UI_Xaml_Editors_AutoCompleteInputSubmittedEventArgs_Handled) - When set to `true`, the framework will not automatically update the selected item or selected item(s) of the `AutoComplete` to the new value.

By using the following code sample, you will display a dialogue box when submitting input (Snap chat) that does not match the assigned `ItemsSource`.

{% tabs %}
{% highlight XAML %}

<editors:SfAutoComplete 
    InputSubmitted="OnAutoCompleteInputSubmitted"
    ItemsSource="{Binding SocialMedias}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"    
    x:Name="autoComplete"
    Width="250">
</editors:SfAutoComplete>

{% endhighlight %}

{% highlight C# %}

autoComplete.InputSubmitted += OnAutoCompleteInputSubmitted;

{% endhighlight %}
{% endtabs %}

The `InputSubmitted` event can be handled as follows.

{% tabs %}
{% highlight C# %}

/// <summary>
/// Occurs when the user submits some text that does not correspond to an item in the `AutoComplete` drop-down list.
/// </summary>
private async void OnAutoCompleteInputSubmitted(object sender, Syncfusion.UI.Xaml.Editors.AutoCompleteInputSubmittedEventArgs e)
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

![WinUI AutoComplete invalid input submission](Selection_images/winui-autoComplete-invalid-input-submission.png)


## Hide clear button in the editor

By default, the clear button `X` will be displayed in the editor of the `AutoComplete` control, which can be used to clear the entered input. Hide the clear button in `AutoComplete` control using the [ShowClearButton](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.DropDownListBase.html#Syncfusion_UI_Xaml_Editors_DropDownListBase_ShowClearButton) property. The default value of `ShowClearButton` property value is `true`.

{% tabs %}
{% highlight XAML %}

<editors:SfAutoComplete 
    ShowClearButton="false"
    ItemsSource="{Binding SocialMedias}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"    
    x:Name="autoComplete"
    Width="250">
</editors:SfAutoComplete>

{% endhighlight %}

{% highlight C# %}

autoComplete.ShowClearButton = false;

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete hide clear button](Selection_images/winui-AutoComplete-hideclearbutton.png)