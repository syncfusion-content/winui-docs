---
layout: post
title: Localization of Syncfusion WinUI Controls
description: Learn about localization support in Syncfusion WinUI controls using the .resw files and editing default strings of WinUI controls.
platform: winui
control: Localization
documentation: ug
---

# Localization of Syncfusion<sup>&reg;</sup> WinUI controls

Localization is the process of making an application multilingual by formatting the content according to the languages. This involves configuring the application for a specific language. For example, 
 `en-US` is the language of English spoken in the United States, while `en-GB` is the language of English spoken in Great Britain. Syncfusion<sup>&reg;</sup> WinUI controls can be localized by adding resource files for each language.

## Changing application language

The application language can be changed by setting the desired language to respective control name with the `ResourceContext.QualifierValues["Language"]` property in the constructor of the main window. Localization can be done while changing the application language by creating a .resw file.

{% tabs %}

{% highlight c# %}

    public sealed partial class MainWindow : Window
    {
        public MainWindow()
        {
            {ControlLocalizationResouceAccessor}.Instance.ResourceContext.QualifierValues["Language"] = "{Language}";
            // eg: EditorsLocalizationResourceAccessor.Instance.ResourceContext.QualifierValues["Language"] = "de";
            this.InitializeComponent();
        }
    }

{% endhighlight %}

{% endtabs %}

**Control resource Accessor list**

<table>
    <tr>
        <td><b>Controls</b></td>
        <td><b>LocalizationName</b></td>
    </tr>
    <tr>
        <td>Editors</td>
        <td>EditorsLocalizationResourceAccessor</td>
    </tr>
    <tr>
        <td>Ribbon</td>
        <td>RibbonLocalizationResourceAccessor</td>
    </tr>
    <tr>
        <td>DataGrid</td>
        <td>GridLocalizationResourceAccessor</td>
    </tr>
    <tr>
        <td>TreeView</td>
        <td>TreeViewLocalizationResourceAccessor</td>
    </tr>
    <tr>
        <td>Scheduler</td>
        <td>SchedulerLocalizationResourceAccessor</td>
    </tr>
    <tr>
        <td>TreeView</td>
        <td>TreeViewLocalizationResourceAccessor</td>
    </tr>
    <tr>
        <td>Kanban</td>
        <td>KanbanLocalizationResourceAccessor</td>
    </tr>
    <tr>
        <td>Chat</td>
        <td>ChatLocalizationResourceAccessor</td>
    </tr>
</table>

N> We recommend to set the above code before InitializeComponent method when you added the '.resw' file in your project. [If not, it leads to crash the project.]

The following screenshot illustrates how the localization is applied to the datagrid based on the defined language to the `ResourceContext.QualifierValues["Language"]` property.

<img src="Localization-images/winui-datagrid-localization.png" alt="WinUI DataGrid Localization" width="100%" Height="Auto"/>


## Creating .resw files

The following steps can be used to generate .resw files for any language:

N> The default resource files of all Syncfusion<sup>&reg;</sup> WinUI libraries can be obtained from [GitHub](https://github.com/syncfusion/winui-controls-localization-resource-files).

1) Right-click the project and add a New folder named as "Resources".

2) Add another folder and name the folder with "language name". For example, "de" for German language. Find the supported culture codes from [here](https://docs.microsoft.com/en-us/windows/uwp/app-resources/how-rms-matches-lang-tags). 

3) Add [default resource files](https://github.com/syncfusion/winui-controls-localization-resource-files) in the following structure.

![WinUI DataGrid resw file](Localization-images/resources-in-winui-project.png)

N> If the `SfDataGrid` control is used in the application, copy and paste the `Syncfusion.Grid.WinUI.resw` (SfDataGrid present in the Syncfusion.Grid.WinUI library) file into the application under Resources folder. So, now you know the key names and values of the default strings in the Syncfusion.Grid.WinUI library.

4) Now, the key names from default resource files can be defined and assigned values based on language.

![WinUI DataGrid Localization](Localization-images/winui-datagrid-resource-keys.png)

> Download demo from [GitHub](https://github.com/SyncfusionExamples/winui-datagrid-localization)

## Editing default language strings

The default string of any control can be changed by adding the default .resw files (from [GitHub](https://github.com/syncfusion/winui-controls-localization-resource-files)) to the Resources folder of the application. If the default string is added, Syncfusion<sup>&reg;</sup> WinUI controls reads it from the .resw files of the application.