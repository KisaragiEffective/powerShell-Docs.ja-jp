---
title: Runspace07 サンプル |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4f7bf81e-4f95-4150-afc3-c0872b24d026
caps.latest.revision: 7
ms.openlocfilehash: c156b2d6a7e7d3fcbd1679d2d61c94f31be0f76a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854728"
---
# <a name="runspace07-sample"></a>Runspace07 サンプル

このサンプルは、実行空間を作成し、その実行空間を使用して、2 つのコマンドレットを使用して、同期的に実行する方法を示します、 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)オブジェクト。

## <a name="requirements"></a>要件

このサンプルでは、Windows PowerShell 2.0 が必要です。

## <a name="demonstrates"></a>使用例

このサンプルは、次を示します。

- 作成、 [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace)オブジェクトを使用して、 [System.Management.Automation.Runspaces.Runspacefactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory)クラス。

- 作成、 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)実行空間を使用するオブジェクト。

- パイプラインにコマンドレットを追加、 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)オブジェクト。

- コマンドレットを同期的に実行します。

- プロパティからの抽出、 [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject)コマンドによって返されるオブジェクト。

## <a name="example"></a>例

このサンプルの作成、実行空間で使用される、 [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject)オブジェクトの実行を[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)と[Measure-object](/powershell/module/microsoft.powershell.utility/measure-object)コマンドレット。

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace07
  {
    /// <summary>
    /// This sample shows how to create a runspace and how to run commands
    /// using a PowerShell object. It builds a pipeline that runs the
    /// get-process cmdlet, which is piped to the measure-object
    /// cmdlet to count the number of processes running on the system.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a runspace using the RunspaceFactory class.
    /// 2. Creating a PowerShell object that uses the runspace.
    /// 3. Adding cmdlets to the pipeline of the PowerShell object.
    /// 4. Running the cmdlets synchronously.
    /// 5. Working with PSObject objects to extract properties
    ///    from the objects returned by the cmdlets.
    /// </remarks>
    private static void Main(string[] args)
    {
      Collection<PSObject> result;     // Will hold the result
                                       // of running the cmdlets.

      // Create a runspace. We can not use the RunspaceInvoke class
      // because we need to get at the underlying runspace to
      // explicitly add the commands. Notice that no PSHost object is
      // supplied to the CreateRunspace method so the default host is
      // used. See the Host samples for more information on creating
      // your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace())
      {
        myRunSpace.Open();

        // Create a PowerShell object and specify the runspace.
        PowerShell powershell = PowerShell.Create();
        powershell.Runspace = myRunSpace;

        // Use the using statement so we dispose of the PowerShell object
        // when we're done.
        using (powershell)
        {
          // Add the get-process cmdlet to the PowerShell object. Notice
          // we are specify the name of the cmdlet, not a script.
          powershell.AddCommand("get-process");

          // Add the measure-object cmdlet to count the number
          // of objects being returned. Commands are always added to the end
          // of the pipeline.
          powershell.AddCommand("measure-object");

          // Run the cmdlets synchronously and save the objects returned.
          result = powershell.Invoke();
        }

        // Even after disposing of the pipeLine, we still need to set
        // the powershell variable to null so that the garbage collector
        // can clean it up.
        powershell = null;

        // Display the results of running the commands (checking that
        // everything is ok first.
        if (result == null || result.Count != 1)
        {
          throw new InvalidOperationException(
                    "pipeline.Invoke() returned the wrong number of objects");
        }

        PSMemberInfo count = result[0].Properties["Count"];
        if (count == null)
        {
          throw new InvalidOperationException(
                    "The object returned doesn't have a 'count' property");
        }

        Console.WriteLine(
                   "Runspace07: The Get-Process cmdlet returned {0} objects",
                   count.Value);

        // Close the runspace to release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>参照

[Windows PowerShell ホスト アプリケーションの作成](./writing-a-windows-powershell-host-application.md)