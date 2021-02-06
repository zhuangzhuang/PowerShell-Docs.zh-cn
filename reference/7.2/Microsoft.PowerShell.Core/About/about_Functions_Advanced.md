---
description: 引入了一种使用脚本创建 cmdlet 的高级功能。
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced
ms.openlocfilehash: a0b8b027c91f2adedfcecd07bfc80392c1b1e071
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597658"
---
# <a name="about-functions-advanced"></a><span data-ttu-id="943bb-103">关于函数高级</span><span class="sxs-lookup"><span data-stu-id="943bb-103">About Functions Advanced</span></span>

## <a name="short-description"></a><span data-ttu-id="943bb-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="943bb-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="943bb-105">引入了一种使用脚本创建 cmdlet 的高级功能。</span><span class="sxs-lookup"><span data-stu-id="943bb-105">Introduces advanced functions that are a way to create cmdlets using scripts.</span></span>

## <a name="long-description"></a><span data-ttu-id="943bb-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="943bb-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="943bb-107">Cmdlet 是参与 PowerShell 管道语义的单个命令。</span><span class="sxs-lookup"><span data-stu-id="943bb-107">A cmdlet is a single command that participates in the pipeline semantics of PowerShell.</span></span> <span data-ttu-id="943bb-108">这包括二进制 cmdlet、高级脚本函数、CDXML 和工作流。</span><span class="sxs-lookup"><span data-stu-id="943bb-108">This includes binary cmdlets, advanced script functions, CDXML, and Workflows.</span></span>

<span data-ttu-id="943bb-109">利用高级功能，你可以创建以 PowerShell 函数形式编写的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="943bb-109">Advanced functions allow you create cmdlets that are written as a PowerShell function.</span></span> <span data-ttu-id="943bb-110">利用高级功能，无需编写和编译二进制 cmdlet 即可更轻松地创建 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="943bb-110">Advanced functions make it easier to create cmdlets without having to write and compile a binary cmdlet.</span></span> <span data-ttu-id="943bb-111">二进制 cmdlet 是用 .NET 语言（如 c #）编写的 .NET 类。</span><span class="sxs-lookup"><span data-stu-id="943bb-111">Binary cmdlets are .NET classes that are written in a .NET language such as C#.</span></span>

<span data-ttu-id="943bb-112">高级函数使用 `CmdletBinding` 特性将它们标识为充当 cmdlet 的函数。</span><span class="sxs-lookup"><span data-stu-id="943bb-112">Advanced functions use the `CmdletBinding` attribute to identify them as functions that act like cmdlets.</span></span> <span data-ttu-id="943bb-113">`CmdletBinding`属性类似于编译的 cmdlet 类中使用的 cmdlet 属性，用于将类标识为 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="943bb-113">The `CmdletBinding` attribute is similar to the Cmdlet attribute that is used in compiled cmdlet classes to identify the class as a cmdlet.</span></span> <span data-ttu-id="943bb-114">有关此属性的详细信息，请参阅 [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)。</span><span class="sxs-lookup"><span data-stu-id="943bb-114">For more information about this attribute, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>

<span data-ttu-id="943bb-115">下面的示例演示一个函数，该函数接受名称，然后使用提供的名称打印问候语。</span><span class="sxs-lookup"><span data-stu-id="943bb-115">The following example shows a function that accepts a name and then prints a greeting using the supplied name.</span></span> <span data-ttu-id="943bb-116">另请注意，此函数定义一个名称，该名称包括一个谓词 (发送) 和名词 (问候语) 对，如编译 cmdlet 的动词-名词对。</span><span class="sxs-lookup"><span data-stu-id="943bb-116">Also notice that this function defines a name that includes a verb (Send) and noun (Greeting) pair like the verb-noun pair of a compiled cmdlet.</span></span> <span data-ttu-id="943bb-117">但是，函数不需要具有动词-名词名称。</span><span class="sxs-lookup"><span data-stu-id="943bb-117">However, functions are not required to have a verb-noun name.</span></span>

```powershell
function Send-Greeting
{
    [CmdletBinding()]
    Param(
        [Parameter(Mandatory=$true)]
        [string] $Name
    )

    Process
    {
        Write-Host ("Hello " + $Name + "!")
    }
}
```

<span data-ttu-id="943bb-118">函数的参数是使用参数特性声明的。</span><span class="sxs-lookup"><span data-stu-id="943bb-118">The parameters of the function are declared by using the Parameter attribute.</span></span>
<span data-ttu-id="943bb-119">此特性可以单独使用，也可以与 Alias 特性或其他一些参数验证特性结合使用。</span><span class="sxs-lookup"><span data-stu-id="943bb-119">This attribute can be used alone, or it can be combined with the Alias attribute or with several other parameter validation attributes.</span></span> <span data-ttu-id="943bb-120">有关如何声明参数 (包括在运行时) 添加的动态参数的详细信息，请参阅 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="943bb-120">For more information about how to declare parameters (including dynamic parameters that are added at runtime), see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

<span data-ttu-id="943bb-121">先前函数的实际工作是在进程块中执行的，该进程块等效于编译的 cmdlet 用来处理传递到 cmdlet 的数据的 ProcessingRecord 方法。</span><span class="sxs-lookup"><span data-stu-id="943bb-121">The actual work of the previous function is performed in the Process block, which is equivalent to the ProcessingRecord method that is used by compiled cmdlets to process the data that is passed to the cmdlet.</span></span> <span data-ttu-id="943bb-122">[About_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)主题中介绍了此块以及 Begin 和 End 块。</span><span class="sxs-lookup"><span data-stu-id="943bb-122">This block, along with the Begin and End blocks, is described in the [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) topic.</span></span>

<span data-ttu-id="943bb-123">高级函数与已编译的 cmdlet 在以下方面有所不同：</span><span class="sxs-lookup"><span data-stu-id="943bb-123">Advanced functions differ from compiled cmdlets in the following ways:</span></span>

- <span data-ttu-id="943bb-124">当字符串数组绑定到布尔参数时，高级函数参数绑定不会引发异常。</span><span class="sxs-lookup"><span data-stu-id="943bb-124">Advanced function parameter binding does not throw an exception when an array of strings is bound to a Boolean parameter.</span></span>
- <span data-ttu-id="943bb-125">ValidateSet 属性和 ValidatePattern 属性不能传递指定的参数。</span><span class="sxs-lookup"><span data-stu-id="943bb-125">The ValidateSet attribute and the ValidatePattern attribute cannot pass named parameters.</span></span>
- <span data-ttu-id="943bb-126">不能在事务中使用高级函数。</span><span class="sxs-lookup"><span data-stu-id="943bb-126">Advanced functions cannot be used in transactions.</span></span>

## <a name="see-also"></a><span data-ttu-id="943bb-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="943bb-127">SEE ALSO</span></span>

[<span data-ttu-id="943bb-128">about_Functions</span><span class="sxs-lookup"><span data-stu-id="943bb-128">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="943bb-129">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="943bb-129">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="943bb-130">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="943bb-130">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="943bb-131">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="943bb-131">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="943bb-132">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="943bb-132">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)
