---
description: 描述可用于遍历项集合中的所有项的语言命令。
Locale: en-US
ms.date: 02/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_foreach?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Foreach
ms.openlocfilehash: 2e9ca47a032834ff0c59a5c24f1f25c93d739e61
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598679"
---
# <a name="about-foreach"></a>关于 ForEach

## <a name="short-description"></a>简短说明
描述可用于遍历项集合中的所有项的语言命令。

## <a name="long-description"></a>长说明

`Foreach`语句 (也称为 `Foreach` 循环) 是一种用于单步执行 () 循环访问项集合中的一系列值的语言构造。

最简单且最典型的集合类型是数组。
在 `Foreach` 循环中，通常对数组中的每个项运行一个或多个命令。

## <a name="syntax"></a>语法

下面显示了 `ForEach` 语法：

```
foreach ($<item> in $<collection>){<statement list>}
```

`ForEach`括在括号中的语句部分表示变量和要循环访问的集合。 `$<item>`当循环运行时，PowerShell 会自动创建变量 `Foreach` 。 在循环的每次迭代之前，变量将设置为集合中的一个值。
语句后面的块 `Foreach` `{<statement list>}` 包含要对集合中的每个项执行的一组命令。

### <a name="examples"></a>示例

例如， `Foreach` 以下示例中的循环显示数组中的值 `$letterArray` 。

```powershell
$letterArray = "a","b","c","d"
foreach ($letter in $letterArray)
{
  Write-Host $letter
}
```

在此示例中，将创建一个数组，并将其 `$letterArray` 初始化为字符串值 `"a"` 、、 `"b"` `"c"` 和 `"d"` 。 第一次 `Foreach` 运行语句时，它会将 `$letter` 变量设置为等于 () 中的第一项 `$letterArray` `"a"` 。 然后，它使用 `Write-Host` cmdlet 来显示字母 a。 下一次循环时，将 `$letter` 设置为 `"b"` ，依此类推。 `Foreach`循环显示字母 d 后，PowerShell 将退出该循环。

整个 `Foreach` 语句必须出现在单个行上，以在 PowerShell 命令提示符下以命令的形式运行该语句。 `Foreach`如果将命令放在 ps1 脚本文件中，则整个语句不必出现在单个行中。

`Foreach` 语句还可与返回项集合的 cmdlet 一起使用。 在下面的示例中，Foreach 语句逐句通过 cmdlet 返回的项的列表 `Get-ChildItem` 。

```powershell
foreach ($file in Get-ChildItem)
{
  Write-Host $file
}
```

您可以通过使用 `If` 语句来限制返回的结果，从而优化示例。 在下面的示例中， `Foreach` 语句执行与上一示例相同的循环操作，但它添加了一个 `If` 语句，用于将结果限制为大于 100 KB (kb) 的文件：

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
  }
}
```

在此示例中， `Foreach` 循环使用该变量的属性 `$file` 执行)  (比较运算 `$file.length -gt 100KB` 。 `$file`变量包含 cmdlet 返回的对象中的所有属性 `Get-ChildItem` 。 因此，你不仅可以返回文件名。
在下一个示例中，PowerShell 将返回语句列表内的长度和上次访问时间：

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
    Write-Host $file.length
    Write-Host $file.lastaccesstime
  }
}
```

在此示例中，你并不限于在语句列表中运行单个命令。

还可以在循环外使用变量 `Foreach` ，并在循环内递增变量。 下面的示例对大小超过 100 KB 的文件进行计数：

```powershell
$i = 0
foreach ($file in Get-ChildItem) {
  if ($file.length -gt 100KB) {
    Write-Host $file "file size:" ($file.length / 1024).ToString("F0") KB
    $i = $i + 1
  }
}

if ($i -ne 0) {
  Write-Host
  Write-Host $i " file(s) over 100 KB in the current directory."
}
else {
  Write-Host "No files greater than 100 KB in the current directory."
}
```

在前面的示例中， `$i` 变量被设置为在 `0` 循环外，在找到的每个大于 100 KB 的文件的循环内，变量将递增。 循环退出时，语句将 `If` 计算的值， `$i` 以显示超过 100 KB 的所有文件的计数。 否则，会显示一条消息，指出未找到超过 100 KB 的文件。

前面的示例还演示如何设置文件长度结果的格式：

```powershell
($file.length / 1024).ToString("F0")
```

该值除以1024，以 kb 为单位（而不是以字节为单位）显示结果，并使用定点格式说明符对结果值进行格式设置，以从结果中删除任何小数值。 0使格式说明符不显示小数位数。

在下面的示例中，函数已定义解析 PowerShell 脚本和脚本模块，并返回中包含的函数的位置。 该示例演示如何使用 `MoveNext` (的方法，该方法的工作方式类似于 `skip X` `For` 循环) 的，以及 `Current` `$foreach` foreach 脚本块内的变量的属性。 示例函数可在脚本中查找函数，即使存在跨多行的异常或不一致的函数定义也是如此。

有关详细信息，请参阅 [使用枚举](about_Automatic_Variables.md#using-enumerators)器。

```powershell
function Get-FunctionPosition {
  [CmdletBinding()]
  [OutputType('FunctionPosition')]
  param(
    [Parameter(Position = 0, Mandatory,
      ValueFromPipeline, ValueFromPipelineByPropertyName)]
    [ValidateNotNullOrEmpty()]
    [Alias('PSPath')]
    [System.String[]]
    $Path
  )

  process {
    try {
      $filesToProcess = if ($_ -is [System.IO.FileSystemInfo]) {
        $_
      } else {
        $filesToProcess = Get-Item -Path $Path
      }
      $parser = [System.Management.Automation.Language.Parser]
      foreach ($item in $filesToProcess) {
        if ($item.PSIsContainer -or
            $item.Extension -notin @('.ps1', '.psm1')) {
          continue
        }
        $tokens = $errors = $null
        $ast = $parser::ParseFile($item.FullName, ([REF]$tokens),
          ([REF]$errors))
        if ($errors) {
          $msg = "File '{0}' has {1} parser errors." -f $item.FullName,
            $errors.Count
          Write-Warning $msg
        }
        :tokenLoop foreach ($token in $tokens) {
          if ($token.Kind -ne 'Function') {
            continue
          }
          $position = $token.Extent.StartLineNumber
          do {
            if (-not $foreach.MoveNext()) {
              break tokenLoop
            }
            $token = $foreach.Current
          } until ($token.Kind -in @('Generic', 'Identifier'))
          $functionPosition = [pscustomobject]@{
            Name       = $token.Text
            LineNumber = $position
            Path       = $item.FullName
          }
          Add-Member -InputObject $functionPosition `
            -TypeName FunctionPosition -PassThru
        }
      }
    }
    catch {
      throw
    }
  }
}
```

## <a name="see-also"></a>另请参阅

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_If](about_If.md)

[ForEach-Object](xref:Microsoft.PowerShell.Core.ForEach-Object)

