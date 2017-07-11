---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, PowerShell, 構成, セットアップ"
title: "DSC on Nano Server の使用"
ms.openlocfilehash: 2233106bfd07144132f95ea7957ebfa3248ca219
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
<a id="using-dsc-on-nano-server" class="xliff"></a>

# DSC on Nano Server の使用

> 適用先: Windows PowerShell 5.0

**DSC on Nano Server** は、Windows Server 2016 メディアの `NanoServer\Packages` フォルダーに含まれるオプションのパッケージです。 このパッケージをインストールするには、Nano Server の VHD を作成するときに、**New-NanoServerImage** 関数の **Packages** パラメーターの値として **Microsoft-NanoServer-DSC-Package** を指定します。 たとえば、仮想マシンの VHD を作成する場合、コマンドは次のようになります。

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Nano Server のインストールと使用、および PowerShell リモート処理による Nano Server の管理方法については、「[Getting Started with Nano Server (Nano Server の概要)](https://technet.microsoft.com/en-us/library/mt126167.aspx)」を参照してください。


<a id="dsc-features-available-on-nano-server" class="xliff"></a>

## Nano Server で使用できる DSC 機能

 Nano Server でサポートされる API のセットは、通常版の Windows Server と比べると限定的であるため、当面の間、DSC on Nano Server では、すべての SKU で DSC が動作する、完全に機能するパリティを利用できません。 DSC on Nano Server は現在開発中であり、まだ完全な機能ではありません。
 
 現在、Nano Server で使用できる DSC 機能は次のとおりです。 


* プッシュ モードとプル モード

* 以下を含む、通常版の Windows Server に存在するすべての DSC コマンドレット 
  * [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx)
  * [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx)   
  * [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx)       
  * [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [Stop-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)      
  * [Publish-DscConfiguraiton](https://technet.microsoft.com/en-us/library/mt517875.aspx) 
  * [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [Restore-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [Remove-DscConfigurationDocument](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [Get-DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [New-DscChecksum](https://technet.microsoft.com/en-us/library/dn521622.aspx)    

* 構成のコンパイル (「[DSC 構成](configurations.md)」を参照)

  **問題:** 構成のコンパイル中にパスワードの暗号化 (「[MOF ファイルのセキュリティ保護](securemof.md)」を参照) が機能しません。

* メタ構成のコンパイル (「[ローカル構成マネージャーの構成](metaConfig.md)」を参照)

* ユーザー コンテキストでのリソースの実行 ([ユーザーの資格情報を指定した DSC の実行 (RunAs)](runAsUser.md) に関するページを参照)

* クラスベースのリソース (「[PowerShell クラスを使用したカスタム DSC リソースの記述](authoringResourceClass.md)」を参照)

* DSC リソースのデバッグ (「[DSC リソースのデバッグ](debugresource.md)」を参照)
  
  **問題:** リソースで PsDscRunAsCredential が使用されている場合に機能しません (「[ユーザーの資格情報を指定して DSC を実行する](runAsUser.md)」を参照)

* [ノードの相互依存関係の指定](crossNodeDependencies.md) 

* [リソースのバージョン管理](sxsResource.md)

* プル クライアント (構成とリソース) (「[構成名を使用したプル クライアントのセットアップ](pullClientConfigNames.md)」を参照)

* [部分構成 (プルとプッシュ)](partialConfigs.md)

* [プル サーバーへの報告](reportServer.md) 

* MOF 暗号化

* イベント ログ

* Azure Automation DSC レポート

* 完全に機能するリソース
  * [Archive](archiveResource.md)
  * [Environment](environmentResource.md)
  * [File](fileResource.md)
  * [Log](logResource.md)
  * ProcessSet
  * [Registry](registryResource.md)
  * [Script](scriptResource.md)
  * WindowsPackageCab
  * [WindowsProcess](windowsProcessResource.md)
  * WaitForAll (「[ノードの相互依存関係の指定](crossNodeDependencies.md)」を参照)
  * WaitForAny (「[ノードの相互依存関係の指定](crossNodeDependencies.md)」を参照)
  * WaitForSome (「[ノードの相互依存関係の指定](crossNodeDependencies.md)」を参照)

* 部分的に機能するリソース
  * [グループ](groupResource.md)
  * GroupSet
  
  **問題:** 特定のインスタンスを 2 回呼び出す (同じ構成を 2 回実行する) と上記のリソースでエラーが発生します
  
  * [Service](serviceResource.md)
  * ServiceSet
  
  **問題:** サービス (状態) の開始/停止でのみ正常に動作します。 StartupType、資格情報、説明などのほかのサービス属性を変更しようとするとエラーが発生します。 次のようなエラーがスローされます。
  
  *型 [management.managementobject] が見つかりません。この型を含むアセンブリが読み込まれていることを確認してください。*
  
* 機能しないリソース
  * [User](userResource.md)
  

<a id="dsc-features-not-available-on-nano-server" class="xliff"></a>

## Nano Server で使用できない DSC 機能

現在、Nano Server で使用できない DSC 機能は次のとおりです。

* 暗号化パスワードを使用した MOF ドキュメントの暗号化解除 
* プル サーバー - 現在、Nano Server でプル サーバーをセットアップすることはできません
* 動作する機能の一覧に含まれていないもの

<a id="using-custom-dsc-resources-on-nano-server" class="xliff"></a>

## Nano Server でのカスタム DSC リソースの使用
 
Nano Server で使用できる Windows API と CLR ライブラリは限定されているため、完全な CLR バージョンの Windows で動作する DSC は、必ずしも Nano Server で動作するとは限りません。 DSC カスタム リソースを運用環境に展開する前に、エンド ツー エンドのテストを完了してください。

<a id="see-also" class="xliff"></a>

## 参照
- [Nano Server の概要](https://technet.microsoft.com/en-us/library/mt126167.aspx)

