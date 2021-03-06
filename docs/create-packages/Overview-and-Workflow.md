---
title: NuGet パッケージの作成の概要とワークフロー
description: NuGet パッケージの作成と発行プロセスの概要と、プロセスの他の特定の部分へのリンク。
author: karann-msft
ms.author: karann
ms.date: 07/26/2017
ms.topic: conceptual
ms.openlocfilehash: e4b9f6dae3a4be69e523888cc9bd2f212b45829c
ms.sourcegitcommit: 2b50c450cca521681a384aa466ab666679a40213
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2020
ms.locfileid: "69488845"
---
# <a name="package-creation-workflow"></a>パッケージ作成ワークフロー

パッケージの作成はコンパイル済みコード (通常は .NET アセンブリ) から始めます。このコードはパッケージ化して、パブリック nuget.org ギャラリーまたは組織内のプライベート ギャラリーを通じて他のユーザーと共有します。 パッケージには、パッケージのインストール時に表示される Readme などの追加ファイルを含めることができます。また、特定のプロジェクト ファイルへの変換を含めることもできます。

パッケージは、独自のコードを含めずに、任意の数の他の依存関係にプルする場合にも対応できます。 このようなパッケージは、複数の独立したパッケージで構成される SDK を配信する便利な方法です。 その他の場合、パッケージにはデバッグを支援するシンボル (`.pdb`) ファイルのみを含めることができます。

> [!Note]
> 他の開発者が使用するパッケージを作成する場合は、他の開発者が自分の作業に依存していることを理解することが重要です。 したがって、パッケージの作成と発行は、バグの修正とその他の更新を行うことへのコミットメントも意味します。また、容易に保持できるように、少なくともパッケージをオープン ソースとして使用できるようにすることへのコミットメントも意味します。

どのような場合でも、パッケージの作成は、その識別子、バージョン番号、ライセンス、著作権情報、およびその他の必要なコンテンツを決定することから始まります。 完了したら、"pack" コマンドを使ってそれらすべてを 1 つの `.nupkg` ファイルにまとめることができます。 このファイルは、nuget.org などの NuGet フィードに公開することができます。

> [!Tip]
> `.nupkg` 拡張子を持つ NuGet パッケージは単なる ZIP ファイルです。 パッケージの内容を簡単に確認するには、拡張子を `.zip` に変更し、その内容を通常どおり展開します。 念のため、ホストへのアップロードを試行する前に拡張子を `.nupkg` に戻してください。

作成プロセスを学習して理解するために、まず、「[Creating a package](../create-packages/creating-a-package.md)」 (パッケージの作成) を参照してください。ここでは、すべてのパッケージに共通の中核となるプロセスについて説明されています。

そこから、パッケージの他の多くのオプションを検討することができます。

- 「[Supporting Multiple Target Frameworks](../create-packages/supporting-multiple-target-frameworks.md)」 (複数のターゲット フレームワークのサポート) では、さまざまな .NET Framework の複数のバリアントを含むパッケージを作成する方法が説明されています。
- 「[Creating Localized Packages](../create-packages/creating-localized-packages.md)」 (ローカライズされたパッケージの作成) では、複数の言語リソースを含むパッケージを構築する方法と、個別のローカライズされたサテライト パッケージを使用する方法が説明されています。
- 「[Pre-release Packages](../create-packages/prerelease-packages.md)」 (プレリリース パッケージ) では、アルファ、ベータ、rc パッケージをそれらに関心のあるユーザー向けにリリースする方法が示されています。
- 「[Source and Config File Transformations](../create-packages/source-and-config-file-transformations.md)」 (ソースと構成ファイルの変換) では、プロジェクトに追加されたファイルでの一方向のトークン置換を実行する方法と、パッケージのアンインストール時に取り消すこともできる設定を使用して `web.config` と `app.config` を変更する方法が説明されています。
- 「[Symbol Packages](../create-packages/symbol-packages-snupkg.md)」 (シンボル パッケージ) では、コンシューマーがデバッグ時にコードにステップ インできるように、ライブラリでシンボルを提供するためのガイダンスが提供されています。
- 「[Package versioning](../concepts/package-versioning.md)」 (パッケージのバージョン管理) では、依存関係 (自分のパッケージから利用する他のパッケージ) がある場合に使用できる正確なバージョンを特定する方法が説明されています。
- 「[Native Packages](../guides/native-packages.md)」 (ネイティブ パッケージ) では、C++ コンシューマー用のパッケージの作成プロセスが説明されています。
- 「[Signing Packages](../create-packages/sign-a-package.md)」(パッケージの署名) では、パッケージにデジタル署名を追加するプロセスが説明されています。

nuget.org にパッケージを発行する準備ができたら、「[Publish a package](../nuget-org/publish-a-package.md)」 (パッケージの発行) の簡単なプロセスに従います。

nuget.org ではなくプライベート フィードを使用する場合は、[パッケージのホスティングの概要](../hosting-packages/overview.md)に関するページを参照してください。
