---
title: 附录 A - 帮助语法
description: 本文介绍如何阅读和理解 Get-Help 提供的 cmdlet 的语法。
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: b8fe218f2a9af1ad1ee6b88740414ecede0194bd
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "99595599"
---
# <a name="appendix-a---help-syntax"></a><span data-ttu-id="2f226-103">附录 A - 帮助语法</span><span class="sxs-lookup"><span data-stu-id="2f226-103">Appendix A - Help Syntax</span></span>

<span data-ttu-id="2f226-104">下面的示例演示了 `Get-EventLog` cmdlet 帮助的“语法”部分。</span><span class="sxs-lookup"><span data-stu-id="2f226-104">The following example shows the **SYNTAX** section of the help for the `Get-EventLog` cmdlet.</span></span>

```powershell
help Get-EventLog
```

```Output
NAME
    Get-EventLog

SYNOPSIS
    Gets the events in an event log, or a list of the event logs, on the local or remote
    computers.


SYNTAX
    Get-EventLog [-LogName] <String> [[-InstanceId] <Int64[]>] [-After <DateTime>]
    [-AsBaseObject] [-Before <DateTime>] [-ComputerName <String[]>] [-EntryType {Error |
    Information | FailureAudit | SuccessAudit | Warning}] [-Index <Int32[]>] [-Message
    <String>] [-Newest <Int32>] [-Source <String[]>] [-UserName <String[]>]
    [<CommonParameters>]

    Get-EventLog [-AsString] [-ComputerName <String[]>] [-List] [<CommonParameters>]
```

<span data-ttu-id="2f226-105">此示例只显示了帮助的相关部分。</span><span class="sxs-lookup"><span data-stu-id="2f226-105">Only the relevant portion of the help is shown in this example.</span></span>

<span data-ttu-id="2f226-106">语法主要由多组左方括号和右方括号 (`[]`) 组成。</span><span class="sxs-lookup"><span data-stu-id="2f226-106">The syntax is primarily made up of several sets of opening and closing brackets (`[]`).</span></span> <span data-ttu-id="2f226-107">它们具有两种不同的含义，具体取决于它们的使用方式。</span><span class="sxs-lookup"><span data-stu-id="2f226-107">These have two different meanings depending on how they're used.</span></span> <span data-ttu-id="2f226-108">方括号内包含的任何内容都是可选的，除非它们是一组空方括号 `[]`。</span><span class="sxs-lookup"><span data-stu-id="2f226-108">Anything contained within square brackets is optional unless they're a set of empty square brackets `[]`.</span></span> <span data-ttu-id="2f226-109">空方括号仅出现在 `<string[]>` 等数据类型之后。</span><span class="sxs-lookup"><span data-stu-id="2f226-109">Empty square brackets only appear after a datatype such as `<string[]>`.</span></span> <span data-ttu-id="2f226-110">这意味着特定参数可以接受多个该类型的值。</span><span class="sxs-lookup"><span data-stu-id="2f226-110">This means that particular parameter can accept more than one value of that type.</span></span>

<span data-ttu-id="2f226-111">`Get-EventLog` 的第一个参数集中的第一个参数是 LogName。</span><span class="sxs-lookup"><span data-stu-id="2f226-111">The first parameter in the first parameter set of `Get-EventLog` is **LogName**.</span></span> <span data-ttu-id="2f226-112">LogName 由方括号括起来，这意味着它是一个位置参数。</span><span class="sxs-lookup"><span data-stu-id="2f226-112">LogName is surrounded by square brackets which means that it's a positional parameter.</span></span> <span data-ttu-id="2f226-113">换句话说，只要在正确的位置指定参数，就可选择指定该参数本身的名称。</span><span class="sxs-lookup"><span data-stu-id="2f226-113">In other words, specifying the name of the parameter itself is optional as long as it's specified in the correct position.</span></span> <span data-ttu-id="2f226-114">参数名称后面的尖括号 (`<>`) 中的信息指示它需要单个字符串值。</span><span class="sxs-lookup"><span data-stu-id="2f226-114">The information in the angle brackets (`<>`) after the parameter name indicates that it needs a single **string** value.</span></span> <span data-ttu-id="2f226-115">整个参数名称和数据类型没有用方括号括起来的，因此在使用此参数集时需要 LogName 参数。</span><span class="sxs-lookup"><span data-stu-id="2f226-115">The entire parameter name and datatype are not surrounded by square brackets so the **LogName** parameter is required when using this parameter set.</span></span>

```powershell
Get-EventLog [-LogName] <String>
```

<span data-ttu-id="2f226-116">第二个参数是 InstanceId。</span><span class="sxs-lookup"><span data-stu-id="2f226-116">The second parameter is **InstanceId**.</span></span> <span data-ttu-id="2f226-117">请注意，参数名称和数据类型都使用了方括号完全括起来。</span><span class="sxs-lookup"><span data-stu-id="2f226-117">Notice that the parameter name and the datatype are both completely surrounded by square brackets.</span></span> <span data-ttu-id="2f226-118">这意味着 InstanceId 参数是可选参数，而不是强制参数。</span><span class="sxs-lookup"><span data-stu-id="2f226-118">This means that the **InstanceId** parameter is optional, not mandatory.</span></span> <span data-ttu-id="2f226-119">另请注意，InstanceId 由其自身的方括号括起来。</span><span class="sxs-lookup"><span data-stu-id="2f226-119">Also notice that **InstanceId** is surrounded by its own set of square brackets.</span></span> <span data-ttu-id="2f226-120">与 LogName 参数一样，这意味着该参数是位置参数。</span><span class="sxs-lookup"><span data-stu-id="2f226-120">As with the **LogName** parameter, this means the parameter is positional.</span></span> <span data-ttu-id="2f226-121">数据类型后是最后一组方括号。</span><span class="sxs-lookup"><span data-stu-id="2f226-121">There's one last set of square brackets after the datatype.</span></span> <span data-ttu-id="2f226-122">这意味着它可以接受多个数组或逗号分隔列表形式的值。</span><span class="sxs-lookup"><span data-stu-id="2f226-122">This means that it can accept more than one value in the form of an array or a comma-separated list.</span></span>

```
[[-InstanceId] <Int64[]>]
```

<span data-ttu-id="2f226-123">第二个参数集具有 List 参数。</span><span class="sxs-lookup"><span data-stu-id="2f226-123">The second parameter set has a **List** parameter.</span></span> <span data-ttu-id="2f226-124">这是一个开关参数，因为参数名称后面没有数据类型。</span><span class="sxs-lookup"><span data-stu-id="2f226-124">It's a switch parameter because there's no datatype following the parameter name.</span></span> <span data-ttu-id="2f226-125">如果指定了 List 参数，则值为 True 。</span><span class="sxs-lookup"><span data-stu-id="2f226-125">When the **List** parameter is specified, the value is **True**.</span></span> <span data-ttu-id="2f226-126">如果未指定，则值为 False。</span><span class="sxs-lookup"><span data-stu-id="2f226-126">When it's not specified, the value is **False**.</span></span>

```
[-List]
```

<span data-ttu-id="2f226-127">还可使用 Syntax 参数和 `Get-Command` 检索命令的语法信息。</span><span class="sxs-lookup"><span data-stu-id="2f226-127">The syntax information for a command can also be retrieved using `Get-Command` using the **Syntax** parameter.</span></span> <span data-ttu-id="2f226-128">这是我一直使用的一种便捷的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="2f226-128">This is a handy shortcut that I use all the time.</span></span> <span data-ttu-id="2f226-129">这可让我快速了解如何使用命令，而无需在多个页面中筛选帮助信息。</span><span class="sxs-lookup"><span data-stu-id="2f226-129">It allows me to quickly learn how to use a command without having to sift through multiple pages of help information.</span></span> <span data-ttu-id="2f226-130">如果我最终需要更多信息，那么我将恢复使用实际帮助内容。</span><span class="sxs-lookup"><span data-stu-id="2f226-130">If I end up needing more information, then I'll revert to using the actual help content.</span></span>

```powershell
Get-Command -Name Get-EventLog -Syntax
```

```Output
Get-EventLog [-LogName] <string> [[-InstanceId] <long[]>] [-ComputerName <string[]>] [-Newest <int>]
 [-After <datetime>] [-Before <datetime>] [-UserName <string[]>] [-Index <int[]> ]
 [-EntryType <string[]>] [-Source <string[]>] [-Message <string>] [-AsBaseObject]
 [<CommonParameters>]

Get-EventLog [-ComputerName <string[]>] [-List] [-AsString] [<CommonParameters>]
```

<span data-ttu-id="2f226-131">在 PowerShell 中使用帮助系统的次数越多，就越容易记住所有不同的细微差别。</span><span class="sxs-lookup"><span data-stu-id="2f226-131">The more you use the help system in PowerShell, the easier remembering all of the different nuances becomes.</span></span> <span data-ttu-id="2f226-132">不知不觉中，使用它会成为第二天性。</span><span class="sxs-lookup"><span data-stu-id="2f226-132">Before you know it, using it becomes second nature.</span></span>
