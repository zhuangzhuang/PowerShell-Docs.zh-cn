---
description: 描述一个语言语句，您可以使用该语句根据条件测试的结果运行命令块。
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_while?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_While
ms.openlocfilehash: 37c277a5919ba5fc39f953e05edaf58d159f3e7c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595826"
---
# <a name="about-while"></a><span data-ttu-id="814b3-103">关于 While</span><span class="sxs-lookup"><span data-stu-id="814b3-103">About While</span></span>

## <a name="short-description"></a><span data-ttu-id="814b3-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="814b3-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="814b3-105">描述一个语言语句，您可以使用该语句根据条件测试的结果运行命令块。</span><span class="sxs-lookup"><span data-stu-id="814b3-105">Describes a language statement that you can use to run a command block based on the results of a conditional test.</span></span>

## <a name="long-description"></a><span data-ttu-id="814b3-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="814b3-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="814b3-107">While 语句 (也称为 While 循环) 是一种用于创建循环的语言构造，只要条件测试的计算结果为 true，就会在命令块中运行命令。</span><span class="sxs-lookup"><span data-stu-id="814b3-107">The While statement (also known as a While loop) is a language construct for creating a loop that runs commands in a command block as long as a conditional test evaluates to true.</span></span> <span data-ttu-id="814b3-108">While 语句的构造比 For 语句更简单，因为它的语法不够复杂。</span><span class="sxs-lookup"><span data-stu-id="814b3-108">The While statement is easier to construct than a For statement because its syntax is less complicated.</span></span> <span data-ttu-id="814b3-109">此外，它比 Foreach 语句更灵活，因为您在 While 语句中指定条件测试来控制循环运行的次数。</span><span class="sxs-lookup"><span data-stu-id="814b3-109">In addition, it is more flexible than the Foreach statement because you specify a conditional test in the While statement to control how many times the loop runs.</span></span>

<span data-ttu-id="814b3-110">下面显示了 While 语句语法：</span><span class="sxs-lookup"><span data-stu-id="814b3-110">The following shows the While statement syntax:</span></span>

```powershell
while (<condition>){<statement list>}
```

<span data-ttu-id="814b3-111">运行 While 语句时，PowerShell 会 `<condition>` 在输入节之前计算语句的部分 `<statement list>` 。</span><span class="sxs-lookup"><span data-stu-id="814b3-111">When you run a While statement, PowerShell evaluates the `<condition>` section of the statement before entering the `<statement list>` section.</span></span> <span data-ttu-id="814b3-112">语句的条件部分解析为 true 或 false。</span><span class="sxs-lookup"><span data-stu-id="814b3-112">The condition portion of the statement resolves to either true or false.</span></span> <span data-ttu-id="814b3-113">只要条件保持为 true，PowerShell 将重新运行该 `<statement list>` 部分。</span><span class="sxs-lookup"><span data-stu-id="814b3-113">As long as the condition remains true, PowerShell reruns the `<statement list>` section.</span></span>

<span data-ttu-id="814b3-114">`<statement list>`语句的部分包含一个或多个命令，这些命令在每次输入或重复循环时都会运行。</span><span class="sxs-lookup"><span data-stu-id="814b3-114">The `<statement list>` section of the statement contains one or more commands that are run each time the loop is entered or repeated.</span></span>

<span data-ttu-id="814b3-115">例如，如果未创建 $val 变量，或者 $val 变量已创建并初始化为0，则以下 While 语句将显示数字1到3。</span><span class="sxs-lookup"><span data-stu-id="814b3-115">For example, the following While statement displays the numbers 1 through 3 if the $val variable has not been created or if the $val variable has been created and initialized to 0.</span></span>

```powershell
while($val -ne 3)
{
    $val++
    Write-Host $val
}
```

<span data-ttu-id="814b3-116">在此示例中，条件 ($val 在 $val \= 0、1、2时不等于 3) 为 true。</span><span class="sxs-lookup"><span data-stu-id="814b3-116">In this example, the condition ($val is not equal to 3) is true while $val \= 0, 1, 2.</span></span> <span data-ttu-id="814b3-117">每次通过循环时，使用 \+ \+ 一元增量运算符 ($val) 递增 1 $val \+ \+ 。</span><span class="sxs-lookup"><span data-stu-id="814b3-117">Each time through the loop, $val is incremented by 1 using the \+\+ unary increment operator ($val\+\+).</span></span> <span data-ttu-id="814b3-118">上次循环的时间，$val \= 3。</span><span class="sxs-lookup"><span data-stu-id="814b3-118">The last time through the loop, $val \= 3.</span></span> <span data-ttu-id="814b3-119">如果 $val 等于3，则 condition 语句的计算结果为 false，并且循环将退出。</span><span class="sxs-lookup"><span data-stu-id="814b3-119">When $val equals 3, the condition statement evaluates to false, and the loop exits.</span></span>

<span data-ttu-id="814b3-120">若要在 PowerShell 命令提示符下轻松写入此命令，可以按以下方式输入：</span><span class="sxs-lookup"><span data-stu-id="814b3-120">To conveniently write this command at the PowerShell command prompt, you can enter it in the following way:</span></span>

```powershell
while($val -ne 3){$val++; Write-Host $val}
```

<span data-ttu-id="814b3-121">请注意，分号将添加1的第一个命令与向控制台写入 $val 的第二个命令中的 $val 隔开。</span><span class="sxs-lookup"><span data-stu-id="814b3-121">Notice that the semicolon separates the first command that adds 1 to $val from the second command that writes the value of $val to the console.</span></span>

## <a name="see-also"></a><span data-ttu-id="814b3-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="814b3-122">SEE ALSO</span></span>

[<span data-ttu-id="814b3-123">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="814b3-123">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="814b3-124">about_Do</span><span class="sxs-lookup"><span data-stu-id="814b3-124">about_Do</span></span>](about_Do.md)

[<span data-ttu-id="814b3-125">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="814b3-125">about_Foreach</span></span>](about_Foreach.md)

[<span data-ttu-id="814b3-126">about_For</span><span class="sxs-lookup"><span data-stu-id="814b3-126">about_For</span></span>](about_For.md)

[<span data-ttu-id="814b3-127">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="814b3-127">about_Language_Keywords</span></span>](about_Language_Keywords.md)

