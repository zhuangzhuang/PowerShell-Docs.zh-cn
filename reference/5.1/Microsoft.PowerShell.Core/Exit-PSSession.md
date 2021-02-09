---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/08/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: 1e0c8413a37a9b8877b6af9089ac311459ada20d
ms.sourcegitcommit: 3a1d80e27438976101f216b8c3d623c61b868db8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2021
ms.locfileid: "99975101"
---
# <span data-ttu-id="d8032-103">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="d8032-103">Exit-PSSession</span></span>

## <span data-ttu-id="d8032-104">摘要</span><span class="sxs-lookup"><span data-stu-id="d8032-104">Synopsis</span></span>
<span data-ttu-id="d8032-105">结束与远程计算机的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="d8032-105">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="d8032-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d8032-106">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="d8032-107">说明</span><span class="sxs-lookup"><span data-stu-id="d8032-107">Description</span></span>

<span data-ttu-id="d8032-108">`Exit-PSSession`Cmdlet 可结束使用 cmdlet 启动的交互式会话 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="d8032-108">The `Exit-PSSession` cmdlet ends interactive sessions that you started by using the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="d8032-109">你还可以使用 `exit` 关键字来结束交互式会话。</span><span class="sxs-lookup"><span data-stu-id="d8032-109">You can also use the `exit` keyword to end an interactive session.</span></span> <span data-ttu-id="d8032-110">此效果与使用相同 `Exit-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="d8032-110">The effect is the same as using `Exit-PSSession`.</span></span>

## <span data-ttu-id="d8032-111">示例</span><span class="sxs-lookup"><span data-stu-id="d8032-111">Examples</span></span>

### <span data-ttu-id="d8032-112">示例1：启动和停止交互式会话</span><span class="sxs-lookup"><span data-stu-id="d8032-112">Example 1: Start and stop an interactive session</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
Server01\PS> Exit-PSSession
PS C:\>
```

<span data-ttu-id="d8032-113">这些命令启动与 Server01 远程计算机的交互式会话，然后停止该会话。</span><span class="sxs-lookup"><span data-stu-id="d8032-113">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="d8032-114">示例2：使用 PSSession 对象启动和停止交互式会话</span><span class="sxs-lookup"><span data-stu-id="d8032-114">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```powershell
PS C:\> $s = New-PSSession -ComputerName Server01
PS C:\> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS C:\> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="d8032-115">这些命令启动和停止与使用 Windows PowerShell 会话 (**PSSession**) 的 Server01 计算机的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="d8032-115">These commands start and stop an interactive session with the Server01 computer that uses a Windows PowerShell session (**PSSession**).</span></span>

<span data-ttu-id="d8032-116">由于交互式会话是通过使用 Windows PowerShell 会话启动的，因此，当交互式会话结束时， **PSSession** 仍然可用。</span><span class="sxs-lookup"><span data-stu-id="d8032-116">Because the interactive session was started by using a Windows PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span> <span data-ttu-id="d8032-117">如果使用 _ComputerName_ 参数，则将 `Enter-PSSession` 创建一个在交互式会话结束时关闭的临时会话。</span><span class="sxs-lookup"><span data-stu-id="d8032-117">If you use the _ComputerName_ parameter, `Enter-PSSession` creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="d8032-118">第一个命令使用 `New-PSSession` cmdlet 在 Server01 计算机上创建 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="d8032-118">The first command uses the `New-PSSession` cmdlet to create a **PSSession** on the Server01 computer.</span></span> <span data-ttu-id="d8032-119">该命令将 **PSSession** 保存在 `$s` 变量中。</span><span class="sxs-lookup"><span data-stu-id="d8032-119">The command saves the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="d8032-120">第二个命令使用 `Enter-PSSession` 在中使用 **PSSession** 启动交互式会话 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="d8032-120">The second command uses `Enter-PSSession` to start an interactive session using the **PSSession** in `$s`.</span></span>

<span data-ttu-id="d8032-121">第三个命令使用 `Exit-PSSession` 来停止交互会话。</span><span class="sxs-lookup"><span data-stu-id="d8032-121">The third command uses `Exit-PSSession` to stop the interactive session.</span></span>

<span data-ttu-id="d8032-122">最后一个命令显示变量中的 PSSession `$s` 。</span><span class="sxs-lookup"><span data-stu-id="d8032-122">The final command displays the **PSSession** in the `$s` variable.</span></span> <span data-ttu-id="d8032-123">**State** 属性显示 **PSSession** 仍处于打开状态并可供使用。</span><span class="sxs-lookup"><span data-stu-id="d8032-123">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="d8032-124">示例3：使用 Exit 关键字停止会话</span><span class="sxs-lookup"><span data-stu-id="d8032-124">Example 3: Use the Exit keyword to stop a session</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
Server01\PS> exit
PS C:\>
```

<span data-ttu-id="d8032-125">此示例使用 `exit` 关键字来停止使用启动的交互式会话 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="d8032-125">This example uses the `exit` keyword to stop an interactive session started by using `Enter-PSSession`.</span></span> <span data-ttu-id="d8032-126">`exit`关键字与使用的效果相同 `Exit-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="d8032-126">The `exit` keyword has the same effect as using `Exit-PSSession`.</span></span>

## <span data-ttu-id="d8032-127">parameters</span><span class="sxs-lookup"><span data-stu-id="d8032-127">Parameters</span></span>

### <span data-ttu-id="d8032-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8032-128">CommonParameters</span></span>

<span data-ttu-id="d8032-129">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d8032-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8032-130">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d8032-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8032-131">输入</span><span class="sxs-lookup"><span data-stu-id="d8032-131">Inputs</span></span>

### <span data-ttu-id="d8032-132">无</span><span class="sxs-lookup"><span data-stu-id="d8032-132">None</span></span>

<span data-ttu-id="d8032-133">不能通过管道将对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8032-133">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="d8032-134">输出</span><span class="sxs-lookup"><span data-stu-id="d8032-134">Outputs</span></span>

### <span data-ttu-id="d8032-135">无</span><span class="sxs-lookup"><span data-stu-id="d8032-135">None</span></span>

<span data-ttu-id="d8032-136">此 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="d8032-136">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="d8032-137">说明</span><span class="sxs-lookup"><span data-stu-id="d8032-137">Notes</span></span>

<span data-ttu-id="d8032-138">此 cmdlet 仅提取通用参数。</span><span class="sxs-lookup"><span data-stu-id="d8032-138">This cmdlet takes only the common parameters.</span></span>

## <span data-ttu-id="d8032-139">相关链接</span><span class="sxs-lookup"><span data-stu-id="d8032-139">RELATED LINKS</span></span>

[<span data-ttu-id="d8032-140">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="d8032-140">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="d8032-141">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="d8032-141">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="d8032-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="d8032-142">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="d8032-143">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="d8032-143">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="d8032-144">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="d8032-144">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="d8032-145">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="d8032-145">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="d8032-146">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="d8032-146">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="d8032-147">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="d8032-147">Remove-PSSession</span></span>](Remove-PSSession.md)
