---
title: "NuGet.Config ファイル参照 | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/25/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
description: "config、bindingRedirects、packageRestore、solution、packageSource の各セクションを含む NuGet.Config ファイル参照。"
keywords: "NuGet.Config ファイル、NuGet 構成参照、NuGet 構成オプション"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: df602cb561a19f0eac085695de80db1fbaa1a313
ms.sourcegitcommit: 33436d122873249dbb20616556cd8c6783f38909
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="nugetconfig-reference"></a><span data-ttu-id="cdbba-104">NuGet.Config 参照</span><span class="sxs-lookup"><span data-stu-id="cdbba-104">NuGet.Config reference</span></span>

<span data-ttu-id="cdbba-105">NuGet の動作は、「[Configuring NuGet Behavior](../consume-packages/configuring-nuget-behavior.md)」(NuGet 動作の構成) に記載の各種 `NuGet.Config` ファイルでの設定によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-105">NuGet behavior is controlled by settings in different `NuGet.Config` files as described in [Configuring NuGet Behavior](../consume-packages/configuring-nuget-behavior.md).</span></span>

<span data-ttu-id="cdbba-106">`NuGet.Config` は、最上位の `<configuration>` ノードを含む XML ファイルであり、このトピックで説明するセクション要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-106">`NuGet.Config` is an XML file containing a top-level `<configuration>` node, which then contains the section elements described in this topic.</span></span> <span data-ttu-id="cdbba-107">各セクションには、`key` 属性および `value` 属性を持つ 0 個以上の `<add>` 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="cdbba-107">Each section contains zero or more `<add>` elements with `key` and `value` attributes.</span></span> <span data-ttu-id="cdbba-108">「[examples config file](#example-config-file)」 (構成ファイルの例) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdbba-108">See the [examples config file](#example-config-file).</span></span> <span data-ttu-id="cdbba-109">名前の設定には大文字と小文字の区別があり、値には[環境変数](#using-environment-variables)を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-109">Setting names are case-insensitive, and values can use [environment variables](#using-environment-variables).</span></span>

<span data-ttu-id="cdbba-110">このトピックの内容:</span><span class="sxs-lookup"><span data-stu-id="cdbba-110">In this topic:</span></span>

- [<span data-ttu-id="cdbba-111">config セクション</span><span class="sxs-lookup"><span data-stu-id="cdbba-111">config section</span></span>](#config-section)
- [<span data-ttu-id="cdbba-112">bindingRedirects セクション</span><span class="sxs-lookup"><span data-stu-id="cdbba-112">bindingRedirects section</span></span>](#bindingredirects-section)
- [<span data-ttu-id="cdbba-113">packageRestore セクション</span><span class="sxs-lookup"><span data-stu-id="cdbba-113">packageRestore section</span></span>](#packagerestore-section)
- [<span data-ttu-id="cdbba-114">solution セクション</span><span class="sxs-lookup"><span data-stu-id="cdbba-114">solution section</span></span>](#solution-section)
- <span data-ttu-id="cdbba-115">[パッケージ ソース セクション](#package-source-sections):</span><span class="sxs-lookup"><span data-stu-id="cdbba-115">[Package source sections](#package-source-sections):</span></span>
  - [<span data-ttu-id="cdbba-116">packageSources</span><span class="sxs-lookup"><span data-stu-id="cdbba-116">packageSources</span></span>](#packagesources)
  - [<span data-ttu-id="cdbba-117">packageSourceCredentials</span><span class="sxs-lookup"><span data-stu-id="cdbba-117">packageSourceCredentials</span></span>](#packagesourcecredentials)
  - [<span data-ttu-id="cdbba-118">apikeys</span><span class="sxs-lookup"><span data-stu-id="cdbba-118">apikeys</span></span>](#apikeys)
  - [<span data-ttu-id="cdbba-119">disabledPackageSources</span><span class="sxs-lookup"><span data-stu-id="cdbba-119">disabledPackageSources</span></span>](#disabledpackagesources)
  - [<span data-ttu-id="cdbba-120">activePackageSource</span><span class="sxs-lookup"><span data-stu-id="cdbba-120">activePackageSource</span></span>](#activepackagesource)
- [<span data-ttu-id="cdbba-121">環境変数の使用</span><span class="sxs-lookup"><span data-stu-id="cdbba-121">Using environment variables</span></span>](#using-environment-variables)
- [<span data-ttu-id="cdbba-122">構成ファイルの例</span><span class="sxs-lookup"><span data-stu-id="cdbba-122">Example config file</span></span>](#example-config-file)

<a name="dependencyVersion"></a>
<a name="globalPackagesFolder"></a>
<a name="repositoryPath"></a>
<a name="proxy-settings"></a>

## <a name="config-section"></a><span data-ttu-id="cdbba-123">config セクション</span><span class="sxs-lookup"><span data-stu-id="cdbba-123">config section</span></span>

<span data-ttu-id="cdbba-124">[`nuget config` コマンド](../tools/cli-ref-config.md)を使用して設定できる、さまざまな構成設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-124">Contains miscellaneous configuration settings, which can be set using the [`nuget config` command](../tools/cli-ref-config.md).</span></span>

<span data-ttu-id="cdbba-125">注: `dependencyVersion` と `repositoryPath` については、`packages.config` を使用するプロジェクトのみに適用されます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-125">Note: `dependencyVersion` and `repositoryPath` apply only to projects using `packages.config`.</span></span> <span data-ttu-id="cdbba-126">`globalPackagesFolder` PackageReference 形式を使用してプロジェクトにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-126">`globalPackagesFolder` applies only to projects using the PackageReference format.</span></span>

| <span data-ttu-id="cdbba-127">キー</span><span class="sxs-lookup"><span data-stu-id="cdbba-127">Key</span></span> | <span data-ttu-id="cdbba-128">[値]</span><span class="sxs-lookup"><span data-stu-id="cdbba-128">Value</span></span> |
| --- | --- |
| <span data-ttu-id="cdbba-129">dependencyVersion (`packages.config` のみ)</span><span class="sxs-lookup"><span data-stu-id="cdbba-129">dependencyVersion (`packages.config` only)</span></span> | <span data-ttu-id="cdbba-130">`-DependencyVersion` スイッチが直接指定されない場合の、パッケージのインストール、復元、および更新における既定の `DependencyVersion` 値です。</span><span class="sxs-lookup"><span data-stu-id="cdbba-130">The default `DependencyVersion` value for package install, restore, and update, when the `-DependencyVersion` switch is not specified directly.</span></span> <span data-ttu-id="cdbba-131">この値は、NuGet パッケージ マネージャー UI でも使用されます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-131">This value is also used by the NuGet Package Manager UI.</span></span> <span data-ttu-id="cdbba-132">値は `Lowest`、`HighestPatch`、`HighestMinor`、`Highest` となります。</span><span class="sxs-lookup"><span data-stu-id="cdbba-132">Values are `Lowest`, `HighestPatch`, `HighestMinor`, `Highest`.</span></span> |
| <span data-ttu-id="cdbba-133">globalPackagesFolder (`packages.config` を使用しないプロジェクト)</span><span class="sxs-lookup"><span data-stu-id="cdbba-133">globalPackagesFolder (projects not using `packages.config`)</span></span> | <span data-ttu-id="cdbba-134">既定のグローバル パッケージ フォルダーの場所です。</span><span class="sxs-lookup"><span data-stu-id="cdbba-134">The location of the default global packages folder.</span></span> <span data-ttu-id="cdbba-135">既定値は、`%USERPROFILE%\.nuget\packages` (Windows) または `~/.nuget/packages` (Mac/Linux) です。</span><span class="sxs-lookup"><span data-stu-id="cdbba-135">The default is `%USERPROFILE%\.nuget\packages` (Windows) or `~/.nuget/packages` (Mac/Linux).</span></span> <span data-ttu-id="cdbba-136">相対パスは、プロジェクト固有の `Nuget.Config` ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-136">A relative path can be used in project-specific `Nuget.Config` files.</span></span> |
| <span data-ttu-id="cdbba-137">repositoryPath (`packages.config` のみ)</span><span class="sxs-lookup"><span data-stu-id="cdbba-137">repositoryPath (`packages.config` only)</span></span> | <span data-ttu-id="cdbba-138">既定の `$(Solutiondir)/packages` フォルダーではなく、NuGet パッケージをインストールする場所です。</span><span class="sxs-lookup"><span data-stu-id="cdbba-138">The location in which to install NuGet packages instead of the default `$(Solutiondir)/packages` folder.</span></span> <span data-ttu-id="cdbba-139">相対パスは、プロジェクト固有の `Nuget.Config` ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-139">A relative path can be used in project-specific `Nuget.Config` files.</span></span> |
| <span data-ttu-id="cdbba-140">defaultPushSource</span><span class="sxs-lookup"><span data-stu-id="cdbba-140">defaultPushSource</span></span> | <span data-ttu-id="cdbba-141">操作に対してパッケージ ソースが他に見つからない場合に、既定値として使用すべきパッケージ ソースの URL またはパスを識別します。</span><span class="sxs-lookup"><span data-stu-id="cdbba-141">Identifies the URL or path of the package source that should be used as the default if no other package sources are found for an operation.</span></span> |
| <span data-ttu-id="cdbba-142">http_proxy http_proxy.user http_proxy.password no_proxy</span><span class="sxs-lookup"><span data-stu-id="cdbba-142">http_proxy http_proxy.user http_proxy.password no_proxy</span></span> | <span data-ttu-id="cdbba-143">パッケージ ソースに接続するときに使用するプロキシ設定です。`http_proxy` の形式は `http://<username>:<password>@<domain>` とする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cdbba-143">Proxy settings to use when connecting to package sources; `http_proxy` should be in the format `http://<username>:<password>@<domain>`.</span></span> <span data-ttu-id="cdbba-144">パスワードは暗号化され、手動で追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="cdbba-144">Passwords are encrypted and cannot be added manually.</span></span> <span data-ttu-id="cdbba-145">`no_proxy` の場合、値はドメイン、バイパス、プロキシ サーバーのコンマ区切りのリストとなります。</span><span class="sxs-lookup"><span data-stu-id="cdbba-145">For `no_proxy`, the value is a comma-separated list of domains the bypass the proxy server.</span></span> <span data-ttu-id="cdbba-146">これらの値に対して http_proxy および no_proxy の環境変数を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-146">You can alternately use the http_proxy and no_proxy environment variables for those values.</span></span> <span data-ttu-id="cdbba-147">詳細については、「[NuGet proxy settings](http://skolima.blogspot.com/2012/07/nuget-proxy-settings.html)」 (NuGet プロキシ設定) (skolima.blogspot.com) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdbba-147">For additional details, see [NuGet proxy settings](http://skolima.blogspot.com/2012/07/nuget-proxy-settings.html) (skolima.blogspot.com).</span></span> |

<span data-ttu-id="cdbba-148">**例**:</span><span class="sxs-lookup"><span data-stu-id="cdbba-148">**Example**:</span></span>

```xml
<config>
    <add key="dependencyVersion" value="Highest" />
    <add key="globalPackagesFolder" value="c:\packages" />
    <add key="repositoryPath" value="c:\repo" />
    <add key="http_proxy" value="http://company-squid:3128@contoso.com" />
</config>
```

## <a name="bindingredirects-section"></a><span data-ttu-id="cdbba-149">bindingRedirects セクション</span><span class="sxs-lookup"><span data-stu-id="cdbba-149">bindingRedirects section</span></span>

<span data-ttu-id="cdbba-150">パッケージのインストール時に、NuGet で自動バインド リダイレクトを実行するかどうかを構成します。</span><span class="sxs-lookup"><span data-stu-id="cdbba-150">Configures whether NuGet does automatic binding redirects when a package is installed.</span></span>

| <span data-ttu-id="cdbba-151">キー</span><span class="sxs-lookup"><span data-stu-id="cdbba-151">Key</span></span> | <span data-ttu-id="cdbba-152">[値]</span><span class="sxs-lookup"><span data-stu-id="cdbba-152">Value</span></span> |
| --- | --- |
| <span data-ttu-id="cdbba-153">スキップ</span><span class="sxs-lookup"><span data-stu-id="cdbba-153">skip</span></span> | <span data-ttu-id="cdbba-154">自動バインド リダイレクトを省略するかどうかを示すブール値です。</span><span class="sxs-lookup"><span data-stu-id="cdbba-154">A Boolean indicating whether to skip automatic binding redirects.</span></span> <span data-ttu-id="cdbba-155">既定値は false です。</span><span class="sxs-lookup"><span data-stu-id="cdbba-155">The default is false.</span></span> |

<span data-ttu-id="cdbba-156">**例**:</span><span class="sxs-lookup"><span data-stu-id="cdbba-156">**Example**:</span></span>

```xml
<bindingRedirects>
    <add key="skip" value="True" />
</bindingRedirects>
```

## <a name="packagerestore-section"></a><span data-ttu-id="cdbba-157">packageRestore セクション</span><span class="sxs-lookup"><span data-stu-id="cdbba-157">packageRestore section</span></span>

<span data-ttu-id="cdbba-158">*2.7 以降では無視されます*</span><span class="sxs-lookup"><span data-stu-id="cdbba-158">*Ignored in 2.7+*</span></span>

<span data-ttu-id="cdbba-159">ビルド時のパッケージの復元を制御します。</span><span class="sxs-lookup"><span data-stu-id="cdbba-159">Controls package restore during builds.</span></span>

| <span data-ttu-id="cdbba-160">キー</span><span class="sxs-lookup"><span data-stu-id="cdbba-160">Key</span></span> | <span data-ttu-id="cdbba-161">[値]</span><span class="sxs-lookup"><span data-stu-id="cdbba-161">Value</span></span> |
| --- | --- |
| <span data-ttu-id="cdbba-162">enabled</span><span class="sxs-lookup"><span data-stu-id="cdbba-162">enabled</span></span> | <span data-ttu-id="cdbba-163">NuGet で自動復元を実行できるかどうかを示すブール値です。</span><span class="sxs-lookup"><span data-stu-id="cdbba-163">A Boolean indicating whether NuGet can perform automatic restore.</span></span> <span data-ttu-id="cdbba-164">構成ファイル内にこのキーを設定するのでなく、`True` の値で `EnableNuGetPackageRestore` 環境変数を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-164">You can also set the `EnableNuGetPackageRestore` environment variable with a value of `True` instead of setting this key in the config file.</span></span> |
| <span data-ttu-id="cdbba-165">自動</span><span class="sxs-lookup"><span data-stu-id="cdbba-165">automatic</span></span> | <span data-ttu-id="cdbba-166">ビルド中に欠落しているパッケージの確認を NuGet で行う必要があるかどうかを示すブール値です。</span><span class="sxs-lookup"><span data-stu-id="cdbba-166">A Boolean indicating whether NuGet should check for missing packages during a build.</span></span> |

<span data-ttu-id="cdbba-167">**例**:</span><span class="sxs-lookup"><span data-stu-id="cdbba-167">**Example**:</span></span>

```xml
<packageRestore>
    <add key="enabled" value="true" />
    <add key="automatic" value="true" />
</packageRestore>
```

## <a name="solution-section"></a><span data-ttu-id="cdbba-168">ソリューション セクション</span><span class="sxs-lookup"><span data-stu-id="cdbba-168">solution section</span></span>

<span data-ttu-id="cdbba-169">ソリューションの `packages` フォルダーをソース管理に含めるかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="cdbba-169">Controls whether the `packages` folder of a solution is included in source control.</span></span> <span data-ttu-id="cdbba-170">このセクションは、ソリューション フォルダー内の `Nuget.Config` ファイルでのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="cdbba-170">This section works only in `Nuget.Config` files in a solution folder.</span></span>

| <span data-ttu-id="cdbba-171">キー</span><span class="sxs-lookup"><span data-stu-id="cdbba-171">Key</span></span> | <span data-ttu-id="cdbba-172">[値]</span><span class="sxs-lookup"><span data-stu-id="cdbba-172">Value</span></span> |
| --- | --- |
| <span data-ttu-id="cdbba-173">disableSourceControlIntegration</span><span class="sxs-lookup"><span data-stu-id="cdbba-173">disableSourceControlIntegration</span></span> | <span data-ttu-id="cdbba-174">ソース管理を使用する場合に、パッケージ フォルダーを無視するかどうかを示すブール値です。</span><span class="sxs-lookup"><span data-stu-id="cdbba-174">A Boolean indicating whether to ignore the packages folder when working with source control.</span></span> <span data-ttu-id="cdbba-175">既定値は false です。</span><span class="sxs-lookup"><span data-stu-id="cdbba-175">The default value is false.</span></span> |

<span data-ttu-id="cdbba-176">**例**:</span><span class="sxs-lookup"><span data-stu-id="cdbba-176">**Example**:</span></span>

```xml
<solution>
    <add key="disableSourceControlIntegration" value="true" />
</solution>
```

## <a name="package-source-sections"></a><span data-ttu-id="cdbba-177">パッケージ ソース セクション</span><span class="sxs-lookup"><span data-stu-id="cdbba-177">Package source sections</span></span>

<span data-ttu-id="cdbba-178">`packageSources`、`packageSourceCredentials`、`apikeys`、`activePackageSource`、および `disabledPackageSources` のすべての連携によって、インストール、復元、および更新の操作中にパッケージ リポジトリを NuGet で操作する方法が構成されます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-178">The `packageSources`, `packageSourceCredentials`, `apikeys`, `activePackageSource`, and `disabledPackageSources` all work together to configure how NuGet works with package repositories during install, restore, and update operations.</span></span>

<span data-ttu-id="cdbba-179">これらの設定を管理するために、通常は、[`nuget sources` コマンド](../tools/cli-ref-sources.md)が使用されます。ただし、`apikeys` の場合は例外であり、[`nuget setapikey` コマンド](../tools/cli-ref-setapikey.md)によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-179">The [`nuget sources` command](../tools/cli-ref-sources.md) is generally used to manage these settings, except for `apikeys` which is managed using the [`nuget setapikey` command](../tools/cli-ref-setapikey.md).</span></span>

<span data-ttu-id="cdbba-180">ここで、nuget.org のソース URL は `https://api.nuget.org/v3/index.json` となります。</span><span class="sxs-lookup"><span data-stu-id="cdbba-180">Note that the source URL for nuget.org is `https://api.nuget.org/v3/index.json`.</span></span>

### <a name="packagesources"></a><span data-ttu-id="cdbba-181">packageSources</span><span class="sxs-lookup"><span data-stu-id="cdbba-181">packageSources</span></span>

<span data-ttu-id="cdbba-182">すべての既知のパッケージ ソースの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="cdbba-182">Lists all known package sources.</span></span> <span data-ttu-id="cdbba-183">復元操作中に、PackageReference 形式を使用して、プロジェクトを使用して、順序は無視されます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-183">The order is ignored during restore operations and with any project using the PackageReference format.</span></span> <span data-ttu-id="cdbba-184">NuGet は、インストールのソースの順序を尊重いたします操作や更新操作を使用して、プロジェクトで`packages.config`です。</span><span class="sxs-lookup"><span data-stu-id="cdbba-184">NuGet respects the order of sources for install and update operations with projects using `packages.config`.</span></span>

| <span data-ttu-id="cdbba-185">キー</span><span class="sxs-lookup"><span data-stu-id="cdbba-185">Key</span></span> | <span data-ttu-id="cdbba-186">[値]</span><span class="sxs-lookup"><span data-stu-id="cdbba-186">Value</span></span> |
| --- | --- |
| <span data-ttu-id="cdbba-187">(パッケージ ソースに割り当てる名前)</span><span class="sxs-lookup"><span data-stu-id="cdbba-187">(name to assign to the package source)</span></span> | <span data-ttu-id="cdbba-188">パッケージ ソースのパスまたは URL です。</span><span class="sxs-lookup"><span data-stu-id="cdbba-188">The path or URL of the package source.</span></span> |

<span data-ttu-id="cdbba-189">**例**:</span><span class="sxs-lookup"><span data-stu-id="cdbba-189">**Example**:</span></span>

```xml
<packageSources>
    <add key="nuget.org" value="https://api.nuget.org/v3/index.json" protocolVersion="3" />
    <add key="Contoso" value="https://contoso.com/packages/" />
    <add key="Test Source" value="c:\packages" />
</packageSources>
```

### <a name="packagesourcecredentials"></a><span data-ttu-id="cdbba-190">packageSourceCredentials</span><span class="sxs-lookup"><span data-stu-id="cdbba-190">packageSourceCredentials</span></span>

<span data-ttu-id="cdbba-191">通常、`-username` スイッチおよび `-password` スイッチと `nuget sources` によって指定される、ソースのユーザー名とパスワードを格納します。</span><span class="sxs-lookup"><span data-stu-id="cdbba-191">Stores usernames and passwords for sources, typically specified with the `-username` and `-password` switches with `nuget sources`.</span></span> <span data-ttu-id="cdbba-192">`-storepasswordincleartext` オプションが使用されていない場合、既定ではパスワードが暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-192">Passwords are encrypted by default unless the `-storepasswordincleartext` option is also used.</span></span>

| <span data-ttu-id="cdbba-193">キー</span><span class="sxs-lookup"><span data-stu-id="cdbba-193">Key</span></span> | <span data-ttu-id="cdbba-194">[値]</span><span class="sxs-lookup"><span data-stu-id="cdbba-194">Value</span></span> |
| --- | --- |
| <span data-ttu-id="cdbba-195">username</span><span class="sxs-lookup"><span data-stu-id="cdbba-195">username</span></span> | <span data-ttu-id="cdbba-196">プレーン テキストで表されるソースのユーザー名です。</span><span class="sxs-lookup"><span data-stu-id="cdbba-196">The user name for the source in plain text.</span></span> |
| <span data-ttu-id="cdbba-197">パスワード</span><span class="sxs-lookup"><span data-stu-id="cdbba-197">password</span></span> | <span data-ttu-id="cdbba-198">ソースの暗号されたパスワードです。</span><span class="sxs-lookup"><span data-stu-id="cdbba-198">The encrypted password for the source.</span></span> |
| <span data-ttu-id="cdbba-199">cleartextpassword</span><span class="sxs-lookup"><span data-stu-id="cdbba-199">cleartextpassword</span></span> | <span data-ttu-id="cdbba-200">ソースの暗号化されていないパスワードです。</span><span class="sxs-lookup"><span data-stu-id="cdbba-200">The unencrypted password for the source.</span></span> |

<span data-ttu-id="cdbba-201">**例:**</span><span class="sxs-lookup"><span data-stu-id="cdbba-201">**Example:**</span></span>

<span data-ttu-id="cdbba-202">構成ファイル内の `<packageSourceCredentials>` 要素には、適用可能なソース名ごとに子ノードが含まれます (名前内のスペースは `_x0020+` と置換されます)。</span><span class="sxs-lookup"><span data-stu-id="cdbba-202">In the config file, the `<packageSourceCredentials>` element contains child nodes for each applicable source name (spaces in the name are replaced with `_x0020+`).</span></span> <span data-ttu-id="cdbba-203">つまり、"Contoso" および "Test Source" という名前のソースの場合は、暗号化されたパスワードを使用するとき、構成ファイルには次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-203">That is, for sources named "Contoso" and "Test Source", the config file contains the following when using encrypted passwords:</span></span>

```xml
<packageSourceCredentials>
    <Contoso>
        <add key="Username" value="user@contoso.com" />
        <add key="Password" value="..." />
    </Contoso>
    <Test_x0020_Source>
        <add key="Username" value="user" />
        <add key="Password" value="..." />
    </Test_x0020_Source>
</packageSourceCredentials>
```

<span data-ttu-id="cdbba-204">暗号化されていないパスワードを使用する場合:</span><span class="sxs-lookup"><span data-stu-id="cdbba-204">When using unencrypted passwords:</span></span>

```xml
<packageSourceCredentials>
    <Contoso>
        <add key="Username" value="user@contoso.com" />
        <add key="ClearTextPassword" value="33f!!lloppa" />
    </Contoso>
    <Test_x0020_Source>
        <add key="Username" value="user" />
        <add key="ClearTextPassword" value="hal+9ooo_da!sY" />
    </Test_x0020_Source>
</packageSourceCredentials>
```

### <a name="apikeys"></a><span data-ttu-id="cdbba-205">apikeys</span><span class="sxs-lookup"><span data-stu-id="cdbba-205">apikeys</span></span>

<span data-ttu-id="cdbba-206">[`nuget setapikey` コマンド](../tools/cli-ref-setapikey.md)で設定される、API キー認証を使用するソースのキーを格納します。</span><span class="sxs-lookup"><span data-stu-id="cdbba-206">Stores keys for sources that use API key authentication, as set with the [`nuget setapikey` command](../tools/cli-ref-setapikey.md).</span></span>

| <span data-ttu-id="cdbba-207">キー</span><span class="sxs-lookup"><span data-stu-id="cdbba-207">Key</span></span> | <span data-ttu-id="cdbba-208">[値]</span><span class="sxs-lookup"><span data-stu-id="cdbba-208">Value</span></span> |
| --- | --- |
| <span data-ttu-id="cdbba-209">(ソース URL)</span><span class="sxs-lookup"><span data-stu-id="cdbba-209">(source URL)</span></span> | <span data-ttu-id="cdbba-210">暗号化された API キー。</span><span class="sxs-lookup"><span data-stu-id="cdbba-210">The encrypted API key.</span></span> |

<span data-ttu-id="cdbba-211">**例**:</span><span class="sxs-lookup"><span data-stu-id="cdbba-211">**Example**:</span></span>

```xml
<apikeys>
    <add key="https://MyRepo/ES/api/v2/package" value="encrypted_api_key" />
</apikeys>
```

### <a name="disabledpackagesources"></a><span data-ttu-id="cdbba-212">disabledPackageSources</span><span class="sxs-lookup"><span data-stu-id="cdbba-212">disabledPackageSources</span></span>

<span data-ttu-id="cdbba-213">現在無効になっているソースを識別します。</span><span class="sxs-lookup"><span data-stu-id="cdbba-213">Identified currently disabled sources.</span></span> <span data-ttu-id="cdbba-214">空の場合もあります。</span><span class="sxs-lookup"><span data-stu-id="cdbba-214">May be empty.</span></span>

| <span data-ttu-id="cdbba-215">キー</span><span class="sxs-lookup"><span data-stu-id="cdbba-215">Key</span></span> | <span data-ttu-id="cdbba-216">[値]</span><span class="sxs-lookup"><span data-stu-id="cdbba-216">Value</span></span> |
| --- | --- |
| <span data-ttu-id="cdbba-217">(ソースの名前)</span><span class="sxs-lookup"><span data-stu-id="cdbba-217">(name of source)</span></span> | <span data-ttu-id="cdbba-218">ソースが無効になっているかどうかを示すブール値です。</span><span class="sxs-lookup"><span data-stu-id="cdbba-218">A Boolean indicating whether the source is disabled.</span></span> |

<span data-ttu-id="cdbba-219">**例:**</span><span class="sxs-lookup"><span data-stu-id="cdbba-219">**Example:**</span></span>

```xml
<disabledPackageSources>
    <add key="Contoso" value="true" />
</disabledPackageSources>

<!-- Empty list -->
<disabledPackageSources />
```

### <a name="activepackagesource"></a><span data-ttu-id="cdbba-220">activePackageSource</span><span class="sxs-lookup"><span data-stu-id="cdbba-220">activePackageSource</span></span>

<span data-ttu-id="cdbba-221">*(2.x のみ。3.x 以降では使用されていない)*</span><span class="sxs-lookup"><span data-stu-id="cdbba-221">*(2.x only; deprecated in 3.x+)*</span></span>

<span data-ttu-id="cdbba-222">現在アクティブなソースを識別し、すべてのソースの集計を示します。</span><span class="sxs-lookup"><span data-stu-id="cdbba-222">Identifies to the currently active source or indicates the aggregate of all sources.</span></span>

| <span data-ttu-id="cdbba-223">キー</span><span class="sxs-lookup"><span data-stu-id="cdbba-223">Key</span></span> | <span data-ttu-id="cdbba-224">[値]</span><span class="sxs-lookup"><span data-stu-id="cdbba-224">Value</span></span> |
| --- | --- |
| <span data-ttu-id="cdbba-225">(ソースの名前) または `All`</span><span class="sxs-lookup"><span data-stu-id="cdbba-225">(name of source) or `All`</span></span> | <span data-ttu-id="cdbba-226">キーがソースの名前である場合は、ソースのパスまたは URL が値となります。</span><span class="sxs-lookup"><span data-stu-id="cdbba-226">If key is the name of a source, the value is the source path or URL.</span></span> <span data-ttu-id="cdbba-227">`All` の場合は、値を `(Aggregate source)` にして、無効になっていないすべてのパッケージ ソースを結合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cdbba-227">If `All`, value should be `(Aggregate source)` to combine all package sources that are not otherwise disabled.</span></span> |

<span data-ttu-id="cdbba-228">**例**:</span><span class="sxs-lookup"><span data-stu-id="cdbba-228">**Example**:</span></span>

```xml
<activePackageSource>
    <!-- Only one active source-->
    <add key="nuget.org" value="https://api.nuget.org/v3/index.json" />

    <!-- All non-disabled sources are active -->
    <add key="All" value="(Aggregate source)" />
</activePackageSource>
```

## <a name="using-environment-variables"></a><span data-ttu-id="cdbba-229">環境変数の使用</span><span class="sxs-lookup"><span data-stu-id="cdbba-229">Using environment variables</span></span>

<span data-ttu-id="cdbba-230">環境変数を `NuGet.Config` 値 (NuGet 3.4 以降) に使用することで、実行時に設定を適用できます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-230">You can use environment variables in `NuGet.Config` values (NuGet 3.4+) to apply settings at run time.</span></span>

<span data-ttu-id="cdbba-231">たとえば、Windows 上の `HOME` 環境変数を `c:\users\username` に設定すると、構成ファイル内の `%HOME%\NuGetRepository` の値は `c:\users\username\NuGetRepository` に解決されます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-231">For example, if the `HOME` environment variable on Windows is set to `c:\users\username`, then the value of `%HOME%\NuGetRepository` in the configuration file resolves to `c:\users\username\NuGetRepository`.</span></span>

<span data-ttu-id="cdbba-232">同様に、Mac/Linux 上の `HOME` を `/home/myStuff` に設定すると、構成ファイル内の `$HOME/NuGetRepository` は `/home/myStuff/NuGetRepository` に解決されます。</span><span class="sxs-lookup"><span data-stu-id="cdbba-232">Similarly, if `HOME` on Mac/Linux is set to `/home/myStuff`, then `$HOME/NuGetRepository` in the configuration file resolves to `/home/myStuff/NuGetRepository`.</span></span>

<span data-ttu-id="cdbba-233">環境変数が見つからない場合、NuGet は構成ファイルからのリテラル値を使用します。</span><span class="sxs-lookup"><span data-stu-id="cdbba-233">If an environment variable is not found, NuGet uses the literal value from the configuration file.</span></span>

## <a name="example-config-file"></a><span data-ttu-id="cdbba-234">構成ファイルの例</span><span class="sxs-lookup"><span data-stu-id="cdbba-234">Example config file</span></span>

<span data-ttu-id="cdbba-235">複数の設定が含まれている `NuGet.Config` ファイルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cdbba-235">Below is an example `NuGet.Config` file that illustrates a number of settings:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <config>
        <!--
            Used to specify the default location to expand packages.
            See: nuget.exe help install
            See: nuget.exe help update

            In this example, %PACKAGEHOME% is an environment variable. On Mac/Linux,
            use $PACKAGE_HOME/External as the value.
        -->
        <add key="repositoryPath" value="%PACKAGEHOME%\External" />

        <!--
            Used to specify default source for the push command.
            See: nuget.exe help push
        -->

        <add key="defaultPushSource" value="https://MyRepo/ES/api/v2/package" />

        <!-- Proxy settings -->
        <add key="http_proxy" value="host" />
        <add key="http_proxy.user" value="username" />
        <add key="http_proxy.password" value="encrypted_password" />
    </config>

    <packageRestore>
        <!-- Allow NuGet to download missing packages -->
        <add key="enabled" value="True" />

        <!-- Automatically check for missing packages during build in Visual Studio -->
        <add key="automatic" value="True" />
    </packageRestore>

    <!--
        Used to specify the default Sources for list, install and update.
        See: nuget.exe help list
        See: nuget.exe help install
        See: nuget.exe help update
    -->
    <packageSources>
        <add key="NuGet official package source" value="https://api.nuget.org/v3/index.json" />
        <add key="MyRepo - ES" value="https://MyRepo/ES/nuget" />
    </packageSources>

    <!-- Used to store credentials -->
    <packageSourceCredentials />

    <!-- Used to disable package sources  -->
    <disabledPackageSources />

    <!--
        Used to specify default API key associated with sources.
        See: nuget.exe help setApiKey
        See: nuget.exe help push
        See: nuget.exe help mirror
    -->
    <apikeys>
        <add key="https://MyRepo/ES/api/v2/package" value="encrypted_api_key" />
    </apikeys>
</configuration>
```