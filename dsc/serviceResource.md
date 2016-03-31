# DSC Service リソース

> 適用先: Windows PowerShell 4.0、Windows PowerShell 5.0


PowerShell Desired State Configuration (DSC) の **Service** リソースは、ターゲット ノード上でサービスを管理するためのメカニズムを備えています。

## 構文

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
}
```

## プロパティ

|  プロパティ  |  説明   | 
|---|---| 
| 名前| サービス名を示します。 これは、表示名とは異なることがあります。 Get-Service コマンドレットを使用すると、サービスとその現在の状態の一覧を取得できます。| 
| BuiltInAccount| サービスに使用するサインイン アカウントを示します。 このプロパティに許容される値は、**LocalService**、**LocalSystem**、および **NetworkService** です。| 
| Credential| サービスを実行するアカウントの資格情報を示します。 このプロパティおよび __BuiltinAccount__ プロパティを同時に使用することはできません。| 
| DependsOn| このリソースを構成する前に、他のリソースの構成を実行する必要があることを示します。 たとえば、最初に実行するリソース構成スクリプト ブロックの ID が __ResourceName__ で、そのタイプが __ResourceType__ である場合、このプロパティを使用する構文は `DependsOn = "[ResourceType]ResourceName"` になります。| 
| StartupType| サービスのスタートアップの種類を示します。 このプロパティに許容される値は、**Automatic**、**Disabled**、および **Manual** です。| 
| State| サービスに対して保証する状態を示します。| 

## 例

```powershell
Service ServiceExample
{
    Name = "TermService"
    StartupType = "Manual"
    State = "Running"
} 
```


<!--HONumber=Feb16_HO4-->


