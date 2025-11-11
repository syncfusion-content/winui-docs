---
layout: post
title: Guide to run online and offline samples from WinUI Studio | Syncfusion
description: Learn how to run the online samples and offline samples of Syncfusion Essential Studio WinUI controls and components.
platform: winui
control: Samples
documentation: ug
---

# Featured Samples for Syncfusion<sup>&reg;</sup> WinUI Controls

## Syncfusion<sup>&reg;</sup> WinUI control panel

To explore Syncfusion<sup>&reg;</sup> WinUI controls and components, open the `Syncfusion<sup>&reg;</sup> WinUI Controls Panel` by searching it from Start and Open. 

![WinUI Control Panel Search](Guide-to-run-the-samples-images/winui-control-panel-search.png)

In another way, open the Control Panel from the following installed location.

C:\Program Files (x86)\Syncfusion\Essential Studio\WinUI\{{ site.releaseversion }}\Infrastructure\Launcher\Syncfusion WinUI Control Panel.exe 

N> In the above section, latest Essential Studio<sup>&reg;</sup> version details has been provided. Refer installed Essential Studio<sup>&reg;</sup> version instead of mentioned version.

## Syncfusion<sup>&reg;</sup> Controls Gallery for WinUI Desktop

The Syncfusion<sup>&reg;</sup> WinUI desktop controls can be explored in the Visual Studio by clicking `Run Local Demos`.
 
 ![Explore Syncfusion WinUI Demos with Desktop Project](Guide-to-run-the-samples-images/exploring-winui-desktop-sample-browser-new.png)

![Syncfusion WinUI Sample Browser with Desktop Project](Guide-to-run-the-samples-images/syncfusion-winui-desktop-sample-browser.png)

## Offline samples

![Exploring Syncfusion WinUI Samples from Syncfusion WinUI Sample Browser](Guide-to-run-the-samples-images/exploring-syncfusion-winui-samples-from-sb.png)

* The individual control samples can also be run by exploring the individual control project.

For example, following is a demonstration to run an individual `Chart` control project in Visual Studio.

![Exploring the Syncfusion WinUI individual control project](Guide-to-run-the-samples-images/exploring-individual-control-project.png)

* Open a standalone executable project desktop (not a lib project) in the Visual Studio, which is available under the category name.

 ![Open the standalone WinUI project in Visual Studio](Guide-to-run-the-samples-images/open-standalone-winui-project-in-visual-studio-new.png)

* Build and deploy the individual control executable project, then run the application.

![Running an individual control project](Guide-to-run-the-samples-images/run-induvidual-control-project.png)

All the sample browser projects are configured as single SDK-style projects that support multiple frameworks: `.NET 8.0`, `.NET 9.0`, and `.NET 10`. 

When you click the `Run Local Demos` or `Explore Demo Source` button, the  `net10.0-windows` entry will be automatically removed from the targets file if `.NET 10` is not installed on your machine, preventing any compilation errors. 

To use the `.NET 10 framework`, install the required SDK and add `net10.0-windows` to the < TargetFrameworks > tag in the `MultiTargeting.targets` file located at the Samples Location:[D:\WinUI31.2.9\WinUI\31.2.9\SampleBrowser\targets\MultiTargeting.targets] as shown in the image below. 

![WinUI TargetFrameworks](Guide-to-run-the-samples-images/TargetFrameworks_winui.png)

## Online Sample

* Download and install demos from [Microsoft Store](https://www.microsoft.com/en-in/p/syncfusion-winui-controls-gallery/9n0fp16ddc06?activetab=pivot:overviewtab).


## Download demos from online (clone from github repository)

Explore the Syncfusion<sup>&reg;</sup> WinUI controls using [GitHub WinUI demos](https://github.com/syncfusion/winui-demos), where all WinUI demos are configured using `NuGet` to run without installing Syncfusion<sup>&reg;</sup> WinUI Studio.