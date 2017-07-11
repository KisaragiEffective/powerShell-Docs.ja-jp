---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, PowerShell, セットアップ"
ms.openlocfilehash: 28da6d12d3f7a59777425e1cc4531a609a793ddb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
<a id="call-base-class-method" class="xliff"></a>

# 基本クラス メソッドの呼び出し

サブクラスで既存のメソッドをオーバーライドすることができます。 そのためには、同じ名前およびシグネチャを使用してメソッドを宣言します。

```PowerShell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

オーバーライドされた実装から基本クラス メソッドを呼び出すには、呼び出し時に基本クラスにキャストします ([baseClass]$this)。

```PowerShell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

すべての PowerShell メソッドは仮想です。 オーバーライドの場合と同じ構文を使用して、サブクラスで非仮想 .NET メソッドを非表示にできます。同じ名前およびシグネチャを持つメソッドを宣言するだけです。

```PowerShell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

