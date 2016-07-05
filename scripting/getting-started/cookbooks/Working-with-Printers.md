---
title: "プリンターの操作"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 27d3d11b71b95cd79817449cf8bdb1a0a26936bd

---

# プリンターの操作
Windows PowerShell を使用してプリンターを管理するには、WMI を使用する方法と WSH から WScript.Network COM オブジェクトを使用する方法があります。 ここでは、両方のツールを組み合わせて使用して、特定のタスクの実行方法を紹介します。

### プリンター接続の一覧表示
コンピューターにインストールされているプリンターを一覧表示する最も簡単な方法は、WMI の **Win32\_Printer** クラスを使用することです。

```
Get-WmiObject -Class Win32_Printer -ComputerName
```

**WScript.Network** という COM オブジェクト (通常、WSH スクリプトで使用されます) を使用してプリンターを一覧表示することもできます。

```
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

このコマンドは、ポート名とプリンター デバイス名の単純な文字列コレクションを返し、識別に役立つラベルがないため、分かりにくい場合があります。

### ネットワーク プリンターの追加
新しいネットワーク プリンターを追加するには、**WScript.Network** を使用します。

```
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### 通常使うプリンターの設定
通常使うプリンターを WMI を使用して設定するには、**Win32\_Printer** コレクションでプリンターを検索し、**SetDefaultPrinter** メソッドを呼び出します。

```
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** の方が多少簡単に使用できます。これは、プリンター名のみを引数として取る **SetDefaultPrinter** メソッドを備えているためです。

```
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### プリンター接続の削除
プリンター接続を削除するには、**WScript.Network RemovePrinterConnection** メソッドを使用します。

```
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```




<!--HONumber=Jun16_HO4-->


