---
title: nuget.exe CLI を使用して NuGet パッケージを管理する
description: nuget.exe CLI を使用して NuGet パッケージを操作する方法。
author: mikejo5000
ms.author: mikejo
ms.date: 06/03/2019
ms.topic: conceptual
ms.openlocfilehash: e60bca8fe2f80b044e466db2a100d6c6d167edb7
ms.sourcegitcommit: b6810860b77b2d50aab031040b047c20a333aca3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67427377"
---
# <a name="manage-packages-using-the-nugetexe-cli"></a><span data-ttu-id="c2a54-103">nuget.exe CLI を使用してパッケージを管理する</span><span class="sxs-lookup"><span data-stu-id="c2a54-103">Manage packages using the nuget.exe CLI</span></span>

<span data-ttu-id="c2a54-104">CLI ツールを使用すると、プロジェクトやソリューションで NuGet パッケージを簡単に更新し、復元できます。</span><span class="sxs-lookup"><span data-stu-id="c2a54-104">The CLI tool allows you to easily update and restore NuGet packages in projects and solutions.</span></span> <span data-ttu-id="c2a54-105">このツールからは、Windows のすべての NuGet 機能が提供され、Mono で実行される場合の Mac と Linux のほとんどの機能も提供されます。</span><span class="sxs-lookup"><span data-stu-id="c2a54-105">This tool provides all NuGet capabilities on Windows, and also provides most features on Mac and Linux when running under Mono.</span></span>

<span data-ttu-id="c2a54-106">nuget.exe CLI は、.NET Framework プロジェクトと非 SDK スタイルのプロジェクト (.NET Standard ライブラリを対象とするものなど) 用です。</span><span class="sxs-lookup"><span data-stu-id="c2a54-106">The nuget.exe CLI is for your .NET Framework project and non-SDK-style projects (for example, one that targets .NET Standard libraries).</span></span> <span data-ttu-id="c2a54-107">`PackageReference` に移行された非 SDK スタイルのプロジェクトを使用している場合、代わりに dotnet CLI を使用してください。</span><span class="sxs-lookup"><span data-stu-id="c2a54-107">If you are using a non-SDK-style project that has been migrated to `PackageReference`, use the dotnet CLI instead.</span></span> <span data-ttu-id="c2a54-108">NuGet CLI には、パッケージ参照のために [packages.config](../reference/packages-config.md) ファイルが必要になります。</span><span class="sxs-lookup"><span data-stu-id="c2a54-108">The NuGet CLI requires a [packages.config](../reference/packages-config.md) file for package references.</span></span>

> [!NOTE]
> <span data-ttu-id="c2a54-109">ほとんどのシナリオでは、PackageReference に `packages.config` を使用する [非 SDK スタイルのプロジェクトを移行する](../reference/migrate-packages-config-to-package-reference.md)ことをお勧めします。そうすることで、`nuget.exe` CLI の代わりに dotnet CLI を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c2a54-109">In most scenarios, we recommend [migrating non-SDK-style projects](../reference/migrate-packages-config-to-package-reference.md) that use `packages.config` to PackageReference, and then you can use the dotnet CLI instead of the `nuget.exe` CLI.</span></span> <span data-ttu-id="c2a54-110">C++ プロジェクトと ASP.NET プロジェクトについては、現在のところ、移行を利用できません。</span><span class="sxs-lookup"><span data-stu-id="c2a54-110">Migration is not currently available for C++ and ASP.NET projects.</span></span>

<span data-ttu-id="c2a54-111">この記事では、最も一般的ないくつかの nuget.exe CLI コマンドの基本的な使用方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="c2a54-111">This article shows you basic usage for a few of the most common nuget.exe CLI commands.</span></span> <span data-ttu-id="c2a54-112">これらのコマンドの多くでは、コマンドにプロジェクト ファイルが指定されていない限り、CLI ツールは現在のディレクトリでプロジェクト ファイルを探します。</span><span class="sxs-lookup"><span data-stu-id="c2a54-112">For most of these commands, the CLI tool looks for a project file in the current directory, unless a project file is specified in the command.</span></span> <span data-ttu-id="c2a54-113">コマンドと使用できる引数の完全一覧については、「[nuget.exe CLI reference](../tools/nuget-exe-cli-reference.md)」(nuget.exe CLI リファレンス) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2a54-113">For a complete list of commands and the arguments you may use, see the [nuget.exe CLI reference](../tools/nuget-exe-cli-reference.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c2a54-114">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c2a54-114">Prerequisites</span></span>

- <span data-ttu-id="c2a54-115">`nuget.exe` CLI をインストールします。[nuget.org](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe)からその `.exe`ファイルをダウンロードし、適切なフォルダーに保存して、そのフォルダーを PATH 環境変数に追加してください。</span><span class="sxs-lookup"><span data-stu-id="c2a54-115">Install the `nuget.exe` CLI by downloading it from [nuget.org](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe), saving that `.exe` file to a suitable folder, and adding that folder to your PATH environment variable.</span></span>

## <a name="install-a-package"></a><span data-ttu-id="c2a54-116">パッケージをインストールします</span><span class="sxs-lookup"><span data-stu-id="c2a54-116">Install a package</span></span>

<span data-ttu-id="c2a54-117">[install](../tools/cli-ref-install.md) コマンドでは、指定されたパッケージ ソースを利用し、パッケージがダウンロードされ、プロジェクトにインストールされます。既定では、現在のフォルダーにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="c2a54-117">The [install](../tools/cli-ref-install.md) command downloads and installs a package into a project, defaulting to the current folder, using specified package sources.</span></span> <span data-ttu-id="c2a54-118">プロジェクトのルート ディレクトリの *packages* フォルダーに新しいパッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="c2a54-118">Install new packages into the *packages* folder in your project root directory.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c2a54-119">`install` コマンドではプロジェクト ファイルや *packages.config* が変更されることはありません。そのため、パッケージがディスクに追加されるだけであり、プロジェクトの依存関係が変更されないという点で `restore` と似ています。</span><span class="sxs-lookup"><span data-stu-id="c2a54-119">The `install`command does not modify a project file or *packages.config*; in this way it's similar to `restore` in that it only adds packages to disk but does not change a project's dependencies.</span></span> <span data-ttu-id="c2a54-120">依存関係を追加するには、Visual Studio でパッケージ マネージャー UI かコンソールを利用してパッケージ復元を追加するか、*packages.config* を変更し、`install` か `restore` を実行します。</span><span class="sxs-lookup"><span data-stu-id="c2a54-120">To add a dependency, either add a package through the Package Manager UI or Console in Visual Studio, or modify *packages.config* and then run either `install` or `restore`.</span></span>

1. <span data-ttu-id="c2a54-121">コマンド ラインを開き、プロジェクト ファイルが含まれるディレクトリに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="c2a54-121">Open a command line and switch to the directory that contains your project file.</span></span>

2. <span data-ttu-id="c2a54-122">次のコマンドを使用し、NuGet パッケージを *packages* フォルダーにインストールします。</span><span class="sxs-lookup"><span data-stu-id="c2a54-122">Use the following command to install a NuGet package to the *packages* folder.</span></span>

    ```cli
    nuget install <packageID> -OutputDirectory packages
    ```

    <span data-ttu-id="c2a54-123">`Newtonsoft.json` パッケージを *packages* フォルダーにインストールするには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c2a54-123">To install the `Newtonsoft.json` package to the *packages* folder, use the following command:</span></span>

    ```cli
    nuget install Newtonsoft.Json -OutputDirectory packages
    ```

<span data-ttu-id="c2a54-124">あるいは、次のコマンドを使用すれば、既存の `packages.config` ファイルを使用する NuGet パッケージを *packages* フォルダーにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="c2a54-124">Alternatively, you can use the following command to install a NuGet package using an existing `packages.config` file to the *packages* folder.</span></span> <span data-ttu-id="c2a54-125">その場合、パッケージはプロジェクトの依存関係に追加されず、ローカルでインストールされます。</span><span class="sxs-lookup"><span data-stu-id="c2a54-125">This does not add the package to your project dependencies, but installs it locally.</span></span>

```cli
nuget install packages.config -OutputDirectory packages
```

## <a name="install-a-specific-version-of-a-package"></a><span data-ttu-id="c2a54-126">パッケージの特定のバージョンをインストールする</span><span class="sxs-lookup"><span data-stu-id="c2a54-126">Install a specific version of a package</span></span>

<span data-ttu-id="c2a54-127">[install](../tools/cli-ref-install.md) コマンドを使用するとき、バージョンが指定されていない場合、NuGet では最新版のパッケージがインストールされまする</span><span class="sxs-lookup"><span data-stu-id="c2a54-127">If the version is not specified when you use the [install](../tools/cli-ref-install.md) command, NuGet installs the latest version of the package.</span></span> <span data-ttu-id="c2a54-128">特定のバージョンの NuGet パッケージをインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c2a54-128">You can also install a specific version of a Nuget package:</span></span>

```cli
nuget install <packageID | configFilePath> -Version <version>
```

<span data-ttu-id="c2a54-129">たとえば、`Newtonsoft.json` パッケージのバージョン 12.0.1 を追加するには、このコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c2a54-129">For example, to add version 12.0.1 of the `Newtonsoft.json` package, use this command:</span></span>

```cli
nuget install Newtonsoft.Json -Version 12.0.1
```

<span data-ttu-id="c2a54-130">`install` の制限や動作については、「[Install a package](#install-a-package)」(パッケージのインストール) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2a54-130">For more information on the limitations and behavior of `install`, see [Install a package](#install-a-package).</span></span>

## <a name="remove-a-package"></a><span data-ttu-id="c2a54-131">パッケージを削除する</span><span class="sxs-lookup"><span data-stu-id="c2a54-131">Remove a package</span></span>

<span data-ttu-id="c2a54-132">1 つまたは複数のパッケージを削除するには、削除するパッケージを *packages* フォルダーから削除します。</span><span class="sxs-lookup"><span data-stu-id="c2a54-132">To delete one or more packages, delete the packages you want to remove from the *packages* folder.</span></span>

<span data-ttu-id="c2a54-133">パッケージを再インストールする場合、`restore` または `install` コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c2a54-133">If you want to reinstall packages, use the `restore` or `install` command.</span></span>

## <a name="list-packages"></a><span data-ttu-id="c2a54-134">パッケージを一覧表示する</span><span class="sxs-lookup"><span data-stu-id="c2a54-134">List packages</span></span>

<span data-ttu-id="c2a54-135">[list](../tools/cli-ref-list.md) コマンドを使用し、特定のソースからパッケージの一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="c2a54-135">You can display a list of packages from a given source using the [list](../tools/cli-ref-list.md) command.</span></span> <span data-ttu-id="c2a54-136">`-Source` オプションを使用し、検索を制限します。</span><span class="sxs-lookup"><span data-stu-id="c2a54-136">Use the `-Source` option to restrict the search.</span></span>

```cli
nuget list -Source <source>
```

<span data-ttu-id="c2a54-137">たとえば、*packages* フォルダーのパッケージを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="c2a54-137">For example, list packages in the *packages* folder.</span></span>

```cli
nuget list -Source C:\Users\username\source\repos\MyProject\packages
```

<span data-ttu-id="c2a54-138">検索語句を使用する場合、検索には、パッケージの名前、タグ、パッケージの説明が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c2a54-138">If you use a search term, the search includes names of packages, tags, and package descriptions.</span></span>

```cli
nuget list <search term>
```

## <a name="update-an-individual-package"></a><span data-ttu-id="c2a54-139">個別パッケージを更新する</span><span class="sxs-lookup"><span data-stu-id="c2a54-139">Update an individual package</span></span>

<span data-ttu-id="c2a54-140">NuGet では、パッケージ バージョンを指定しない限り、`install` コマンドを使用すると、最新版のパッケージがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="c2a54-140">NuGet installs the latest version of the package when you use the `install` command unless you specify the package version.</span></span>

## <a name="update-all-packages"></a><span data-ttu-id="c2a54-141">すべてのパッケージを更新する</span><span class="sxs-lookup"><span data-stu-id="c2a54-141">Update all packages</span></span>

<span data-ttu-id="c2a54-142">すべてのパッケージを更新するには、[update](../tools/cli-ref-update.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c2a54-142">Use the [update](../tools/cli-ref-update.md) command to update all packages.</span></span> <span data-ttu-id="c2a54-143">利用できる最も新しいバージョンに (`packages.config` を使用する) プロジェクトのすべてのパッケージを更新します。</span><span class="sxs-lookup"><span data-stu-id="c2a54-143">Updates all packages in a project (using `packages.config`) to their latest available versions.</span></span> <span data-ttu-id="c2a54-144">`restore` は `update` を実行する前に実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c2a54-144">It is recommended to run `restore` before running `update`.</span></span>

```cli
nuget update
```

## <a name="restore-packages"></a><span data-ttu-id="c2a54-145">パッケージの復元</span><span class="sxs-lookup"><span data-stu-id="c2a54-145">Restore packages</span></span>

<span data-ttu-id="c2a54-146">[restore](../tools/cli-ref-restore.md) コマンドを使用すると、*packages* フォルダーにないすべてのパッケージがダウンロードされ、インストールされます。</span><span class="sxs-lookup"><span data-stu-id="c2a54-146">Use the [restore](../tools/cli-ref-restore.md) command, which downloads and installs any packages missing from the *packages* folder.</span></span>

<span data-ttu-id="c2a54-147">`restore` ではパッケージがディスクに追加されるだけで、プロジェクトの依存関係は変更されません。</span><span class="sxs-lookup"><span data-stu-id="c2a54-147">`restore` only adds packages to disk but does not change a project's dependencies.</span></span> <span data-ttu-id="c2a54-148">プロジェクトの依存関係を復元するには、`packages.config` を変更し、`restore` コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c2a54-148">To restore project dependencies, modify `packages.config`, then use the `restore` command.</span></span>

<span data-ttu-id="c2a54-149">`restore` を使用してパッケージを復元するには:</span><span class="sxs-lookup"><span data-stu-id="c2a54-149">To restore a package using `restore`:</span></span>

```cli
nuget restore MySolution.sln
```