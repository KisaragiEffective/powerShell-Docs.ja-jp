---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: "PowerShell, コマンドレット"
ms.date: 2016-12-12
title: "オブジェクトの並べ替え"
ms.technology: powershell
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 00ee71337331c730f37723152175e2ca10263191
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="sorting-objects"></a>オブジェクトの並べ替え
**Sort-Object** コマンドレットを使用すると、表示データを見やすく整理できます。 **Sort-Object** では、並べ替え条件としてプロパティ名 (複数可) を指定すると、そのプロパティ値で並べ替えられたデータが返されます。

たとえば、Win32_SystemDriver のインスタンスを一覧表示する場合を考えてみます。 **State** で並べ替えた後、**Name** で並べ替えるには、次のように入力します。

```
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

多くの情報が表示されるものの、同じ状態の項目がグループ化されていることがわかります。

```
Name           State   Started DisplayName
----           -----   ------- -----------
ACPI           Running    True Microsoft ACPI Driver
AFD            Running    True AFD
AmdK7          Running    True AMD K7 Processor Driver
AsyncMac       Running    True RAS Asynchronous Media Driver
...
Abiosdsk       Stopped   False Abiosdsk
ACPIEC         Stopped   False ACPIEC
aec            Stopped   False Microsoft Kernel Acoustic Echo Canceller
...
```

**Descending** パラメーターを指定して、オブジェクトを降順に並べ替えることもできます。 並べ替え順序が反転され、名前はアルファベットの最後から先に、数字は値の大きい方から先に表示されます。

```
PS> Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name -Descending | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap

Name           State   Started DisplayName
----           -----   ------- -----------
WS2IFSL        Stopped   False Windows Socket 2.0 Non-IFS Service Provider Supp
                               ort Environment
wceusbsh       Stopped   False Windows CE USB Serial Host Driver...
...
wdmaud         Running    True Microsoft WINMM WDM Audio Compatibility Driver
Wanarp         Running    True Remote Access IP ARP Driver
...
```

