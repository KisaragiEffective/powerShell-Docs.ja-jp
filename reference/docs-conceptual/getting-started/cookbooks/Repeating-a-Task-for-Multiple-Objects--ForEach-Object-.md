---
ms.date: 06/05/2017
keywords: PowerShell, コマンドレット
title: 複数のオブジェクトのタスクを繰り返す (ForEach-Object)
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 64d85edad4a6931b2376b95b6d1f5b4d5194399f
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587263"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>複数のオブジェクトのタスクを繰り返す (ForEach-Object)

**ForEach-Object** コマンドレットは、現在のパイプライン オブジェクトのスクリプト ブロックと `$_` 記述子を使用して、パイプライン内の各オブジェクトのコマンドを実行できるようにします。 これは、いくつかの複雑なタスクを実行するために使用できます。

これが有用な状況の 1 つは、データをさらに有効活用するよう操作する場合です。 たとえば、WMI からの Win32_LogicalDisk クラスは、各ローカル ディスクの空き領域の情報を返すのに使用できます。 データはバイト単位で返されますが、次のように、読み取るのは困難です。

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

FreeSpace の値を 1024 で 2 回割ると、メガバイト単位に変換できます。最初の除算の後、データはキロバイト単位になり、2 回目の除算の後、メガバイト単位になります。 ForEach-Object のスクリプト ブロックでこのことを実行できます。次のように入力します。

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

残念ながら、出力はラベルとは関連付けられていないデータになります。 この例のように、WMI プロパティは読み取り専用なので、FreeSpace を直接変換することはできません。 次のように入力するとします。

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

次のようなエラー メッセージが表示されます。

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

高度な技法を幾つか使用してデータを再編成できますが、よりシンプルな方法は、**Select-Object** を使用して新しいオブジェクトを作成することです。