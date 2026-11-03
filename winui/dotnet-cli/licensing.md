---
layout: post
title: License Activation using Syncfusion .NET CLI | Syncfusion®
description: Learn here about how to activate and view Syncfusion® licenses for WinUI 3 projects using the Syncfusion® .NET CLI (sf) license commands.
platform: winui
control: Syncfusion<sup>®</sup> .NET CLI
documentation: ug
---

# Activate Syncfusion<sup>®</sup> licenses

The CLI detects the Syncfusion<sup>®</sup> controls used in a project, downloads the matching license keys from your Syncfusion<sup>®</sup> account, and registers the keys in the project's startup code. For example, when a sample is created with the DataGrid control, the CLI registers the license for `Syncfusion.Grid.WinUI` in `App.xaml.cs` so the build runs without a license warning.

N> Open the Command Prompt or Terminal in the target sample's project directory before running the license activation command. The license operation is project-specific, and the command path must point to the intended sample.

## Sign in to Syncfusion

License activation requires a signed-in Syncfusion<sup>®</sup> account. You can sign in ahead of activation, or the CLI prompts you during activation when no session exists.

1. Run the following command to sign in to your Syncfusion<sup>®</sup> account:

    {% tabs %}
    {% highlight bash tabtitle="Bash" %}

    sf login

    {% endhighlight %}
    {% endtabs %}

2. The CLI opens your default browser to the Syncfusion<sup>®</sup> sign-in page. Complete sign in with your Syncfusion<sup>®</sup> account credentials.

    ![Syncfusion sign-in page in the browser](images/cli-license-sign-in.png)

3. After sign in completes, the browser confirms the session and the CLI stores it locally so subsequent license operations do not require sign in again.

## Activate a license through the interactive menu

1. Open the Command Prompt or Terminal in the target sample's project directory.

    {% tabs %}
    {% highlight bash tabtitle="Bash" %}

    cd C:\Projects\MyApp

    {% endhighlight %}
    {% endtabs %}

2. Run `sf` to open the main menu.

    {% tabs %}
    {% highlight bash tabtitle="Bash" %}

    sf

    {% endhighlight %}
    {% endtabs %}

3. Under **License management**, select **Activate license**. The CLI focuses the **Activate License** entry and shows the navigation hint at the bottom of the screen.

    ![Activate license option in the Syncfusion .NET CLI](images/cli-activate-license.png)

4. If you are not signed in, the CLI opens your default browser to the Syncfusion<sup>®</sup> sign-in page. Complete sign in with your Syncfusion<sup>®</sup> account.

5. After sign in, the CLI checks your entitlements, downloads the matching keys for the Syncfusion<sup>®</sup> controls in the sample, and registers the keys in `App.xaml.cs`.

    ![License registered successfully in the Syncfusion .NET CLI](images/cli-license-registered.png)

6. Rebuild the application so the newly registered license is applied. The CLI prints the following reminder at the end of the activation output.

    > Note: Rebuild the application so the newly registered license is applied.

## Activate a license using a direct command

Run the activation command from the sample's project directory:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sf license activate

{% endhighlight %}
{% endtabs %}

Pass `--path` to point the CLI at a specific project directory or `.csproj` file:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sf license activate --path ./MyApp
sf license activate --path ./MyApp/MyApp.csproj

{% endhighlight %}
{% endtabs %}

Use `--yes` to accept the trial EULA prompt without asking:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sf license activate --yes

{% endhighlight %}
{% endtabs %}

## Activate a license from a key file

Use `--file` to activate from an existing key file. With no value, the CLI reads `./syncfusion-license.txt` from the project directory. With an absolute path, the CLI uses the specified file instead:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sf license activate --file
sf license activate --file C:\Keys\syncfusion-license.txt

{% endhighlight %}
{% endtabs %}

N> When a license key is supplied through `--file`, the CLI skips sign in and download and registers the keys already in the file. The file path must be absolute.

## View installed licenses

To see the licenses cached for the current project, run:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sf license view

{% endhighlight %}
{% endtabs %}

The command reads the cached metadata, lists each product, the license type, the status, and the expiry date, and warns when a Syncfusion<sup>®</sup> package in the project is not covered.

![View installed licenses in the Syncfusion .NET CLI](images/cli-view-installed-license-menu.png)

The cached output reports the registered email, platform, major version, and one row per product.

![Installed license details in the Syncfusion .NET CLI](images/cli-view-installed-license.png)

## Sign out of Syncfusion

To clear the local sign-in session, run:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sf logout

{% endhighlight %}
{% endtabs %}

Sign out does not remove any license registered in the project. To sign in again without running activation, use `sf login`.

## Managing account authentication during license activation

* If no sign-in session exists when you run `sf license activate`, the CLI opens the browser sign-in page automatically before the keys are downloaded. Complete sign in and the activation continues.
* If sign in is not desired during activation, use `sf login` beforehand to establish the session, or use `sf license activate --file` to register keys from an existing key file without contacting the license service.
* If a control in the project is not covered by a paid entitlement, the CLI prompts you to accept the Syncfusion<sup>®</sup> trial EULA and download a trial key for the missing packages. Pass `--yes` to accept the prompt automatically.
* When activation fails due to an expired session, run `sf login` again and re-run the activation command. Registered keys are refreshed without duplication.

## Register a license without activation

You can also register a license without writing values into generated sources by setting the `SYNCFUSION_LICENSE_KEY` environment variable in the application environment. When controls are selected, generated apps read this variable and register the license at startup. Refer to the [WinUI licensing overview](https://help.syncfusion.com/winui/licensing/overview) to generate a license key.

## License options

| Option | Description |
| --- | --- |
| `-p`, `--path` | The project directory or `.csproj`/`.vbproj` to scan for Syncfusion<sup>®</sup> packages. Defaults to the current directory |
| `-y`, `--yes` | Accept the trial EULA prompt automatically during activation |
| `--file` | Activate from an existing key file. With no value, the CLI reads `./syncfusion-license.txt` from the project directory. With an absolute path, the CLI uses the specified file |
| `--json` | Emit one JSON document instead of table output |

## FAQs

**Does the CLI register a license?**

Yes. `sf license activate` scans the project for Syncfusion<sup>®</sup> `PackageReference` entries, downloads the matching license keys from your Syncfusion<sup>®</sup> account, and inserts `SyncfusionLicenseProvider.RegisterLicense(...)` into `App.xaml.cs`. The CLI signs you in through the browser the first time, or you can sign in ahead with `sf login`.

**Where does the CLI register the license for WinUI?**

In `App.xaml.cs`, inside the `App` constructor before any other initialization.

**Can I use my own key file?**

Yes. Run `sf license activate --file C:\Keys\syncfusion-license.txt` with an absolute path. The CLI reads the keys from the file and registers them in the project's startup code without contacting the license service.

## See also

* [Create a WinUI 3 project](/winui/dotnet-cli/create-project)
* [Manage packages in an existing project](/winui/dotnet-cli/manage-packages)
* [Syncfusion<sup>®</sup> licensing overview](https://help.syncfusion.com/common/essential-studio/licensing/overview)
* [WinUI licensing overview](https://help.syncfusion.com/winui/licensing/overview)
