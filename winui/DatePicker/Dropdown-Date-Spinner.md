---
layout: post
title: DropDown date spinner in DatePicker control | Syncfusion
description: This page explain about how to Customization the Drop Down of the WinUI SfDatePicker control and items features.
platform: winui
control:  SfDatePicker
documentation: ug
---

# Dropdown date spinner in WPF DatePicker (SfDatePicker)

This section describes how to select a date from drop down date spinner and its customization options in [SfDatePicker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html) control.

## Change dropdown alignment

You can change the alignment of the drop down date spinner as full, center, left, right, top or bottom with edge of the `DatePicker` by using the [DropDownPlacement](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_DropDownPlacement) property. The default value of `DropDownPlacement` property is `Auto`.

{% tabs %}
{% highlight XAML %}

<editors:SfDatePicker DropDownPlacement="BottomEdgeAlignedLeft" 
                      x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.DropDownPlacement = FlyoutPlacementMode.BottomEdgeAlignedLeft;

{% endhighlight %}
{% endtabs %}

![Alignment of drop down date spinner is changed to BottomEdgeAlignedLeft](Dropdown-Date-Spinner_images/DropDownPlacement.png)

N> Download demo application from [GitHub]()

## Customize the date field in dropdown spinner using event

You can change the date format header text, size of date field cells, customize the UI of date field cells and enables the date looping, etc., by using the [DateFieldPrepared](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_DateFieldPrepared) event.

Here, date format, header and cell size of the dropdown date field is customized by using `DateFieldPrepared` event.

N> This will effective only for the date field cells.

{% tabs %}
{% highlight XAML %}

<editors:SfDatePicker DateFieldPrepared="SfDatePicker_DateFieldPrepared"
                      x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.DateFieldPrepared = SfDatePicker_DateFieldPrepared;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows,

{% tabs %}
{% highlight C# %}

private void SfDatePicker_DateFieldPrepared(object sender, DateTimeFieldPreparedEventArgs e)
{
    if (e.Column != null)
    {
        e.Column.Format = "ddd dd";
        e.Column.Header = "Choose Date";
        e.Column.ShowHeader = true;
        e.Column.ItemHeight = 60;
        e.Column.ItemWidth = 100;
        e.Column.ShouldLoop = true;
    }
}

{% endhighlight %}
{% endtabs %}

![Dropdown spinner date field elements customized using DateFieldPrepared event](Dropdown-Date-Spinner_images/DateFieldPrepared.png)

N> Download demo application from [GitHub]()

## Custom UI for specific cell in dropdown spinner

You can change the UI of specific date, month or year cells in dropdown spinner by using the `ItemTemplateSelector` property. The `DataContext` of `ItemTemplateSelector` is `SfDatePicker`. 

{% tabs %}
{% highlight C# %}

public class DateItemTemplateSelector : DataTemplateSelector
{
    public DataTemplate DefaultTemplate { get; set; }
    public DataTemplate BirthdayTemplate { get; set; }
    public DataTemplate GiftTemplate { get; set; }
    public DataTemplate AwardTemplate { get; set; }

    protected override DataTemplate SelectTemplateCore(object item, DependencyObject container)
    {
        DateTimeFieldItemInfo dateTimeField = item as DateTimeFieldItemInfo;
        if (dateTimeField.Field == DateTimeField.Day)
        {
            switch (dateTimeField.DateTime.Value.Day)
            {
                case 2:
                    return BirthdayTemplate as DataTemplate;
                case 7:
                    return GiftTemplate as DataTemplate;
                case 12:
                    return AwardTemplate as DataTemplate;
                case 17:
                    return BirthdayTemplate as DataTemplate;
                case 20:
                    return GiftTemplate as DataTemplate;
                case 26:
                    return AwardTemplate as DataTemplate;
            }
        }
        return base.SelectTemplateCore(item, container);
    }
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight XAML %}

<Page.Resources>
        <x:String x:Key="birthday">M24.188005,24.530994C24.999008,24.530994 25.657011,25.188997 25.657011,26 25.657011,26.811003 24.999008,27.469006 24.188005,27.469006 23.377003,27.469006 22.719,26.811003 22.719,26 22.719,25.188997 23.377003,24.530994 24.188005,24.530994z M16.000006,24.530994C16.811008,24.530994 17.469011,25.188997 17.469011,26 17.469011,26.811003 16.811008,27.469006 16.000006,27.469006 15.189002,27.469006 14.530999,26.811003 14.530999,26 14.530999,25.188997 15.189002,24.530994 16.000006,24.530994z M7.813005,24.405994C8.6240082,24.405994 9.282011,25.063997 9.282011,25.875 9.282011,26.686003 8.6240082,27.344006 7.813005,27.344006 7.0020018,27.344006 6.3439994,26.686003 6.3439994,25.875 6.3439994,25.063997 7.0020018,24.405994 7.813005,24.405994z M3,22.5C2.4490051,22.5,2,22.949005,2,23.5L2,29.5 30,29.5 30,23.5C30,22.949005,29.550995,22.5,29,22.5z M5,14.5C4.4489999,14.5,4,14.949,4,15.5L4,20.5 28,20.5 28,15.5C28,14.949,27.551001,14.5,27,14.5L16,14.5z M16,8.5C16.552,8.5,17,8.948,17,9.5L17,12.5 27,12.5C28.653999,12.5,30,13.846,30,15.5L30,20.672067 30.030354,20.68236C31.178461,21.103616,32,22.207819,32,23.5L32,30.5C32,31.052002,31.552002,31.5,31,31.5L1,31.5C0.44799805,31.5,0,31.052002,0,30.5L0,23.5C0,22.207819,0.82153827,21.103616,1.969646,20.68236L2,20.672067 2,15.5C2,13.846,3.346,12.5,5,12.5L15,12.5 15,9.5C15,8.948,15.448,8.5,16,8.5z M16.019098,0C16.450115,1.7290001 18.144182,3.5890007 18.144182,4.7290001 18.219185,6.1879997 17.684164,7 16.019098,7 14.354033,7 13.856012,6.0419998 13.856012,4.7290001 13.856012,3.323 14.56604,1.3330002 16.019098,0z</x:String>
        <x:String x:Key="gift">M14.072999,21.71989L14.173005,21.71989 23.954012,21.71989 23.954012,30.402982C23.954012,31.300994,23.255007,31.999997,22.356997,31.999997L14.072999,31.999997z M1.2980041,21.71989L11.178987,21.71989 11.178987,31.999997 2.8949892,31.999997C1.9960022,31.999997,1.2980041,31.300994,1.2980041,30.402982z M19.661989,3.2556945C19.06299,3.2556945,14.072999,7.3477336,12.975007,8.545744L12.975007,8.8447515C13.674012,8.6447526 15.670015,7.1477343 17.267,6.1497227 19.162996,5.0517112 19.962008,3.7546926 19.661989,3.2556945z M5.5889899,3.2556945C5.3899848,3.7546926 6.1879889,5.0517112 7.984986,6.2497221 9.4819957,7.2477342 11.578004,8.6447526 12.277009,8.9447509L12.277009,8.6447526C11.178987,7.3477336,6.287995,3.2556945,5.5889899,3.2556945z M17.864281,0.00017286225C18.476668,-0.0068490629 19.175909,0.19928326 19.962008,0.76066515 22.756014,2.6566814 22.656008,4.2536984 22.656008,5.2517105 22.157015,7.447733 19.463015,8.4457446 16.868014,8.9447509L23.355013,8.9447509C24.252993,8.9447509,24.951998,9.6427566,24.951998,10.541768L24.951998,13.235797C24.951998,13.834803,24.553011,14.433808,24.053988,14.633815L24.053988,19.723867 14.173005,19.723867 14.173005,9.3437568 13.574006,9.3437568 13.075013,9.3437568 12.675996,9.3437568 12.277009,9.3437568 11.578004,9.3437568 11.477998,9.3437568 11.178987,9.3437568 11.178987,19.723867 1.2980041,19.723867 1.2980041,14.732815C0.59899889,14.533815,-2.3291432E-07,13.934802,0,13.136797L0,10.441769C-2.3291432E-07,9.5437566,0.69900499,8.8447515,1.5969848,8.8447515L8.4840099,8.8447515C5.8890082,8.545744 3.0939943,7.447733 2.6950075,5.2517105 2.6950075,4.353706 2.5950014,2.7566885 5.3899848,0.76066515 6.0889899,0.261659 6.7869879,0.061659901 7.385987,0.061660053 8.9830028,0.061659901 10.080995,1.4586705 10.480012,1.8586761 10.878999,2.2576827 12.076997,4.452706 12.675996,6.6487285 13.274995,4.452706 14.471986,2.2576827 14.871003,1.8586761 15.301535,1.4281411 16.29929,0.018116923 17.864281,0.00017286225z</x:String>
        <x:String x:Key="award">M6.4050484,19.617198L3.7509956,25.34103 6.5209923,24.451031 7.7069907,27.094029 10.305956,21.486943 10.209199,21.463142C8.8243089,21.103976,7.5456314,20.475896,6.431808,19.637838z M20.198464,18.975471L19.810075,19.313839C18.872342,20.092266,17.802781,20.71557,16.640677,21.144267L16.418594,21.22308 18.634039,27.072047 19.967047,24.487023 22.674016,25.519068z M12.916001,5.5320349C9.9759998,5.5320349 7.5829983,7.9410334 7.5829983,10.903033 7.5829983,13.865032 9.9759998,16.274031 12.916001,16.274031 15.857003,16.274031 18.250004,13.865032 18.250004,10.903033 18.250004,7.9410334 15.857003,5.5320349 12.916001,5.5320349z M12.916001,3.5320349C16.960003,3.5320349 20.250005,6.8390341 20.250005,10.903033 20.250005,14.968032 16.960003,18.274031 12.916001,18.274031 8.8729992,18.274031 5.5829973,14.968032 5.5829973,10.903033 5.5829973,6.8390341 8.8729992,3.5320349 12.916001,3.5320349z M12.91602,2.0000057C8.0390205,2.0000057 4.0710211,5.9940157 4.0710211,10.903028 4.0710211,15.81304 8.0390205,19.80705 12.91602,19.80705 17.79302,19.80705 21.761019,15.81304 21.761019,10.903028 21.761019,5.9940157 17.79302,2.0000057 12.91602,2.0000057z M12.91602,0C18.89502,0 23.761019,4.8920126 23.761019,10.903028 23.761019,13.251471 23.018526,15.429016 21.757237,17.210832L21.674238,17.325164 21.711064,17.311053 26.135013,28.99606 20.926031,27.007045 18.356024,31.999053 14.455157,21.696701 14.295179,21.719278C13.843446,21.777196 13.383129,21.807055 12.91602,21.807055 12.822598,21.807055 12.729448,21.805861 12.636584,21.803486L12.375046,21.793458 7.6759906,31.926026 5.4279938,26.921029 0,28.665028 4.8565531,18.189458 4.5508928,17.834802C3.0024042,15.949165 2.0710211,13.533284 2.0710211,10.903028 2.0710211,4.8920126 6.9370208,0 12.91602,0z</x:String>
        <DataTemplate x:Key="defaultTemplate">
            <TextBlock Text="{Binding DisplayText}" />
        </DataTemplate>
        <DataTemplate x:Key="birthdayTemplate">
            <Grid>
                <TextBlock
                    HorizontalAlignment="Center"
                    VerticalAlignment="Center"
                    Text="{Binding DisplayText}" />
                <Path
                    Width="18"
                    Height="18"
                    Margin="3"
                    HorizontalAlignment="Right"
                    VerticalAlignment="Bottom"
                    Data="{StaticResource birthday}"
                    Fill="{ThemeResource SystemBaseHighColor}"
                    Stretch="Uniform" />
            </Grid>
        </DataTemplate>
        <DataTemplate x:Key="giftTemplate">
            <Grid>
                <TextBlock
                    HorizontalAlignment="Center"
                    VerticalAlignment="Center"
                    Text="{Binding DisplayText}" />
                <Path
                    Width="18"
                    Height="18"
                    Margin="3"
                    HorizontalAlignment="Right"
                    VerticalAlignment="Bottom"
                    Data="{StaticResource gift}"
                    Fill="{ThemeResource SystemBaseHighColor}"
                    Stretch="Uniform" />
            </Grid>
        </DataTemplate>
        <DataTemplate x:Key="awardTemplate">
            <Grid>
                <TextBlock
                    HorizontalAlignment="Center"
                    VerticalAlignment="Center"
                    Text="{Binding DisplayText}" />
                <Path
                    Width="18"
                    Height="18"
                    Margin="3"
                    HorizontalAlignment="Right"
                    VerticalAlignment="Bottom"
                    Data="{StaticResource award}"
                    Fill="{ThemeResource SystemBaseHighColor}"
                    Stretch="Uniform" />
            </Grid>
        </DataTemplate>

        <local:DateItemTemplateSelector
            x:Key="selector"
            AwardTemplate="{StaticResource awardTemplate}"
            BirthdayTemplate="{StaticResource birthdayTemplate}"
            DefaultTemplate="{StaticResource defaultTemplate}"
            GiftTemplate="{StaticResource giftTemplate}" />
    </Page.Resources>

    <editors:SfDatePicker ItemTemplateSelector="{StaticResource selector}"
                          x:Name="sfDatePicker"/>

{% endhighlight %}
{% endtabs %}

![Custom UI of specific date cells in dropdown spinner](Dropdown-Date-Spinner_images/ItemTemplateSelector.png)

N> Download demo application from [GitHub]()

## Setting hints in dropdown header

You can add a hints in dropdown header by using the [DropDownHeader](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_DropDownHeader) property. The dropdown hints shown only by setting the [ShowDropDownHeader](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_ShowDropDownHeader) property values as `true`. Otherwise, drop down header will not be shown. The default value of `DropDownHeader` property is `null` and `ShowDropDownHeader` property is `false`.

{% tabs %}
{% highlight XAML %}

<editors:SfDatePicker DropDownHeader="Select Date" 
                      ShowDropDownHeader="True" 
				      x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.DropDownHeader = "Select Date";
sfDatePicker.ShowDropDownHeader = true;

{% endhighlight %}
{% endtabs %}

![DatePicker displays the drop down date spinner header](Dropdown-Date-Spinner_images/DropDownHeader.png)

N> Download demo application from [GitHub]()

## Custom UI of dropdown header

You can customize the header of dropdown date spinner by using the [DropDownHeaderTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_DropDownHeaderTemplate) property. The `DataContext` of `DropDownHeaderTemplate` property is `SfDatePicker.DropDownHeader`.

{% tabs %}
{% highlight XAML %}

<editors:SfDatePicker DropDownHeader="Choose a Travel Date" 
                      ShowDropDownHeader="True" 
	                  x:Name="sfDatePicker">
    <editors:SfDatePicker.DropDownHeaderTemplate>
        <DataTemplate>
            <StackPanel>
                <TextBlock
                    HorizontalAlignment="Center"
                    VerticalAlignment="Center"
                    Foreground="Green"
                    Text="{Binding}" />
                <Path
                    Width="32"
                    Height="32"
                    Margin="5,5,5,10"
                    HorizontalAlignment="Center"
                    VerticalAlignment="Bottom"
                    Fill="Blue"
                    Data="M5.0499409,20.854989C5.6799391,20.854989 6.1909379,21.365994 6.1909379,21.995999 6.1909379,22.626004 5.6799391,23.137007 5.0499409,23.137007 4.4199427,23.137007 3.9099439,22.626004 3.9099437,21.995999 3.9099439,21.365994 4.4199427,20.854989 5.0499409,20.854989z M14.596949,20.759993C15.226947,20.759993 15.737946,21.270998 15.737946,21.901003 15.737946,22.531008 15.226947,23.042012 14.596949,23.042012 13.966951,23.042012 13.456952,22.531008 13.456952,21.901003 13.456952,21.270998 13.966951,20.759993 14.596949,20.759993z M5.4789585,10.087996C5.2049588,10.087996,4.9809588,10.311996,4.9809588,10.585996L4.9809588,12.577998C4.9809588,14.500999,6.5449585,16.065,8.4669574,16.065L11.455957,16.065C13.377957,16.065,14.941956,14.500999,14.941956,12.577998L14.941956,10.585996C14.941956,10.311996,14.718956,10.087996,14.443957,10.087996z M5.4789585,9.0919948L14.443957,9.0919948C15.267956,9.0919948,15.937956,9.7619953,15.937956,10.585996L15.937956,12.577998C15.937956,15.05,13.927957,17.061,11.455957,17.061L8.4669574,17.061C5.9959587,17.061,3.984959,15.05,3.9849592,12.577998L3.9849592,10.585996C3.984959,9.7619953,4.6549586,9.0919948,5.4789585,9.0919948z M10.605848,6.2067145C10.182643,6.2076663,9.9221548,6.2276208,9.9099678,6.2286375L9.8250068,6.2326353C3.4400006,6.2326355,2.1699818,8.8086996,1.9920029,9.2787094L1.9920029,23.634949C1.9920033,24.403944,2.6179796,25.030968,3.3879987,25.030968L16.945976,25.030968C17.489004,25.030968,17.929983,24.588944,17.929983,24.044928L17.931997,9.3637023C16.43066,6.4917114,12.266111,6.202981,10.605848,6.2067145z M10.652609,4.2130087C12.769905,4.2105492,17.93724,4.6332789,19.83196,8.7126899L19.924001,8.9116983 19.922963,24.044928C19.922963,25.686985,18.586965,27.023009,16.945976,27.023009L15.744038,27.023009 18.39861,30.386019C18.739616,30.818005 18.665614,31.444987 18.234607,31.785977 18.051605,31.929972 17.8336,31.99997 17.617597,31.99997 17.322593,31.99997 17.030588,31.870974 16.834585,31.621981L13.203441,27.023009 7.3373374,27.023009 3.7063731,31.621964C3.5103699,31.869967 3.2183651,31.99997 2.92336,31.99997 2.7073566,31.99997 2.489353,31.929968 2.3063499,31.785967 1.8753428,31.444962 1.8013416,30.817952 2.1423472,30.385945L4.7967409,27.023009 3.3879987,27.023009C1.5189811,27.023009,1.5606929E-09,25.502963,0,23.634949L0.018981917,8.9346786C0.057983368,8.7426891 1.067016,4.2546039 9.7849678,4.2405961 9.9051145,4.2323452 10.21317,4.2135194 10.652609,4.2130087z M9.9619535,0C10.772957,0 11.430959,0.65799594 11.430959,1.4689908 11.430959,2.2799857 10.772957,2.9379814 9.9619535,2.9379817 9.1509508,2.9379814 8.4929479,2.2799857 8.4929479,1.4689908 8.4929479,0.65799594 9.1509508,0 9.9619535,0z"
                    Stretch="Uniform" />
            </StackPanel>
        </DataTemplate>
    </editors:SfDatePicker.DropDownHeaderTemplate>
</editors:SfDatePicker>

{% endhighlight %}
{% endtabs %}

![DatePicker with customized drop down date spinner header](Dropdown-Date-Spinner_images/DropDownHeaderTemplate.png)

N> Download demo application from [GitHub]()

## Hide the dropdown column headers

If you want to hide the dropdown day, month and year spinner's column headers, use the [ShowColumnHeaders](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_ShowColumnHeaders) property value as `false`. The default value of `ShowColumnHeaders` property is `true`.

{% tabs %}
{% highlight XAML %}

<editors:SfDatePicker ShowColumnHeaders="False" 
                      x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.ShowColumnHeaders = false;

{% endhighlight %}
{% endtabs %}

![DatePicker hides the drop down date spinner column headers](Dropdown-Date-Spinner_images/ShowColumnHeaders.png)

N> Download demo application from [GitHub]()

## Hide submit button(Select date directly from date spinner)

If you want to hide the submit button and select the date directly from the drop down date spinner without clicking the `Ok` button, use the [ShowSubmitButtons](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_ShowSubmitButtons) property value as `false`. The default value of `ShowSubmitButtons` property is `true`.

{% tabs %}
{% highlight XAML %}

<editors:SfDatePicker ShowSubmitButtons="False"
                      x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.ShowSubmitButtons = false;

{% endhighlight %}
{% endtabs %}

![SfDatePicker hides the drop down date spinner submit and cancel buttons](Getting-Started_images/ShowSubmitButtons.gif)

## Change the number of dates to be shown in the dropdown

You can change the number of dates to be shown in the drop down date spinner by using the [VisibleItemsCount](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_VisibleItemsCount) property. The default value of `VisibleItemsCount` property is `-1`.

{% tabs %}
{% highlight XAML %}

<editors:SfDatePicker VisibleItemsCount="5" 
                      x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.VisibleItemsCount = 5

{% endhighlight %}
{% endtabs %}

![Number of dates to be shown in the dropdown is changed](Dropdown-Date-Spinner_images/VisibleItemsCount.png)

N> Download demo application from [GitHub]()

## Change the size of dropdown cells

You can change the cell size in the drop down date spinner by setting the values to [ItemWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_ItemWidth) and [ItemHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_ItemHeight) properties. The default value of the `ItemWidth` and `ItemHeight` properties is `80` and `40`. 

You can also restrict the width of drop down date spinner cells with particular pixels by using the [MinItemWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_MinItemWidth) and [MaxItemWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDatePicker.html#Syncfusion_UI_Xaml_Editors_SfDatePicker_MaxItemWidth) properties. The default value of `MinItemWidth` property is `0` and `MaxItemWidth` property is `Infinity`.

N> `ItemWidth` values must be within the `MinItemWidth` and `MaxItemWidth`values. Otherwise, `ItemWidth` will take the closest value from `MinItemWidth` or `MaxItemWidth` value.

{% tabs %}
{% highlight XAML %}

<editors:SfDatePicker MinItemWidth="70" 
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

![Drop down date spinner cell size changed](Dropdown-Date-Spinner_images/ItemWidth.png)

N> Download demo application from [GitHub]()

## Change dropdown height

You can change the height of drop down date spinner by using the [DropDownHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_DropDownHeight) property. Based on the value of `DropDownHeight`, `ItemWidth` and `ItemHeight`, date items to be visible. The default value of `DropDownHeight` property is `NaN`.

{% tabs %}
{% highlight XAML %}

<editors:SfDatePicker DropDownHeight="500"
                      x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.DropDownHeight = 500;

{% endhighlight %}
{% endtabs %}

![DatePicker with customized dropdown height](Dropdown-Date-Spinner_images/DropDownHeight.png)

N> Download demo application from [GitHub]()

## Change flow direction

You can change the flow direction of the `DatePicker` layout from right to left by setting the `FlowDirection` property value as `RightToLeft`. The default value of `FlowDirection` property is `LeftToRight`.

{% tabs %}
{% highlight XAML %}

<editors:SfDatePicker FlowDirection="RightToLeft" 
                      x:Name="sfDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.FlowDirection = FlowDirection.RightToLeft;

{% endhighlight %}
{% endtabs %}

![DatePicker flow direction changed to right to left](Dropdown-Date-Spinner_images/FlowDirection.png)

N> Download demo application from [GitHub]()
