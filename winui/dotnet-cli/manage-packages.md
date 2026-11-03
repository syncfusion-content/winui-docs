---
layout: post
title: Manage Syncfusion WinUI NuGet Packages using .NET CLI | Syncfusion®
description: Learn here about how to add, update, list, and search Syncfusion® WinUI NuGet packages in an existing project using the Syncfusion® .NET CLI (sf).
platform: winui
control: Syncfusion<sup>®</sup> .NET CLI
documentation: ug
---

# Manage packages in an existing project

Package operations change NuGet references only. They do not generate control files. Existing-project commands accept `-p/--path` with a `.csproj` file, a project directory, or a supported subdirectory, and `--json` emits one JSON document for script use.

## Add a package

You can add a package using the canonical package alias, or using the exact package identifier.

### Install a specific package by package name

Use the canonical package alias to add a package by its name:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sf add winui grid

{% endhighlight %}
{% endtabs %}

### Install a package using the exact package identifier

Use the canonical package ID to add a package by its exact identifier:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sf add winui Syncfusion.Grid.WinUI

{% endhighlight %}
{% endtabs %}

N> `<package>` accepts a canonical package alias, a canonical package ID, or an exact unambiguous package display name.

## Update a package

To update a package in an existing project, optionally with a specific version:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sf update winui chart --version 35.1.40

{% endhighlight %}
{% endtabs %}

## List available packages

To list all WinUI packages available on the package source:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sf list winui packages

{% endhighlight %}
{% endtabs %}

![List of available packages in the Syncfusion .NET CLI](images/cli-package-list.png)

## List installed packages

To list the Syncfusion<sup>®</sup> packages installed in an existing project:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sf list winui installed -p .\MyApp\MyApp.csproj

{% endhighlight %}
{% endtabs %}

## Search packages

To search the WinUI package catalog:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sf search winui chart
sf search chart --framework winui

{% endhighlight %}
{% endtabs %}

N> WinUI projects retain package-only operations. Package operations never apply control registration based on package metadata.

## Package operation options

| Option | Description |
| --- | --- |
| `-p`, `--path` | The project directory, `.csproj` file, or a supported subdirectory |
| `-v`, `--version` | The Syncfusion<sup>®</sup> NuGet package version |
| `--source` | Package source; Syncfusion<sup>®</sup> packages require `https://api.nuget.org/v3/index.json` |
| `--configfile` | The NuGet configuration file to use |
| `--dry-run` | Preview the action without making changes |
| `--force` | Allow supported overwrites |
| `--no-restore` | Skip `dotnet restore` after the action |
| `--json` | Emit one JSON document |

## FAQs

**Why do DataGrid and TreeGrid share a package?**

Both controls are provided by `Syncfusion.Grid.WinUI`. Use the control alias (`datagrid` or `treegrid`) to add the matching package.

## See also

* [Create a WinUI 3 project](/winui/dotnet-cli/create-project)
* [License activation](/winui/dotnet-cli/licensing)
* [Installing and deploying WinUI NuGet packages](https://help.syncfusion.com/winui/installation/install-nuget-packages)
