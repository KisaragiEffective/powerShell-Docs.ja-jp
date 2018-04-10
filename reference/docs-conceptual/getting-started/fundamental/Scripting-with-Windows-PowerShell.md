---
ms.date: 06/05/2017
keywords: PowerShell, コマンドレット
title: Windows PowerShell を使用したスクリプト
ms.assetid: c425d27a-bb41-4947-8d73-ba5480bc8ee0
ms.openlocfilehash: 9bb420a3d725d3fa925b79452bbbcc542bf9f4db
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2018
---
# <a name="scripting-with-windows-powershell"></a>Windows PowerShell を使用したスクリプト

Windows PowerShell® は、システム管理に重点を置いて設計されたタスクベースのコマンド ライン シェルおよびスクリプト言語です。 .NET Framework 上に構築された Windows PowerShell は、IT 技術者およびパワー ユーザーが Windows オペレーティング システムと Windows 上で実行するアプリケーションの管理の自動化を制御するときに役立ちます。

*コマンドレット*と呼ばれる Windows PowerShell コマンドを使用すると、コマンド ラインからコンピューターを管理できます。 Windows PowerShell の*プロバイダー*を使用すると、レジストリや証明書ストアなどのデータ ストアに、ファイル システムにアクセスするのと同じくらい簡単にアクセスすることができます。 さらに、Windows PowerShell には、豊富な式パーサーと、完全に開発されたスクリプト言語があります。

Windows PowerShell には、次に示す機能があります。

- レジストリ、サービス、プロセス、およびイベント ログの管理、Windows Management Instrumentation (WMI) の使用など、一般的なシステム管理タスクを実行するコマンドレットです。
- 既存のスクリプトおよびコマンド ライン ツール用のタスク ベースのスクリプト言語およびサポートです。
- 一貫した設計。 コマンドレットとシステム データ ストアは、共通の構文と命名規則を使用しているため、データを簡単に共有できるとともに、1 つのコマンドレットからの出力を、再フォーマットや操作を実行することなく別のコマンドレットへの入力として使用できます。
- ユーザーがファイル システムの移動に使用するのと同じ手法を使用してレジストリおよびその他のデータ ストアを移動できるようにする、オペレーティング システムの簡略化されたコマンドベースのナビゲーションです。
- 強力なオブジェクト操作機能です。 オブジェクトを直接操作したり、その他のツールやデータベースに送信したりすることができます。
- 拡張可能なインターフェイスです。 独立系ソフトウェア ベンダーや企業の開発者は、自社のソフトウェアを管理するカスタム ツールとユーティリティをビルドできます。