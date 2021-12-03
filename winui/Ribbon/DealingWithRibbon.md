---
layout: post
title: Dealing with Ribbon in WinUI Ribbon control | Syncfusion
description:  Learn here all about dealing with Ribbon feature of Syncfusion WinUI Ribbon(sfRibbon) control and more.
platform: winui
control: Ribbon
documentation: ug
---

# Dealing with Ribbon in WinUI Ribbon

The below section describes more information about [Ribbon](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Ribbon.SfRibbon.html) and its features.

## Ribbon tab selection

The `SelectedTab` property returns the value of the currently selected [RibbonTab](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Ribbon.RibbonTab.html) and the `SelectedIndex` property returns the index of the `SelectedTab` in Ribbon.

{% tabs %}
{% highlight xaml %}

// Setting of Selected Index
<ribbon:SfRibbon SelectedIndex="2">
    <ribbon:SfRibbon.Tabs>
        <ribbon:RibbonTab Header="Home"/>
        <ribbon:RibbonTab Header="Insert" />
        <ribbon:RibbonTab Header="View" />
        <ribbon:RibbonTab Header="Layout" />
    </ribbon:SfRibbon.Tabs>
</ribbon:SfRibbon>

// Selected Tab Binding
<ribbon:SfRibbon x:Name="ribbon"
                         SelectedTab="{Binding ElementName=view}">
    <ribbon:SfRibbon.Tabs>
        <ribbon:RibbonTab Header="Home" />
            <ribbon:RibbonTab Header="Insert" />
            <ribbon:RibbonTab x:Name="view" Header="View" />
        <ribbon:RibbonTab Header="Layout" />
    </ribbon:SfRibbon.Tabs>
</ribbon:SfRibbon>
{% endhighlight %} 
{% endtabs %}

![RibbonTab selection with Selected tab and Selected index](Dealing-With-Ribbon-imgaes/ribbon-tab-selection-by-index-and-selected-tab-binding.png)

N> The selected index value should not exceed the child count of the `Tabs` collection in the [Ribbon](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Ribbon.SfRibbon.html).


## Grouping RibbonTabs using ContextualTabGroups

ContextualTabGroups are used to group the RibbonTabs for easy Navigation. This ContextualTabGroups appear when a user enable their context. 

## Creating ContextualTabGroups 

This ContextTabGroup can also be kept hidden and shown while required cases like in Word Document’s TABLETOOLS ContextTabGroups which gets displayed automatically, while selecting the table.  The following code snippet used to create a ContextualTabGroups

{% tabs %}
 
{% highlight XAML %}

<ribbon:SfRibbon.ContextualTabGroups>
                <ribbon:RibbonContextualTabGroup x:Name="TableTools"
                    Foreground="Orange" Background="Green"
                    Visibility="Visible"  >
                    <ribbon:RibbonTab Header="Options" x:Name="TableTab"/>
                </ribbon:RibbonContextualTabGroup>
</ribbon:SfRibbon.ContextualTabGroups>

{% endhighlight %}

{% endtabs %}

![WINUI Ribbon displays ContextTabGroup](Dealing-With-Ribbon-imgaes/WINUI-ribbon-context-tab-group.png)

## Add Items to RibbonGroup using RibbonItemHost

This `RibbonItemHost` used Add the multiple items under the RibbonContextTabGroup with the RibbonGroup.
{% tabs %}

{% highlight XAML %}

<Grid x:Name="rootGrid"
          BorderBrush="LightGray"
          BorderThickness="2">
        <Grid.DataContext>
            <local:ViewModel />
        </Grid.DataContext>
        <ribbon:SfRibbon x:Name="ribbon"
            LayoutModeOptions="Simplified"
            AllowMinimize="False"
            BackstageMenuButtonContent="File">
            <ribbon:SfRibbon.Tabs>
<ribbon:SfRibbon.ContextualTabGroups>
                <ribbon:RibbonContextualTabGroup x:Name="TableTools"
                    Foreground="Orange" Background="Green"
                    Visibility="Visible">
                    <ribbon:RibbonTab Header="Options" x:Name="TableTab">
                        <ribbon:RibbonGroup>
                            <ribbon:RibbonItemHost>
                                <ribbon:RibbonItemHost.ItemTemplate>
                                    <DataTemplate>
                                        <CheckBox x:Name="allowSort"
                                            Command="{Binding ButtonCommand}"
                                            CommandParameter="allowSort"
                                            Content="AllowSorting"
                                            IsChecked="{Binding AllowSorting, Mode=TwoWay}"/>
                                    </DataTemplate>
                                </ribbon:RibbonItemHost.ItemTemplate>
                            </ribbon:RibbonItemHost>
                            <ribbon:RibbonItemHost>
                                <ribbon:RibbonItemHost.ItemTemplate>
                                    <DataTemplate>
                                        <CheckBox x:Name="allowGroup"
                                            Content="AllowGrouping"
                                            IsChecked="{Binding AllowGrouping  ,Mode=TwoWay}"/>
                                    </DataTemplate>
                                </ribbon:RibbonItemHost.ItemTemplate>
                            </ribbon:RibbonItemHost>
                            <ribbon:RibbonItemHost>
                                <ribbon:RibbonItemHost.ItemTemplate>
                                    <DataTemplate>
                                        <CheckBox x:Name="allowFilter"
                                            Content="AllowFiltering"
                                            IsChecked="{Binding AllowFiltering ,Mode=TwoWay}"/>
                                    </DataTemplate>
                                </ribbon:RibbonItemHost.ItemTemplate>
                            </ribbon:RibbonItemHost>
                            <ribbon:RibbonItemHost>
                                <ribbon:RibbonItemHost.ItemTemplate>
                                    <DataTemplate>
                                        <CheckBox x:Name="showGroupDropArea"
                                            Content="ShowGroupDropArea"
                                            IsChecked="{Binding ShowGroupDropArea,Mode=TwoWay}"/>
                                    </DataTemplate>
                                </ribbon:RibbonItemHost.ItemTemplate>
                            </ribbon:RibbonItemHost>
                        </ribbon:RibbonGroup>
                        </ribbon:RibbonTab>
                </ribbon:RibbonContextualTabGroup>
</ribbon:SfRibbon.ContextualTabGroups>
</ribbon:SfRibbon.Tabs>
</ribbon:SfRibbon>
</Grid>

{% endhighlight %}

{% highlight C# %}

public class ViewModel : NotificationObject
    {
        public ICommand ButtonCommand { get; set; }

        public ViewModel()
        {
            this.ButtonCommand = new DelegateCommand(ExecuteButtonCommand, CanExecuteCommand);
        }

        private bool allowFiltering;

        public bool AllowFiltering
        {
            get { return allowFiltering; }
            set
            {
                allowFiltering = value;
                this.RaisePropertyChanged(nameof(AllowFiltering));
            }
        }
        private bool allowSorting = true;

        public bool AllowSorting
        {
            get
            {
                return allowSorting;
            }
            set
            {
                allowSorting = value;
                this.RaisePropertyChanged(nameof(AllowSorting));
            }
        }

        private bool showGroupDropArea;

        public bool ShowGroupDropArea
        {
            get { return showGroupDropArea; }
            set
            {
                showGroupDropArea = value;
                this.RaisePropertyChanged(nameof(ShowGroupDropArea));
            }
        }
    }
{% endhighlight %}

{% endtabs %}

![WINUI Ribbon add Item to RibbonGroup using RibbonItemHost](Dealing-With-Ribbon-imgaes/WINUI-ribbon-contextualtabgroup-ribbon-item-host.png)

## ContextaulTabGroups with Simplified Mode

When the simplified layout is enabled, the ContextTabGroup can be added and its items will be displayed in a single line as shown below. We could enable the simplified layout by setting `ActiveLayoutMode` and `LayoutModeOptions` as Simplified.

{% tabs %}

{% highlight XAML %}

<Grid x:Name="rootGrid"
          BorderBrush="LightGray"
          BorderThickness="2">
        <Grid.DataContext>
            <local:ViewModel />
        </Grid.DataContext>
        <ribbon:SfRibbon x:Name="ribbon"
            LayoutModeOptions="Simplified"
            AllowMinimize="False"
            ActiveLayoutMode="Simplified"
            BackstageMenuButtonContent="File">
            <ribbon:SfRibbon.Tabs>
<ribbon:SfRibbon.ContextualTabGroups>
                <ribbon:RibbonContextualTabGroup x:Name="TableTools"
                    Foreground="Orange" Background="Green"
                    Visibility="Visible">
                    <ribbon:RibbonTab Header="Options" x:Name="TableTab">
                        <ribbon:RibbonGroup>
                            <ribbon:RibbonItemHost>
                                <ribbon:RibbonItemHost.ItemTemplate>
                                    <DataTemplate>
                                        <CheckBox x:Name="allowSort"
                                            Command="{Binding ButtonCommand}"
                                            CommandParameter="allowSort"
                                            Content="AllowSorting"
                                            IsChecked="{Binding AllowSorting, Mode=TwoWay}"/>
                                    </DataTemplate>
                                </ribbon:RibbonItemHost.ItemTemplate>
                            </ribbon:RibbonItemHost>
                            <ribbon:RibbonItemHost>
                                <ribbon:RibbonItemHost.ItemTemplate>
                                    <DataTemplate>
                                        <CheckBox x:Name="allowGroup"
                                            Content="AllowGrouping"
                                            IsChecked="{Binding AllowGrouping  ,Mode=TwoWay}"/>
                                    </DataTemplate>
                                </ribbon:RibbonItemHost.ItemTemplate>
                            </ribbon:RibbonItemHost>
                            <ribbon:RibbonItemHost>
                                <ribbon:RibbonItemHost.ItemTemplate>
                                    <DataTemplate>
                                        <CheckBox x:Name="allowFilter"
                                            Content="AllowFiltering"
                                            IsChecked="{Binding AllowFiltering ,Mode=TwoWay}"/>
                                    </DataTemplate>
                                </ribbon:RibbonItemHost.ItemTemplate>
                            </ribbon:RibbonItemHost>
                            <ribbon:RibbonItemHost>
                                <ribbon:RibbonItemHost.ItemTemplate>
                                    <DataTemplate>
                                        <CheckBox x:Name="showGroupDropArea"
                                            Content="ShowGroupDropArea"
                                            IsChecked="{Binding ShowGroupDropArea,Mode=TwoWay}"/>
                                    </DataTemplate>
                                </ribbon:RibbonItemHost.ItemTemplate>
                            </ribbon:RibbonItemHost>
                        </ribbon:RibbonGroup>
                        </ribbon:RibbonTab>
                </ribbon:RibbonContextualTabGroup>
</ribbon:SfRibbon.ContextualTabGroups>
</ribbon:SfRibbon.Tabs>
</ribbon:SfRibbon>
</Grid>

{% endhighlight %}
{% highlight C# %}
public MainWindow()
        {
            ribbon.LayoutModeOptions = LayoutModeOptions.Simplified;
            ribbon.ActiveLayoutMode = LayoutMode.Simplified;
        }
{% endhighlight %}
{% endtabs %}

![WINUI Ribbon displays ContextTabGroup with Simplified Layout](Dealing-With-Ribbon-imgaes/WINUI-ribbon-contextualtabgroup-simplified.png)

## Multiple RibbonContextualTabGroup

To differentiate one RibbonContextTabGroup with one another. We could use the `Background` or `Forground` Properties in RibbonContextualTabGroup.
 
{% tabs %}

{% highlight XAML %}

<ribbon:SfRibbon.ContextualTabGroups>
            <ribbon:RibbonContextualTabGroup x:Name="TableTools" 
                    Visibility="Visible" 
                    Foreground="Yellow" Background="Green"
                    SelectFirstTabOnVisible="True" >
                    <ribbon:RibbonTab x:Name="TableTab" Header="Options"/>
                    <ribbon:RibbonTab Header="Layout"/>
            </ribbon:RibbonContextualTabGroup>
            <ribbon:RibbonContextualTabGroup x:Name="PictureTool" 
                    Foreground="LawnGreen" Background="DarkBlue"
                    Visibility="Visible" 
                    SelectFirstTabOnVisible="True">
                    <ribbon:RibbonTab Header="ItemTemplate" />
            </ribbon:RibbonContextualTabGroup>
</ribbon:SfRibbon.ContextualTabGroups>


{% endhighlight %}

{% endtabs %}

![WINUI Ribbon displays Multiple ContextTabGroups](Dealing-With-Ribbon-imgaes/WINUI-ribbon-multiple-contextualtabgroup.png)

## RibbonContextualTabGroup with SelectFirstTabOnVisible

When we set the `SelectFirstTabOnVisible` as true, The correponding tab group will be selected when that group get visible.

{% tabs %}

{% highlight XAML %}
<ribbon:SfRibbon.ContextualTabGroups>
            <ribbon:RibbonContextualTabGroup x:Name="TableTools" 
                    Visibility="Visible" 
                    Foreground="Yellow" Background="Green"
                    SelectFirstTabOnVisible="false" >
                    <ribbon:RibbonTab x:Name="TableTab" Header="Options"/>
                    <ribbon:RibbonTab Header="Layout"/>
            </ribbon:RibbonContextualTabGroup>
            <ribbon:RibbonContextualTabGroup x:Name="PictureTool" 
                    Foreground="Red" Background="Pink"
                    Visibility="Visible" 
                    SelectFirstTabOnVisible="True">
                    <ribbon:RibbonTab Header="ItemTemplate" />
            </ribbon:RibbonContextualTabGroup>
</ribbon:SfRibbon.ContextualTabGroups>
{% endhighlight %}
 
{% endtabs %}

![WINUI Ribbon displays Multiple RibbonContextualTabGroup](Dealing-With-Ribbon-imgaes/WINUI-ribbon-contextualtabgroup-select-first-tab-on-visible.png)

## Changing the visibility at run time

RibbonContextualTabGroup visibility can also be changed at the runtime. To change the visibility, use `Visibility` property in RibbonContextualTabGroup.
 
{% tabs %}

{% highlight XAML %}

<ribbon:SfRibbon.ContextualTabGroups>
            <ribbon:RibbonContextualTabGroup x:Name="TableTools" 
                    Visibility="Visible" 
                    Foreground="Yellow" Background="Green">
                    <ribbon:RibbonTab x:Name="TableTab" Header="Options"/>
                    <ribbon:RibbonTab Header="Layout"/>
            </ribbon:RibbonContextualTabGroup>
</ribbon:SfRibbon.ContextualTabGroups>

{% endhighlight %}
 
{% endtabs %}
 
{% tabs %}

{% highlight C# %}

private void Button_Click(object sender, RoutedEventArgs e)
{
    TableTools.Visibility = Visibility.Collapsed;
}

{% endhighlight %}
 
{% endtabs %}

![RibbonContextualTabGroup visibility as visible](Dealing-With-Ribbon-imgaes/WINUI-ribbon-contextualtabgroup-visibility-true.png)


After Button clicked, the RibbonContextualTabGroup visibility changes as follows

![Changing RibbonContextualTabGroup visibility at Runtime in WINUI Ribbon](Dealing-With-Ribbon-imgaes/WINUI-ribbon-contextualtabgroup-visibility-false.png)

### Detecting selection changes in the Ribbon tab

The [SelectedTabChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Ribbon.SfRibbon.html#Syncfusion_UI_Xaml_Ribbon_SfRibbon_SelectedTabChanged) event triggers when a user attempts to switch the [RibbonTab](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Ribbon.RibbonTab.html) in a Ribbon.

* The sender argument contains the [SfRibbon](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Ribbon.SfRibbon.html). This argument is of type object but can be casted to the SfRibbon type.
* The second argument is a `SelectionChangedEventArgs` that receives the old and newly selected ribbon tabs in an argument.

{% tabs %}
{% highlight xaml %}

<ribbon:SfRibbon x:Name="ribbon"
                 SelectedTabChanged="ribbon_SelectedTabChanged">
    <ribbon:SfRibbon.Tabs>
        <ribbon:RibbonTab Header="Home" />
        <ribbon:RibbonTab Header="Insert" />
        <ribbon:RibbonTab Header="View" />
        <ribbon:RibbonTab Header="Layout" />
    </ribbon:SfRibbon.Tabs>
</ribbon:SfRibbon>

{% endhighlight %} 
{% highlight c# %}

private void ribbon_SelectedTabChanged(object sender, SelectionChangedEventArgs e)
{
    // Write your code here
}

{% endhighlight %} 
{% endtabs %}





