---
layout: post
title: Node CheckBox in WinUI TreeGrid control | Syncfusion
description: Learn here all about Node CheckBox support in Syncfusion WinUI TreeGrid(SfTreeGrid) control and more.
platform: winui
control: SfTreeGrid
documentation: ug
---
# Node CheckBox in WinUI TreeGrid

SfTreeGrid provides support for loading `CheckBox` in the expander cell of each node, which allows the user to check/uncheck the corresponding node. You can display check box in each node by setting [SfTreeGrid.ShowCheckBox](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_ShowCheckBox) property as `true`. It also provides support to process the selection in the context of state of the checkbox based on [SfTreeGrid.CheckBoxSelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CheckBoxSelectionMode) property.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfTreeGrid Name="treeGrid"
                       ChildPropertyName="ReportsTo"
                       ItemsSource="{Binding Employees}"
                       CheckBoxSelectionMode="Default"
                       ShowCheckBox="True"
                       ParentPropertyName="ID"
                       SelfRelationRootValue="-1" />
{% endhighlight %}
{% highlight c# %}
treeGrid.ShowCheckBox = true;
treeGrid.CheckBoxSelectionMode = CheckBoxSelectionMode.Default;
{% endhighlight %}
{% endtabs %}

![Node with CheckBox in WinUI TreeGrid](Node-CheckBox_images/Node-CheckBox_img1.png)

## Indeterminate State Support

You can enable or disable the indeterminate state for node CheckBox using [SfTreeGrid.AllowTriStateChecking](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_AllowTriStateChecking) property.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfTreeGrid Name="treeGrid"
                       ChildPropertyName="ReportsTo"
                       ItemsSource="{Binding Employees}"
                       AllowTriStateChecking="True"
                       ShowCheckBox="True"
                       ParentPropertyName="ID"
                       SelfRelationRootValue="-1" />
{% endhighlight %}
{% highlight c# %}
treeGrid.AllowTriStateChecking = true;
{% endhighlight %}
{% endtabs %}

## Recursive Checking

SfTreeGrid provides support for recursive checking where the checked state of parent node and child nodes is changed recursively based on the state of currently changed node. You can enable recursive checking by setting [SfTreeGrid.EnableRecursiveChecking](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_EnableRecursiveChecking) property as `true`.

* A tree node will be checked only if all its child nodes are checked.
* A tree node will be unchecked if all its child nodes are unchecked. 
* The tree node will be in Indeterminate state in other combinations of its children.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfTreeGrid Name="treeGrid"
                       ChildPropertyName="ReportsTo"
                       ItemsSource="{Binding Employees}"
                       EnableRecursiveChecking="True"
                       ShowCheckBox="True"
                       ParentPropertyName="ID"
                       SelfRelationRootValue="-1" />
{% endhighlight %}
{% highlight c# %}
treeGrid.EnableRecursiveChecking = true;
{% endhighlight %}
{% endtabs %}

![RecursiveChecking mode demo for WinUI TreeGrid ](Node-CheckBox_images/Node-CheckBox_img2.png)

N> Even though [SfTreeGrid.AllowTriStateChecking](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_AllowTriStateChecking) is `false` if [SfTreeGrid.EnableRecursiveChecking](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_EnableRecursiveChecking) is `true`, CheckBox can be in indeterminate state.

## Collapsing CheckBox for certain nodes

You can collapse node CheckBox for certain nodes by editing the control template of [TreeGridExpanderCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridExpanderCell.html) and changing the Checkbox visibility based on condition.

{% tabs %}
{% highlight xaml %}
<Page.Resources>
    <ResourceDictionary>
        <ResourceDictionary.MergedDictionaries>
            <ResourceDictionary Source="ms-appx:///Syncfusion.Grid.WinUI/Control/Themes/Generic.xaml" />
        </ResourceDictionary.MergedDictionaries>
        <local:BoolToVisibilityConverter x:Key="VisibilityConverter" />
        <Style TargetType="syncfusion:TreeGridExpanderCell">
            <Setter Property="Background" Value="Transparent" />
            <Setter Property="BorderThickness" Value="0,0,1,1" />
            <Setter Property="BorderBrush" Value="#CECECE" />
            <Setter Property="Padding" Value="0" />
            <Setter Property="Template">
                <Setter.Value>
                    <ControlTemplate TargetType="syncfusion:TreeGridExpanderCell">
                        <Grid x:Name="Root"
                        BorderBrush="{TemplateBinding BorderBrush}"
                        BorderThickness="{TemplateBinding BorderThickness}">
                            <Grid Margin="{TemplateBinding IndentMargin}">
                                <Grid.ColumnDefinitions>
                                    <ColumnDefinition Width="18" />
                                    <ColumnDefinition Width="Auto" />
                                    <ColumnDefinition Width="*" />
                                </Grid.ColumnDefinitions>
                                <syncfusion:TreeGridExpander x:Name="PART_ExpanderCell"
                                                        Grid.Column="0"
                                                        Width="16"
                                                        Height="16"
                                                        Margin="2,1,0,1"
                                                         HorizontalAlignment="Center"
                                                        VerticalAlignment="Center"
                                                        IsExpanded="{Binding RelativeSource={RelativeSource TemplatedParent},
                                                                            Path=IsExpanded,
                                                                            Mode=TwoWay,
                                                                            UpdateSourceTrigger=PropertyChanged}"
                                                        Visibility="{Binding RelativeSource={RelativeSource TemplatedParent},
                                                                            Path=HasChildNodes,
                                                                            Converter={StaticResource VisibilityConverter},
                                                                            Mode=TwoWay}" />

                                <CheckBox Name="PART_SelectCheckBox"
                                    Grid.Column="1"
                                    Width="18"
                                    Height="18"
                                    MinWidth="22"
                                    Margin="2,0,0,0"
                                    HorizontalAlignment="Center"
                                    VerticalAlignment="Center"
                                    IsEnabled="{Binding RelativeSource={RelativeSource TemplatedParent},
                                                        Path=IsCheckBoxEnabled,
                                                        Mode=TwoWay,
                                                        UpdateSourceTrigger=PropertyChanged}"
                                    IsTabStop="False"
                                    IsThreeState="True"
                                    Visibility="{Binding Path=HasChildNodes,
                                                        RelativeSource={RelativeSource Mode=TemplatedParent},
                                                        Converter={StaticResource VisibilityConverter},
                                                        Mode=TwoWay}" />
                                <Grid Grid.Column="2"
                                Margin="2,0,0,0"
                                Background="{TemplateBinding Background}">
                                    <ContentPresenter />
                                    <Border x:Name="PART_CurrentCellBorder"
                                    Margin="1,0,0,0"
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
                                        Fill="Red"
                                        Stretch="Fill" />
                                    </Border>
                                </Grid>
                            </Grid>
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
{% highlight c# %}
public class BoolToVisibilityConverter : IValueConverter
{

    public object Convert(object value, Type targetType, object parameter, System.Globalization.CultureInfo culture)
    {

        if ((bool)value)
            return Visibility.Visible;
        return Visibility.Collapsed;
    }

    public object ConvertBack(object value, Type targetType, object parameter, System.Globalization.CultureInfo culture)
    {

        if ((Visibility)value == Visibility.Visible)
            return true;
        return false;
    }
}
{% endhighlight %}
{% endtabs %}

Here, node CheckBox is collapsed for leaf nodes.

![Leaf nodes checkbox visibility collapsed in WinUI TreeGrid](Node-CheckBox_images/Node-CheckBox_img4.png)

## Handling Selection based on CheckBox State

SfTreeGrid has following modes for processing selection based on check box state.

1. Default – Selection and state of checkbox works independent of each other.
2. SelectOnCheck – Row can be selected or deselected based on state of checkbox.
3. SynchronizeSelection – Row can be selected or deselected based on state of checkbox and vice versa.

**Default mode**

If you don’t want to affect the selection while checking/unchecking the node CheckBox, you need to set [SfTreeGrid.CheckBoxSelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CheckBoxSelectionMode) as `Default`.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfTreeGrid Name="treeGrid"
                       CheckBoxSelectionMode="Default"
                       ItemsSource="{Binding PersonDetails}"
                       ShowCheckBox="True"/>

{% endhighlight %}
{% endtabs %}
{% tabs %}
{% highlight c# %}
treeGrid.CheckBoxSelectionMode = CheckBoxSelectionMode.Default;
{% endhighlight %}
{% endtabs %}

![CheckBoxSelectionMode as default demo for WinUI TreeGrid](Node-CheckBox_images/Node-CheckBox_img5.png)

**SelectOnCheck**

If you want to select/deselect the rows using node CheckBox only, you need to set [SfTreeGrid. CheckBoxSelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CheckBoxSelectionMode) as `SelectOnCheck`. 
Navigation, editing and programmatic selection are not supported in this mode.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfTreeGrid Name="treeGrid"
                       CheckBoxSelectionMode="SelectOnCheck"
                       ItemsSource="{Binding PersonDetails}"
                       ShowCheckBox="True"/>

{% endhighlight %}
{% highlight c# %}
treeGrid.CheckBoxSelectionMode = CheckBoxSelectionMode.SelectOnCheck;
{% endhighlight %}
{% endtabs %}

![CheckBoxSelectionMode as SelectOnCheck demo for WinUi TreeGrid](Node-CheckBox_images/Node-CheckBox_img6.png)

**SynchronizeSelection**

If you want to synchronize the selection with node CheckBox’s IsChecked state, you need to set [SfTreeGrid.CheckBoxSelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CheckBoxSelectionMode) as `SynchronizeSelection`. In this mode, you can select by checking checkbox and Selecting/Deselecting the row will check/uncheck the corresponding node checkbox.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfTreeGrid Name="treeGrid"
                       CheckBoxSelectionMode="SynchronizeSelection"
                       ItemsSource="{Binding PersonDetails}"
                       ShowCheckBox="True"/>

{% endhighlight %}
{% highlight c# %}
treeGrid.CheckBoxSelectionMode = CheckBoxSelectionMode.SynchronizeSelection;
{% endhighlight %}
{% endtabs %}

![CheckBoxSelectionMode as SynchronizeSelection demo for WinUI TreeGrid](Node-CheckBox_images/Node-CheckBox_img7.png)

N>
* Recursive checking is not supported when selection mode is single.
* CheckBox selection is not supported if selection mode in None.

## Events

### NodeCheckStateChanged

[NodeCheckStateChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_NodeCheckStateChanged) event triggered when user check or uncheck the node check box.

{% tabs %}
{% highlight c# %}
treeGrid.NodeCheckStateChanged += TreeGrid_NodeCheckStateChanged;

private void TreeGrid_NodeCheckStateChanged(object sender, NodeCheckStateChangedEventArgs e)
{
    var node = e.Node;
}
{% endhighlight %}
{% endtabs %}

## Programmatically Processing Node CheckBox

You can change the state of node checkbox programmatically by calling [SetCheckedState](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeNode.html#Syncfusion_UI_Xaml_TreeGrid_TreeNode_SetCheckedState_System_Nullable_System_Boolean__System_Boolean_System_Boolean_) method as below,

{% tabs %}
{% highlight c# %}
var treeNode = treeGrid.View.Nodes[0];
treeNode.SetCheckedState(true);
{% endhighlight %}
{% endtabs %}

If you want to restrict the `IsChecked` update of the parent and child nodes (when [SfTreeGrid.EnableRecursiveChecking](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_EnableRecursiveChecking) is `true`), you can pass default parameter values as `false` in [SetCheckedState](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeNode.html#Syncfusion_UI_Xaml_TreeGrid_TreeNode_SetCheckedState_System_Nullable_System_Boolean__System_Boolean_System_Boolean_) method.

{% tabs %}
{% highlight c# %}
var treeNode = treeGrid.View.Nodes[0];
treeNode.SetCheckedState(true, false, false);
{% endhighlight %}
{% endtabs %}

## Getting Checked nodes

You can get the checked nodes collection using [GetCheckedNodes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_GetCheckedNodes_System_Boolean_) method.

{% tabs %}
{% highlight c# %}
var nodes = treeGrid.GetCheckedNodes();
{% endhighlight %}
{% endtabs %}

If you want to get all the checked nodes even though they are not in view, you can pass parameter as ‘true’ in `GetCheckedNodes` method.

{% tabs %}
{% highlight c# %}
var nodes = treeGrid.GetCheckedNodes(true);
{% endhighlight %}
{% endtabs %}
