---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-output?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Output
ms.openlocfilehash: 7e0c958201dbd1b42d1f4c4ee286b8aca1f8595a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598676"
---
# <span data-ttu-id="1502e-102">Write-Output</span><span class="sxs-lookup"><span data-stu-id="1502e-102">Write-Output</span></span>

## <span data-ttu-id="1502e-103">摘要</span><span class="sxs-lookup"><span data-stu-id="1502e-103">SYNOPSIS</span></span>
<span data-ttu-id="1502e-104">将指定的对象发送到管道中的下一个命令。</span><span class="sxs-lookup"><span data-stu-id="1502e-104">Sends the specified objects to the next command in the pipeline.</span></span> <span data-ttu-id="1502e-105">如果该命令是管道中的最后一个命令，则这些对象将在控制台中显示。</span><span class="sxs-lookup"><span data-stu-id="1502e-105">If the command is the last command in the pipeline, the objects are displayed in the console.</span></span>

## <span data-ttu-id="1502e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1502e-106">SYNTAX</span></span>

```
Write-Output [-InputObject] <PSObject[]> [-NoEnumerate] [<CommonParameters>]
```

## <span data-ttu-id="1502e-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1502e-107">DESCRIPTION</span></span>

<span data-ttu-id="1502e-108">`Write-Output`Cmdlet 将指定的对象沿管道向下发送到下一个命令。</span><span class="sxs-lookup"><span data-stu-id="1502e-108">The `Write-Output` cmdlet sends the specified object down the pipeline to the next command.</span></span>
<span data-ttu-id="1502e-109">如果该命令是管道中的最后一个命令，则该对象将在控制台中显示。</span><span class="sxs-lookup"><span data-stu-id="1502e-109">If the command is the last command in the pipeline, the object is displayed in the console.</span></span>

<span data-ttu-id="1502e-110">`Write-Output` 沿主要管道（也称为 "输出流" 或 "成功管道"）向下发送对象。</span><span class="sxs-lookup"><span data-stu-id="1502e-110">`Write-Output` sends objects down the primary pipeline, also known as the "output stream" or the "success pipeline."</span></span> <span data-ttu-id="1502e-111">若要通过错误管道向下发送错误对象，请使用 Write-Error。</span><span class="sxs-lookup"><span data-stu-id="1502e-111">To send error objects down the error pipeline, use Write-Error.</span></span>

<span data-ttu-id="1502e-112">此 cmdlet 通常在脚本中使用，以在控制台上显示字符串和其他对象。</span><span class="sxs-lookup"><span data-stu-id="1502e-112">This cmdlet is typically used in scripts to display strings and other objects on the console.</span></span> <span data-ttu-id="1502e-113">的内置别名之一是，与 `Write-Output` 使用的 `echo` 其他 shell 类似 `echo` ，默认行为是在管道末尾显示输出。</span><span class="sxs-lookup"><span data-stu-id="1502e-113">One of the built-in aliases for `Write-Output` is `echo` and similar to other shells that use `echo`, the default behavior is to display the output at the end of a pipeline.</span></span> <span data-ttu-id="1502e-114">在 PowerShell 中，通常不需要在默认情况下显示输出的实例中使用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1502e-114">In PowerShell, it is generally not necessary to use the cmdlet in instances where the output is displayed by default.</span></span> <span data-ttu-id="1502e-115">例如，`Get-Process | Write-Output` 等效于 `Get-Process`。</span><span class="sxs-lookup"><span data-stu-id="1502e-115">For example, `Get-Process | Write-Output` is equivalent to `Get-Process`.</span></span> <span data-ttu-id="1502e-116">或 `echo "Home directory: $HOME"` 可以写入 `"Home directory: $HOME"` 。</span><span class="sxs-lookup"><span data-stu-id="1502e-116">Or, `echo "Home directory: $HOME"` can be written, `"Home directory: $HOME"`.</span></span>

<span data-ttu-id="1502e-117">默认情况下，会 `Write-Output` 枚举提供给 cmdlet 的集合。</span><span class="sxs-lookup"><span data-stu-id="1502e-117">By default, `Write-Output` enumerates through collections provided to the cmdlet.</span></span> <span data-ttu-id="1502e-118">但是， `Write-Output` 还可用于将集合作为带有 **NoEnumerate** 参数的单个对象向下传递到管道。</span><span class="sxs-lookup"><span data-stu-id="1502e-118">However, `Write-Output` can also be used to pass collections down the pipeline as a single object with the **NoEnumerate** parameter.</span></span>

## <span data-ttu-id="1502e-119">示例</span><span class="sxs-lookup"><span data-stu-id="1502e-119">EXAMPLES</span></span>

### <span data-ttu-id="1502e-120">示例1：获取对象并将它们写入控制台</span><span class="sxs-lookup"><span data-stu-id="1502e-120">Example 1: Get objects and write them to the console</span></span>

```powershell
$P = Get-Process
Write-Output $P
```

<span data-ttu-id="1502e-121">第一个命令获取在计算机上运行的进程，并将其存储在 `$P` 变量中。</span><span class="sxs-lookup"><span data-stu-id="1502e-121">The first command gets processes running on the computer and stores them in the `$P` variable.</span></span>

<span data-ttu-id="1502e-122">第二个和第三个命令在控制台上显示中的进程对象 `$P` 。</span><span class="sxs-lookup"><span data-stu-id="1502e-122">The second and third commands display the process objects in `$P` on the console.</span></span>

### <span data-ttu-id="1502e-123">示例2：将输出传递给另一个 cmdlet</span><span class="sxs-lookup"><span data-stu-id="1502e-123">Example 2: Pass output to another cmdlet</span></span>

```powershell
Write-Output "test output" | Get-Member
```

<span data-ttu-id="1502e-124">此命令通过管道将 "测试输出" 字符串传递给 `Get-Member` cmdlet，该 cmdlet 将显示 **system.object** 类的成员，并演示该字符串是沿管道传递的。</span><span class="sxs-lookup"><span data-stu-id="1502e-124">This command pipes the "test output" string to the `Get-Member` cmdlet, which displays the members of the **System.String** class, demonstrating that the string was passed along the pipeline.</span></span>

### <span data-ttu-id="1502e-125">示例3：在输出中取消枚举</span><span class="sxs-lookup"><span data-stu-id="1502e-125">Example 3: Suppress enumeration in output</span></span>

```powershell
Write-Output 1,2,3 | Measure-Object
```

```Output
Count    : 3
...
```

```powershell
Write-Output 1,2,3 -NoEnumerate | Measure-Object
```

```Output
Count    : 1
...
```

<span data-ttu-id="1502e-126">此命令添加 **NoEnumerate** 参数以将集合或数组视为通过管道的单个对象。</span><span class="sxs-lookup"><span data-stu-id="1502e-126">This command adds the **NoEnumerate** parameter to treat a collection or array as a single object through the pipeline.</span></span>

## <span data-ttu-id="1502e-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1502e-127">PARAMETERS</span></span>

### <span data-ttu-id="1502e-128">-InputObject</span><span class="sxs-lookup"><span data-stu-id="1502e-128">-InputObject</span></span>

<span data-ttu-id="1502e-129">指定要通过管道向下发送的对象。</span><span class="sxs-lookup"><span data-stu-id="1502e-129">Specifies the objects to send down the pipeline.</span></span> <span data-ttu-id="1502e-130">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="1502e-130">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1502e-131">-NoEnumerate</span><span class="sxs-lookup"><span data-stu-id="1502e-131">-NoEnumerate</span></span>

<span data-ttu-id="1502e-132">默认情况下，该 `Write-Output` cmdlet 始终枚举其输出。</span><span class="sxs-lookup"><span data-stu-id="1502e-132">By default, the `Write-Output` cmdlet always enumerates its output.</span></span> <span data-ttu-id="1502e-133">**NoEnumerate** 参数取消默认行为，并阻止 `Write-Output` 枚举输出。</span><span class="sxs-lookup"><span data-stu-id="1502e-133">The **NoEnumerate** parameter suppresses the default behavior, and prevents `Write-Output` from enumerating output.</span></span> <span data-ttu-id="1502e-134">如果将命令括在括号中，则 **NoEnumerate** 参数不起作用，因为括号会强制执行枚举。</span><span class="sxs-lookup"><span data-stu-id="1502e-134">The **NoEnumerate** parameter has no effect if the command is wrapped in parentheses, because the parentheses force enumeration.</span></span> <span data-ttu-id="1502e-135">例如， `(Write-Output 1,2,3)` 仍枚举数组。</span><span class="sxs-lookup"><span data-stu-id="1502e-135">For example, `(Write-Output 1,2,3)` still enumerates the array.</span></span>

> [!NOTE]
> <span data-ttu-id="1502e-136">此开关仅适用于 PowerShell Core 6.2 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="1502e-136">This switch only works correctly with PowerShell Core 6.2 and newer.</span></span> <span data-ttu-id="1502e-137">在较旧版本的 PowerShell Core 上，即使使用此开关，也仍会枚举该集合。</span><span class="sxs-lookup"><span data-stu-id="1502e-137">On older versions of PowerShell Core, the collection is still enumerated even with use of this switch.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1502e-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1502e-138">CommonParameters</span></span>

<span data-ttu-id="1502e-139">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="1502e-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1502e-140">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1502e-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1502e-141">输入</span><span class="sxs-lookup"><span data-stu-id="1502e-141">INPUTS</span></span>

### <span data-ttu-id="1502e-142">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="1502e-142">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="1502e-143">可以通过管道将对象传递给 `Write-Output` 。</span><span class="sxs-lookup"><span data-stu-id="1502e-143">You can pipe objects to `Write-Output`.</span></span>

## <span data-ttu-id="1502e-144">输出</span><span class="sxs-lookup"><span data-stu-id="1502e-144">OUTPUTS</span></span>

### <span data-ttu-id="1502e-145">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="1502e-145">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="1502e-146">`Write-Output` 返回作为输入提交的对象。</span><span class="sxs-lookup"><span data-stu-id="1502e-146">`Write-Output` returns the objects that are submitted as input.</span></span>

## <span data-ttu-id="1502e-147">注释</span><span class="sxs-lookup"><span data-stu-id="1502e-147">NOTES</span></span>

## <span data-ttu-id="1502e-148">相关链接</span><span class="sxs-lookup"><span data-stu-id="1502e-148">RELATED LINKS</span></span>

[<span data-ttu-id="1502e-149">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="1502e-149">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="1502e-150">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="1502e-150">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="1502e-151">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="1502e-151">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="1502e-152">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="1502e-152">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="1502e-153">Write-Error</span><span class="sxs-lookup"><span data-stu-id="1502e-153">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="1502e-154">Write-Host</span><span class="sxs-lookup"><span data-stu-id="1502e-154">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="1502e-155">Write-Information</span><span class="sxs-lookup"><span data-stu-id="1502e-155">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="1502e-156">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="1502e-156">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="1502e-157">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="1502e-157">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="1502e-158">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="1502e-158">Write-Warning</span></span>](Write-Warning.md)
