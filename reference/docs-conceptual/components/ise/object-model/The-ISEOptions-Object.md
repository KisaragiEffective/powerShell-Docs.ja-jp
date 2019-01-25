---
ms.date: 06/05/2017
keywords: PowerShell, コマンドレット
title: ISEOptions オブジェクト
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: e756da21aaa5465f7fa6a90563b4180f0c89e87b
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403182"
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="e8c2c-103">ISEOptions オブジェクト</span><span class="sxs-lookup"><span data-stu-id="e8c2c-103">The ISEOptions Object</span></span>

<span data-ttu-id="e8c2c-104">**ISEOptions** オブジェクトは、Windows PowerShell ISE のさまざまな設定を表します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="e8c2c-105">これは **Microsoft.PowerShell.Host.ISE.ISEOptions** クラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

<span data-ttu-id="e8c2c-106">**ISEOptions** オブジェクトは、次のメソッドとプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="e8c2c-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="e8c2c-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="e8c2c-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="e8c2c-108">RestoreDefaultConsoleTokenColors\(\)</span></span>

<span data-ttu-id="e8c2c-109">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-110">コンソール ウィンドウのトークンの色の既定値を復元します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-110">Restores the default values of the token colors in the Console pane.</span></span>

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="e8c2c-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="e8c2c-111">RestoreDefaults\(\)</span></span>

<span data-ttu-id="e8c2c-112">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-113">コンソール ウィンドウのすべてのオプション設定の既定値を復元します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="e8c2c-114">メッセージが再度表示されることを防ぐため、標準のチェック ボックスを提供する各種の警告メッセージの動作もリセットされます。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="e8c2c-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="e8c2c-115">RestoreDefaultTokenColors\(\)</span></span>

<span data-ttu-id="e8c2c-116">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-117">スクリプト ウィンドウのトークンの色の既定値を復元します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-117">Restores the default values of the token colors in the Script pane.</span></span>

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="e8c2c-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="e8c2c-118">RestoreDefaultXmlTokenColors\(\)</span></span>

<span data-ttu-id="e8c2c-119">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-120">Windows PowerShell ISE で表示される XML 要素のトークンの色の既定値を復元します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="e8c2c-121">[XmlTokenColors](#xmltokencolors) も参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="e8c2c-122">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e8c2c-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="e8c2c-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="e8c2c-123">AutoSaveMinuteInterval</span></span>

<span data-ttu-id="e8c2c-124">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-125">Windows PowerShell ISE によるファイルの自動保存の処理間隔を分単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="e8c2c-126">既定値は 2 分です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-126">The default value is 2 minutes.</span></span> <span data-ttu-id="e8c2c-127">値は整数です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-127">The value is an integer.</span></span>

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="e8c2c-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="e8c2c-128">CommandPaneBackgroundColor</span></span>

<span data-ttu-id="e8c2c-129">この機能は、Windows PowerShell ISE 2.0 に存在しますが、それよりも後のバージョンの ISE では削除されているか、名前が変更されています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="e8c2c-130">後のバージョンについては、[ConsolePaneBackgroundColor](#consolepanebackgroundcolor) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="e8c2c-131">コマンド ウィンドウの背景色を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="e8c2c-132">これは **System.Windows.Media.Color** クラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a><span data-ttu-id="e8c2c-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="e8c2c-133">CommandPaneUp</span></span>

<span data-ttu-id="e8c2c-134">この機能は、Windows PowerShell ISE 2.0 に存在しますが、それよりも後のバージョンの ISE では削除されているか、名前が変更されています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

<span data-ttu-id="e8c2c-135">コマンド ウィンドウを出力ウィンドウの上に配置するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="e8c2c-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="e8c2c-136">ConsolePaneBackgroundColor</span></span>

<span data-ttu-id="e8c2c-137">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-138">コンソール ウィンドウの背景色を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="e8c2c-139">これは **System.Windows.Media.Color** クラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="e8c2c-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="e8c2c-140">ConsolePaneForegroundColor</span></span>

<span data-ttu-id="e8c2c-141">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-142">コンソール ウィンドウのテキストの前景色を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-142">Specifies the foreground color of the text in the Console pane.</span></span>

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="e8c2c-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="e8c2c-143">ConsolePaneTextBackgroundColor</span></span>

<span data-ttu-id="e8c2c-144">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-145">コンソール ウィンドウのテキストの背景色を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-145">Specifies the background color of the text in the Console pane.</span></span>

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a><span data-ttu-id="e8c2c-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="e8c2c-146">ConsoleTokenColors</span></span>

<span data-ttu-id="e8c2c-147">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-148">Windows PowerShell ISE のコンソール ウィンドウの IntelliSense のトークンの色を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="e8c2c-149">このプロパティは、コンソール ウィンドウのトークンの種類と色の名前/値のペアを含むディクショナリ オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="e8c2c-150">スクリプト ウィンドウで IntelliSense トークンの色を変更する場合は、[TokenColors](#tokencolors) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span> <span data-ttu-id="e8c2c-151">色を既定値にリセットする場合、[RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span> <span data-ttu-id="e8c2c-152">次のトークンの色を設定できます。属性、コマンド、CommandArgument、CommandParameter、コメント、GroupEnd、GroupStart、キーワード、LineContinuation、LoopLabel、メンバー、改行、数値、演算子、位置、StatementSeparator、文字列、型、不明、変数です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="e8c2c-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="e8c2c-153">DebugBackgroundColor</span></span>

<span data-ttu-id="e8c2c-154">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-155">コンソール ウィンドウに表示されるデバッグ テキストの背景色を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="e8c2c-156">これは **System.Windows.Media.Color** クラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="e8c2c-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="e8c2c-157">DebugForegroundColor</span></span>

<span data-ttu-id="e8c2c-158">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-159">コンソール ウィンドウに表示されるデバッグ テキストの前景色を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="e8c2c-160">これは **System.Windows.Media.Color** クラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a><span data-ttu-id="e8c2c-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="e8c2c-161">DefaultOptions</span></span>

<span data-ttu-id="e8c2c-162">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-163">Reset メソッドを使用する場合に使用する既定値を指定するプロパティのコレクション。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```powershell
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3
```

### <a name="errorbackgroundcolor"></a><span data-ttu-id="e8c2c-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="e8c2c-164">ErrorBackgroundColor</span></span>

<span data-ttu-id="e8c2c-165">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-166">コンソール ウィンドウに表示されるエラー テキストの背景色を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="e8c2c-167">これは **System.Windows.Media.Color** クラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="e8c2c-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="e8c2c-168">ErrorForegroundColor</span></span>

<span data-ttu-id="e8c2c-169">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-170">コンソール ウィンドウに表示されるエラー テキストの前景色を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="e8c2c-171">これは **System.Windows.Media.Color** クラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a><span data-ttu-id="e8c2c-172">FontName</span><span class="sxs-lookup"><span data-stu-id="e8c2c-172">FontName</span></span>

<span data-ttu-id="e8c2c-173">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-174">スクリプト ウィンドウおよびコンソール ウィンドウの両方で現在使用しているフォント名を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a><span data-ttu-id="e8c2c-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="e8c2c-175">FontSize</span></span>

<span data-ttu-id="e8c2c-176">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-177">整数値としてフォント サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="e8c2c-178">スクリプト ウィンドウ、コマンド ウィンドウ、出力ウィンドウで使用されます。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="e8c2c-179">有効な値の範囲は、8 ~ 32 です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-179">The valid range of values is 8 through 32.</span></span>

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="e8c2c-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="e8c2c-180">IntellisenseTimeoutInSeconds</span></span>

<span data-ttu-id="e8c2c-181">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-182">IntelliSense が、現在入力しているテキストを解決しようとするために使用する秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="e8c2c-183">この秒数が経ったら、IntelliSense はタイムアウトし、入力を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="e8c2c-184">既定値は 3 秒です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-184">The default value is 3 seconds.</span></span> <span data-ttu-id="e8c2c-185">値は整数です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-185">The value is an integer.</span></span>

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="e8c2c-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="e8c2c-186">MruCount</span></span>

<span data-ttu-id="e8c2c-187">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-188">Windows PowerShell ISE が追跡し、**[ファイルを開く]** メニューの下部で表示する、最近使ったファイルの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="e8c2c-189">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-189">The default value is 10.</span></span> <span data-ttu-id="e8c2c-190">値は整数です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-190">The value is an integer.</span></span>

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="e8c2c-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="e8c2c-191">OutputPaneBackgroundColor</span></span>

<span data-ttu-id="e8c2c-192">この機能は、Windows PowerShell ISE 2.0 に存在しますが、それよりも後のバージョンの ISE では削除されているか、名前が変更されています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="e8c2c-193">後のバージョンについては、[ConsolePaneBackgroundColor](#consolepanebackgroundcolor) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="e8c2c-194">出力ウィンドウ自体の背景色を取得または設定する読み取り/書き込みのプロパティ。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="e8c2c-195">これは **System.Windows.Media.Color** クラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="e8c2c-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="e8c2c-196">OutputPaneTextForegroundColor</span></span>

<span data-ttu-id="e8c2c-197">この機能は、Windows PowerShell ISE 2.0 に存在しますが、それよりも後のバージョンの ISE では削除されているか、名前が変更されています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="e8c2c-198">後のバージョンについては、[ConsolePaneForegroundColor](#consolepaneforegroundcolor) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

<span data-ttu-id="e8c2c-199">Windows PowerShell ISE 2.0 で出力ウィンドウのテキストの前景色を変更する読み取り/書き込みプロパティ。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="e8c2c-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="e8c2c-200">OutputPaneTextBackgroundColor</span></span>

<span data-ttu-id="e8c2c-201">この機能は、Windows PowerShell ISE 2.0 に存在しますが、それよりも後のバージョンの ISE では削除されているか、名前が変更されています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="e8c2c-202">後のバージョンについては、[ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

<span data-ttu-id="e8c2c-203">出力ウィンドウのテキストの背景色を変更する読み取り/書き込みプロパティ。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="e8c2c-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="e8c2c-204">ScriptPaneBackgroundColor</span></span>

<span data-ttu-id="e8c2c-205">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-206">ファイルの背景色を取得または設定する読み取り/書き込みのプロパティ。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="e8c2c-207">これは **System.Windows.Media.Color** クラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="e8c2c-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="e8c2c-208">ScriptPaneForegroundColor</span></span>

<span data-ttu-id="e8c2c-209">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-210">スクリプト ウィンドウのスクリプト以外のファイルの前景色を取得または設定する読み取り/書き込みのプロパティ。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="e8c2c-211">スクリプト ファイルの前景色を設定する場合、[TokenColors](#tokencolors) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="e8c2c-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="e8c2c-212">SelectedScriptPaneState</span></span>

<span data-ttu-id="e8c2c-213">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-214">ディスクプレイでのスクリプト ウィンドウの位置を取得または設定する読み取り/書き込みのプロパティ。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="e8c2c-215">「Maximized」、「Top」、「Right」のいずれかの文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-215">The string can be either 'Maximized', 'Top', or 'Right'.</span></span>

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a><span data-ttu-id="e8c2c-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="e8c2c-216">ShowDefaultSnippets</span></span>

<span data-ttu-id="e8c2c-217">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-218">スニペットの **CTRL + J** 一覧に、Windows PowerShell に含まれるスターター セットを含めるどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-218">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="e8c2c-219">**$false** に設定すると、ユーザー定義のスニペットのみが **CTRL + J** 一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-219">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="e8c2c-220">既定値は **$true** です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-220">The default value is **$true**.</span></span>

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="e8c2c-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="e8c2c-221">ShowIntellisenseInConsolePane</span></span>

<span data-ttu-id="e8c2c-222">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-223">IntelliSense がコンソール ウィンドウで構文、パラメーター、および値の候補を提供するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="e8c2c-224">既定値は **$true** です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-224">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="e8c2c-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="e8c2c-225">ShowIntellisenseInScriptPane</span></span>

<span data-ttu-id="e8c2c-226">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-227">IntelliSense がスクリプト ウィンドウで構文、パラメーター、および値の候補を提供するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="e8c2c-228">既定値は **$true** です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-228">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="e8c2c-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="e8c2c-229">ShowLineNumbers</span></span>

<span data-ttu-id="e8c2c-230">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-231">スクリプト ペインの左の余白に行番号を表示するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="e8c2c-232">既定値は **$true** です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-232">The default value is **$true**.</span></span>

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="e8c2c-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="e8c2c-233">ShowOutlining</span></span>

<span data-ttu-id="e8c2c-234">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-235">スクリプト ペインの左の余白のコードのセクションの横にある展開と折りたたみの角かっこを表示するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="e8c2c-236">表示する場合、テキストのブロックの横にあるマイナス アイコン \(-\) をクリックすると折りたたみ、プラス アイコン \(+\) をクリックするとテキストのブロックを展開することができます。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-236">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="e8c2c-237">既定値は **$true** です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-237">The default value is **$true**.</span></span>

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="e8c2c-238">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="e8c2c-238">ShowToolBar</span></span>

<span data-ttu-id="e8c2c-239">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-240">Windows PowerShell ISE ウィンドウの上部に ISE ツールバーを表示するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="e8c2c-241">既定値は **$true** です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-241">The default value is **$true**.</span></span>

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="e8c2c-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="e8c2c-242">ShowWarningBeforeSavingOnRun</span></span>

<span data-ttu-id="e8c2c-243">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-244">スクリプトが実行される前に自動的に保存されるときに警告メッセージを表示するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="e8c2c-245">既定値は **$true** です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-245">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="e8c2c-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="e8c2c-246">ShowWarningForDuplicateFiles</span></span>

<span data-ttu-id="e8c2c-247">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-248">さまざまな PowerShell タブで同じファイルが開かれているときに警告メッセージを表示するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="e8c2c-249">場合設定 **$true**を複数のタブが表示されますこのメッセージで、同じファイルを開きます。"このファイルのコピーが別の Windows PowerShell タブで開きます。このファイルを変更すると、開かれているすべてのファイルに影響します。」というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-249">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="e8c2c-250">既定値は **$true** です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-250">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a><span data-ttu-id="e8c2c-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="e8c2c-251">TokenColors</span></span>

<span data-ttu-id="e8c2c-252">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-253">Windows PowerShell ISE のスクリプト ウィンドウの IntelliSense トークンの色を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="e8c2c-254">このプロパティは、スクリプト ウィンドウのトークンの種類と色の名前/値のペアを含むディクショナリ オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="e8c2c-255">コンソール ウィンドウで IntelliSense トークンの色を変更する場合は、[ConsoleTokenColors](#consoletokencolors) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span> <span data-ttu-id="e8c2c-256">色を既定値にリセットする場合、[RestoreDefaultTokenColors](#restoredefaulttokencolors) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span> <span data-ttu-id="e8c2c-257">次のトークンの色を設定できます。属性、コマンド、CommandArgument、CommandParameter、コメント、GroupEnd、GroupStart、キーワード、LineContinuation、LoopLabel、メンバー、改行、数値、演算子、位置、StatementSeparator、文字列、型、不明、変数です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="e8c2c-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="e8c2c-258">UseEnterToSelectInConsolePaneIntellisense</span></span>

<span data-ttu-id="e8c2c-259">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-260">Enter キーを使用して、IntelliSense が提供するオプションをコンソール ウィンドウで選択できるようにするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="e8c2c-261">既定値は **$true** です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-261">The default value is **$true**.</span></span>

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="e8c2c-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="e8c2c-262">UseEnterToSelectInScriptPaneIntellisense</span></span>

<span data-ttu-id="e8c2c-263">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-264">Enter キーを使用して、IntelliSense が提供するオプションをスクリプト ウィンドウで選択できるようにするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="e8c2c-265">既定値は **$true** です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-265">The default value is **$true**.</span></span>

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a><span data-ttu-id="e8c2c-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="e8c2c-266">UseLocalHelp</span></span>

<span data-ttu-id="e8c2c-267">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-268">カーソルをキーワードに置いた状態で F1 キーを押したときに、ローカルにインストールされたヘルプまたはオンラインの TechNet ライブラリのヘルプを表示するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="e8c2c-269">**$true** に設定すると、ローカルにインストールされたヘルプ コンテンツがポップアップ ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-269">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="e8c2c-270">`Update-Help` コマンドを実行すると、ヘルプ ファイルをインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="e8c2c-271">**$false** に設定すると、ブラウザーが開き、TechNet ライブラリ内のページに移動します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-271">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="e8c2c-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="e8c2c-272">VerboseBackgroundColor</span></span>

<span data-ttu-id="e8c2c-273">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-274">コンソール ウィンドウに表示される詳細テキストの背景色を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="e8c2c-275">これは **System.Windows.Media.Color** オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-275">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="e8c2c-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="e8c2c-276">VerboseForegroundColor</span></span>

<span data-ttu-id="e8c2c-277">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-278">コンソール ウィンドウに表示される詳細テキストの前景色を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="e8c2c-279">これは **System.Windows.Media.Color** オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-279">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="e8c2c-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="e8c2c-280">WarningBackgroundColor</span></span>

<span data-ttu-id="e8c2c-281">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-282">コンソール ウィンドウに表示される警告テキストの背景色を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="e8c2c-283">これは **System.Windows.Media.Color** オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-283">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="e8c2c-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="e8c2c-284">WarningForegroundColor</span></span>

<span data-ttu-id="e8c2c-285">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e8c2c-286">出力ウィンドウに表示される警告テキストの前景色を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="e8c2c-287">これは **System.Windows.Media.Color** オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-287">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="e8c2c-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="e8c2c-288">XmlTokenColors</span></span>

<span data-ttu-id="e8c2c-289">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-290">Windows PowerShell ISE で表示される XML コンテンツのトークンの種類と色の名前/値のペアを含むディクショナリ オブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="e8c2c-291">次のトークンの色を設定できます。属性、コマンド、CommandArgument、CommandParameter、コメント、GroupEnd、GroupStart、キーワード、LineContinuation、LoopLabel、メンバー、改行、数値、演算子、位置、StatementSeparator、文字列、型、不明、変数です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="e8c2c-292">[RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors) も参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a><span data-ttu-id="e8c2c-293">ズーム</span><span class="sxs-lookup"><span data-stu-id="e8c2c-293">Zoom</span></span>

<span data-ttu-id="e8c2c-294">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e8c2c-295">コンソール ウィンドウとスクリプト ウィンドウの両方でのテキストの相対サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="e8c2c-296">既定値は 100 です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-296">The default value is 100.</span></span> <span data-ttu-id="e8c2c-297">Windows PowerShell 内のテキストは、値が小さいと小さく表示され、値が大きいと大きく表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="e8c2c-298">値は、20 ~ 400 の範囲の整数です。</span><span class="sxs-lookup"><span data-stu-id="e8c2c-298">The value is an integer that ranges from 20 to 400.</span></span>

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="e8c2c-299">参照</span><span class="sxs-lookup"><span data-stu-id="e8c2c-299">See Also</span></span>

- [<span data-ttu-id="e8c2c-300">Windows PowerShell ISE スクリプト オブジェクト モデルの目的</span><span class="sxs-lookup"><span data-stu-id="e8c2c-300">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="e8c2c-301">ISE オブジェクト モデルの階層</span><span class="sxs-lookup"><span data-stu-id="e8c2c-301">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)