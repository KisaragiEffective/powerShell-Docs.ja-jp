---
ms.date: 08/25/2017
keywords: powershell,コマンドレット
title: ObjectModelRoot オブジェクト
ms.openlocfilehash: cd94e69de2e62f7ce9fac413e15458ae9986540e
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809568"
---
# <a name="the-objectmodelroot-object"></a>ObjectModelRoot オブジェクト

Windows PowerShell® Integrated Scripting Environment (ISE) のプリンシパル ルート オブジェクトである `$psISE` オブジェクトは、Microsoft.PowerShell.Host.ISE.ObjectModelRoot クラスのインスタンスです。 このトピックでは、**ObjectModelRoot** オブジェクトのプロパティについて説明します。

## <a name="properties"></a>Properties

### <a name="currentfile"></a>CurrentFile

> Windows PowerShell ISE 2.0 以降でサポートされています。

現在フォーカスしているこのホスト オブジェクトに関連付けられているファイルを取得する読み取り専用のプロパティ。

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> Windows PowerShell ISE 2.0 以降でサポートされています。

フォーカスしている PowerShell タブを取得する読み取り専用のプロパティ。

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> Windows PowerShell ISE 2.0 以降でサポートされています。

エディターの下部にある水平方向のツール ウィンドウに現在表示されている Windows PowerShell ISE アドオン ツールを取得する読み取り専用のプロパティ。

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> Windows PowerShell ISE 2.0 以降でサポートされています。

エディターの右側にある垂直方向のツール ウィンドウに現在表示されている Windows PowerShell ISE アドオン ツールを取得する読み取り専用のプロパティ。

### <a name="options"></a>Options

> Windows PowerShell ISE 2.0 以降でサポートされています。

Windows PowerShell ISE の設定を変更することができるさまざまなオプションを取得する読み取り専用のプロパティ。

### <a name="powershelltabs"></a>PowerShellTabs

> Windows PowerShell ISE 2.0 以降でサポートされています。

Windows PowerShell ISE で開かれている PowerShell タブのコレクションを取得する読み取り専用のプロパティ。 既定では、このオブジェクトには 1 つの PowerShell タブが含まれています。ただし、スクリプトまたは Windows PowerShell ISE のメニューを使用して、このオブジェクトに他の PowerShell タブを追加することができます。

## <a name="see-also"></a>参照

- [Windows PowerShell ISE スクリプト オブジェクト モデルの目的](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE オブジェクト モデルの階層](The-ISE-Object-Model-Hierarchy.md)
