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
ms.openlocfilehash: 3adceac8c725d9ea1610aea090753c9c1d8bc818
ms.sourcegitcommit: 2b50c450cca521681a384aa466ab666679a40213
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2020
ms.locfileid: "79428421"
---
# <a name="install-and-manage-packages-in-visual-studio-using-the-nuget-package-manager"></a>NuGet パッケージ マネージャーを使用して Visual Studio にパッケージをインストールして管理する

Windows 上の Visual Studio 内で NuGet パッケージ マネージャー UI を使用すると、プロジェクトやソリューション内で NuGet パッケージを簡単にインストール、アンインストール、更新することができます。 Visual Studio for Mac でのエクスペリエンスについては、「[プロジェクトに NuGet パッケージを含める](/visualstudio/mac/nuget-walkthrough?toc=/nuget/toc.json)」をご覧ください。 パッケージ マネージャー UI は、Visual Studio Code には含まれていません。

> [!NOTE]
> Visual Studio 2015 内に NuGet パッケージ マネージャーが見当たらない場合は、 **[ツール] > [拡張機能と更新プログラム]** を確認して、 *[NuGet パッケージ マネージャー]* 拡張機能を検索してください。 Visual Studio 内で拡張機能のインストーラーを使用できない場合は、拡張機能を [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html) から直接ダウンロードしてください。
>
> Visual Studio 2017 以降では、NuGet および NuGet パッケージ マネージャーが、.NET 関連のワークロードと共に自動的にインストールされます。 個別にインストールするには、Visual Studio のインストーラー内で **[個別のコンポーネント ] > [コード ツール] > [NuGet パッケージ マネージャー]** オプションを選択します。

## <a name="find-and-install-a-package"></a>パッケージを検索してインストールする

1. **ソリューション エクスプローラー**上で、 **[参照]** またはプロジェクトのどちらかを右クリックし、 **[NuGet パッケージの管理]** を選択します。

    ![[NuGet パッケージの管理] メニュー オプション](media/ManagePackagesUICommand.png)

1. **[参照]** タブには、現在選択されているソースからの人気度順に、パッケージが表示されます (「[パッケージ ソース](#package-sources)」を参照)。 左上の検索ボックスを使用して、特定のパッケージを検索します。 一覧からパッケージを選択して、その情報を表示します。また、これにより、バージョン選択のドロップダウンと共に **[インストール]** ボタンが有効になります。

    ![[NuGet パッケージの管理] ダイアログの [参照] タブ](media/Search.png)

1. ドロップダウンから目的のバージョンを選び、 **[インストール]** を選択します。 Visual Studio によって、パッケージとその依存関係がプロジェクトにインストールされます。 ライセンス条項への同意を求められる場合があります。 インストールが完了すると、追加したパッケージが **[インストール済み]** タブ上に表示されます。また、パッケージがソリューション エクスプローラーの **[参照]** ノードに一覧表示されます。`using` ステートメントを使用すると、プロジェクト内でそれらを参照できることを意味します。

    ![ソリューション エクスプローラー内の [参照]](media/References.png)

> [!Tip]
> 検索にプレリリースバージョンを含めるため、また、バージョンのドロップダウン内でプレリリース バージョンを使用可能にするためには、 **[プレリリースを含める]** オプションを選択します。

> [!Note]
> NuGet には、プロジェクトでパッケージを使用できる、[`PackageReference`](package-references-in-project-files.md) と [`packages.config`](../reference/packages-config.md) の 2 つの形式があります。 [既定値は、Visual Studio のオプション ウィンドウで設定できます](Package-Restore.md#choose-default-package-management-format)。

## <a name="uninstall-a-package"></a>パッケージをアンインストールします

1. **ソリューション エクスプローラー**上で、 **[参照]** または目的のプロジェクトのどちらかを右クリックし、 **[NuGet パッケージの管理]** を選択します。
1. **[インストール済み]** タブを選択します。
1. アンインストールするパッケージを選択し (必要に応じて、検索を使用して一覧をフィルター処理します)、 **[アンインストール]** を選択します。

    ![パッケージのアンインストール](media/UninstallPackage.png)

1. パッケージのアンインストール時には、 **[プレリリースを含める]**および**[パッケージ ソース]** の制御は無効になっていることに注意してください。

## <a name="update-a-package"></a>パッケージを更新する

1. **ソリューション エクスプローラー**上で、 **[参照]** または目的のプロジェクトのどちらかを右クリックし、 **[NuGet パッケージの管理]** を選択します。(Web サイトのプロジェクトでは、**Bin** フォルダーを右クリックします)。
1. **[更新]** タブを選択して、選択されたパッケージ ソースからの使用可能な更新プログラムがあるパッケージを確認します。 **[プレリリースを含める]** を選択して、更新リストにあるプレリリース パッケージを含めます。
1. 更新するパッケージを選択し、右側にあるドロップダウンから目的のバージョンを選択して、 **[更新]** を選択します。

    ![パッケージの更新](media/UpdatePackages.png)

1. <a name="implicit_reference"></a>一部のパッケージでは、 **[更新]** ボタンが無効になり、"SDK によって暗黙的に参照されています" というメッセージ (または "AutoReferenced") が表示されます。 このメッセージは、パッケージがより大きなフレームワークまたは SDK の一部であり、個別に更新してはいけないことを示しています。 (このようなパッケージは、内部的に `<IsImplicitlyDefined>True</IsImplicitlyDefined>` とマークされています。)たとえば、`Microsoft.NETCore.App` は .NET Core SDK の一部であり、パッケージ バージョンは、アプリケーションによって使用されるランタイム フレームワークのバージョンと同じではありません。 [ご自身の .NET Core インストールを更新](https://aka.ms/dotnet-download)して、ASP.NET Core および .NET Core ランタイムの新しいバージョンを取得する必要があります。 [.NET Core メタパッケージとバージョン管理の詳細については、こちらのドキュメントをご覧ください](/dotnet/core/packages)。 これは、一般的に使用されている次のパッケージに該当します。
    * Microsoft.AspNetCore.All
    * Microsoft.AspNetCore.App
    * Microsoft.NETCore.App
    * NETStandard.Library

    ![暗黙的な参照または AutoReferenced としてマークされたパッケージの例](media/PackageManagerUIAutoReferenced.png)

1. 複数のパッケージをそれぞれの最新バージョンに更新するには、リスト内で選択して、リストの上にある **[更新]** ボタンを選択します。
1. また、 **[インストール済み]** タブから個々のパッケージを更新することもできます。この場合、パッケージの詳細にはバージョン セレクター ( **[プレリリースを含める]** オプションに依存します) と **[更新]** ボタンが含まれています。

## <a name="manage-packages-for-the-solution"></a>ソリューションのパッケージの管理

ソリューションのパッケージの管理は、複数のプロジェクトを同時に操作するための便利な手段です。

1. **[ツール] > [NuGet パッケージ マネージャー] > [ソリューションの NuGet パッケージの管理]** メニュー コマンドを選択するか、ソリューションを右クリックして **[NuGet パッケージの管理]** を選択します。

    ![ソリューションの NuGet パッケージの管理](media/ManagePackagesSolutionUICommand.png)

1. ソリューションのパッケージを管理する場合、UI を利用して、操作によって影響を与えるプロジェクトを選択できます。

    ![ソリューションのパッケージを管理する場合のプロジェクト セレクター](media/SolutionPackagesUI.png)

### <a name="consolidate-tab"></a>[統合] タブ

開発者は通常、同じソリューション内のさまざまなプロジェクト間で同じ NuGet パッケージの異なるバージョンを使用することは不適切であると考えています。 ソリューションの NuGet パッケージを管理することを選んだ場合、パッケージ マネージャー UI に **[統合]** タブが表示され、個別のバージョン番号が付与されたパッケージがソリューション内のさまざまなプロジェクトによってどこに使用されているかを簡単に確認できます。

![パッケージ マネージャー UI の [統合] タブ](media/ConsolidateTab.png)

この例では、ClassLibrary1 プロジェクトが EntityFramework 6.2.0 を使用しているのに対して、ConsoleApp1 は EntityFramework 6.1.0 を使用しています。 パッケージ バージョンを統合するには、次を実行します。

- プロジェクトの一覧で、更新するプロジェクトを選択します。
- EntityFramework 6.2.0 など、 **[バージョン]** コントロール内でそれらすべてのプロジェクトに使用するバージョンを選択します。
- **[インストール]** ボタンを選択します。

パッケージ マネージャーによって、選択されたすべてのプロジェクトに対して、選択されたパッケージ バージョンがインストールされます。パッケージは **[統合]** タブ上には表示されなくなります。

## <a name="package-sources"></a>パッケージ ソース

Visual Studio がパッケージを取得するソースを変更するには、ソース セレクターから選択します。

![パッケージ マネージャー UI のパッケージ ソース セレクター](media/PackageSourceDropDown.png)

パッケージ ソースを管理するには:

1. 以下に示したパッケージ マネージャー UI にある**設定**のアイコンを選択するか、 **[ツール] > [オプション]** コマンドを使用して **[NuGet パッケージ マネージャー]** までスクロールします。

    ![パッケージ マネージャー UI の設定のアイコン](media/PackageSourceSettings.png)

1. **[パッケージ ソース]** ノードを選択します。

    ![[パッケージ ソース] オプション](media/options.png)

1. ソースを追加するには、 **+** を選択して、名前を編集し、 **[ソース]** コントロールに URL またはパスを入力して、 **[更新]** を選択します。 ソースがセレクターのドロップダウンに表示されるようになりました。
1. パッケージ ソースを変更するには、それを選択して **[名前]** と **[ソース]** ボックス内で編集を行い、 **[更新]** を選択します。
1. パッケージ ソースを無効にするには、一覧内で名前の左側にあるボックスをオフにします。
1. パッケージ ソースを削除するには、それを選択してから、**X** ボタンを選択します。
1. 上下の矢印ボタンを使用しても、パッケージ ソースの優先順位は変更されません。 Visual Studio では、パッケージ ソースの順序は無視され、要求に最初に応答したいずれかのソースからパッケージが使用されます。 詳しくは、[パッケージの復元](../consume-packages/package-restore.md)に関する記事をご覧ください。

> [!Tip]
> 削除後にパッケージ ソースが再表示される場合は、コンピューター レベルまたはユーザー レベルの `NuGet.Config` ファイルに含まれている可能性があります。 これらのファイルの場所について「[一般的な NuGet 構成](../consume-packages/configuring-nuget-behavior.md)」で確認してから、[nuget ソース コマンド](../reference/nuget-exe-CLI-reference.md)を使用して手動でファイルを編集して、ソースを削除してください。

## <a name="package-manager-options-control"></a>パッケージ マネージャーの [オプション] コントロール

パッケージが選択されると、パッケージ マネージャー UI では、バージョン セレクターの下に展開可能な小さな **[オプション]** コントロールが表示されます (ここでは、折りたたまれた状態と展開された状態の両方が示されています)。 一部のプロジェクトの種類では、 **[プレビュー ウィンドウの表示]** オプションのみが提示されることに注意してください。

![パッケージ マネージャーのオプション](media/PackageManagerUIOptions.png)

以降のセクションでは、これらのオプションについて説明します。

### <a name="show-preview-window"></a>プレビュー ウィンドウの表示

選択すると、パッケージがインストールされる前に、選択したパッケージの依存関係がモ―ダル ウィンドウに表示されます。

![プレビュー ダイアログの例](media/InstallPreviewDialog.png)

<!-- This is here because the link in the UI needs this anchor. See https://github.com/NuGet/NuGet.Client/blob/dev/src/NuGet.Clients/PackageManagement.UI/Xamls/OptionsControl.xaml -->
<a name="install-options"></a>

### <a name="install-and-update-options"></a>インストールと更新のオプション

(すべてのプロジェクトの種類で使用できるわけではありません。)

**[依存関係の動作]** では、インストールする依存パッケージのバージョンが NuGet によってどのように決定されるかを設定します。

- *[依存関係を無視する]* では、すべての依存関係のインストールをスキップします。通常は、パッケージのインストールが中断されます。
- *[最低]* (既定値) では、選択された主要なパッケージの要件に合う最小のバージョン番号を使用して、依存関係がインストールされます。
- *[最高のパッチ]* では、メジャーおよびマイナーのバージョン番号が同じで、パッチ番号が最も大きいバージョンがインストールされます。 たとえば、バージョン 1.2.2 が指定された場合、1.2 から始まる最高のバージョンがインストールされます
- *[最高のマイナー]* では、メジャーのバージョン番号が同じで、マイナー番号とパッチ番号が最も大きいバージョンがインストールされます。 バージョン 1.2.2 が指定された場合、1 から始まる最高のバージョンがインストールされます
- *[最高]* では、使用可能な最高のパッケージ バージョンがインストールされます。

**[ファイルの競合時のアクション]** では、プロジェクト内またはローカル コンピューター上に既に存在するパッケージを NuGet ではどのように処理するべきかを指定します。

- *[プロンプト]* では、既存のパッケージを保持するか上書きするかを尋ねるように NuGet に指示します。
- *[すべて無視]* では、すべての既存のパッケージの上書きをスキップするように NuGet に指示します。
- *[すべて上書き]* では、すべての既存のパッケージを上書きするように NuGet に指示します。

<!-- This is here because the link in the UI needs this anchor. See https://github.com/NuGet/NuGet.Client/blob/dev/src/NuGet.Clients/PackageManagement.UI/Xamls/OptionsControl.xaml -->
<a name="uninstall-options"></a>

### <a name="uninstall-options"></a>アンインストールのオプション

(すべてのプロジェクトの種類で使用できるわけではありません。)

**[依存関係の削除]** : 選択すると、プロジェクト内の他の場所で参照されていない場合は、依存パッケージがすべて削除されます。

**[依存関係が存在する場合でも強制的にアンインストールする]** : 選択すると、プロジェクト内でまだ参照されている場合でも、パッケージがアンインストールされます。 これは通常、パッケージとそれによってインストールされたあらゆる依存関係を削除するために、 **[依存関係の削除]** と組み合わせて使用されます。 ただし、このオプションを使用すると、プロジェクト内での参照が壊れてしまう場合があります。 このような場合、必要に応じて[他のパッケージを再インストールする](../consume-packages/reinstalling-and-updating-packages.md)必要があります。
