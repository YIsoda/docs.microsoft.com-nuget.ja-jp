---
title: Visual Studio に NuGet パッケージをインストールして管理する
description: Visual Studio 内で NuGet パッケージ マネージャー UI を使用して、NuGet パッケージを操作する方法について説明します。
author: karann-msft
ms.author: karann
ms.date: 07/08/2019
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.nuget_package_manager
- vs.toolsoptionspages.nuget_package_manager.general
- vs.toolsoptionspages.nuget_package_manager.package_sources
- vs.nuget.packagemanager.ui
ms.openlocfilehash: 7e4ea59b9954e787e7ab060adc964f3097a8240b
ms.sourcegitcommit: e65180e622f6233b51bb0b41d0e919688083eb26
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419975"
---
# <a name="install-and-manage-packages-in-visual-studio-using-the-nuget-package-manager"></a><span data-ttu-id="7c6d8-103">NuGet パッケージ マネージャーを使用して Visual Studio にパッケージをインストールして管理する</span><span class="sxs-lookup"><span data-stu-id="7c6d8-103">Install and manage packages in Visual Studio using the NuGet Package Manager</span></span>

<span data-ttu-id="7c6d8-104">Windows 上の Visual Studio 内で NuGet パッケージ マネージャー UI を使用すると、プロジェクトやソリューション内で NuGet パッケージを簡単にインストール、アンインストール、更新することができます。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-104">The NuGet Package Manager UI in Visual Studio on Windows allows you to easily install, uninstall, and update NuGet packages in projects and solutions.</span></span> <span data-ttu-id="7c6d8-105">Visual Studio for Mac でのエクスペリエンスについては、「[プロジェクトに NuGet パッケージを含める](/visualstudio/mac/nuget-walkthrough?toc=/nuget/toc.json)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-105">For the experience in Visual Studio for Mac, see [Including a NuGet package in your project](/visualstudio/mac/nuget-walkthrough?toc=/nuget/toc.json).</span></span> <span data-ttu-id="7c6d8-106">パッケージ マネージャー UI は、Visual Studio Code には含まれていません。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-106">The Package Manager UI is not included with Visual Studio Code.</span></span>

> [!NOTE]
> <span data-ttu-id="7c6d8-107">Visual Studio 2015 内に NuGet パッケージ マネージャーが見当たらない場合は、 **[ツール] > [拡張機能と更新プログラム]** を確認して、 *[NuGet パッケージ マネージャー]* 拡張機能を検索してください。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-107">If you're missing the NuGet Package Manager in Visual Studio 2015, check **Tools > Extensions and Updates...** and search for the *NuGet Package Manager* extension.</span></span> <span data-ttu-id="7c6d8-108">Visual Studio 内で拡張機能のインストーラーを使用できない場合は、拡張機能を [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html) から直接ダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-108">If you're unable to use the extensions installer in Visual Studio, download the extension directly from [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html).</span></span>
>
> <span data-ttu-id="7c6d8-109">Visual Studio 2017 以降では、NuGet および NuGet パッケージ マネージャーが、.NET 関連のワークロードと共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-109">Starting in Visual Studio 2017, NuGet and the NuGet Package Manager are automatically installed with any .NET-related workloads.</span></span> <span data-ttu-id="7c6d8-110">個別にインストールするには、Visual Studio のインストーラー内で **[個別のコンポーネント ] > [コード ツール] > [NuGet パッケージ マネージャー]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-110">Install it individually by selecting the **Individual components > Code tools > NuGet package manager** option in the Visual Studio installer.</span></span>

## <a name="find-and-install-a-package"></a><span data-ttu-id="7c6d8-111">パッケージを検索してインストールする</span><span class="sxs-lookup"><span data-stu-id="7c6d8-111">Find and install a package</span></span>

1. <span data-ttu-id="7c6d8-112">**ソリューション エクスプローラー**上で、 **[参照]** またはプロジェクトのどちらかを右クリックし、 **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-112">In **Solution Explorer**, right-click either **References**  or a project and select **Manage NuGet Packages...**.</span></span>

    ![[NuGet パッケージの管理] メニュー オプション](media/ManagePackagesUICommand.png)

1. <span data-ttu-id="7c6d8-114">**[参照]** タブには、現在選択されているソースからの人気度順に、パッケージが表示されます (「[パッケージ ソース](#package-sources)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-114">The **Browse** tab displays packages by popularity from the currently selected source (see [package sources](#package-sources)).</span></span> <span data-ttu-id="7c6d8-115">左上の検索ボックスを使用して、特定のパッケージを検索します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-115">Search for a specific package using the search box on the upper left.</span></span> <span data-ttu-id="7c6d8-116">一覧からパッケージを選択して、その情報を表示します。また、これにより、バージョン選択のドロップダウンと共に **[インストール]** ボタンが有効になります。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-116">Select a package from the list to display its information, which also enables the **Install** button along with a version-selection drop-down.</span></span>

    ![[NuGet パッケージの管理] ダイアログの [参照] タブ](media/Search.png)

1. <span data-ttu-id="7c6d8-118">ドロップダウンから目的のバージョンを選び、 **[インストール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-118">Select the desired version from the drop-down and select **Install**.</span></span> <span data-ttu-id="7c6d8-119">Visual Studio によって、パッケージとその依存関係がプロジェクトにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-119">Visual Studio installs the package and its dependencies into the project.</span></span> <span data-ttu-id="7c6d8-120">ライセンス条項への同意を求められる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-120">You may be asked to accept license terms.</span></span> <span data-ttu-id="7c6d8-121">インストールが完了すると、追加したパッケージが **[インストール済み]** タブ上に表示されます。また、パッケージがソリューション エクスプローラーの **[参照]** ノードに一覧表示されます。`using` ステートメントを使用すると、プロジェクト内でそれらを参照できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-121">When installation is complete, the added packages appear on the **Installed** tab. Packages are also listed in the **References** node of Solution Explorer, indicating that you can refer to them in the project with `using` statements.</span></span>

    ![ソリューション エクスプローラー内の [参照]](media/References.png)

> [!Tip]
> <span data-ttu-id="7c6d8-123">検索にプレリリースバージョンを含めるため、また、バージョンのドロップダウン内でプレリリース バージョンを使用可能にするためには、 **[プレリリースを含める]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-123">To include prerelease versions in the search, and to make prerelease versions available in the version drop-down, select the **Include prerelease** option.</span></span>

## <a name="uninstall-a-package"></a><span data-ttu-id="7c6d8-124">パッケージをアンインストールします</span><span class="sxs-lookup"><span data-stu-id="7c6d8-124">Uninstall a package</span></span>

1. <span data-ttu-id="7c6d8-125">**ソリューション エクスプローラー**上で、 **[参照]** または目的のプロジェクトのどちらかを右クリックし、 **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-125">In **Solution Explorer**, right-click either **References** or the desired project, and select **Manage NuGet Packages...**.</span></span>
1. <span data-ttu-id="7c6d8-126">**[インストール済み]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-126">Select the **Installed** tab.</span></span>
1. <span data-ttu-id="7c6d8-127">アンインストールするパッケージを選択し (必要に応じて、検索を使用して一覧をフィルター処理します)、 **[アンインストール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-127">Select the package to uninstall (using search to filter the list if necessary) and select **Uninstall**.</span></span>

    ![パッケージのアンインストール](media/UninstallPackage.png)

1. <span data-ttu-id="7c6d8-129">パッケージのアンインストール時には、 **[プレリリースを含める]**および**[パッケージ ソース]** の制御は無効になっていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-129">Note that the **Include prerelease** and **Package source** controls have no effect when uninstalling packages.</span></span>

## <a name="update-a-package"></a><span data-ttu-id="7c6d8-130">パッケージを更新する</span><span class="sxs-lookup"><span data-stu-id="7c6d8-130">Update a package</span></span>

1. <span data-ttu-id="7c6d8-131">**ソリューション エクスプローラー**上で、 **[参照]** または目的のプロジェクトのどちらかを右クリックし、 **[NuGet パッケージの管理]** を選択します。(Web サイトのプロジェクトでは、**Bin** フォルダーを右クリックします)。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-131">In **Solution Explorer**, right-click either **References** or the desired project, and select **Manage NuGet Packages...**. (In web site projects, right-click the **Bin** folder.)</span></span>
1. <span data-ttu-id="7c6d8-132">**[更新]** タブを選択して、選択されたパッケージ ソースからの使用可能な更新プログラムがあるパッケージを確認します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-132">Select the **Updates** tab to see packages that have available updates from the selected package sources.</span></span> <span data-ttu-id="7c6d8-133">**[プレリリースを含める]** を選択して、更新リストにあるプレリリース パッケージを含めます。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-133">Select **Include prerelease** to include prerelease packages in the update list.</span></span>
1. <span data-ttu-id="7c6d8-134">更新するパッケージを選択し、右側にあるドロップダウンから目的のバージョンを選択して、 **[更新]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-134">Select the package to update, select the desired version from the drop-down on the right, and select **Update**.</span></span>

    ![パッケージの更新](media/UpdatePackages.png)

1. <a name="implicit_reference"></a><span data-ttu-id="7c6d8-136">一部のパッケージでは、 **[更新]** ボタンが無効になり、"SDK によって暗黙的に参照されています" というメッセージ (または "AutoReferenced") が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-136">For some packages, the **Update** button is disabled and a message appears saying that it's "Implicitly referenced by an SDK" (or "AutoReferenced").</span></span> <span data-ttu-id="7c6d8-137">このメッセージは、パッケージがより大きなフレームワークまたは SDK の一部であり、個別に更新してはいけないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-137">This message indicates that the package is part of a larger framework or SDK and should not be updated independently.</span></span> <span data-ttu-id="7c6d8-138">(このようなパッケージは、内部的に `<IsImplicitlyDefined>True</IsImplicitlyDefined>` とマークされています。)たとえば、`Microsoft.NETCore.App` は .NET Core SDK の一部であり、パッケージ バージョンは、アプリケーションによって使用されるランタイム フレームワークのバージョンと同じではありません。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-138">(Such packages are internally marked with `<IsImplicitlyDefined>True</IsImplicitlyDefined>`.) For example, `Microsoft.NETCore.App` is part of the .NET Core SDK, and the package version is not the same as the version of the runtime framework used by the application.</span></span> <span data-ttu-id="7c6d8-139">[ご自身の .NET Core インストールを更新](https://aka.ms/dotnet-download)して、ASP.NET Core および .NET Core ランタイムの新しいバージョンを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-139">You need to [update your .NET Core installation](https://aka.ms/dotnet-download) to get new versions of the ASP.NET Core and .NET Core runtime.</span></span> <span data-ttu-id="7c6d8-140">[.NET Core メタパッケージとバージョン管理の詳細については、こちらのドキュメントをご覧ください](/dotnet/core/packages)。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-140">[See this document for more details on .NET Core metapackages and versioning](/dotnet/core/packages).</span></span> <span data-ttu-id="7c6d8-141">これは、一般的に使用されている次のパッケージに該当します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-141">This applies to the following commonly used packages:</span></span>
    * <span data-ttu-id="7c6d8-142">Microsoft.AspNetCore.All</span><span class="sxs-lookup"><span data-stu-id="7c6d8-142">Microsoft.AspNetCore.All</span></span>
    * <span data-ttu-id="7c6d8-143">Microsoft.AspNetCore.App</span><span class="sxs-lookup"><span data-stu-id="7c6d8-143">Microsoft.AspNetCore.App</span></span>
    * <span data-ttu-id="7c6d8-144">Microsoft.NETCore.App</span><span class="sxs-lookup"><span data-stu-id="7c6d8-144">Microsoft.NETCore.App</span></span>
    * <span data-ttu-id="7c6d8-145">NETStandard.Library</span><span class="sxs-lookup"><span data-stu-id="7c6d8-145">NETStandard.Library</span></span>

    ![暗黙的な参照または AutoReferenced としてマークされたパッケージの例](media/PackageManagerUIAutoReferenced.png)

1. <span data-ttu-id="7c6d8-147">複数のパッケージをそれぞれの最新バージョンに更新するには、リスト内で選択して、リストの上にある **[更新]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-147">To update multiple packages to their newest versions, select  them in the list and select the **Update** button above the list.</span></span>
1. <span data-ttu-id="7c6d8-148">また、 **[インストール済み]** タブから個々のパッケージを更新することもできます。この場合、パッケージの詳細にはバージョン セレクター ( **[プレリリースを含める]** オプションに依存します) と **[更新]** ボタンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-148">You can also update an individual package from the **Installed** tab. In this case, the details for the package include a version selector (subject to the **Include prerelease** option) and an **Update** button.</span></span>

## <a name="manage-packages-for-the-solution"></a><span data-ttu-id="7c6d8-149">ソリューションのパッケージの管理</span><span class="sxs-lookup"><span data-stu-id="7c6d8-149">Manage packages for the solution</span></span>

<span data-ttu-id="7c6d8-150">ソリューションのパッケージの管理は、複数のプロジェクトを同時に操作するための便利な手段です。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-150">Managing packages for a solution is a convenient means to work with multiple projects simultaneously.</span></span>

1. <span data-ttu-id="7c6d8-151">**[ツール] > [NuGet パッケージ マネージャー] > [ソリューションの NuGet パッケージの管理]** メニュー コマンドを選択するか、ソリューションを右クリックして **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-151">Select the **Tools > NuGet Package Manager > Manage NuGet Packages for Solution...** menu command, or right-click the solution and select **Manage NuGet Packages...**:</span></span>

    ![ソリューションの NuGet パッケージの管理](media/ManagePackagesSolutionUICommand.png)

1. <span data-ttu-id="7c6d8-153">ソリューションのパッケージを管理する場合、UI を利用して、操作によって影響を与えるプロジェクトを選択できます。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-153">When managing packages for the solution, the UI lets you select the projects that are affected by the operations:</span></span>

    ![ソリューションのパッケージを管理する場合のプロジェクト セレクター](media/SolutionPackagesUI.png)

### <a name="consolidate-tab"></a><span data-ttu-id="7c6d8-155">[統合] タブ</span><span class="sxs-lookup"><span data-stu-id="7c6d8-155">Consolidate tab</span></span>

<span data-ttu-id="7c6d8-156">開発者は通常、同じソリューション内のさまざまなプロジェクト間で同じ NuGet パッケージの異なるバージョンを使用することは不適切であると考えています。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-156">Developers typically consider it bad practice to use different versions of the same NuGet package across different projects in the same solution.</span></span> <span data-ttu-id="7c6d8-157">ソリューションの NuGet パッケージを管理することを選んだ場合、パッケージ マネージャー UI に **[統合]** タブが表示され、個別のバージョン番号が付与されたパッケージがソリューション内のさまざまなプロジェクトによってどこに使用されているかを簡単に確認できます。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-157">When you choose to manage packages for a solution, the Package Manager UI provides a **Consolidate** tab on which you can easily see where packages with distinct version numbers are used by different projects in the solution:</span></span>

![パッケージ マネージャー UI の [統合] タブ](media/ConsolidateTab.png)

<span data-ttu-id="7c6d8-159">この例では、ClassLibrary1 プロジェクトが EntityFramework 6.2.0 を使用しているのに対して、ConsoleApp1 は EntityFramework 6.1.0 を使用しています。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-159">In this example, the ClassLibrary1 project is using EntityFramework 6.2.0, whereas ConsoleApp1 is using EntityFramework 6.1.0.</span></span> <span data-ttu-id="7c6d8-160">パッケージ バージョンを統合するには、次を実行します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-160">To consolidate package versions, do the following:</span></span>

- <span data-ttu-id="7c6d8-161">プロジェクトの一覧で、更新するプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-161">Select the projects to update in the project list.</span></span>
- <span data-ttu-id="7c6d8-162">EntityFramework 6.2.0 など、 **[バージョン]** コントロール内でそれらすべてのプロジェクトに使用するバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-162">Select the version to use in all those projects in the **Version** control, such as EntityFramework 6.2.0.</span></span>
- <span data-ttu-id="7c6d8-163">**[インストール]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-163">Select the **Install** button.</span></span>

<span data-ttu-id="7c6d8-164">パッケージ マネージャーによって、選択されたすべてのプロジェクトに対して、選択されたパッケージ バージョンがインストールされます。パッケージは **[統合]** タブ上には表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-164">The Package Manager installs the selected package version into all selected projects, after which the package no longer appears on the **Consolidate** tab.</span></span>

## <a name="package-sources"></a><span data-ttu-id="7c6d8-165">パッケージ ソース</span><span class="sxs-lookup"><span data-stu-id="7c6d8-165">Package sources</span></span>

<span data-ttu-id="7c6d8-166">Visual Studio がパッケージを取得するソースを変更するには、ソース セレクターから選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-166">To change the source from which Visual Studio obtains packages, select one from the source selector:</span></span>

![パッケージ マネージャー UI のパッケージ ソース セレクター](media/PackageSourceDropDown.png)

<span data-ttu-id="7c6d8-168">パッケージ ソースを管理するには:</span><span class="sxs-lookup"><span data-stu-id="7c6d8-168">To manage package sources:</span></span>

1. <span data-ttu-id="7c6d8-169">以下に示したパッケージ マネージャー UI にある**設定**のアイコンを選択するか、 **[ツール] > [オプション]** コマンドを使用して **[NuGet パッケージ マネージャー]** までスクロールします。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-169">Select the **Settings** icon in the Package Manager UI outlined below or use the **Tools > Options** command and scroll to **NuGet Package Manager**:</span></span>

    ![パッケージ マネージャー UI の設定のアイコン](media/PackageSourceSettings.png)

1. <span data-ttu-id="7c6d8-171">**[パッケージ ソース]** ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-171">Select the **Package Sources** node:</span></span>

    ![[パッケージ ソース] オプション](media/options.png)

1. <span data-ttu-id="7c6d8-173">ソースを追加するには、 **+** を選択して、名前を編集し、 **[ソース]** コントロールに URL またはパスを入力して、 **[更新]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-173">To add a source, select **+**, edit the name, enter the URL or path in the **Source** control, and select  **Update**.</span></span> <span data-ttu-id="7c6d8-174">ソースがセレクターのドロップダウンに表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-174">The source now appears in the selector drop-down.</span></span>
1. <span data-ttu-id="7c6d8-175">パッケージ ソースを変更するには、それを選択して **[名前]** と **[ソース]** ボックス内で編集を行い、 **[更新]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-175">To change a package source, select it, make edits in the **Name** and **Source** boxes, and select **Update**.</span></span>
1. <span data-ttu-id="7c6d8-176">パッケージ ソースを無効にするには、一覧内で名前の左側にあるボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-176">To disable a package source, clear the box to the left of the name in the list.</span></span>
1. <span data-ttu-id="7c6d8-177">パッケージ ソースを削除するには、それを選択してから、**X** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-177">To remove a package source, select it and then select the **X** button.</span></span>
1. <span data-ttu-id="7c6d8-178">上下の矢印ボタンを使用しても、パッケージ ソースの優先順位は変更されません。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-178">Using the up and down arrow buttons does not change the priority order of the package sources.</span></span> <span data-ttu-id="7c6d8-179">Visual Studio では、パッケージ ソースの順序は無視され、要求に最初に応答したいずれかのソースからパッケージが使用されます。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-179">Visual Studio ignores the order of package sources, using the package from whichever source is first to respond to requests.</span></span> <span data-ttu-id="7c6d8-180">詳しくは、[パッケージの復元](../consume-packages/package-restore.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-180">For more information, see [Package restore](../consume-packages/package-restore.md).</span></span>

> [!Tip]
> <span data-ttu-id="7c6d8-181">削除後にパッケージ ソースが再表示される場合は、コンピューター レベルまたはユーザー レベルの `NuGet.Config` ファイルに含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-181">If a package source reappears after deleting it, it may be listed in a computer-level or user-level `NuGet.Config` files.</span></span> <span data-ttu-id="7c6d8-182">これらのファイルの場所について「[一般的な NuGet 構成](../consume-packages/configuring-nuget-behavior.md)」で確認してから、[nuget ソース コマンド](../reference/nuget-exe-CLI-reference.md)を使用して手動でファイルを編集して、ソースを削除してください。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-182">See [Common NuGet configurations](../consume-packages/configuring-nuget-behavior.md) for the location of these files, then remove the source by editing the files manually or using the [nuget sources command](../reference/nuget-exe-CLI-reference.md).</span></span>

## <a name="package-manager-options-control"></a><span data-ttu-id="7c6d8-183">パッケージ マネージャーの [オプション] コントロール</span><span class="sxs-lookup"><span data-stu-id="7c6d8-183">Package manager Options control</span></span>

<span data-ttu-id="7c6d8-184">パッケージが選択されると、パッケージ マネージャー UI では、バージョン セレクターの下に展開可能な小さな **[オプション]** コントロールが表示されます (ここでは、折りたたまれた状態と展開された状態の両方が示されています)。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-184">When a package is selected, the Package Manager UI displays a small, expandable **Options** control below the version selector (shown here both collapsed and expanded).</span></span> <span data-ttu-id="7c6d8-185">一部のプロジェクトの種類では、 **[プレビュー ウィンドウの表示]** オプションのみが提示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-185">Note that for some project types, only the **Show preview window** option is provided.</span></span>

![パッケージ マネージャーのオプション](media/PackageManagerUIOptions.png)

<span data-ttu-id="7c6d8-187">以降のセクションでは、これらのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-187">The following sections explain these options.</span></span>

### <a name="show-preview-window"></a><span data-ttu-id="7c6d8-188">プレビュー ウィンドウの表示</span><span class="sxs-lookup"><span data-stu-id="7c6d8-188">Show preview window</span></span>

<span data-ttu-id="7c6d8-189">選択すると、パッケージがインストールされる前に、選択したパッケージの依存関係がモ―ダル ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-189">When selected, a modal window displays which the dependencies of a chosen package before the package is installed:</span></span>

![プレビュー ダイアログの例](media/InstallPreviewDialog.png)

<!-- This is here because the link in the UI needs this anchor. See https://github.com/NuGet/NuGet.Client/blob/dev/src/NuGet.Clients/PackageManagement.UI/Xamls/OptionsControl.xaml -->
<a name="install-options"></a>

### <a name="install-and-update-options"></a><span data-ttu-id="7c6d8-191">インストールと更新のオプション</span><span class="sxs-lookup"><span data-stu-id="7c6d8-191">Install and Update Options</span></span>

<span data-ttu-id="7c6d8-192">(すべてのプロジェクトの種類で使用できるわけではありません。)</span><span class="sxs-lookup"><span data-stu-id="7c6d8-192">(Not available for all project types.)</span></span>

<span data-ttu-id="7c6d8-193">**[依存関係の動作]** では、インストールする依存パッケージのバージョンが NuGet によってどのように決定されるかを設定します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-193">**Dependency behavior** configures how NuGet decides which versions of dependent packages to install:</span></span>

- <span data-ttu-id="7c6d8-194">*[依存関係を無視する]* では、すべての依存関係のインストールをスキップします。通常は、パッケージのインストールが中断されます。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-194">*Ignore dependencies* skips installing any dependencies, which typically breaks the package being installed.</span></span>
- <span data-ttu-id="7c6d8-195">*[最低]* (既定値) では、選択された主要なパッケージの要件に合う最小のバージョン番号を使用して、依存関係がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-195">*Lowest* [Default] installs the dependency with the minimal version number that meets the requirements of the primary chosen package.</span></span>
- <span data-ttu-id="7c6d8-196">*[最高のパッチ]* では、メジャーおよびマイナーのバージョン番号が同じで、パッチ番号が最も大きいバージョンがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-196">*Highest Patch* installs the version with the same major and minor version numbers, but the highest patch number.</span></span> <span data-ttu-id="7c6d8-197">たとえば、バージョン 1.2.2 が指定された場合、1.2 から始まる最高のバージョンがインストールされます</span><span class="sxs-lookup"><span data-stu-id="7c6d8-197">For example, if version 1.2.2 is specified then the highest version that starts with 1.2 will be installed</span></span>
- <span data-ttu-id="7c6d8-198">*[最高のマイナー]* では、メジャーのバージョン番号が同じで、マイナー番号とパッチ番号が最も大きいバージョンがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-198">*Highest Minor* installs the version with the same major version number but the highest minor number and patch number.</span></span> <span data-ttu-id="7c6d8-199">バージョン 1.2.2 が指定された場合、1 から始まる最高のバージョンがインストールされます</span><span class="sxs-lookup"><span data-stu-id="7c6d8-199">If version 1.2.2 is specified, then the highest version that starts with 1 will be installed</span></span>
- <span data-ttu-id="7c6d8-200">*[最高]* では、使用可能な最高のパッケージ バージョンがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-200">*Highest* installs the highest available version of the package.</span></span>

<span data-ttu-id="7c6d8-201">**[ファイルの競合時のアクション]** では、プロジェクト内またはローカル コンピューター上に既に存在するパッケージを NuGet ではどのように処理するべきかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-201">**File conflict action** specifies how NuGet should handle packages that already exist in the project or local machine:</span></span>

- <span data-ttu-id="7c6d8-202">*[プロンプト]* では、既存のパッケージを保持するか上書きするかを尋ねるように NuGet に指示します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-202">*Prompt* instructs NuGet to ask whether to keep or overwrite existing packages.</span></span>
- <span data-ttu-id="7c6d8-203">*[すべて無視]* では、すべての既存のパッケージの上書きをスキップするように NuGet に指示します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-203">*Ignore All* instructs NuGet to skip overwriting any existing packages.</span></span>
- <span data-ttu-id="7c6d8-204">*[すべて上書き]* では、すべての既存のパッケージを上書きするように NuGet に指示します。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-204">*Overwrite All* instructs NuGet to overwrite any existing packages.</span></span>

<!-- This is here because the link in the UI needs this anchor. See https://github.com/NuGet/NuGet.Client/blob/dev/src/NuGet.Clients/PackageManagement.UI/Xamls/OptionsControl.xaml -->
<a name="uninstall-options"></a>

### <a name="uninstall-options"></a><span data-ttu-id="7c6d8-205">アンインストールのオプション</span><span class="sxs-lookup"><span data-stu-id="7c6d8-205">Uninstall Options</span></span>

<span data-ttu-id="7c6d8-206">(すべてのプロジェクトの種類で使用できるわけではありません。)</span><span class="sxs-lookup"><span data-stu-id="7c6d8-206">(Not available for all project types.)</span></span>

<span data-ttu-id="7c6d8-207">**[依存関係の削除]** : 選択すると、プロジェクト内の他の場所で参照されていない場合は、依存パッケージがすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-207">**Remove dependencies**: when selected, removes any dependent packages if they're not referenced elsewhere in the project.</span></span>

<span data-ttu-id="7c6d8-208">**[依存関係が存在する場合でも強制的にアンインストールする]** : 選択すると、プロジェクト内でまだ参照されている場合でも、パッケージがアンインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-208">**Force uninstall even if there are dependencies on it**: when selected, uninstalls a package even if it's still being referenced in the project.</span></span> <span data-ttu-id="7c6d8-209">これは通常、パッケージとそれによってインストールされたあらゆる依存関係を削除するために、 **[依存関係の削除]** と組み合わせて使用されます。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-209">This is typically used in combination with **Remove dependencies** to remove a package and whatever dependencies it installed.</span></span> <span data-ttu-id="7c6d8-210">ただし、このオプションを使用すると、プロジェクト内での参照が壊れてしまう場合があります。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-210">Using this option may, however, lead to broken references in the project.</span></span> <span data-ttu-id="7c6d8-211">このような場合、必要に応じて[他のパッケージを再インストールする](../consume-packages/reinstalling-and-updating-packages.md)必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c6d8-211">In such cases, you may need to [reinstall those other packages](../consume-packages/reinstalling-and-updating-packages.md).</span></span>