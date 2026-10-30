---
layout: post
title: Manage Syncfusion WinUI NuGet Packages using .NET CLI | Syncfusion®
description: Learn here about how to add, update, list, and search Syncfusion® WinUI NuGet packages in an existing project using the Syncfusion® .NET CLI (sfdotnet).
platform: winui
control: Syncfusion<sup>®</sup> .NET CLI
documentation: ug
---

# Manage packages in an existing project

Package operations change NuGet references in an existing project. Existing-project commands accept `-p/--path` with a `.csproj` file or the project directory, and `--json` emits one JSON document for script use. When the directory contains more than one project, pass the `.csproj` file explicitly.

N> On a project created by the CLI, adding or removing a control package also adds or removes the matching generated control sample and its navigation entry, tracked by the `Syncfusion/desktop.json` manifest. On any other project, only the NuGet reference changes.

## Add a package

You can add a package using the canonical package alias, or using the exact package identifier.

### Install a specific package by package name

Use the canonical package alias to add a package by its name:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sfdotnet add winui grid

{% endhighlight %}
{% endtabs %}

### Install a package using the exact package identifier

Use the canonical package ID to add a package by its exact identifier:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sfdotnet add winui Syncfusion.Grid.WinUI

{% endhighlight %}
{% endtabs %}

N> `<package>` accepts a canonical package alias, a canonical package ID, or an exact unambiguous package display name.

## Update a package

To update a package in an existing project, optionally with a specific version:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sfdotnet update winui chart --version 35.1.40

{% endhighlight %}
{% endtabs %}

## List available packages

To list all WinUI packages available on the package source:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sfdotnet list winui packages

{% endhighlight %}
{% endtabs %}

Add `--details` to show package descriptions, setup support, and verification evidence, or `--search <text>` to filter the list by alias, name, package ID, or description.

![List of available packages in the Syncfusion .NET CLI](images/cli-package-list.png)

## List installed packages

To list the Syncfusion<sup>®</sup> packages installed in an existing project:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sfdotnet list winui installed -p .\MyApp\MyApp.csproj

{% endhighlight %}
{% endtabs %}

## Search packages

To search the WinUI package catalog:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sfdotnet search winui chart
sfdotnet search chart --framework winui

{% endhighlight %}
{% endtabs %}

N> Existing-project package commands do not accept `--control`; pass the package alias or package ID instead. When a package ID supplies multiple control samples, use a control alias to select the sample.

## Package operation options

| Option | Description |
| --- | --- |
| `-p`, `--path` | The project directory or `.csproj` file |
| `-v`, `--version` | The Syncfusion<sup>®</sup> NuGet package version |
| `--build` | Build the changed project after the operation. Conflicts with `--no-build` |
| `--details` | Show package descriptions, setup support, and verification evidence (`list` and `search`) |
| `--search` | Filter listed packages by alias, name, package ID, or description (`list`) |
| `--source` | Package source; Syncfusion<sup>®</sup> packages require `https://api.nuget.org/v3/index.json` |
| `--configfile` | The NuGet configuration file to use |
| `--dry-run` | Preview the action without making changes |
| `--force` | Allow supported overwrites |
| `--no-restore` | Skip `dotnet restore` after the action. Restore and build (`--build`) requires restore, so remove `--no-restore` to build |
| `--no-interactive` | Disable interactive prompts |
| `--json` | Emit one JSON document |

## FAQs

**Why do DataGrid and TreeGrid share a package?**

Both controls are provided by `Syncfusion.Grid.WinUI`. Add the package with the package alias (`grid` or `Syncfusion.Grid.WinUI`), and create the matching sample with the control alias (`datagrid` or `treegrid`) in `sfdotnet new winui --control`.

## See also

* [Create a WinUI 3 project](/winui/dotnet-cli/create-project)
* [License activation](/winui/dotnet-cli/licensing)
* [Installing and deploying WinUI NuGet packages](https://help.syncfusion.com/winui/installation/install-nuget-packages)
