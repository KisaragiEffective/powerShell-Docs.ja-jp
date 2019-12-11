---
ms.date: 06/05/2017
keywords: PowerShell, コマンドレット
title: ISESnippetObject
ms.openlocfilehash: 62d470569deb051fca80005235d4c492319cf5ec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "67028894"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="898f4-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="898f4-103">The ISESnippetObject</span></span>

<span data-ttu-id="898f4-104">**ISESnippet** オブジェクトは、Microsoft.PowerShell.Host.ISE.ISESnippet クラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="898f4-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="898f4-105">**$psISE.CurrentPowerShellTab.Snippets** コレクションのメンバーは、すべて **ISESnippet** オブジェクトの例です。</span><span class="sxs-lookup"><span data-stu-id="898f4-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="898f4-106">スニペットを作成する最も簡単な方法として、[New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="898f4-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="898f4-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="898f4-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="898f4-108">作成者</span><span class="sxs-lookup"><span data-stu-id="898f4-108">Author</span></span>

<span data-ttu-id="898f4-109">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="898f4-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="898f4-110">スニペットの作成者名を取得する読み取り専用プロパティ。</span><span class="sxs-lookup"><span data-stu-id="898f4-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="898f4-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="898f4-111">CodeFragment</span></span>

<span data-ttu-id="898f4-112">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="898f4-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="898f4-113">エディターに挿入するコード フラグメントを取得する読み取り専用プロパティ。</span><span class="sxs-lookup"><span data-stu-id="898f4-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="898f4-114">Shortcut</span><span class="sxs-lookup"><span data-stu-id="898f4-114">Shortcut</span></span>

<span data-ttu-id="898f4-115">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="898f4-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="898f4-116">メニュー項目の Windows ショートカット キーを取得する読み取り専用プロパティ。</span><span class="sxs-lookup"><span data-stu-id="898f4-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="898f4-117">参照</span><span class="sxs-lookup"><span data-stu-id="898f4-117">See Also</span></span>

- [<span data-ttu-id="898f4-118">ISESnippetCollection オブジェクト</span><span class="sxs-lookup"><span data-stu-id="898f4-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="898f4-119">Windows PowerShell ISE スクリプト オブジェクト モデルの目的</span><span class="sxs-lookup"><span data-stu-id="898f4-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="898f4-120">ISE オブジェクト モデルの階層</span><span class="sxs-lookup"><span data-stu-id="898f4-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
