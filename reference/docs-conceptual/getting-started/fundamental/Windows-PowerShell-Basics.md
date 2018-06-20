---
ms.date: 06/05/2017
keywords: PowerShell, コマンドレット
title: Windows PowerShell の基礎
ms.assetid: 6b3cbbc8-060c-4877-b00b-7300dbbe4e28
ms.openlocfilehash: b21c6cd84ea29d5e8085ccf8df2a5a9199e1d859
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950536"
---
# <a name="windows-powershell-basics"></a>Windows PowerShell の基礎
グラフィカル ユーザー インターフェイスでは、ほとんどのコンピューターのユーザーによく知られているいくつかの基本的な概念を使用します。 ユーザーはタスクを実行する際、なじみのあるインターフェイスに依存します。 オペレーティング システムは閲覧可能な項目のグラフィック表示をユーザーに提示しますが、これには通常、特定の機能にアクセスするためのドロップダウン メニューと、コンテキスト特有の機能にアクセスするためのコンテキスト メニューが含まれています。

Windows PowerShell などのコマンド ライン インターフェイス (CLI) にはユーザーを支援するメニューやグラフィカル システムがないため、情報を表示するための別のアプローチを使用する必要があります。 コマンドを使用するには、その名前を把握しておく必要があります。 GUI 環境の機能と等価の複雑なコマンドを入力することはできますが、一般的なコマンドとコマンド パラメーターをよく理解する必要があります。

ほとんどの CLI には、インターフェイスについてユーザーが学ぶのに役立つパターンがありません。 CLI は最初のオペレーティング システム シェルだったため、多くのコマンド名とパラメーター名は任意に選ばれました。 一般に、明快さよりも簡潔さを旨としてコマンド名が選ばれました。 大部分の CLI にはヘルプ システムとコマンド設計標準が組み込まれていますが、一般に最初期のコマンドとの互換性を保つ設計になっているため、コマンド セットは今も数十年前の決定によって形作られているのが現状です。

Windows PowerShell の設計は、ユーザーが持つ CLI の歴史的知識を生かすものです。 この章では、Windows PowerShell について素早く学習するために使用できる基本的なツールと概念を説明します。 具体的な内容を次に示します。

- [Get-Command](/powershell/module/Microsoft.PowerShell.Core/get-command) の使用

- [Cmd.exe](/windows-server/administration/windows-commands/cmd) および [UNIX コマンド](/windows/wsl/reference)の使用

- [Tab-Completion の使用](../../core-powershell/console/using-tab-expansion.md)

- [Get-Help の使用](./getting-detailed-help-information.md)