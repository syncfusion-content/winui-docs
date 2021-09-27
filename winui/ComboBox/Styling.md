---
layout: post
title: Styling in WinUI ComboBox control | Syncfusion
description: Learn here all about styling support in Syncfusion WinUI ComboBox(SfComboBox) control into WinUI application and its basic features.
platform: winui
control: SfComboBox
documentation: ug
---

# Styling in WinUI ComboBox (SfComboBox)

This section explains different UI customization available in SfComboBox.

## Header for ComboBox

The ComboBox control header can be changed by using the `Header` or `HeaderTemplate` properties. The default value of `HeaderTemplate` is `null` and `Header` is `null`.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox
    Width="250"
    Header="Favourite Social Media"
    ItemsSource="{Binding SocialMedias}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"
    SelectedIndex="2"
    x:Name="sfComboBox">
    <editors:SfComboBox.DataContext>
        <local:SocialMediaViewModel/>
    </editors:SfComboBox.DataContext>
    <editors:SfComboBox.HeaderTemplate>
        <DataTemplate>
            <TextBlock
                Foreground="Red"
                FontWeight="SemiBold"
                FontSize="16"
                Text="{Binding}" />
        </DataTemplate>
    </editors:SfComboBox.HeaderTemplate>
</editors:SfComboBox>

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox displays header](Styling_images/winui-combobox-headerTemplate.png)

## Description for ComboBox

The ComboBox control description can be changed by using the `Description` property. The default value of `Description` is `null`.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox
    Width="280"
    Header="Favourite Social Media"
    ItemsSource="{Binding SocialMedias}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"
    SelectedIndex="2"
    Description="Instagram is an online photo sharing service."
    x:Name="sfComboBox">
    <editors:SfComboBox.DataContext>
        <local:SocialMediaViewModel/>
    </editors:SfComboBox.DataContext>
    <editors:SfComboBox.HeaderTemplate>
        <DataTemplate>
            <TextBlock
                Foreground="Red"
                FontWeight="SemiBold"
                FontSize="16"
                Text="{Binding}" />
        </DataTemplate>
    </editors:SfComboBox.HeaderTemplate>
</editors:SfComboBox>

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox displays description](Styling_images/winui-combobox-description.png)

## Placeholder text

You can prompt the user with any information by using the `PlaceholderText` property. This text will be displayed only when no item is selected or edit text is empty. The default value of `PlaceholderText` property is **string.Empty** (No string will be displayed).

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox
    Width="250"
    ItemsSource="{Binding SocialMedias}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"
    PlaceholderText="Select a social media"
    x:Name="sfComboBox"/>

{% endhighlight %}
{% highlight C# %}

sfComboBox.PlaceholderText = "Select a social media";

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox Watermark Text](Styling_images/winui-combobox-watermark_text.png)

### Change foreground of Placeholder Text

The placeholder text's foreground can be changed by using the `PlaceholderForeground` property. The default value of `PlaceholderForeground` property is **null**.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox
    Width="250"
    ItemsSource="{Binding SocialMedias}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"
    PlaceholderForeground="Red"
    PlaceholderText="Select a social media"
    x:Name="sfComboBox"/>

{% endhighlight %}
{% highlight C# %}

sfComboBox.PlaceholderForeground = new SolidColorBrush(Colors.Red);

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox placeholder text foreground](Styling_images/winui-combobox-placeholder-text-foreground.png)

## Customize edit mode TextBox

The appearance of the editing textbox in `ComboBox` control can be customized by using the `TextBoxStyle` property. The default value of `TextBoxStyle` is `null`.

N> `TextBoxStyle` will have effect only in single selection editable mode.

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox
    Width="250"
    IsEditable="True"
    SelectionMode="Single"
    ItemsSource="{Binding SocialMedias}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"
    ShowClearButton="False"
    x:Name="sfComboBox">
    <editors:SfComboBox.TextBoxStyle>
        <Style TargetType="TextBox">                   
            <Style.Setters>              
                <Setter Property="SelectionHighlightColor" Value="Green"/>  
                <Setter Property="BorderThickness" Value="0"/> 
            </Style.Setters>
        </Style>
    </editors:SfComboBox.TextBoxStyle>
</editors:SfComboBox>

{% endhighlight %}
{% endtabs %}

![Styling the editing textBox using TextBoxStyle](Styling_images/winui-combobox-textBoxStyle.png)

## Styling ComboBoxItem

The ComboBox control allows to customize the style of `ComboBoxItem` generated in drop down by using the `ItemContainerStyle` property. The default value of `ItemContainerStyle` is `null`. 

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox
    Width="250"
    IsEditable="True"
    ItemsSource="{Binding SocialMedias}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"
    PlaceholderText="Select a social media"
    x:Name="sfComboBox">
    <editors:SfComboBox.ItemContainerStyle>
        <Style TargetType="editors:SfComboBoxItem">
            <Setter Property="Foreground" Value="Red"/>
            <Setter Property="Background" Value="LightCyan"/>
            <Setter Property="FontStyle" Value="Italic"/>
        </Style>
    </editors:SfComboBox.ItemContainerStyle>
</editors:SfComboBox>

{% endhighlight %}
{% endtabs %}

![Custom UI of ComboBoxItem using ItemContainerStyle](Styling_images/winui-combobox-itemContainerStyle.png)

### Style ComboBoxItem based on condition   

The ComboBox control allows to customize the style of `ComboBoxItem` conditionally based on its content by using the `ItemContainerStyleSelector` property. The default value of `ItemContainerStyleSelector` is `null`. 

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
        this.SocialMedias.Add(new SocialMedia() { Name = "Tumblr", ID = 5 });
        this.SocialMedias.Add(new SocialMedia() { Name = "Twitter", ID = 6 });
        this.SocialMedias.Add(new SocialMedia() { Name = "Vimeo", ID = 7 });
        this.SocialMedias.Add(new SocialMedia() { Name = "WhatsApp", ID = 8 });
        this.SocialMedias.Add(new SocialMedia() { Name = "YouTube", ID = 9 });
    }
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight c# %}

public class SocialMediaStyleSelector : StyleSelector
{
    public Style MediaStyle1 { get; set; }
    public Style MediaStyle2 { get; set; }
    protected override Style SelectStyleCore(object item, DependencyObject container)
    {
        var mediaItem = (item as SocialMedia).Name;
        if (mediaItem.ToString() == "Facebook" || mediaItem.ToString() == "Instagram" ||
            mediaItem.ToString() == "Twitter" || mediaItem.ToString() == "WhatsApp" ||
            mediaItem.ToString() == "Skype")
        {
            return MediaStyle1;
        }           
        else
        {
            return MediaStyle2;
        }
    }
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight XAML %}

<Grid>
    <Grid.Resources>
        <Style x:Key="MediaStyle1" TargetType="editors:SfComboBoxItem">
            <Setter Property="Foreground" Value="Blue"/>
            <Setter Property="Background" Value="LightCyan"/>
            <Setter Property="Content" Value="{Binding}"/>
        </Style>
        <Style x:Key="MediaStyle2" TargetType="editors:SfComboBoxItem">
            <Setter Property="Foreground" Value="Red"/>
            <Setter Property="Background" Value="LightCyan"/>
            <Setter Property="Content" Value="{Binding}"/>
        </Style>
        <local:SocialMediaStyleSelector x:Key="socialMediaStyleSelector" 
                                        MediaStyle1="{StaticResource MediaStyle1}"
                                        MediaStyle2="{StaticResource MediaStyle2}"/>
    </Grid.Resources>
    <editors:SfComboBox x:Name="sfComboBox"
        Width="250"
        PlaceholderText="Select a social media"
        IsEditable="True" 
        ItemsSource="{Binding SocialMedias}"
        ItemContainerStyleSelector="{StaticResource socialMediaStyleSelector}"
        DisplayMemberPath="Name"
        TextMemberPath="Name">
    </editors:SfComboBox>
</Grid>

{% endhighlight %}
{% endtabs %}

![Different custom UI of ComboBoxItem using ItemContainerStyleSelector](Styling_images/winui-combobox-itemContainerStyleSelector.png)

## Customize ComboBoxItem 

The `ItemTemplate` property helps to decorate drop down items with custom templates. The default value of `ItemTemplate` is `null`. Below example shows, how to add image or custom control in drop down items using templates.

{% tabs %}
{% highlight C# %}

//Model.cs
public class Employee
{
    public string Name { get; set; }
    public BitmapImage ProfilePicture { get; set; }
    public string Designation { get; set; }
}

//ViewModel.cs
public class EmployeeViewModel
{
    public ObservableCollection<Employee> Employees { get; set; }
    public EmployeeViewModel()
    {
        this.Employees = new ObservableCollection<Employee>();
        this.Employees.Add(new Employee {
            Name = "Anne Dodsworth",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/Employees/AnneDodsworth.png",
                                                 UriKind.RelativeOrAbsolute)),
            Designation = "Developer"
        });
        this.Employees.Add(new Employee {
            Name = "Andrew Fuller",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/Employees/AndrewFuller.png",
                                                 UriKind.RelativeOrAbsolute)),
            Designation = "Team Lead"
        });
        this.Employees.Add(new Employee {
            Name = "Emilia Alvaro",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/Employees/EmiliaAlvaro.png",
                                                 UriKind.RelativeOrAbsolute)),
            Designation = "Product Manager"
        });
        
        this.Employees.Add(new Employee {
            Name = "Janet Leverling",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/Employees/JanetLeverling.png",
                                                 UriKind.RelativeOrAbsolute)),
            Designation = "HR"
        });
        this.Employees.Add(new Employee {
            Name = "Laura Callahan",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/ComboBox/Employees/LauraCallahan.png",
                                                 UriKind.RelativeOrAbsolute)),
            Designation = "Product Manager"
        });
    }
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight XAML %}

<editors:SfComboBox
    x:Name="sfComboBox"
    Width="250"
    TextMemberPath="Name"
    IsEditable="True"
    ItemsSource="{Binding Employees}">
    <editors:SfComboBox.DataContext>
        <local:EmployeeViewModel/>
    </editors:SfComboBox.DataContext>
    <editors:SfComboBox.ItemTemplate>
        <DataTemplate>
            <Grid
                Margin="0,5"
                HorizontalAlignment="Stretch"
                VerticalAlignment="Stretch">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="48"/>
                    <ColumnDefinition Width="*"/>
                </Grid.ColumnDefinitions>
                <Image 
                    Grid.Column="0"
                    HorizontalAlignment="Center"
                    VerticalAlignment="Center" 
                    Source="{Binding ProfilePicture}" 
                    Stretch="Uniform"/>
                <StackPanel
                    Grid.Column="1"
                    Margin="15,0,0,0"
                    HorizontalAlignment="Left"
                    VerticalAlignment="Center">
                    <TextBlock 
                        Opacity="0.87"
                        FontSize="14"
                        Text="{Binding Name}"/>
                    <TextBlock 
                        Opacity="0.54"
                        FontSize="12"
                        Text="{Binding Designation}"/>
                </StackPanel>
            </Grid>
        </DataTemplate>
    </editors:SfComboBox.ItemTemplate>
</editors:SfComboBox>

{% endhighlight %}
{% endtabs %}

![Custom UI of ComboboxItem using ItemTemplate](Styling_images/winui-combobox-itemTemplate.png)

### Customize ComboBoxItem based on condition

The `ItemTemplateSelector` property helps to decorate drop down items conditionally based on its content with custom templates. The default value of `ItemTemplateSelector` is `null`.

{% tabs %}
{% highlight C# %}

//Model.cs
public class Employee
{
    public string Name { get; set; }
    public BitmapImage ProfilePicture { get; set; }
    public string Designation { get; set; }
}

//ViewModel.cs
public class EmployeeViewModel
{
    public ObservableCollection<Employee> Employees { get; set; }
    public EmployeeViewModel()
    {
        this.Employees = new ObservableCollection<Employee>();
        this.Employees.Add(new Employee {
            Name = "Anne Dodsworth",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/Employees/AnneDodsworth.png",
                                                 UriKind.RelativeOrAbsolute)),
            Designation = "Developer"
        });
        this.Employees.Add(new Employee {
            Name = "Andrew Fuller",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/Employees/AndrewFuller.png",
                                                 UriKind.RelativeOrAbsolute)),
            Designation = "Team Lead"
        });
        this.Employees.Add(new Employee {
            Name = "Emilia Alvaro",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/Employees/EmiliaAlvaro.png",
                                                 UriKind.RelativeOrAbsolute)),
            Designation = "Product Manager"
        });
        
        this.Employees.Add(new Employee {
            Name = "Janet Leverling",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/Employees/JanetLeverling.png",
                                                 UriKind.RelativeOrAbsolute)),
            Designation = "HR"
        });
        this.Employees.Add(new Employee {
            Name = "Laura Callahan",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/ComboBox/Employees/LauraCallahan.png",
                                                 UriKind.RelativeOrAbsolute)),
            Designation = "Product Manager"
        });
    }
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight XAML %}

<Grid>
    <Grid.Resources>
        <DataTemplate x:Key="employeeTemplate1">
            <Grid Margin="0,5">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="48"/>
                    <ColumnDefinition Width="*"/>
                </Grid.ColumnDefinitions>
                <Image 
                    Grid.Column="0"
                    Source="{Binding ProfilePicture}" 
                    Stretch="Uniform"/>
                <StackPanel
                    Grid.Column="1"
                    Margin="15,0,0,0">
                    <TextBlock 
                        Foreground="Blue"
                        Opacity="0.87"
                        FontSize="14"
                        Text="{Binding Name}"/>
                    <TextBlock 
                        Foreground="Coral"
                        Opacity="0.54"
                        FontSize="12"
                        Text="{Binding Designation}"/>
                </StackPanel>
            </Grid>
        </DataTemplate>
        
        <DataTemplate x:Key="employeeTemplate2">
            <Grid Margin="0,5">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="48"/>
                    <ColumnDefinition Width="*"/>
                </Grid.ColumnDefinitions>
                <Image 
                    Grid.Column="0" 
                    Source="{Binding ProfilePicture}" 
                    Stretch="Uniform"/>
                <StackPanel
                    Grid.Column="1"
                    Margin="15,0,0,0">
                    <TextBlock
                        Foreground="Red"
                        Opacity="0.87"
                        FontSize="14"
                        Text="{Binding Name}"/>
                    <TextBlock 
                        Foreground="Green"
                        Opacity="0.54"
                        FontSize="12"
                        Text="{Binding Designation}"/>
                </StackPanel>
            </Grid>
        </DataTemplate>

        <local:EmployeeTemplateSelector
            x:Key="employeeTemplateSelector"
            EmployeeTemplate1="{StaticResource employeeTemplate1}"
            EmployeeTemplate2="{StaticResource employeeTemplate2}"/>
    </Grid.Resources>
    <editors:SfComboBox 
        Width="250" 
        TextMemberPath="Name"
        ItemsSource="{Binding Employees}"
        PlaceholderText="Select an employee"
        IsEditable="True"            
        ItemTemplateSelector="{StaticResource employeeTemplateSelector}"
        x:Name="sfComboBox">
        <editors:SfComboBox.DataContext>
            <local:EmployeeViewModel/>
        </editors:SfComboBox.DataContext>
    </editors:SfComboBox>
</Grid>

{% endhighlight %}
{% endtabs %}

![Different custom UI of ComboBoxItem using ItemTemplateSelector](Styling_images/winui-combobox-itemTemplateSelector.png)

## How to change DropDown MaxHeight?

The maximum height of the drop down can be changed by using the `MaxDropDownHeight` property of ComboBox control. The default value of `MaxDropDownHeight` property is **Auto**. 

 N> If the `MaxDropDownHeight` is too small compared the populated items, scroll viewer will be automatically shown to navigate the hidden items.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox x:Name="sfComboBox"
                    Width="250"
                    IsEditable="true"
                    MaxDropDownHeight="208"
                    ItemsSource="{Binding SocialMedias}"
                    DisplayMemberPath="Name"
                    TextMemberPath="Name">
</editors:SfComboBox>

{% endhighlight %}
{% highlight C# %}

sfComboBox.MaxDropDownHeight = 208;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox dropdown height changed.](Styling_images/winui-combobox-maxdropdownheight.png)
