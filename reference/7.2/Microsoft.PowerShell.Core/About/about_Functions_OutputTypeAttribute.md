---
description: 介绍报告函数返回的对象类型的属性。
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_OutputTypeAttribute
ms.openlocfilehash: 82f1615c4a2fe2a24f104d8e5637103dea6e5a0a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596438"
---
# <a name="about-functions-outputtypeattribute"></a><span data-ttu-id="15fff-103">关于函数 OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="15fff-103">About Functions OutputTypeAttribute</span></span>

## <a name="short-description"></a><span data-ttu-id="15fff-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="15fff-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="15fff-105">介绍报告函数返回的对象类型的属性。</span><span class="sxs-lookup"><span data-stu-id="15fff-105">Describes an attribute that reports the type of object that the function returns.</span></span>

## <a name="long-description"></a><span data-ttu-id="15fff-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="15fff-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="15fff-107">OutputType 属性列出函数返回的对象的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="15fff-107">The OutputType attribute lists the .NET types of objects that the functions returns.</span></span> <span data-ttu-id="15fff-108">可以使用其可选的 ParameterSetName 参数为每个参数集列出不同的输出类型。</span><span class="sxs-lookup"><span data-stu-id="15fff-108">You can use its optional ParameterSetName parameter to list different output types for each parameter set.</span></span>

<span data-ttu-id="15fff-109">简单函数和高级函数支持 OutputType 特性。</span><span class="sxs-lookup"><span data-stu-id="15fff-109">The OutputType attribute is supported on simple and advanced functions.</span></span> <span data-ttu-id="15fff-110">它独立于 CmdletBinding 属性。</span><span class="sxs-lookup"><span data-stu-id="15fff-110">It is independent of the CmdletBinding attribute.</span></span>

<span data-ttu-id="15fff-111">OutputType 属性提供该 cmdlet 返回的 **FunctionInfo** 对象的 outputtype 属性的值的值 `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="15fff-111">The OutputType attribute provides the value of the OutputType property of the **System.Management.Automation.FunctionInfo** object that the `Get-Command` cmdlet returns.</span></span>

<span data-ttu-id="15fff-112">OutputType 属性值只是一个文档说明。</span><span class="sxs-lookup"><span data-stu-id="15fff-112">The OutputType attribute value is only a documentation note.</span></span> <span data-ttu-id="15fff-113">它不是从函数代码派生或与实际函数输出进行比较。</span><span class="sxs-lookup"><span data-stu-id="15fff-113">It is not derived from the function code or compared to the actual function output.</span></span> <span data-ttu-id="15fff-114">因此，值可能不准确。</span><span class="sxs-lookup"><span data-stu-id="15fff-114">As such, the value might be inaccurate.</span></span>

## <a name="syntax"></a><span data-ttu-id="15fff-115">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="15fff-115">SYNTAX</span></span>

<span data-ttu-id="15fff-116">函数的 OutputType 特性具有以下语法：</span><span class="sxs-lookup"><span data-stu-id="15fff-116">The OutputType attribute of functions has the following syntax:</span></span>

```
[OutputType([<TypeLiteral>], ParameterSetName="<Name>")]
[OutputType("<TypeNameString>", ParameterSetName="<Name>")]
```

<span data-ttu-id="15fff-117">**ParameterSetName** 参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="15fff-117">The **ParameterSetName** parameter is optional.</span></span>

<span data-ttu-id="15fff-118">可以列出 OutputType 属性中的多个类型。</span><span class="sxs-lookup"><span data-stu-id="15fff-118">You can list multiple types in the OutputType attribute.</span></span>

```
[OutputType([<Type1>],[<Type2>],[<Type3>])]
```

<span data-ttu-id="15fff-119">您可以使用 **ParameterSetName** 参数来指示不同的参数集返回不同的类型。</span><span class="sxs-lookup"><span data-stu-id="15fff-119">You can use the **ParameterSetName** parameter to indicate that different parameter sets return different types.</span></span>

```
[OutputType([<Type1>], ParameterSetName=("<Set1>","<Set2>"))]
[OutputType([<Type2>], ParameterSetName="<Set3>")]
```

<span data-ttu-id="15fff-120">将 OutputType 属性语句放在语句之前的属性列表中 `Param` 。</span><span class="sxs-lookup"><span data-stu-id="15fff-120">Place the OutputType attribute statements in the attributes list that precedes the `Param` statement.</span></span>

<span data-ttu-id="15fff-121">下面的示例演示了一个简单函数中 OutputType 特性的位置。</span><span class="sxs-lookup"><span data-stu-id="15fff-121">The following example shows the placement of the OutputType attribute in a simple function.</span></span>

```powershell
function SimpleFunction2
{
  [OutputType([<Type>])]
  Param ($Parameter1)

  <function body>
}
```

<span data-ttu-id="15fff-122">下面的示例演示了在高级函数中放置 OutputType 属性的情况。</span><span class="sxs-lookup"><span data-stu-id="15fff-122">The following example shows the placement of the OutputType attribute in advanced functions.</span></span>

```powershell
function AdvancedFunction1
{
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}

function AdvancedFunction2
{
  [CmdletBinding(SupportsShouldProcess=<Boolean>)]
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}
```

## <a name="examples"></a><span data-ttu-id="15fff-123">示例</span><span class="sxs-lookup"><span data-stu-id="15fff-123">EXAMPLES</span></span>

### <a name="example-1-create-a-function-that-has-the-outputtype-of-string"></a><span data-ttu-id="15fff-124">示例1：创建具有字符串 OutputType 的函数</span><span class="sxs-lookup"><span data-stu-id="15fff-124">Example 1: Create a function that has the OutputType of String</span></span>

```powershell
function Send-Greeting
{
  [OutputType([String])]
  Param ($Name)

  "Hello, $Name"
}
```

<span data-ttu-id="15fff-125">若要查看生成的输出类型属性，请使用 `Get-Command` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="15fff-125">To see the resulting output type property, use the `Get-Command` cmdlet.</span></span>

```powershell
(Get-Command Send-Greeting).OutputType
```

```Output
Name                                               Type
----                                               ----
System.String                                      System.String
```

### <a name="example-2-use-the-output-attribute-to-indicate-dynamic-output-types"></a><span data-ttu-id="15fff-126">示例2：使用 Output 特性指示动态输出类型</span><span class="sxs-lookup"><span data-stu-id="15fff-126">Example 2: Use the Output attribute to indicate dynamic output types</span></span>

<span data-ttu-id="15fff-127">以下高级函数使用 OutputType 属性来指示函数返回不同的类型，具体取决于 function 命令中使用的参数集。</span><span class="sxs-lookup"><span data-stu-id="15fff-127">The following advanced function uses the OutputType attribute to indicate that the function returns different types depending on the parameter set used in the function command.</span></span>

```powershell
function Get-User
{
  [CmdletBinding(DefaultParameterSetName="ID")]

  [OutputType("System.Int32", ParameterSetName="ID")]
  [OutputType([String], ParameterSetName="Name")]

  Param (
    [parameter(Mandatory=$true, ParameterSetName="ID")]
    [Int[]]
    $UserID,

    [parameter(Mandatory=$true, ParameterSetName="Name")]
    [String[]]
    $UserName
  )

  <function body>
}
```

### <a name="example-3-shows-when-an-actual-output-differs-from-the-outputtype"></a><span data-ttu-id="15fff-128">示例3：显示实际输出不同于 OutputType 的情况</span><span class="sxs-lookup"><span data-stu-id="15fff-128">Example 3: Shows when an actual output differs from the OutputType</span></span>

<span data-ttu-id="15fff-129">下面的示例演示 output type 属性值显示 OutputType 属性的值，即使它不准确。</span><span class="sxs-lookup"><span data-stu-id="15fff-129">The following example demonstrates that the output type property value displays the value of the OutputType attribute, even when it is inaccurate.</span></span>

<span data-ttu-id="15fff-130">`Get-Time`函数返回一个字符串，该字符串包含任何 DateTime 对象中的时间的缩写形式。</span><span class="sxs-lookup"><span data-stu-id="15fff-130">The `Get-Time` function returns a string that contains the short form of the time in any DateTime object.</span></span> <span data-ttu-id="15fff-131">但是，OutputType 属性会报告它 **返回了 system.string 对象。**</span><span class="sxs-lookup"><span data-stu-id="15fff-131">However, the OutputType attribute reports that it returns a **System.DateTime** object.</span></span>

```powershell
function Get-Time
{
  [OutputType([DateTime])]
  Param (
    [parameter(Mandatory=$true)]
    [Datetime]$DateTime
  )

  $DateTime.ToShortTimeString()
}
```

<span data-ttu-id="15fff-132">`GetType()`方法确认函数返回一个字符串。</span><span class="sxs-lookup"><span data-stu-id="15fff-132">The `GetType()` method confirms that the function returns a string.</span></span>

```powershell
(Get-Time -DateTime (Get-Date)).GetType().FullName
```

```Output
System.String
```

<span data-ttu-id="15fff-133">但是，OutputType 属性从 OutputType 特性获取其值，它报告该函数返回 **DateTime** 对象。</span><span class="sxs-lookup"><span data-stu-id="15fff-133">However, the OutputType property, which gets its value from the OutputType attribute, reports that the function returns a **DateTime** object.</span></span>

```powershell
(Get-Command Get-Time).OutputType
```

```Output
Name                                      Type
----                                      ----
System.DateTime                           System.DateTime
```

### <a name="example-4-a-function--that-shouldnt-have-output"></a><span data-ttu-id="15fff-134">示例4：不应具有输出的函数</span><span class="sxs-lookup"><span data-stu-id="15fff-134">Example 4: A function  that shouldn't have output</span></span>

<span data-ttu-id="15fff-135">下面的示例演示了应执行和操作但不返回任何内容的自定义函数。</span><span class="sxs-lookup"><span data-stu-id="15fff-135">The following example shows a custom function that should perform and action but not return anything.</span></span>

```powershell
function Invoke-Notepad
{
  [OutputType([System.Void])]
  Param ()
  & notepad.exe | Out-Null
}
```

## <a name="notes"></a><span data-ttu-id="15fff-136">注释</span><span class="sxs-lookup"><span data-stu-id="15fff-136">NOTES</span></span>

<span data-ttu-id="15fff-137">**FunctionInfo** 对象的 OutputType 属性的值是 **PSTypeName** 对象的数组，其中每个对象都具有 Name 和 Type 属性。</span><span class="sxs-lookup"><span data-stu-id="15fff-137">The value of the OutputType property of a **FunctionInfo** object is an array of **System.Management.Automation.PSTypeName** objects, each of which have Name and Type properties.</span></span>

<span data-ttu-id="15fff-138">若要仅获取每个输出类型的名称，请使用具有以下格式的命令。</span><span class="sxs-lookup"><span data-stu-id="15fff-138">To get only the name of each output type, use a command with the following format.</span></span>

```powershell
(Get-Command Get-Time).OutputType | ForEach {$_.Name}
```

<span data-ttu-id="15fff-139">OutputType 属性的值可以为 null。</span><span class="sxs-lookup"><span data-stu-id="15fff-139">The value of the OutputType property can be null.</span></span> <span data-ttu-id="15fff-140">当输出不是 .NET 类型（如 **WMI** 对象或对象的格式化视图）时，请使用 null 值。</span><span class="sxs-lookup"><span data-stu-id="15fff-140">Use a null value when the output is a not a .NET type, such as a **WMI** object or a formatted view of an object.</span></span>

## <a name="see-also"></a><span data-ttu-id="15fff-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15fff-141">SEE ALSO</span></span>

[<span data-ttu-id="15fff-142">about_Functions</span><span class="sxs-lookup"><span data-stu-id="15fff-142">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="15fff-143">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="15fff-143">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="15fff-144">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="15fff-144">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="15fff-145">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="15fff-145">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="15fff-146">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="15fff-146">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

