---
ms.date: 06/05/2017
keywords: PowerShell, コマンドレット
title: PowerShell スクリプト
ms.openlocfilehash: 7de5a3f3149d8d464b34101d94a5f9430d9b0f23
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="powershell"></a>PowerShell

PowerShell は、システム管理者とパワーユーザー向けに .NET Framework 上に構築されたタスクベースのコマンドライン シェルとスクリプト言語であり、複数のオペレーティング システム (Linux、macOS、Unix、Windows) の管理とこれらのオペレーティング システム上で実行されるアプリケーションに関連するプロセスを迅速に自動化するものです。

## <a name="powershell-is-open-source"></a>PowerShell はオープン ソースです

PowerShell ベースのソース コードは現在、GitHub で入手可能であり、コミュニティ投稿が可能です。 [GitHub の PowerShell のソース](https://github.com/powershell/powershell)を参照してください。

「[PowerShell を入手](https://github.com/PowerShell/PowerShell#get-powershell)」で必要なものから開始できます。
または、「[はじめに](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)」からクイック ツアーを開始します。

## <a name="powershell-design-goals"></a>PowerShell の設計目標
Windows PowerShell は、従来からの問題を排除し、新しい機能を追加することにより、コマンド ラインおよびスクリプト環境を改善することを目的として設計されています。

### <a name="discoverability"></a>機能の見つけやすさ
Windows PowerShell では、簡単にその機能を見つけられます。 たとえば、Windows サービスを表示したり変更したりするコマンドレットの一覧を検索するには、次のように入力します。

```powershell
Get-Command *-Service
```

タスクを実行するコマンドレットが見つかったら、Get-Help コマンドレットを使用して、コマンドレットの詳細を確認することができます。 たとえば、Get-Service コマンドレットのヘルプを表示するには、次のように入力します。

```powershell
Get-Help Get-Service
```
ほとんどのコマンドレットでは、操作を加えてから表示用のテキストに変換できるオブジェクトが出力されます。 そのコマンドレットの出力を完全に理解するには、Get-Member コマンドレットにその出力をパイプ処理します。 たとえば、次のコマンドは、Get-Service コマンドレットによって出力されるオブジェクトのメンバーについての情報を表示します。

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Consistency
システム管理は複雑な作業になる場合があります。一貫性のあるインターフェースを備えたツールを使用することで、システム管理に特有の複雑な作業を制御しやすくなります。 残念ながら、コマンド ライン ツールもスクリプト可能な COM オブジェクトも一貫性に優れてはいません。

Windows PowerShell の持つ一貫性は、その主要な利点の 1 つです。 たとえば、Sort-Object コマンドレットの使用法を習得すると、その知識を使用して、あらゆるコマンドレットの出力を並べ替えることができます。 コマンドレットごとに異なる並べ替えルーチンを習得する必要はありません。

さらに、コマンドレットの開発者は、コマンドレットの並べ替え機能を設計する必要はありません。 Windows PowerShell は、基本的な機能を備えたフレームワークをコマンドレット開発者に提供し、インターフェイスの多くの側面について一貫性が維持されるよう開発者に強制します。 このフレームワークにより、通常は開発者に委ねられる選択の一部が減ることになりますが、その代わり、堅牢かつ使いやすいコマンドレットの開発がより簡単に実行できるようになります。

### <a name="interactive-and-scripting-environments"></a>対話型環境とスクリプト環境
Windows PowerShell は、対話型環境とスクリプト環境を組み合わせた環境であり、コマンド ライン ツールと COM オブジェクトへのアクセスを提供するだけでなく、.NET Framework クラス ライブラリ (FCL) の強力な機能を使用できるようにします。

この環境は Windows コマンド プロンプトを改良したもので、複数のコマンド ライン ツールを備えた対話型環境を提供します。 またそれは、Windows Script Host (WSH) スクリプトを改良したものでもあります。WSH では、さまざまなコマンドライン ツールや COM オートメーション オブジェクトを利用できますが、対話型の環境は用意されていません。

Windows PowerShell では、これらのすべての機能へのアクセスを統合することで、対話型環境のユーザーとスクリプト作成者の作業能力を向上させ、システム管理をより容易に行うことができます。

### <a name="object-orientation"></a>オブジェクト指向
Windows PowerShell との対話はコマンドをテキストで入力して行いますが、Windows PowerShell は、テキストではなくオブジェクトに基づいています。 コマンドの出力は、オブジェクトです。 出力されたオブジェクトは、別のコマンドの入力として渡すことができます。 その結果、Windows PowerShell は、新しい強力なコマンド ライン パラダイムを導入すると同時に、他のシェルを利用してきたユーザーにとって使い慣れたインターフェイスを提供することができます。 Windows PowerShell では、テキストではなくオブジェクトを渡せるようにすることで、コマンド間でデータを送信するという概念が拡張されています。

### <a name="easy-transition-to-scripting"></a>スクリプトへの移行が容易
Windows PowerShell では、対話的なコマンドの入力から、それを基にしたスクリプトの作成および実行に容易に移行できます。 Windows PowerShell コマンド プロンプトでコマンドを入力することにより、タスクを実行するコマンドを見つけることができます。 見つかったコマンドはトランスクリプト (履歴) に保存し、後でスクリプトとして使用するためにファイルにコピーできます。
