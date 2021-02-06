---
description: PowerShell 提供动态添加新属性和更改对象输出到管道的格式的功能。
Locale: en-US
ms.date: 08/07/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_calculated_properties?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Calculated_Properties
ms.openlocfilehash: 1f7470a47a24b7c2b8265d180aac49cfec9031f6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598704"
---
# <a name="about-calculated-properties"></a><span data-ttu-id="d6ffe-103">关于计算属性</span><span class="sxs-lookup"><span data-stu-id="d6ffe-103">About calculated properties</span></span>

## <a name="short-description"></a><span data-ttu-id="d6ffe-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="d6ffe-104">Short Description</span></span>

<span data-ttu-id="d6ffe-105">PowerShell 提供动态添加新属性和更改对象输出到管道的格式的功能。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-105">PowerShell provides the ability to dynamically add new properties and alter the formatting of objects output to the pipeline.</span></span>

## <a name="long-description"></a><span data-ttu-id="d6ffe-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="d6ffe-106">Long Description</span></span>

<span data-ttu-id="d6ffe-107">许多 PowerShell cmdlet 使用参数将输入对象转换、聚合或处理到输出对象，这些参数允许向这些输出对象添加新属性。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-107">A number of PowerShell cmdlets transform, aggregate, or process input objects into output objects using parameters that allow the addition of new properties to those output objects.</span></span> <span data-ttu-id="d6ffe-108">这些参数可用于基于输入对象的值为输出对象生成新的计算属性。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-108">These parameters can be used to generate new, calculated properties on output objects based on the values of input objects.</span></span>
<span data-ttu-id="d6ffe-109">计算属性由包含键/值对（用于指定新属性的名称）、用于计算值的表达式和可选格式设置 [信息的键](about_hash_tables.md) /值对来定义。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-109">The calculated property is defined by a [hashtable](about_hash_tables.md) containing key-value pairs that specify the name of the new property, an expression to calculate the value, and optional formatting information.</span></span>

## <a name="supported-cmdlets"></a><span data-ttu-id="d6ffe-110">受支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="d6ffe-110">Supported cmdlets</span></span>

<span data-ttu-id="d6ffe-111">以下 cmdlet 支持 **属性** 参数的计算属性值。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-111">The following cmdlets support calculated property values for the **Property** parameter.</span></span> <span data-ttu-id="d6ffe-112">`Format-*`Cmdlet 还支持 **GroupBy** 参数的计算值。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-112">The `Format-*` cmdlets also support calculated values for the **GroupBy** parameter.</span></span>

<span data-ttu-id="d6ffe-113">以下列表列举支持计算属性的 cmdlet 和每个 cmdlet 支持的键值对。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-113">The following list itemizes the cmdlets that support calculated properties and the key-value pairs that are supported by each cmdlet.</span></span>

- `Compare-Object`
  - `expression`

- `ConvertTo-Html`
  - <span data-ttu-id="d6ffe-114">`name`/`label` -可选 (在 PowerShell 3.x 中添加) </span><span class="sxs-lookup"><span data-stu-id="d6ffe-114">`name`/`label` - optional (added in PowerShell 6.x)</span></span>
  - `expression`
  - <span data-ttu-id="d6ffe-115">`width` -可选</span><span class="sxs-lookup"><span data-stu-id="d6ffe-115">`width` - optional</span></span>
  - <span data-ttu-id="d6ffe-116">`alignment` -可选</span><span class="sxs-lookup"><span data-stu-id="d6ffe-116">`alignment` - optional</span></span>

- `Format-Custom`
  - `expression`
  - <span data-ttu-id="d6ffe-117">`depth` -可选</span><span class="sxs-lookup"><span data-stu-id="d6ffe-117">`depth` - optional</span></span>

- `Format-List`
  - <span data-ttu-id="d6ffe-118">`name`/`label` -可选</span><span class="sxs-lookup"><span data-stu-id="d6ffe-118">`name`/`label` - optional</span></span>
  - `expression`
  - <span data-ttu-id="d6ffe-119">`formatstring` -可选</span><span class="sxs-lookup"><span data-stu-id="d6ffe-119">`formatstring` - optional</span></span>

  <span data-ttu-id="d6ffe-120">这一组相同的键/值对同样适用于传递到所有 cmdlet 的 **GroupBy** 参数的计算属性值 `Format-*` 。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-120">This same set of key-value pairs also apply to calculated property values passed to the **GroupBy** parameter for all `Format-*` cmdlets.</span></span>

- `Format-Table`
  - <span data-ttu-id="d6ffe-121">`name`/`label` -可选</span><span class="sxs-lookup"><span data-stu-id="d6ffe-121">`name`/`label` - optional</span></span>
  - `expression`
  - <span data-ttu-id="d6ffe-122">`formatstring` -可选</span><span class="sxs-lookup"><span data-stu-id="d6ffe-122">`formatstring` - optional</span></span>
  - <span data-ttu-id="d6ffe-123">`width` -可选</span><span class="sxs-lookup"><span data-stu-id="d6ffe-123">`width` - optional</span></span>
  - <span data-ttu-id="d6ffe-124">`alignment` -可选</span><span class="sxs-lookup"><span data-stu-id="d6ffe-124">`alignment` - optional</span></span>

- `Format-Wide`
  - `expression`
  - <span data-ttu-id="d6ffe-125">`formatstring` -可选</span><span class="sxs-lookup"><span data-stu-id="d6ffe-125">`formatstring` - optional</span></span>

- `Group-Object`
  - `expression`

- `Measure-Object`
  - <span data-ttu-id="d6ffe-126">仅支持表达式的脚本块，而不支持哈希表。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-126">Only supports a script block for the expression, not a hashtable.</span></span>
  - <span data-ttu-id="d6ffe-127">在 PowerShell 5.1 和更早版本中不受支持。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-127">Not supported in PowerShell 5.1 and older.</span></span>

- `Select-Object`
  - <span data-ttu-id="d6ffe-128">`name`/`label` -可选</span><span class="sxs-lookup"><span data-stu-id="d6ffe-128">`name`/`label` - optional</span></span>
  - `expression`

- `Sort-Object`
  - `expression`
  - <span data-ttu-id="d6ffe-129">`ascending`/`descending` -可选</span><span class="sxs-lookup"><span data-stu-id="d6ffe-129">`ascending`/`descending` - optional</span></span>

> [!NOTE]
> <span data-ttu-id="d6ffe-130">的值可以是 `expression` 脚本块，而不是哈希表。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-130">The value of the `expression` can be a script block instead of a hashtable.</span></span> <span data-ttu-id="d6ffe-131">有关详细信息，请参阅 " [备注](#notes) " 部分。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-131">For more information, see the [Notes](#notes) section.</span></span>

## <a name="hashtable-key-definitions"></a><span data-ttu-id="d6ffe-132">哈希表键定义</span><span class="sxs-lookup"><span data-stu-id="d6ffe-132">Hashtable key definitions</span></span>

- <span data-ttu-id="d6ffe-133">`name`/`label` -指定正在创建的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-133">`name`/`label` - Specifies the name of the property being created.</span></span> <span data-ttu-id="d6ffe-134">您可以使用 `name` 或其别名，可以 `label` 互换。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-134">You can use `name` or its alias, `label`, interchangeably.</span></span>
- <span data-ttu-id="d6ffe-135">`expression` -用于计算新属性值的脚本块。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-135">`expression` - A script block used to calculate the value of the new property.</span></span>
- <span data-ttu-id="d6ffe-136">`alignment` -由生成表格输出的 cmdlet 用来定义值在列中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-136">`alignment` - Used by cmdlets that produce tabular output to define how the values are displayed in a column.</span></span> <span data-ttu-id="d6ffe-137">值必须为 `'left'` 、 `'center'` 或 `'right'` 。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-137">The value must be `'left'`, `'center'`, or `'right'`.</span></span>
- <span data-ttu-id="d6ffe-138">`formatstring` -指定一个格式字符串，该字符串定义如何为输出设置值的格式。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-138">`formatstring` - Specifies a format string that defines how the value is formatted for output.</span></span> <span data-ttu-id="d6ffe-139">有关格式字符串的详细信息，请参阅 [.net 中的格式类型](/dotnet/standard/base-types/formatting-types)。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-139">For more information about format strings, see [Format types in .NET](/dotnet/standard/base-types/formatting-types).</span></span>
- <span data-ttu-id="d6ffe-140">`width` -指定显示值时表中的最大宽度列。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-140">`width` - Specifies the maximum width column in a table when the value is displayed.</span></span> <span data-ttu-id="d6ffe-141">该值必须大于 `0` 。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-141">The value must be greater than `0`.</span></span>
- <span data-ttu-id="d6ffe-142">`depth` -的 **深度** 参数 `Format-Custom` 指定所有属性的展开深度。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-142">`depth` - The **Depth** parameter of `Format-Custom` specifies the depth of expansion for all properties.</span></span> <span data-ttu-id="d6ffe-143">`depth`键允许您指定每个属性的展开深度。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-143">The `depth` key allows you to specify the depth of expansion per property.</span></span>
- <span data-ttu-id="d6ffe-144">`ascending` / `descending` -用于指定一个或多个属性的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-144">`ascending` / `descending` - Allows you to specify the order of sorting for one or more properties.</span></span> <span data-ttu-id="d6ffe-145">这些值是布尔值。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-145">These are boolean values.</span></span>

<span data-ttu-id="d6ffe-146">只要指定的名称前缀明确，哈希表键就不需要拼写。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-146">The hashtable keys need not be spelled out as long as the specified name prefix is unambiguous.</span></span> <span data-ttu-id="d6ffe-147">例如， `n` 可用于代替 `Name` ， `e` 可用于代替 `Expression` 。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-147">For example, `n` can be used in lieu of `Name` and `e` can be used in lieu of `Expression`.</span></span>

## <a name="examples"></a><span data-ttu-id="d6ffe-148">示例</span><span class="sxs-lookup"><span data-stu-id="d6ffe-148">Examples</span></span>

### <a name="compare-object"></a><span data-ttu-id="d6ffe-149">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="d6ffe-149">Compare-Object</span></span>

<span data-ttu-id="d6ffe-150">利用计算属性，您可以控制如何对输入对象的属性进行比较。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-150">With calculated properties, you can control how the properties of the input objects are compared.</span></span> <span data-ttu-id="d6ffe-151">在此示例中，将值与 2)  (取模运算的结果进行比较，而不是直接比较值。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-151">In this example, rather than comparing the values directly, the values are compared to the result of the arithmetic operation (modulus of 2).</span></span>

```powershell
Compare-Object @{p=1} @{p=2} -property @{ Expression = { $_.p % 2 } }
```

```Output
 $_.p % 2  SideIndicator
---------- -------------
         0 =>
         1 <=
```

### <a name="convertto-html"></a><span data-ttu-id="d6ffe-152">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="d6ffe-152">ConvertTo-Html</span></span>

<span data-ttu-id="d6ffe-153">`ConvertTo-Html` 可以将对象集合转换为 HTML 表。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-153">`ConvertTo-Html` can convert a collection of objects to an HTML table.</span></span>
<span data-ttu-id="d6ffe-154">计算属性允许您控制表的显示方式。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-154">Calculated properties allow you to control how the table is presented.</span></span>

```powershell
Get-Alias |
  ConvertTo-Html Name,
                 Definition,
                 @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                    align='center'
                 } |
    Out-File .\aliases.htm -Force
```

<span data-ttu-id="d6ffe-155">此示例将创建一个 HTML 表，其中包含 PowerShell 别名列表和每个别名命令的编号参数。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-155">This example creates an HTML table containing a list of PowerShell aliases and the number parameters for each aliased command.</span></span> <span data-ttu-id="d6ffe-156">**ParameterCount** 列的值居中。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-156">The values of **ParameterCount** column are centered.</span></span>

### <a name="format-custom"></a><span data-ttu-id="d6ffe-157">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="d6ffe-157">Format-Custom</span></span>

<span data-ttu-id="d6ffe-158">`Format-Custom` 以类似于类定义的格式提供对象的自定义视图。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-158">`Format-Custom` provides a custom view of an object in a format similar to a class definition.</span></span> <span data-ttu-id="d6ffe-159">更复杂的对象可以包含深度与复杂类型嵌套的成员。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-159">More complex objects can contain members that are deeply nested with complex types.</span></span> <span data-ttu-id="d6ffe-160">的 **深度** 参数 `Format-Custom` 指定所有属性的展开深度。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-160">The **Depth** parameter of `Format-Custom` specifies the depth of expansion for all properties.</span></span> <span data-ttu-id="d6ffe-161">`depth`键允许您指定每个属性的展开深度。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-161">The `depth` key allows you to specify the depth of expansion per property.</span></span>

<span data-ttu-id="d6ffe-162">在此示例中， `depth` 该键简化了 cmdlet 的自定义输出 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-162">In this example, the `depth` key simplifies the custom output for the `Get-Date` cmdlet.</span></span> <span data-ttu-id="d6ffe-163">`Get-Date` 返回 **DateTime** 对象。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-163">`Get-Date` returns a **DateTime** object.</span></span> <span data-ttu-id="d6ffe-164">此对象的 **日期** 属性也是 **DateTime** 对象，因此该对象是嵌套的。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-164">The **Date** property of this object is also a **DateTime** object, so the object is nested.</span></span>

```powershell
Get-Date | Format-Custom @{expr={$_.Date};depth=1},TimeOfDay
```

```Output
class DateTime
{
  $_.Date =
    class DateTime
    {
      Date = 8/7/2020 12:00:00 AM
      Day = 7
      DayOfWeek = Friday
      DayOfYear = 220
      Hour = 0
      Kind = Local
      Millisecond = 0
      Minute = 0
      Month = 8
      Second = 0
      Ticks = 637323552000000000
      TimeOfDay = 00:00:00
      Year = 2020
      DateTime = Friday, August 07, 2020 12:00:00 AM
    }
  TimeOfDay =
    class TimeSpan
    {
      Ticks = 435031592302
      Days = 0
      Hours = 12
      Milliseconds = 159
      Minutes = 5
      Seconds = 3
      TotalDays = 0.503508787386574
      TotalHours = 12.0842108972778
      TotalMilliseconds = 43503159.2302
      TotalMinutes = 725.052653836667
      TotalSeconds = 43503.1592302
    }
}
```

### <a name="format-list"></a><span data-ttu-id="d6ffe-165">Format-List</span><span class="sxs-lookup"><span data-stu-id="d6ffe-165">Format-List</span></span>

<span data-ttu-id="d6ffe-166">在此示例中，我们使用计算属性更改输出的名称和格式 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-166">In this example, we use calculated properties to change the name and format of the output from `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem *.json -File |
  Format-List Fullname,
              @{
                 name='Modified'
                 expression={$_.LastWriteTime}
                 formatstring='O'
              },
              @{
                 name='Size'
                 expression={$_.Length/1KB}
                 formatstring='N2'
              }
```

```Output
FullName : C:\Git\PS-Docs\PowerShell-Docs\.markdownlint.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.40

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.publish.config.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.25

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.redirection.json
Modified : 2020-07-27T13:05:24.3887629-07:00
Size     : 324.60
```

### <a name="format-table"></a><span data-ttu-id="d6ffe-167">Format-Table</span><span class="sxs-lookup"><span data-stu-id="d6ffe-167">Format-Table</span></span>

<span data-ttu-id="d6ffe-168">在此示例中，计算属性添加了用于按内容类型对文件进行分类的 **类型** 属性。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-168">In this example, the calculated property adds a **Type** property used to classify the files by the content type.</span></span>

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Format-Table Name, Length -GroupBy @{
      name='Type'
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
   Type: Metacontent

Name              Length
----              ------
ThirdPartyNotices   1229
LICENSE-CODE        1106
LICENSE            19047

   Type: Configuration

Name                                Length
----                                ------
.editorconfig                          183
.gitattributes                         419
.gitignore                             228
.markdownlint.json                    2456
.openpublishing.publish.config.json   2306
.openpublishing.redirection.json    332394
.localization-config                   232

   Type: Content

Name            Length
----            ------
README.md         3355
CONTRIBUTING.md    247

   Type: Automation

Name                      Length
----                      ------
.openpublishing.build.ps1    796
build.ps1                   7495
ci.yml                       645
ci-steps.yml                2035
daily.yml                   1271
```

### <a name="format-wide"></a><span data-ttu-id="d6ffe-169">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="d6ffe-169">Format-Wide</span></span>

<span data-ttu-id="d6ffe-170">使用 `Format-Wide` cmdlet 可以将集合中对象的一个属性值显示为多列列表。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-170">The `Format-Wide` cmdlet allows you to display the value of one property for objects in a collection as a multi-column list.</span></span>

<span data-ttu-id="d6ffe-171">在此示例中，我们希望以 kb) 的形式查看文件名和大小 (。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-171">For this example, we want to see the filename and the size (in kilobytes) as a wide listing.</span></span> <span data-ttu-id="d6ffe-172">由于不 `Format-Wide` 显示多个属性，因此我们使用计算属性将两个属性的值合并为一个值。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-172">Since `Format-Wide` does not display more than one property, we use a calculated property to combine the value of two properties into a single value.</span></span>

```powershell
Get-ChildItem -File |
  Format-Wide -Property @{e={'{0} ({1:N2}kb)' -f $_.name,($_.length/1kb)}}
```

```Output
.editorconfig (0.18kb)                          .gitattributes (0.41kb)
.gitignore (0.22kb)                             .localization-config (0.23kb)
.markdownlint.json (2.40kb)                     .openpublishing.build.ps1 (0.78kb)
.openpublishing.publish.config.json (2.25kb)    .openpublishing.redirection.json (324.60kb)
build.ps1 (7.32kb)                              ci.yml (0.63kb)
ci-steps.yml (1.99kb)                           CONTRIBUTING.md (0.24kb)
daily.yml (1.24kb)                              LICENSE (18.60kb)
LICENSE-CODE (1.08kb)                           README.md (3.28kb)
ThirdPartyNotices (1.20kb)
```

### <a name="group-object"></a><span data-ttu-id="d6ffe-173">Group-Object</span><span class="sxs-lookup"><span data-stu-id="d6ffe-173">Group-Object</span></span>

<span data-ttu-id="d6ffe-174">该 `Group-Object` cmdlet 根据指定属性的值在组中显示对象。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-174">The `Group-Object` cmdlet displays objects in groups based on the value of a specified property.</span></span> <span data-ttu-id="d6ffe-175">在此示例中，计算属性计算每种内容类型的文件数。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-175">In this example, the calculated property counts the number of files of each content type.</span></span>

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Group-Object -NoElement -Property @{
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
Count Name
----- ----
    5 Automation
    7 Configuration
    2 Content
    3 Metacontent
```

### <a name="measure-object"></a><span data-ttu-id="d6ffe-176">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="d6ffe-176">Measure-Object</span></span>

<span data-ttu-id="d6ffe-177">`Measure-Object`Cmdlet 计算对象的数值属性。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-177">The `Measure-Object` cmdlet calculates the numeric properties of objects.</span></span> <span data-ttu-id="d6ffe-178">在此示例中，我们将使用计算属性来获取计数，该计数是介于1和10之间的数字 (**求和**) ，可被3整除。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-178">In this example, we use a calculated property to get the count (**Sum**) of the numbers, between 1 and 10, that are evenly divisible by 3.</span></span>

```powershell
1..10 | Measure-Object -Property {($_ % 3) -eq 0} -Sum
```

```Output
Count             : 10
Average           :
Sum               : 3
Maximum           :
Minimum           :
StandardDeviation :
Property          : ($_ % 3) -eq 0
```

> [!NOTE]
> <span data-ttu-id="d6ffe-179">与其他 cmdlet 不同的 `Measure-Object` 是，不接受计算属性的哈希表。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-179">Unlike the other cmdlets, `Measure-Object` does not accept a hashtable for calculated properties.</span></span> <span data-ttu-id="d6ffe-180">必须使用脚本块。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-180">You must use a script block.</span></span>

### <a name="select-object"></a><span data-ttu-id="d6ffe-181">Select-Object</span><span class="sxs-lookup"><span data-stu-id="d6ffe-181">Select-Object</span></span>

<span data-ttu-id="d6ffe-182">您可以使用计算属性将其他成员添加到使用 cmdlet 输出的对象 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-182">You can use calculated properties to add additional members to the objects output with the `Select-Object` cmdlet.</span></span> <span data-ttu-id="d6ffe-183">在此示例中，我们列出了以字母开头的 PowerShell 别名 `C` 。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-183">In this example, we are listing the PowerShell aliases that begin with the letter `C`.</span></span> <span data-ttu-id="d6ffe-184">使用 `Select-Object` ，我们输出别名、它映射到的 cmdlet 以及为 cmdlet 定义的参数的数量计数。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-184">Using `Select-Object`, we output the alias, the cmdlet it's mapped to, and a count for the number of parameters defined for the cmdlet.</span></span> <span data-ttu-id="d6ffe-185">使用计算属性，我们可以创建 **ParameterCount** 属性。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-185">Using a calculated property, we can create the **ParameterCount** property.</span></span>

```powershell
$aliases = Get-Alias c* |
  Select-Object Name,
                Definition,
                @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                }
$aliases | Get-Member
$aliases
```

```Output
   TypeName: Selected.System.Management.Automation.AliasInfo

Name           MemberType   Definition
----           ----------   ----------
Equals         Method       bool Equals(System.Object obj)
GetHashCode    Method       int GetHashCode()
GetType        Method       type GetType()
ToString       Method       string ToString()
Definition     NoteProperty string Definition=Get-Content
Name           NoteProperty string Name=cat
ParameterCount NoteProperty System.Int32 ParameterCount=21

Name    Definition         ParameterCount
----    ----------         --------------
cat     Get-Content                    21
cd      Set-Location                   15
cdd     Push-MyLocation                 1
chdir   Set-Location                   15
clc     Clear-Content                  20
clear   Clear-Host                      0
clhy    Clear-History                  17
cli     Clear-Item                     20
clp     Clear-ItemProperty             22
cls     Clear-Host                      0
clv     Clear-Variable                 19
cnsn    Connect-PSSession              29
compare Compare-Object                 20
copy    Copy-Item                      24
cp      Copy-Item                      24
cpi     Copy-Item                      24
cpp     Copy-ItemProperty              23
cvpa    Convert-Path                   13
```

### <a name="sort-object"></a><span data-ttu-id="d6ffe-186">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="d6ffe-186">Sort-Object</span></span>

<span data-ttu-id="d6ffe-187">使用计算属性，可以按属性对数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-187">Using the calculated properties, you can sort data in different orders per property.</span></span> <span data-ttu-id="d6ffe-188">此示例按 **日期** 以升序顺序对 CSV 文件中的数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-188">This example sorts data from a CSV file in ascending order by **Date**.</span></span> <span data-ttu-id="d6ffe-189">但在每个日期中，将按 **UnitsSold** 以降序对行进行排序。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-189">But within each date, it sorts the rows in descending order by **UnitsSold**.</span></span>

```powershell
Import-Csv C:\temp\sales-data.csv |
  Sort-Object Date, @{expr={$_.UnitsSold}; desc=$true}, Salesperson  |
    Select-Object Date, Salesperson, UnitsSold
```

```Output
Date       Salesperson UnitsSold
----       ----------- ---------
2020-08-01 Sally       3
2020-08-01 Anne        2
2020-08-01 Fred        1
2020-08-02 Anne        6
2020-08-02 Fred        2
2020-08-02 Sally       0
2020-08-03 Anne        5
2020-08-03 Sally       3
2020-08-03 Fred        1
2020-08-04 Anne        2
2020-08-04 Fred        2
2020-08-04 Sally       2
```

## <a name="notes"></a><span data-ttu-id="d6ffe-190">说明</span><span class="sxs-lookup"><span data-stu-id="d6ffe-190">Notes</span></span>

- <span data-ttu-id="d6ffe-191">您可以 _直接_ 指定表达式脚本块作为参数，而不是将其指定为 `Expression` 哈希表中的条目。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-191">You may specify the expression script block _directly_, as an argument, rather than specifying it as the `Expression` entry in a hashtable.</span></span> <span data-ttu-id="d6ffe-192">例如：</span><span class="sxs-lookup"><span data-stu-id="d6ffe-192">For example:</span></span>

  ```powershell
  '1', '10', '2' | Sort-Object { [int] $_ }
  ```

  <span data-ttu-id="d6ffe-193">此示例对于不需要 (或支持) 通过键命名属性（ `Name` 例如、和）的 cmdlet 非常方便 `Sort-Object` `Group-Object` `Measure-Object` 。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-193">This example is convenient for cmdlets that do not require (or support) naming a property via the `Name` key, such as `Sort-Object`, `Group-Object`, and `Measure-Object`.</span></span>

  <span data-ttu-id="d6ffe-194">对于支持命名属性的 cmdlet，脚本块会转换为字符串，并在输出中用作属性的名称。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-194">For cmdlets that support naming the property, the script block is converted to a string and used as the name of the property in the output.</span></span>

- <span data-ttu-id="d6ffe-195">`Expression` 脚本块在 _子_ 范围内运行，这意味着调用方的变量不能直接修改。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-195">`Expression` script blocks run in _child_ scopes, meaning that the caller's variables cannot be directly modified.</span></span>

- <span data-ttu-id="d6ffe-196">管道逻辑应用于脚本块的输出 `Expression` 。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-196">Pipeline logic is applied to the output from `Expression` script blocks.</span></span> <span data-ttu-id="d6ffe-197">这意味着输出单个元素数组将导致该数组解包。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-197">This means that outputting a single-element array causes that array to be unwrapped.</span></span>

- <span data-ttu-id="d6ffe-198">对于大多数 cmdlet，表达式脚本块中的错误都将不知不觉地忽略。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-198">For most cmdlets, errors inside expression script blocks are quietly ignored.</span></span>
  <span data-ttu-id="d6ffe-199">对于 `Sort-Object` ，语句终止和脚本终止错误是 _输出_ ，但不会终止语句。</span><span class="sxs-lookup"><span data-stu-id="d6ffe-199">For `Sort-Object`, statement-terminating and script-terminating errors are _output_ but they do not terminate the statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6ffe-200">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d6ffe-200">See Also</span></span>

[<span data-ttu-id="d6ffe-201">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="d6ffe-201">about_Hash_Tables</span></span>](about_hash_tables.md)

[<span data-ttu-id="d6ffe-202">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="d6ffe-202">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)

[<span data-ttu-id="d6ffe-203">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="d6ffe-203">ConvertTo-Html</span></span>](xref:Microsoft.PowerShell.Utility.ConvertTo-Html)

[<span data-ttu-id="d6ffe-204">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="d6ffe-204">Format-Custom</span></span>](xref:Microsoft.PowerShell.Utility.Format-Custom)

[<span data-ttu-id="d6ffe-205">Format-List</span><span class="sxs-lookup"><span data-stu-id="d6ffe-205">Format-List</span></span>](xref:Microsoft.PowerShell.Utility.Format-List)

[<span data-ttu-id="d6ffe-206">Format-Table</span><span class="sxs-lookup"><span data-stu-id="d6ffe-206">Format-Table</span></span>](xref:Microsoft.PowerShell.Utility.Format-Table)

[<span data-ttu-id="d6ffe-207">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="d6ffe-207">Format-Wide</span></span>](xref:Microsoft.PowerShell.Utility.Format-Wide)

[<span data-ttu-id="d6ffe-208">Group-Object</span><span class="sxs-lookup"><span data-stu-id="d6ffe-208">Group-Object</span></span>](xref:Microsoft.PowerShell.Utility.Group-Object)

[<span data-ttu-id="d6ffe-209">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="d6ffe-209">Measure-Object</span></span>](xref:Microsoft.PowerShell.Utility.Measure-Object)

[<span data-ttu-id="d6ffe-210">Select-Object</span><span class="sxs-lookup"><span data-stu-id="d6ffe-210">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)

[<span data-ttu-id="d6ffe-211">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="d6ffe-211">Sort-Object</span></span>](xref:Microsoft.PowerShell.Utility.Sort-Object)

[<span data-ttu-id="d6ffe-212">.NET 中的格式类型</span><span class="sxs-lookup"><span data-stu-id="d6ffe-212">Format types in .NET</span></span>](/dotnet/standard/base-types/formatting-types)
