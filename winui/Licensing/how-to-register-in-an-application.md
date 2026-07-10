---
layout: post
title: Overview of Syncfusion license registration - Syncfusion
description: Learn how to register the Syncfusion license key in a WinUI application for license validation.
platform: WinUI
control: Essential Studio
documentation: ug
---

# Register Syncfusion license key in a WinUI application

To generate or obtain a license key, see [License key generation](https://www.syncfusion.com/account/licensing).

N> **Prerequisites:** Install the Syncfusion WinUI NuGet package (for example, `Syncfusion.Licensing.WinUI`, or the platform-specific control package that depends on it) from the Syncfusion NuGet feed, and ensure `Syncfusion.Licensing.dll` is referenced in your project. Licensing support is available in Syncfusion Essential Studio version 20.1.0.47 and later.

The generated license key is a string that must be registered before any Syncfusion control is initialized. The `Syncfusion.Licensing.SyncfusionLicenseProvider.RegisterLicense` method takes the license-key string as its only parameter and returns `void`. The following code registers the license.

{% tabs %}
{% highlight c# %}
Syncfusion.Licensing.SyncfusionLicenseProvider.RegisterLicense("YOUR LICENSE KEY");
{% endhighlight %}
{% endtabs %}

N> * Place the license key between double quotes.  Also, ensure that Syncfusion.Licensing.dll is referenced in your project where the license key is being registered.
* Syncfusion license validation is done offline during application execution and does not require internet access.  Apps registered with a Syncfusion license key can be deployed on any system that does not have an internet connection.

I> Syncfusion license keys can be validated during the Continuous Integration (CI) processes to ensure proper licensing and prevent licensing errors during deployment. Refer to the [CI License Validation](https://help.syncfusion.com/winui/licensing/licensing-faq/ci-license-validation) section for detailed instructions on how to implement it.

### WinUI 

You can register the license key in App constructor of **App.xaml.cs** in C#. If App constructor not available in **App.xaml.cs**, create the "App()" constructor in **App.xaml.cs** and register the license key inside the constructor. In Visual Basic, register the license code in **App.xaml.vb**.

{% tabs %}
{% highlight c# %}
public partial class App : Application
{
	public App()
	{
		//Register Syncfusion license
		Syncfusion.Licensing.SyncfusionLicenseProvider.RegisterLicense("YOUR LICENSE KEY");
	}	
} 
{% endhighlight %}
{% endtabs %}