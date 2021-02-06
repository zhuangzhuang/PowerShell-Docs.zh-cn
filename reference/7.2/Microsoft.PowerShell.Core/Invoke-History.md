---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-History
ms.openlocfilehash: 7fb4341a84706f7d31d463bb527a1a31f387c2ae
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596645"
---
# <span data-ttu-id="b9954-102">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="b9954-102">Invoke-History</span></span>

## <span data-ttu-id="b9954-103">摘要</span><span class="sxs-lookup"><span data-stu-id="b9954-103">SYNOPSIS</span></span>
<span data-ttu-id="b9954-104">从会话历史记录中运行命令。</span><span class="sxs-lookup"><span data-stu-id="b9954-104">Runs commands from the session history.</span></span>

## <span data-ttu-id="b9954-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b9954-105">SYNTAX</span></span>

```
Invoke-History [[-Id] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b9954-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b9954-106">DESCRIPTION</span></span>

<span data-ttu-id="b9954-107">`Invoke-History`Cmdlet 从会话历史记录中运行命令。</span><span class="sxs-lookup"><span data-stu-id="b9954-107">The `Invoke-History` cmdlet runs commands from the session history.</span></span> <span data-ttu-id="b9954-108">您可以将表示命令的对象从 Get-History 传递到 `Invoke-History` ，也可以通过使用其 **Id** 号来标识当前历史记录中的命令。</span><span class="sxs-lookup"><span data-stu-id="b9954-108">You can pass objects representing the commands from Get-History to `Invoke-History`, or you can identify commands in the current history by using their **Id** number.</span></span> <span data-ttu-id="b9954-109">若要查找命令的标识号，请使用 `Get-History` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b9954-109">To find the identification number of a command, use the `Get-History` cmdlet.</span></span>

<span data-ttu-id="b9954-110">会话历史记录与 **PSReadLine** 模块维护的历史记录分开管理。</span><span class="sxs-lookup"><span data-stu-id="b9954-110">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="b9954-111">在加载 **PSReadLine** 的会话中提供两个历史记录。</span><span class="sxs-lookup"><span data-stu-id="b9954-111">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="b9954-112">此 cmdlet 仅适用于会话历史记录。</span><span class="sxs-lookup"><span data-stu-id="b9954-112">This cmdlet only works with the session history.</span></span> <span data-ttu-id="b9954-113">有关详细信息，请参阅 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。</span><span class="sxs-lookup"><span data-stu-id="b9954-113">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="b9954-114">示例</span><span class="sxs-lookup"><span data-stu-id="b9954-114">EXAMPLES</span></span>

### <span data-ttu-id="b9954-115">示例1：运行历史记录中的最新命令</span><span class="sxs-lookup"><span data-stu-id="b9954-115">Example 1: Run the most recent command in the history</span></span>

<span data-ttu-id="b9954-116">此示例在会话历史记录中运行最后一个或最新的命令。</span><span class="sxs-lookup"><span data-stu-id="b9954-116">This example runs the last, or most recent, command in the session history.</span></span> <span data-ttu-id="b9954-117">可以将此命令缩写为 `r` 的别名 `Invoke-History` 。</span><span class="sxs-lookup"><span data-stu-id="b9954-117">You can abbreviate this command as `r`, the alias for `Invoke-History`.</span></span>

```powershell
Invoke-History
```

### <span data-ttu-id="b9954-118">示例2：运行具有指定 ID 的命令</span><span class="sxs-lookup"><span data-stu-id="b9954-118">Example 2: Run the command that has a specified ID</span></span>

<span data-ttu-id="b9954-119">此示例在 **Id** 为132的会话历史记录中运行命令。</span><span class="sxs-lookup"><span data-stu-id="b9954-119">This example runs the command in the session history with **Id** 132.</span></span> <span data-ttu-id="b9954-120">由于 **Id** 参数的名称是可选的，因此可以将此命令缩写为： `Invoke-History 132` 、 `ihy 132` 或 `r 132` 。</span><span class="sxs-lookup"><span data-stu-id="b9954-120">Because the name of the **Id** parameter is optional, you can abbreviate this command as the following: `Invoke-History 132`, `ihy 132`, or `r 132`.</span></span>

```powershell
Invoke-History -Id 132
```

### <span data-ttu-id="b9954-121">示例3：使用命令文本运行最新命令</span><span class="sxs-lookup"><span data-stu-id="b9954-121">Example 3: Run the most recent command by using the command text</span></span>

<span data-ttu-id="b9954-122">此示例运行 `Get-Process` 会话历史记录中的最新命令。</span><span class="sxs-lookup"><span data-stu-id="b9954-122">This example runs the most recent `Get-Process` command in the session history.</span></span> <span data-ttu-id="b9954-123">键入 **Id** 参数的字符时， `Invoke-History` 会从最新命令开始，运行它发现的与该模式匹配的第一个命令。</span><span class="sxs-lookup"><span data-stu-id="b9954-123">When you type characters for the **Id** parameter, `Invoke-History` runs the first command that it finds that matches the pattern, starting with the most recent commands.</span></span>

```powershell
Invoke-History -Id get-pr
```

> [!NOTE]
> <span data-ttu-id="b9954-124">模式匹配不区分大小写，但模式与行的开头匹配。</span><span class="sxs-lookup"><span data-stu-id="b9954-124">Pattern matching is case-insensitive, but the pattern matches the beginning of the line.</span></span>

### <span data-ttu-id="b9954-125">示例4：从历史记录中运行命令序列</span><span class="sxs-lookup"><span data-stu-id="b9954-125">Example 4: Run a sequence of commands from the history</span></span>

<span data-ttu-id="b9954-126">此示例运行命令16至24。</span><span class="sxs-lookup"><span data-stu-id="b9954-126">This example runs commands 16 through 24.</span></span> <span data-ttu-id="b9954-127">由于只能列出一个 **id** 值，因此该命令将使用 `ForEach-Object` cmdlet 对 `Invoke-History` 每个 **id** 值运行一次此命令。</span><span class="sxs-lookup"><span data-stu-id="b9954-127">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command one time for each **Id** value.</span></span>

```powershell
16..24 | ForEach {Invoke-History -Id $_ }
```

### <span data-ttu-id="b9954-128">示例 5</span><span class="sxs-lookup"><span data-stu-id="b9954-128">Example 5</span></span>

<span data-ttu-id="b9954-129">此示例运行历史记录中以命令 255 (249 到 255) 结束的七个命令。</span><span class="sxs-lookup"><span data-stu-id="b9954-129">This example runs the seven commands in the history that end with command 255 (249 through 255).</span></span> <span data-ttu-id="b9954-130">它使用 `Get-History` cmdlet 检索命令。</span><span class="sxs-lookup"><span data-stu-id="b9954-130">It uses the `Get-History` cmdlet to retrieve the commands.</span></span> <span data-ttu-id="b9954-131">由于只能列出一个 **id** 值，因此该命令将使用 `ForEach-Object` cmdlet 对 `Invoke-History` 每个 **id** 值运行一次命令。</span><span class="sxs-lookup"><span data-stu-id="b9954-131">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command once for each **Id** value.</span></span>

```powershell
Get-History -Id 255 -Count 7 | ForEach {Invoke-History -Id $_.Id}
```

## <span data-ttu-id="b9954-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b9954-132">PARAMETERS</span></span>

### <span data-ttu-id="b9954-133">-Id</span><span class="sxs-lookup"><span data-stu-id="b9954-133">-Id</span></span>

<span data-ttu-id="b9954-134">指定历史记录中命令的 **Id** 。</span><span class="sxs-lookup"><span data-stu-id="b9954-134">Specifies the **Id** of a command in the history.</span></span> <span data-ttu-id="b9954-135">你可以键入命令的 **Id** 号或命令的前几个字符。</span><span class="sxs-lookup"><span data-stu-id="b9954-135">You can type the **Id** number of the command or the first few characters of the command.</span></span>

<span data-ttu-id="b9954-136">如果键入字符，则 `Invoke-History` 先匹配最新的命令。</span><span class="sxs-lookup"><span data-stu-id="b9954-136">If you type characters, `Invoke-History` matches the most recent commands first.</span></span> <span data-ttu-id="b9954-137">如果省略此参数，则 `Invoke-History` 运行最后一个或最新的命令。</span><span class="sxs-lookup"><span data-stu-id="b9954-137">If you omit this parameter, `Invoke-History` runs the last, or most recent, command.</span></span> <span data-ttu-id="b9954-138">若要查找命令的 **Id** 号，请使用 `Get-History` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b9954-138">To find the **Id** number of a command, use the `Get-History` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b9954-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b9954-139">-Confirm</span></span>

<span data-ttu-id="b9954-140">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="b9954-140">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b9954-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b9954-141">-WhatIf</span></span>

<span data-ttu-id="b9954-142">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="b9954-142">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b9954-143">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="b9954-143">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b9954-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b9954-144">CommonParameters</span></span>

<span data-ttu-id="b9954-145">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b9954-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b9954-146">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b9954-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b9954-147">输入</span><span class="sxs-lookup"><span data-stu-id="b9954-147">INPUTS</span></span>

### <span data-ttu-id="b9954-148">System.String</span><span class="sxs-lookup"><span data-stu-id="b9954-148">System.String</span></span>

<span data-ttu-id="b9954-149">可以通过管道将历史记录 **Id** 传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b9954-149">You can pipe a history **Id** to this cmdlet.</span></span>

## <span data-ttu-id="b9954-150">输出</span><span class="sxs-lookup"><span data-stu-id="b9954-150">OUTPUTS</span></span>

### <span data-ttu-id="b9954-151">无</span><span class="sxs-lookup"><span data-stu-id="b9954-151">None</span></span>

<span data-ttu-id="b9954-152">此 cmdlet 不会生成任何输出，但输出可能由运行的命令生成 `Invoke-History` 。</span><span class="sxs-lookup"><span data-stu-id="b9954-152">This cmdlet does not generate any output, but output might be generated by the commands that `Invoke-History` runs.</span></span>

## <span data-ttu-id="b9954-153">注释</span><span class="sxs-lookup"><span data-stu-id="b9954-153">NOTES</span></span>

<span data-ttu-id="b9954-154">会话历史记录是在会话期间输入的命令的列表。</span><span class="sxs-lookup"><span data-stu-id="b9954-154">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="b9954-155">会话历史记录表示命令的执行顺序、状态以及开始和结束时间。</span><span class="sxs-lookup"><span data-stu-id="b9954-155">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="b9954-156">当你输入每个命令时，PowerShell 会将其添加到历史记录，以便你可以重复使用它。</span><span class="sxs-lookup"><span data-stu-id="b9954-156">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="b9954-157">有关会话历史记录的详细信息，请参阅 [about_History](About/about_History.md)。</span><span class="sxs-lookup"><span data-stu-id="b9954-157">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="b9954-158">还可以 `Invoke-History` 通过其内置别名（和）来引用 `r` `ihy` 。</span><span class="sxs-lookup"><span data-stu-id="b9954-158">You can also refer to `Invoke-History` by its built-in aliases, `r` and `ihy`.</span></span> <span data-ttu-id="b9954-159">有关详细信息，请参阅 [about_Aliases](About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="b9954-159">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>

## <span data-ttu-id="b9954-160">相关链接</span><span class="sxs-lookup"><span data-stu-id="b9954-160">RELATED LINKS</span></span>

[<span data-ttu-id="b9954-161">Add-History</span><span class="sxs-lookup"><span data-stu-id="b9954-161">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="b9954-162">Clear-History</span><span class="sxs-lookup"><span data-stu-id="b9954-162">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="b9954-163">Get-History</span><span class="sxs-lookup"><span data-stu-id="b9954-163">Get-History</span></span>](Get-History.md)

