---
title: リモート実行空間を作成する |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 057a666f-731b-423d-9d80-7be6b1836244
caps.latest.revision: 5
ms.openlocfilehash: 964320108d7aff24d59905028fb976e0f75642e7
ms.sourcegitcommit: 08e9ed4bc9bffc7af82b3130e74ec7763db74e4f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83382628"
---
# <a name="creating-remote-runspaces"></a>リモート実行空間を作成する

**ComputerName**パラメーターを受け取る powershell コマンドは、powershell を実行する任意のコンピューターで実行できます。 **ComputerName**パラメーターを受け取らないコマンドを実行するには、ws-management を使用して、指定したコンピューターに接続し、そのコンピューターでコマンドを実行する実行空間を構成します。

## <a name="using-a-wsmanconnection-to-create-a-remote-runspace"></a>WSManConnection を使用してリモートの実行空間を作成する

 リモートコンピューターに接続する実行空間を作成するには、 [WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)オブジェクトを作成します。 接続のターゲットエンドポイントは、オブジェクトの[WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri)プロパティを設定することによって指定してください。 次に、 [RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace)メソッドを呼び出して、 [WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)オブジェクトをパラメーターとして指定して、実行空間を作成してから、このメソッドを呼び出します。 `connectionInfo`

 次の例は、リモートコンピューターに接続する実行空間を作成する方法を示しています。 この例で `RemoteComputerUri` は、はリモートコンピューターの実際の URI のプレースホルダーとして使用されます。

```csharp
namespace Samples
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;            // PowerShell namespace.
  using System.Management.Automation.Runspaces;  // PowerShell namespace.

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class RemoteRunspace02
  {
    /// <summary>
    /// This sample shows how to create a remote runspace that
    /// runs commands on the local computer.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create a WSManConnectionInfo object using the default constructor
      // to connect to the "localHost". The WSManConnectionInfo object can
      // also be used to specify connections to remote computers.
      Uri RemoteComputerUri = new Uri("http://Server01:5985/WSMAN");
      WSManConnectionInfo connectionInfo = new WSManConnectionInfo(RemoteComputerUri);

      // Set the OperationTimeout property and OpenTimeout properties.
      // The OperationTimeout property is used to tell PowerShell
      // how long to wait (in milliseconds) before timing out for an
      // operation. The OpenTimeout property is used to tell Windows
      // PowerShell how long to wait (in milliseconds) before timing out
      // while establishing a remote connection.
      connectionInfo.OperationTimeout = 4 * 60 * 1000; // 4 minutes.
      connectionInfo.OpenTimeout = 1 * 60 * 1000; // 1 minute.

      // Create a remote runspace using the connection information.
      //using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace())
      using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace(connectionInfo))
      {
        // Establish the connection by calling the Open() method to open the runspace.
        // The OpenTimeout value set previously will be applied while establishing
        // the connection. Establishing a remote connection involves sending and
        // receiving some data, so the OperationTimeout will also play a role in this process.
          remoteRunspace.Open();

        // Create a PowerShell object to run commands in the remote runspace.
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = remoteRunspace;
          powershell.AddCommand("get-process");
          powershell.Invoke();

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the results.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                              "{0,-20} {1}",
                              result.Members["ProcessName"].Value,
                              result.Members["HandleCount"].Value);
          }
        }

        // Close the connection. Call the Close() method to close the remote
        // runspace. The Dispose() method (called by using primitive) will call
        // the Close() method if it is not already called.
        remoteRunspace.Close();
      }
    }
  }
}
```
