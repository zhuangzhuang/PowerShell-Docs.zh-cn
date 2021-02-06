---
description: 说明语言模式及其对 PowerShell 会话的影响。
Locale: en-US
ms.date: 09/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_modes?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Modes
ms.openlocfilehash: 9e4b1ec2dd16d3442c553460ff217e7e0223f41f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595386"
---
# <a name="about-language-modes"></a>关于语言模式

## <a name="short-description"></a>简短说明
说明语言模式及其对 PowerShell 会话的影响。

## <a name="long-description"></a>详细说明

PowerShell 会话的语言模式确定可以在会话中使用 PowerShell 语言的哪些元素。

PowerShell 支持以下语言模式：

- FullLanguage
- PowerShell 3.0) 中引入的 ConstrainedLanguage (
- RestrictedLanguage
- NoLanguage

### <a name="what-is-a-language-mode"></a>什么是语言模式？

语言模式决定了会话中允许使用的语言元素。

语言模式实际上是会话配置的属性 (或用于创建会话的 "终结点" ) 。 使用特定会话配置的所有会话都具有会话配置的语言模式。

所有 PowerShell 会话都具有一种语言模式，其中包括使用 cmdlet 创建的 Pssession `New-PSSession` 、使用 ComputerName 参数的临时会话以及启动 PowerShell 时显示的默认会话。

远程会话是使用远程计算机上的会话配置创建的。 会话配置中设置的语言模式确定会话的语言模式。 若要指定 PSSession 的会话配置，请使用创建会话的 cmdlet 的 ConfigurationName 参数。

### <a name="language-modes"></a>语言模式

本部分介绍 PowerShell 会话中的语言模式。

#### <a name="full-language-fulllanguage"></a>完整语言 (FullLanguage) 

FullLanguage 模式允许会话中的所有语言元素。
FullLanguage 是所有 Windows 版本（Windows RT 除外）上默认会话的默认语言模式。

#### <a name="restricted-language-restrictedlanguage"></a>受限语言 (RestrictedLanguage) 

在 RestrictedLanguage 模式下，用户可以运行 (cmdlet、函数、CIM 命令和工作流的命令) 但不允许使用脚本块。

默认情况下，在 RestrictedLanguage 模式下仅允许使用以下变量：

- `$PSCulture`
- `$PSUICulture`
- `$True`
- `$False`
- `$Null`

使用 RestrictedLanguage 模式的模块清单还允许下列附加变量：

- `$PSScriptRoot`
- `$PSEdition` PowerShell Core 中的 () 
- `$EnabledExperimentalFeatures` PowerShell Core 中的 () 

仅允许以下比较运算符：

- `-eq` (等于) 
- `-gt` (大于) 
- `-lt` (小于) 

不允许使用赋值语句、属性引用和方法调用。

#### <a name="no-language-nolanguage"></a>无语言 (NoLanguage) 

仅可通过 API 使用 NoLanguage 模式。 NoLanguage 模式表示不允许任何格式的脚本文本。 这将排除使用 **AddScript ( # B1** 方法，该方法发送要分析和执行的 PowerShell 脚本片段。 只能使用 **AddCommand ( # B1** 和 **AddParameter ( # B3** ，而不会经历分析器。

#### <a name="constrained-language-constrained-language"></a>受约束语言 (约束语言) 

ConstrainedLanguage 模式允许所有 cmdlet 和所有 PowerShell 语言元素，但它会限制允许的类型。

ConstrainedLanguage 模式旨在支持 Windows RT 上的用户模式代码完整性 (UMCI) 。 它在 Windows RT 上是唯一受支持的语言模式，但在所有支持的系统上都可用。

UMCI 通过仅允许在基于 Windows RT 的设备上安装经过 Microsoft 签名和 Microsoft 认证的应用来保护 ARM 设备。
ConstrainedLanguage 模式阻止用户使用 PowerShell 来绕过或违反 UMCI。

ConstrainedLanguage 模式的功能如下所示：

- 除了前面所述，Windows 模块中的所有 cmdlet 和其他 UMCI 批准的 cmdlet 均可完全正常运行，并且具有对系统资源的完全访问权限。

- 允许使用 PowerShell 脚本语言的所有元素。

- 可以导入 Windows 中包括的所有模块，以及模块导出在会话中运行的所有命令。

- 在 PowerShell 工作流中，你可以编写和运行 (以 PowerShell 语言) 编写的工作流的脚本工作流。 不支持基于 XAML 的工作流，并且不能在脚本工作流中运行 XAML，如使用 `Invoke-Expression -Language XAML` 。 此外，尽管允许嵌套工作流，但工作流不能调用其他工作流。

- `Add-Type`Cmdlet 可以加载签名的程序集，但无法加载任意 c # 代码或 Win32 api。

- `New-Object`Cmdlet 仅可用于) 下面列出 (允许的类型。

- 只能在 PowerShell 中使用) 下面 (允许的类型。 不允许使用其他类型。

- 允许类型转换，但仅当结果为允许的类型时。

- 仅当生成的类型为允许的类型时，才会使用 Cmdlet 参数将字符串输入转换为类型。

- 可以调用 **( # B1** 方法和 (下面列出的允许的类型的 .net 方法) 。 无法调用其他方法。

- 用户可以获取允许类型的所有属性。 用户只能在核心类型上设置属性的值。 仅允许下列 COM 对象：

  - **脚本编写。字典**
  - **Scripting.FileSystemObject**
  - **VBScript**

在 ConstrainedLanguage 模式下允许使用以下类型。 用户可以获取属性、调用方法以及将对象转换为这些类型。

允许的类型：

- AliasAttribute
- AllowEmptyCollectionAttribute
- AllowEmptyStringAttribute
- AllowNullAttribute
- Array
- Bool
- 字节
- char
- CmdletBindingAttribute
- DateTime
- Decimal
- DirectoryEntry
- DirectorySearcher
- Double
- FLOAT
- Guid
- Hashtable
- int
- Int16
- long
- ManagementClass
- System.management.managementobject
- ManagementObjectSearcher
- NullString
- OutputTypeAttribute
- ParameterAttribute
- PSCredential
- PSDefaultValueAttribute
- PSListModifier
- PSObject
- PSPrimitiveDictionary
- PSReference
- PSTypeNameAttribute
- 正则表达式
- SByte
- string
- SupportsWildcardsAttribute
- SwitchParameter
- System.Globalization.CultureInfo
- 系统 .Net. IPAddress
- 系统 MailAddress
- BigInteger
- System.Security.SecureString
- TimeSpan
- UInt16
- UInt32
- UInt64

### <a name="finding-the-language-mode-of-a-session-configuration"></a>查找会话配置的语言模式

使用会话配置文件创建会话配置时，会话配置将具有 LanguageMode 属性。 可以通过获取 LanguageMode 属性的值来找到语言模式。

```powershell
(Get-PSSessionConfiguration -Name Test).LanguageMode
FullLanguage
```

在其他会话配置中，你可以通过查找使用会话配置创建的会话的语言模式来间接查找语言模式。

### <a name="finding-the-language-mode-of-a-session"></a>查找会话的语言模式

可以通过获取会话状态的 LanguageMode 属性的值来找到 FullLanguage 或 ConstrainedLanguage 会话的语言模式。

例如：

```powershell
$ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

但是，在 RestrictedLanguage 模式和 NoLanguage 模式下，不能使用点方法来获取属性值。 相反，错误消息会显示语言模式。

`$ExecutionContext.SessionState.LanguageMode`在 RestrictedLanguage 会话中运行命令时，PowerShell 将返回 PropertyReferenceNotSupportedInDataSection 和 VariableReferenceNotSupportedInDataSection 错误消息。

- PropertyReferenceNotSupportedInDataSection：在受限语言模式或 Data 节中不允许使用属性引用。
- VariableReferenceNotSupportedInDataSection 在被限制语言模式下无法引用的变量或正在引用的数据节。

在 `$ExecutionContext.SessionState.LanguageMode` NoLanguage 会话中运行命令时，PowerShell 将返回 ScriptsNotAllowed 错误消息。

- ScriptsNotAllowed：此运行空间不支持语法。 这可能是因为它不是语言模式。

## <a name="see-also"></a>另请参阅

- [about_Session_Configuration_Files](about_Session_Configuration_Files.md)
- [about_Session_Configurations](about_Session_Configurations.md)
