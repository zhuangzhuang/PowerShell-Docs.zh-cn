---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-modulemanifest?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ModuleManifest
ms.openlocfilehash: c86a7253335b91011d2eb225bc53d1c5cc671aff
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597441"
---
# Test-ModuleManifest

## 摘要
验证模块清单文件是否准确描述了模块的内容。

## SYNTAX

```
Test-ModuleManifest [-Path] <String> [<CommonParameters>]
```

## DESCRIPTION

**New-modulemanifest** cmdlet 验证模块清单中列出的文件 () 文件实际上是否位于指定的路径中。

此 cmdlet 旨在帮助模块作者测试其清单文件。
模块用户还可以在脚本和命令中使用此 cmdlet 来检测错误，然后再运行依赖于该模块的脚本。

**New-modulemanifest** 返回表示模块的对象。
这是 Get-Module 返回的相同类型的对象。
如果有任何文件在清单中指定的位置上不存在，则该 cmdlet 还将针对每个缺少的文件生成一个错误。

## 示例

### 示例1：测试清单

```powershell
test-ModuleManifest -Path "$pshome\Modules\TestModule.psd1"
```

此命令将测试 TestModule.psd1 模块清单。

### 示例2：使用管道测试清单

```powershell
"$pshome\Modules\TestModule.psd1" | test-modulemanifest
```

```Output
Test-ModuleManifest : The specified type data file 'C:\Windows\System32\Wi
ndowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml' could not be processed because the file was not found. Please correct the path and try again.
At line:1 char:34
+ "$pshome\Modules\TestModule.psd1" | test-modulemanifest <<<<
+ CategoryInfo          : ResourceUnavailable: (C:\Windows\System32\WindowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml:String) [Test-ModuleManifest], FileNotFoundException
+ FullyQualifiedErrorId : Modules_TypeDataFileNotFound,Microsoft.PowerShell.Commands.TestModuleManifestCommandName

Name              : TestModule
Path              : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule\TestModule.psd1
Description       :
Guid              : 6f0f1387-cd25-4902-b7b4-22cff6aefa7b
Version           : 1.0
ModuleBase        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule
ModuleType        : Manifest
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {}
ExportedVariables : {}
NestedModules     : {}
```

此命令使用管道运算符 (|) 将路径字符串发送到 **new-modulemanifest**。

命令输出显示测试未通过，因为找不到清单中所列出的 TestTypes.ps1xml 文件。

### 示例3：编写用于测试模块清单的函数

```powershell
function Test-ManifestBool ($path)
```

```Output
{$a = dir $path | Test-ModuleManifest -ErrorAction SilentlyContinue; $?}
```

此函数类似于 **new-modulemanifest**，但它返回一个布尔值。
如果清单已通过测试 $False，则函数返回 $True; 否则返回。

该函数使用 Get-ChildItem cmdlet alias = dir 来获取由 $path 变量指定的模块清单。
该命令使用管道运算符 (|) 将文件对象传递给 **new-modulemanifest**。

**New-modulemanifest** 使用值为 SilentlyContinue 的 *ErrorAction* 通用参数来禁止显示该命令生成的任何错误。
它还会保存 **new-modulemanifest** 在 $a 变量中返回的 **PSModuleInfo** 对象。
因此，不会显示该对象。

然后，在单独的命令中，该函数显示 $？
自动变量。
如果上面的命令未生成错误，则该命令将显示 $True，否则 $False。

您可以在条件语句中使用此函数，例如可能位于 **import-module** 命令或使用模块的命令之前的语句。

## PARAMETERS

### -Path

指定清单文件的路径和文件名。
输入包含 psd1 文件扩展名的模块清单文件的可选路径和名称。
默认位置为当前目录。
支持通配符，但必须将其解析为单个模块清单文件。
此参数是必需的。
还可以通过管道将路径传递给 **new-modulemanifest**。

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

可以通过管道将模块清单的路径传递给此 cmdlet。

## 输出

### System.Management.Automation.PSModuleInfo

此 cmdlet 将返回表示模块的 **PSModuleInfo** 对象。
即使清单有错误，它也会返回此对象。

## 注释

## 相关链接

[Export-ModuleMember](Export-ModuleMember.md)

[Get-Module](Get-Module.md)

[Import-Module](Import-Module.md)

[New-Module](New-Module.md)

[New-ModuleManifest](New-ModuleManifest.md)

[Remove-Module](Remove-Module.md)

[about_Modules](About/about_Modules.md)

