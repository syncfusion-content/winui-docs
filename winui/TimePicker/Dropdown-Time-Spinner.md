---
layout: post
title: DropDown time spinner in SfTimePicker control | Syncfusion
description: This page explain about how to Customization the Drop Down of the WinUI SfTimePicker control and items features.
platform: winui
control:  SfTimePicker
documentation: ug
---

# Dropdown time spinner in WPF TimePicker (SfTimePicker)

This section describes how to select a time from drop down time spinner and its customization options in [SfTimePicker]() control.

## Change time format for Spinner

You can allow the user to select the pair of hour, minutes, seconds and meridiem spinner or any single spinner cell from the drop down time spinner by using the [DropdownFormatString]() property. The default value of `DropdownFormatString` property is `hh:mm tt`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfTimePicker x:Name="sfTimePicker" 
                         DropdownFormatString="hh tt"/>

{% endhighlight  %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.DropdownFormatString = "hh tt";

{% endhighlight  %}
{% endtabs %}

![SfTimePicker contains only drop down hour and meridiem spinner](Features_images/DropdownFormatString.png)

Here, you can only able to select the hour and meridiem value from the drop down spinner.

N> Download demo application from [GitHub]()

## Show or hide Dropdown button

If you want to restrict the user to select a time from a drop down time spinner, hide the drop down button by using the [ShowDropDownButton]() property value as `false`. The default value of `ShowDropDownButton` property is `true`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfTimePicker ShowDropDownButton="False" 
	                     x:Name="sfTimePicker"/>

{% endhighlight %}
{% highlight c# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.ShowDropDownButton = false;

{% endhighlight %}
{% endtabs %}

![SfTimePicker hides the drop down button](Customizing-DropDown_images/ShowDropDownButton.png)

N> Download demo application from [GitHub]()

## Hide Dropdown submit button(Select time directly from time spinner)

If you want to hide the submit button and select the time directly from the drop down time spinner without clicking the `Ok` button, use the [ShowSubmitButtons]() property value as `false`. The default value of `ShowSubmitButtons` property is `true`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfTimePicker ShowSubmitButtons="False" 
	                     x:Name="sfTimePicker"/>

{% endhighlight %}
{% highlight c# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.ShowSubmitButtons = false;

{% endhighlight %}
{% endtabs %}

![SfTimePicker hides the drop down time spinner submit and cancel buttons](Customizing-DropDown_images/ShowSubmitButtons.png)

N> Download demo application from [GitHub]()

## Change Dropdown alignment

You can change alignment of the drop down time spinner as full, center, left, right, top or bottom with edge of the `TimePicker` by using the [DropDownPlacement]() property. The default value of `DropDownPlacement` property is `Auto`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfTimePicker DropDownPlacement="BottomEdgeAlignedRight" 
	                     x:Name="sfTimePicker"/>

{% endhighlight %}
{% highlight c# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.DropDownPlacement = FlyoutPlacementMode.BottomEdgeAlignedRight;

{% endhighlight %}
{% endtabs %}

![Alignment of drop down time spinner is changed to BottomEdgeAlignedRight](Customizing-DropDown_images/DropDownPlacement.png)

N> Download demo application from [GitHub]()

## Setting the Dropdown header text

You can add the drop down time spinner's header text by using the [DropDownHeader]() property.
If you want to show the drop down header, use the [ShowDropDownHeader]() property value as `true`. Otherwise, drop down header will not be shown. The default value of `DropDownHeader` property is `null` and `ShowDropDownHeader` property is `false`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfTimePicker DropDownHeader="Select Time" 
						 ShowDropDownHeader="True" 
	                     x:Name="sfTimePicker"/>

{% endhighlight %}
{% highlight c# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.DropDownHeader = "Select Time";
sfTimePicker.ShowDropDownHeader = true;

{% endhighlight %}
{% endtabs %}

![SfTimePicker displays the drop down time spinner header](Customizing-DropDown_images/DropDownHeader.png)

N> Download demo application from [GitHub]()

## Custom UI of Dropdown header

You can customize the header of drop down time spinner by using the [DropDownHeaderTemplate]() property. The `DataContext` of `DropDownHeaderTemplate` property is `SfTimePicker.DropDownHeader`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfTimePicker DropDownHeader="Select Time" 
						 ShowDropDownHeader="True" 
	                     x:Name="sfTimePicker">
    <syncfusion:SfTimePicker.DropDownHeaderTemplate>
        <DataTemplate>
            <Grid>
                <TextBlock 
                    Foreground="Red" 
                    Text="{Binding}"/>
            </Grid>
        </DataTemplate>
    </syncfusion:SfTimePicker.DropDownHeaderTemplate>
</syncfusion:SfTimePicker>

{% endhighlight %}
{% endtabs %}

![SfTimePicker with customized drop down time spinner header](Customizing-DropDown_images/DropDownHeaderTemplate.png)

N> Download demo application from [GitHub]()

## Hide the Dropdown column headers

If you want to hide the drop down hour, minutes, seconds and meridiem spinner's column headers, use the [ShowColumnHeaders]() property value as `false`. The default value of `ShowColumnHeaders` property is `true`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfTimePicker ShowColumnHeaders="False" 
	                     x:Name="sfTimePicker"/>

{% endhighlight %}
{% highlight c# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.ShowColumnHeaders = false;

{% endhighlight %}
{% endtabs %}

![SfTimePicker hides the drop down time spinner column headers](Customizing-DropDown_images/ShowColumnHeaders.png)

N> Download demo application from [GitHub]()

## Change the number of times to be shown in the Dropdown

You can change the number of times to be shown in the drop down time spinner by using the [VisibleItemsCount]() property. The default value of `VisibleItemsCount` property is `-1`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfTimePicker VisibleItemsCount="BottomEdgeAlignedRight" 
	                     x:Name="sfTimePicker"/>

{% endhighlight %}
{% highlight c# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.VisibleItemsCount = FlyoutPlacementMode.BottomEdgeAlignedRight;

{% endhighlight %}
{% endtabs %}

![Alignment of drop down time spinner is changed to](Customizing-DropDown_images/VisibleItemsCount.png)

N> Download demo application from [GitHub]()

## Change Dropdown height

You can change the height of drop down time spinner by using the [DropDownHeight]() property. The default value of `DropDownHeight` property is `NaN`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfTimePicker DropDownHeight="200"
						 x:Name="sfTimePicker"/>

{% endhighlight %}
{% highlight c# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.DropDownHeight = 200;

{% endhighlight %}
{% endtabs %}

![SfTimePicker with DropDownHeight](Customizing-DropDown_images/DropDownHeight.png)

N> Download demo application from [GitHub]()

## Change the size of Dropdown cells

You can change the cell size in the drop down time spinner by setting the values to [ItemWidth]() and [ItemHeight]() properties. The default value of the `ItemWidth` and `ItemHeight` properties is `80` and `40`. 

You can also restrict the width of drop down time spinner cells with particular pixels by using the [MinItemWidth]() and [MaxItemWidth]() properties. The default value of `MinItemWidth` property is `0` and `MaxItemWidth` property is `Infinity`.

N> `ItemWidth` values must be within the `MinItemWidth` and `MaxItemWidth`values. Otherwise, `ItemWidth` will take the closest value from `MinItemWidth` or `MaxItemWidth` value.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfTimePicker MinItemWidth="70" 
						 MaxItemWidth="120" 
						 ItemWidth="100"
						 ItemHeight="50" 
	                     x:Name="sfTimePicker"/>

{% endhighlight %}
{% highlight c# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.MinItemWidth = 70;
sfTimePicker.MaxItemWidth = 120;
sfTimePicker.ItemWidth = 100;
sfTimePicker.ItemHeight = 50;

{% endhighlight %}
{% endtabs %}

![Drop down time spinner cell size changed](Customizing-DropDown_images/ItemWidth.png)

N> Download demo application from [GitHub]()

## Change flow direction

You can change the flow direction of the `TimePicker` layout from right to left by setting the `FlowDirection` property value as `RightToLeft`. The default value of `FlowDirection` property is `LeftToRight`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfTimePicker FlowDirection="RightToLeft" 
	                     x:Name="sfTimePicker"/>

{% endhighlight %}
{% highlight c# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.FlowDirection = FlowDirection.RightToLeft;

{% endhighlight %}
{% endtabs %}

![SfTimePicker flow direction changed to right to left](Customizing-DropDown_images/FlowDirection.png)

N> Download demo application from [GitHub]()