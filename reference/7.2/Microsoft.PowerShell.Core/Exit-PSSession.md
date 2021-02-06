---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: b76f7dc87105318285c930b6cd2ae4ae10c2b0e7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599062"
---
# <span data-ttu-id="054d7-102">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="054d7-102">Exit-PSSession</span></span>

## <span data-ttu-id="054d7-103">摘要</span><span class="sxs-lookup"><span data-stu-id="054d7-103">SYNOPSIS</span></span>
<span data-ttu-id="054d7-104">结束与远程计算机的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="054d7-104">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="054d7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="054d7-105">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="054d7-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="054d7-106">DESCRIPTION</span></span>

<span data-ttu-id="054d7-107">**Exit-PSSession** cmdlet 结束使用 Enter-PSSession cmdlet 启动的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="054d7-107">The **Exit-PSSession** cmdlet ends interactive sessions that you started by using the Enter-PSSession cmdlet.</span></span>

<span data-ttu-id="054d7-108">你还可以使用 **Exit** 关键字来结束交互式会话。</span><span class="sxs-lookup"><span data-stu-id="054d7-108">You can also use the **Exit** keyword to end an interactive session.</span></span>
<span data-ttu-id="054d7-109">其效果与使用 **Exit-PSSession** 相同。</span><span class="sxs-lookup"><span data-stu-id="054d7-109">The effect is the same as using **Exit-PSSession**.</span></span>

## <span data-ttu-id="054d7-110">示例</span><span class="sxs-lookup"><span data-stu-id="054d7-110">EXAMPLES</span></span>

### <span data-ttu-id="054d7-111">示例1：启动和停止交互式会话</span><span class="sxs-lookup"><span data-stu-id="054d7-111">Example 1: Start and stop an interactive session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> Exit-PSSession
PS>
```

<span data-ttu-id="054d7-112">这些命令启动与 Server01 远程计算机的交互式会话，然后停止该会话。</span><span class="sxs-lookup"><span data-stu-id="054d7-112">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="054d7-113">示例2：使用 PSSession 对象启动和停止交互式会话</span><span class="sxs-lookup"><span data-stu-id="054d7-113">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="054d7-114">这些命令启动和停止与使用 PowerShell 会话 (**PSSession**) 的 Server01 计算机的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="054d7-114">These commands start and stop an interactive session with the Server01 computer that uses a PowerShell session (**PSSession**).</span></span>

<span data-ttu-id="054d7-115">由于交互式会话是使用 PowerShell 会话启动的，因此当交互式会话结束时， **PSSession** 仍然可用。</span><span class="sxs-lookup"><span data-stu-id="054d7-115">Because the interactive session was started by using a PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span>
<span data-ttu-id="054d7-116">如果使用 *ComputerName* 参数，则 **输入-PSSession** 会创建一个临时会话，当交互式会话结束时，该会话将关闭。</span><span class="sxs-lookup"><span data-stu-id="054d7-116">If you use the *ComputerName* parameter, **Enter-PSSession** creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="054d7-117">第一个命令使用 New-PSSession cmdlet 在 Server01 计算机上创建 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="054d7-117">The first command uses the New-PSSession cmdlet to create a **PSSession** on the Server01 computer.</span></span>
<span data-ttu-id="054d7-118">该命令将 **PSSession** 保存在 $s 的变量中。</span><span class="sxs-lookup"><span data-stu-id="054d7-118">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="054d7-119">第二个命令使用 **Enter-PSSession** 在 $s 中使用 **PSSession** 启动交互式会话。</span><span class="sxs-lookup"><span data-stu-id="054d7-119">The second command uses **Enter-PSSession** to start an interactive session using the **PSSession** in $s.</span></span>

<span data-ttu-id="054d7-120">第三个命令使用 **Exit-PSSession** 来停止交互会话。</span><span class="sxs-lookup"><span data-stu-id="054d7-120">The third command uses **Exit-PSSession** to stop the interactive session.</span></span>

<span data-ttu-id="054d7-121">最后一个命令显示 $s 变量中的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="054d7-121">The final command displays the **PSSession** in the $s variable.</span></span>
<span data-ttu-id="054d7-122">**State** 属性显示 **PSSession** 仍处于打开状态并可供使用。</span><span class="sxs-lookup"><span data-stu-id="054d7-122">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="054d7-123">示例3：使用 Exit 关键字停止会话</span><span class="sxs-lookup"><span data-stu-id="054d7-123">Example 3: Use the Exit keyword to stop a session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> exit
PS>
```

<span data-ttu-id="054d7-124">此示例使用 **Exit** 关键字来停止使用 **Enter-PSSession** 启动的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="054d7-124">This example uses the **Exit** keyword to stop an interactive session started by using **Enter-PSSession**.</span></span>
<span data-ttu-id="054d7-125">**Exit** 关键字与使用 **exit-PSSession** 具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="054d7-125">The **Exit** keyword has the same effect as using **Exit-PSSession**.</span></span>

## <span data-ttu-id="054d7-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="054d7-126">PARAMETERS</span></span>

### <span data-ttu-id="054d7-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="054d7-127">CommonParameters</span></span>

<span data-ttu-id="054d7-128">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="054d7-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="054d7-129">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="054d7-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="054d7-130">输入</span><span class="sxs-lookup"><span data-stu-id="054d7-130">INPUTS</span></span>

### <span data-ttu-id="054d7-131">无</span><span class="sxs-lookup"><span data-stu-id="054d7-131">None</span></span>

<span data-ttu-id="054d7-132">不能通过管道将对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="054d7-132">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="054d7-133">输出</span><span class="sxs-lookup"><span data-stu-id="054d7-133">OUTPUTS</span></span>

### <span data-ttu-id="054d7-134">无</span><span class="sxs-lookup"><span data-stu-id="054d7-134">None</span></span>

<span data-ttu-id="054d7-135">此 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="054d7-135">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="054d7-136">注释</span><span class="sxs-lookup"><span data-stu-id="054d7-136">NOTES</span></span>

* <span data-ttu-id="054d7-137">此 cmdlet 仅提取通用参数。</span><span class="sxs-lookup"><span data-stu-id="054d7-137">This cmdlet takes only the common parameters.</span></span>

*

## <span data-ttu-id="054d7-138">相关链接</span><span class="sxs-lookup"><span data-stu-id="054d7-138">RELATED LINKS</span></span>

[<span data-ttu-id="054d7-139">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="054d7-139">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="054d7-140">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="054d7-140">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="054d7-141">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="054d7-141">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="054d7-142">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="054d7-142">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="054d7-143">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="054d7-143">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="054d7-144">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="054d7-144">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="054d7-145">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="054d7-145">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="054d7-146">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="054d7-146">Remove-PSSession</span></span>](Remove-PSSession.md)

