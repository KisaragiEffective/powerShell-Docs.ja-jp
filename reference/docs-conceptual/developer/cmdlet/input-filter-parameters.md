---
title: 入力フィルターパラメーター |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 7a1582031d27f78bad069f5539408312ccabb3f2
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563870"
---
# <a name="input-filter-parameters"></a>入力フィルターのパラメーター

コマンドレットでは `Filter` 、 `Include` `Exclude` コマンドレットが影響する入力オブジェクトのセットをフィルター処理する、、およびパラメーターを定義できます。

通常、入力オブジェクトのセットは `InputObject` 、、 `Path` 、またはパラメーターによって指定され `Name` ます。 たとえば、コマンドレットは、ワイルドカード文字を使用して複数のパスを受け取るパラメーターを持つことができ、 `Path` 各パスは入力オブジェクトを指します。 、、およびの `Filter` `Include` 各パラメーターは、コマンドレットが呼び出されるたび `Exclude` に機能するパスをさらに修飾します。

## <a name="include-and-exclude-parameters"></a>Include パラメーターと Exclude パラメーター

`Include`パラメーターと `Exclude` パラメーターは、コマンドレットに渡された入力オブジェクトのセットに含まれる、または除外されるオブジェクトを識別します。 フィルターを標準のワイルドカード言語で表現できる場合は、これらのパラメーターを使用します。 (ワイルドカード文字の詳細については、「[コマンドレットパラメーターでのワイルドカードのサポート](./supporting-wildcard-characters-in-cmdlet-parameters.md)」を参照してください)。パラメーターには、 `Include` 包含フィルターに一致する名前を持つすべてのオブジェクトが含まれます。 パラメーターには、 `Exclude` フィルターに一致する名前を持つすべてのオブジェクトが除外されます。

## <a name="filter-parameter"></a>フィルターパラメーター

パラメーターは、 `Filter` 標準のワイルドカード言語で表されないフィルターを指定します。 たとえば、パラメーターを使用して、Active Directory サービスインターフェイス (ADSI) または SQL フィルターをコマンドレットに渡すことができ `Filter` ます。 Windows PowerShell によって提供されるコマンドレットでは、これらのフィルターは、コマンドレットを使用してデータストアにアクセスする Windows PowerShell プロバイダーによって指定されます。 各プロバイダーは、通常、独自のフィルターを定義します。

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>入力オブジェクトのセットが指定されていない場合のフィルター処理

入力オブジェクトのセットが指定されていない場合、これは通常、すべてのオブジェクトに対してフィルター処理を行うことを意味します。 詳細については、「[Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)」を参照してください。

## <a name="see-also"></a>参照

[Writing a Windows PowerShell Cmdlet (Windows PowerShell コマンドレットの記述)](./writing-a-windows-powershell-cmdlet.md)
