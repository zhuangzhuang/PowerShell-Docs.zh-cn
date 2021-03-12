---
description: 介绍 Throw 关键字，用于生成终止错误。
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: e573722154fff99363b26806064ec17c8903bfd8
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194179"
---
# <a name="about-throw"></a><span data-ttu-id="e2896-103">关于 Throw</span><span class="sxs-lookup"><span data-stu-id="e2896-103">About Throw</span></span>

## <a name="short-description"></a><span data-ttu-id="e2896-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="e2896-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="e2896-105">介绍 Throw 关键字，用于生成终止错误。</span><span class="sxs-lookup"><span data-stu-id="e2896-105">Describes the Throw keyword, which generates a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="e2896-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="e2896-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="e2896-107">Throw 关键字导致终止错误。</span><span class="sxs-lookup"><span data-stu-id="e2896-107">The Throw keyword causes a terminating error.</span></span> <span data-ttu-id="e2896-108">可以使用 Throw 关键字停止对命令、函数或脚本的处理。</span><span class="sxs-lookup"><span data-stu-id="e2896-108">You can use the Throw keyword to stop the processing of a command, function, or script.</span></span>

<span data-ttu-id="e2896-109">例如，可以在 If 语句的脚本块中使用 Throw 关键字来响应某个条件，或在 try-catch Finally 语句的 Catch 块中使用 Throw 关键字。</span><span class="sxs-lookup"><span data-stu-id="e2896-109">For example, you can use the Throw keyword in the script block of an If statement to respond to a condition or in the Catch block of a Try-Catch-Finally statement.</span></span> <span data-ttu-id="e2896-110">还可以在参数声明中使用 Throw 关键字，使函数参数成为必需的。</span><span class="sxs-lookup"><span data-stu-id="e2896-110">You can also use the Throw keyword in a parameter declaration to make a function parameter mandatory.</span></span>

<span data-ttu-id="e2896-111">Throw 关键字可以引发任何对象，例如用户消息字符串或导致错误的对象。</span><span class="sxs-lookup"><span data-stu-id="e2896-111">The Throw keyword can throw any object, such as a user message string or the object that caused the error.</span></span>

## <a name="syntax"></a><span data-ttu-id="e2896-112">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e2896-112">SYNTAX</span></span>

<span data-ttu-id="e2896-113">Throw 关键字的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="e2896-113">The syntax of the Throw keyword is as follows:</span></span>

```powershell
throw [<expression>]
```

<span data-ttu-id="e2896-114">Throw 语法中的表达式是可选的。</span><span class="sxs-lookup"><span data-stu-id="e2896-114">The expression in the Throw syntax is optional.</span></span> <span data-ttu-id="e2896-115">如果 Throw 语句未出现在 Catch 块中，并且它不包含表达式，则会生成一个 ScriptHalted 错误。</span><span class="sxs-lookup"><span data-stu-id="e2896-115">When the Throw statement does not appear in a Catch block, and it does not include an expression, it generates a ScriptHalted error.</span></span>

```powershell
C:\PS> throw

ScriptHalted
At line:1 char:6
+ throw <<<<
+ CategoryInfo          : OperationStopped: (:) [], RuntimeException
+ FullyQualifiedErrorId : ScriptHalted
```

<span data-ttu-id="e2896-116">如果在没有表达式的 Catch 块中使用 Throw 关键字，将再次引发当前的 RuntimeException。</span><span class="sxs-lookup"><span data-stu-id="e2896-116">If the Throw keyword is used in a Catch block without an expression, it throws the current RuntimeException again.</span></span> <span data-ttu-id="e2896-117">有关详细信息，请参阅 about_Try_Catch_Finally。</span><span class="sxs-lookup"><span data-stu-id="e2896-117">For more information, see about_Try_Catch_Finally.</span></span>

## <a name="throwing-a-string"></a><span data-ttu-id="e2896-118">引发字符串</span><span class="sxs-lookup"><span data-stu-id="e2896-118">THROWING A STRING</span></span>

<span data-ttu-id="e2896-119">Throw 语句中的可选表达式可以是字符串，如下面的示例中所示：</span><span class="sxs-lookup"><span data-stu-id="e2896-119">The optional expression in a Throw statement can be a string, as shown in the following example:</span></span>

```powershell
C:\PS> throw "This is an error."

This is an error.
At line:1 char:6
+ throw <<<<  "This is an error."
+ CategoryInfo          : OperationStopped: (This is an error.:String) [], R
untimeException
+ FullyQualifiedErrorId : This is an error.
```

## <a name="throwing-other-objects"></a><span data-ttu-id="e2896-120">引发其他对象</span><span class="sxs-lookup"><span data-stu-id="e2896-120">THROWING OTHER OBJECTS</span></span>

<span data-ttu-id="e2896-121">表达式还可以是一个对象，该对象引发表示 PowerShell 进程的对象，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="e2896-121">The expression can also be an object that throws the object that represents the PowerShell process, as shown in the following example:</span></span>

```powershell
C:\PS> throw (get-process PowerShell)

System.Diagnostics.Process (PowerShell)
At line:1 char:6
+ throw <<<<  (get-process PowerShell)
+ CategoryInfo          : OperationStopped: (System.Diagnostics.Process (Pow
erShell):Process) [],
RuntimeException
+ FullyQualifiedErrorId : System.Diagnostics.Process (PowerShell)
```

<span data-ttu-id="e2896-122">您可以使用 $error 自动变量中 ErrorRecord 对象的 TargetObject 属性来检查错误。</span><span class="sxs-lookup"><span data-stu-id="e2896-122">You can use the TargetObject property of the ErrorRecord object in the $error automatic variable to examine the error.</span></span>

```powershell
C:\PS> $error[0].targetobject

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
319      26    61016      70864   568     3.28   5548 PowerShell
```

<span data-ttu-id="e2896-123">还可以引发 ErrorRecord 对象或 Microsoft .NET Framework 异常。</span><span class="sxs-lookup"><span data-stu-id="e2896-123">You can also throw an ErrorRecord object or a Microsoft .NET Framework exception.</span></span> <span data-ttu-id="e2896-124">下面的示例使用 Throw 关键字来引发 FormatException 对象。</span><span class="sxs-lookup"><span data-stu-id="e2896-124">The following example uses the Throw keyword to throw a System.FormatException object.</span></span>

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

One of the identified items was in an invalid format.
At line:1 char:6
+ throw <<<<  $formatError
+ CategoryInfo          : OperationStopped: (:) [], FormatException
+ FullyQualifiedErrorId : One of the identified items was in an invalid
format.
```

## <a name="resulting-error"></a><span data-ttu-id="e2896-125">产生的错误</span><span class="sxs-lookup"><span data-stu-id="e2896-125">RESULTING ERROR</span></span>

<span data-ttu-id="e2896-126">Throw 关键字可以生成 ErrorRecord 对象。</span><span class="sxs-lookup"><span data-stu-id="e2896-126">The Throw keyword can generate an ErrorRecord object.</span></span> <span data-ttu-id="e2896-127">ErrorRecord 对象的 Exception 属性包含 RuntimeException 对象。</span><span class="sxs-lookup"><span data-stu-id="e2896-127">The Exception property of the ErrorRecord object contains a RuntimeException object.</span></span> <span data-ttu-id="e2896-128">ErrorRecord 对象和 RuntimeException 对象的其余部分将与 Throw 关键字引发的对象不同。</span><span class="sxs-lookup"><span data-stu-id="e2896-128">The remainder of the ErrorRecord object and the RuntimeException object vary with the object that the Throw keyword throws.</span></span>

<span data-ttu-id="e2896-129">RunTimeException 对象包装在 ErrorRecord 对象中，ErrorRecord 对象自动保存在 $Error 自动变量中。</span><span class="sxs-lookup"><span data-stu-id="e2896-129">The RunTimeException object is wrapped in an ErrorRecord object, and the ErrorRecord object is automatically saved in the $Error automatic variable.</span></span>

## <a name="using-throw-to-create-a-mandatory-parameter"></a><span data-ttu-id="e2896-130">使用 THROW 创建强制参数</span><span class="sxs-lookup"><span data-stu-id="e2896-130">USING THROW TO CREATE A MANDATORY PARAMETER</span></span>

<span data-ttu-id="e2896-131">您可以使用 Throw 关键字使函数参数成为必需的。</span><span class="sxs-lookup"><span data-stu-id="e2896-131">You can use the Throw keyword to make a function parameter mandatory.</span></span>

<span data-ttu-id="e2896-132">这是使用 Parameter 关键字的必需参数的替代方法。</span><span class="sxs-lookup"><span data-stu-id="e2896-132">This is an alternative to using the Mandatory parameter of the Parameter keyword.</span></span> <span data-ttu-id="e2896-133">使用强制参数时，系统将提示用户输入所需的参数值。</span><span class="sxs-lookup"><span data-stu-id="e2896-133">When you use the Mandatory parameter, the system prompts the user for the required parameter value.</span></span> <span data-ttu-id="e2896-134">使用 Throw 关键字时，该命令将停止并显示错误记录。</span><span class="sxs-lookup"><span data-stu-id="e2896-134">When you use the Throw keyword, the command stops and displays the error record.</span></span>

<span data-ttu-id="e2896-135">例如，参数子表达式中的 Throw 关键字使 Path 参数成为函数中的必需参数。</span><span class="sxs-lookup"><span data-stu-id="e2896-135">For example, the Throw keyword in the parameter subexpression makes the Path parameter a required parameter in the function.</span></span>

<span data-ttu-id="e2896-136">在这种情况下，Throw 关键字将引发一个消息字符串，但它是 Throw 关键字的存在，如果未指定 Path 参数，则会生成终止错误。</span><span class="sxs-lookup"><span data-stu-id="e2896-136">In this case, the Throw keyword throws a message string, but it is the presence of the Throw keyword that generates the terminating error if the Path parameter is not specified.</span></span> <span data-ttu-id="e2896-137">以下引发的表达式是可选的。</span><span class="sxs-lookup"><span data-stu-id="e2896-137">The expression that follows Throw is optional.</span></span>

```powershell
function Get-XMLFiles
{
  param ($path = $(throw "The Path parameter is required."))
  dir -path $path\*.xml -recurse |
    sort lastwritetime |
      ft lastwritetime, attributes, name  -auto
}
```

## <a name="see-also"></a><span data-ttu-id="e2896-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2896-138">SEE ALSO</span></span>

[<span data-ttu-id="e2896-139">about_Break</span><span class="sxs-lookup"><span data-stu-id="e2896-139">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="e2896-140">about_Continue</span><span class="sxs-lookup"><span data-stu-id="e2896-140">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="e2896-141">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="e2896-141">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="e2896-142">about_Trap</span><span class="sxs-lookup"><span data-stu-id="e2896-142">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="e2896-143">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="e2896-143">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
