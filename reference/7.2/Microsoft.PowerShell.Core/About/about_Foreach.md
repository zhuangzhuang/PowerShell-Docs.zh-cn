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
# <a name="about-foreach"></a><span data-ttu-id="649d0-103">关于 ForEach</span><span class="sxs-lookup"><span data-stu-id="649d0-103">About ForEach</span></span>

## <a name="short-description"></a><span data-ttu-id="649d0-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="649d0-104">Short description</span></span>
<span data-ttu-id="649d0-105">描述可用于遍历项集合中的所有项的语言命令。</span><span class="sxs-lookup"><span data-stu-id="649d0-105">Describes a language command you can use to traverse all the items in a collection of items.</span></span>

## <a name="long-description"></a><span data-ttu-id="649d0-106">长说明</span><span class="sxs-lookup"><span data-stu-id="649d0-106">Long description</span></span>

<span data-ttu-id="649d0-107">`Foreach`语句 (也称为 `Foreach` 循环) 是一种用于单步执行 () 循环访问项集合中的一系列值的语言构造。</span><span class="sxs-lookup"><span data-stu-id="649d0-107">The `Foreach` statement (also known as a `Foreach` loop) is a language construct for stepping through (iterating) a series of values in a collection of items.</span></span>

<span data-ttu-id="649d0-108">最简单且最典型的集合类型是数组。</span><span class="sxs-lookup"><span data-stu-id="649d0-108">The simplest and most typical type of collection to traverse is an array.</span></span>
<span data-ttu-id="649d0-109">在 `Foreach` 循环中，通常对数组中的每个项运行一个或多个命令。</span><span class="sxs-lookup"><span data-stu-id="649d0-109">Within a `Foreach` loop, it is common to run one or more commands against each item in an array.</span></span>

## <a name="syntax"></a><span data-ttu-id="649d0-110">语法</span><span class="sxs-lookup"><span data-stu-id="649d0-110">Syntax</span></span>

<span data-ttu-id="649d0-111">下面显示了 `ForEach` 语法：</span><span class="sxs-lookup"><span data-stu-id="649d0-111">The following shows the `ForEach` syntax:</span></span>

```
foreach ($<item> in $<collection>){<statement list>}
```

<span data-ttu-id="649d0-112">`ForEach`括在括号中的语句部分表示变量和要循环访问的集合。</span><span class="sxs-lookup"><span data-stu-id="649d0-112">The part of the `ForEach` statement enclosed in parenthesis represents a variable and a collection to iterate.</span></span> <span data-ttu-id="649d0-113">`$<item>`当循环运行时，PowerShell 会自动创建变量 `Foreach` 。</span><span class="sxs-lookup"><span data-stu-id="649d0-113">PowerShell creates the variable `$<item>` automatically when the `Foreach` loop runs.</span></span> <span data-ttu-id="649d0-114">在循环的每次迭代之前，变量将设置为集合中的一个值。</span><span class="sxs-lookup"><span data-stu-id="649d0-114">Prior to each iteration through the loop, the variable is set to a value in the collection.</span></span>
<span data-ttu-id="649d0-115">语句后面的块 `Foreach` `{<statement list>}` 包含要对集合中的每个项执行的一组命令。</span><span class="sxs-lookup"><span data-stu-id="649d0-115">The block following a `Foreach` statement `{<statement list>}` contains a set of commands to execute against each item in a collection.</span></span>

### <a name="examples"></a><span data-ttu-id="649d0-116">示例</span><span class="sxs-lookup"><span data-stu-id="649d0-116">Examples</span></span>

<span data-ttu-id="649d0-117">例如， `Foreach` 以下示例中的循环显示数组中的值 `$letterArray` 。</span><span class="sxs-lookup"><span data-stu-id="649d0-117">For example, the `Foreach` loop in the following example displays the values in the `$letterArray` array.</span></span>

```powershell
$letterArray = "a","b","c","d"
foreach ($letter in $letterArray)
{
  Write-Host $letter
}
```

<span data-ttu-id="649d0-118">在此示例中，将创建一个数组，并将其 `$letterArray` 初始化为字符串值 `"a"` 、、 `"b"` `"c"` 和 `"d"` 。</span><span class="sxs-lookup"><span data-stu-id="649d0-118">In this example, the `$letterArray` array is created and initialized with the string values `"a"`, `"b"`, `"c"`, and `"d"`.</span></span> <span data-ttu-id="649d0-119">第一次 `Foreach` 运行语句时，它会将 `$letter` 变量设置为等于 () 中的第一项 `$letterArray` `"a"` 。</span><span class="sxs-lookup"><span data-stu-id="649d0-119">The first time the `Foreach` statement runs, it sets the `$letter` variable equal to the first item in `$letterArray` (`"a"`).</span></span> <span data-ttu-id="649d0-120">然后，它使用 `Write-Host` cmdlet 来显示字母 a。</span><span class="sxs-lookup"><span data-stu-id="649d0-120">Then, it uses the `Write-Host` cmdlet to display the letter a.</span></span> <span data-ttu-id="649d0-121">下一次循环时，将 `$letter` 设置为 `"b"` ，依此类推。</span><span class="sxs-lookup"><span data-stu-id="649d0-121">The next time through the loop, `$letter` is set to `"b"`, and so on.</span></span> <span data-ttu-id="649d0-122">`Foreach`循环显示字母 d 后，PowerShell 将退出该循环。</span><span class="sxs-lookup"><span data-stu-id="649d0-122">After the `Foreach` loop displays the letter d, PowerShell exits the loop.</span></span>

<span data-ttu-id="649d0-123">整个 `Foreach` 语句必须出现在单个行上，以在 PowerShell 命令提示符下以命令的形式运行该语句。</span><span class="sxs-lookup"><span data-stu-id="649d0-123">The entire `Foreach` statement must appear on a single line to run it as a command at the PowerShell command prompt.</span></span> <span data-ttu-id="649d0-124">`Foreach`如果将命令放在 ps1 脚本文件中，则整个语句不必出现在单个行中。</span><span class="sxs-lookup"><span data-stu-id="649d0-124">The entire `Foreach` statement does not have to appear on a single line if you place the command in a .ps1 script file instead.</span></span>

<span data-ttu-id="649d0-125">`Foreach` 语句还可与返回项集合的 cmdlet 一起使用。</span><span class="sxs-lookup"><span data-stu-id="649d0-125">`Foreach` statements can also be used together with cmdlets that return a collection of items.</span></span> <span data-ttu-id="649d0-126">在下面的示例中，Foreach 语句逐句通过 cmdlet 返回的项的列表 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="649d0-126">In the following example, the Foreach statement steps through the list of items that is returned by the `Get-ChildItem` cmdlet.</span></span>

```powershell
foreach ($file in Get-ChildItem)
{
  Write-Host $file
}
```

<span data-ttu-id="649d0-127">您可以通过使用 `If` 语句来限制返回的结果，从而优化示例。</span><span class="sxs-lookup"><span data-stu-id="649d0-127">You can refine the example by using an `If` statement to limit the results that are returned.</span></span> <span data-ttu-id="649d0-128">在下面的示例中， `Foreach` 语句执行与上一示例相同的循环操作，但它添加了一个 `If` 语句，用于将结果限制为大于 100 KB (kb) 的文件：</span><span class="sxs-lookup"><span data-stu-id="649d0-128">In the following example, the `Foreach` statement performs the same looping operation as the previous example, but it adds an `If` statement to limit the results to files that are greater than 100 kilobytes (KB):</span></span>

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
  }
}
```

<span data-ttu-id="649d0-129">在此示例中， `Foreach` 循环使用该变量的属性 `$file` 执行)  (比较运算 `$file.length -gt 100KB` 。</span><span class="sxs-lookup"><span data-stu-id="649d0-129">In this example, the `Foreach` loop uses a property of the `$file` variable to perform a comparison operation (`$file.length -gt 100KB`).</span></span> <span data-ttu-id="649d0-130">`$file`变量包含 cmdlet 返回的对象中的所有属性 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="649d0-130">The `$file` variable contains all the properties in the object that is returned by the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="649d0-131">因此，你不仅可以返回文件名。</span><span class="sxs-lookup"><span data-stu-id="649d0-131">Therefore, you can return more than just a file name.</span></span>
<span data-ttu-id="649d0-132">在下一个示例中，PowerShell 将返回语句列表内的长度和上次访问时间：</span><span class="sxs-lookup"><span data-stu-id="649d0-132">In the next example, PowerShell returns the length and the last access time inside the statement list:</span></span>

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

<span data-ttu-id="649d0-133">在此示例中，你并不限于在语句列表中运行单个命令。</span><span class="sxs-lookup"><span data-stu-id="649d0-133">In this example, you are not limited to running a single command in a statement list.</span></span>

<span data-ttu-id="649d0-134">还可以在循环外使用变量 `Foreach` ，并在循环内递增变量。</span><span class="sxs-lookup"><span data-stu-id="649d0-134">You can also use a variable outside a `Foreach` loop and increment the variable inside the loop.</span></span> <span data-ttu-id="649d0-135">下面的示例对大小超过 100 KB 的文件进行计数：</span><span class="sxs-lookup"><span data-stu-id="649d0-135">The following example counts files over 100 KB in size:</span></span>

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

<span data-ttu-id="649d0-136">在前面的示例中， `$i` 变量被设置为在 `0` 循环外，在找到的每个大于 100 KB 的文件的循环内，变量将递增。</span><span class="sxs-lookup"><span data-stu-id="649d0-136">In the preceding example, the `$i` variable is set to `0` outside the loop, and the variable is incremented inside the loop for each file that is found that is larger than 100 KB.</span></span> <span data-ttu-id="649d0-137">循环退出时，语句将 `If` 计算的值， `$i` 以显示超过 100 KB 的所有文件的计数。</span><span class="sxs-lookup"><span data-stu-id="649d0-137">When the loop exits, an `If` statement evaluates the value of `$i` to display a count of all the files over 100 KB.</span></span> <span data-ttu-id="649d0-138">否则，会显示一条消息，指出未找到超过 100 KB 的文件。</span><span class="sxs-lookup"><span data-stu-id="649d0-138">Or, it displays a message stating that no files over 100 KB were found.</span></span>

<span data-ttu-id="649d0-139">前面的示例还演示如何设置文件长度结果的格式：</span><span class="sxs-lookup"><span data-stu-id="649d0-139">The previous example also demonstrates how to format the file length results:</span></span>

```powershell
($file.length / 1024).ToString("F0")
```

<span data-ttu-id="649d0-140">该值除以1024，以 kb 为单位（而不是以字节为单位）显示结果，并使用定点格式说明符对结果值进行格式设置，以从结果中删除任何小数值。</span><span class="sxs-lookup"><span data-stu-id="649d0-140">The value is divided by 1,024 to show the results in kilobytes rather than bytes, and the resulting value is then formatted using the fixed-point format specifier to remove any decimal values from the result.</span></span> <span data-ttu-id="649d0-141">0使格式说明符不显示小数位数。</span><span class="sxs-lookup"><span data-stu-id="649d0-141">The 0 makes the format specifier show no decimal places.</span></span>

<span data-ttu-id="649d0-142">在下面的示例中，函数已定义解析 PowerShell 脚本和脚本模块，并返回中包含的函数的位置。</span><span class="sxs-lookup"><span data-stu-id="649d0-142">In the following example, the function defined parses PowerShell scripts and script modules and returns the location of functions contained within.</span></span> <span data-ttu-id="649d0-143">该示例演示如何使用 `MoveNext` (的方法，该方法的工作方式类似于 `skip X` `For` 循环) 的，以及 `Current` `$foreach` foreach 脚本块内的变量的属性。</span><span class="sxs-lookup"><span data-stu-id="649d0-143">The example demonstrates how to use the `MoveNext` method (which works similarly to `skip X` on a `For` loop) and the `Current` property of the `$foreach` variable inside of a foreach script block.</span></span> <span data-ttu-id="649d0-144">示例函数可在脚本中查找函数，即使存在跨多行的异常或不一致的函数定义也是如此。</span><span class="sxs-lookup"><span data-stu-id="649d0-144">The example function can find functions in a script even if there are unusually- or inconsistently-spaced function definitions that span multiple lines.</span></span>

<span data-ttu-id="649d0-145">有关详细信息，请参阅 [使用枚举](about_Automatic_Variables.md#using-enumerators)器。</span><span class="sxs-lookup"><span data-stu-id="649d0-145">For more information, see [Using Enumerators](about_Automatic_Variables.md#using-enumerators).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="649d0-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="649d0-146">SEE ALSO</span></span>

[<span data-ttu-id="649d0-147">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="649d0-147">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="649d0-148">about_If</span><span class="sxs-lookup"><span data-stu-id="649d0-148">about_If</span></span>](about_If.md)

[<span data-ttu-id="649d0-149">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="649d0-149">ForEach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)

