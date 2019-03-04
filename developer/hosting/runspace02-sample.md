---
title: Runspace02 サンプル |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7630bb63-ef39-4abd-b795-8000f984c1e5
caps.latest.revision: 9
ms.openlocfilehash: 6352169cffbb8a8bf59a42f79979f5003c150fa4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854288"
---
# <a name="runspace02-sample"></a><span data-ttu-id="e683b-102">Runspace02 サンプル</span><span class="sxs-lookup"><span data-stu-id="e683b-102">Runspace02 Sample</span></span>

<span data-ttu-id="e683b-103">このサンプルは、使用する方法を示します、 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)を実行するクラス、 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)と[Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object)コマンドレット同期的にします。</span><span class="sxs-lookup"><span data-stu-id="e683b-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span> <span data-ttu-id="e683b-104">[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)コマンドレットが返す[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 、ローカル コンピューターで実行されている各プロセス オブジェクトおよび`Sort-Object`に基づいてオブジェクトを並べ替えます、 [System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id)プロパティ。</span><span class="sxs-lookup"><span data-stu-id="e683b-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) property.</span></span> <span data-ttu-id="e683b-105">使用してこれらのコマンドの結果が表示されます、 [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView)コントロール。</span><span class="sxs-lookup"><span data-stu-id="e683b-105">The results of these commands is displayed by using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

## <a name="requirements"></a><span data-ttu-id="e683b-106">要件</span><span class="sxs-lookup"><span data-stu-id="e683b-106">Requirements</span></span>

<span data-ttu-id="e683b-107">このサンプルでは、Windows PowerShell 2.0 が必要です。</span><span class="sxs-lookup"><span data-stu-id="e683b-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e683b-108">使用例</span><span class="sxs-lookup"><span data-stu-id="e683b-108">Demonstrates</span></span>

<span data-ttu-id="e683b-109">このサンプルは、次を示します。</span><span class="sxs-lookup"><span data-stu-id="e683b-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="e683b-110">作成、 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)コマンドを実行するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e683b-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run commands.</span></span>

- <span data-ttu-id="e683b-111">パイプラインにコマンドを追加する[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e683b-111">Adding commands to the pipeline of [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="e683b-112">同期的にコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="e683b-112">Running the commands synchronously.</span></span>

- <span data-ttu-id="e683b-113">使用して、 [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) Windows フォーム アプリケーションでのコマンドの出力を表示するコントロール。</span><span class="sxs-lookup"><span data-stu-id="e683b-113">Using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control to display the output of the commands in a Windows Forms application.</span></span>

## <a name="example"></a><span data-ttu-id="e683b-114">例</span><span class="sxs-lookup"><span data-stu-id="e683b-114">Example</span></span>

<span data-ttu-id="e683b-115">このサンプルの実行、 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)と[Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object)コマンドレットは同期的に Windows PowerShell によって提供される既定の実行空間。</span><span class="sxs-lookup"><span data-stu-id="e683b-115">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="e683b-116">フォームを使用して、出力が表示されます、 [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView)コントロール。</span><span class="sxs-lookup"><span data-stu-id="e683b-116">The output is displayed in a form using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using System.Windows.Forms;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace02
  {
    /// <summary>
    /// This method creates the form where the output is displayed.
    /// </summary>
    private static void CreateForm()
    {
      Form form = new Form();
      DataGridView grid = new DataGridView();
      form.Controls.Add(grid);
      grid.Dock = DockStyle.Fill;

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddCommand("get-process").AddCommand("sort-object").AddArgument("ID");
        if (Runspace.DefaultRunspace == null)
        {
          Runspace.DefaultRunspace = powershell.Runspace;
        }

        Collection<PSObject> results = powershell.Invoke();

        // The generic collection needs to be re-wrapped in an ArrayList
        // for data-binding to work.
        ArrayList objects = new ArrayList();
        objects.AddRange(results);

        // The DataGridView will use the PSObjectTypeDescriptor type
        // to retrieve the properties.
        grid.DataSource = objects;
      }

      form.ShowDialog();
    }

    /// <summary>
    /// This sample uses a PowerShell object to run the Get-Process
    /// and Sort-Object cmdlets synchronously. Windows Forms and
    /// data binding are then used to display the results in a
    /// DataGridView control.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object.
    /// 2. Adding commands and arguments to the pipeline of
    ///    the PowerShell object.
    /// 3. Running the commands synchronously.
    /// 4. Using a DataGridView control to display the output
    ///    of the commands in a Windows Forms application.
    /// </remarks>
    private static void Main(string[] args)
    {
      Runspace02.CreateForm();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="e683b-117">参照</span><span class="sxs-lookup"><span data-stu-id="e683b-117">See Also</span></span>

[<span data-ttu-id="e683b-118">Windows PowerShell ホスト アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="e683b-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)