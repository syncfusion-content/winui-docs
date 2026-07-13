---
layout: post
title: Localization of Syncfusion WinUI Controls
description: Learn about localization support in Syncfusion WinUI controls using the .resw files and editing default strings of WinUI controls.
platform: winui
control: Localization
documentation: ug
---

# Localization of Syncfusion<sup>&reg;</sup> WinUI controls

Localization is the process of making an application multilingual by formatting the content according to the languages. This involves configuring the application for a specific language. For example `en-US` is the language of English spoken in the United States, while `en-GB` is the language of English spoken in Great Britain. Syncfusion<sup>&reg;</sup> WinUI controls can be localized by adding resource files for each language.

## Changing application language

The application language can be changed by setting the desired language to the [ApplicationLanguages.PrimaryLanguageOverride](https://learn.microsoft.com/en-us/uwp/api/windows.globalization.applicationlanguages.primarylanguageoverride?view=winrt-19041) property in the constructor of the main window. Localization can be done while changing the application language by creating a .resw file.

{% tabs %}

{% highlight c# %}

    public sealed partial class MainWindow : Window
    {
        public MainWindow()
        {
            Microsoft.Windows.Globalization.ApplicationLanguages.PrimaryLanguageOverride = "de";
            this.InitializeComponent();            
        }
    }

{% endhighlight %}

{% endtabs %}

### For packaged deployments only

You can also use the `Windows.Globalization.ApplicationLanguages.PrimaryLanguageOverride` property. However, in unpackaged deployments, it may cause the app to crash.

{% tabs %}

{% highlight c# %}

    public sealed partial class MainWindow : Window
    {
        public MainWindow()
        {
            Windows.Globalization.ApplicationLanguages.PrimaryLanguageOverride = "de";
            this.InitializeComponent();
        }
    }

{% endhighlight %}

{% endtabs %}

N> We recommend setting the `ApplicationLanguages.PrimaryLanguageOverride` property **before** the `InitializeComponent` method call if you have added a .resw file to your project. Otherwise, it may cause the app to crash. The [supported culture codes](https://docs.microsoft.com/en-us/windows/uwp/app-resources/how-rms-matches-lang-tags) can be used as the language value (e.g., `de` for German).

The following screenshot illustrates how the localization is applied to the datagrid based on the defined language to the [ApplicationLanguages.PrimaryLanguageOverride](https://learn.microsoft.com/en-us/uwp/api/windows.globalization.applicationlanguages.primarylanguageoverride?view=winrt-19041) property.

<img src="Localization-images/winui-datagrid-localization.png" alt="WinUI DataGrid Localization" width="100%" Height="Auto"/>


## Creating .resw files

The following steps can be used to generate .resw files for any language:

N> The default resource files of all Syncfusion<sup>&reg;</sup> WinUI libraries can be obtained from [GitHub](https://github.com/syncfusion/winui-controls-localization-resource-files).

1) Right-click the project and add a new folder named **Resources**.

2) Add another folder named with the **language name**. For example, use `de` for German. Find the supported culture codes from [here](https://docs.microsoft.com/en-us/windows/uwp/app-resources/how-rms-matches-lang-tags). 

3) Add the [default resource files](https://github.com/syncfusion/winui-controls-localization-resource-files) in the following structure.

![WinUI DataGrid resw file](Localization-images/resources-in-winui-project.png)

N> If the [SfDataGrid](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.html) control is used in the application, copy and paste the `Syncfusion.Grid.WinUI.resw` (SfDataGrid is present in the Syncfusion.Grid.WinUI library) file into the **Resources** folder. These default files contain the key names and values of the default strings in the Syncfusion.Grid.WinUI library.


4) Now, the key names from default resource files can be defined and assigned values based on language.

![WinUI DataGrid Localization](Localization-images/winui-datagrid-resource-keys.png)

> Download demo from [GitHub](https://github.com/SyncfusionExamples/winui-datagrid-localization)

## Editing default language strings

The default string of any control can be changed by adding the default .resw files (from [GitHub](https://github.com/syncfusion/winui-controls-localization-resource-files)) to the Resources folder of the application. If the default string is added, Syncfusion<sup>&reg;</sup> WinUI controls reads it from the .resw files of the application.

## Localizing without using .resw files

You can localize the WinUI controls using the [Provider](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.LocalizationProvider.html#Syncfusion_UI_Xaml_Core_LocalizationProvider_Provider) property of the [LocalizationProvider](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.LocalizationProvider.html) class.

To implement localization of [Syncfusion WinUI](https://help.syncfusion.com/cr/winui) controls without using `.resw` files, using a custom string, follow the steps below.

**Implementation in sample:**

The following procedure helps you localize WinUI controls using a string provider.

**Step 1:** Include the required namespace `using Syncfusion.UI.Xaml.Core;` at the beginning of the file. Refer to [Syncfusion.UI.Xaml.Core](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.html) for more information.

**Step 2:** Create a class that implements the [ILocalizationProvider](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.ILocalizationProvider.html) interface defined in the `Syncfusion.UI.Xaml.Core` namespace in the `Syncfusion.Core.WinUI.dll`.

**Step 3:** In the `GetLocalizedString` method, return a custom string value for a localizable key. If the same key name exists in two different assemblies, you can retrieve the specific assembly's name along with the key to update the custom string for that key from the desired assembly by using the `ResourceAssemblyName` property of the [LocalizationInfo](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.LocalizationInfo.html) parameter.

**Step 4:** Return `null` for the rest of the localizable keys that are not involved in the localization. These keys are loaded with a resource map if available; otherwise, they fall back to the default resource map.

**Step 5:** Assign the instance to the [Provider](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.LocalizationProvider.html#Syncfusion_UI_Xaml_Core_LocalizationProvider_Provider) property of the [LocalizationProvider](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.LocalizationProvider.html) class, before the `InitializeComponent` call in the constructor of the application.

**Registering the provider:**

{% tabs %}

{% highlight c# %}

    LocalizationProvider.Provider = new MyStringLoader(); 

{% endhighlight %}

{% endtabs %}

The following code example is a reference to assign a localization string to the [DataGrid control](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.html) in WinUI without using `.resw` files.

**Implementing the provider:**

{% tabs %}

{% highlight c# %}

using Syncfusion.UI.Xaml.Core;

public class MyStringLoader : ILocalizationProvider
{
    public string GetLocalizedString(LocalizationInfo info) 
    {
        if (info.ResourceAssemblyName == "Syncfusion.Grid.WinUI" && info.ResourceName == "SortDateDescending")
        {
            return "CustomText";
        }

        switch (info.ResourceName)
        {
            case "AddNewRowText": // resource key from Syncfusion.Grid.WinUI assembly 
                return "CustomText1"; 
            case "Automatic":   // resource key from Syncfusion.Editors.WinUI assembly
                return "CustomText2";
            default:
                return null; 
        }
    }
}

{% endhighlight %}

{% endtabs %}

{% tabs %}

{% highlight c#  %}

public partial class App : Application
{
    public App()
    {
        LocalizationProvider.Provider = new MyStringLoader();
        this.InitializeComponent();
    }
}

{% endhighlight %}

{% endtabs %}

N> Using `Provider` (highest priority, overrides everything) - Uses your own implemented method for localization. Using a `resource map` (fallback option) - Uses your own created resource file. This file contains a table with keys values where we can set our own values.
