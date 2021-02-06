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
# <a name="about-functions-outputtypeattribute"></a>关于函数 OutputTypeAttribute

## <a name="short-description"></a>简短说明
介绍报告函数返回的对象类型的属性。

## <a name="long-description"></a>详细说明

OutputType 属性列出函数返回的对象的 .NET 类型。 可以使用其可选的 ParameterSetName 参数为每个参数集列出不同的输出类型。

简单函数和高级函数支持 OutputType 特性。 它独立于 CmdletBinding 属性。

OutputType 属性提供该 cmdlet 返回的 **FunctionInfo** 对象的 outputtype 属性的值的值 `Get-Command` 。

OutputType 属性值只是一个文档说明。 它不是从函数代码派生或与实际函数输出进行比较。 因此，值可能不准确。

## <a name="syntax"></a>SYNTAX

函数的 OutputType 特性具有以下语法：

```
[OutputType([<TypeLiteral>], ParameterSetName="<Name>")]
[OutputType("<TypeNameString>", ParameterSetName="<Name>")]
```

**ParameterSetName** 参数是可选的。

可以列出 OutputType 属性中的多个类型。

```
[OutputType([<Type1>],[<Type2>],[<Type3>])]
```

您可以使用 **ParameterSetName** 参数来指示不同的参数集返回不同的类型。

```
[OutputType([<Type1>], ParameterSetName=("<Set1>","<Set2>"))]
[OutputType([<Type2>], ParameterSetName="<Set3>")]
```

将 OutputType 属性语句放在语句之前的属性列表中 `Param` 。

下面的示例演示了一个简单函数中 OutputType 特性的位置。

```powershell
function SimpleFunction2
{
  [OutputType([<Type>])]
  Param ($Parameter1)

  <function body>
}
```

下面的示例演示了在高级函数中放置 OutputType 属性的情况。

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

## <a name="examples"></a>示例

### <a name="example-1-create-a-function-that-has-the-outputtype-of-string"></a>示例1：创建具有字符串 OutputType 的函数

```powershell
function Send-Greeting
{
  [OutputType([String])]
  Param ($Name)

  "Hello, $Name"
}
```

若要查看生成的输出类型属性，请使用 `Get-Command` cmdlet。

```powershell
(Get-Command Send-Greeting).OutputType
```

```Output
Name                                               Type
----                                               ----
System.String                                      System.String
```

### <a name="example-2-use-the-output-attribute-to-indicate-dynamic-output-types"></a>示例2：使用 Output 特性指示动态输出类型

以下高级函数使用 OutputType 属性来指示函数返回不同的类型，具体取决于 function 命令中使用的参数集。

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

### <a name="example-3-shows-when-an-actual-output-differs-from-the-outputtype"></a>示例3：显示实际输出不同于 OutputType 的情况

下面的示例演示 output type 属性值显示 OutputType 属性的值，即使它不准确。

`Get-Time`函数返回一个字符串，该字符串包含任何 DateTime 对象中的时间的缩写形式。 但是，OutputType 属性会报告它 **返回了 system.string 对象。**

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

`GetType()`方法确认函数返回一个字符串。

```powershell
(Get-Time -DateTime (Get-Date)).GetType().FullName
```

```Output
System.String
```

但是，OutputType 属性从 OutputType 特性获取其值，它报告该函数返回 **DateTime** 对象。

```powershell
(Get-Command Get-Time).OutputType
```

```Output
Name                                      Type
----                                      ----
System.DateTime                           System.DateTime
```

### <a name="example-4-a-function--that-shouldnt-have-output"></a>示例4：不应具有输出的函数

下面的示例演示了应执行和操作但不返回任何内容的自定义函数。

```powershell
function Invoke-Notepad
{
  [OutputType([System.Void])]
  Param ()
  & notepad.exe | Out-Null
}
```

## <a name="notes"></a>注释

**FunctionInfo** 对象的 OutputType 属性的值是 **PSTypeName** 对象的数组，其中每个对象都具有 Name 和 Type 属性。

若要仅获取每个输出类型的名称，请使用具有以下格式的命令。

```powershell
(Get-Command Get-Time).OutputType | ForEach {$_.Name}
```

OutputType 属性的值可以为 null。 当输出不是 .NET 类型（如 **WMI** 对象或对象的格式化视图）时，请使用 null 值。

## <a name="see-also"></a>另请参阅

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

