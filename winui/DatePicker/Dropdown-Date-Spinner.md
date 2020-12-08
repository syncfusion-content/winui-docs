---
layout: post
title: DropDown date selector in SfDatePicker control | Syncfusion
description: This page explain about how to Customization the Drop Down of the WinUI SfDatePicker control and items features.
platform: winui
control:  SfDatePicker
documentation: ug
---

# Dropdown date selector in WPF DatePicker (SfDatePicker)

This section describes how to select a date from drop down date selector and its customization options in [SfDatePicker]() control.

## Specifying date format for the DateSelector

You can allow the user to select the pair of date, month and year selector or any single selector cell from the drop down date selector by using the [DropdownFormatString]() property. The default value of `DropdownFormatString` property is `d`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker x:Name="sfDatePicker" 
                         DropdownFormatString="dd/MM"/>

{% endhighlight  %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.DropdownFormatString = "dd/MM";

{% endhighlight  %}
{% endtabs %}

![SfDatePicker contains only date and month selector](Features_images/DropdownFormatString.png)

Here, you can only able to select the date and month value from the drop down selector.

N> Download demo application from [GitHub]()

## Show or hide Dropdown button

If you want to restrict the user to select a date from a drop down date selector, hide the drop down button by using the [ShowDropDownButton]() property value as `false`. The default value of `ShowDropDownButton` property is `true`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfDatePicker ShowDropDownButton="False" 
	                     x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.ShowDropDownButton = false;

{% endhighlight %}
{% endtabs %}

![SfDatePicker hides the drop down button](Customizing-DropDown_images/ShowDropDownButton.png)

N> Download demo application from [GitHub]()

## Hide Dropdown submit button(Select date directly from date selector)

If you want to hide the submit button and select the date directly from the drop down date selector without clicking the `Ok` button, use the [ShowSubmitButtons]() property value as `false`. The default value of `ShowSubmitButtons` property is `true`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfDatePicker ShowSubmitButtons="False" 
	                     x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.ShowSubmitButtons = false;

{% endhighlight %}
{% endtabs %}

![SfDatePicker hides the drop down date selector submit and cancel buttons](Customizing-DropDown_images/ShowSubmitButtons.png)

N> Download demo application from [GitHub]()

## Change Dropdown alignment

You can change alignment of the drop down date selector as full, center, left, right, top or bottom with edge of the `DatePicker` by using the [DropDownPlacement]() property. The default value of `DropDownPlacement` property is `Auto`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfDatePicker DropDownPlacement="BottomEdgeAlignedRight" 
	                     x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.DropDownPlacement = FlyoutPlacementMode.BottomEdgeAlignedRight;

{% endhighlight %}
{% endtabs %}

![Alignment of drop down date selector is changed to BottomEdgeAlignedRight](Customizing-DropDown_images/DropDownPlacement.png)

N> Download demo application from [GitHub]()

## Setting the Dropdown header text

You can add the drop down date selector's header text by using the [DropDownHeader]() property.
If you want to show the drop down header, use the [ShowDropDownHeader]() property value as `true`. Otherwise, drop down header will not be shown. The default value of `DropDownHeader` property is `null` and `ShowDropDownHeader` property is `false`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfDatePicker DropDownHeader="Select Date" 
						 ShowDropDownHeader="True" 
	                     x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.DropDownHeader = "Select Date";
sfDatePicker.ShowDropDownHeader = true;

{% endhighlight %}
{% endtabs %}

![SfDatePicker displays the drop down date selector header](Customizing-DropDown_images/DropDownHeader.png)

N> Download demo application from [GitHub]()

## Custom UI of Dropdown header

You can customize the header of drop down date selector by using the [DropDownHeaderTemplate]() property. The `DataContext` of `DropDownHeaderTemplate` property is `SfDatePicker.DropDownHeader`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfDatePicker DropDownHeader="Select Date" 
						 ShowDropDownHeader="True" 
	                     x:Name="sfDatePicker">
    <syncfusion:SfDatePicker.DropDownHeaderTemplate>
        <DataTemplate>
            <Grid>
                <TextBlock 
                    Foreground="Red" 
                    Text="{Binding}"/>
            </Grid>
        </DataTemplate>
    </syncfusion:SfDatePicker.DropDownHeaderTemplate>
</syncfusion:SfDatePicker>

{% endhighlight %}
{% endtabs %}

![SfDatePicker with customized drop down date selector header](Customizing-DropDown_images/DropDownHeaderTemplate.png)

N> Download demo application from [GitHub]()

## Hide the Dropdown column headers

If you want to hide the drop down day, month and year selector's column headers, use the [ShowColumnHeaders]() property value as `false`. The default value of `ShowColumnHeaders` property is `true`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfDatePicker ShowColumnHeaders="False" 
	                     x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.ShowColumnHeaders = false;

{% endhighlight %}
{% endtabs %}

![SfDatePicker hides the drop down date selector column headers](Customizing-DropDown_images/ShowColumnHeaders.png)

N> Download demo application from [GitHub]()

## Change the number of dates to be shown in the Dropdown

You can change the number of dates to be shown in the drop down date selector by using the [VisibleItemsCount]() property. The default value of `VisibleItemsCount` property is `-1`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfDatePicker VisibleItemsCount="BottomEdgeAlignedRight" 
	                     x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.VisibleItemsCount = FlyoutPlacementMode.BottomEdgeAlignedRight;

{% endhighlight %}
{% endtabs %}

![Alignment of drop down date selector is changed to](Customizing-DropDown_images/VisibleItemsCount.png)

N> Download demo application from [GitHub]()

## Change Dropdown height

You can change the height of drop down date selector by using the [DropDownHeight]() property. The default value of `DropDownHeight` property is `NaN`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfDatePicker DropDownHeight="200"
						 x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.DropDownHeight = 200;

{% endhighlight %}
{% endtabs %}

![SfDatePicker with DropDownHeight](Customizing-DropDown_images/DropDownHeight.png)

N> Download demo application from [GitHub]()

## Change the size of Dropdown cells

You can change the cell size in the drop down date selector by setting the values to [ItemWidth]() and [ItemHeight]() properties. The default value of the `ItemWidth` and `ItemHeight` properties is `80` and `40`. 

You can also restrict the width of drop down date selector cells with particular pixels by using the [MinItemWidth]() and [MaxItemWidth]() properties. The default value of `MinItemWidth` property is `0` and `MaxItemWidth` property is `Infinity`.

N> `ItemWidth` values must be within the `MinItemWidth` and `MaxItemWidth`values. Otherwise, `ItemWidth` will take the closest value from `MinItemWidth` or `MaxItemWidth` value.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfDatePicker MinItemWidth="70" 
						 MaxItemWidth="120" 
						 ItemWidth="100"
						 ItemHeight="50" 
	                     x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.MinItemWidth = 70;
sfDatePicker.MaxItemWidth = 120;
sfDatePicker.ItemWidth = 100;
sfDatePicker.ItemHeight = 50;

{% endhighlight %}
{% endtabs %}

![Drop down date selector cell size changed](Customizing-DropDown_images/ItemWidth.png)

N> Download demo application from [GitHub]()

## Change flow direction

You can change the flow direction of the `DatePicker` layout from right to left by setting the `FlowDirection` property value as `RightToLeft`. The default value of `FlowDirection` property is `LeftToRight`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfDatePicker FlowDirection="RightToLeft" 
	                     x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.FlowDirection = FlowDirection.RightToLeft;

{% endhighlight %}
{% endtabs %}

![SfDatePicker flow direction changed to right to left](Customizing-DropDown_images/FlowDirection.png)

N> Download demo application from [GitHub]()