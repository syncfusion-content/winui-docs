---
layout: post
title: Data Validation | TreeGrid | WinUI | Syncfusion
description: Learn how to validate the data in Syncfusion WinUI TreeGrid ( SfTreeGrid ) control and more details.
platform: winui
control: SfTreeGrid
documentation: ug
---


# Data Validation in WinUI TreeGrid (SfTreeGrid)

SfTreeGrid allows you to validate the data and display hints in case of validation is not passed. In case of invalid data, error icon is displayed at the top right corner of [TreeGridCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCell.html). When mouse over the error icon, error information will be displayed in tooltip.

## Built-in validations

Built-in validations through INotifyDataErrorInfo and Data annotation attributes, can be enabled by setting[SfTreeGrid.DataValidationMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_DataValidationMode) or [TreeGridColumn.DataValidationMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_DataValidationMode) properties. `TreeGridColumn.DataValidationMode` takes priority than `SfTreeGrid.DataValidationMode`.

* `GridValidationMode.InView` - displays error icons and tips alone.
* `GridValidationMode.None` - disables built-in validation support.

### Built-in validation using INotifyDataErrorInfo

You can validate the data by implementing the [INotifyDataErrorInfo](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.inotifydataerrorinfo?view=net-5.0) interface in model class.

{% tabs %}
{% highlight c# %}
public class EmployeeInfo : INotifyDataErrorInfo
{

    private string _title;

    public string Title
    {
        get { return _title; }
        set { _title = value; }
    }

    private List<string> errors = new List<string>();

    public IEnumerable<object> GetErrors(string propertyName)
    {
        if (!propertyName.Equals("Title"))
            return null;

        if (this.Title.Contains("Purchasing") )
            errors.Add("Invalid Title");

        return errors;
    }

    public bool HasErrors
    {
        get
        {
            return false;
        }
    }

    public event EventHandler<DataErrorsChangedEventArgs> ErrorsChanged;
}
{% endhighlight %}
{% endtabs %}

Enable built-in validation support by setting `SfTreeGrid.DataValidationMode` or `TreeGridColumn.DataValidationMode` property `InView`.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfTreeGrid Name="treeGrid" 
                        ChildPropertyName="ReportsTo"
                        ParentPropertyName="ID"
                        AllowEditing="True"
                        DataValidationMode="InView"
                        ItemsSource="{Binding Employees}"
                        SelfRelationRootValue="-1" />
{% endhighlight %}
{% highlight c# %}
treeGrid.DataValidationMode = GridValidationMode.InView;
{% endhighlight %}
{% endtabs %}

![Displaying validation based on conditions in WinUI SfTreeGrid using INotifyDataErrorInfo](Data-Validation_images/Data-Validation_img1.png)

### Built-in validation using Data Annotation

You can validate the data using data annotation attributes by setting `SfTreeGrid.DataValidationMode` or `TreeGridColumn.DataValidationMode` property to `InView`.

#### Using different annotations

The numeric type like int, double, decimal properties can be validated using [Range attributes](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.rangeattribute.aspx).

{% tabs %}
{% highlight c# %}
private int  _id;
[Range(3, 6, ErrorMessage = "OrderID between 3 and 6 alone processed")]

public int ID
{
    get { return _id; }
    set { _id = value; }
}

{% endhighlight %}
{% endtabs %}

The string type property can be validated using [Required](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.requiredattribute.aspx), [String Length attributes](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.stringlengthattribute.aspx)

{% tabs %}
{% highlight c# %}
private string _title;

[Required]

public string Title
{
    get { return _title; }
    set { _title = value; }
}

private string _lastName;

[StringLength(6)]

public string LastName
{
    get { return _lastName; }
    set { _lastName = value; }
}
{% endhighlight %}
{% endtabs %}

The data that has heterogeneous type (combination of number, special character) can be validated using [RegularExpressions](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.regularexpressionattribute.aspx).

{% tabs %}
{% highlight c# %}
[RegularExpressionAttribute(@"^[a-zA-Z]{1,40}$", ErrorMessage = "Numbers and special characters not allowed")]

public string FirstName
{
    get { return _firstName; }
    set { _firstName = value; }
}

{% endhighlight %}
{% endtabs %}

## Custom validation through events

You can validate the cells and rows using [CurrentCellValidating](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CurrentCellValidating) and [RowValidating](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_RowValidating) events. SfTreeGrid will not allow user to edit other cell / row if validation failed.

### Cell Validation

You can validate the cells using [CurrentCellValidating](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CurrentCellValidating) event when the cell is edited. `CurrentCellValidating` event occurs when the edited cell tries to commit the data or lose the focus.

[TreeGridCurrentCellValidatingEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCurrentCellValidatingEventArgs.html) provides information to `CurrentCellValidating` event for validating the cell.  
`TreeGridCurrentCellValidatingEventArgs.NewValue` returns the edited value and you can set the validation status using `TreeGridCurrentCellValidatingEventArgs.IsValid` property.

{% tabs %}
{% highlight c# %}
treeGrid.CurrentCellValidating += treeGrid_CurrentCellValidating;

private void treeGrid_CurrentCellValidating(object sender, TreeGridCurrentCellValidatingEventArgs e)
{
    if (e.NewValue.ToString().Equals("11"))
    {
        e.IsValid = false;
        e.ErrorMessage = "ID 11 is invalid";
    }
}
{% endhighlight %}
{% endtabs %}

[SfTreeGrid.CurrentCellValidated](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CurrentCellValidated) event triggered when the cell has finished validating with valid data.

{% tabs %}
{% highlight c# %}
treeGrid.CurrentCellValidated += treeGrid_CurrentCellValidated;

void treeGrid_CurrentCellValidated(object sender, TreeGridCurrentCellValidatedEventArgs e)
{
}
{% endhighlight %}
{% endtabs %}

### Row Validation

You can validate the row using [RowValidating](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_RowValidating) event when the cell is edited. The `RowValidating` event occurs when the edited cells tries to commit the row data or lose the focus.

[TreeGridRowValidatingEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowValidatingEventArgs.html) provides information to `RowValidating` event for validating row. 
`TreeGridRowValidatingEventArgs.RowData` returns the edited value and you can set the validation status using `TreeGridRowValidatingEventArgs.IsValid` property.

{% tabs %}
{% highlight c# %}
treeGrid.RowValidating += treeGrid_RowValidating;

private void TreeGrid_RowValidating(object sender, TreeGridRowValidatingEventArgs e)
{
    var data = e.RowData.GetType().GetProperty("FirstName").GetValue(e.RowData);

    if (data.ToString().Equals("John"))
    {
        e.IsValid = false;
        e.ErrorMessages.Add("FirstName", "FirstName John is invalid");
    }
}
{% endhighlight %}
{% endtabs %}

[SfTreeGrid.RowValidated](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_RowValidated) event triggered when the row has finished validating with valid row data.

{% tabs %}
{% highlight c# %}
treeGrid.RowValidated += treeGrid_RowValidated;

void treeGrid_RowValidated(object sender, TreeGridRowValidatedEventArgs e)
{
}
{% endhighlight %}
{% endtabs %}

## Error icon and tip customization

### Customizing error icon

You can customize the error icon by editing `TreeGridCell` control template. If you want to customize the error icon in expander column, you need to edit the control template of [TreeGridExpanderCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridExpanderCell.html).

#### Change the shape of error icon

You can change the validation error template shape of the `TreeGridCell` by changing the `Data` property of the path in the PART_InValidCellBorder of TreeGridCell.

{% tabs %}
{% highlight xaml %}
<Page.Resources>
    <ResourceDictionary>
        <ResourceDictionary.MergedDictionaries>
            <ResourceDictionary Source="ms-appx:///Syncfusion.Grid.WinUI/SfTreeGrid/Themes/Generic.xaml" />
    </ResourceDictionary.MergedDictionaries>
        <Style TargetType="syncfusion:TreeGridCell">
            <Setter Property="Background" Value="Transparent" />
            <Setter Property="BorderThickness" Value="0,0,1,1" />
            <Setter Property="Padding" Value="0" />
            <Setter Property="Template">
                <Setter.Value>
                    <ControlTemplate TargetType="syncfusion:TreeGridCell">
                        <Grid x:Name="Root"
                            Background="{TemplateBinding Background}"
                            BorderBrush="{TemplateBinding BorderBrush}"
                            BorderThickness="{TemplateBinding BorderThickness}">
                            <ContentPresenter />
                            <Border x:Name="PART_CurrentCellBorder"
                                Background="Transparent"
                                BorderBrush="{TemplateBinding CurrentCellBorderBrush}"
                                BorderThickness="{TemplateBinding CurrentCellBorderThickness}"
                                IsHitTestVisible="False"
                                Visibility="Collapsed" />
                            <Border x:Name="PART_InValidCellBorder"
                                Width="10"
                                Height="10"
                                HorizontalAlignment="Right"
                                VerticalAlignment="Top"
                                Visibility="Collapsed">
                                <ToolTipService.ToolTip>

                                    <ToolTip Background="#FFDB000C"
                                            Placement="Right"
                                            Tag="{TemplateBinding ErrorMessage}"
                                            Template="{StaticResource ValidationToolTipTemplate}" />
                                </ToolTipService.ToolTip>
                                <Path Data="M15.396557,23.044006C14.220558,23.044006 13.268559,23.886993 13.268559,24.927994 13.268559,25.975006 14.220558,26.817001 15.396557,26.817001 16.572557,26.817001 17.523547,25.975006 17.523547,24.927994 17.523547,23.886993 16.572557,23.044006 15.396557,23.044006z M15.467541,5.1819992C15.447552,5.1819992 15.436566,5.1829987 15.436566,5.1829987 13.118533,5.5049973 13.055545,7.3330002 13.055545,7.3330002L13.055545,9.2929993 13.626531,16.539001C13.983558,18.357002 14.243538,19.020004 14.243538,19.020004 15.275555,19.975006 16.203567,19.25 16.203567,19.25 16.976548,18.565994 17.028552,16.962997 17.028552,16.962997 17.956563,9.2929993 17.696553,7.1029968 17.696553,7.1029968 17.608571,5.2839966 15.823561,5.1849976 15.490551,5.1819992 15.481549,5.1819992 15.473553,5.1819992 15.467541,5.1819992z M15.56355,0C15.56355,0 21.710574,4.1259995 31.581613,2.8030014 31.581613,2.8030014 33.634629,26.556992 15.56355,32 15.56355,32 -0.10249132,27.548004 0.00050565118,2.9670029 0.0005058694,2.9670029 10.72555,3.6309967 15.56355,0z"
                                    Fill="Red"
                                    Stretch="Fill" />
                            </Border>
                            <VisualStateManager.VisualStateGroups>
                                <VisualStateGroup x:Name="IndicationStates">
                                    <VisualState x:Name="NoError" />
                                    <VisualState x:Name="HasError">
                                        <VisualState.Setters>
                                            <Setter Target="PART_InValidCellBorder.Visibility" Value="Visible" />
                                        </VisualState.Setters>
                                    </VisualState>
                                </VisualStateGroup>
                                <VisualStateGroup x:Name="CurrentStates">
                                    <VisualState x:Name="Regular" />
                                    <VisualState x:Name="Current">
                                        <VisualState.Setters>
                                            <Setter Target="PART_CurrentCellBorder.Visibility" Value="Visible" />
                                        </VisualState.Setters>
                                    </VisualState>
                                </VisualStateGroup>
                            </VisualStateManager.VisualStateGroups>
                        </Grid>
                    </ControlTemplate>
                </Setter.Value>
            </Setter>
        </Style>
    </ResourceDictionary>
</Page.Resources>
{% endhighlight %}
{% endtabs %}

![Displaying changed validation error icon WinUI SfTreeGrid](Data-Validation_images/Data-Validation_img2.png)

#### Change the color of error icon

You can change the validation error template color of the `TreeGridCell` by changing the `Fill` property of the path in the PART_InValidCellBorder of `TreeGridCell`.

{% tabs %}
{% highlight xaml %}
<Page.Resources>
    <ResourceDictionary>
        <ResourceDictionary.MergedDictionaries>
            <ResourceDictionary Source="ms-appx:///Syncfusion.Grid.WinUI/SfTreeGrid/Themes/Generic.xaml" />
        </ResourceDictionary.MergedDictionaries>
        <Style TargetType="syncfusion:TreeGridCell">
            <Setter Property="Background" Value="Transparent" />
            <Setter Property="BorderThickness" Value="0,0,1,1" />
            <Setter Property="Padding" Value="0" />
            <Setter Property="Template">
                <Setter.Value>
                    <ControlTemplate TargetType="syncfusion:TreeGridCell">
                        <Grid x:Name="Root"
                    Background="{TemplateBinding Background}"
                    BorderBrush="{TemplateBinding BorderBrush}"
                    BorderThickness="{TemplateBinding BorderThickness}">
                            <ContentPresenter />
                            <Border x:Name="PART_CurrentCellBorder"
                        Background="Transparent"
                        BorderBrush="{TemplateBinding CurrentCellBorderBrush}"
                        BorderThickness="{TemplateBinding CurrentCellBorderThickness}"
                        IsHitTestVisible="False"
                        Visibility="Collapsed" />
                            <Border x:Name="PART_InValidCellBorder"
                        Width="10"
                        Height="10"
                        HorizontalAlignment="Right"
                        VerticalAlignment="Top"
                        Visibility="Collapsed">
                                <ToolTipService.ToolTip>
                                    <ToolTip Background="#FFDB000C"
                                    Placement="Right"
                                    Tag="{TemplateBinding ErrorMessage}"
                                    Template="{StaticResource ValidationToolTipTemplate}" />
                                </ToolTipService.ToolTip>
                                <Path Data="M0.5,0.5 L12.652698,0.5 12.652698,12.068006 z"
                                        Fill="Orange"
                                        Stretch="Fill" />
                            </Border>
                            <VisualStateManager.VisualStateGroups>
                                <VisualStateGroup x:Name="IndicationStates">
                                    <VisualState x:Name="NoError" />
                                    <VisualState x:Name="HasError">
                                        <VisualState.Setters>
                                            <Setter Target="PART_InValidCellBorder.Visibility" Value="Visible" />
                                        </VisualState.Setters>
                                    </VisualState>
                                </VisualStateGroup>
                                <VisualStateGroup x:Name="CurrentStates">
                                    <VisualState x:Name="Regular" />
                                    <VisualState x:Name="Current">
                                        <VisualState.Setters>
                                            <Setter Target="PART_CurrentCellBorder.Visibility" Value="Visible" />
                                        </VisualState.Setters>
                                    </VisualState>
                                </VisualStateGroup>
                            </VisualStateManager.VisualStateGroups>
                        </Grid>
                    </ControlTemplate>
                </Setter.Value>
            </Setter>
        </Style>
    </ResourceDictionary>
</Page.Resources>

{% endhighlight %}
{% endtabs %}

![Displaying changed validation error icon color WinUI SfTreeGrid](Data-Validation_images/Data-Validation_img3.png)

### Customizing error tip (Help tip)

You can customize the error tip by editing the style of `ValidationToolTipTemplate`. Get the style of `ValidationToolTipTemplate` by editing the `TreeGridCell` style.

#### Change the background and foreground color of error tip (Help tip)

You can change the error tip background color by setting `Background` property of the border in `ValidationToolTipTemplate`.The error tip foreground color can be changed by setting `Foreground` property of the TextBlock in 'ValidationToolTipTemplate'.

{% tabs %}
{% highlight xaml %}
<ControlTemplate x:Key="ValidationToolTipTemplate">
    <Grid x:Name="PART_ToolTipPresenter"
        Margin="5,0"
        Opacity="0"
        RenderTransformOrigin="0,0">
        <Grid.RenderTransform>
            <TranslateTransform x:Name="Transform" X="-25" />
        </Grid.RenderTransform>
                
        <Border Margin="4,4,-4,-4"
            Background="Transparent"
            CornerRadius="5" />
        <Border Margin="3,3,-3,-3"
            Background="Transparent"
            CornerRadius="4" />
        <Border Margin="2,2,-2,-2"
            Background="Transparent"
            CornerRadius="3" />
        <Border Margin="1,1,-1,-1"
            Background="Transparent"
            CornerRadius="2" />

        <Border Background="Orange" CornerRadius="2" />
        <Border CornerRadius="2" >
            <TextBlock MaxWidth="250"
                    Margin="8,4,8,4"
                    Foreground= "Black"
                    Text="{TemplateBinding Tag}"
                    TextWrapping="Wrap"
                    UseLayoutRounding="false" />
        </Border>
        <VisualStateManager.VisualStateGroups>
            <VisualStateGroup x:Name="OpenStates">
                <VisualStateGroup.Transitions>
                    <VisualTransition GeneratedDuration="0" />
                    <VisualTransition GeneratedDuration="0:0:0.2" To="Opened">
                        <Storyboard>
                            <DoubleAnimation Duration="0:0:0.2"
                                            Storyboard.TargetName="Transform"
                                            Storyboard.TargetProperty="X"
                                            To="0">
                                <DoubleAnimation.EasingFunction>
                                    <BackEase Amplitude=".3" EasingMode="EaseOut" />
                                </DoubleAnimation.EasingFunction>
                            </DoubleAnimation>
                            <DoubleAnimation Duration="0:0:0.2"
                                            Storyboard.TargetName="PART_ToolTipPresenter"
                                            Storyboard.TargetProperty="Opacity"
                                            To="1" />
                        </Storyboard>
                    </VisualTransition>
                </VisualStateGroup.Transitions>
                <VisualState x:Name="Closed">
                    <Storyboard>
                        <DoubleAnimation Duration="0"
                                        Storyboard.TargetName="PART_ToolTipPresenter"
                                        Storyboard.TargetProperty="Opacity"
                                        To="0" />
                    </Storyboard>
                </VisualState>
                <VisualState x:Name="Opened">
                    <Storyboard>
                        <DoubleAnimation Duration="0"
                                        Storyboard.TargetName="Transform"
                                        Storyboard.TargetProperty="X"
                                        To="0" />
                        <DoubleAnimation Duration="0"
                                        Storyboard.TargetName="PART_ToolTipPresenter"
                                        Storyboard.TargetProperty="Opacity"
                                        To="1" />
                    </Storyboard>
                </VisualState>
            </VisualStateGroup>
        </VisualStateManager.VisualStateGroups>
    </Grid>
</ControlTemplate>
{% endhighlight %}
{% endtabs %}

![Displaying changed validation error tooltip WinUI SfTreeGrid](Data-Validation_images/Data-Validation_img4.png)

### Showing error details in RowHeader

SfTreeGrid supports to show the error icon in [TreeGridRowHeaderCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowHeaderCell.html) based on  [INotifyDataErrorInfo.HasErrors](https://msdn.microsoft.com/en-us/library/system.componentmodel.inotifydataerrorinfo.haserrors.aspx) property.


#### Using INotifyDataErrorInfo

You can show the error information in row header by setting [INotifyDataErrorInfo.HasErrors](https://msdn.microsoft.com/en-us/library/system.componentmodel.inotifydataerrorinfo.haserrors.aspx). By default, error message “Row Containing Error” will be displayed.  You can change this by changing `RowErrorMessage` in the **resx** file.

{% tabs %}
{% highlight c# %}
[Display(AutoGenerateField = false)]

public bool HasErrors
{
    get
    {

        if (this.Title.Contains("Purchasing") || this.Title.Contains("Sales"))
            return true;
        return false;
    }
}
{% endhighlight %}
{% endtabs %}

![Displaying validation in rowheader WinUI SfTreeGrid](Data-Validation_images/Data-Validation_img5.png)
