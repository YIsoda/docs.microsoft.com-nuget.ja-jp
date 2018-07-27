---
title: NuGet 3.0 RC のリリース ノートには
description: 既知の問題、バグの修正、追加された機能、および Dcr を含む NuGet 3.0 RC のリリース ノートします。
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 11/11/2016
ms.topic: conceptual
ms.openlocfilehash: 28ac49d9e9071d16d20b24808abb0acaab214ffd
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31819599"
---
# <a name="nuget-30-rc-release-notes"></a>NuGet 3.0 RC のリリース ノートには

[NuGet 3.0 Beta リリース ノート](../release-notes/nuget-3.0-beta.md) | [NuGet 3.0 RC2 リリース ノート](../release-notes/nuget-3.0-RC2.md)

NuGet 3.0 RC は、Visual Studio 2015 RC のリリースでは、2015 年 4 月 29 日にリリースされました。 このリリースでは重要なバグ修正、パフォーマンスの向上、および新しいフレームワークをサポートするために更新プログラムの数。  Visual Studio 2015 のできるだけです。

### <a name="continued-focus-on-performance"></a>継続的なパフォーマンス重視

安定性と NuGet のクエリのパフォーマンスに焦点を当てたおをホット トピックし続けます。  このリリースでは、NuGet UI や web サイトでの非常に高速検索操作を参照してくださいを開始する必要があります。  サービスとこれらの操作を調整することを続行するために、サービスを使用する方法を監視しています。

## <a name="significant-issues-resolved"></a>重要な問題の解決

NuGet クライアントを安定化するために、このリリースの一部としての多くの問題を解決します。  いくつかの解決より重要な問題の簡単な一覧を次に示します。

* Dnx および dnxcore を処理する更新されたフレームワーク モニカーの ASP.NET 5 K、フレームワークの名前の変更の一環として、[リンク](https://github.com/NuGet/Home/issues/215)
* Visual Studio UI 内のリンクからヘルプ ドキュメントを追加[リンク](https://github.com/NuGet/Home/issues/232)
* 複雑な参照の処理の改善`.nuspec`カンマ区切りのフレームワーク参照を含む[リンク](https://github.com/NuGet/Home/issues/276)
* 日本語のカルチャのサポートを固定[リンク](https://github.com/NuGet/Home/issues/253)
* ASP.NET 5 プロジェクトの新しい v3 エンドポイントの使用を許可する更新されたクライアント[リンク](https://github.com/NuGet/Home/issues/219)
* ソース コントロールのハンドルをより効率的に更新されたパッケージ フォルダー[リンク](https://github.com/NuGet/Home/issues/56)
* サテライトのパッケージのサポートを固定[リンク](https://github.com/NuGet/Home/issues/17)
* フレームワーク固有のコンテンツ ファイルのサポートを修正[リンク](https://github.com/NuGet/Home/issues/18)

## <a name="github-presence-overhaul"></a>GitHub プレゼンスの修理

いくつかの変更を加えられた、 [GitHub でコード リポジトリのソース](http://github.com/nuget/home)です。  NuGet の Visual Studio クライアント、Powershell コマンドまたはコマンドラインで問題があれば実行可能それらの問題をログおよび監視できますその進行状況で、[ホームの GitHub リポジトリの問題一覧](http://github.com/nuget/home/issues)です。  ギャラリー内の問題を追跡して、 [GitHub NuGetGallery リポジトリ](http://github.com/nuget/NuGetGallery/issues)です。


## <a name="stay-tuned"></a>待ち

くださいに注意[私たちのブログ](http://blog.nuget.org)の詳細の進行状況と NuGet 3.0 のお知らせください。