---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-History
ms.openlocfilehash: be47925211c57760ddbd0bd4c8e985e161d24593
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596216"
---
# <span data-ttu-id="4a225-102">Get-History</span><span class="sxs-lookup"><span data-stu-id="4a225-102">Get-History</span></span>

## <span data-ttu-id="4a225-103">摘要</span><span class="sxs-lookup"><span data-stu-id="4a225-103">SYNOPSIS</span></span>
<span data-ttu-id="4a225-104">获取在当前会话过程中输入的命令列表。</span><span class="sxs-lookup"><span data-stu-id="4a225-104">Gets a list of the commands entered during the current session.</span></span>

## <span data-ttu-id="4a225-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4a225-105">SYNTAX</span></span>

```
Get-History [[-Id] <Int64[]>] [[-Count] <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="4a225-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4a225-106">DESCRIPTION</span></span>

<span data-ttu-id="4a225-107">该 `Get-History` cmdlet 将获取会话历史记录，即在当前会话期间输入的命令的列表。</span><span class="sxs-lookup"><span data-stu-id="4a225-107">The `Get-History` cmdlet gets the session history, that is, the list of commands entered during the current session.</span></span>

<span data-ttu-id="4a225-108">PowerShell 会自动维护每个会话的历史记录。</span><span class="sxs-lookup"><span data-stu-id="4a225-108">PowerShell automatically maintains a history of each session.</span></span> <span data-ttu-id="4a225-109">会话历史记录中的条目数由 `$MaximumHistoryCount` 首选项变量的值确定。</span><span class="sxs-lookup"><span data-stu-id="4a225-109">The number of entries in the session history is determined by the value of the `$MaximumHistoryCount` preference variable.</span></span> <span data-ttu-id="4a225-110">从 Windows PowerShell 3.0 开始，默认值为 `4096` 。</span><span class="sxs-lookup"><span data-stu-id="4a225-110">Beginning in Windows PowerShell 3.0, the default value is `4096`.</span></span> <span data-ttu-id="4a225-111">默认情况下，历史记录文件保存在主目录中，但你可以将该文件保存在任何位置。</span><span class="sxs-lookup"><span data-stu-id="4a225-111">By default, history files are saved in the home directory, but you can save the file in any location.</span></span> <span data-ttu-id="4a225-112">有关 PowerShell 中的历史记录功能的详细信息，请参阅 [about_History](About/about_History.md)。</span><span class="sxs-lookup"><span data-stu-id="4a225-112">For more information about the history features in PowerShell, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="4a225-113">会话历史记录与 **PSReadLine** 模块维护的历史记录分开管理。</span><span class="sxs-lookup"><span data-stu-id="4a225-113">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="4a225-114">在加载 **PSReadLine** 的会话中提供两个历史记录。</span><span class="sxs-lookup"><span data-stu-id="4a225-114">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="4a225-115">此 cmdlet 仅适用于会话历史记录。</span><span class="sxs-lookup"><span data-stu-id="4a225-115">This cmdlet only works with the session history.</span></span> <span data-ttu-id="4a225-116">有关详细信息，请参阅 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。</span><span class="sxs-lookup"><span data-stu-id="4a225-116">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="4a225-117">示例</span><span class="sxs-lookup"><span data-stu-id="4a225-117">EXAMPLES</span></span>

### <span data-ttu-id="4a225-118">示例 1：获取会话历史记录</span><span class="sxs-lookup"><span data-stu-id="4a225-118">Example 1: Get the session history</span></span>

<span data-ttu-id="4a225-119">此示例将获取会话历史记录中的条目。</span><span class="sxs-lookup"><span data-stu-id="4a225-119">This example gets the entries in the session history.</span></span> <span data-ttu-id="4a225-120">将默认显示每个命令及其 ID，指示其运行顺序。</span><span class="sxs-lookup"><span data-stu-id="4a225-120">The default display shows each command and its ID, which indicates the order in which they ran.</span></span>

```powershell
Get-History
```

### <span data-ttu-id="4a225-121">示例 2：获取包含字符串的条目</span><span class="sxs-lookup"><span data-stu-id="4a225-121">Example 2: Get entries that include a string</span></span>

<span data-ttu-id="4a225-122">此示例将获取命令历史记录中包含字符串服务的条目。</span><span class="sxs-lookup"><span data-stu-id="4a225-122">This example gets entries in the command history that include the string service.</span></span> <span data-ttu-id="4a225-123">第一个命令获取会话历史记录中的所有条目。</span><span class="sxs-lookup"><span data-stu-id="4a225-123">The first command gets all entries in the session history.</span></span> <span data-ttu-id="4a225-124">管道运算符 (`|`) 将结果传递给 `Where-Object` cmdlet，后者只选择包含服务的命令。</span><span class="sxs-lookup"><span data-stu-id="4a225-124">The pipeline operator (`|`) passes the results to the `Where-Object` cmdlet, which selects only the commands that include service.</span></span>

```powershell
Get-History | Where-Object {$_.CommandLine -like "*Service*"}
```

### <span data-ttu-id="4a225-125">示例3：导出特定 ID 的历史记录条目</span><span class="sxs-lookup"><span data-stu-id="4a225-125">Example 3: Export history entries up to a specific ID</span></span>

<span data-ttu-id="4a225-126">此示例获取以条目7结尾的五个最新历史记录条目。</span><span class="sxs-lookup"><span data-stu-id="4a225-126">This example gets the five most recent history entries ending with entry 7.</span></span> <span data-ttu-id="4a225-127">管道运算符将结果传递给 `Export-Csv` cmdlet，这会将历史记录的格式设置为以逗号分隔的文本，并将其保存在 History.csv 文件中。</span><span class="sxs-lookup"><span data-stu-id="4a225-127">The pipeline operator passes the result to the `Export-Csv` cmdlet, which formats the history as comma-separated text and saves it in the History.csv file.</span></span> <span data-ttu-id="4a225-128">该文件包括将历史记录的格式设置为列表时显示的数据。</span><span class="sxs-lookup"><span data-stu-id="4a225-128">The file includes the data that is displayed when you format the history as a list.</span></span> <span data-ttu-id="4a225-129">这包括该命令的状态以及开始和结束时间。</span><span class="sxs-lookup"><span data-stu-id="4a225-129">This includes the status and start and end times of the command.</span></span>

```powershell
Get-History -ID 7 -Count 5 | Export-Csv History.csv
```

### <span data-ttu-id="4a225-130">示例 4：显示最新的命令</span><span class="sxs-lookup"><span data-stu-id="4a225-130">Example 4: Display the most recent command</span></span>

<span data-ttu-id="4a225-131">此示例获取命令历史记录中的最后一个命令。</span><span class="sxs-lookup"><span data-stu-id="4a225-131">This example gets the last command in the command history.</span></span> <span data-ttu-id="4a225-132">最后一个命令是最新输入的命令。</span><span class="sxs-lookup"><span data-stu-id="4a225-132">The last command is the most recently entered command.</span></span> <span data-ttu-id="4a225-133">此命令使用 Count 参数以仅显示一个命令。</span><span class="sxs-lookup"><span data-stu-id="4a225-133">This command uses the **Count** parameter to display just one command.</span></span> <span data-ttu-id="4a225-134">默认情况下， `Get-History` 获取最新命令。</span><span class="sxs-lookup"><span data-stu-id="4a225-134">By default, `Get-History` gets the most recent commands.</span></span> <span data-ttu-id="4a225-135">此命令可缩写为“h -c 1”，等效于按向上箭头键。</span><span class="sxs-lookup"><span data-stu-id="4a225-135">This command can be abbreviated to "h -c 1" and is equivalent to pressing the up-arrow key.</span></span>

```powershell
Get-History -Count 1
```

### <span data-ttu-id="4a225-136">示例 5：显示历史记录中的条目的所有属性</span><span class="sxs-lookup"><span data-stu-id="4a225-136">Example 5: Display all the properties of the entries in the history</span></span>

<span data-ttu-id="4a225-137">此示例显示会话历史记录中条目的所有属性。</span><span class="sxs-lookup"><span data-stu-id="4a225-137">This example displays all of the properties of entries in the session history.</span></span> <span data-ttu-id="4a225-138">管道运算符将命令的结果传递 `Get-History` 给 `Format-List` cmdlet，后者将显示每个历史记录条目的所有属性。</span><span class="sxs-lookup"><span data-stu-id="4a225-138">The pipeline operator passes the results of a `Get-History` command to the `Format-List` cmdlet, which displays all of the properties of each history entry.</span></span> <span data-ttu-id="4a225-139">这包括该命令的 ID、状态以及开始和结束时间。</span><span class="sxs-lookup"><span data-stu-id="4a225-139">This includes the ID, status, and start and end times of the command.</span></span>

```powershell
Get-History | Format-List -Property *
```

## <span data-ttu-id="4a225-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4a225-140">PARAMETERS</span></span>

### <span data-ttu-id="4a225-141">-Count</span><span class="sxs-lookup"><span data-stu-id="4a225-141">-Count</span></span>

<span data-ttu-id="4a225-142">指定此 cmdlet 获取的最新历史记录条目数。</span><span class="sxs-lookup"><span data-stu-id="4a225-142">Specifies the number of the most recent history entries that this cmdlet gets.</span></span> <span data-ttu-id="4a225-143">默认情况下， `Get-History` 将获取会话历史记录中的所有条目。</span><span class="sxs-lookup"><span data-stu-id="4a225-143">By, default, `Get-History` gets all entries in the session history.</span></span> <span data-ttu-id="4a225-144">如果在命令中同时使用 **Count** 和 **Id** 参数，显示结果将以 **Id** 参数指定的命令结尾。</span><span class="sxs-lookup"><span data-stu-id="4a225-144">If you use both the **Count** and **Id** parameters in a command, the display ends with the command that is specified by the **Id** parameter.</span></span>

<span data-ttu-id="4a225-145">默认情况下，在 Windows PowerShell 2.0 中， `Get-History` 获取最新的32项。</span><span class="sxs-lookup"><span data-stu-id="4a225-145">In Windows PowerShell 2.0, by default, `Get-History` gets the 32 most recent entries.</span></span>

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

### <span data-ttu-id="4a225-146">-Id</span><span class="sxs-lookup"><span data-stu-id="4a225-146">-Id</span></span>

<span data-ttu-id="4a225-147">指定会话历史记录中的条目的 ID 数组。</span><span class="sxs-lookup"><span data-stu-id="4a225-147">Specifies an array of the IDs of entries in the session history.</span></span> <span data-ttu-id="4a225-148">`Get-History` 仅获取指定的项。</span><span class="sxs-lookup"><span data-stu-id="4a225-148">`Get-History` gets only specified entries.</span></span> <span data-ttu-id="4a225-149">如果在命令中同时使用 **Id** 和 **Count** 参数，则将 `Get-History` 获取以 **id** 参数指定的条目结尾的最新条目。</span><span class="sxs-lookup"><span data-stu-id="4a225-149">If you use both the **Id** and **Count** parameters in a command, `Get-History` gets the most recent entries ending with the entry specified by the **Id** parameter.</span></span>

```yaml
Type: System.Int64[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4a225-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4a225-150">CommonParameters</span></span>

<span data-ttu-id="4a225-151">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4a225-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4a225-152">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4a225-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4a225-153">输入</span><span class="sxs-lookup"><span data-stu-id="4a225-153">INPUTS</span></span>

### <span data-ttu-id="4a225-154">System.Int64</span><span class="sxs-lookup"><span data-stu-id="4a225-154">System.Int64</span></span>

<span data-ttu-id="4a225-155">可以通过管道将历史记录 ID 传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a225-155">You can pipe a history ID to this cmdlet.</span></span>

## <span data-ttu-id="4a225-156">输出</span><span class="sxs-lookup"><span data-stu-id="4a225-156">OUTPUTS</span></span>

### <span data-ttu-id="4a225-157">Microsoft.PowerShell.Commands.HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="4a225-157">Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="4a225-158">此 cmdlet 将返回它所获取的每个历史记录项的历史记录对象。</span><span class="sxs-lookup"><span data-stu-id="4a225-158">This cmdlet returns a history object for each history item that it gets.</span></span>

## <span data-ttu-id="4a225-159">注释</span><span class="sxs-lookup"><span data-stu-id="4a225-159">NOTES</span></span>

<span data-ttu-id="4a225-160">会话历史记录是在会话期间输入的命令的列表。</span><span class="sxs-lookup"><span data-stu-id="4a225-160">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="4a225-161">会话历史记录表示命令的运行顺序、状态以及开始和结束时间。</span><span class="sxs-lookup"><span data-stu-id="4a225-161">The session history represents the run order, the status, and the start and end times of the command.</span></span> <span data-ttu-id="4a225-162">当你输入每个命令时，PowerShell 会将其添加到历史记录，以便你可以重复使用它。</span><span class="sxs-lookup"><span data-stu-id="4a225-162">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="4a225-163">有关命令历史记录的详细信息，请参阅 [about_History](About/about_History.md)。</span><span class="sxs-lookup"><span data-stu-id="4a225-163">For more information about the command history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="4a225-164">从 Windows PowerShell 3.0 开始， `$MaximumHistoryCount` 首选项变量的默认值为 `4096` 。</span><span class="sxs-lookup"><span data-stu-id="4a225-164">Starting in Windows PowerShell 3.0, the default value of the `$MaximumHistoryCount` preference variable is `4096`.</span></span> <span data-ttu-id="4a225-165">在 Windows PowerShell 2.0 中，默认值为 `64` 。</span><span class="sxs-lookup"><span data-stu-id="4a225-165">In Windows PowerShell 2.0, the default value is `64`.</span></span> <span data-ttu-id="4a225-166">有关变量的详细信息 `$MaximumHistoryCount` ，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="4a225-166">For more information about the `$MaximumHistoryCount` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="4a225-167">相关链接</span><span class="sxs-lookup"><span data-stu-id="4a225-167">RELATED LINKS</span></span>

[<span data-ttu-id="4a225-168">Add-History</span><span class="sxs-lookup"><span data-stu-id="4a225-168">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="4a225-169">Clear-History</span><span class="sxs-lookup"><span data-stu-id="4a225-169">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="4a225-170">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="4a225-170">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="4a225-171">about_History</span><span class="sxs-lookup"><span data-stu-id="4a225-171">about_History</span></span>](About/about_History.md)
