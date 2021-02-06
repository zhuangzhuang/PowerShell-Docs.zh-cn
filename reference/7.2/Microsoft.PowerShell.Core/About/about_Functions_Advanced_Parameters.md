---
description: 说明如何将参数添加到高级函数。
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Parameters
ms.openlocfilehash: da21f6fb7d19fa2ffcd9cd6c5eea217792937ae4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596208"
---
# <a name="about-functions-advanced-parameters"></a>关于函数高级参数

## <a name="short-description"></a>简短说明

说明如何将参数添加到高级函数。

## <a name="long-description"></a>长说明

你可以向你编写的高级函数添加参数，并使用参数特性和参数来限制函数用户使用参数提交的参数值。

除了 PowerShell 自动添加到所有 cmdlet 和高级函数的通用参数外，添加到函数的参数还可供用户使用。 有关 PowerShell 通用参数的详细信息，请参阅 [about_CommonParameters](about_CommonParameters.md)。

从 PowerShell 3.0 开始，可以将展开与结合使用 `@Args` 来表示命令中的参数。 展开在简单函数和高级函数中有效。 有关详细信息，请参阅 [about_Functions](about_Functions.md) 和 [about_Splatting](about_Splatting.md)。

## <a name="type-conversion-of-parameter-values"></a>参数值的类型转换

将字符串作为参数提供给需要不同类型的参数时，PowerShell 会将这些字符串隐式转换为参数目标类型。
高级函数执行参数值的区域性固定分析。

与此相反，在编译的 cmdlet 的参数绑定期间执行区分区域性的转换。

在此示例中，我们将创建一个 cmdlet 和一个带有参数的脚本函数 `[datetime]` 。 将当前区域性更改为使用德语设置。
德语格式的日期将传递给参数。

```powershell
# Create a cmdlet that accepts a [datetime] argument.
Add-Type @'
  using System;
  using System.Management.Automation;
  [Cmdlet("Get", "Date_Cmdlet")]
  public class GetFooCmdlet : Cmdlet {

    [Parameter(Position=0)]
    public DateTime Date { get; set; }

    protected override void ProcessRecord() {
      WriteObject(Date);
    }
  }
'@ -PassThru | % Assembly | Import-Module

[cultureinfo]::CurrentCulture = 'de-DE'
$dateStr = '19-06-2018'

Get-Date_Cmdlet $dateStr
```

```Output
Dienstag, 19. Juni 2018 00:00:00
```

如上所示，cmdlet 使用区分区域性的分析来转换字符串。

```powershell
# Define an equivalent function.
function Get-Date_Func {
  param(
    [DateTime] $Date
  )
  process {
    $Date
  }
}

[cultureinfo]::CurrentCulture = 'de-DE'

# This German-format date string doesn't work with the invariant culture.
# E.g., [datetime] '19-06-2018' breaks.
$dateStr = '19-06-2018'

Get-Date_Func $dateStr
```

高级函数使用区域性固定的分析，这会导致出现以下错误。

```Output
Get-Date_Func: Cannot process argument transformation on parameter 'Date'.
Cannot convert value "19-06-2018" to type "System.DateTime". Error: "String
'19-06-2018' was not recognized as a valid DateTime."
```

## <a name="static-parameters"></a>静态参数

静态参数是函数中始终可用的参数。
PowerShell cmdlet 和脚本中的大多数参数均为静态参数。

下面的示例演示具有以下特征的 **ComputerName** 参数的声明：

- 这是必需的)  (必需的。
- 它从管道中获取输入。
- 它采用字符串数组作为输入。

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

## <a name="attributes-of-parameters"></a>参数的特性

本节介绍可添加到函数参数的属性。

所有特性都是可选的。 但是，如果省略了 **CmdletBinding** 属性，则将其识别为高级函数时，该函数必须包括 **Parameter** 属性。

可以在每个参数声明中添加一个或多个属性。 可以添加到参数声明中的属性数没有限制。

### <a name="parameter-attribute"></a>参数属性

**参数** 属性用于声明函数参数的属性。

**参数** 属性是可选的，如果函数的参数均不需要属性，则可以省略此属性。 但是，若要被识别为高级函数而不是简单函数，函数必须有 **CmdletBinding** 特性或 **Parameter** 特性，或者两者都是。

**参数** 特性具有定义参数特征的参数，如参数是必需还是可选的。

使用以下语法声明 **参数** 属性、参数和参数值。 括住参数及其值的括号必须跟在不带空格的 **参数** 之后。

```powershell
Param(
    [Parameter(Argument=value)]
    $ParameterName
)
```

使用逗号分隔括号内的参数。 使用以下语法声明 **参数** 特性的两个参数。

```powershell
Param(
    [Parameter(Argument1=value1,
    Argument2=value2)]
)
```

**参数特性的** 布尔参数类型在从 **参数** 特性中省略时默认为 **False** 。 将参数值设置为 `$true` 或只按名称列出参数。 例如，以下 **参数** 属性是等效的。

```powershell
Param(
    [Parameter(Mandatory=$true)]
)

# Boolean arguments can be defined using this shorthand syntax

Param(
    [Parameter(Mandatory)]
)
```

如果使用不带参数的 **参数** 特性，作为使用 **CmdletBinding** 特性的替代方法，仍需使用特性名称后面的括号。

```powershell
Param(
    [Parameter()]
    $ParameterName
)
```

#### <a name="mandatory-argument"></a>必需参数

`Mandatory`参数指示参数是必需的。 如果未指定此参数，则该参数是可选的。

下面的示例声明 **ComputerName** 参数。 它使用 `Mandatory` 参数以使参数成为必需的。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="position-argument"></a>Position 参数

参数 `Position` 确定在命令中使用参数时，参数名是否是必需的。 如果参数声明包含 `Position` 参数，则可以省略参数名，并且 PowerShell 将通过命令中未命名的参数值列表中的位置或顺序来标识未命名的参数值。

如果 `Position` 未指定参数，则每次在命令中使用参数时，参数名称或参数名别名或缩写都必须在参数值之前。

默认情况下，所有函数参数都是位置。 PowerShell 将位置编号按参数在函数中的声明顺序分配给参数。 若要禁用此功能，请将 `PositionalBinding` **CmdletBinding** 属性的参数值设置为 `$False` 。 `Position`参数优先于 `PositionalBinding` **CmdletBinding** 属性的参数值。 有关详细信息，请 `PositionalBinding` 参阅 [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)中的。

参数的值 `Position` 指定为整数。 位置值 **0** 表示命令中的第一个位置，位置值 **1** 表示命令中的第二个位置，依此类推。

如果函数没有位置参数，则 PowerShell 会根据参数的声明顺序将位置分配给每个参数。
但是，最佳做法是不要依赖于此分配。 如果要将参数定位到位置，请使用 `Position` 参数。

下面的示例声明 **ComputerName** 参数。 它使用 `Position` 值为 **0** 的参数。 因此，当 `-ComputerName` 从命令中省略时，其值必须是命令中的第一个或唯一一个未命名的参数值。

```powershell
Param(
    [Parameter(Position=0)]
    [String[]]
    $ComputerName
)
```

#### <a name="parametersetname-argument"></a>ParameterSetName 参数

`ParameterSetName`参数指定参数所属的参数集。 如果未指定参数集，则参数属于函数定义的所有参数集。 因此，若要为唯一，每个参数集必须至少具有一个不是任何其他参数集成员的参数。

> [!NOTE]
> 对于 cmdlet 或函数，有32个参数集的限制。

下面的示例在 `Computer` 参数集、参数集中的 **用户名** 参数以及 `User` 这两个参数集中的 **Summary** 参数中声明了 ComputerName 参数。

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false)]
    [Switch]
    $Summary
)
```

只能在 `ParameterSetName` 每个参数中指定一个值， `ParameterSetName` 每个 **参数** 特性中只能指定一个参数。 若要指示参数出现在多个参数集中，请添加其他 **参数** 属性。

下面的示例将 **Summary** 参数显式添加到 `Computer` 和 `User` 参数集。 **Summary** 参数在参数集中是可选的 `Computer` ，并且在参数集中是必需的 `User` 。

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false, ParameterSetName="Computer")]
    [Parameter(Mandatory=$true, ParameterSetName="User")]
    [Switch]
    $Summary
)
```

有关参数集的详细信息，请参阅 [关于参数集](about_parameter_sets.md)。

#### <a name="valuefrompipeline-argument"></a>ValueFromPipeline 参数

`ValueFromPipeline`参数指示参数接受来自管道对象的输入。 如果函数接受整个对象，而不只是对象的属性，则指定此参数。

下面的示例声明一个必需的 **ComputerName** 参数，并接受从管道传递到函数的对象。

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="valuefrompipelinebypropertyname-argument"></a>ValueFromPipelineByPropertyName 参数

`ValueFromPipelineByPropertyName`参数指示参数接受管道对象的属性输入。 对象属性必须与参数具有相同的名称或别名。

例如，如果该函数具有 **computername** 参数，且该管道对象具有 **computername** 属性，则 **computername** 属性的值将分配给该函数的 **computername** 参数。

下面的示例声明一个必需的 **ComputerName** 参数，并接受通过管道传递给函数的对象 **computername** 属性中的输入。

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipelineByPropertyName=$true)]
    [String[]]
    $ComputerName
)
```

> [!NOTE]
> 一个类型化参数，该参数接受管道输入 (`by Value`) 或 (`by PropertyName`) 允许在参数上使用 _延迟绑定_ 脚本块。
>
> _延迟绑定_ 脚本块在 **ParameterBinding** 期间自动运行。 结果绑定到参数。 延迟绑定对于定义为类型或的参数不起作用 `ScriptBlock` `System.Object` 。 _不_ 调用脚本块。
>
> 可在此处阅读有关 _延迟绑定_ 脚本块的 [about_Script_Blocks。](about_Script_Blocks.md)

#### <a name="valuefromremainingarguments-argument"></a>ValueFromRemainingArguments 参数

`ValueFromRemainingArguments`参数指示参数接受命令中的所有参数值，这些值未分配给函数的其他参数。

下面的示例声明一个 **值** 参数，该参数是必需的， **另** 一个参数接受提交给函数的所有剩余参数值。

```powershell
function Test-Remainder
{
     param(
         [string]
         [Parameter(Mandatory = $true, Position=0)]
         $Value,
         [string[]]
         [Parameter(Position=1, ValueFromRemainingArguments)]
         $Remaining)
     "Found $($Remaining.Count) elements"
     for ($i = 0; $i -lt $Remaining.Count; $i++)
     {
        "${i}: $($Remaining[$i])"
     }
}
Test-Remainder first one,two
```

```Output
Found 2 elements
0: one
1: two
```

> [!NOTE]
> 在 PowerShell 6.2 之前， **ValueFromRemainingArguments** 集合作为索引 **0** 下的单个实体加入。

#### <a name="helpmessage-argument"></a>HelpMessage 参数

`HelpMessage`参数指定一个字符串，其中包含参数或其值的简短说明。 当命令中缺少必需的参数值时，PowerShell 将在出现的提示中显示此消息。 此参数对可选参数无效。

下面的示例声明一个必需的 **ComputerName** 参数和一个帮助消息，用于说明所需的参数值。

如果函数没有其他 [基于注释的帮助](./about_comment_based_help.md) 语法 (例如， `.SYNOPSIS`) 则此消息也会显示在 `Get-Help` 输出中。

```powershell
Param(
    [Parameter(Mandatory=$true,
    HelpMessage="Enter one or more computer names separated by commas.")]
    [String[]]
    $ComputerName
)
```

### <a name="alias-attribute"></a>Alias 特性

**Alias** 属性为参数建立替换名称。
可以分配给参数的别名数量没有限制。

下面的示例演示了一个参数声明，该声明将 **CN** 和 **MachineName** 别名添加到必需的 **ComputerName** 参数。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [Alias("CN","MachineName")]
    [String[]]
    $ComputerName
)
```

### <a name="supportswildcards-attribute"></a>SupportsWildcards 特性

**SupportsWildcards** 特性用于指示参数接受通配符值。 下面的示例演示了支持通配符值的强制 **路径** 参数的参数声明。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [SupportsWildcards()]
    [String[]]
    $Path
)
```

使用此属性不会自动启用通配符支持。 Cmdlet 开发人员必须实现代码来处理通配符输入。 支持的通配符可能因基础 API 或 PowerShell 提供程序而异。 有关详细信息，请参阅 [about_Wildcards](about_Wildcards.md)。

### <a name="parameter-and-variable-validation-attributes"></a>参数和变量验证特性

验证特性直接 PowerShell 用于测试用户在调用 advanced 函数时提交的参数值。 如果参数值未通过测试，则会生成错误，并且不会调用函数。 参数验证仅适用于所提供的输入，并且不会验证任何其他值（如默认值）。

你还可以使用验证属性来限制用户可以为变量指定的值。 将类型转换器与验证特性一起使用时，必须在特性之前定义类型转换器。

```powershell
[int32][AllowNull()] $number = 7
```

### <a name="allownull-validation-attribute"></a>AllowNull 验证特性

**AllowNull** 属性允许必需参数的值为 `$null` 。 下面的示例声明一个可以具有 **null** 值的哈希表 **ComputerInfo** 参数。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowNull()]
    [hashtable]
    $ComputerInfo
)
```

> [!NOTE]
> 如果类型转换器设置为 string，则 **AllowNull** 属性不起作用，因为字符串类型不接受 null 值。 对于此方案，可以使用 **AllowEmptyString** 属性。

### <a name="allowemptystring-validation-attribute"></a>AllowEmptyString 验证特性

**AllowEmptyString** 属性允许必需参数的值为 () 的空字符串 `""` 。 下面的示例声明一个可以具有空字符串值的 **ComputerName** 参数。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyString()]
    [String]
    $ComputerName
)
```

### <a name="allowemptycollection-validation-attribute"></a>AllowEmptyCollection 验证特性

**AllowEmptyCollection** 属性允许必需参数的值为空集合 `@()` 。 下面的示例声明一个可以具有空集合值的 **ComputerName** 参数。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyCollection()]
    [String[]]
    $ComputerName
)
```

### <a name="validatecount-validation-attribute"></a>ValidateCount 验证特性

**ValidateCount** 属性指定参数接受的参数值的最小值和最大数目。 如果调用函数的命令中的参数值数目不在此范围内，则 PowerShell 会生成错误。

以下参数声明创建一个 **ComputerName** 参数，该参数采用一个到五个参数值。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateCount(1,5)]
    [String[]]
    $ComputerName
)
```

### <a name="validatelength-validation-attribute"></a>ValidateLength 验证特性

**ValidateLength** 属性指定参数或变量值中的最小和最大字符数。 如果为参数或变量指定的值的长度超出范围，则 PowerShell 会生成错误。

在下面的示例中，每个计算机名必须包含一到十个字符。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateLength(1,10)]
    [String[]]
    $ComputerName
)
```

在下面的示例中，变量的值的 `$number` 长度必须至少为1个字符，最多只能有10个字符。

```powershell
[Int32][ValidateLength(1,10)]$number = '01'
```

> [!NOTE]
> 在此示例中，的值 `01` 以单引号括起来。 **ValidateLength** 属性不接受数字，而不会将其包装在引号内。

### <a name="validatepattern-validation-attribute"></a>ValidatePattern 验证特性

**ValidatePattern** 属性指定与参数或变量值进行比较的正则表达式。 如果值与正则表达式模式不匹配，则 PowerShell 会生成错误。

在下面的示例中，参数值必须包含一个四位数字，并且每个数字必须是从0到9的数字。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [String[]]
    $ComputerName
)
```

在下面的示例中，变量的值 `$number` 必须是一个四位数字，并且每个数字必须是从0到9的数字。

```powershell
[Int32][ValidatePattern("^[0-9][0-9][0-9][0-9]$")]$number = 1111
```

### <a name="validaterange-validation-attribute"></a>ValidateRange 验证特性

**ValidateRange** 属性为每个参数或变量值指定一个数值范围或 **ValidateRangeKind** 枚举值。
如果任何值超出此范围，则 PowerShell 会生成错误。

**ValidateRangeKind** 枚举允许以下值：

- **正数** -大于零的数字。
- **负数** -小于零的数字。
- **NonPositive** -小于或等于零的数字。
- 非 **负**-大于或等于零的数字。

在下面的示例中，" **尝试** " 参数的值必须介于0和10之间。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateRange(0,10)]
    [Int]
    $Attempts
)
```

在下面的示例中，变量的值 `$number` 必须介于0和10之间。

```powershell
[Int32][ValidateRange(0,10)]$number = 5
```

在下面的示例中，变量的值 `$number` 必须大于零。

```powershell
[Int32][ValidateRange("Positive")]$number = 1
```

### <a name="validatescript-validation-attribute"></a>ValidateScript 验证特性

**ValidateScript** 属性指定用于验证参数或变量值的脚本。 PowerShell 将值传递给脚本，如果脚本返回 `$false` 或脚本引发异常，则会生成错误。

使用 **ValidateScript** 属性时，所验证的值将映射到 `$_` 变量。 您可以使用 `$_` 变量来引用脚本中的值。

在下面的示例中， **EventDate** 参数的值必须大于或等于当前日期。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateScript({$_ -ge (Get-Date)})]
    [DateTime]
    $EventDate
)
```

在下面的示例中，变量的值 `$date` 必须大于或等于当前日期和时间。

```powershell
[DateTime][ValidateScript({$_ -ge (Get-Date)})]$date = (Get-Date)
```

> [!NOTE]
> 如果使用 **ValidateScript**，则不能将 `$null` 值传递给参数。 传递 null 值时， **ValidateScript** 无法验证参数。

### <a name="validateset-attribute"></a>ValidateSet 特性

**ValidateSet** 特性为参数或变量指定一组有效值，并启用 tab 自动补全。 如果参数或变量值与集中的值不匹配，则 PowerShell 会生成错误。 在下面的示例中， **Detail** 参数的值只能是 Low、Average 或 High。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateSet("Low", "Average", "High")]
    [String[]]
    $Detail
)
```

在下面的示例中，变量的值 `$flavor` 必须是巧克力、草莓或 Vanilla。

```powershell
[ValidateSet("Chocolate", "Strawberry", "Vanilla")]
[String]$flavor = "Strawberry"
```

只要在脚本内分配了该变量，就会进行验证。 例如，以下错误会导致运行时错误：

```powershell
Param(
    [ValidateSet("hello", "world")]
    [String]$Message
)

$Message = "bye"
```

#### <a name="dynamic-validateset-values"></a>动态 validateSet 值

可以使用 **类** 在运行时动态生成 **ValidateSet** 的值。 在下面的示例中，变量的有效值 `$Sound` 是通过名为 **SoundNames** 的 **类** 生成的，它检查三个可用声音文件的文件系统路径：

```powershell
Class SoundNames : System.Management.Automation.IValidateSetValuesGenerator {
    [String[]] GetValidValues() {
        $SoundPaths = '/System/Library/Sounds/',
            '/Library/Sounds','~/Library/Sounds'
        $SoundNames = ForEach ($SoundPath in $SoundPaths) {
            If (Test-Path $SoundPath) {
                (Get-ChildItem $SoundPath).BaseName
            }
        }
        return [String[]] $SoundNames
    }
}
```

然后，将 `[SoundNames]` 类实现为动态 **ValidateSet** 值，如下所示：

```powershell
Param(
    [ValidateSet([SoundNames])]
    [String]$Sound
)
```

### <a name="validatenotnull-validation-attribute"></a>ValidateNotNull 验证特性

**ValidateNotNull** 特性指定参数值不能为 `$null` 。 如果参数值为，则 PowerShell 会生成错误 `$null` 。

当参数为可选且类型为 undefined 或具有不能隐式转换 null 值（如 **对象**）的类型转换器时，将使用 **ValidateNotNull** 特性。 如果指定一个将隐式转换为 null 值（如 **字符串**）的类型，则即使使用 **ValidateNotNull** 属性，也会将空值转换为空字符串。 对于此方案，请使用 **ValidateNotNullOrEmpty**

在下面的示例中， **ID** 参数的值不能为 `$null` 。

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [ValidateNotNull()]
    $ID
)
```

### <a name="validatenotnullorempty-validation-attribute"></a>ValidateNotNullOrEmpty 验证特性

**ValidateNotNullOrEmpty** 属性指定 () 参数值不能为 `$null` 空字符串，也不能为空字符串 `""` 。 如果在函数调用中使用参数，但其值为 `$null` 、空字符串 (`""`) 或空数组，则 PowerShell 会生成错误 `@()` 。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateNotNullOrEmpty()]
    [String[]]
    $UserName
)
```

### <a name="validatedrive-validation-attribute"></a>ValidateDrive 验证特性

**ValidateDrive** 属性指定参数值必须代表路径，该路径仅引用允许的驱动器。 如果参数值是指除 "允许" 之外的驱动器，则 PowerShell 会生成错误。 存在路径（驱动器本身除外），则不会进行验证。

如果使用相对路径，则当前驱动器必须位于允许的驱动器列表中。

```powershell
Param(
    [ValidateDrive("C", "D", "Variable", "Function")]
    [String]$Path
)
```

### <a name="validateuserdrive-validation-attribute"></a>ValidateUserDrive 验证特性

**ValidateUserDrive** 属性指定参数值必须表示引用驱动器的路径 `User` 。 如果路径引用其他驱动器，则 PowerShell 会生成错误。 验证特性仅测试路径的驱动器部分是否存在。

如果使用相对路径，则当前驱动器必须是 `User` 。

```powershell
function Test-UserDrivePath{
    [OutputType([bool])]
    Param(
      [Parameter(Mandatory=, Position=0)][ValidateUserDrive()][String]$Path
      )
    $True
}

Test-UserDrivePath -Path C:\
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. The path
argument drive C does not belong to the set of approved drives: User.
Supply a path argument with an approved drive.
```

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. Cannot
find drive. A drive with the name 'User' does not exist.
```

`User`只需 (JEA) 会话配置中的管理即可定义驱动器。 在此示例中，我们创建了 User：驱动器。

```powershell
New-PSDrive -Name 'User' -PSProvider FileSystem -Root $env:HOMEPATH
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
User               75.76         24.24 FileSystem    C:\Users\ExampleUser

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
True
```

### <a name="validatetrusteddata-validation-attribute"></a>ValidateTrustedData 验证特性

此属性是在 PowerShell 6.1.1 中添加的。

此时，属性由 PowerShell 本身在内部使用，不用于外部使用。

## <a name="dynamic-parameters"></a>动态参数

动态参数是仅在特定条件下可用的 cmdlet、函数或脚本的参数。

例如，多个提供程序 cmdlet 的参数仅在提供程序驱动器中使用 cmdlet 时，或在提供程序驱动器的特定路径中可用。 例如，  `Add-Content` `Get-Content` `Set-Content` 仅当在文件系统驱动器中使用编码参数时，才在、和 cmdlet 上使用该参数。

你还可以创建一个参数，该参数仅在函数命令中使用另一个参数或其他参数具有特定值时显示。

动态参数非常有用，但仅在必要时才使用，因为它们可能会很难发现用户。 若要查找动态参数，用户必须在提供程序路径中，使用 cmdlet 的 **ArgumentList** 参数 `Get-Command` ，或使用的 **path** 参数 `Get-Help` 。

若要为函数或脚本创建动态参数，请使用 `DynamicParam` 关键字。

语法如下：

`DynamicParam {<statement-list>}`

在语句列表中，使用 `If` 语句指定参数在函数中可用的条件。

使用 `New-Object` cmdlet 创建一个 **RuntimeDefinedParameter** 对象，用于表示参数并指定其名称。

您可以使用 `New-Object` 命令创建 **ParameterAttribute** 对象来表示参数的属性，例如 **必需**、 **位置** 或 **ValueFromPipeline** 或其参数集。。

下面的示例演示了一个示例函数，其中包含名为 **Name** 和 **Path** 的标准参数，以及一个名为 **sjc-dp1** 的可选动态参数。 **Sjc-dp1** 参数在 `PSet1` 参数集中，并且具有类型 `Int32` 。
**Sjc-dp1** 参数 `Get-Sample` 仅在 **Path** 参数的值以开头时才在函数中提供 `HKLM:` ，指示它正在 `HKEY_LOCAL_MACHINE` 注册表驱动器中使用。

```powershell
function Get-Sample {
  [CmdletBinding()]
  Param([String]$Name, [String]$Path)

  DynamicParam
  {
    if ($Path.StartsWith("HKLM:"))
    {
      $attributes = New-Object -Type `
        System.Management.Automation.ParameterAttribute
      $attributes.ParameterSetName = "PSet1"
      $attributes.Mandatory = $false
      $attributeCollection = New-Object `
        -Type System.Collections.ObjectModel.Collection[System.Attribute]
      $attributeCollection.Add($attributes)

      $dynParam1 = New-Object -Type `
        System.Management.Automation.RuntimeDefinedParameter("DP1", [Int32],
          $attributeCollection)

      $paramDictionary = New-Object `
        -Type System.Management.Automation.RuntimeDefinedParameterDictionary
      $paramDictionary.Add("DP1", $dynParam1)
      return $paramDictionary
    }
  }
}
```

有关详细信息，请参阅 [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter)。

## <a name="switch-parameters"></a>开关参数

开关参数是没有参数值的参数。 它们只有在使用时才有效，只具有一个效果。

例如， **powershell.exe** 的 **NoProfile** 参数是一个开关参数。

若要在函数中创建开关参数，请 `Switch` 在参数定义中指定类型。

例如：

```powershell
Param([Switch]<ParameterName>)
```

或者，您可以使用另一种方法：

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [Switch]
    $<ParameterName>
)
```

开关参数易于使用，并且优先于具有更难语法的布尔参数。

例如，若要使用开关参数，用户需要在命令中键入参数。

`-IncludeAll`

若要使用布尔参数，用户需要键入参数和布尔值。

`-IncludeAll:$true`

创建开关参数时，请仔细选择参数名称。 请确保参数名称将参数的效果传达给用户。
避免使用不明确的术语，如 " **筛选器** " 或 " **最大** 值"。

## <a name="argumentcompleter-attribute"></a>ArgumentCompleter 特性

**ArgumentCompleter** 属性允许您向特定参数添加制表符完成值。 必须为需要 tab 自动补全的每个参数定义 **ArgumentCompleter** 属性。 类似于 **get-dynamicparameters**，当用户在参数名称后面按 <kbd>Tab 键</kbd> 时，可用值会在运行时计算。

若要添加 **ArgumentCompleter** 属性，需要定义一个确定值的脚本块。 脚本块必须按下面指定的顺序采用以下参数。 参数的名称并不重要，因为按位置提供了这些值。

语法如下：

```powershell
Param(
    [Parameter(Mandatory)]
    [ArgumentCompleter({
        param ( $commandName,
                $parameterName,
                $wordToComplete,
                $commandAst,
                $fakeBoundParameters )
        # Perform calculation of tab completed values here.
    })]
)
```

### <a name="argumentcompleter-script-block"></a>ArgumentCompleter 脚本块

脚本块参数设置为以下值：

- `$commandName` (位置 0) -此参数设置为脚本块为其提供 tab 自动补全的命令的名称。
- `$parameterName` (位置 1) -此参数设置为其值需要 tab 自动补全的参数。
- `$wordToComplete` (位置 2) -此参数设置为用户在按 <kbd>Tab 键</kbd>之前提供的值。脚本块应使用此值来确定 tab 填写值。
- `$commandAst` (位置 3) -此参数设置为当前输入行 (AST) 的抽象语法树。 有关详细信息，请参阅 [Ast 类](/dotnet/api/system.management.automation.language.ast)。
- `$fakeBoundParameters` (位置 4) - `$PSBoundParameters` 在用户按 <kbd>Tab</kbd>之前，此参数设置为包含 cmdlet 的的哈希表。有关详细信息，请参阅 [about_Automatic_Variables](about_Automatic_Variables.md)。

**ArgumentCompleter** 脚本块必须使用管道（例如 `ForEach-Object` 、 `Where-Object` ）或其他合适的方法展开值。
返回值数组将导致 PowerShell 将整个数组视为 **一个** 制表符完成值。

下面的示例将 tab 自动补全添加到 **值** 参数。 如果只指定 **值** 参数，则显示 **值** 的所有可能的值或参数。 指定 **类型** 参数时， **Value** 参数只显示该类型的可能值。

此外， `-like` 运算符确保如果用户键入以下命令并使用 <kbd>Tab</kbd> 自动补全，则仅返回 **Apple** 。

`Test-ArgumentCompleter -Type Fruits -Value A`

```powershell
function Test-ArgumentCompleter {
[CmdletBinding()]
 param (
        [Parameter(Mandatory=$true)]
        [ValidateSet('Fruits', 'Vegetables')]
        $Type,
        [Parameter(Mandatory=$true)]
        [ArgumentCompleter( {
            param ( $commandName,
                    $parameterName,
                    $wordToComplete,
                    $commandAst,
                    $fakeBoundParameters )

            $possibleValues = @{
                Fruits = @('Apple', 'Orange', 'Banana')
                Vegetables = @('Tomato', 'Squash', 'Corn')
            }
            if ($fakeBoundParameters.ContainsKey('Type'))
            {
                $possibleValues[$fakeBoundParameters.Type] | Where-Object {
                    $_ -like "$wordToComplete*"
                }
            }
            else
            {
                $possibleValues.Values | ForEach-Object {$_}
            }
        } )]
        $Value
      )
}
```

## <a name="see-also"></a>请参阅

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)
