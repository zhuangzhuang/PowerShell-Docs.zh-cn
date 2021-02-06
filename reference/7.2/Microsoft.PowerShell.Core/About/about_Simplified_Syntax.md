---
description: 介绍更简单、更自然语言的对象集合脚本筛选方式。
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_simplified_syntax?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Simplified_Syntax
ms.openlocfilehash: dbd30d566414f784e7d5eca04af716c2bf1642b9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597467"
---
# <a name="about_simplified_syntax"></a><span data-ttu-id="3cae0-103">about_Simplified_Syntax</span><span class="sxs-lookup"><span data-stu-id="3cae0-103">about_Simplified_Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="3cae0-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="3cae0-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="3cae0-105">介绍更简单、更自然语言的对象集合脚本筛选方式。</span><span class="sxs-lookup"><span data-stu-id="3cae0-105">Describes easier, more natural-language ways of scripting filters for collections of objects.</span></span>

## <a name="long-description"></a><span data-ttu-id="3cae0-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="3cae0-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="3cae0-107">Windows PowerShell 3.0 中引入的简化语法使你可以在不使用脚本块的情况下生成某些筛选器命令。</span><span class="sxs-lookup"><span data-stu-id="3cae0-107">Simplified syntax, introduced in Windows PowerShell 3.0, lets you build some filter commands without using script blocks.</span></span> <span data-ttu-id="3cae0-108">简化的语法更加类似于自然语言，并主要用于通过管道转换为命令的对象集合及其 `Where-Object` 对应的 `ForEach-Object` 别名 `where` 和 `foreach` 。</span><span class="sxs-lookup"><span data-stu-id="3cae0-108">The simplified syntax more closely resembles natural language, and is primarily useful with collections of objects that get piped into commands `Where-Object` and `ForEach-Object` and their corresponding aliases `where` and `foreach`.</span></span>

<span data-ttu-id="3cae0-109">您可以对集合的成员使用方法 (最常见的是数组) ，而不引用 `$_` 脚本块中的自动变量。</span><span class="sxs-lookup"><span data-stu-id="3cae0-109">You can use a method on the members of a collection (most commonly, an array) without referring to the automatic variable `$_` inside a script block.</span></span>

<span data-ttu-id="3cae0-110">请考虑以下两个调用：</span><span class="sxs-lookup"><span data-stu-id="3cae0-110">Consider the following two invocations:</span></span>

### <a name="standard-syntax"></a><span data-ttu-id="3cae0-111">标准语法</span><span class="sxs-lookup"><span data-stu-id="3cae0-111">Standard Syntax</span></span>

```powershell
dir Cert:\LocalMachine\Root | where { $_.FriendlyName -eq 'Verisign' }
dir Cert:\ -Recurse | foreach { $_.GetKeyAlgorithm() }
```

### <a name="simplified-syntax"></a><span data-ttu-id="3cae0-112">简化的语法</span><span class="sxs-lookup"><span data-stu-id="3cae0-112">Simplified syntax</span></span>

<span data-ttu-id="3cae0-113">在简化语法下，处理集合中对象成员的比较运算符被视为参数。</span><span class="sxs-lookup"><span data-stu-id="3cae0-113">Under the simplified syntax, comparison operators that work on members of objects in a collection are treated as parameters.</span></span> <span data-ttu-id="3cae0-114">您可以对集合中的对象调用方法，而不引用 `$_` 脚本块中的自动变量。</span><span class="sxs-lookup"><span data-stu-id="3cae0-114">You can invoke a method on objects in a collection without referring to the automatic variable `$_` inside a script block.</span></span>
<span data-ttu-id="3cae0-115">将以下两个调用与上一示例中的调用进行比较：</span><span class="sxs-lookup"><span data-stu-id="3cae0-115">Compare the following two invocations to those of the previous example:</span></span>

```powershell
dir Cert:\LocalMachine\Root | where FriendlyName -eq 'Verisign'
dir Cert:\ -Recurse | foreach GetKeyAlgorithm
```

<span data-ttu-id="3cae0-116">虽然这两种语法都起作用，但简化的语法返回结果，而不引用 `$_` 脚本块中的自动变量。</span><span class="sxs-lookup"><span data-stu-id="3cae0-116">While both syntaxes work, the simplified syntax returns results without referring to the automatic variable `$_` inside a script block.</span></span>
<span data-ttu-id="3cae0-117">方法名称 `GetKeyAlgorithm` 被视为的参数 `ForEach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="3cae0-117">The method name `GetKeyAlgorithm` is treated as a parameter of `ForEach-Object`.</span></span>
<span data-ttu-id="3cae0-118">第二个命令将返回相同的结果，但不会返回错误，因为简化的语法不会尝试返回指定参数不适用于的项的结果。</span><span class="sxs-lookup"><span data-stu-id="3cae0-118">The second command returns the same results, but without errors, because the simplified syntax does not attempt to return results for items for which the specified argument did not apply.</span></span>

<span data-ttu-id="3cae0-119">在此示例中， `Process` 属性 `Description` 作为成员名称参数传递到 `ForEach-Object` 命令。</span><span class="sxs-lookup"><span data-stu-id="3cae0-119">In this example, the `Process` property `Description` is passed as the member name parameter to the `ForEach-Object` command.</span></span> <span data-ttu-id="3cae0-120">结果是活动过程的说明。</span><span class="sxs-lookup"><span data-stu-id="3cae0-120">The results are descriptions of active processes.</span></span>

```powershell
Get-Process | foreach Description
```

<span data-ttu-id="3cae0-121">在此示例中， `DirectoryInfo` 方法 `GetFiles` 作为命令的成员名称参数传递 `ForEach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="3cae0-121">In this example, the `DirectoryInfo` method `GetFiles` is passed as the member name parameter of the `ForEach-Object` command.</span></span>  
<span data-ttu-id="3cae0-122">用搜索模式参数调用方法 `.*` 。</span><span class="sxs-lookup"><span data-stu-id="3cae0-122">The method is called with the search pattern parameter `.*`.</span></span>  
<span data-ttu-id="3cae0-123">结果为 `FileInfo` 用户主目录中所有 Unix 样式的隐藏文件的记录。</span><span class="sxs-lookup"><span data-stu-id="3cae0-123">The results are `FileInfo` records for all Unix-style hidden files in user home directories.</span></span> 

```powershell
Get-ChildItem /home -Directory | foreach GetFiles .*
```

## <a name="see-also"></a><span data-ttu-id="3cae0-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3cae0-124">SEE ALSO</span></span>

- [<span data-ttu-id="3cae0-125">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="3cae0-125">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="3cae0-126">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="3cae0-126">about_Foreach</span></span>](about_Foreach.md)
- [<span data-ttu-id="3cae0-127">Where-Object</span><span class="sxs-lookup"><span data-stu-id="3cae0-127">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)
- [<span data-ttu-id="3cae0-128">Foreach-对象</span><span class="sxs-lookup"><span data-stu-id="3cae0-128">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)

