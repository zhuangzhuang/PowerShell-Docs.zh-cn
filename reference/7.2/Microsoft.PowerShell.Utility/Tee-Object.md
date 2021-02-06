---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/tee-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Tee-Object
ms.openlocfilehash: 5fd1ff9760cbddeb0c5c29052caf0f36d6d760d0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598467"
---
# <span data-ttu-id="b7abf-102">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="b7abf-102">Tee-Object</span></span>

## <span data-ttu-id="b7abf-103">摘要</span><span class="sxs-lookup"><span data-stu-id="b7abf-103">SYNOPSIS</span></span>
<span data-ttu-id="b7abf-104">将命令输出保存在文件或变量中，同时通过管道向下发送。</span><span class="sxs-lookup"><span data-stu-id="b7abf-104">Saves command output in a file or variable and also sends it down the pipeline.</span></span>

## <span data-ttu-id="b7abf-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b7abf-105">SYNTAX</span></span>

### <span data-ttu-id="b7abf-106">File（默认值）</span><span class="sxs-lookup"><span data-stu-id="b7abf-106">File (Default)</span></span>

```
Tee-Object [-InputObject <PSObject>] [-FilePath] <String> [-Append] [<CommonParameters>]
```

### <span data-ttu-id="b7abf-107">LiteralFile</span><span class="sxs-lookup"><span data-stu-id="b7abf-107">LiteralFile</span></span>

```
Tee-Object [-InputObject <PSObject>] -LiteralPath <String> [<CommonParameters>]
```

### <span data-ttu-id="b7abf-108">变量</span><span class="sxs-lookup"><span data-stu-id="b7abf-108">Variable</span></span>

```
Tee-Object [-InputObject <PSObject>] -Variable <String> [<CommonParameters>]
```

## <span data-ttu-id="b7abf-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b7abf-109">DESCRIPTION</span></span>

<span data-ttu-id="b7abf-110">`Tee-Object`Cmdlet 将重定向输出，即它以两个方向发送命令的输出 (如字母 T) 。</span><span class="sxs-lookup"><span data-stu-id="b7abf-110">The `Tee-Object` cmdlet redirects output, that is, it sends the output of a command in two directions (like the letter T).</span></span> <span data-ttu-id="b7abf-111">它将输出存储在文件或变量中，同时通过管道向下发送。</span><span class="sxs-lookup"><span data-stu-id="b7abf-111">It stores the output in a file or variable and also sends it down the pipeline.</span></span> <span data-ttu-id="b7abf-112">如果 `Tee-Object` 是管道中的最后一个命令，则命令输出将显示在提示符处。</span><span class="sxs-lookup"><span data-stu-id="b7abf-112">If `Tee-Object` is the last command in the pipeline, the command output is displayed at the prompt.</span></span>

## <span data-ttu-id="b7abf-113">示例</span><span class="sxs-lookup"><span data-stu-id="b7abf-113">EXAMPLES</span></span>

### <span data-ttu-id="b7abf-114">示例1：向文件和控制台输出进程</span><span class="sxs-lookup"><span data-stu-id="b7abf-114">Example 1: Output processes to a file and to the console</span></span>

<span data-ttu-id="b7abf-115">此示例获取计算机上运行的进程的列表，并将结果发送到文件。</span><span class="sxs-lookup"><span data-stu-id="b7abf-115">This example gets a list of the processes running on the computer and sends the result to a file.</span></span>
<span data-ttu-id="b7abf-116">由于未指定第二个路径，因此进程也会显示在控制台中。</span><span class="sxs-lookup"><span data-stu-id="b7abf-116">Because a second path is not specified, the processes are also displayed in the console.</span></span>

```powershell
Get-Process | Tee-Object -FilePath "C:\Test1\testfile2.txt"
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
83       4     2300       4520    39     0.30    4032 00THotkey
272      6     1400       3944    34     0.06    3088 alg
81       3      804       3284    21     2.45     148 ApntEx
81       4     2008       5808    38     0.75    3684 Apoint
...
```

### <span data-ttu-id="b7abf-117">示例2：将进程输出到变量并 `Select-Object`</span><span class="sxs-lookup"><span data-stu-id="b7abf-117">Example 2: Output processes to a variable and `Select-Object`</span></span>

<span data-ttu-id="b7abf-118">此示例获取在计算机上运行的进程的列表，将其保存到 `$proc` 变量，然后将其传递给 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="b7abf-118">This example gets a list of the processes running on the computer, saves them to the `$proc` variable, and pipes them to `Select-Object`.</span></span>

```powershell
Get-Process notepad | Tee-Object -Variable proc | Select-Object processname,handles
```

```Output
ProcessName                              Handles
-----------                              -------
notepad                                  43
notepad                                  37
notepad                                  38
notepad                                  38
```

<span data-ttu-id="b7abf-119">`Select-Object`Cmdlet 将选择 **ProcessName** 并 **处理** 属性。</span><span class="sxs-lookup"><span data-stu-id="b7abf-119">The `Select-Object` cmdlet selects the **ProcessName** and **Handles** properties.</span></span> <span data-ttu-id="b7abf-120">请注意， `$proc` 变量包括返回的默认信息 `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="b7abf-120">Note that the `$proc` variable includes the default information returned by `Get-Process`.</span></span>

### <span data-ttu-id="b7abf-121">示例3：将系统文件输出到两个日志文件</span><span class="sxs-lookup"><span data-stu-id="b7abf-121">Example 3: Output system files to two log files</span></span>

<span data-ttu-id="b7abf-122">此示例将系统文件的列表保存在两个日志文件中，即累计文件和当前文件。</span><span class="sxs-lookup"><span data-stu-id="b7abf-122">This example saves a list of system files in a two log files, a cumulative file and a current file.</span></span>

```powershell
Get-ChildItem -Path D: -File -System -Recurse |
  Tee-Object -FilePath "c:\test\AllSystemFiles.txt" -Append |
    Out-File c:\test\NewSystemFiles.txt
```

<span data-ttu-id="b7abf-123">该命令使用 `Get-ChildItem` cmdlet 对 D：驱动器上的系统文件执行递归搜索。</span><span class="sxs-lookup"><span data-stu-id="b7abf-123">The command uses the `Get-ChildItem` cmdlet to do a recursive search for system files on the D: drive.</span></span> <span data-ttu-id="b7abf-124">管道运算符 (|) 会将列表发送到 `Tee-Object` ，后者会将列表追加到 AllSystemFiles.txt 文件，并将该列表向下传递到 `Out-File` cmdlet，这会将列表保存在 NewSystemFiles.txt 文件中。</span><span class="sxs-lookup"><span data-stu-id="b7abf-124">A pipeline operator (|) sends the list to `Tee-Object`, which appends the list to the AllSystemFiles.txt file and passes the list down the pipeline to the `Out-File` cmdlet, which saves the list in the NewSystemFiles.txt file.</span></span>

## <span data-ttu-id="b7abf-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b7abf-125">PARAMETERS</span></span>

### <span data-ttu-id="b7abf-126">-Append</span><span class="sxs-lookup"><span data-stu-id="b7abf-126">-Append</span></span>

<span data-ttu-id="b7abf-127">指示 cmdlet 将输出追加到指定的文件。</span><span class="sxs-lookup"><span data-stu-id="b7abf-127">Indicates that the cmdlet appends the output to the specified file.</span></span> <span data-ttu-id="b7abf-128">在没有此参数的情况下，新内容将替换文件中的所有现有内容，而不显示警告。</span><span class="sxs-lookup"><span data-stu-id="b7abf-128">Without this parameter, the new content replaces any existing content in the file without warning.</span></span>

<span data-ttu-id="b7abf-129">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="b7abf-129">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7abf-130">-FilePath</span><span class="sxs-lookup"><span data-stu-id="b7abf-130">-FilePath</span></span>

<span data-ttu-id="b7abf-131">指定一个文件，此 cmdlet 允许将对象保存到通配符，但必须解析为单个文件。</span><span class="sxs-lookup"><span data-stu-id="b7abf-131">Specifies a file that this cmdlet saves the object to Wildcard characters are permitted, but must resolve to a single file.</span></span>

```yaml
Type: System.String
Parameter Sets: File
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="b7abf-132">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b7abf-132">-InputObject</span></span>

<span data-ttu-id="b7abf-133">指定要保存和显示的对象。</span><span class="sxs-lookup"><span data-stu-id="b7abf-133">Specifies the object to be saved and displayed.</span></span> <span data-ttu-id="b7abf-134">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="b7abf-134">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="b7abf-135">还可以通过管道将对象传递给 `Tee-Object` 。</span><span class="sxs-lookup"><span data-stu-id="b7abf-135">You can also pipe an object to `Tee-Object`.</span></span>

<span data-ttu-id="b7abf-136">当你将 **inputobject** 参数与一起使用时 `Tee-Object` ， `Tee-Object` **inputobject** 值将被视为单个对象（即使该值是集合）。</span><span class="sxs-lookup"><span data-stu-id="b7abf-136">When you use the **InputObject** parameter with `Tee-Object`, instead of piping command results to `Tee-Object`, the **InputObject** value is treated as a single object even if the value is a collection.</span></span>

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

### <span data-ttu-id="b7abf-137">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b7abf-137">-LiteralPath</span></span>

<span data-ttu-id="b7abf-138">指定此 cmdlet 将对象保存到的文件。</span><span class="sxs-lookup"><span data-stu-id="b7abf-138">Specifies a file that this cmdlet saves the object to.</span></span> <span data-ttu-id="b7abf-139">与 **FilePath** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="b7abf-139">Unlike **FilePath**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="b7abf-140">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="b7abf-140">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b7abf-141">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="b7abf-141">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b7abf-142">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="b7abf-142">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7abf-143">-Variable</span><span class="sxs-lookup"><span data-stu-id="b7abf-143">-Variable</span></span>

<span data-ttu-id="b7abf-144">指定该 cmdlet 将对象保存到的变量。</span><span class="sxs-lookup"><span data-stu-id="b7abf-144">Specifies a variable that the cmdlet saves the object to.</span></span> <span data-ttu-id="b7abf-145">输入一个变量名称，其中不含前面的美元符号 (`$`) 。</span><span class="sxs-lookup"><span data-stu-id="b7abf-145">Enter a variable name without the preceding dollar sign (`$`).</span></span>

```yaml
Type: System.String
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7abf-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b7abf-146">CommonParameters</span></span>

<span data-ttu-id="b7abf-147">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b7abf-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b7abf-148">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b7abf-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b7abf-149">输入</span><span class="sxs-lookup"><span data-stu-id="b7abf-149">INPUTS</span></span>

### <span data-ttu-id="b7abf-150">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="b7abf-150">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b7abf-151">可以通过管道将对象传递给 `Tee-Object` 。</span><span class="sxs-lookup"><span data-stu-id="b7abf-151">You can pipe objects to `Tee-Object`.</span></span>

## <span data-ttu-id="b7abf-152">输出</span><span class="sxs-lookup"><span data-stu-id="b7abf-152">OUTPUTS</span></span>

### <span data-ttu-id="b7abf-153">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="b7abf-153">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b7abf-154">`Tee-Object` 返回它重定向的对象。</span><span class="sxs-lookup"><span data-stu-id="b7abf-154">`Tee-Object` returns the object that it redirects.</span></span>

## <span data-ttu-id="b7abf-155">注释</span><span class="sxs-lookup"><span data-stu-id="b7abf-155">NOTES</span></span>

<span data-ttu-id="b7abf-156">你还可以使用 `Out-File` cmdlet 或重定向运算符，这两个运算符都将输出保存在文件中，但不会向下发送管道。</span><span class="sxs-lookup"><span data-stu-id="b7abf-156">You can also use the `Out-File` cmdlet or the redirection operator, both of which save the output in a file but do not send it down the pipeline.</span></span>

<span data-ttu-id="b7abf-157">从 PowerShell 6 开始，在 `Tee-Object` 写入文件时，使用不带 BOM 的 utf-8 编码。</span><span class="sxs-lookup"><span data-stu-id="b7abf-157">Beginning in PowerShell 6, `Tee-Object` uses BOM-less UTF-8 encoding when it writes to files.</span></span> <span data-ttu-id="b7abf-158">如果需要其他编码，请将 `Out-File` cmdlet 与 **encoding** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="b7abf-158">If you need a different encoding, use the `Out-File` cmdlet with the **Encoding** parameter.</span></span>

## <span data-ttu-id="b7abf-159">相关链接</span><span class="sxs-lookup"><span data-stu-id="b7abf-159">RELATED LINKS</span></span>

[<span data-ttu-id="b7abf-160">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="b7abf-160">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="b7abf-161">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="b7abf-161">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="b7abf-162">Group-Object</span><span class="sxs-lookup"><span data-stu-id="b7abf-162">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="b7abf-163">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="b7abf-163">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="b7abf-164">New-Object</span><span class="sxs-lookup"><span data-stu-id="b7abf-164">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="b7abf-165">Select-Object</span><span class="sxs-lookup"><span data-stu-id="b7abf-165">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="b7abf-166">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="b7abf-166">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="b7abf-167">Where-Object</span><span class="sxs-lookup"><span data-stu-id="b7abf-167">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

[<span data-ttu-id="b7abf-168">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="b7abf-168">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

