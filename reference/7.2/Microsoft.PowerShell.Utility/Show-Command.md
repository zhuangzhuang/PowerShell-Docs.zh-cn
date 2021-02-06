---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/29/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Command
ms.openlocfilehash: 87bdd5a9610267b8fce9e391431d24872a77e2de
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603806"
---
# Show-Command

## 摘要
在图形窗口中显示 PowerShell 命令信息。

## SYNTAX

```
Show-Command [[-Name] <String>] [-Height <Double>] [-Width <Double>] [-NoCommonParameter]
 [-ErrorPopup] [-PassThru] [<CommonParameters>]
```

## DESCRIPTION

`Show-Command`Cmdlet 可让你在命令窗口中创建 PowerShell 命令。 你可以使用命令窗口的功能运行命令或使其向你返回命令。

`Show-Command` 是一个非常有用的教学和学习工具。 `Show-Command` 适用于所有命令类型，包括 cmdlet、函数、工作流和 CIM 命令。

如果没有参数，则会 `Show-Command` 显示一个命令窗口，其中列出了所有已安装模块中的所有可用命令。 若要查找某个模块中的命令，请从“模块”下拉列表中选择该模块。 若要选择命令，请单击命令名称。

若要使用命令窗口，请通过使用 Name 或单击 **Commands** 列表中的命令名称选择命令。 每个参数集都显示在单独的选项卡上。星号表示强制参数。 若要输入某个参数的值，请在文本框中键入该值或从下拉框中选择值。 若要添加开关参数，请单击以选中参数复选框。

当你准备就绪后，可以单击 **Copy**，以将你创建的命令复制到剪贴板，或单击 **Run** 运行该命令。 你还可以使用 **PassThru** 参数将命令返回到主机程序，如 PowerShell 控制台。 若要取消命令选择并返回到显示所有命令的视图，请按 Ctrl 并单击所选的命令。

在 PowerShell 集成脚本环境中 (ISE) ， `Show-Command` 默认情况下会显示窗口的一个变体。 有关使用此命令窗口的信息，请参阅 PowerShell ISE 帮助主题。

此 cmdlet 已在 PowerShell 7 中引入。

由于此 cmdlet 需要用户界面，因此它在 Windows Server Core 或 Windows Nano Server 上不起作用。 此 cmdlet 仅适用于支持 Windows 桌面的 Windows 系统。

## 示例

### 示例 1：打开命令窗口

此示例显示了窗口的默认视图 `Show-Command` 。 " **命令** " 窗口显示计算机上安装的所有模块中的所有命令的列表。

```powershell
Show-Command
```

### 示例 2：在命令窗口中打开 cmdlet

此示例 `Invoke-Command` 在 " **命令** " 窗口中显示该 cmdlet。 可以使用此显示运行 `Invoke-Command` 命令。

```powershell
Show-Command -Name "Invoke-Command"
```

### 示例 3：打开具有指定参数的 cmdlet

此命令打开 `Show-Command` cmdlet 的窗口 `Connect-PSSession` 。

```powershell
Show-Command -Name "Connect-PSSession" -Height 700 -Width 1000 -ErrorPopup
```

**Height** 和 **Width** 参数指定命令窗口的维度。 **ErrorPopup** 参数显示错误命令窗口。

单击 " **运行**" 时， `Connect-PSSession` 命令将运行，就像你在 `Connect-PSSession` 命令行中键入命令一样。

### 示例 4：为 cmdlet 指定新的默认参数值

此示例使用 `$PSDefaultParameterValues` 自动变量为 cmdlet 的 **Height**、 **Width** 和 **ErrorPopup** 参数设置新的默认值 `Show-Command` 。

```powershell
$PSDefaultParameterValues = @{
    "Show-Command:Height" = 700
    "Show-Command:Width" = 1000
    "Show-Command:ErrorPopup" = $True
}
```

现在，运行命令时 `Show-Command` ，将自动应用新的默认值。 若要在每个 PowerShell 会话中使用这些默认值，请将 `$PSDefaultParameterValues` 变量添加到 powershell 配置文件。 有关详细信息，请参阅 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) 和 [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md)。

### 示例 5：将输出发送到网格视图

此命令显示如何 `Show-Command` 一起使用和 `Out-GridView` cmdlet。

```powershell
Show-Command Get-ChildItem | Out-GridView
```

该命令使用 `Show-Command` cmdlet 打开 cmdlet 的命令窗口 `Get-ChildItem` 。
单击 " **运行** " 按钮时，该 `Get-ChildItem` 命令将运行并生成输出。 管道运算符 ( |) 将命令的输出发送 `Get-ChildItem` 到 `Out-GridView` cmdlet，该 cmdlet 将 `Get-ChildItem` 在交互窗口中显示输出。

### 示例 6：显示在命令窗口中创建的命令

此示例显示了你在窗口中创建的命令 `Show-Command` 。 该命令使用 **PassThru** 参数，该参数 `Show-Command` 在字符串中返回结果。

```powershell
Show-Command -PassThru
```

```Output
Get-EventLog -LogName "Windows PowerShell" -Newest 5
```

例如，如果使用 `Show-Command` 窗口创建一个 `Get-EventLog` 命令，该命令可获取 Windows PowerShell 事件日志中的五个最新事件，然后单击 **"确定**"，则该命令将返回上面所示的输出。 查看命令字符串可帮助你了解 PowerShell。

### 示例 7：将命令保存到变量

此示例演示如何运行在使用 cmdlet 的 **PassThru** 参数时获取的命令字符串 `Show-Command` 。 此策略使你可以查看该命令并使用它。

```powershell
$C = Show-Command -PassThru
$C
Invoke-Expression $C
```

```Output
Get-EventLog -LogName "PowerShell" -Newest 5

Index Time          EntryType   Source                 InstanceID Message
----- ----          ---------   ------                 ---------- -------
11520 Dec 16 16:37  Information Windows PowerShell            400 Engine state is changed from None to Available...
11519 Dec 16 16:37  Information Windows PowerShell            600 Provider "Variable" is Started. ...
11518 Dec 16 16:37  Information Windows PowerShell            600 Provider "Registry" is Started. ...
11517 Dec 16 16:37  Information Windows PowerShell            600 Provider "Function" is Started. ...
11516 Dec 16 16:37  Information Windows PowerShell            600 Provider "FileSystem" is Started. ...
```

第一个命令使用 cmdlet 的 **PassThru** 参数 `Show-Command` ，并将命令的结果保存在变量中 `$C` 。 在这种情况下，我们将使用 `Show-Command` 窗口来创建一个 `Get-EventLog` 命令，用于获取 Windows PowerShell 事件日志中的五个最新事件。 单击 **"确定**" 后，将 `Show-Command` 返回保存在变量中的命令字符串 `$C` 。

### 示例 8：将命令输出保存到变量

此示例使用 **ErrorPopup** 参数将命令的输出保存在变量中。

```powershell
$P = Show-Command Get-Process -ErrorPopup
$P
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    473      33    94096     112532   709     2.06   4492 powershell
```

除了在窗口中显示错误以外，**ErrorPopup** 还会将命令输出返回到当前命令，而不是创建新命令。 运行此命令时，将 `Show-Command` 打开窗口。 你可以使用窗口功能来设置参数值。 若要运行该命令，请单击窗口中的 " **运行** " 按钮 `Show-Command` 。

## PARAMETERS

### -ErrorPopup

指示除了在命令行中显示错误以外，该 cmdlet 还在弹出窗口中显示错误。 默认情况下，如果在窗口中运行的命令 `Show-Command` 生成错误，则该错误仅显示在命令行中。

此外，在使用窗口) 中的 " **运行** " 按钮运行命令 (时 `Show-Command` ， **ErrorPopup** 参数会将命令结果返回到当前命令，而不是运行该命令并将其输出返回到新的命令。 你可以使用此功能将命令结果保存在变量中。

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

### -Height

指定窗口的高度 `Show-Command` （以像素为单位）。 输入一个介于 300 和屏幕分辨率中的像素数之间的值。 如果值太大而无法在屏幕上显示命令窗口，则会 `Show-Command` 生成错误。 默认高度为 600 像素。 对于 `Show-Command` 包含 **Name** 参数的命令，默认高度为300像素。

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

为指定的命令显示命令窗口。 输入一个命令的名称，例如 cmdlet、函数或 CIM 命令的名称。 如果省略此参数，则 `Show-Command` 将显示一个命令窗口，该窗口列出计算机上安装的所有模块中的所有 PowerShell 命令。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CommandName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoCommonParameter

指示此 cmdlet 省略命令显示的“通用参数”部分。 默认情况下，“通用参数”显示在命令窗口底部的可展开部分中。

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

### -PassThru

返回一个代表你所处理的项目的对象。 默认情况下，此 cmdlet 将不产生任何输出。 若要运行命令字符串，请在命令提示符下复制并粘贴它，或将其保存在变量中，然后使用 `Invoke-Expression` cmdlet 来运行变量中的字符串。

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

### -Width

指定窗口的宽度 `Show-Command` （以像素为单位）。 输入一个介于 300 和屏幕分辨率中的像素数之间的值。 如果值太大而无法在屏幕上显示命令窗口，则会 `Show-Command` 生成错误。 默认宽度为 300 像素。

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给 `Show-Command` 。

## 输出

### None、System.object、System.string

当使用 **PassThru** 参数时，将 `Show-Command` 返回命令字符串。 使用 **ErrorPopup** 参数时，将 `Show-Command` (任何对象) 返回命令输出。 否则，不 `Show-Command` 会生成任何输出。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

`Show-Command` 在远程会话中不起作用。

## 相关链接
