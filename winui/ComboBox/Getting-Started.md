---
layout: post
title: Getting Started with WinUI ComboBox | Syncfusion
description: Learn how to get started with Syncfusion WinUI ComboBox (SfComboBox) control, its elements, and more in here.
platform: WinUI
control: SfComboBox
documentation: ug
---

# Getting Started with WinUI ComboBox

This section explains the steps required to add the ComboBox control and binding data in ComboBox control. This section covers only basic features needed to get started with Syncfusion ComboBox control.

## Creating an application with WinUI ComboBox

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop).
2.  Download and refer the following NuGet package in the project.

    * [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI)

3. Import the control namespace `Syncfusion.UI.Xaml.Editors` in XAML or C# code.
4. Initialize the `SfComboBox` control.

{% tabs %}
{% highlight xaml %}

<Window
    x:Class="GettingStarted.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:editors="using:Syncfusion.UI.Xaml.Editors"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid Name="grid">
        <!--Adding ComboBox control -->
        <editors:SfComboBox Name="sfComboBox"/>
    </Grid>
</Window>

{% endhighlight %}

{% highlight c# %}

using Syncfusion.UI.Xaml.Editors;
namespace GettingStarted
{
    public sealed partial class MainWindow : Window
    {
        public MainPage()
        {
            this.InitializeComponent();
            // Creating an instance of the ComboBox control
            SfComboBox sfComboBox = new SfComboBox();

            grid.Children.Add(sfComboBox);
        }
    }
}

{% endhighlight %}
{% endtabs %}

## Populating items using SfComboBoxItem

You can add the items inside the `ComboBox` control using the `SfComboBoxItem`.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox x:Name="sfComboBox" 
                    Width="250">
    <editors:SfComboBoxItem Content="Badminton"/>
    <editors:SfComboBoxItem Content="Cricket"/>
    <editors:SfComboBoxItem Content="Football"/>
    <editors:SfComboBoxItem Content="Golf"/>
    <editors:SfComboBoxItem Content="Hockey"/>
</editors:SfComboBox>

{% endhighlight %}

{% highlight C# %}

SfComboBox sfComboBox = new SfComboBox();

SfComboBoxItem item1 = new SfComboBoxItem() { Content = "Badminton" };
SfComboBoxItem item2 = new SfComboBoxItem() { Content = "Cricket" };
SfComboBoxItem item3 = new SfComboBoxItem() { Content = "Football" };
SfComboBoxItem item4 = new SfComboBoxItem() { Content = "Golf" };
SfComboBoxItem item5 = new SfComboBoxItem() { Content = "Hockey" };

sfComboBox.Items.Add(item1);
sfComboBox.Items.Add(item2);
sfComboBox.Items.Add(item3);
sfComboBox.Items.Add(item4);
sfComboBox.Items.Add(item5);

this.Content = sfComboBox;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox populating the SfComboBoxItem](GettingStarted_images/winui-combobox-populating-comboBoxItem.gif)

## Populating items through data binding

The ComboBox can bound to an external data source using `ItemsSource` property. Now let us create Model and ViewModel classes to populate ComboBox with SocialMedia details.

**Step 1** Define a simple model class SocialMedia with fields ID and name, and then populate social media data in ViewModel.

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

**Step 2**  Populate data in ComboBox 

Now populate this SocialMediaViewModel data in SfComboBox control by binding with `ItemSource` property. 

{% tabs %}
{% highlight xaml %}

<Window
    x:Class="GettingStarted.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:editors="using:Syncfusion.UI.Xaml.Editors"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid Name="grid">
       <Grid.DataContext>
         <local:SocialMediaViewModel />
       </Grid.DataContext>

        <!--Setting ItemsSource-->
        <editors:SfComboBox x:Name="sfComboBox" 
                            Width="250"
                            ItemsSource="{Binding SocialMedias}" />
    </Grid>
</Window>

{% endhighlight %}

{% highlight C# %}

SfComboBox sfComboBox = new SfComboBox();
sfComboBox.DataContext = new SocialMediaViewModel();
sfComboBox.ItemsSource = (sfComboBox.DataContext as SocialMediaViewModel).SocialMedias;

{% endhighlight %}
{% endtabs %}

N> Set the SocialMediaViewModel instance as the DataContext of your control; this is done to bind properties of SocialMediaViewModel to SfComboBox.

**Step 3** Setting TextMemberPath and DisplayMemberPath

The combo box control is populated with the list of social medias. But the SocialMedia model contains two properties ID and Name so it is necessary to intimate by which property it should display value in the selection box portion of the ComboBox control, when an item is selected.

`TextMemberPath` - This property path is used to get the value for display in the selection box portion of the combo box control, when an item is selected. The default value is `String.Empty`.
`DisplayMemberPath` - This property path is used to the name or path of the property displayed for each data item in the dropdown list. The default value is `String.Empty`.

{% tabs %}
{% highlight C# %}

sfComboBox.DisplayMemberPath = "Name";
sfComboBox.TextMemberPath = "Name";

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox populating using data binding](GettingStarted_images/winui-combobox-populating-data-binding.png)

## Multi selection

The SfComboBox allows you to select multiple values from the drop-down list. The multi-select combo box mode can be enabled by setting the `SelectionMode` property as `Multiple`. Checkboxes can be used to represent selected items.

You can handle the selection operations with the help of `SelectionChanged` event of SfComboBox.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox x:Name="sfComboBox"
                    Width="250"
                    SelectionMode="Multiple"
                    ItemsSource="{Binding SocialMedias}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name">
</editors:SfComboBox>

{% endhighlight %}
{% highlight C# %}

sfComboBox.SelectionMode = ComboBoxSelectionMode.Multiple;

{% endhighlight %}
{% endtabs %}

![Multiselect ComboBox control](GettingStarted_images/winui-combobox-multi-selection.png)

## Editing

The ComboBox control supports editable and non-editable modes to choose items. To enable editing functionality, you have to set the `IsEditable` property as `true`. The default value is false.

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

![WinUI ComboBox choose item using editing](GettingStarted_images/winui-combobox-edit-mode.png)

## Searching

The ComboBox control provides support to highlights the first item which fits the user input in the drop down list based on `TextSearchMode` property. To disable searching functionality, you have to set the `IsTextSearchEnabled` property as `false`. The default value is true.

## Filtering

The ComboBox control provides support to filter the items in the dropdown based on the starting letter or whether they contain a specific letter. To enable filtering functionality, you have to set the `IsFilteringEnabled` property as true. The default value is false.

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

## SelectionBox UI

You can change the selection box appearance by using the `SelectionBoxItemTemplate`. The default value of `SelectionBoxItemTemplate` is `null`.

N> `SelectionBoxItemTemplate` does not have effect when `IsEditable` is `true`.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox x:Name="sfComboBox"
                    Width="250"
                    SelectionMode="Multiple"
                    ItemsSource="{Binding SocialMedias}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name">
    <editors:SfComboBox.SelectionBoxItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
                <TextBlock Margin="12,5,0,6" 
                           FontFamily="{ThemeResource ContentControlThemeFontFamily}"
                           FontSize="{ThemeResource ControlContentThemeFontSize}"
                           Text="Selected Social Media Count:" />
                <TextBlock Margin="2,5,0,0"
                           FontFamily="{ThemeResource ContentControlThemeFontFamily}"
                           FontSize="{ThemeResource ControlContentThemeFontSize}"
                           Text="{Binding ElementName=sfComboBox, Path=SelectedItems.Count}" />
            </StackPanel>
        </DataTemplate>
    </editors:SfComboBox.SelectionBoxItemTemplate>
</editors:SfComboBox>

{% endhighlight %}
{% endtabs %}

![Custom UI of Selection Box using SelectionBoxItemTemplate](GettingStarted_images/winui-combobox-selectionBoxItemTemplate.png)
