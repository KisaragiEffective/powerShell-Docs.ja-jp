---
title: "32 ビット版の Windows PowerShell を起動する"
ms.date: 2016-05-11
keywords: "PowerShell, コマンドレット"
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: e6e9d951b2dd10637bbf2c6afda774cd9ba32a8d
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a>32 ビット版の Windows PowerShell を起動する
64 ビット コンピューターに Windows PowerShell をインストールする場合、64 ビット版に加えて、**Windows PowerShell (x86)**、つまり Windows PowerShell の 32 ビット版もインストールされます。 Windows PowerShell を実行すると、既定では 64 ビット版が実行されます。

ただし、32 ビット版を必要とするモジュールを使用するときや、32 ビットのコンピューターにリモートで接続しているときなど、**Windows PowerShell (x86)** の実行を必要とすることもときどきあります。

Windows PowerShell の 32 ビット版を起動するには、次の手順のいずれかを使用します。

#### <a name="in-windows-server-2012-r2"></a>Windows Server® 2012 R2 の場合

-   **[スタート]** 画面で、「**Windows PowerShell (x86)**」と入力します。 **[Windows PowerShell x86]** タイルをクリックします。

-   **サーバー マネージャー**の **[ツール]** メニューから、**[Windows PowerShell (x86)]** を選択します。

-   デスクトップで、右上隅にカーソルを移動し、**[検索]** をクリックする。「**PowerShell x86**」と入力し、**[Windows PowerShell (x86)]** をクリックします。

-   コマンド ラインで、次のように入力します。`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>Windows Server® 2012 の場合

-   **[スタート]** 画面で、「**PowerShell**」と入力して **[Windows PowerShell (x86)]** をクリックします。

-   **サーバー マネージャー**の **[ツール]** メニューから、**[Windows PowerShell (x86)]** を選択します。

-   デスクトップで、右上隅にカーソルを移動し、**[検索]** をクリックする。「**PowerShell**」と入力し、**[Windows PowerShell (x86)]** をクリックします。

-   コマンド ラインで、次のように入力します。`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>Windows® 8.1 の場合

-   **[スタート]** 画面で、「**Windows PowerShell (x86)**」と入力します。 **[Windows PowerShell x86]** タイルをクリックします。

-   Windows 8.1 の[リモート サーバー管理ツール](http://go.microsoft.com/fwlink/?LinkID=304145)を実行している場合、**[サーバー管理ツール]** メニューから [Windows PowerShell x86] を開くこともできます。 **[Windows PowerShell (x86)]** を選択します。

-   デスクトップで、右上隅にカーソルを移動し、**[検索]** をクリックする。「**PowerShell x86**」と入力し、**[Windows PowerShell (x86)]** をクリックします。
   
-   コマンド ラインで、次のように入力します。`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>In Windows® 8 の場合

-   **[スタート]** 画面で、右上隅にカーソルを移動し、**[設定]** をクリックし、**[タイル]** をクリックします。そして、**[管理ツールを表示する]** スライダーを [はい] に移動させます。 次に「**PowerShell**」と入力し、**[Windows PowerShell(x86)]** をクリックします。

-   Windows 8 の[リモート サーバー管理ツール](http://www.microsoft.com/download/details.aspx?id=28972)を実行している場合、**[サーバー管理ツール]** メニューから [Windows PowerShell x86] を開くこともできます。 **[Windows PowerShell (x86)]** を選択します。

-   **[スタート]** 画面またはデスクトップで、「**PowerShell (x86)**」と入力し、**[Windows PowerShell (x86)]** をクリックします。

-   コマンド ラインで、次のように入力します。`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`
