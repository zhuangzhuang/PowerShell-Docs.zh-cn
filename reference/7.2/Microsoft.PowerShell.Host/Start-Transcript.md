---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/start-transcript?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transcript
ms.openlocfilehash: d0987c77e3c2bb8cee08e67610cd6fe4fedc36e4
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2021
ms.locfileid: "99596226"
---
# <span data-ttu-id="4b21d-102">Start-Transcript</span><span class="sxs-lookup"><span data-stu-id="4b21d-102">Start-Transcript</span></span>

## <span data-ttu-id="4b21d-103">摘要</span><span class="sxs-lookup"><span data-stu-id="4b21d-103">Synopsis</span></span>
<span data-ttu-id="4b21d-104">创建与文本文件的全部或部分 PowerShell 会话的记录。</span><span class="sxs-lookup"><span data-stu-id="4b21d-104">Creates a record of all or part of a PowerShell session to a text file.</span></span>

## <span data-ttu-id="4b21d-105">语法</span><span class="sxs-lookup"><span data-stu-id="4b21d-105">Syntax</span></span>

### <span data-ttu-id="4b21d-106">ByPath（默认值）</span><span class="sxs-lookup"><span data-stu-id="4b21d-106">ByPath (Default)</span></span>

```
Start-Transcript [[-Path] <String>] [-Append] [-Force] [-NoClobber] [-IncludeInvocationHeader]
 [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="4b21d-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="4b21d-107">ByLiteralPath</span></span>

```
Start-Transcript [[-LiteralPath] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="4b21d-108">ByOutputDirectory</span><span class="sxs-lookup"><span data-stu-id="4b21d-108">ByOutputDirectory</span></span>

```
Start-Transcript [[-OutputDirectory] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="4b21d-109">说明</span><span class="sxs-lookup"><span data-stu-id="4b21d-109">Description</span></span>

<span data-ttu-id="4b21d-110">`Start-Transcript`Cmdlet 可在文本文件中创建所有或部分 PowerShell 会话的记录。</span><span class="sxs-lookup"><span data-stu-id="4b21d-110">The `Start-Transcript` cmdlet creates a record of all or part of a PowerShell session to a text file.</span></span> <span data-ttu-id="4b21d-111">该脚本包括用户键入的所有命令和在控制台上显示的所有输出。</span><span class="sxs-lookup"><span data-stu-id="4b21d-111">The transcript includes all command that the user types and all output that appears on the console.</span></span>

<span data-ttu-id="4b21d-112">从 Windows PowerShell 5.0 开始，在 `Start-Transcript` 所有脚本的生成文件名中包含主机名。</span><span class="sxs-lookup"><span data-stu-id="4b21d-112">Starting in Windows PowerShell 5.0, `Start-Transcript` includes the hostname in the generated file name of all transcripts.</span></span> <span data-ttu-id="4b21d-113">这在集中处理企业的日志记录时尤其有用。</span><span class="sxs-lookup"><span data-stu-id="4b21d-113">This is especially useful when your enterprise's logging is centralized.</span></span>
<span data-ttu-id="4b21d-114">Cmdlet 创建的文件 `Start-Transcript` 在名称中包含随机字符，以防止在两个或多个脚本同时启动时可能覆盖或重复。</span><span class="sxs-lookup"><span data-stu-id="4b21d-114">Files that are created by the `Start-Transcript` cmdlet include random characters in names to prevent potential overwrites or duplication when two or more transcripts are started simultaneously.</span></span>
<span data-ttu-id="4b21d-115">这还可以防止未经授权地发现存储在集中文件共享中的脚本。</span><span class="sxs-lookup"><span data-stu-id="4b21d-115">This also prevents unauthorized discovery of transcripts that are stored in a centralized file share.</span></span>

<span data-ttu-id="4b21d-116">如果目标文件在 BOM)  (没有字节顺序标记， `Start-Transcript` 则默认为 `Utf8NoBom` 目标文件中的编码。</span><span class="sxs-lookup"><span data-stu-id="4b21d-116">If the target file doesn't have a Byte Order Mark (BOM), `Start-Transcript` defaults to `Utf8NoBom` encoding in the target file.</span></span>

## <span data-ttu-id="4b21d-117">示例</span><span class="sxs-lookup"><span data-stu-id="4b21d-117">Examples</span></span>

### <span data-ttu-id="4b21d-118">示例 1：在使用默认设置的情况下启动脚本文件</span><span class="sxs-lookup"><span data-stu-id="4b21d-118">Example 1: Start a transcript file with default settings</span></span>

```powershell
Start-Transcript
```

<span data-ttu-id="4b21d-119">此命令将启动默认文件位置中的脚本。</span><span class="sxs-lookup"><span data-stu-id="4b21d-119">This command starts a transcript in the default file location.</span></span>

### <span data-ttu-id="4b21d-120">示例 2：在特定位置启动脚本文件</span><span class="sxs-lookup"><span data-stu-id="4b21d-120">Example 2: Start a transcript file at a specific location</span></span>

```powershell
Start-Transcript -Path "C:\transcripts\transcript0.txt" -NoClobber
```

<span data-ttu-id="4b21d-121">此命令启动中文件中的脚本 `Transcript0.txt` `C:\transcripts` 。</span><span class="sxs-lookup"><span data-stu-id="4b21d-121">This command starts a transcript in the `Transcript0.txt` file in `C:\transcripts`.</span></span> <span data-ttu-id="4b21d-122">因为使用了 NoClobber 参数，所以此命令可防止覆盖任何现有文件。</span><span class="sxs-lookup"><span data-stu-id="4b21d-122">Since the **NoClobber** parameter is used, the command prevents any existing files from being overwritten.</span></span> <span data-ttu-id="4b21d-123">如果 `Transcript0.txt` 文件已存在，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="4b21d-123">If the `Transcript0.txt` file already exists, the command fails.</span></span>

## <span data-ttu-id="4b21d-124">参数</span><span class="sxs-lookup"><span data-stu-id="4b21d-124">Parameters</span></span>

### <span data-ttu-id="4b21d-125">-Append</span><span class="sxs-lookup"><span data-stu-id="4b21d-125">-Append</span></span>

<span data-ttu-id="4b21d-126">指示此 cmdlet 将新脚本添加到现有文件末尾。</span><span class="sxs-lookup"><span data-stu-id="4b21d-126">Indicates that this cmdlet adds the new transcript to the end of an existing file.</span></span> <span data-ttu-id="4b21d-127">使用 **Path** 参数指定文件。</span><span class="sxs-lookup"><span data-stu-id="4b21d-127">Use the **Path** parameter to specify the file.</span></span>

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

### <span data-ttu-id="4b21d-128">-Force</span><span class="sxs-lookup"><span data-stu-id="4b21d-128">-Force</span></span>

<span data-ttu-id="4b21d-129">允许 cmdlet 将该脚本追加到现有的只读文件。</span><span class="sxs-lookup"><span data-stu-id="4b21d-129">Allows the cmdlet to append the transcript to an existing read-only file.</span></span> <span data-ttu-id="4b21d-130">在只读文件上使用时，该 cmdlet 会将文件权限更改为读写。</span><span class="sxs-lookup"><span data-stu-id="4b21d-130">When used on a read-only file, the cmdlet changes the file permission to read-write.</span></span> <span data-ttu-id="4b21d-131">使用此参数时，cmdlet 无法覆盖安全限制。</span><span class="sxs-lookup"><span data-stu-id="4b21d-131">The cmdlet cannot override security restrictions when this parameter is used.</span></span>

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

### <span data-ttu-id="4b21d-132">-IncludeInvocationHeader</span><span class="sxs-lookup"><span data-stu-id="4b21d-132">-IncludeInvocationHeader</span></span>

<span data-ttu-id="4b21d-133">指示此 cmdlet 记录命令运行时的时间戳。</span><span class="sxs-lookup"><span data-stu-id="4b21d-133">Indicates that this cmdlet logs the time stamp when commands are run.</span></span>

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

### <span data-ttu-id="4b21d-134">-UseMinimalHeader</span><span class="sxs-lookup"><span data-stu-id="4b21d-134">-UseMinimalHeader</span></span>

<span data-ttu-id="4b21d-135">在脚本前面追加短标题，而不是默认包含的详细标头。</span><span class="sxs-lookup"><span data-stu-id="4b21d-135">Prepend a short header to the transcript, instead of the detailed header included by default.</span></span> <span data-ttu-id="4b21d-136">此参数是在 PowerShell 6.2 中添加的。</span><span class="sxs-lookup"><span data-stu-id="4b21d-136">This parameter was added in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="4b21d-137">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4b21d-137">-LiteralPath</span></span>

<span data-ttu-id="4b21d-138">指定脚本文件的位置。</span><span class="sxs-lookup"><span data-stu-id="4b21d-138">Specifies a location to the transcript file.</span></span> <span data-ttu-id="4b21d-139">与 **Path** 参数不同，**LiteralPath** 参数的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="4b21d-139">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="4b21d-140">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="4b21d-140">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="4b21d-141">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="4b21d-141">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="4b21d-142">单引号通知 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="4b21d-142">Single quotation marks inform PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b21d-143">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="4b21d-143">-NoClobber</span></span>

<span data-ttu-id="4b21d-144">指示此 cmdlet 不会覆盖现有文件。</span><span class="sxs-lookup"><span data-stu-id="4b21d-144">Indicates that this cmdlet will not overwrite of an existing file.</span></span> <span data-ttu-id="4b21d-145">默认情况下，如果指定路径中存在脚本文件，则将 `Start-Transcript` 覆盖该文件而不发出警告。</span><span class="sxs-lookup"><span data-stu-id="4b21d-145">By default, if a transcript file exists in the specified path, `Start-Transcript` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b21d-146">-OutputDirectory</span><span class="sxs-lookup"><span data-stu-id="4b21d-146">-OutputDirectory</span></span>

<span data-ttu-id="4b21d-147">指定要在其中保存脚本的特定路径和文件夹。</span><span class="sxs-lookup"><span data-stu-id="4b21d-147">Specifies a specific path and folder in which to save a transcript.</span></span> <span data-ttu-id="4b21d-148">PowerShell 会自动分配脚本名称。</span><span class="sxs-lookup"><span data-stu-id="4b21d-148">PowerShell automatically assigns the transcript name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByOutputDirectory
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b21d-149">-Path</span><span class="sxs-lookup"><span data-stu-id="4b21d-149">-Path</span></span>

<span data-ttu-id="4b21d-150">指定脚本文件的位置。</span><span class="sxs-lookup"><span data-stu-id="4b21d-150">Specifies a location to the transcript file.</span></span> <span data-ttu-id="4b21d-151">输入文件的路径 `.txt` 。</span><span class="sxs-lookup"><span data-stu-id="4b21d-151">Enter a path to a `.txt` file.</span></span> <span data-ttu-id="4b21d-152">不允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="4b21d-152">Wildcards are not permitted.</span></span>

<span data-ttu-id="4b21d-153">如果未指定路径，将 `Start-Transcript` 使用全局变量的值中的路径 `$Transcript` 。</span><span class="sxs-lookup"><span data-stu-id="4b21d-153">If you do not specify a path, `Start-Transcript` uses the path in the value of the `$Transcript` global variable.</span></span> <span data-ttu-id="4b21d-154">如果尚未创建此变量，请将 `Start-Transcript` 这些脚本存储在 `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` 文件中。</span><span class="sxs-lookup"><span data-stu-id="4b21d-154">If you have not created this variable, `Start-Transcript` stores the transcripts in the `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` files.</span></span>

<span data-ttu-id="4b21d-155">如果路径中不存在任何目录，该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="4b21d-155">If any of the directories in the path do not exist, the command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b21d-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4b21d-156">-Confirm</span></span>

<span data-ttu-id="4b21d-157">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="4b21d-157">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b21d-158">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4b21d-158">-WhatIf</span></span>

<span data-ttu-id="4b21d-159">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="4b21d-159">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4b21d-160">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="4b21d-160">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b21d-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4b21d-161">CommonParameters</span></span>

<span data-ttu-id="4b21d-162">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4b21d-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4b21d-163">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4b21d-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4b21d-164">输入</span><span class="sxs-lookup"><span data-stu-id="4b21d-164">Inputs</span></span>

### <span data-ttu-id="4b21d-165">无</span><span class="sxs-lookup"><span data-stu-id="4b21d-165">None</span></span>

<span data-ttu-id="4b21d-166">不能通过管道将对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4b21d-166">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="4b21d-167">输出</span><span class="sxs-lookup"><span data-stu-id="4b21d-167">Outputs</span></span>

### <span data-ttu-id="4b21d-168">System.String</span><span class="sxs-lookup"><span data-stu-id="4b21d-168">System.String</span></span>

<span data-ttu-id="4b21d-169">此 cmdlet 将返回一个字符串，包含一条确认消息和输出文件的路径。</span><span class="sxs-lookup"><span data-stu-id="4b21d-169">This cmdlet returns a string that contains a confirmation message and the path to the output file.</span></span>

## <span data-ttu-id="4b21d-170">说明</span><span class="sxs-lookup"><span data-stu-id="4b21d-170">Notes</span></span>

<span data-ttu-id="4b21d-171">若要停止脚本，请使用 `Stop-Transcript` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4b21d-171">To stop a transcript, use the `Stop-Transcript` cmdlet.</span></span>

<span data-ttu-id="4b21d-172">若要记录整个会话，请将 `Start-Transcript` 命令添加到配置文件。</span><span class="sxs-lookup"><span data-stu-id="4b21d-172">To record an entire session, add the `Start-Transcript` command to your profile.</span></span> <span data-ttu-id="4b21d-173">有关详细信息，请参阅 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="4b21d-173">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

## <span data-ttu-id="4b21d-174">相关链接</span><span class="sxs-lookup"><span data-stu-id="4b21d-174">Related Links</span></span>

[<span data-ttu-id="4b21d-175">Stop-Transcript</span><span class="sxs-lookup"><span data-stu-id="4b21d-175">Stop-Transcript</span></span>](Stop-Transcript.md)
