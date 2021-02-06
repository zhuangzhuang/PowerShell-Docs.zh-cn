---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlineoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineOption
ms.openlocfilehash: cac2c2bb8ce1f3a28c0d91c7503b3ac4d038ccad
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/24/2020
ms.locfileid: "99597661"
---
# Set-PSReadLineOption

## 摘要
自定义 **PSReadLine** 中命令行编辑的行为。

## 语法

```
Set-PSReadLineOption [-EditMode <EditMode>] [-ContinuationPrompt <String>] [-HistoryNoDuplicates]
 [-AddToHistoryHandler <System.Func`2[System.String,System.Object]>]
 [-CommandValidationHandler <System.Action`1[System.Management.Automation.Language.CommandAst]>]
 [-HistorySearchCursorMovesToEnd] [-MaximumHistoryCount <Int32>] [-MaximumKillRingCount <Int32>]
 [-ShowToolTips] [-ExtraPromptLineCount <Int32>] [-DingTone <Int32>] [-DingDuration <Int32>]
 [-BellStyle <BellStyle>] [-CompletionQueryItems <Int32>] [-WordDelimiters <String>]
 [-HistorySearchCaseSensitive] [-HistorySaveStyle <HistorySaveStyle>] [-HistorySavePath <String>]
 [-AnsiEscapeTimeout <Int32>] [-PromptText <String[]>] [-ViModeIndicator <ViModeStyle>]
 [-ViModeChangeHandler <ScriptBlock>] [-PredictionSource <PredictionSource>]
 [-PredictionViewStyle <PredictionViewStyle>] [-Colors <Hashtable>] [<CommonParameters>]
```

## 说明

`Set-PSReadLineOption`当你编辑该命令行时，该 cmdlet 将自定义 **PSReadLine** 模块的行为。 若要查看 **PSReadLine** 设置，请使用 `Get-PSReadLineOption` 。

## 示例

### 示例1：设置前景色和背景色

此示例将 **PSReadLine** 设置为显示灰色背景上带有绿色前景文本的 **注释** 标记。 在示例中使用的转义序列中， **32** 表示前景色， **47** 表示背景色。

```powershell
Set-PSReadLineOption -Colors @{ "Comment"="`e[32;47m" }
```

您可以选择仅设置前景文本颜色。 例如， **注释** 标记的浅绿色前景文本颜色： ``"Comment"="`e[92m"`` 。

### 示例2：设置铃声样式

在此示例中， **PSReadLine** 将响应需要用户注意的错误或情况。
**BellStyle** 设置为在 1221 Hz 为60毫秒发出嘟嘟声。

```powershell
Set-PSReadLineOption -BellStyle Audible -DingTone 1221 -DingDuration 60
```

> [!NOTE]
> 此功能可能不适用于平台上的所有主机。

### 示例3：设置多个选项

`Set-PSReadLineOption` 可以设置具有哈希表的多个选项。

```powershell
$PSReadLineOptions = @{
    EditMode = "Emacs"
    HistoryNoDuplicates = $true
    HistorySearchCursorMovesToEnd = $true
    Colors = @{
        "Command" = "#8181f7"
    }
}
Set-PSReadLineOption @PSReadLineOptions
```

`$PSReadLineOptions`哈希表设置键和值。 `Set-PSReadLineOption` 使用的键和值 `@PSReadLineOptions` 来更新 **PSReadLine** 选项。

可以 `$PSReadLineOptions` 在 PowerShell 命令行上查看输入哈希表名称的键和值。

### 示例4：设置多个颜色选项

此示例演示如何在单个命令中设置多个颜色值。

```powershell
Set-PSReadLineOption -Colors @{
  Command            = 'Magenta'
  Number             = 'DarkGray'
  Member             = 'DarkGray'
  Operator           = 'DarkGray'
  Type               = 'DarkGray'
  Variable           = 'DarkGreen'
  Parameter          = 'DarkGreen'
  ContinuationPrompt = 'DarkGray'
  Default            = 'DarkGray'
}
```

### 示例5：设置多个类型的颜色值

此示例显示了三种不同的方法，说明如何设置 **PSReadLine** 中显示的标记的颜色。

```powershell
Set-PSReadLineOption -Colors @{
 # Use a ConsoleColor enum
 "Error" = [ConsoleColor]::DarkRed

 # 24 bit color escape sequence
 "String" = "$([char]0x1b)[38;5;100m"

 # RGB value
 "Command" = "#8181f7"
}
```

### 示例6：使用 ViModeChangeHandler 显示 Vi 模式更改

此示例将发出一个游标更改 VT 转义，以响应 **Vi** 模式更改。

```powershell
function OnViModeChange {
    if ($args[0] -eq 'Command') {
        # Set the cursor to a blinking block.
        Write-Host -NoNewLine "`e[1 q"
    } else {
        # Set the cursor to a blinking line.
        Write-Host -NoNewLine "`e[5 q"
    }
}
Set-PSReadLineOption -ViModeIndicator Script -ViModeChangeHandler $Function:OnViModeChange
```

**OnViModeChange** 函数设置用于 **Vi** 模式的游标选项： insert 和 command。
**ViModeChangeHandler** 使用 `Function:` 提供程序将 **OnViModeChange** 引用为脚本块对象。

有关详细信息，请参阅 [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)。

## 参数

### -AddToHistoryHandler

指定控制哪些命令将添加到 **PSReadLine** 历史记录的 **ScriptBlock** 。

**ScriptBlock** 接收命令行作为输入。 如果 **ScriptBlock** 返回 `$True` ，则会将命令行添加到历史记录中。

```yaml
Type: System.Func`2[System.String,System.Object]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AnsiEscapeTimeout

此选项在重定向输入时（例如，在或下运行时）特定于 Windows `tmux` `screen` 。

使用 Windows 上的重定向输入时，会以转义符开头的字符序列发送多个密钥。 不可能区分后跟多个字符和有效转义序列的单个转义字符。

假设终端发送字符的速度比用户类型要快。 **PSReadLine** 在结束之前将等待此超时，直到它收到了一个完整的转义序列。

如果在键入时看到随机或意外的字符，则可以调整此超时值。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -BellStyle

指定 **PSReadLine** 如何响应各种错误和不明确的情况。

有效值如下：

- **声响**：短时间提示音。
- **视觉对象**：文本短暂闪烁。
- **无**：无反馈。

```yaml
Type: Microsoft.PowerShell.BellStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Audible
Accept pipeline input: False
Accept wildcard characters: False
```

### -颜色

**Colors** 参数指定 **PSReadLine** 使用的各种颜色。

参数是一个哈希表，其中的键指定哪个元素和值指定了颜色。
有关详细信息，请参阅 [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)。

颜色既可以是 **ConsoleColor** 中的值，也可以是 `[ConsoleColor]::Red` 有效的 ANSI 转义序列。 有效的转义序列取决于你的终端。 在 PowerShell 5.0 中，红色文本的示例转义序列是 `$([char]0x1b)[91m` 。 在 PowerShell 6 及更高版本中，同一转义序列是 `` `e[91m`` 。 可以指定其他转义序列，包括以下类型：

添加了两个颜色设置，以支持 `ListView` 在 PSReadLine 2.2.0 中自定义：

- **ListPredictionColor** -设置前导 `>` 字符和尾随源名称的颜色，例如 `[History]` 。 默认情况下，它使用 `DarkYellow` 作为前景色。
- **ListPredictionSelectedColor** -设置用于指示列表项已选定的颜色。 默认情况下，它使用 `DarkBlack` 作为背景色。

- 256颜色
- 24位颜色
- 前景、背景或两者
- 反色、粗体

有关 ANSI 颜色代码的详细信息，请参阅维基百科中的 [ansi 转义码](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) 。

有效的密钥包括：

- **ContinuationPrompt**：继续提示的颜色。
- **强调**：强调颜色。 例如，在搜索历史记录时匹配文本。
- **错误**：错误颜色。 例如，在提示符下。
- **选择**：突出显示菜单选择或选定文本的颜色。
- **默认** 值：默认标记颜色。
- **Comment**：注释标记颜色。
- **关键字**：关键字标记颜色。
- **String**：字符串标记颜色。
- **运算符**：运算符标记颜色。
- **变量**：变量标记颜色。
- **命令**：命令标记颜色。
- **参数**：参数标记颜色。
- **类型**：类型标记颜色。
- **Number**：数字标记颜色。
- **Member**：成员名称令牌颜色。
- **InlinePrediction**：预测建议的内嵌视图的颜色。

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandValidationHandler

指定从 **ValidateAndAcceptLine** 调用的 **ScriptBlock** 。 如果引发异常，验证将失败并报告错误。

在引发异常之前，验证处理程序可以将光标置于错误的点，以便更轻松地进行修复。 验证处理程序还可以更改命令行，如更正常见的录入错误。

**ValidateAndAcceptLine** 用于避免使用无法使用的命令使历史记录混乱。

```yaml
Type: System.Action`1[System.Management.Automation.Language.CommandAst]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CompletionQueryItems

指定在不提示的情况下显示的最大完成项数。

如果要显示的项的数目大于此值， **PSReadLine** 将在显示完成项之前提示 **"是/否** "。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContinuationPrompt

指定输入多行输入时在后续行开头显示的字符串。 默认值为 double 大于符号 (`>>`) 。 空字符串有效。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >>
Accept pipeline input: False
Accept wildcard characters: False
```

### -DingDuration

指定当 **BellStyle** 设置为 "可 **听见**" 时提示音的持续时间。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 50ms
Accept pipeline input: False
Accept wildcard characters: False
```

### -DingTone

指定 **BellStyle** 设置为 "可 **听见**" 时提示音 (Hz) 的色调。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1221
Accept pipeline input: False
Accept wildcard characters: False
```

### -EditMode

指定命令行编辑模式。 使用此参数将重置任何由设置的键绑定 `Set-PSReadLineKeyHandler` 。

有效值如下：

- **Windows**：键绑定模拟 PowerShell、Cmd 和 Visual Studio。
- **Emacs**：键绑定模拟 Bash 或 Emacs。
- **Vi**：键绑定模拟 Vi。

使用 `Get-PSReadLineKeyHandler` 可查看当前配置的 **EditMode** 的键绑定。

```yaml
Type: Microsoft.PowerShell.EditMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExtraPromptLineCount

指定额外行的数目。

如果提示跨多行，请为此参数指定一个值。 如果希望在显示某些输出后 **PSReadLine** 显示提示时提供额外的行，请使用此选项。 例如， **PSReadLine** 返回完成列表。

在以前版本的 **PSReadLine** 中需要此选项，但在使用函数时，此选项很有用 `InvokePrompt` 。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistoryNoDuplicates

此选项控制回调行为。 重复的命令仍将添加到历史记录文件中。
如果设置了此选项，则在调用命令时仅显示最新的调用。 重复执行的命令将添加到历史记录，以便在撤回期间保留排序。 但是，在调用或搜索历史记录时，通常不需要多次看到此命令。

默认情况下，global **PSConsoleReadLineOptions** 对象的 **HistoryNoDuplicates** 属性设置为 `True` 。 使用此 **SwitchParameter** 会将属性值设置为 `True` 。 若要更改属性值，必须按如下所示指定 **SwitchParameter** 的值： `-HistoryNoDuplicates:$False` 。

使用以下命令，可以直接设置属性值：

`(Get-PSReadLineOption).HistoryNoDuplicates = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySavePath

指定保存历史记录的文件的路径。 运行 Windows 或非 Windows 平台的计算机将文件存储在不同的位置。 例如，filename 存储在一个变量中 `$($host.Name)_history.txt` `ConsoleHost_history.txt` 。

如果不使用此参数，则默认路径如下所示：

**Windows**

`$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine\$($host.Name)_history.txt`

**非 Windows**

`$env:XDG_DATA_HOME/powershell/PSReadLine\$($host.Name)_history.txt`

`$env:HOME/.local/share/powershell/PSReadLine\$($host.Name)_history.txt`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A file named $($host.Name)_history.txt in $env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine on Windows and $env:XDG_DATA_HOME/powershell/PSReadLine or $env:HOME/.local/share/powershell/PSReadLine on non-Windows platforms
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySaveStyle

指定 **PSReadLine** 如何保存历史记录。

以下是有效值：

- **SaveIncrementally**：在每个命令执行后保存历史记录，并跨多个 PowerShell 实例共享。
- **SaveAtExit**： PowerShell 退出时追加历史记录文件。
- **SaveNothing**：不要使用历史记录文件。

```yaml
Type: Microsoft.PowerShell.HistorySaveStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SaveIncrementally
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySearchCaseSensitive

指定在函数（如 **ReverseSearchHistory** 或 **HistorySearchBackward**）中，历史记录搜索区分大小写。

默认情况下，global **PSConsoleReadLineOptions** 对象的 **HistorySearchCaseSensitive** 属性设置为 `False` 。 使用此 **SwitchParameter** 会将属性值设置为 `True` 。 若要更改属性值，必须按如下所示指定 **SwitchParameter** 的值： `-HistorySearchCaseSensitive:$False` 。

使用以下命令，可以直接设置属性值：

`(Get-PSReadLineOption).HistorySearchCaseSensitive = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySearchCursorMovesToEnd

指示光标移动到通过使用搜索从历史记录加载的命令的末尾。
如果将此参数设置为 `$False` ，则光标将保持按向上或向下箭头时的位置。

默认情况下，global **PSConsoleReadLineOptions** 对象的 **HistorySearchCursorMovesToEnd** 属性设置为 `False` 。 使用此 **SwitchParameter** 将属性值设置为 `True` 。 若要更改属性值，必须按如下所示指定 **SwitchParameter** 的值： `-HistorySearchCursorMovesToEnd:$False` 。

使用以下命令，可以直接设置属性值：

`(Get-PSReadLineOption).HistorySearchCursorMovesToEnd = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumHistoryCount

指定要在 **PSReadLine** 历史记录中保存的最大命令数。

**PSReadLine** 历史记录独立于 PowerShell 历史记录。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumKillRingCount

指定存储在终止环中的最大项数。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -PromptText

出现分析错误时， **PSReadLine** 会将 "提示" 部分更改为 "红色"。 **PSReadLine** 分析 prompt 函数，以确定如何仅更改提示部分的颜色。 此分析的可靠性不是100%。

如果 **PSReadLine** 以意外的方式更改提示，请使用此选项。 包括任何尾随空格。

例如，如果您的 prompt 函数如下例所示：

`function prompt { Write-Host -NoNewLine -ForegroundColor Yellow "$pwd"; return "# " }`

然后设置：

`Set-PSReadLineOption -PromptText "# "`

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >
Accept pipeline input: False
Accept wildcard characters: False
```

### -ShowToolTips

显示可能的完成时，工具提示将显示在完成列表中。

默认情况下会启用此选项。 默认情况下，在早期版本的 **PSReadLine** 中未启用此选项。 若要禁用，请将此选项设置为 `$False` 。

默认情况下，global **PSConsoleReadLineOptions** 对象的 **ShowToolTips** 属性设置为 `True` 。 使用此 **SwitchParameter** 会将属性值设置为 `True` 。 若要更改属性值，必须按如下所示指定 **SwitchParameter** 的值： `-ShowToolTips:$False` 。

使用以下命令，可以直接设置属性值：

`(Get-PSReadLineOption).ShowToolTips = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViModeChangeHandler

当 **ViModeIndicator** 设置为时 `Script` ，每次模式更改时将调用提供的脚本块。 脚本块提供了一个类型为的参数 `ViMode` 。

此参数是在 PowerShell 7 中引入的。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViModeIndicator

此选项设置当前 **Vi** 模式的视觉指示。 插入模式或命令模式。

有效值如下：

- **无**：无指示。
- **Prompt**：提示更改颜色。
- **Cursor**：光标改变大小。
- **脚本**：打印用户指定的文本。

```yaml
Type: Microsoft.PowerShell.ViModeStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WordDelimiters

指定分隔函数（如 **ForwardWord** 或 **KillWord**）的字词的字符。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: ;:,.[]{}()/\|^&*-=+'"---
Accept pipeline input: False
Accept wildcard characters: False
```

### -PredictionSource

指定 PSReadLine 的源以获取预测建议。

有效值是：

- **无** -禁用预测 IntelliSense 功能 (默认) 。
-`**History** -启用预测 IntelliSense 功能，并使用 PSReadLine 历史记录作为唯一的源。
- **插件** -启用预测 IntelliSense 功能，并使用插件 (`CommandPrediction`) 为唯一的源。 此值已添加到 PSReadLine 2.2.0 中。
- **HistoryAndPlugin** -启用预测 IntelliSense 功能，并同时使用历史记录和插件作为源。 此值已添加到 PSReadLine 2.2.0 中。

```yaml
Type: Microsoft.PowerShell.PredictionSource
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PredictionViewStyle

设置预测文本显示的样式。 默认值为 **InlineView**。

- **InlineView** -当前的样式，类似于鱼 shell 和 zsh 中的样式。 （默认值）
- **ListView** -建议呈现在下拉列表中，用户可以选择使用 <kbd>向上键</kbd> 和 <kbd>向下键</kbd>。

在 PSReadLine 2.2.0 中添加了此参数。

```yaml
Type: Microsoft.PowerShell.PredictionViewStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: InlineView
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将对象传递给 `Set-PSReadLineOption.`

## 输出

### 无

此 cmdlet 将不生成任何输出。

## 说明

## 相关链接

[about_PSReadLine](./About/about_PSReadLine.md)

[PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[PSReadLineOption](Get-PSReadLineOption.md)

[PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)

[PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)
