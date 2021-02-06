---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-History
ms.openlocfilehash: 1b465779f56c6bd71d7adfa7ffb5b391f5402656
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603417"
---
# <span data-ttu-id="0fe4f-102">Clear-History</span><span class="sxs-lookup"><span data-stu-id="0fe4f-102">Clear-History</span></span>

## <span data-ttu-id="0fe4f-103">摘要</span><span class="sxs-lookup"><span data-stu-id="0fe4f-103">SYNOPSIS</span></span>
<span data-ttu-id="0fe4f-104">从 PowerShell 会话命令历史记录中删除条目。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-104">Deletes entries from the PowerShell session command history.</span></span>

## <span data-ttu-id="0fe4f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0fe4f-105">SYNTAX</span></span>

### <span data-ttu-id="0fe4f-106">IDParameter (默认值) </span><span class="sxs-lookup"><span data-stu-id="0fe4f-106">IDParameter (Default)</span></span>

```
Clear-History [[-Id] <int[]>] [[-Count] <int>] [-Newest] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0fe4f-107">CommandLineParameter</span><span class="sxs-lookup"><span data-stu-id="0fe4f-107">CommandLineParameter</span></span>

```
Clear-History [[-Count] <int>] [-CommandLine <string[]>] [-Newest] [-WhatIf] [-Confirm]
[<CommonParameters>]
```

## <span data-ttu-id="0fe4f-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0fe4f-108">DESCRIPTION</span></span>

<span data-ttu-id="0fe4f-109">`Clear-History` 从 PowerShell 会话中删除命令历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-109">`Clear-History` deletes the command history from a PowerShell session.</span></span> <span data-ttu-id="0fe4f-110">每个 PowerShell 会话都有自己的命令历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-110">Each PowerShell session has its own command history.</span></span> <span data-ttu-id="0fe4f-111">若要显示命令历史记录，请使用 `Get-History` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-111">To display the command history, use the `Get-History` cmdlet.</span></span>

<span data-ttu-id="0fe4f-112">默认情况下， `Clear-History` 从 PowerShell 会话中删除整个命令历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-112">By default, `Clear-History` deletes the entire command history from a PowerShell session.</span></span> <span data-ttu-id="0fe4f-113">可以使用参数 `Clear-History` 来删除选定的命令。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-113">You can use parameters with `Clear-History` to delete selected commands.</span></span>

<span data-ttu-id="0fe4f-114">`Clear-History` 不清除 `PSReadLine` 命令历史记录文件。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-114">`Clear-History` does not clear the `PSReadLine` command history file.</span></span> <span data-ttu-id="0fe4f-115">该 `PSReadLine` 模块存储包含每个 powershell 会话中每个 powershell 命令的历史文件。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-115">The `PSReadLine` module stores a history file that contains every PowerShell command from every PowerShell session.</span></span> <span data-ttu-id="0fe4f-116">在 PowerShell 提示符下，使用键盘上的向上键和向下键滚动浏览命令历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-116">From a PowerShell prompt, use the up and down arrows on your keyboard to scroll through the command history.</span></span> <span data-ttu-id="0fe4f-117">若要显示 `PSReadLine` 命令历史记录的配置，请使用 `Get-PSReadLineOption` 。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-117">To display the `PSReadLine` configuration for command history, use `Get-PSReadLineOption`.</span></span>
<span data-ttu-id="0fe4f-118">`PSReadLine` 随附 PowerShell 5.0 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-118">`PSReadLine` shipped with PowerShell 5.0 and above.</span></span> <span data-ttu-id="0fe4f-119">有关详细信息，请参阅 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-119">For more information, see [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="0fe4f-120">示例</span><span class="sxs-lookup"><span data-stu-id="0fe4f-120">EXAMPLES</span></span>

### <span data-ttu-id="0fe4f-121">示例1：从 PowerShell 会话中删除命令历史记录</span><span class="sxs-lookup"><span data-stu-id="0fe4f-121">Example 1: Delete the command history from a PowerShell session</span></span>

<span data-ttu-id="0fe4f-122">此命令从 PowerShell 会话的历史记录中删除所有命令。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-122">This command deletes all of the commands from a PowerShell session's history.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location .\Test
   2 Update-Help
   3 Set-Location C:\Test\Logs
   4 Get-Location
```

```powershell
Clear-History
Get-History
```

```Output
  Id CommandLine
  -- -----------
   5 Clear-History
```

<span data-ttu-id="0fe4f-123">`Get-History`Cmdlet 将显示 PowerShell 会话的历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-123">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="0fe4f-124">`Clear-History` 删除整个命令历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-124">`Clear-History` deletes the entire command history.</span></span> <span data-ttu-id="0fe4f-125">`Get-History` 显示更新的命令历史记录，并确认之前的历史记录已删除。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-125">`Get-History` displays the updated command history and confirms the prior history was deleted.</span></span>

### <span data-ttu-id="0fe4f-126">示例2：删除最新命令</span><span class="sxs-lookup"><span data-stu-id="0fe4f-126">Example 2: Delete the newest commands</span></span>

<span data-ttu-id="0fe4f-127">此命令使用 **Count** 和 **最新** 参数从 PowerShell 会话的历史记录中删除最新的命令。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-127">This command uses the **Count** and **Newest** parameters to delete the newest commands from a PowerShell session's history.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Count 5 -Newest
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
  11 Clear-History -Count 5 -Newest
```

<span data-ttu-id="0fe4f-128">`Get-History`Cmdlet 将显示 PowerShell 会话的历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-128">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="0fe4f-129">`Clear-History` 用于删除命令历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-129">`Clear-History` is used to delete the command history.</span></span> <span data-ttu-id="0fe4f-130">**Count** 参数指定要删除的命令数，包括指定的 **Id**。**最新** 参数指定从历史记录中清除最新的命令。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-130">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id**. The **Newest** parameter specifies that the newest commands are cleared from the history.</span></span> <span data-ttu-id="0fe4f-131">`Get-History`显示更新的命令历史记录，并确认已删除5个最新命令（ **id 6**  -  **id 10**）。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-131">`Get-History` displays the updated command history and confirms that the five newest commands were deleted, **Id 6** - **Id 10**.</span></span>

### <span data-ttu-id="0fe4f-132">示例3：删除符合特定条件的命令</span><span class="sxs-lookup"><span data-stu-id="0fe4f-132">Example 3: Delete commands that match specific criteria</span></span>

<span data-ttu-id="0fe4f-133">此命令删除与命令 **行** 参数所定义的特定条件匹配的命令。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-133">This command deletes commands that match specific criteria defined by the **CommandLine** parameter.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
```

```powershell
Clear-History -CommandLine *Help*, *Syntax
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   4 Get-Command Clear-History -ShowCommandInfo
   8 Clear-History -CommandLine *Help*, *Syntax
```

<span data-ttu-id="0fe4f-134">`Get-History`Cmdlet 将显示 PowerShell 会话的历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-134">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="0fe4f-135">`Clear-History` 删除命令历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-135">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="0fe4f-136">**命令行** 参数指定包含 "**帮助**" 或 "以 **语法** 结尾" 的命令。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-136">The **CommandLine** parameter specifies commands that contain **Help** or end with **Syntax**.</span></span> <span data-ttu-id="0fe4f-137">`Get-History` 显示更新的命令历史记录，并确认已删除命令 **Id 3**、 **id 5**、 **id 6** 和 **id 7** 。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-137">`Get-History` displays the updated command history and confirms that commands **Id 3**, **Id 5**, **Id 6**, and **Id 7** were deleted.</span></span>

### <span data-ttu-id="0fe4f-138">示例4：按 Id 号删除命令</span><span class="sxs-lookup"><span data-stu-id="0fe4f-138">Example 4: Delete commands by Id number</span></span>

<span data-ttu-id="0fe4f-139">此命令删除使用 **Id** 的特定历史记录项。若要删除多个命令，请提交一个逗号分隔列表，其中列出了 **Id** 号。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-139">This command deletes specific history items using the **Id**. To delete multiple commands, submit a comma-separated list of **Id** numbers.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   3 Get-Help Get-Alias
   4 Get-Command Clear-History
   5 Get-Command Clear-History -Syntax
   6 Get-Command Clear-History -ShowCommandInfo
```

```powershell
Clear-History -Id 3, 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   4 Get-Command Clear-History
   6 Get-Command Clear-History -ShowCommandInfo
   7 Get-History
   8 Clear-History -Id 3, 5
```

<span data-ttu-id="0fe4f-140">`Get-History`Cmdlet 将显示 PowerShell 会话的历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-140">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="0fe4f-141">`Clear-History` 删除命令历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-141">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="0fe4f-142">**Id** 参数指定要删除的命令。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-142">The **Id** parameter specifies which commands to delete.</span></span> <span data-ttu-id="0fe4f-143">`Get-History` 显示更新的命令历史记录，并确认已删除 **id 3** 和 **id 5** 。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-143">`Get-History` displays the updated command history and confirms that **Id 3** and **Id 5** were deleted.</span></span>

### <span data-ttu-id="0fe4f-144">示例5：按 Id 号和计数删除命令</span><span class="sxs-lookup"><span data-stu-id="0fe4f-144">Example 5: Delete commands by Id number and count</span></span>

<span data-ttu-id="0fe4f-145">此命令使用 **Id** 和 **Count** 参数来删除命令历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-145">This command uses the **Id** and **Count** parameters to delete command history.</span></span> <span data-ttu-id="0fe4f-146">命令从指定的 **Id** 按相反顺序从最新到最旧的顺序删除。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-146">Commands are deleted from the specified **Id** in reverse order, newest to oldest.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Id 7 -Count 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
  11 Clear-History -Id 7 -Count 5
```

<span data-ttu-id="0fe4f-147">`Get-History`Cmdlet 将显示 PowerShell 会话的历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-147">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="0fe4f-148">`Clear-History` 删除命令历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-148">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="0fe4f-149">**Id** 参数指定以 **id 7** 开头。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-149">The **Id** parameter specifies to begin with **Id 7**.</span></span> <span data-ttu-id="0fe4f-150">**Count** 参数指定删除包含指定 **Id** 的五个命令。`Get-History`显示更新的命令历史记录，并确认已删除5个命令， **id 3**  -  **id 7**。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-150">The **Count** parameter specifies to delete five commands, inclusive of the specified **Id**. `Get-History` displays the updated command history and confirms that five commands were deleted, **Id 3** - **Id 7**.</span></span>

## <span data-ttu-id="0fe4f-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0fe4f-151">PARAMETERS</span></span>

### <span data-ttu-id="0fe4f-152">-命令行</span><span class="sxs-lookup"><span data-stu-id="0fe4f-152">-CommandLine</span></span>

<span data-ttu-id="0fe4f-153">从 PowerShell 会话中删除命令历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-153">Deletes command history from a PowerShell session.</span></span> <span data-ttu-id="0fe4f-154">字符串必须是完全匹配项，或者使用通配符匹配显示的 PowerShell 会话历史记录中的命令 `Get-History` 。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-154">The string must be an exact match or use wildcards to match commands in the PowerShell session history displayed by `Get-History`.</span></span> <span data-ttu-id="0fe4f-155">如果输入多个字符串，则会 `Clear-History` 删除与任何字符串匹配的命令。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-155">If you enter more than one string, `Clear-History` deletes commands that match any of the strings.</span></span> <span data-ttu-id="0fe4f-156">**命令行** 参数可与 **Count** 一起使用。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-156">The **CommandLine** parameter can be used with **Count**.</span></span>

<span data-ttu-id="0fe4f-157">对于带有空格的字符串，请使用单引号。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-157">For strings with a space, use single quotations.</span></span> <span data-ttu-id="0fe4f-158">有关详细信息，请参阅 [about_Quoting_Rules](About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-158">For more information, see [about_Quoting_Rules](About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandLineParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0fe4f-159">-Count</span><span class="sxs-lookup"><span data-stu-id="0fe4f-159">-Count</span></span>

<span data-ttu-id="0fe4f-160">指定要删除的历史记录条目数 `Clear-History` 。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-160">Specifies the number of history entries that `Clear-History` deletes.</span></span> <span data-ttu-id="0fe4f-161">从历史记录中最旧的条目开始，按顺序删除命令。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-161">Commands are deleted in order, beginning with the oldest entry in the history.</span></span>

<span data-ttu-id="0fe4f-162">**Count** 和 **Id** 参数可以一起使用。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-162">The **Count** and **Id** parameters can be used together.</span></span> <span data-ttu-id="0fe4f-163">**Count** 参数指定要删除的命令数，包括指定的 **Id**。从指定的 **Id** 开始，将按顺序反向删除命令。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-163">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id**. Beginning at the specified **Id**, commands are deleted in reverse sequential order.</span></span> <span data-ttu-id="0fe4f-164">例如，如果 **Id** 为30， **计数** 为10，则 `Clear-History` 删除项目21到30。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-164">For example, if the **Id** is 30 and the **Count** is 10, `Clear-History` deletes items 21 through 30.</span></span>

<span data-ttu-id="0fe4f-165">**Count** 和 **命令行** 参数可以一起使用。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-165">The **Count** and **CommandLine** parameters can be used together.</span></span> <span data-ttu-id="0fe4f-166">**计数** 指定与 **命令行** 参数值匹配的要删除的命令数。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-166">**Count** specifies the number of commands to delete that match **CommandLine** parameter value.</span></span> <span data-ttu-id="0fe4f-167">命令按顺序删除。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-167">The commands are deleted in sequential order.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0fe4f-168">-Id</span><span class="sxs-lookup"><span data-stu-id="0fe4f-168">-Id</span></span>

<span data-ttu-id="0fe4f-169">指定要删除的命令历史记录 **Id** `Clear-History` 。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-169">Specifies the command history **Id** that `Clear-History` deletes.</span></span> <span data-ttu-id="0fe4f-170">若要显示 **Id** 号，请使用 `Get-History` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-170">To display **Id** numbers, use the `Get-History` cmdlet.</span></span> <span data-ttu-id="0fe4f-171">**Id** 号是连续的，命令在 PowerShell 会话中保留其 **Id** 号。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-171">The **Id** numbers are sequential and commands keep their **Id** number throughout a PowerShell session.</span></span> <span data-ttu-id="0fe4f-172">**Id** 参数可用于 **计数** 和 **最新**。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-172">The **Id** parameter can be used with **Count** and **Newest**.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IDParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0fe4f-173">-Newest</span><span class="sxs-lookup"><span data-stu-id="0fe4f-173">-Newest</span></span>

<span data-ttu-id="0fe4f-174">使用 **最新** 的参数时，会 `Clear-History` 删除历史记录中的最新条目。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-174">When the **Newest** parameter is used, `Clear-History` deletes the newest entries in the history.</span></span> <span data-ttu-id="0fe4f-175">默认情况下，会 `Clear-History` 删除历史记录中最旧的条目。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-175">By default, `Clear-History` deletes the oldest entries in the history.</span></span>

<span data-ttu-id="0fe4f-176">**最新** 参数可以与 **Id** 和 **计数** 一起使用。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-176">The **Newest** parameter can be used with **Id** and **Count**.</span></span> <span data-ttu-id="0fe4f-177">**Count** 参数指定要删除的命令数，包括指定的 **Id**。从指定的 **Id** 开始，按顺序删除命令。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-177">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id**. Beginning at the specified **Id**, commands are deleted in sequential order.</span></span> <span data-ttu-id="0fe4f-178">例如，如果 **Id** 为30， **计数** 为10，则会 `Clear-History` 删除30到39项。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-178">For example, if the **Id** is 30 and the **Count** is 10, `Clear-History` deletes items 30 through 39.</span></span>

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

### <span data-ttu-id="0fe4f-179">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0fe4f-179">-Confirm</span></span>

<span data-ttu-id="0fe4f-180">提示你在运行 cmdlet 之前进行确认 `Clear-History` 。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-180">Prompts you for confirmation before running the `Clear-History` cmdlet.</span></span>

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

### <span data-ttu-id="0fe4f-181">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0fe4f-181">-WhatIf</span></span>

<span data-ttu-id="0fe4f-182">显示在 cmdlet 运行时将发生 `Clear-History` 的情况。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-182">Shows what would happen if the `Clear-History` cmdlet runs.</span></span> <span data-ttu-id="0fe4f-183">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-183">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0fe4f-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0fe4f-184">CommonParameters</span></span>

<span data-ttu-id="0fe4f-185">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0fe4f-186">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-186">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="0fe4f-187">输入</span><span class="sxs-lookup"><span data-stu-id="0fe4f-187">INPUTS</span></span>

### <span data-ttu-id="0fe4f-188">无</span><span class="sxs-lookup"><span data-stu-id="0fe4f-188">None</span></span>

<span data-ttu-id="0fe4f-189">不能通过管道将对象传递给 `Clear-History` 。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-189">You cannot pipe objects to `Clear-History`.</span></span>

## <span data-ttu-id="0fe4f-190">输出</span><span class="sxs-lookup"><span data-stu-id="0fe4f-190">OUTPUTS</span></span>

### <span data-ttu-id="0fe4f-191">无</span><span class="sxs-lookup"><span data-stu-id="0fe4f-191">None</span></span>

<span data-ttu-id="0fe4f-192">`Clear-History` 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-192">`Clear-History` does not generate any output.</span></span>

## <span data-ttu-id="0fe4f-193">注释</span><span class="sxs-lookup"><span data-stu-id="0fe4f-193">NOTES</span></span>

<span data-ttu-id="0fe4f-194">PowerShell 会话历史记录是在 PowerShell 会话期间输入的命令的列表。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-194">The PowerShell session history is a list of the commands entered during a PowerShell session.</span></span> <span data-ttu-id="0fe4f-195">可以查看历史记录、添加和删除命令以及运行历史记录中的命令。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-195">You can view the history, add and delete commands, and run commands from the history.</span></span> <span data-ttu-id="0fe4f-196">有关详细信息，请参阅 [about_History](About/about_History.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-196">For more information, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="0fe4f-197">会话历史记录与 **PSReadLine** 模块维护的历史记录分开管理。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-197">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="0fe4f-198">在加载 **PSReadLine** 的会话中提供两个历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-198">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="0fe4f-199">此 cmdlet 仅适用于会话历史记录。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-199">This cmdlet only works with the session history.</span></span> <span data-ttu-id="0fe4f-200">有关详细信息，请参阅 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe4f-200">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="0fe4f-201">相关链接</span><span class="sxs-lookup"><span data-stu-id="0fe4f-201">RELATED LINKS</span></span>

[<span data-ttu-id="0fe4f-202">about_History</span><span class="sxs-lookup"><span data-stu-id="0fe4f-202">about_History</span></span>](About/about_History.md)

[<span data-ttu-id="0fe4f-203">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="0fe4f-203">about_PSReadLine</span></span>](../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="0fe4f-204">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="0fe4f-204">about_Quoting_Rules</span></span>](About/about_Quoting_Rules.md)

[<span data-ttu-id="0fe4f-205">Add-History</span><span class="sxs-lookup"><span data-stu-id="0fe4f-205">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="0fe4f-206">Get-History</span><span class="sxs-lookup"><span data-stu-id="0fe4f-206">Get-History</span></span>](Get-History.md)

[<span data-ttu-id="0fe4f-207">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="0fe4f-207">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="0fe4f-208">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="0fe4f-208">Get-PSReadLineOption</span></span>](/powershell/module/psreadline/get-psreadlineoption)

[<span data-ttu-id="0fe4f-209">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="0fe4f-209">Set-PSReadLineOption</span></span>](/powershell/module/psreadline/set-psreadlineoption)

