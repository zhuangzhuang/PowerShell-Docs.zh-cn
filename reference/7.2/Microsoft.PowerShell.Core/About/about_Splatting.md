---
description: 介绍如何使用展开在 PowerShell 中将参数传递给命令。
Locale: en-US
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_splatting?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Splatting
ms.openlocfilehash: e028f43828afd69d645591ab20795689cb115e12
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598706"
---
# <a name="about-splatting"></a>关于展开

## <a name="short-description"></a>简短说明

介绍如何使用展开在 PowerShell 中将参数传递给命令。

## <a name="long-description"></a>长说明

展开是将参数值集合作为一个单元传递到命令的方法。 PowerShell 会将集合中的每个值与命令参数相关联。 Splatted 参数值存储在名为展开的变量中，它们看起来像标准变量，但以 in 符号开头 (`@`) ，而不是 () 美元符号 `$` 。 At 符号通知 PowerShell 要传递值的集合，而不是传递单个值。

展开使你的命令更简单、更易于阅读。 可以在不同的命令调用中重复使用展开值，并使用展开将参数值从 `$PSBoundParameters` 自动变量传递到其他脚本和函数。

从 Windows PowerShell 3.0 开始，还可以使用展开来表示命令的所有参数。

## <a name="syntax"></a>语法

```
<CommandName> <optional parameters> @<HashTable> <optional parameters>
<CommandName> <optional parameters> @<Array> <optional parameters>
```

若要为位置参数提供参数值（在不需要参数名称的情况下），请使用数组语法。 若要提供参数名称和值对，请使用哈希表语法。 Splatted 值可以出现在参数列表中的任何位置。

当展开时，无需使用哈希表或数组传递所有参数。 可以通过使用展开传递某些参数，并通过位置或参数名称传递其他参数。 此外，你可以在单个命令中 splat 多个对象，因此不会为每个参数传递多个值。

在 PowerShell 7.1 中，可以通过在命令中显式定义参数来重写 splatted 参数。

## <a name="splatting-with-hash-tables"></a>具有哈希表的展开

使用哈希表 splat 参数名称和值对。 对于所有参数类型（包括位置参数和开关参数），都可以使用此格式。
必须按名称指定位置参数。

下面的示例比较两个 `Copy-Item` 命令，它们将 Test.txt 文件复制到相同目录中的 Test2.txt 文件。

第一个示例使用传统格式，其中包含参数名称。

```powershell
Copy-Item -Path "test.txt" -Destination "test2.txt" -WhatIf
```

第二个示例使用哈希表展开。 第一个命令创建参数名称和参数值对的哈希表，并将其存储在 `$HashArguments` 变量中。 第二个命令使用 `$HashArguments` 展开中的变量。 位于符号 (`@HashArguments`) 替换命令中的美元符号 (`$HashArguments`) 。

若要为 **WhatIf** 开关参数提供一个值，请使用 `$True` 或 `$False` 。

```powershell
$HashArguments = @{
  Path = "test.txt"
  Destination = "test2.txt"
  WhatIf = $true
}
Copy-Item @HashArguments
```

> [!NOTE]
> 在第一个命令中，At 符号 (`@`) 指示哈希表，而不是 splatted 值。 PowerShell 中的哈希表语法为： `@{<name>=<value>; <name>=<value>; ...}`

## <a name="splatting-with-arrays"></a>具有数组的展开

使用数组 splat 位置参数的值，不需要参数名称。 值必须在数组中的位置号顺序内。

下面的示例比较两个 `Copy-Item` 命令，它们将 Test.txt 文件复制到相同目录中的 Test2.txt 文件。

第一个示例使用省略了参数名称的传统格式。 参数值按位置顺序出现在命令中。

```powershell
Copy-Item "test.txt" "test2.txt" -WhatIf
```

第二个示例使用数组展开。 第一个命令创建参数值的数组，并将其存储在 `$ArrayArguments` 变量中。 值在数组中的位置顺序。 第二个命令在 `$ArrayArguments` 展开中的命令中使用该变量。 位于符号 (`@ArrayArguments`) 替换命令中的美元符号 (`$ArrayArguments`) 。

```powershell
$ArrayArguments = "test.txt", "test2.txt"
Copy-Item @ArrayArguments -WhatIf
```

### <a name="using-the-argumentlist-parameter"></a>使用 ArgumentList 参数

多个 cmdlet 具有 **ArgumentList** 参数，该参数用于将参数值传递到 cmdlet 执行的脚本块。 **ArgumentList** 参数采用传递到脚本块的值数组。 PowerShell 有效地使用数组展开将值绑定到脚本块的参数。 当使用 **ArgumentList** 时，如果需要将一个数组作为绑定到单个参数的单个对象传递，则必须将该数组包装为另一个数组的唯一元素。

下面的示例具有一个脚本块，该脚本块采用一个字符串数组的参数。

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
  } -ArgumentList $array
```
<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->
在此示例中，只将中的第一项 `$array` 传递到脚本块。

```Output
Hello
```

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
} -ArgumentList (,$array)
```

在此示例中， `$array` 包装在数组中，以便将整个数组作为单个对象传递到脚本块。

```Output
Hello World!
```

## <a name="examples"></a>示例

### <a name="example-1-reuse-splatted-parameters-in-different-commands"></a>示例1：在不同的命令中重复使用 splatted 参数

此示例演示如何在不同的命令中重复使用 splatted 值。 此示例中的命令使用 `Write-Host` cmdlet 将消息写入主机程序控制台。 它使用展开来指定前景色和背景色。

若要更改所有命令的颜色，只需更改变量的值 `$Colors` 。

第一个命令创建参数名称和值的哈希表，并将该哈希表存储在 `$Colors` 变量中。

```powershell
$Colors = @{ForegroundColor = "black"; BackgroundColor = "white"}
```

第二个和第三个命令 `$Colors` 在命令中使用展开的变量 `Write-Host` 。 若要使用 `$Colors variable` ，请将美元符号 (`$Colors`) 替换为符号 (`@Colors`) 。

```powershell
#Write a message with the colors in $Colors
Write-Host "This is a test." @Colors

#Write second message with same colors. The position of splatted
#hash table does not matter.
Write-Host @Colors "This is another test."
```

### <a name="example-2-forward-parameters-using-psboundparameters"></a>示例2：使用 $PSBoundParameters 转发参数

此示例显示了如何使用展开和自动变量将其参数转发到其他命令 `$PSBoundParameters` 。

`$PSBoundParameters`自动变量是 () 的字典对象，其中包含运行脚本或函数时使用的所有参数名称和值。

在下面的示例中，我们使用 `$PSBoundParameters` 变量将传递给脚本或函数的参数值转发给 `Test2` `Test1` 函数。 对函数的两个调用都 `Test1` `Test2` 使用展开。

```powershell
function Test1
{
    param($a, $b, $c)

    $a
    $b
    $c
}

function Test2
{
    param($a, $b, $c)

    #Call the Test1 function with $a, $b, and $c.
    Test1 @PsBoundParameters

    #Call the Test1 function with $b and $c, but not with $a
    $LimitedParameters = $PSBoundParameters
    $LimitedParameters.Remove("a") | Out-Null
    Test1 @LimitedParameters
}
```

```Output
Test2 -a 1 -b 2 -c 3
1
2
3
2
3
```

### <a name="example-3-override-splatted-parameters-with-explicitly-defined-parameters"></a>示例3：重写具有显式定义的参数的 splatted 参数

此示例演示如何使用显式定义的参数重写 splatted 参数。 当您不想生成新的哈希表或更改您用于 splat 的哈希表中的值时，这非常有用。

`$commonParams`变量存储用于在位置创建虚拟机的参数 `East US` 。 `$allVms`变量是要创建的虚拟机的列表。 我们循环遍历列表，并使用 `$commonParams` splat 参数来创建每个虚拟机。 但是，我们希望 `myVM2` 在不同于其他虚拟机的区域中创建。 `$commonParams`您可以在中显式定义 **Location** 参数，而不是调整哈希表， `New-AzVm` 以取代中的键的值 `Location` `$commonParams` 。

```powershell
$commonParams = @{
    ResourceGroupName = "myResourceGroup"
    Location = "East US"
    VirtualNetworkName = "myVnet"
    SubnetName = "mySubnet"
    SecurityGroupName = "myNetworkSecurityGroup"
    PublicIpAddressName = "myPublicIpAddress"
}

$allVms = @('myVM1','myVM2','myVM3',)

foreach ($vm in $allVms)
{
    if ($vm -eq 'myVM2')
    {
        New-AzVm @commonParams -Name $vm -Location "West US"
    }
    else
    {
        New-AzVm @commonParams -Name $vm
    }
}
```

## <a name="splatting-command-parameters"></a>展开命令参数

可以使用展开来表示命令的参数。 当你创建的是一个代理函数（即调用另一个命令的函数）时，此方法非常有用。 此功能是在 Windows PowerShell 3.0 中引入的。

若要 splat 命令的参数，请使用 `@Args` 表示命令参数。 此方法比枚举命令参数更简单，即使调用的命令的参数发生更改，它也无需进行修订。

此功能使用 `$Args` 自动变量，该变量包含所有未分配的参数值。

例如，以下函数调用 `Get-Process` cmdlet。 在此函数中， `@Args` 表示 cmdlet 的所有参数 `Get-Process` 。

```powershell
function Get-MyProcess { Get-Process @Args }
```

使用 `Get-MyProcess` 函数时，所有未分配的参数和参数值将传递到 `@Args` ，如以下命令中所示。

```powershell
Get-MyProcess -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    463      46   225484     237196   719    15.86   3228 powershell
```

```powershell
Get-MyProcess -Name PowerShell_Ise -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.2.9200.16384   6.2.9200.1638... C:\Windows\system32\WindowsPowerShell\...
```

可以 `@Args` 在具有显式声明的参数的函数中使用。 可以在函数中多次使用它，但输入的所有参数都将传递给的所有实例 `@Args` ，如下面的示例中所示。

```powershell
function Get-MyCommand
{
    Param ([switch]$P, [switch]$C)
    if ($P) { Get-Process @Args }
    if ($C) { Get-Command @Args }
}

Get-MyCommand -P -C -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
408      28    75568      83176   620     1.33   1692 powershell

Path               : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Extension          : .exe
Definition         : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Visibility         : Public
OutputType         : {System.String}
Name               : powershell.exe
CommandType        : Application
ModuleName         :
Module             :
RemotingCapability : PowerShell
Parameters         :
ParameterSets      :
HelpUri            :
FileVersionInfo    : File:             C:\Windows\System32\WindowsPowerShell
                     \v1.0\powershell.exe
                     InternalName:     POWERSHELL
                     OriginalFilename: PowerShell.EXE.MUI
                     FileVersion:      10.0.14393.0 (rs1_release.160715-1616
                     FileDescription:  Windows PowerShell
                     Product:          Microsoft Windows Operating System
                     ProductVersion:   10.0.14393.0
                     Debug:            False
                     Patched:          False
                     PreRelease:       False
                     PrivateBuild:     False
                     SpecialBuild:     False
                     Language:         English (United States)
```

## <a name="notes"></a>说明

如果使用 **CmdletBinding** 或 **参数** 特性使函数进入高级函数，则该 `$args` 函数中的自动变量将不再可用。 高级函数需要显式参数定义。

PowerShell 所需状态配置 (DSC) 设计为不使用展开。
不能使用展开将值传递给 DSC 资源。 有关详细信息，请参阅 Gael Colas 文章 [展开 DSC 资源](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/)。

## <a name="see-also"></a>请参阅

[about_Arrays](about_Arrays.md)

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Parameters](about_Parameters.md)
