---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-clixml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Clixml
ms.openlocfilehash: 3658ea5eded0fed95a1c9a1ea6e7d84a557e1e36
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597071"
---
# Import-Clixml

## 摘要
导入 EXPORT-CLIXML 文件并在 PowerShell 中创建相应的对象。

## SYNTAX

### ByPath（默认值）

```
Import-Clixml [-Path] <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

### ByLiteralPath

```
Import-Clixml -LiteralPath <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

## DESCRIPTION

`Import-Clixml`Cmdlet (CLI) XML 文件导入公共语言基础结构，其中包含表示 Microsoft .NET 框架对象的数据，并创建 PowerShell 对象。 有关 CLI 的详细信息，请参阅 [语言独立性](/dotnet/standard/language-independence)。

Windows 计算机上的一个重要用途 `Import-Clixml` 是导入凭据，并使用作为安全 XML 导出的安全字符串 `Export-Clixml` 。 有关示例，请参见示例2。

`Import-Clixml` 使用字节顺序标记 (BOM) 来检测文件的编码格式。 如果文件没有 BOM，则假定编码为 UTF8。

## 示例

### 示例1：导入序列化的文件并重新创建对象

此示例使用 `Export-Clixml` cmdlet 保存返回的进程信息的序列化副本 `Get-Process` 。 `Import-Clixml` 检索序列化文件的内容，并重新创建存储在变量中的对象 `$Processes` 。

```powershell
Get-Process | Export-Clixml -Path .\pi.xml
$Processes = Import-Clixml -Path .\pi.xml
```

### 示例2：导入安全凭据对象

在此示例中，给定通过运行 cmdlet 存储在变量中的凭据 `$Credential` `Get-Credential` ，可以运行 `Export-Clixml` cmdlet 将凭据保存到磁盘。

> [!IMPORTANT]
> `Export-Clixml` 仅导出 Windows 上的加密凭据。 在非 Windows 操作系统（如 macOS 和 Linux）上，凭据以纯文本格式导出。

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

`Export-Clixml`Cmdlet 使用 Windows[数据保护 API](/previous-versions/windows/apps/hh464970(v=win.10))加密凭据对象。
加密可确保只有你的用户帐户才能解密 credential 对象的内容。 导出的 `CLIXML` 文件不能用于其他计算机或其他用户。

在此示例中，存储凭据的文件由表示 `TestScript.ps1.credential` 。 将 **TestScript** 替换为要在其中加载凭据的脚本的名称。

将凭据对象向下发送到管道 `Export-Clixml` ，并将其保存到在 `$Credxmlpath` 第一个命令中指定的路径。

若要将凭据自动导入脚本，请运行最后两个命令。 运行 `Import-Clixml` 将受保护的凭据对象导入脚本。 此导入消除了在脚本中公开纯文本密码的风险。

## PARAMETERS

### -第一个

只获取指定数量的对象。 输入要获取的对象数量。

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeTotalCount

报告数据集中的对象总数，后跟所选对象。 如果该 cmdlet 无法确定总计数，则会显示 **未知的总计数**。 整数具有一个 **准确性** 属性，该属性指示总计值的可靠性。 **准确性** 的值范围从 `0.0` 到到 `1.0` ， `0.0` 表示该 cmdlet 无法对对象进行计数，这 `1.0` 意味着该计数是精确的，介于和之间的值 `0.0` `1.0` 表示越来越可靠的估计值。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

指定 XML 文件的路径。 与 **Path** 不同， **LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定 XML 文件的路径。

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Skip

忽略指定数量的对象，然后获取其余对象。 输入要跳过的对象数量。

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将包含路径的字符串进行管道 `Import-Clixml` 。

## 输出

### PSObject

`Import-Clixml` 返回从存储的 XML 文件反序列化的对象。

## 注释

为一个参数指定多个值时，请使用逗号分隔这些值。 例如，`<parameter-name> <value1>, <value2>`。

## 相关链接

[Export-Clixml](Export-Clixml.md)

[XML 序列化简介](/dotnet/standard/serialization/introducing-xml-serialization)

[Join-Path](../Microsoft.PowerShell.Management/Join-Path.md)

[Securely Store Credentials on Disk](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)（将凭据安全存储到磁盘）

[Use PowerShell to Pass Credentials to Legacy Systems](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)（使用 PowerShell 将凭据传递到旧系统）

