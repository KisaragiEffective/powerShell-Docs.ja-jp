---
title: GetProc02 (C#) Sample Code |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: 5989b1e7030375b1bacdd9b82c25c1a8288fd637
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360371"
---
# <a name="getproc02-c-sample-code"></a>GetProc02 (C#) サンプル コード

次のコードは、コマンドライン入力を受け入れる `Get-Process` コマンドレットの実装を示しています。 この実装では、コマンドライン入力を許可する `Name` パラメーターを定義し、 [WriteObject (system.object, system.string)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)メソッドを出力機構として使用して、パイプラインに出力オブジェクトを送信することに注意してください。

## <a name="code-sample"></a>コードサンプル

[!code-csharp[GetProcessSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a>関連項目

[Windows PowerShell SDK](../windows-powershell-reference.md)
