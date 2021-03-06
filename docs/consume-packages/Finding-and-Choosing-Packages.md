---
title: NuGet パッケージの検索と選択
description: NuGet 検索構文の詳細を含む、プロジェクトに最適な NuGet パッケージを検索して選択する方法の概要。
author: karann-msft
ms.author: karann
ms.date: 06/04/2018
ms.topic: conceptual
ms.openlocfilehash: 9f427005251bc2bf7a8a79285e39b4bd49062dbf
ms.sourcegitcommit: 2b50c450cca521681a384aa466ab666679a40213
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2020
ms.locfileid: "79428493"
---
# <a name="finding-and-evaluating-nuget-packages-for-your-project"></a>プロジェクトの NuGet パッケージの検索と評価

任意の .NET プロジェクトを開始する場合や、ご利用のアプリまたはサービスの機能上のニーズを特定する場合は常に、そのニーズを満たす既存の NuGet パッケージを使用することで時間と手間を大幅に省くことができます。 これらのパッケージは、[nuget.org](https://www.nuget.org/packages/) のパブリック コレクション、または組織あるいは別のサードパーティによって提供されるプライベート ソースから取得できます。

## <a name="finding-packages"></a>パッケージの検索

nuget.org にアクセスしたとき、または Visual Studio でパッケージ マネージャー UI を開いたときに、総ダウンロード数で並べ替えられたパッケージのリストが表示されます。 その際に、数百万の .NET プロジェクト間で最も広く使用されているパッケージが即時に示されます。 最初の数ページにリストされる少なくともいくつかのパッケージがプロジェクトで役立つことは十分あり得ます。

![最もよく利用されているパッケージを示す uget.org/パッケージの既定ビュー](media/Finding-01-Popularity.png)

ページの右上にある **[プレリリースを含める]** オプションに注目してください。 これが選択されている場合、nuget.org にベータ リリースおよびその他の初期リリースを含むすべてのバージョンのパッケージが表示されます。 安定リリースのみを表示するには、このオプションをオフにします。

特定のニーズに合わせて、(Visual Studio のパッケージ マネージャー内、または nuget.org などのポータル上で) タグで検索するのが、適切なパッケージを検出する最も一般的な方法です。 たとえば、"json" で検索すると、そのキーワードのタグが付いた (したがって、JSON データ形式となんらかの関係がある) すべての NuGet パッケージがリストされます。

![nuget.org での 'json' の検索結果](media/Finding-02-SearchResults.png)

パッケージ ID がわかっている場合は、その ID を使用して検索することもできます。 後述の「[検索構文](#search-syntax)」を参照してください。

この時点では、検索結果は関連性のみで並べ替えられているため、通常は、ニーズに合うパッケージの少なくとも最初の数ページの結果に目を通す必要があります。あるいは、検索条件を絞り込んでより詳細な結果が得られるようにする必要があります。

### <a name="does-the-package-support-my-projects-target-framework"></a>パッケージでプロジェクトのターゲット フレームワークはサポートされますか?

NuGet でパッケージがプロジェクトにインストールされるのは、そのパッケージのサポートされているフレームワークにプロジェクトのターゲット フレームワークが含まれている場合のみです パッケージに互換性がない場合、NuGet はエラーを表示します。

サポートされているフレームワークが nuget.org ギャラリーに直接リストされるパッケージもありますが、そのようなデータは必要でないため、多くのパッケージにはそのリストは含まれません。 現時点では、特定のターゲット フレームワークをサポートするパッケージを nuget.org で検索する手段はありません (この機能は検討中です。[NuGet の問題 2936](https://github.com/NuGet/NuGetGallery/issues/2936) を参照してください)。

幸いにも、以下の別の 2 つの方法でサポートされているフレームワークを判別できます。

1. NuGet パッケージ マネージャー コンソールで [`Install-Package`](../reference/ps-reference/ps-ref-install-package.md) コマンドを使用して、プロジェクトにパッケージをインストールしてみます。 パッケージに互換性がない場合は、このコマンドでパッケージのサポートされているフレームワークが表示されます。

1. **[情報]** の下にある **[手動でダウンロード]** リンクを使用して、nuget.org のページからパッケージをダウンロードします。 拡張子を `.nupkg` から `.zip` に変更し、ファイルを開き、その `lib` フォルダーの内容を調べます。 そこに、サポートされている各フレームワークのサブフォルダーが表示されます。各サブフォルダーには、ターゲット フレームワーク モニカー (TFM。「[ターゲット フレームワーク](../reference/target-frameworks.md)」を参照) を使用して名前が付けられます。 `lib` の下にサブフォルダーがなく、DLL が 1 つだけの場合は、プロジェクトにパッケージをインストールしてみて、その互換性を検出する必要があります。

## <a name="pre-release-packages"></a>プレリリース パッケージ

多くのパッケージの作成者は、継続的に改善を行い、最新リビジョンに対するフィードバックを求めるため、プレビュー リリースとベータ リリースを利用できるようにします。

既定では、nuget.org での検索結果にプレリリース パッケージが表示されます。 安定リリースのみを検索するには、ページの右上にある **[プレリリースを含める]** オプションをオフにします。

![nuget.org の [プレリリースを含める] チェックボックス](media/Finding-06-include-prerelease.png)

Visual Studio の場合、また、NuGet CLI および dotnet CLI ツールを使用する場合、既定では NuGet にプレリリース版は含まれません。 この動作を変更するには、次の手順を実行します。

- **Visual Studio のパッケージ マネージャー UI**: **[NuGet パッケージの管理]** UI で、 **[プレリリースを含める]** ボックスを設定します。 このボックスを設定または設定解除するとパッケージ マネージャー UI とインストールできるバージョンのリストが更新されます。

    ![Visual Studio の [プレリリースを含める] チェックボックス](media/Prerelease_02-CheckPrerelease.png)

- **パッケージ マネージャー コンソール**: `Find-Package`、`Get-Package`、`Install-Package`、`Sync-Package`、`Update-Package` コマンドで `-IncludePrerelease` スイッチを使用します。 「[PowerShell Reference](../reference/powershell-reference.md)」 (PowerShell リファレンス) を参照してください。

- **nuget.exe CLI**: `install`、`update`、`delete`、`mirror` コマンドで `-prerelease` スイッチを使用します。 「[NuGet CLI reference](../reference/nuget-exe-cli-reference.md)」(NuGet CLI リファレンス) を参照してください。

- **dotnet.exe CLI**: `-v` 引数を使用して、正確なプレリリース バージョンを指定します。 「[dotnet add package](/dotnet/core/tools/dotnet-add-package)」を参照してください。

<a name="native-cpp-packages"></a>

### <a name="native-c-packages"></a>ネイティブ C++ パッケージ

NuGet では、Visual Studio の C++ プロジェクトで使用できるネイティブ C++ パッケージがサポートされます。 これにより、プロジェクトの **[NuGet パッケージの管理]** コンテキスト メニュー コマンドが有効になり、`native` ターゲット フレームワークが導入され、MSBuild 統合が提供されます。

[nuget.org](https://www.nuget.org/packages) でネイティブ パッケージを見つけるには、`tag:native` を使用して検索します。 通常、このようなパッケージでは `.targets` ファイルと `.props` ファイルが提供されます。これらのファイルは、パッケージがプロジェクトに追加されると、NuGet で自動的にインポートされます。

## <a name="evaluating-packages"></a>パッケージの評価

パッケージの有用性を評価する最適な方法は、該当のパッケージをダウンロードし、自分のコードで試行してみることです (なお、nuget.org のすべてのパッケージでは、定期的にウィルスをスキャンしています)。 結局、人気の高いパッケージはどれも最初はごく少数の開発者のみが使用するため、あなたは早期導入者の 1 人である可能性があります

同時に、NuGet パッケージを使用するということはそれに依存することを意味するため、堅牢で信頼性が高いことを確認する必要があります。 パッケージをインストールして直接テストするには時間がかかるため、パッケージのリスト ページの情報を使用して、パッケージの品質について多くを学習することもできます。

- *ダウンロード統計*: nuget.org のパッケージ ページにある **[統計]** セクションには、総ダウンロード数、最新版のダウンロード数、および 1 日あたりの平均ダウンロード数が表示されます。 大きい数は他の多くの開発者がパッケージに依存していることを示しており、その能力が実証されたことを意味します。

    ![パッケージのリスト ページのダウンロード統計](media/Finding-03-Downloads.png)

- *GitHub Usage (GitHub 使用)* : パッケージ ページの **[GitHub Usage]\(GitHub 使用\)** セクションには、このパッケージに依存していて GitHub に多数の星のあるパブリック GitHub リポジトリが一覧表示されます。 GitHub リポジトリの星の数は、通常、そのリポジトリが GitHub ユーザーにどの程度広く普及しているかを示しています (星の数が多いほど広く普及しています)。 GitHub の星とリポジトリのランク付けシステムの詳細については、[GitHub の概要ページ](https://help.github.com/en/github/getting-started-with-github/saving-repositories-with-stars#about-stars)を参照してください。

    ![GitHub 使用](media/GitHub-Usage.png)

    > [!Note]
    > パッケージの [GitHub Usage]\(GitHub 使用\) セクションは、個々のリポジトリを人間が確認することなく、定期的かつ自動的に生成されます。また、パッケージに依存していて GitHub ユーザーに広く普及している GitHub リポジトリを表示するために、情報提供のみを目的としています。

- *バージョン履歴*: パッケージ ページの **[情報]** で最新の更新日を見つけて、 **[バージョン履歴]** を確認します。 適切に保守されているパッケージの場合、最新の更新情報と豊かなバージョン履歴が表示されます。 放置されたパッケージの場合、更新情報は少なく、しばらくの間更新されていないことがほとんどです。

    ![パッケージのリスト ページの [バージョン履歴]](media/Finding-04-VersionHistory.png)

- *最近のインストール*: パッケージ ページの **[統計]** で、 **[View full stats]\(完全な統計を表示\)** を選択します。完全な統計のページには、バージョン番号ごとに過去 6 週間のパッケージのインストール数が表示されます。 他の開発者が積極的に使用しているパッケージを選択することをお勧めします。

- *サポート*: パッケージ ページの **[情報]** で、 **[プロジェクト サイト]** (使用可能な場合) を選択すると、作成者が提供しているサポート オプションが表示されます。 専用サイトを持つプロジェクトは、一般的に、よりよくサポートされています。

- *開発者履歴*: パッケージ ページの **[所有者]** で、所有者を選択すると、発行済みの他のパッケージが表示されます。 複数のパッケージがある場合、今後も継続的に作業がサポートされる可能性が高くなります。

- *オープン ソース コントリビューション*: 多くのパッケージはオープン ソース リポジトリに保持されます。これにより、パッケージに依存する開発者は、直接バグの修正と機能の向上に貢献できます。 また、任意のパッケージのコントリビューション履歴を見れば、どれだけ多くの開発者が積極的に関与しているかがよくわかります。

- *所有者へのインタビュー*: 新しい開発者は確実に、あなたが使用する優れたパッケージを生成することに同等にコミットできます。NuGet エコシステムに新しい何かをもたらすよい機会となります。 この点を考慮して、リスト ページの **[情報]** にある **[Contact Owners]\(所有者に問い合わせる\)** オプションを介してパッケージ開発者に直接連絡します。 おそらく、所有者はあなたのニーズに応えるために喜んで協力してくれることでしょう。

- *予約されているパッケージ ID プレフィックス*: 多くのパッケージ所有者が[パッケージ ID プレフィックスの予約](../nuget-org/id-prefix-reservation.md)を申請し、与えられています。 [nuget.org](https://www.nuget.org/) または Visual Studio でパッケージ ID の隣にチェックマークが表示されている場合、それはパッケージ所有者が ID プレフィックス予約に関する Microsoft の[条件](../nuget-org/id-prefix-reservation.md#id-prefix-reservation-criteria)を満たしていることを意味します。 パッケージ所有者は、自身とパッケージの同一性確認に成功しています。

> [!Note]
> 常にパッケージのライセンス条項に留意してください。これは、nuget.org のパッケージのリスト ページにある **[ライセンス情報]** を選択することで確認できます。パッケージでライセンス条項が指定されていない場合は、パッケージ ページの **[Contact owners]\(所有者に問い合わせる\)** リンクを使用して、パッケージ所有者に直接問い合わせてください。 Microsoft はサードパーティのパッケージ プロバイダーを通じてユーザーに知的財産ライセンスを付与することはありません。また、サードパーティによって提供される情報について責任を負いません。

## <a name="license-url-deprecation"></a>ライセンス URL の非推奨
[licenseUrl](../reference/nuspec.md#licenseurl) から [license](../reference/nuspec.md#license) への移行に従い、一部の NuGet クライアントや NuGet フィードでは、場合によってはまだライセンス情報を表示できない可能性があります。 下位互換性を維持するために、ライセンス URL の指定先は、このような場合にライセンス情報を取得する方法について説明しているこのドキュメントとなります。

パッケージのライセンス URL をクリックしてこのページに移動してきた場合、そのパッケージにはライセンス ファイルが含まれていて、また次が該当します。
* 新しいライセンス情報を解釈してクライアントに表示する方法をまだ把握していないフィードに接続している、**または**
* フィードによって提供される可能性のある新しいライセンス情報を解釈して読み取る方法をまだ把握していないクライアントを使用している、**または**
* 両方の組み合わせ

パッケージ内のライセンス ファイルに含まれている情報を読み取る方法は次のとおりです。
1. NuGet パッケージをダウンロードし、その内容をフォルダーに解凍します。
1. そのフォルダーのルートにある `.nuspec` ファイルを開きます。
1. これは `<license type="file">license\license.txt</license>` のようなタグを含んでいます。 これは、ライセンス ファイルが `license.txt` と名付けられ、同様にそのフォルダーのルートにある `license` というフォルダー内にあることを意味しています。
1. `license` フォルダーに移動して `license.txt` ファイルを開きます。

`.nuspec` でライセンスを設定することと同じことを MSBuild で行う方法については、「[ライセンス式またはライセンスファイルのパッキング](../reference/msbuild-targets.md#packing-a-license-expression-or-a-license-file)」を参照してください。

## <a name="search-syntax"></a>検索構文

NuGet パッケージ検索は、nuget.org、NuGet CLI、Visual Studio の NuGet パッケージ マネージャー拡張機能で同じように動作します。 一般に、検索はキーワードとパッケージの説明に適用されます。

- **フィルタリング**: 構文 `<property>:<term>` (この `<property>` (大文字と小文字を区別しない) に `id`、`packageid`、`version`、`title`、`tags`、`author`、`description`、`summary`、`owner` を指定することができます) を使用して、特定のプロパティに検索用語を適用することができます。 複数のプロパティを同時に検索することができます。 `id` プロパティの検索が部分文字列一致であるのに対して、`packageid` および `owner` では大文字と小文字を区別しない完全一致が使用されます。 次に例を示します。

```
PackageId:jquery             # Match the package ID in an exact, case-insensitive manner

owner:microsoft              # Match the owner in an exact, case-insensitive manner

id:NuGet.Core                # Match any part of the ID property
Id:"Nuget.Core"
ID:jQuery
id:jquery id:ui              # Search for multiple terms in the ID
id:jquery tags:validation    # Search multiple properties

invalid:jquery ui            # Unsupported properties are ignored, so this
                             # is the same as searching on ui
```
