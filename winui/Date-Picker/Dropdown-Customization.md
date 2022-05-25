---
layout: post
title: Dropdown Customization in WinUI Date Picker control | Syncfusion
description: This section describes about how to customize the Date Picker (SfDatePicker) control dropdown into WinUI application and its basic features.
platform: WinUI
control: SfDatePicker
documentation: ug
---

# Dropdown Customization in WinUI Date Picker

This section describes about various dropdown customization options available in [Date Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html) control.

## Customize the dropdown button

You can customize the UI of dropdown button by using the [`DropDownButtonTemplate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_DropDownButtonTemplate) property. The `DataContext` of `DropDownButtonTemplate` property is `SfDatePicker`.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20" %}

<editors:SfDatePicker
    x:Name="sfDatePicker"
    PlaceholderText="pick a travel date">
    <editors:SfDatePicker.DropDownButtonTemplate>
       <DataTemplate>
            <Grid>
                <Grid.Resources>
                    <x:String x:Key="flight">M11.294993,2L15.378997,14 15.277995,14 13.188995,14 9.1429941,14 7.6250149,14 6.9399958,14 6.0199964,11.5 3.2099977,11.5 4.725997,16.014 3.2099977,20.5 6.0199964,20.5 6.8039956,18 7.6250201,18 8.8379947,18 15.288014,18 15.365021,18.000015 11.436984,30.000015 14.368989,30.000015 20.100004,18.000015 20.273989,18.000015 27.989002,18C29.084003,18 29.975004,17.121 29.975004,15.96 29.975004,14.879 29.084003,14 27.989002,14L22.309006,14 20.211995,14 20.096004,14 14.368996,2z M8.6259891,0L15.719998,0 21.367719,12 27.989002,12C30.205004,12,32.001007,13.773,32.001007,15.96L32.001007,16.04C32.001007,18.227,30.205004,20,27.989002,20L21.366735,20 15.719025,32.000015 8.6260106,32.000015 12.536309,20 8.2531061,20 7.5219953,22.5 0,22.5 2.5709982,16.013 0,9.5 7.4539952,9.5 8.3923279,12 12.537137,12z</x:String>
                </Grid.Resources>
                <Path
                    Width="20"
                    Height="20"
                    HorizontalAlignment="Center"
                    VerticalAlignment="Center"
                    Data="{StaticResource flight}"
                    Fill="{Binding Foreground, RelativeSource={RelativeSource Mode=TemplatedParent}}"
                    RenderTransformOrigin="0.5,0.5"
                    Stretch="Uniform" />
            </Grid>
        </DataTemplate>
    </editors:SfDatePicker.DropDownButtonTemplate>
</editors:SfDatePicker>

{% endhighlight %}
{% endtabs %}

![customize-drop-down-button-template-in-winui-date-picker](Images/drop-down-date-spinner/customize-drop-down-button-template-in-winui-date-picker.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/tree/main/Samples/SpinnerCustomUI)

## Hide dropdown button

You can hide the dropdown button in `Date Picker` by setting the [`ShowDropDownButton`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_ShowDropDownButton) property value as `false`. The default value of `ShowDropDownButton` property is `true`.

N> To open a dropdown date spinner, press the `Alt` + `Down Arrow` keys.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="3" %}

<editors:SfDatePicker  
                      x:Name="sfDatePicker"
                      ShowDropDownButton="False" />

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.ShowDropDownButton = false;

{% endhighlight %}
{% endtabs %}

![hide-drop-down-button-in-winui-date-picker](Images/drop-down-date-spinner/hide-drop-down-button-in-winui-date-picker.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/blob/main/Samples/ViewAndItemCustomization)

## Change dropdown alignment

You can change the alignment of the dropdown date spinner as full, center, left, right, top or bottom edge by using the [DropDownPlacement](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_DropDownPlacement) property. The default value of `DropDownPlacement` property is `Auto`.

N> If you change the dropdown alignment by using `DropDownPlacement` property and there is not sufficient space, then `Date Picker` smartly shifts the spinner alignment.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="3" %}

<editors:SfDatePicker 
                      x:Name="sfDatePicker"
                      DropDownPlacement="BottomEdgeAlignedLeft" />

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.DropDownPlacement = FlyoutPlacementMode.BottomEdgeAlignedLeft;

{% endhighlight %}
{% endtabs %}

![change-drop-down-placement-in-winui-date-picker](Images/drop-down-date-spinner/change-drop-down-placement-in-winui-date-picker.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/blob/main/Samples/ViewAndItemCustomization)

## Open dropdown programmatically

You can open or close the dropdown date spinner programmatically by setting [IsOpen](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_SelectedDate) property value as **true** or **false**. The default value of `IsOpen` property is **false**.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="3" %}

<editors:SfDatePicker 
                      x:Name="sfDatePicker"
                      IsOpen="True"/>

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.IsOpen = true;

{% endhighlight %}
{% endtabs %}

![programmatic-drop-down-open-in-winui-date-picker](Images/drop-down-date-spinner/programmatic-drop-down-open-in-winui-date-picker.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/tree/main/Samples/Localization)

## Change dropdown height

You can change the height of dropdown date spinner by using the [`DropDownHeight`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_DropDownHeight) property. Based on the value of `DropDownHeight`, `ItemWidth` and `ItemHeight` properties, particular date items will be visible. The default value of `DropDownHeight` property is `NaN`.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="3" %}

<editors:SfDatePicker 
                      x:Name="sfDatePicker"
                      DropDownHeight="200"/>

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.DropDownHeight = 200;

{% endhighlight %}
{% endtabs %}

![change-drop-down-height-in-winui-date-picker](Images/drop-down-date-spinner/change-drop-down-height-in-winui-date-picker.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/blob/main/Samples/ViewAndItemCustomization)

## Change the number of dates to be shown in the dropdown

You can change the number of dates to be shown in the dropdown date spinner by using the [VisibleItemsCount](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_VisibleItemsCount) property. The default value of `VisibleItemsCount` property is `-1`.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="3" %}

<editors:SfDatePicker 
                      x:Name="sfDatePicker"
                      VisibleItemsCount="5" />

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.VisibleItemsCount = 5;

{% endhighlight %}
{% endtabs %}

![show-number-of-dates-in-drop-down-in-winui-date-picker](Images/drop-down-date-spinner/show-number-of-dates-in-drop-down-in-winui-date-picker.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-datepicker-examples/blob/main/Samples/DateRestriction)
s
N> When `DropDownHeight` and `VisibleItemsCount` properties are set, `VisibleItemsCount` property have higher precedence.