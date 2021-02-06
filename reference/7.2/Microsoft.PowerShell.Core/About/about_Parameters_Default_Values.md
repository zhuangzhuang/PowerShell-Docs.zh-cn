---
description: 描述如何为 cmdlet 参数和高级函数设置自定义默认值。
Locale: en-US
ms.date: 05/31/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters_default_values?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters_Default_Values
ms.openlocfilehash: 102f163287717f7c9cd4f430704cc27ddea7ff4c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598086"
---
# <a name="about-parameters-default-values"></a>关于参数默认值

## <a name="short-description"></a>简短说明

描述如何为 cmdlet 参数和高级函数设置自定义默认值。

## <a name="long-description"></a>长说明

`$PSDefaultParameterValues`首选项变量使你能够为任何 cmdlet 或高级函数指定自定义默认值。 Cmdlet 和高级函数使用自定义默认值，除非在命令中指定另一个值。

Cmdlet 和高级函数的作者为其参数设置标准默认值。 通常，标准默认值非常有用，但它们可能不适用于所有环境。

当你在每次使用该命令时或者当某个特定参数值难以记住时，此功能特别有用，例如电子邮件服务器名称或项目 GUID。

如果所需的默认值因情况而异，则可以指定在不同条件下为参数提供不同默认值的脚本块。

`$PSDefaultParameterValues` 是在 PowerShell 3.0 中引入的。

## <a name="syntax"></a>语法

`$PSDefaultParameterValues`变量是一个哈希表，它将键的格式作为 **DefaultParameterDictionary** 的对象类型进行验证。 哈希表包含 **键/值** 对。 **键** 的格式为 `CmdletName:ParameterName` 。 **值** 是分配给该键的 **DefaultValue** 或 **ScriptBlock** 。

`$PSDefaultParameterValues`首选项变量的语法如下所示：

```
$PSDefaultParameterValues=@{"CmdletName:ParameterName"="DefaultValue"}

$PSDefaultParameterValues=@{ "CmdletName:ParameterName"={{ScriptBlock}} }

$PSDefaultParameterValues["Disabled"]=$True | $False
```

**CmdletName** 和 **ParameterName** 值中允许使用通配符。

若要从设置、更改、添加或删除特定的 **键/值** 对 `$PSDefaultParameterValues` ，请使用方法编辑标准哈希表。 例如，" **添加** " 和 " **移除** " 方法。 这些方法不会覆盖哈希表中的其他值。

还有另一个不覆盖现有 `$PSDefaultParameterValues` 哈希表的语法。 若要添加或更改特定的 **键/值** 对，请使用以下语法：

```
$PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

**CmdletName** 必须是 cmdlet 的名称或使用 **CmdletBinding** 属性的高级函数的名称。 不能使用 `$PSDefaultParameterValues` 来指定脚本或简单函数的默认值。

**DefaultValue** 可以是对象或脚本块。 如果值是脚本块，则 PowerShell 将计算脚本块，并将结果用作参数值。 当指定的参数接受脚本块值时，将脚本块值括在另一组大括号中，例如：

```powershell
$PSDefaultParameterValues=@{ "Invoke-Command:ScriptBlock"={{Get-Process}} }
```

有关详细信息，请参阅以下文档：

- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Script_Blocks](about_Script_Blocks.md)
- [about_Preference_Variables](about_Preference_Variables.md)

## <a name="examples"></a>示例

### <a name="how-to-set-psdefaultparametervalues"></a>如何设置 \$ PSDefaultParameterValues

`$PSDefaultParameterValues` 是一个首选项变量，因此它只存在于其设置的会话中。 它没有默认值。

若要设置 `$PSDefaultParameterValues` ，请键入变量名称以及一个或多个 **键/值** 对。 如果运行另一个 `$PSDefaultParameterValues` 命令，它将覆盖现有的哈希表。

有关如何更改 **键/值** 对而不覆盖现有哈希表值的示例，请参阅 [如何在 \$ PSDefaultParameterValues 中添加值](#how-to-add-values-to-psdefaultparametervalues) 或 [如何在 \$ PSDefaultParameterValues 中更改值](#how-to-change-values-in-psdefaultparametervalues)。

若要保存以 `$PSDefaultParameterValues` 供将来会话使用，请将 `$PSDefaultParameterValues` 命令添加到 PowerShell 配置文件。 有关详细信息，请参阅 [about_Profiles](about_Profiles.md)。

#### <a name="set-a-custom-default-value"></a>设置自定义默认值

**键/值** 对将密钥设置 `Send-MailMessage:SmtpServer` 为自定义默认值 **Server123**。

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
}
```

#### <a name="set-default-values-for-multiple-parameters"></a>为多个参数设置默认值

若要为多个参数设置默认值，请用分号分隔每个 **键/值** 对 (`;`) 。 `Send-MailMessage:SmtpServer`和 `Get-WinEvent:LogName` 键设置为自定义默认值。

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123";
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
}
```

#### <a name="use-wildcards-and-switch-parameters"></a>使用通配符和开关参数

Cmdlet 和参数名称可以包含通配符。 使用 `$True` 和 `$False` 设置开关参数的值，例如 " **详细**"。 对于所有命令，通用参数的 **Verbose** 参数均设置为 `$True` 。

```powershell
$PSDefaultParameterValues = @{"*:Verbose"=$True}
```

#### <a name="use-an-array-for-the-default-value"></a>使用数组作为默认值

如果参数可以接受多个值，则可以将多个值设置为默认值。 该键的默认值 `Invoke-Command:ComputerName` 设置为 **Server01** 和 **Server02** 的数组值。

```powershell
$PSDefaultParameterValues = @{
  "Invoke-Command:ComputerName"="Server01","Server02"
}
```

#### <a name="use-a-script-block"></a>使用脚本块

您可以使用脚本块在不同条件下为参数指定不同的默认值。 PowerShell 将计算脚本块，并将结果用作默认参数值。

`Format-Table:AutoSize`键将参数切换为默认值 **True**。 `If`语句包含的条件 `$host.Name` 必须是 PowerShell 控制台 **ConsoleHost**。

```powershell
$PSDefaultParameterValues=@{
  "Format-Table:AutoSize"={if ($host.Name -eq "ConsoleHost"){$True}}
}
```

如果参数接受脚本块值，请将脚本块括在一组额外的大括号中。 当 PowerShell 评估外部脚本块时，结果为内部脚本块，并设置为默认参数值。

`Invoke-Command:ScriptBlock`由于脚本块包含在另一组大括号中，因此设置为 **系统事件日志** 的默认值的键。 脚本块的结果传递给 `Invoke-Command` cmdlet。

```powershell
$PSDefaultParameterValues=@{
  "Invoke-Command:ScriptBlock"={{Get-EventLog -Log System}}
}
```

### <a name="how-to-get-psdefaultparametervalues"></a>如何获取 \$ PSDefaultParameterValues

通过在 PowerShell 提示符下输入来显示哈希表的值 `$PSDefaultParameterValues` 。

`$PSDefaultParameterValues`哈希表是使用三个 **键/值** 对设置的。
下面的示例使用此哈希表，其中介绍了如何添加、更改和删除中的值 `$PSDefaultParameterValues` 。

```
PS> $PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
  "Get-*:Verbose"=$True
}

PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

若要获取特定键的值 `CmdletName:ParameterName` ，请使用以下语法：

```
$PSDefaultParameterValues["CmdletName:ParameterName"]
```

例如，若要获取键的值，则为 `Send-MailMessage:SmtpServer` 。

```
PS> $PSDefaultParameterValues["Send-MailMessage:SmtpServer"]
Server123
```

### <a name="how-to-add-values-to-psdefaultparametervalues"></a>如何向 PSDefaultParameterValues 添加值 \$

若要向添加值 `$PSDefaultParameterValues` ，请使用 **add** 方法。 添加值并不会影响哈希表的现有值。

使用逗号 (`,`) 将 **键** 与 **值** 分隔开。 下面的语法演示如何对使用 **Add** 方法 `$PSDefaultParameterValues` 。

```
PS> $PSDefaultParameterValues.Add("CmdletName:ParameterName", "DefaultValue")
```

使用新的 **键/值** 对来更新在上一个示例中创建的哈希表。 **Add** 方法将密钥设置 `Get-Process:Name` 为值 **PowerShell**。

```powershell
$PSDefaultParameterValues.Add("Get-Process:Name", "PowerShell")
```

下面的语法实现相同的结果。

```powershell
$PSDefaultParameterValues["Get-Process:Name"]="PowerShell"
```

`$PSDefaultParameterValues`变量显示已更新的哈希表。 已 `Get-Process:Name` 添加密钥。

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-Process:Name               PowerShell
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-remove-values-from-psdefaultparametervalues"></a>如何从 PSDefaultParameterValues 中删除值 \$

若要从中删除值 `$PSDefaultParameterValues` ，请使用哈希表的 **remove** 方法。 删除值并不会影响哈希表的现有值。

下面的语法演示如何对使用 **Remove** 方法 `$PSDefaultParameterValues` 。

```
PS> $PSDefaultParameterValues.Remove("CmdletName:ParameterName")
```

在此示例中，将更新在上一个示例中创建的哈希表，以删除 **键/值** 对。 **Remove** 方法删除该 `Get-Process:Name` 密钥。

```powershell
$PSDefaultParameterValues.Remove("Get-Process:Name")
```

`$PSDefaultParameterValues`变量显示已更新的哈希表。 `Get-Process:Name`已删除该密钥。

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-change-values-in-psdefaultparametervalues"></a>如何更改 PSDefaultParameterValues 中的值 \$

对特定值所做的更改不会影响现有哈希表的值。 若要在中更改特定的 **键/值** 对 `$PSDefaultParameterValues` ，请使用以下语法：

```
PS> $PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

在此示例中，将更新在上一个示例中创建的哈希表以更改 **键/值** 对。 以下命令将键更改 `Send-MailMessage:SmtpServer` 为新值 **ServerXYZ**。

```powershell
$PSDefaultParameterValues["Send-MailMessage:SmtpServer"]="ServerXYZ"
```

`$PSDefaultParameterValues`变量显示已更新的哈希表。 `Send-MailMessage:SmtpServer`该键已更改为新值。

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

### <a name="how-to-disable-and-re-enable-psdefaultparametervalues"></a>如何禁用和重新启用 \$ PSDefaultParameterValues

你可以暂时禁用然后重新启用 `$PSDefaultParameterValues` 。
`$PSDefaultParameterValues`如果正在运行需要不同默认参数值的脚本，禁用会很有用。

若要禁用 `$PSDefaultParameterValues` ，请添加 `Disabled` 值为 **True** 的的键。 中的值 `$PSDefaultParameterValues` 将保留，但无效。

```
PS> $PSDefaultParameterValues.Add("Disabled", $True)
```

下面的语法实现相同的结果。

```
PS> $PSDefaultParameterValues["Disabled"]=$True
```

`$PSDefaultParameterValues`变量显示已更新的哈希表，其中包含键的值 `Disabled` 。

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       True
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

若要重新启用 `$PSDefaultParameterValues` ，请删除 **禁用** 的密钥，或将 **禁用** 的项的值更改为 `$False` 。 以前的值 `$PSDefaultParameterValues` 再次生效。

```
PS> $PSDefaultParameterValues.Remove("Disabled")
```

下面的语法实现相同的结果。

```
PS> $PSDefaultParameterValues["Disabled"]=$False
```

`$PSDefaultParameterValues`变量显示已更新的哈希表。 使用 **Remove** 方法时， `Disabled` 会从输出中删除该密钥。
如果使用了替代语法重新启用 `$PSDefaultParameterValues` ，则 `Disabled` 键显示为 **False**。

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       False
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

## <a name="see-also"></a>请参阅

[about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Script_Blocks](about_Script_Blocks.md)

