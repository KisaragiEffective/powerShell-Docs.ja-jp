---
ms.date: 06/05/2017
keywords: PowerShell, コマンドレット
title: ユーザー設定の入力ボックスを作成する
ms.assetid: 0b12e56c-299f-40ee-afbf-d30d23ed2565
ms.openlocfilehash: 681a75a28a8fb03eb4442d5e20b32b25a337d540
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2018
---
# <a name="creating-a-custom-input-box"></a>ユーザー設定の入力ボックスを作成する

Windows PowerShell 3.0 以降のリリースで、Microsoft .NET Framework フォーム作成機能を使用してカスタムのグラフィカル入力ボックスをスクリプト化します。

## <a name="create-a-custom-graphical-input-box"></a>カスタムのグラフィカル入力ボックスの作成

以下を Windows PowerShell ISE にコピーしてから貼り付け、Windows PowerShell スクリプト (.ps1) として保存します。

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)

$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)

$form.Topmost = $true

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

このスクリプトは 2 つの .NET Framework クラス、つまり **System.Drawing** と **System.Windows.Forms** を最初に読み込みます。 次に、.NET Framework クラス **System.Windows.Forms.Form** の新しいインスタンスを開始します。これにより、コントロールの追加を開始する空白のフォームまたはウィンドウが作成されます。

```powershell
$form = New-Object System.Windows.Forms.Form
```

フォーム クラスのインスタンスを作成したら、このクラスの次の 3 つのプロパティに値を割り当てます。

- **Text**。 ウィンドウのタイトルになります。

- **Size**。 フォームのサイズをピクセル単位で表します。 前述のスクリプトにより、幅 300 ピクセル、高さ 200 ピクセルのフォームが作成されます。

- **StartingPosition**。 前述のスクリプトでは、この省略可能なプロパティは **CenterScreen** に設定されています。 このプロパティを追加しない場合、Windows はフォームを開いたときの場所を選択します。 **StartingPosition** を **CenterScreen** に設定すると、フォームを読み込むたびに、フォームが画面中央に自動的に表示されます。

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

次に、フォームに **[OK]** ボタンを作成します。 **[OK]** ボタンのサイズと動作を指定します。 この例では、ボタンの位置は、フォームの上端から 120 ピクセル、左端から 75 ピクセルです。 ボタンの高さは 23 ピクセル、ボタンの幅は 75 ピクセルです。 スクリプトは、ボタンの動作を決定するために定義済みの Windows フォームの型を使用します。

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

同様に、**[キャンセル]** ボタンを作成します。 **[キャンセル]** ボタンの位置は、ウィンドウの最上部から 120 ピクセル、左端から 150 ピクセルです。

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

次に、ユーザーに提供する情報を記述するラベルのテキストをウィンドウ上に用意します。

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

ラベルのテキストに記述した情報をユーザーに提供できるようにするコントロール (この場合はテキスト ボックス) を追加します。 テキスト ボックスに加えて、他に多数の適用可能なコントロールがあります。その他のコントロールについては、MSDN の「[System.Windows.Forms 名前空間](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx)」をご覧ください。

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

**Topmost** プロパティを **$true** に設定すると、開いているその他のウィンドウとダイアログ ボックスの最上部にウィンドウが強制的に開きます。

```powershell
$form.Topmost = $true
```

続いて、次のコード行を追加してフォームをアクティブにするとともに、作成したテキスト ボックスにフォーカスを設定します。

```powershell
$form.Add_Shown({$textBox.Select()})
```

次のコード行を追加して、Windows でフォームを表示します。

```powershell
$result = $form.ShowDialog()
```

最後に、**If** ブロック内のコードは、ユーザーがテキスト ボックスにテキストを入力した後のフォームの操作を Windows に指示します。続いて **[OK]** ボタンをクリックするか、**Enter** キーを押します。

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a>参照

- [Hey Scripting Guy: これらの PowerShell GUI の例が機能しないのはなぜですか。](http://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt の WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell Tip of the Week: ユーザー設定の入力ボックスを作成する](http://technet.microsoft.com/library/ff730941.aspx)