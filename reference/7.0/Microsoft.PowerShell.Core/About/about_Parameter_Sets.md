---
description: 描述如何定义和使用高级函数中的参数集。
title: about_Parameter_Sets
ms.date: 01/05/2021
ms.openlocfilehash: 8f3a33345a8e2fa19810c8ebd527d9a7dca7dec5
ms.sourcegitcommit: eb7ad1850550032880f5529b4e4281514cba1673
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/06/2021
ms.locfileid: "97917813"
---
# <a name="about-parameter-sets"></a>关于参数集

## <a name="short-description"></a>简短说明
描述如何定义和使用高级函数中的参数集。

## <a name="long-description"></a>详细说明

PowerShell 使用参数集使你可以编写一个函数，该函数可对不同方案执行不同的操作。 参数集使你可以向用户公开不同参数。 和，根据用户指定的参数返回不同的信息。

## <a name="parameter-set-requirements"></a>参数集要求

以下要求适用于所有参数集。

- 每个参数集都必须具有唯一的参数组合。 如果可能，必须至少有一个唯一参数是必需参数。

- 包含多个位置参数的参数集必须为每个参数定义唯一的位置。 无两个位置参数可以指定同一位置。

- 集内只有一个参数可以 `ValueFromPipeline` 用值声明关键字 `true` 。 多个参数可以 `ValueFromPipelineByPropertyName` 使用值定义关键字 `true` 。

- 如果未指定参数的参数集，则参数属于所有参数集。

> [!NOTE]
> 参数集限制为32。

## <a name="default-parameter-sets"></a>默认参数集

如果定义了多个参数集，则 `DefaultParameterSetName` **CmdletBinding** 属性的关键字将指定默认参数集。
当 PowerShell 无法根据提供给命令的信息确定设置为使用的参数时，将使用默认参数集。 有关 **CmdletBinding** 属性的详细信息，请参阅 [about_functions_cmdletbindingattribute](about_functions_cmdletbindingattribute.md)。

## <a name="declaring-parameter-sets"></a>声明参数集

若要创建参数集，必须 `ParameterSetName` 为参数集中的每个参数指定 **参数** 属性的关键字。 对于属于多个参数集的参数，请为每个参数集添加一个 **参数** 特性。

**参数** 特性使你能够以不同的方式为每个参数集定义参数。 例如，可以在一组中将参数定义为强制参数，并在另一个集中定义为可选参数。 但是，每个参数集必须至少包含一个唯一参数。

没有分配的参数集名称的参数属于所有参数集。

### <a name="example"></a>示例

以下示例函数对文本文件中的行、字符和单词进行计数。 使用参数可以指定要返回的值以及要度量的文件。 定义了四个参数集：

- 路径
- PathAll
- LiteralPath
- LiteralPathAll

```powershell
function Measure-Lines {
    [CmdletBinding(DefaultParameterSetName = 'Path')]
    param (
        [Parameter(Mandatory = $true,
            ParameterSetName = 'Path',
            HelpMessage = 'Enter one or more filenames',
            Position = 0)]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'PathAll',
            Position = 0)]
        [string[]]$Path,

        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'LiteralPath',
            HelpMessage = 'Enter a single filename',
            ValueFromPipeline = $true)]
        [string]$LiteralPath,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Lines,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Words,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Characters,

        [Parameter(Mandatory = $true, ParameterSetName = 'PathAll')]
        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [switch]$All,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'PathAll')]
        [switch]$Recurse
    )

    begin {
        if ($All) {
            $Lines = $Words = $Characters = $true
        }
        elseif (($Words -eq $false) -and ($Characters -eq $false)) {
            $Lines = $true
        }

        if ($Path) {
            $Files = Get-ChildItem -Path $Path -Recurse:$Recurse
        }
        else {
            $Files = Get-ChildItem -LiteralPath $LiteralPath
        }
    }
    process {
        foreach ($file in $Files) {
            $result = [ordered]@{ }
            $result.Add('File', $file.fullname)

            $content = Get-Content -LiteralPath $file.fullname

            if ($Lines) { $result.Add('Lines', $content.Length) }

            if ($Words) {
                $wc = 0
                foreach ($line in $content) { $wc += $line.split(' ').Length }
                $result.Add('Words', $wc)
            }

            if ($Characters) {
                $cc = 0
                foreach ($line in $content) { $cc += $line.Length }
                $result.Add('Characters', $cc)
            }

            New-Object -TypeName psobject -Property $result
        }
    }
}
```

每个参数集都必须具有唯一参数或参数的唯一组合。 `Path`和 `PathAll` 参数集非常相似，但 **All** 参数对于参数集是唯一的 `PathAll` 。 对于 `LiteralPath` 和参数集也是如此 `LiteralPathAll` 。 即使 `PathAll` 和 `LiteralPathAll` 参数均设置了 **All** 参数， **路径** 和 **LiteralPath** 参数也会将它们区分开来。

使用 `Get-Command -Syntax` 会显示每个参数集的语法。 但它不显示参数集的名称。 下面的示例显示了可在每个参数集中使用哪些参数。

```powershell
(Get-Command Measure-Lines).ParameterSets |
  Select-Object -Property @{n='ParameterSetName';e={$_.name}},
    @{n='Parameters';e={$_.ToString()}}
```

```Output
ParameterSetName Parameters
---------------- ----------
Path             [-Path] <string[]> [-Lines] [-Words] [-Characters] [-Recurse] [<CommonParameters>]
PathAll          [-Path] <string[]> -All [-Recurse] [<CommonParameters>]
LiteralPath      -LiteralPath <string> [-Lines] [-Words] [-Characters] [<CommonParameters>]
LiteralPathAll   -LiteralPath <string> -All [<CommonParameters>]
```

### <a name="parameter-sets-in-action"></a>操作中的参数集

在此示例中，我们使用 `PathAll` 参数集。

```powershell
Measure-Lines test* -All
```

```Output
File                       Lines Words Characters
----                       ----- ----- ----------
C:\temp\test\test.help.txt    31   562       2059
C:\temp\test\test.md          30  1527       3224
C:\temp\test\test.ps1          3     3         79
C:\temp\test\test[1].txt      31   562       2059
```
