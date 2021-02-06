---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-pscallstack?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSCallStack
ms.openlocfilehash: 607e3999a1dbe9a4f22a751f11ac93ee3f9d9409
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596411"
---
# <span data-ttu-id="27aea-102">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="27aea-102">Get-PSCallStack</span></span>

## <span data-ttu-id="27aea-103">摘要</span><span class="sxs-lookup"><span data-stu-id="27aea-103">SYNOPSIS</span></span>
<span data-ttu-id="27aea-104">显示当前的调用堆栈。</span><span class="sxs-lookup"><span data-stu-id="27aea-104">Displays the current call stack.</span></span>

## <span data-ttu-id="27aea-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="27aea-105">SYNTAX</span></span>

```
Get-PSCallStack [<CommonParameters>]
```

## <span data-ttu-id="27aea-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="27aea-106">DESCRIPTION</span></span>

<span data-ttu-id="27aea-107">**Get-pscallstack** cmdlet 显示当前的调用堆栈。</span><span class="sxs-lookup"><span data-stu-id="27aea-107">The **Get-PSCallStack** cmdlet displays the current call stack.</span></span>

<span data-ttu-id="27aea-108">尽管它旨在用于 PowerShell 调试器，但你可以使用此 cmdlet 在调试器外的脚本或函数中显示调用堆栈。</span><span class="sxs-lookup"><span data-stu-id="27aea-108">Although it is designed to be used with the PowerShell debugger, you can use this cmdlet to display the call stack in a script or function outside of the debugger.</span></span>

<span data-ttu-id="27aea-109">若要在调试器中运行 **get-pscallstack** 命令，请键入 `k` 或 `Get-PSCallStack` 。</span><span class="sxs-lookup"><span data-stu-id="27aea-109">To run a **Get-PSCallStack** command while in the debugger, type `k` or `Get-PSCallStack`.</span></span>

## <span data-ttu-id="27aea-110">示例</span><span class="sxs-lookup"><span data-stu-id="27aea-110">EXAMPLES</span></span>

### <span data-ttu-id="27aea-111">示例1：获取函数的调用堆栈</span><span class="sxs-lookup"><span data-stu-id="27aea-111">Example 1: Get the call stack for a function</span></span>

```
PS C:\> function my-alias {
$p = $args[0]
Get-Alias | where {$_.definition -like "*$p"} | format-table definition, name -auto
}
PS C:\ps-test> Set-PSBreakpoint -Command my-alias
Command    : my-alias
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : prompt PS C:\> my-alias Get-Content

Entering debug mode. Use h or ? for help.
Hit Command breakpoint on 'prompt:my-alias'
my-alias get-content
[DBG]: PS C:\ps-test> s
$p = $args[0]
DEBUG: Stepped to ':    $p = $args[0]    '
[DBG]: PS C:\ps-test> s
get-alias | Where {$_.Definition -like "*$p*"} | format-table Definition,
[DBG]: PS C:\ps-test>get-pscallstack

Name        CommandLineParameters         UnboundArguments              Location
----        ---------------------         ----------------              --------
prompt      {}                            {}                            prompt
my-alias    {}                            {get-content}                 prompt
prompt      {}                            {}                            prompt PS C:\> [DBG]: PS C:\ps-test> o
Definition  Name
----------  ----
Get-Content gc
Get-Content cat
Get-Content type
```

<span data-ttu-id="27aea-112">此命令使用 **get-pscallstack** cmdlet 来显示别名的调用堆栈，这是一个获取 cmdlet 名称的别名的简单函数。</span><span class="sxs-lookup"><span data-stu-id="27aea-112">This command uses the **Get-PSCallStack** cmdlet to display the call stack for My-Alias, a simple function that gets the aliases for a cmdlet name.</span></span>

<span data-ttu-id="27aea-113">第一个命令在 PowerShell 提示符下进入函数。</span><span class="sxs-lookup"><span data-stu-id="27aea-113">The first command enters the function at the PowerShell prompt.</span></span>
<span data-ttu-id="27aea-114">第二个命令使用 Set-PSBreakpoint cmdlet 在 My-Alias 函数上设置断点。</span><span class="sxs-lookup"><span data-stu-id="27aea-114">The second command uses the Set-PSBreakpoint cmdlet to set a breakpoint on the My-Alias function.</span></span>
<span data-ttu-id="27aea-115">第三个命令使用 My-Alias 函数在 Get-Content cmdlet 的当前会话中获取所有别名。</span><span class="sxs-lookup"><span data-stu-id="27aea-115">The third command uses the My-Alias function to get all of the aliases in the current session for the Get-Content cmdlet.</span></span>

<span data-ttu-id="27aea-116">调试器在函数调用时中断。</span><span class="sxs-lookup"><span data-stu-id="27aea-116">The debugger breaks in at the function call.</span></span>
<span data-ttu-id="27aea-117">两个连续的 step-into (s) 命令开始逐行执行该函数。</span><span class="sxs-lookup"><span data-stu-id="27aea-117">Two consecutive step-into (s) commands begin executing the function line by line.</span></span>
<span data-ttu-id="27aea-118">然后，使用 **get-pscallstack** 命令来检索调用堆栈。</span><span class="sxs-lookup"><span data-stu-id="27aea-118">Then, a **Get-PSCallStack** command is used to retrieve the call stack.</span></span>

<span data-ttu-id="27aea-119">最后的命令是 Step-Out 命令 (o)，它退出调试器并继续执行该脚本直到完成。</span><span class="sxs-lookup"><span data-stu-id="27aea-119">The final command is a Step-Out command (o) that exits the debugger and continues executing the script to completion.</span></span>

## <span data-ttu-id="27aea-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="27aea-120">PARAMETERS</span></span>

### <span data-ttu-id="27aea-121">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="27aea-121">CommonParameters</span></span>

<span data-ttu-id="27aea-122">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="27aea-122">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="27aea-123">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="27aea-123">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="27aea-124">输入</span><span class="sxs-lookup"><span data-stu-id="27aea-124">INPUTS</span></span>

### <span data-ttu-id="27aea-125">无</span><span class="sxs-lookup"><span data-stu-id="27aea-125">None</span></span>

<span data-ttu-id="27aea-126">不能通过管道将对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="27aea-126">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="27aea-127">输出</span><span class="sxs-lookup"><span data-stu-id="27aea-127">OUTPUTS</span></span>

### <span data-ttu-id="27aea-128">System.web. CallStackFrame</span><span class="sxs-lookup"><span data-stu-id="27aea-128">System.Management.Automation.CallStackFrame</span></span>

<span data-ttu-id="27aea-129">**Get-pscallstack** 返回一个对象，该对象表示调用堆栈中的项。</span><span class="sxs-lookup"><span data-stu-id="27aea-129">**Get-PSCallStack** returns an object that represents the items in the call stack.</span></span>

## <span data-ttu-id="27aea-130">注释</span><span class="sxs-lookup"><span data-stu-id="27aea-130">NOTES</span></span>

## <span data-ttu-id="27aea-131">相关链接</span><span class="sxs-lookup"><span data-stu-id="27aea-131">RELATED LINKS</span></span>

[<span data-ttu-id="27aea-132">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="27aea-132">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="27aea-133">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="27aea-133">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="27aea-134">Format-Table</span><span class="sxs-lookup"><span data-stu-id="27aea-134">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="27aea-135">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="27aea-135">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="27aea-136">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="27aea-136">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="27aea-137">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="27aea-137">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

