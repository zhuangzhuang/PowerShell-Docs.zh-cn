---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-GridView
ms.openlocfilehash: 19a53b5b14d2dfdb513fbbda4c55ba0df37ab1c0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598677"
---
# Out-GridView

## 摘要
将输出发送到单独窗口中的交互式表中。

## SYNTAX

### PassThru (默认值) 

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-PassThru] [<CommonParameters>]
```

### Wait

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-Wait] [<CommonParameters>]
```

### OutputMode

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-OutputMode <OutputModeOption>]
 [<CommonParameters>]
```

## DESCRIPTION

`Out-GridView`Cmdlet 将命令的输出发送到网格视图窗口，其中的输出显示在交互式表中。

由于此 cmdlet 需要用户界面，因此它在 Windows Server Core 或 Windows Nano Server 上不起作用。

你可以使用该表的以下功能检查你的数据：

- 隐藏、显示和重新排列列
- 对行进行排序
- 快速筛选器
- 添加条件筛选器
- 复制和粘贴

有关完整说明，请参阅本文的 " [备注](#notes) " 部分。

> [!NOTE]
> 此 cmdlet 已在 PowerShell 7 中引入。 此 cmdlet 仅适用于支持 Windows 桌面的 Windows 系统。 有关此 cmdlet 的跨平台版本，请参阅 PowerShell 库中的 [GraphicalTools](https://www.powershellgallery.com/packages/Microsoft.PowerShell.GraphicalTools) 模块。

## 示例

### 示例1：将进程输出到网格视图

此示例将获取在本地计算机上运行的进程，并将其发送到网格视图窗口。

```powershell
Get-Process | Out-GridView
```

### 示例2：使用变量将进程输出到网格视图

此示例还将获取在本地计算机上运行的进程，并将其发送到网格视图窗口。

```powershell
$P = Get-Process
$P | Out-GridView
```

Cmdlet 的输出 `Get-Process` 保存在 `$P` 变量中。 然后， `$P` 将传递给 `Out-GridView` 。

### 示例3：在网格视图中显示所选属性

此示例在网格视图中显示正在运行的进程的选定属性。

```powershell
Get-Process | Select-Object -Property Name, WorkingSet, PeakWorkingSet |
  Sort-Object -Property WorkingSet -Descending | Out-GridView
```

的输出 `Get-Process` 将输送到， `Select-Object` 以选择 **名称**、工作集和 **PeakWorkingSet** 属性。 另一个管道运算符将筛选的对象发送到 `Sort-Object` cmdlet，以按工作集属性的值降序对它们进行排序。
然后，将排序结果传递给 `Out-GridView` 。 你现在可以使用网格视图的功能搜索、排序和筛选数据。

### 示例4：将输出保存到变量，然后输出网格视图

此示例将 cmdlet 输出保存在一个变量中，然后将其发送到 `Out-GridView` 。

```powershell
($A = Get-ChildItem -Path $PSHOME -Recurse) | Out-GridView
```

`Get-ChildItem` 使用自动变量获取 PowerShell 安装目录及其子目录中的所有文件 `$PSHOME` 。 命令中的括号可建立操作的顺序。 因此，该命令的输出 `Get-ChildItem` 保存在变量中， `$A` 然后再将其发送到 `Out-GridView` 。

### 示例5：将指定计算机的输出过程输出到网格视图

此示例在网格视图窗口中显示在 Server01 计算机上运行的进程。

```powershell
Get-Process -ComputerName "Server01" | ogv -Title "Processes - Server01"
```

示例使用 `ogv` ，它是 cmdlet 的别名 `Out-GridView` 。 **Title** 参数指定窗口标题。

### 示例6：将数据从远程计算机输出到网格视图

此示例演示如何将从远程计算机收集的数据发送到 `Out-GridView` 。

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture} | Out-GridView
```

`Invoke-Command``Get-Culture`在三台远程计算机上运行。 生成的数据将通过管道传输到 `Out-GridView` 。 请注意，在远程计算机上运行的脚本块不包含 `Out-GridView` 命令。 如果包括该命令，则当它尝试在每台远程计算机上打开网格视图窗口时，该命令将会失败。

### 示例7：通过传递多个项 `Out-GridView`

此示例可让你从窗口中选择多个进程 `Out-GridView` 。 你选择的进程将传递到 `Export-Csv` 命令并写入到 `ProcessLog.csv` 文件中。

```powershell
Get-Process | Out-GridView -PassThru | Export-Csv -Path .\ProcessLog.csv
```

**通过的 PassThru** 参数 `Out-GridView` ，可将多个项沿管道向下发送。 **PassThru** 参数等效于使用 **OutputMode** 参数的 **Multiple** 值。

### 示例8：创建 Windows 快捷方式 `Out-GridView`

此示例演示如何使用的 **Wait** 参数 `Out-GridView` 创建窗口的窗口快捷方式 `Out-GridView` 。

```powershell
pwsh -Command "Get-Service | Out-GridView -Wait"
```

可在 Windows 快捷方式中使用此命令行。 如果没有 **Wait** 参数，PowerShell 将在窗口打开后立即退出 `Out-GridView` ，这会 `Out-GridView` 立即关闭窗口。

## PARAMETERS

### -InputObject

指定 cmdlet 接受作为输入的对象 `Out-GridView` 。

使用 **InputObject** 参数将对象集合发送到时 `Out-GridView` ， `Out-GridView` 会将该集合视为一个集合对象，并显示一个表示该集合的行。 若要显示集合中的每个对象，请使用管道运算符 (`|`) 将对象发送到 `Out-GridView` 。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -OutputMode

指定交互式窗口将管道向下发送到其他命令的输入的项。
默认情况下，此 cmdlet 将不产生任何输出。 若要将交互式窗口中的项通过管道向下发送，请单击以选择项，然后单击“确定”。

此参数的值确定你可以通过管道向下发送多少项。

- 无。  无项。 这是默认值。
- 单一。 零个项或一个项。 当下一个命令只能获取一个输入对象时，使用此值。
- 多个. 零个、一个或多个项。 当下一个命令可以获取多个输入对象时，使用此值。 此值等效于 **Passthru** 参数。

```yaml
Type: Microsoft.PowerShell.Commands.OutputModeOption
Parameter Sets: OutputMode
Aliases:
Accepted values: None, Single, Multiple

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

指示该 cmdlet 将交互窗口中的项作为输入通过管道向下发送到其他命令。 默认情况下，此 cmdlet 将不产生任何输出。 此参数等效于使用 **OutputMode** 参数的 **Multiple** 值。

若要将交互式窗口中的项通过管道向下发送，请单击以选择项，然后单击“确定”。 支持 Shift 单击和 Ctrl 单击。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PassThru
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Title

指定在窗口的标题栏中显示的文本 `Out-GridView` 。 默认情况下，标题栏将显示调用的命令 `Out-GridView` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wait

指示此 cmdlet 禁止显示命令提示符，并阻止 Windows PowerShell 关闭，直到 `Out-GridView` 窗口关闭。 默认情况下，当窗口打开时，命令提示符 `Out-GridView` 会返回。

此功能可让你 `Out-GridView` 在 Windows 快捷方式中使用 cmdlet。 如果 `Out-GridView` 在没有 **Wait** 参数的快捷方式中使用，则该 `Out-GridView` 窗口仅在 PowerShell 关闭之前出现一段时间。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Wait
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

可以向此 cmdlet 发送任何对象。

## 输出

### 无

通常，不 `Out-GridView` 返回任何对象。 当使用 **PassThru** 参数时，表示所选行的对象将返回到管道中。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

你不能使用远程命令在另一台计算机上打开网格视图窗口。

你发送到的命令输出 `Out-GridView` 不能使用 `Format` cmdlet （如或 cmdlet）进行格式设置 `Format-Table` `Format-Wide` 。 若要选择属性，请使用 `Select-Object` cmdlet。

在网格视图窗口中，可能无法对来自远程命令的反序列化输出正确进行格式设置。

**键盘快捷方式**`Out-GridView`

|              使用此键：              |                                   若要执行此操作：                                    |
| --------------------------------------- | -------------------------------------------------------------------------------------------- |
| Tab                           | 将光标从 " **筛选器** " 框移到表的 " **添加条件** " 菜单，然后返回。 |
| <kbd>向上键</kbd>                      | 向上移动一行。 从数据的第一行移到列标题。                             |
| <kbd>向下键</kbd>                    | 向下移动一行。                                                                           |
| <kbd>向左键</kbd>                    | 在列标题行中，向左移动一列。                                                  |
| <kbd>右箭头</kbd>                   | 在列标题行中，右移一列。                                                 |
| <kbd>ContextMenuKey</kbd>               | 在 "列标题行" 中，显示 "选择列" 选项。                                    |
| <kbd>Enter</kbd> 或 <kbd>空格键</kbd> | 在列标题行中，对列数据进行排序 (切换 a-z，Z-A) 。                                    |

**如何使用网格视图窗口功能**

**若要隐藏或显示列：**

1. 右键单击任何列标题，然后单击 " **选择列**"。
2. 在 " **选择列** " 对话框中，使用箭头键将所选列之间的列移动到 "可用的列" 框中。 网格视图窗口中仅显示 " **选择列** " 框中的列。

**若要重新排序列：**

您可以将列拖放到所需的位置。 或使用以下步骤：

1. 右键单击任何列标题，然后单击 " **选择列**"。
2. 在 " **选择列** " 对话框中，使用 " **上移** **" 和 "下移"** 按钮对列进行重新排序。 列表顶部的列显示在网格视图窗口中列表底部的列的左边。

**如何对表数据排序**

- 若要对数据排序，请单击列标题。
- 若要更改排序顺序，请再次单击列标题。 每次你单击同一标题时，排序顺序会在升序和降序之间切换。 当前顺序由列标题中的三角形指示。

**如何选择表数据**

- 若要选择某一行，请选择该行或使用向上或向下箭头导航到该行。
- 若要选择除标题行) 之外的所有行 (，请按<kbd>CTRL</kbd> + <kbd>A</kbd>。
- 若要选择连续的行，请在单击行或使用箭头键的同时按住 <kbd>SHIFT</kbd> 键。
- 若要选择不连续的行，请按 <kbd>CTRL</kbd> 键，然后单击将行添加到选定内容。
- 你不能选择列，也不能选择整个列标题行。

**如何复制行**

- 若要从表中复制一个或多个行，请选择行，然后按 CTRL + C。

  可以将数据粘贴到任何文本或电子表格程序。 你无法复制列或部分行，也无法复制列标题行。

**如何在表中搜索 (快速筛选)**

使用 "筛选器" 框搜索表中的数据。 当你在框中进行键入时，表中仅显示包含所键入的文本的项。

- 搜索文本。 若要在表中搜索文本，请在 "筛选器" 框中键入要查找的文本。
- 搜索多个字词。 若要在表中搜索多个字词，请键入由空格分隔的字词。 `Out-GridView` 显示包含 (逻辑 AND) 的所有单词的行。
- 搜索文字短语。 若要搜索包含空格或特殊字符的短语，请将该短语用引号引起来。 `Out-GridView` 显示包含短语完全匹配项的行。
- 在列中搜索。 若要在一个或多个列中搜索文本，请使用以下格式：

  `<column>:<text> [<column>:<text>] ...`

  例如，若要在 **DisplayName** 列中查找 "Net"，请在 " **筛选器** " 框中键入：

  `displayname:net`

  若要在 **DisplayName** 和 **Name** 列中查找 "Net" 行，请在 " **筛选器** " 框中键入：

  `displayname:net name:net`

- 关闭搜索。 若要再次显示整个表，请单击 " **筛选器** " 框右上角的红色 X 按钮或从 " **筛选器** " 框中删除文本。

**使用条件来筛选表**

您可以使用规则或条件来确定哪些项显示在表中。 仅当项满足你建立的所有条件时，才会显示这些项。 可用条件由网格视图窗口中显示的对象的属性和这些属性的 .NET Framework 类型来确定。

每个条件具有以下格式：

`<column> <operator> <value>`

不同属性的条件由 **和** 连接。 相同属性的条件由 **或** 连接。 你不能更改逻辑连接符。

条件仅影响显示。 它不会从表中删除项。

**如何添加条件**

1. 若要显示 " **添加条件** " 菜单按钮，请在窗口右上角单击 "展开" 箭头。
2. 单击 " **添加条件** " 菜单按钮。
3. 单击以选择列（属性）。 你可以选择一个或多个属性。
4. 选择完属性后，单击 " **添加** " 按钮。
5. 若要取消添加，请单击 " **取消**"。
6. 若要添加更多条件，请再次单击 " **添加条件** " 按钮。

**如何编辑条件**

- 若要更改运算符，请单击蓝色运算符值，然后从下拉列表中选择其他运算符。
- 若要输入或更改值，请在 "值" 框中键入值。 如果输入的值无效，将显示一个圆形的 X 图标。 若要删除它，请更改该值。
- 若要创建 **或** 语句，请添加具有相同属性的条件。

**如何删除条件**

- 若要删除所选的条件，请单击每个条件旁边的红色 X。
- 若要删除所有条件，请单击 " **全部清除** " 按钮。

## 相关链接

[Out-File](Out-File.md)

[Out-printer](Out-Printer.md)

[Out-String](Out-String.md)

