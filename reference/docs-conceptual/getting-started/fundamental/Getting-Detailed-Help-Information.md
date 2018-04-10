---
ms.date: 06/05/2017
keywords: PowerShell, コマンドレット
title: 詳しいヘルプ情報の取得
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: bb0fac4eb338354e411458fad575c726a5f0da35
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2018
---
# <a name="getting-detailed-help-information"></a>詳しいヘルプ情報の取得
Windows PowerShell には、Windows PowerShell の概念と言語について説明した詳しいヘルプ トピックが含まれています。 また、各コマンドレットおよびプロバイダーに関するヘルプ トピックや、多くの関数およびスクリプトに関するヘルプ トピックもあります。

これらのヘルプ トピックはコマンド プロンプトで表示でき、Microsoft TechNet ライブラリで最新版のトピックを見ることもできます。 Windows PowerShell Integrated Scripting Environment など、Windows PowerShell をホストする多くのプログラムでは、状況依存のヘルプやコンパイル済みヘルプ ファイル (.chm) などの追加のヘルプ機能が用意されています。

## <a name="getting-help-for-cmdlets"></a>コマンドレットのヘルプの表示
Windows PowerShell のコマンドレットに関するヘルプを表示するには、[Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) コマンドレットを使用します。 たとえば、[Get-ChildItem [m2]](https://technet.microsoft.com/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) コマンドレットのヘルプを表示するには、次のように入力します。

```
get-help get-childitem
```

または

```
get-childitem -?
```

Get-Help コマンドレットに関するヘルプも表示できます。 たとえば、次のように入力します。

```
get-help get-help
```

セッションのすべてのコマンドレットのヘルプ トピックの一覧を表示するには、次のように入力します。

```
get-help -category cmdlet
```

各ヘルプ トピックを 1 ページずつ表示するには、**help** 関数、またはそのエイリアスである **man** を使用します。 たとえば、Get-ChildItem コマンドレットのヘルプを表示するには、次のように入力します。

```
man get-childitem
```

または

```
help get-childitem
```

パラメーターの説明や使用例など、コマンドレット、関数、またはスクリプトに関する詳細情報を表示するには、Get-Help コマンドレットの *Detailed* パラメーターを使用します。 たとえば、Get-ChildItem コマンドレットに関する詳細情報を表示するには、次のように入力します。

```
get-help get-childitem -detailed
```

ヘルプ トピックのすべての内容を表示するには、Get-Help コマンドレットの *Full* パラメーターを使用します。 たとえば、Get-ChildItem コマンドレットのヘルプ トピックの内容をすべて表示するには、次のように入力します。

```
get-help get-childitem -full
```

コマンドレットのパラメーターに関する詳しいヘルプを表示するには、Get-Help コマンドレットの *Parameter* パラメーターを使用します。 たとえば、Get-ChildItem コマンドレットのすべてのパラメーターの詳しいヘルプを表示するには、次のように入力します。

```
get-help get-childitem -parameter *
```

ヘルプ トピック内の例だけを表示するには、Get-Help の *Example* パラメーターを使用します。 たとえば、Get-ChildItem コマンドレットのヘルプ トピック内の例のみを表示するには、次のように入力します。

```
get-help get-childitem -examples
```

作成したコマンドレットに関するヘルプ トピックを記述する方法については、MSDN ライブラリの「[How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415)」 (コマンドレット ヘルプの記述方法) をご覧ください。

## <a name="getting-conceptual-help"></a>概念説明のヘルプの表示
Get-Help コマンドレットでは、Windows PowerShell 言語に関するトピックなど、Windows PowerShell の概念説明トピックの情報も表示されます。 概念説明のヘルプ トピックには、"about_" というプレフィックスが付きます (about_line_editing など)。 概念説明のトピックの名前は、英語バージョン以外の Windows PowerShell でも英語で入力する必要があります。

概念説明のトピックを一覧表示するには、次のように入力します。

```
get-help about_*
```

特定のヘルプ トピックを表示するには、次のように、トピック名を入力します。

```
get-help about_command_syntax
```

Get-Help の *Detailed*、*Parameter*、*Examples* などのパラメーターは、概念説明ヘルプ トピックの表示には効果がありません。

## <a name="getting-help-about-providers"></a>プロバイダーに関するヘルプの表示
Get-Help コマンドレットでは、Windows PowerShell プロバイダーに関する情報を表示できます。 プロバイダーのヘルプを取得するには、"Get-Help" に続けてプロバイダー名を入力します。 たとえば、Registry プロバイダーのヘルプを取得するには、次のように入力します。

```
get-help registry
```

セッションのすべてのプロバイダーのヘルプ トピックの一覧を表示するには、次のように入力します。

```
get-help -category provider
```

Get-Help の *Detailed*、*Parameter*、*Examples* などのパラメーターは、プロバイダーに関するヘルプ トピックの表示には効果がありません。

## <a name="getting-help-about-scripts-and-functions"></a>スクリプトおよび関数に関するヘルプの表示
Windows PowerShell の多くのスクリプトおよび関数には、ヘルプ トピックが用意されています。 Get-Help コマンドレットを使用して、スクリプトや関数のヘルプ トピックを表示できます。

関数のヘルプを表示するには、"get-help" に続けて関数名を入力します。 たとえば、Disable-PSRemoting 関数のヘルプを表示するには、次のように入力します。

```
get-help disable-psremoting
```

スクリプトのヘルプを表示するには、スクリプト ファイルへの完全修飾パスを入力します。 スクリプトのパスが Path 環境変数に含まれている場合は、コマンドからパスを省略できます。

たとえば、"TestScript.ps1" という名前のスクリプトが C:\\PS-Test ディレクトリに格納されている場合、このスクリプトのヘルプ トピックを表示するには、次のように入力します。

```
get-help c:\ps-test\TestScript.ps1
```

*Detailed*、*Full*、*Examples*、*Parameter* など、コマンドレットのヘルプを表示するためにデザインされているパラメーターは、スクリプトのヘルプや関数のヘルプにも使用できます。 ただし、"get-help \*" を入力してすべてのヘルプを表示した場合、関数およびスクリプトのヘルプは表示されません。

関数およびスクリプトに関するヘルプ トピックを記述する方法については、「[about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)」、「[about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)」、「[about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)」をご覧ください。

## <a name="getting-help-online"></a>オンライン ヘルプの表示
インターネットに接続している場合、ヘルプを見るための最も良い方法の 1 つは、ヘルプ トピックをオンラインで表示することです。 オンライン トピックは簡単に更新できるため、最新の情報が得られる可能性が高くなります。

オンライン ヘルプを表示するには、Get-Help コマンドレットの *Online* パラメーターを使用します。 Get-Help コマンドレットの *Online* パラメーターは、コマンドレットのヘルプ、関数のヘルプ、スクリプトのヘルプに対してのみ機能します。 概念説明のトピック ("about" ヘルプ) やプロバイダーに関するヘルプ トピックに対しては、*Online* パラメーターを使用できません。 また、この機能はオプションであるため、すべてのコマンドレット、関数、スクリプトのヘルプ トピックに有効なわけではありません。

ただし、プロバイダーのヘルプ トピックや概念説明 ("about" ヘルプ) トピックも含め、Windows PowerShell に付属するすべてのヘルプ トピックが、Microsoft TechNet ライブラリの [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) セクションからオンラインで参照できるようになっています。

Get-Help コマンドレットの *Online* パラメーターを使用するには、次のコマンド形式を使用します。

```
get-help <command-name> -online
```

たとえば、Get-ChildItem コマンドレットのヘルプ トピックのオンライン バージョンを表示するには、次のように入力します。

```
get-help get-childitem -online
```

ヘルプ トピックのオンライン バージョンが存在する場合には、既定のブラウザーにそのトピックが表示されます。

あるへルプ トピックに対してオンライン ヘルプがサポートされている場合、そのヘルプ トピックのインターネット アドレス (URL) を表示することもできます。 インターネット アドレスは、ヘルプ トピックの「関連リンク」セクションに表示されます。

たとえば、Add-Computer コマンドレットのオンライン ヘルプ トピックの URL を表示するには、次のように入力します。

```
get-help add-computer
```

トピックの「関連リンク」セクションの最初の行を次に示します。

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

ヘルプ トピックのオンライン サポートを提供する方法については、「[about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)」と MSDN ライブラリの [「How to Write Cmdlet Help」](https://go.microsoft.com/fwlink/?LinkID=123415) (コマンドレット ヘルプの記述方法) をご覧ください。

## <a name="see-also"></a>参照
- [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)
- [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
- [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)