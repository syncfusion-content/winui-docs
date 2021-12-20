---
layout: post
title: UI Customization in WinUI AutoComplete control | Syncfusion
description: Learn here all about UI customization support in Syncfusion WinUI AutoComplete (multi-select AutoComplete) control into WinUI application and its basic features.
platform: winui
control: SfAutoComplete
documentation: ug
---

# UI Customization in WinUI AutoComplete (SfAutoComplete)

This section explains different UI customization available in the `AutoComplete` control.

## Header for AutoComplete

The `AutoComplete` control header can be changed by using the `Header` or `HeaderTemplate` properties. The default value of `HeaderTemplate` is `null` and `Header` is `null`.

{% tabs %}
{% highlight XAML %}

<editors:SfAutoComplete
    Header="Favourite Social Media"
    ItemsSource="{Binding SocialMedias}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"
    Width="250"
    x:Name="autoComplete">
    <editors:SfAutoComplete.HeaderTemplate>
        <DataTemplate>
            <TextBlock
                Foreground="Red"
                FontWeight="SemiBold"
                FontSize="16"
                Text="{Binding}" />
        </DataTemplate>
    </editors:SfAutoComplete.HeaderTemplate>
</editors:SfAutoComplete>

{% endhighlight %}
{% highlight C# %}

autoComplete.Header = "Favourite Social Media";

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete displays header](Styling_images/winui-autocomplete-headerTemplate.png)

## Description for AutoComplete

The `AutoComplete` control description can be changed by using the `Description` property. The default value of `Description` is `null`.

{% tabs %}
{% highlight XAML %}

<editors:SfAutoComplete
    Description="This will be added to your profile."
    Header="Favourite Social Media"
    ItemsSource="{Binding SocialMedias}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"
    Width="250"
    x:Name="autoComplete"/>

{% endhighlight %}
{% highlight C# %}

autoComplete.Description = "This will be added to your profile.";
autoComplete.Header = "Favourite Social Media";

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete displays description](Styling_images/winui-autocomplete-description.png)

## Placeholder text

You can prompt the user with any information by using the `PlaceholderText` property. This text will be displayed only when no item is selected or edit text is empty. The default value of `PlaceholderText` property is `string.Empty` (No string will be displayed).

{% tabs %}
{% highlight xaml %}

<editors:SfAutoComplete
    PlaceholderText="Select a social media"
    ItemsSource="{Binding SocialMedias}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"
    Width="250"
    x:Name="autoComplete"/>

{% endhighlight %}
{% highlight C# %}

autoComplete.PlaceholderText = "Select a social media";

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete Watermark Text](Styling_images/winui-autocomplete-watermark_text.png)

### Change foreground of placeholder text

The placeholder texts’ foreground can be changed by using the `PlaceholderForeground` property. The default value of `PlaceholderForeground` property is `null`.

{% tabs %}
{% highlight xaml %}

<editors:SfAutoComplete
    PlaceholderForeground="Red"
    PlaceholderText="Select a social media"
    ItemsSource="{Binding SocialMedias}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"
    Width="250"
    x:Name="autoComplete"/>

{% endhighlight %}
{% highlight C# %}

autoComplete.PlaceholderForeground = new SolidColorBrush(Colors.Red);

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete placeholder text foreground](Styling_images/winui-autocomplete-placeholder-text-foreground.png)

## Customize the editing TextBox

The appearance of the editing textbox in `AutoComplete` control can be customized by using the `TextBoxStyle` property. The default value of `TextBoxStyle` is `null`.

N> `TextBoxStyle` will only have an effect in single selection mode.

{% tabs %}
{% highlight XAML %}

<editors:SfAutoComplete
    SelectionMode="Single"
    ItemsSource="{Binding SocialMedias}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"
    ShowClearButton="False"    
    Width="250"
    x:Name="autoComplete">
   <editors:SfAutoComplete.TextBoxStyle>
        <Style TargetType="TextBox">                   
            <Style.Setters>              
                <Setter Property="SelectionHighlightColor" Value="Green"/>  
                <Setter Property="BorderThickness" Value="0"/> 
            </Style.Setters>
        </Style>
    </editors:SfAutoComplete.TextBoxStyle>
</editors:SfAutoComplete>

{% endhighlight %}
{% endtabs %}

![Styling the editing textBox using TextBoxStyle.](Styling_images/winui-autocomplete-textboxstyle.png)

## Customize the Dropdown (suggestion) item 

The `ItemTemplate` property helps you to decorate drop-down items using the custom templates. The default value of `ItemTemplate` is `null`. The following example shows how to customize drop-down items using templates.


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
        this.Employees.Add(new Employee
        {
            Name = "Anne Dodsworth",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/AutoComplete/Employees/Employee1.png", UriKind.RelativeOrAbsolute)),
            Designation= "Developer",
            ID="E001",
            Country= "USA",
        });
        this.Employees.Add(new Employee
        {
            Name = "Andrew Fuller",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/AutoComplete/Employees/Employee7.png", UriKind.RelativeOrAbsolute)),
            Designation = "Team Lead",
            ID = "E002",
            Country = "England",
        });
        this.Employees.Add(new Employee
        {
            Name = "Emilio Alvaro",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/AutoComplete/Employees/Employee5.png", UriKind.RelativeOrAbsolute)),
            Designation = "Product Manager",
            ID = "E003",
            Country = "England",
        });
        this.Employees.Add(new Employee
        {
            Name = "Janet Leverling",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/AutoComplete/Employees/Employee3.png", UriKind.RelativeOrAbsolute)),
            Designation = "HR",
            ID = "E004",
            Country = "USA",
        });
        this.Employees.Add(new Employee
        {
            Name = "Laura Callahan",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/AutoComplete/Employees/Employee2.png", UriKind.RelativeOrAbsolute)),
            Designation = "Product Manager",
            ID = "E005",
            Country = "USA",
        });
        this.Employees.Add(new Employee
        {
            Name = "Margaret Peacock",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/AutoComplete/Employees/Employee6.png", UriKind.RelativeOrAbsolute)),
            Designation = "Developer",
            ID = "E006",
            Country = "USA",
        });
        this.Employees.Add(new Employee
        {
            Name = "Michael Suyama",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/AutoComplete/Employees/Employee9.png", UriKind.RelativeOrAbsolute)),
            Designation = "Team Lead",
            ID = "E007",
            Country = "USA",
        });
        this.Employees.Add(new Employee
        {
            Name = "Nancy Davolio",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/AutoComplete/Employees/Employee4.png", UriKind.RelativeOrAbsolute)),
            Designation = "Developer",
            ID = "E008",
            Country = "USA",
        });
        this.Employees.Add(new Employee
        {
            Name = "Robert King",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/AutoComplete/Employees/Employee8.png", UriKind.RelativeOrAbsolute)),
            Designation = "Developer",
            ID = "E009",
            Country = "England",
        });
        this.Employees.Add(new Employee
        {
            Name = "Steven Buchanan",
            ProfilePicture = new BitmapImage(new Uri(@"ms-appx:///Assets/AutoComplete/Employees/Employee10.png", UriKind.RelativeOrAbsolute)),
            Designation = "CEO",
            ID = "E010",
            Country = "England",
        });
    }
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight XAML %}

<editors:SfAutoComplete
    TextMemberPath="Name"
    DisplayMemberPath="Name"
    ItemsSource="{Binding Employees}"
    Width="250"
    x:Name="autoComplete">
    <editors:SfAutoComplete.DataContext>
        <local:EmployeeViewModel/>
    </editors:SfAutoComplete.DataContext>
    <editors:SfAutoComplete.ItemTemplate>
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
    </editors:SfAutoComplete.ItemTemplate>
</editors:SfAutoComplete>

{% endhighlight %}
{% endtabs %}

![Custom UI of dropdown items using ItemTemplate.](Styling_images/winui-autocomplete-itemtemplate.png)

### Customize Dropdown (suggestion) items based on condition

The `ItemTemplateSelector` property helps you to decorate drop-down items conditionally based on its content using the custom templates. The default value of `ItemTemplateSelector` is `null`.

{% tabs %}
{% highlight C# %}

public class EmployeeTemplateSelector : DataTemplateSelector
{
    public DataTemplate EmployeeTemplate1 { get; set; }
    public DataTemplate EmployeeTemplate2 { get; set; }
    
    protected override DataTemplate SelectTemplateCore(object item, DependencyObject container)
    {
        var employeeName = (item as Employee).Name;
        if (employeeName.ToString() == "Anne Dodsworth" || employeeName.ToString() == "Emilia Alvaro" ||
            employeeName.ToString() == "Laura Callahan")
        {
            return EmployeeTemplate1;
        }
        else
        {
            return EmployeeTemplate2;
        }
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
    
    <editors:SfAutoComplete 
        TextMemberPath="Name"
        ItemsSource="{Binding Employees}"
        ItemTemplateSelector="{StaticResource employeeTemplateSelector}"        
        Width="250" 
        x:Name="autoComplete">
        <editors:SfAutoComplete.DataContext>
            <local:EmployeeViewModel/>
        </editors:SfAutoComplete.DataContext>
    </editors:SfAutoComplete>
</Grid>

{% endhighlight %}
{% endtabs %}

![Different custom UI of dropdown items using ItemTemplateSelector](Styling_images/winui-autocomplete-custom-itemtemplate.png)

## How to change DropDown MaxHeight

The maximum height of the drop-down can be changed by using the `MaxDropDownHeight` property of `AutoComplete` control. The default value of `MaxDropDownHeight` property is `288`. 

 N> If the `MaxDropDownHeight` is too small compared to the populated items, scroll viewer will be automatically shown to navigate the hidden items.

{% tabs %}
{% highlight xaml %}

<editors:SfAutoComplete 
    MaxDropDownHeight="530"
    ItemsSource="{Binding Employees}"
    ItemTemplateSelector="{StaticResource employeeTemplateSelector}"
    DisplayMemberPath="Name"
    TextMemberPath="Name"  
    Width="250"  
    x:Name="autoComplete">
    <editors:SfAutoComplete.DataContext>
        <local:EmployeeViewModel/>
    </editors:SfAutoComplete.DataContext>
</editors:SfAutoComplete>

{% endhighlight %}
{% highlight C# %}

autoComplete.MaxDropDownHeight = 530;

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete maximum drop down height changed](Styling_images/winui-autocomplete-maxdropdownheight.png)
