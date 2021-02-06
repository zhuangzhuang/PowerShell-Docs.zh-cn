---
description: 说明如何将输出从 PowerShell 重定向到文本文件。
Locale: en-US
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_redirection?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Redirection
ms.openlocfilehash: 91eb3f524ddeeb729ce53749c9b0ae922ce21f18
ms.sourcegitcommit: b9826dcf402db8a2b6d3eab37edb82c6af113343
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "99598900"
---
# <a name="about-redirection"></a>关于重定向

## <a name="short-description"></a>简短说明
说明如何将输出从 PowerShell 重定向到文本文件。

## <a name="long-description"></a>长说明

默认情况下，PowerShell 会将输出发送到 PowerShell 主机。 通常，这是控制台应用程序。 但是，您可以将输出定向到一个文本文件，您可以将错误输出重定向到常规输出流。

您可以使用以下方法来重定向输出：

- 使用 `Out-File` cmdlet，该 cmdlet 将命令输出发送到文本文件。
  通常， `Out-File` 需要使用 cmdlet （如 `Encoding` 、 `Force` 、 `Width` 或参数）时，请使用 cmdlet `NoClobber` 。

- 使用 `Tee-Object` cmdlet，该 cmdlet 将命令输出发送到文本文件，然后将其发送到管道。

- 使用 PowerShell 重定向运算符。 使用带有文件目标的重定向运算符在功能上等效于 `Out-File` 无额外参数的管道。

有关流的详细信息，请参阅 [about_Output_Streams](about_Output_Streams.md)。

### <a name="redirectable-output-streams"></a>可重定向输出流

PowerShell 支持以下输出流的重定向。

| 流# |      说明       | 引入  |    写入 Cmdlet     |
| -------- | ---------------------- | -------------- | ------------------- |
| 1        | **成功** 流     | PowerShell 2.0 | `Write-Output`      |
| 2        | **错误** 流       | PowerShell 2.0 | `Write-Error`       |
| 3        | **警告** 流     | PowerShell 3.0 | `Write-Warning`     |
| 4        | **详细** 流     | PowerShell 3.0 | `Write-Verbose`     |
| 5        | **调试** 流       | PowerShell 3.0 | `Write-Debug`       |
| 6        | **信息** 流 | PowerShell 5.0 | `Write-Information` |
| *        | 所有流            | PowerShell 3.0 |                     |

> [!NOTE]
> PowerShell 中还有一个 **进度** 流，但它不支持重定向。

### <a name="powershell-redirection-operators"></a>PowerShell 重定向运算符

PowerShell 重定向运算符如下所示，其中 `n` 表示流号。  `1` 如果未指定流，则 ( ) 的成功流为默认值。

| 操作员 |                         说明                         | 语法 |
| -------- | ----------------------------------------------------------- | ------ |
| `>`      | 向文件发送指定的流。                            | `n>`   |
| `>>`     | 将指定的流 **追加** 到文件中。                      | `n>>`  |
| `>&1`    | 将指定的流 _重定向_ 到 **成功** 流。 | `n>&1` |

> [!NOTE]
> 与某些 Unix shell 不同，只能将其他流重定向到 **成功** 流。

## <a name="examples"></a>示例

### <a name="example-1-redirect-errors-and-output-to-a-file"></a>示例1：将错误和输出重定向到文件

此示例 `dir` 在一个将成功的项和一个将出错的项上运行。

```powershell
dir 'C:\', 'fakepath' 2>&1 > .\dir.log
```

它使用 `2>&1` 将 **错误** 流重定向到 **成功** 流，并将 `>` 结果 **成功** 流发送到名为的文件 `dir.log`

### <a name="example-2-send-all-success-stream-data-to-a-file"></a>示例2：将所有成功流数据发送到文件

此示例将所有 **成功** 流数据发送到名为的文件 `script.log` 。

```powershell
.\script.ps1 > script.log
```

### <a name="example-3-send-success-warning-and-error-streams-to-a-file"></a>示例3：将成功、警告和错误流发送到文件

此示例演示如何组合重定向运算符以获得所需的结果。

```powershell
&{
   Write-Warning "hello"
   Write-Error "hello"
   Write-Output "hi"
} 3>&1 2>&1 > C:\Temp\redirection.log
```

- `3>&1` 将 **警告** 流重定向到 **成功** 流。
- `2>&1` 将 **错误** 流重定向到 **成功** 流 (后者现在同时包含所有 **警告** 流数据) 
- `>` 重定向 **成功** 流， (现在包含) 到名为的文件的 **警告** 和 **错误** 流 `C:\temp\redirection.log`) 

### <a name="example-4-redirect-all-streams-to-a-file"></a>示例4：将所有流重定向到文件

此示例将一个名为的脚本输出从一个名 `script.ps1` 为 `script.log`

```powershell
.\script.ps1 *> script.log
```

### <a name="example-5-suppress-all-write-host-and-information-stream-data"></a>示例5：禁止显示所有 Write-Host 和信息流数据

此示例将禁止显示所有信息流数据。 若要了解有关 **信息流** cmdlet 的详细信息，请参阅 [写入主机](xref:Microsoft.PowerShell.Utility.Write-Host) 和 [写入信息](xref:Microsoft.PowerShell.Utility.Write-Information)

```powershell
&{
   Write-Host "Hello"
   Write-Information "Hello" -InformationAction Continue
} 6> $null
```

### <a name="example-6-show-the-effect-of-action-preferences"></a>示例6：显示操作首选项的效果

操作首选项变量和参数可以更改写入特定流的内容。 此示例中的脚本显示的值如何 `$ErrorActionPreference` 影响写入 **错误** 流的内容。

```powershell
$ErrorActionPreference = 'Continue'
$ErrorActionPreference > log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'SilentlyContinue'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Stop'
$ErrorActionPreference >> log.txt
Try {
    get-item /not-here 2>&1 >> log.txt
}
catch {
    "`tError caught!" >> log.txt
}
$ErrorActionPreference = 'Ignore'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Inquire'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Continue'
```

当我们运行此脚本时 `$ErrorActionPreference` ，将在设置为时收到提示 `Inquire` 。

```powershell
PS C:\temp> .\test.ps1

Confirm
Cannot find path 'C:\not-here' because it does not exist.
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): H
Get-Item: C:\temp\test.ps1:23
Line |
  23 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | The running command stopped because the user selected the Stop option.
```

当我们检查日志文件时，将看到以下内容：

```
PS C:\temp> Get-Content .\log.txt
Continue

Get-Item: C:\temp\test.ps1:3
Line |
   3 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | Cannot find path 'C:\not-here' because it does not exist.

SilentlyContinue
Stop
    Error caught!
Ignore
Inquire
```

## <a name="notes"></a>说明

不会在不发出警告的情况下将数据追加 (`>` 和 `n>`) 覆盖指定文件的当前内容的重定向运算符。

但是，如果该文件是只读文件、隐藏文件或系统文件，则重定向 **会失败**。 追加重定向运算符 (`>>` 和 `n>>`) 不写入只读文件，但会将内容附加到系统文件或隐藏文件。

若要强制将内容重定向到只读、隐藏或系统文件，请使用 `Out-File` cmdlet 及其 `Force` 参数。

写入文件时，重定向运算符使用 `UTF8NoBOM` 编码。 如果文件具有不同的编码，则输出的格式可能不正确。 若要使用不同的编码写入文件，请使用 `Out-File` cmdlet 及其 `Encoding` 参数。

### <a name="potential-confusion-with-comparison-operators"></a>比较运算符可能产生混淆

`>`运算符不会与[大于](about_Comparison_Operators.md#-gt--ge--lt-and--le)比较运算符混淆， (通常 `>`) 的其他编程语言中表示为。

根据所比较的对象，使用的输出 `>` 可能看起来是正确的 (因为36不大于 42) 。

```powershell
PS> if (36 > 42) { "true" } else { "false" }
false
```

但是，对本地文件系统的检查可以看到名为的文件 `42` 是用内容编写的 `36` 。

```powershell
PS> dir

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
------          1/02/20  10:10 am              3 42

PS> cat 42
36
```

尝试使用反向比较 `<` (小于) 时，会产生系统错误：

```powershell
PS> if (36 < 42) { "true" } else { "false" }
At line:1 char:8
+ if (36 < 42) { "true" } else { "false" }
+        ~
The '<' operator is reserved for future use.
    + CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
    + FullyQualifiedErrorId : RedirectionNotSupported
```

如果数字比较是必需的操作， `-lt` 则 `-gt` 应使用。 有关详细信息，请参阅 `-gt` [about_Comparison_Operators](about_Comparison_Operators.md#-gt--ge--lt-and--le)中的运算符。

## <a name="see-also"></a>请参阅

- [Out-File](xref:Microsoft.PowerShell.Utility.Out-File)
- [Tee-Object](xref:Microsoft.PowerShell.Utility.Tee-Object)
- [Write-Debug](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error)
- [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host)
- [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)
- [Write-Output](xref:Microsoft.PowerShell.Utility.Write-Output)
- [Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [about_Output_Streams](about_Output_Streams.md)
- [about_Operators](about_Operators.md)
- [about_Command_Syntax](about_Command_Syntax.md)
- [about_Path_Syntax](about_Path_Syntax.md)
