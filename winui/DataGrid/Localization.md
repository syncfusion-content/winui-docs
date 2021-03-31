---
layout: post
title: Localization | DataGrid | WinUI | Syncfusion
description: Learn about localization support to customize the default strings in Syncfusion WinUI DataGrid (SfDataGrid) control and more details.
platform: winui
control: DataGrid
documentation: ug
---


# Localization in WinUI DataGrid (SfDataGrid)

Localization is the process of translating the application resources into different language for the specific cultures. You can localize the SfDataGrid by adding [resource](https://msdn.microsoft.com/library/aa992030.aspx) file. Application culture can be changed by setting [CurrentUICulture] (https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.currentuiculture.aspx) before `InitializeComponent()` method. 

Below application culture changed to German.

{% tabs %}
{% highlight c# %}
public MainPage()
{
    CultureInfo.CurrentUICulture = new CultureInfo("de");

    InitializeComponent();
}    
{% endhighlight %}
{% endtabs %}


To localize the SfDataGrid based on `CurrentUICulture` using resource files, follow the below steps. 

N> You can get the default resource files of all Syncfusion WinUI libraries from [GitHub](https://github.com/syncfusion/winui-controls-localization-resource-files).

1) Right click your project and add new folder named Resources.

2) Add another folder and name the folder name as culture name. For example, you have to give name as de for German culture. Find the supported culture codes from [here](https://docs.microsoft.com/en-us/windows/uwp/app-resources/how-rms-matches-lang-tags) 

3) Add [default resource files](https://github.com/syncfusion/winui-controls-localization-resource-files) in the following structure.

![Resw file in WinUI DataGrid](Localization_images/Resw-file-in-WinUI-DataGrid.png)
 
4) Now, you can define the key names from default resource files and assign value based on the culture.

![Localization in WinUI DataGrid](Localization_images/Localization-in-WinUI-DataGrid.png)

![Shows the localized in German for WinUI DataGrid](Localization_images/Shows-the-localized-in-German-for-WinUI-DataGrid.png)

5) Also, localize application text in XAML using below steps

    a)Add resource name in .resx file
	
![Localize application text in WinUI DataGrid](Localization_images/Localize-application-text-in-WinUI-DataGrid.png)

    b)Refer the mentioned resource name in XAML like below.
	
{% tabs %}
{% highlight xaml %}
xmlns:grid="using:Syncfusion.UI.Xaml.Grids"
xmlns:dataGrid="using:Syncfusion.UI.Xaml.DataGrid"

<dataGrid:SfDataGrid x:Name="sfDataGrid"
                       AddNewRowPosition="Top"
                       AutoGenerateColumns="False"
                       ItemsSource="{Binding Orders}">
    <dataGrid:SfDataGrid.Columns>
        <dataGrid:GridTextColumn HeaderText="{grid:GridLocalizationResourceExtension ResourceName=OrderIDText}" MappingName="OrderID" TextAlignment="Right"/>
        <dataGrid:GridTextColumn HeaderText="{grid:GridLocalizationResourceExtension ResourceName=CustomerIDText}" MappingName="CustomerID" />
        <dataGrid:GridTextColumn HeaderText="{gGrid:GridLocalizationResourceExtension ResourceName=CustomerNameText}" MappingName="CustomerName" />
        <dataGrid:GridTextColumn HeaderText="{grid:GridLocalizationResourceExtension ResourceName=CountryText}" MappingName="Country" />
        <dataGrid:GridTextColumn HeaderText="{grid:GridLocalizationResourceExtension ResourceName=UnitPriceText}" MappingName="UnitPrice" TextAlignment="Right"/>
    </dataGrid:SfDataGrid.Columns>
</dataGrid:SfDataGrid>
{% endhighlight %}
{% endtabs %}

![Shows the localized application text in German for WinUI DataGrid](Localization_images/Shows-the-localized-application-text-in-German-for-WinUI-DataGrid.png)

## Editing default culture resource

You can change the default string of datagrid control by adding the default .resw files ([from GitHub](https://github.com/syncfusion/winui-controls-localization-resource-files)) to Resources folder of your application. Syncfusion WinUI controls reads the default string from the .resw files of application if its added.
