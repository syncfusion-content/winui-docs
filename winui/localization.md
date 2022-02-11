---
layout: post
title: Localization of Syncfusion WinUI Controls
description: Learn about localization support in Syncfusion WinUI controls using the .resw files and editing default strings of WinUI controls.
platform: winui
control: Localization
documentation: ug
---

# Localization of Syncfusion WinUI controls

Localization is the process of making an application multilingual by formatting the content according to the cultures. This involves configuring the application for a specific language. Culture is the combination of language and location. For example, 
 `en-US` is the culture of English spoken in the United States, while `en-GB` is the culture of English spoken in Great Britain. Syncfusion WinUI controls can be localized by adding resource files for each language.

## Changing application culture

The application culture can be changed by assigning the `CultureInfo.CurrentUICulture` to the desired language in the constructor of the main page. Localization can be done while changing the application culture by creating a.resw file.

{% tabs %}

{% highlight c# %}

    public sealed partial class MainPage
    {
        public MainPage()
        {
            CultureInfo.CurrentUICulture = new CultureInfo("de");
            this.InitializeComponent();
        }
    }

{% endhighlight %}

{% endtabs %}

## Creating .resw files

The following steps can be used to generate .resw files for any language:

N> The default resource files of all Syncfusion WinUI libraries can be obtained from [GitHub](https://github.com/syncfusion/winui-controls-localization-resource-files).

1) Right-click the project and add a New folder named as "Resources".

2) Add another folder and name the folder with "Culture name". For example, "de" for German culture. Find the supported culture codes from [here](https://docs.microsoft.com/en-us/windows/uwp/app-resources/how-rms-matches-lang-tags). 

3) Add [default resource files](https://github.com/syncfusion/winui-controls-localization-resource-files) in the following structure.

![WinUI DataGrid resw file](Localization-images/resources-in-winui-project.png)

N> If the `SfDataGrid` control is used in the application, copy and paste the `Syncfusion.Grid.WinUI.resw` (SfDataGrid present in the Syncfusion.Grid.WinUI library) file into the application under Resources folder. So, now you know the key names and values of the default strings in the Syncfusion.Grid.WinUI library.

4) Now, the key names from default resource files can be defined and assigned values based on culture.

![WinUI DataGrid Localization](Localization-images/winui-datagrid-resource-keys.png)

> Download demo from [GitHub](https://github.com/SyncfusionExamples/winui-datagrid-localization)

## Editing default culture strings

The default string of any control can be changed by adding the default .resw files (from [GitHub](https://github.com/syncfusion/winui-controls-localization-resource-files)) to the Resources folder of the application. If the default string is added, Syncfusion WinUI controls reads it from the .resw files of the application.