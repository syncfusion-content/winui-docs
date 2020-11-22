---
layout: post
title: Localization of Syncfusion WinUI Controls
description: Learn about localization support in Syncfusion WinUI controls using .resw files and explains editing default strings of WinUI controls.
platform: winui
control: Localization
documentation: ug
---

# Localization of Syncfusion WinUI controls

Localization is the process of making application multilingual by formatting the content according to the cultures. This involves configuring the application for a specific language. Culture is the combination of language and location. For example, en-US is the culture for English spoken in United States; en-GB is the culture for English spoken in Great Britain. Syncfusion WinUI controls can be localized by adding resource file for each language.

## Changing application culture

We can change the application culture by assigning the `CultureInfo.CurrentUICulture` to the desired language in the constructor of the Main page. When you are changing the application culture, then you can localize the application based on application culture by creating .resw file.

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

You can create .resw files for any language by following the steps below,

N> You can get the default resource files of all Syncfusion WinUI libraries from [GitHub](https://github.com/syncfusion/winui-controls-localization-resource-files).

1) Right click your project and add new folder named Resources.

2) Add another folder and name the folder name as culture name. For example, you have to give name as de for German culture. Find the supported culture codes from [here](https://docs.microsoft.com/en-us/windows/uwp/app-resources/how-rms-matches-lang-tags) 

3) Add [default resource files](https://github.com/syncfusion/winui-controls-localization-resource-files) in the following structure.

![WinUI DataGrid resw file](Localization-images/resources-in-winui-project.png)

N> Consider you are using `SfDataGrid` control in your application. Then you need to copy and include `Syncfusion.Grid.WinUI.resw` (SfDataGrid present in Syncfusion.Grid.WinUI library) file in your application under Resources folder. So, now you can know the key names and values of default strings used in Syncfusion.Grid.WinUI library.

4) Now, you can define the key names from default resource files and assign value based on the culture.

![WinUI DataGrid Localization](Localization-images/winui-datagrid-resource-keys.png)

> Download demo from [GitHub](https://github.com/SyncfusionExamples/winui-datagrid-localization)

## Editing default culture strings

You can change the default string of any control by adding the default .resw files (from [GitHub](https://github.com/syncfusion/winui-controls-localization-resource-files)) to Resources folder of your application. Syncfusion WinUI controls reads the default string from the .resw files of application if its added.