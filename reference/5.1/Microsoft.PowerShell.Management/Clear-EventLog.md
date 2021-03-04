---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-EventLog
ms.openlocfilehash: af1c808b22a812700857e756136fd570fa0acc35
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685911"
---
# <span data-ttu-id="8a553-103">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="8a553-103">Clear-EventLog</span></span>

## <span data-ttu-id="8a553-104">摘要</span><span class="sxs-lookup"><span data-stu-id="8a553-104">SYNOPSIS</span></span>
<span data-ttu-id="8a553-105">清除本地或远程计算机上指定事件日志中的所有条目。</span><span class="sxs-lookup"><span data-stu-id="8a553-105">Clears all entries from specified event logs on the local or remote computers.</span></span>

## <span data-ttu-id="8a553-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8a553-106">SYNTAX</span></span>

```
Clear-EventLog [-LogName] <String[]> [[-ComputerName] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8a553-107">说明</span><span class="sxs-lookup"><span data-stu-id="8a553-107">DESCRIPTION</span></span>

<span data-ttu-id="8a553-108">`Clear-EventLog`Cmdlet 将删除本地计算机或远程计算机上指定事件日志中的所有条目。</span><span class="sxs-lookup"><span data-stu-id="8a553-108">The `Clear-EventLog` cmdlet deletes all of the entries from the specified event logs on the local computer or on remote computers.</span></span> <span data-ttu-id="8a553-109">若要使用 `Clear-EventLog` ，您必须是受影响计算机上 Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="8a553-109">To use `Clear-EventLog`, you must be a member of the Administrators group on the affected computer.</span></span>

<span data-ttu-id="8a553-110"> (EventLog cmdlet 包含 **eventlog** 名词的 cmdlet) 仅适用于经典事件日志。</span><span class="sxs-lookup"><span data-stu-id="8a553-110">The cmdlets that contain the **EventLog** noun (the EventLog cmdlets) work only on classic event logs.</span></span> <span data-ttu-id="8a553-111">若要从使用 windows Vista 和更高版本 Windows 中的 Windows 事件日志技术的日志中获取事件，请使用 Get-WinEvent cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8a553-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of Windows, use the Get-WinEvent cmdlet.</span></span>

## <span data-ttu-id="8a553-112">示例</span><span class="sxs-lookup"><span data-stu-id="8a553-112">EXAMPLES</span></span>

### <span data-ttu-id="8a553-113">示例1：从本地计算机中清除特定的事件日志类型</span><span class="sxs-lookup"><span data-stu-id="8a553-113">Example 1: Clear specific event log types from the local computer</span></span>

```powershell
Clear-EventLog "Windows PowerShell"
```

<span data-ttu-id="8a553-114">此命令从本地计算机上的 Windows PowerShell 事件日志中清除条目。</span><span class="sxs-lookup"><span data-stu-id="8a553-114">This command clears the entries from the Windows PowerShell event log on the local computer.</span></span>

### <span data-ttu-id="8a553-115">示例2：清除本地和远程计算机中的特定多个日志类型</span><span class="sxs-lookup"><span data-stu-id="8a553-115">Example 2: Clear specific multiple log types from the local and remote computers</span></span>

```powershell
Clear-EventLog -LogName ODiag, OSession -ComputerName localhost, Server02
```

<span data-ttu-id="8a553-116">此命令清除本地计算机和 Server02 远程计算机上 Microsoft Office 诊断 (ODiag) 和 Microsoft Office 会话 (OSession) 日志中的所有条目。</span><span class="sxs-lookup"><span data-stu-id="8a553-116">This command clears all of the entries in the Microsoft Office Diagnostics (ODiag) and Microsoft Office Sessions (OSession) logs on the local computer and the Server02 remote computer.</span></span>

### <span data-ttu-id="8a553-117">示例3：清除指定计算机上的所有日志，然后显示 "事件日志" 列表</span><span class="sxs-lookup"><span data-stu-id="8a553-117">Example 3: Clear all logs on the specified computers then display the event log list</span></span>

```powershell
Clear-EventLog -LogName application, system -confirm
```

<span data-ttu-id="8a553-118">此命令将在删除指定事件日志中的条目之前提示你进行确认。</span><span class="sxs-lookup"><span data-stu-id="8a553-118">This command prompts you for confirmation before deleting the entries in the specified event logs.</span></span>

### <span data-ttu-id="8a553-119">示例4：清除指定计算机上的所有日志，然后显示 "事件日志" 列表</span><span class="sxs-lookup"><span data-stu-id="8a553-119">Example 4: Clear all logs on the specified computers then display the event log list</span></span>

```powershell
function clear-all-event-logs ($computerName="localhost")
{
   $logs = Get-EventLog -ComputerName $computername -List | ForEach-Object {$_.Log}
   $logs | ForEach-Object {Clear-EventLog -ComputerName $computername -LogName $_ }
   Get-EventLog -ComputerName $computername -list
}

clear-all-event-logs -ComputerName Server01
```

```Output
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded           0 Application
15,168      0 OverwriteAsNeeded           0 DFS Replication
512         7 OverwriteOlder              0 DxStudio
20,480      0 OverwriteAsNeeded           0 Hardware Events
512         7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
16,384      0 OverwriteAsNeeded           0 Microsoft Office Diagnostics
16,384      0 OverwriteAsNeeded           0 Microsoft Office Sessions
30,016      0 OverwriteAsNeeded           1 Security
15,168      0 OverwriteAsNeeded           2 System
15,360      0 OverwriteAsNeeded           0 Windows PowerShell
```

<span data-ttu-id="8a553-120">此函数将清除指定计算机上的所有事件日志，然后显示生成的事件日志列表。</span><span class="sxs-lookup"><span data-stu-id="8a553-120">This function clears all event logs on the specified computers and then displays the resulting event log list.</span></span>

<span data-ttu-id="8a553-121">请注意，在清除系统和安全日志之后但在显示它们之前，向其中添加了几个条目。</span><span class="sxs-lookup"><span data-stu-id="8a553-121">Notice that a few entries were added to the System and Security logs after the logs were cleared but before they were displayed.</span></span>

## <span data-ttu-id="8a553-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8a553-122">PARAMETERS</span></span>

### <span data-ttu-id="8a553-123">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="8a553-123">-ComputerName</span></span>

<span data-ttu-id="8a553-124">指定远程计算机。</span><span class="sxs-lookup"><span data-stu-id="8a553-124">Specifies a remote computer.</span></span> <span data-ttu-id="8a553-125">默认为本地计算机。</span><span class="sxs-lookup"><span data-stu-id="8a553-125">The default is the local computer.</span></span>

<span data-ttu-id="8a553-126">键入远程计算机的 NetBIOS 名称、Internet 协议 (IP) 地址或完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="8a553-126">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name of a remote computer.</span></span> <span data-ttu-id="8a553-127">若要指定本地计算机，请键入该计算机名称、句点 (.) 或“localhost”。</span><span class="sxs-lookup"><span data-stu-id="8a553-127">To specify the local computer, type the computer name, a dot (.), or "localhost".</span></span>

<span data-ttu-id="8a553-128">此参数不依赖于 Windows PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="8a553-128">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="8a553-129"> `Get-EventLog` 即使你的计算机未配置为运行远程命令，你也可以使用 ComputerName 参数。</span><span class="sxs-lookup"><span data-stu-id="8a553-129">You can use the **ComputerName** parameter of `Get-EventLog` even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 1
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8a553-130">-LogName</span><span class="sxs-lookup"><span data-stu-id="8a553-130">-LogName</span></span>

<span data-ttu-id="8a553-131">指定事件日志。</span><span class="sxs-lookup"><span data-stu-id="8a553-131">Specifies the event logs.</span></span> <span data-ttu-id="8a553-132">输入日志名称 (**日志** 属性的值，而不是由逗号分隔的一个或多个事件日志的 **LogDisplayName**) 。</span><span class="sxs-lookup"><span data-stu-id="8a553-132">Enter the log name (the value of the **Log** property not the **LogDisplayName**) of one or more event logs, separated by commas.</span></span> <span data-ttu-id="8a553-133">不允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="8a553-133">Wildcard characters are not permitted.</span></span> <span data-ttu-id="8a553-134">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="8a553-134">This parameter is required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8a553-135">此参数应按属性名称接受管道中的值。</span><span class="sxs-lookup"><span data-stu-id="8a553-135">This parameter is supposed to accept values from the pipeline by property name.</span></span> <span data-ttu-id="8a553-136">但是，有一个 bug 阻止了此操作。</span><span class="sxs-lookup"><span data-stu-id="8a553-136">However, there is a bug that prevents this from working.</span></span> <span data-ttu-id="8a553-137">必须直接使用参数传递值。</span><span class="sxs-lookup"><span data-stu-id="8a553-137">You must pass a value using the parameter directly.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8a553-138">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8a553-138">-Confirm</span></span>

<span data-ttu-id="8a553-139">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="8a553-139">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8a553-140">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8a553-140">-WhatIf</span></span>

<span data-ttu-id="8a553-141">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="8a553-141">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8a553-142">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="8a553-142">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8a553-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8a553-143">CommonParameters</span></span>

<span data-ttu-id="8a553-144">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="8a553-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8a553-145">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="8a553-145">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="8a553-146">输入</span><span class="sxs-lookup"><span data-stu-id="8a553-146">INPUTS</span></span>

### <span data-ttu-id="8a553-147">None</span><span class="sxs-lookup"><span data-stu-id="8a553-147">None</span></span>

<span data-ttu-id="8a553-148">不能通过管道将对象传递给 `Clear-EventLog` 。</span><span class="sxs-lookup"><span data-stu-id="8a553-148">You cannot pipe objects to `Clear-EventLog`.</span></span>

## <span data-ttu-id="8a553-149">输出</span><span class="sxs-lookup"><span data-stu-id="8a553-149">OUTPUTS</span></span>

### <span data-ttu-id="8a553-150">None</span><span class="sxs-lookup"><span data-stu-id="8a553-150">None</span></span>

<span data-ttu-id="8a553-151">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="8a553-151">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="8a553-152">注释</span><span class="sxs-lookup"><span data-stu-id="8a553-152">NOTES</span></span>

- <span data-ttu-id="8a553-153">若要 `Clear-EventLog` 在 Windows Vista 和更高版本的 windows 上使用，请使用 "以管理员身份运行" 选项启动 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="8a553-153">To use `Clear-EventLog` on Windows Vista and later versions of Windows, start Windows PowerShell with the "Run as administrator" option.</span></span>

## <span data-ttu-id="8a553-154">相关链接</span><span class="sxs-lookup"><span data-stu-id="8a553-154">RELATED LINKS</span></span>

[<span data-ttu-id="8a553-155">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="8a553-155">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="8a553-156">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="8a553-156">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="8a553-157">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="8a553-157">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="8a553-158">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="8a553-158">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="8a553-159">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="8a553-159">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="8a553-160">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="8a553-160">Write-EventLog</span></span>](Write-EventLog.md)
