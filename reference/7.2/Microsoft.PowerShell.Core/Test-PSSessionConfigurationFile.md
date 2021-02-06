---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-PSSessionConfigurationFile
ms.openlocfilehash: c6d6d305b283522215d43b7339683b1617a85804
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596036"
---
# Test-PSSessionConfigurationFile

## 摘要
验证会话配置文件中的键和值。

## SYNTAX

```
Test-PSSessionConfigurationFile [-Path] <String> [<CommonParameters>]
```

## DESCRIPTION

此 cmdlet 验证会话配置文件是否包含有效的密钥，以及这些值是否为正确的类型。 对于枚举值，该 cmdlet 将验证指定的值是否有效。

`$True`如果文件通过了所有测试，则该 cmdlet 将返回， `$False` 否则返回。 若要查找任何错误，请使用 **Verbose** 参数。

`Test-PSSessionConfigurationFile` 验证会话配置文件，如由 cmdlet 创建的文件 `New-PSSessionConfigurationFile` 。 有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。 有关会话配置文件的信息，请参阅 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。

此 cmdlet 是在 PowerShell 3.0 中引入的。

## 示例

### 示例1：测试会话配置文件

```powershell
Test-PSSessionConfigurationFile -Path "FullLanguage.pssc"
```

```Output
True
```

### 示例2：测试会话配置的会话配置文件

在此示例中，我们将测试 **受限** 会话配置中使用的配置文件。
**Path** 参数的值是 `Get-PSSessionConfiguration` 用于获取 **受限** 会话配置的命令的结果。 会话配置文件的路径存储在会话配置的 **ConfigFilePath** 属性的值中。

```powershell
Test-PSSessionConfigurationFile -Path (Get-PSSessionConfiguration -Name Restricted).ConfigFilePath
```

### 示例3：测试所有会话配置文件

此示例中的函数测试本地计算机上的所有会话配置文件。 函数使用 `Get-PSSessionConfiguration` cmdlet 获取所有会话配置。 循环内的代码 `ForEach-Object` 显示文件路径并测试每个会话配置。

```powershell
function Test-AllConfigFiles
{
    Get-PSSessionConfiguration | ForEach-Object {
        if ($_.ConfigFilePath) {
            $_.ConfigFilePath
            Test-PSSessionConfigurationFile -Verbose -Path $_.ConfigFilePath
        }
    }
}
Test-AllConfigFiles
```

```Output
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Empty_6fd77bf6-e084-4372-bd8a-af3e207354d3.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
VERBOSE: The member 'AliasDefinitions' must contain the required key 'Description'. Add the require key
to the fileC:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc.
False
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RestrictedLang_b6bd9474-0a6c-4e06-8722-c2c95bb10d3e.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RRS_3fb29420-2c87-46e5-a402-e21436331efc.pssc
True
```

会话配置的 **ConfigFilePath** 属性包含在会话配置中使用的会话配置文件的路径（如果有）。

如果填充了 **ConfigFilePath** 属性的值（该值为 true），则该命令将获取（打印）**ConfigFilePath** 属性值。 然后，它使用 `Test-PSSessionConfigurationFile` cmdlet 来测试 **ConfigFilePath** 值中的文件。 当文件无法通过测试时，**Verbose** 参数将返回文件错误。

## PARAMETERS

### -Path

指定会话配置文件的路径和文件名 ( .pssc) 。 如果省略该路径，则默认为当前文件夹。 支持通配符，但它们必须解析为单个文件。 还可以通过管道将会话配置文件路径传递给 `Test-PSSessionConfigurationFile` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

你可以通过管道将会话配置文件路径传递给 `Test-PSSessionConfigurationFile` 。

## 输出

### System.Boolean

## 注释

此 cmdlet 仅在 Windows 平台上可用。

## 相关链接

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 提供程序](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
