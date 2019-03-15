---
title: ValidateCount 属性の宣言 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 4e0be34b6f7a56dcf02a4381de4d2a5d08db14df
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794445"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="682d7-102">ValidateCount 属性の宣言</span><span class="sxs-lookup"><span data-stu-id="682d7-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="682d7-103">ValidateCount 属性には、コマンドレット パラメーターの許可されている引数の最小値と最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="682d7-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="682d7-104">構文</span><span class="sxs-lookup"><span data-stu-id="682d7-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="682d7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="682d7-105">Parameters</span></span>

<span data-ttu-id="682d7-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) が必要です。</span><span class="sxs-lookup"><span data-stu-id="682d7-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="682d7-107">引数の最小数を指定します。</span><span class="sxs-lookup"><span data-stu-id="682d7-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="682d7-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) が必要です。</span><span class="sxs-lookup"><span data-stu-id="682d7-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="682d7-109">引数の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="682d7-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="682d7-110">コメント</span><span class="sxs-lookup"><span data-stu-id="682d7-110">Remarks</span></span>

- <span data-ttu-id="682d7-111">この属性を宣言する方法の詳細については、次を参照してください。[入力検証規則の宣言方法](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)します。</span><span class="sxs-lookup"><span data-stu-id="682d7-111">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="682d7-112">この属性がない呼び出されると、コマンドレットの対応するパラメーターに任意の数の引数のことができます。</span><span class="sxs-lookup"><span data-stu-id="682d7-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="682d7-113">Windows PowerShell ランタイムには、次の条件下でエラーがスローされます。</span><span class="sxs-lookup"><span data-stu-id="682d7-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="682d7-114">`MinLength`と`MaxLength`型の属性のパラメーターがない[System.Int32](/dotnet/api/System.Int32)します。</span><span class="sxs-lookup"><span data-stu-id="682d7-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32](/dotnet/api/System.Int32).</span></span>

    - <span data-ttu-id="682d7-115">値、`MaxLength`属性パラメーターは、の値より小さい、`MinLength`属性パラメーター。</span><span class="sxs-lookup"><span data-stu-id="682d7-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="682d7-116">ValidateCount 属性を定義した、 [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount)クラス。</span><span class="sxs-lookup"><span data-stu-id="682d7-116">The ValidateCount attribute is defined by the [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="682d7-117">参照</span><span class="sxs-lookup"><span data-stu-id="682d7-117">See Also</span></span>

[<span data-ttu-id="682d7-118">System.Management.Automation.Validatecount</span><span class="sxs-lookup"><span data-stu-id="682d7-118">System.Management.Automation.Validatecount</span></span>](/dotnet/api/System.Management.Automation.ValidateCount)

[<span data-ttu-id="682d7-119">入力の検証規則を宣言する方法</span><span class="sxs-lookup"><span data-stu-id="682d7-119">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="682d7-120">Windows PowerShell コマンドレットの記述</span><span class="sxs-lookup"><span data-stu-id="682d7-120">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)