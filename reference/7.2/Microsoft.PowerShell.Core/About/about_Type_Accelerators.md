---
description: 介绍适用于 .NET framework 类的类型加速器
Locale: en-US
ms.date: 05/01/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_type_accelerators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Type_Accelerators
ms.openlocfilehash: 67264326cc17b733e267225d521cfda0fa36d458
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598047"
---
# <a name="about-type-accelerators"></a>关于类型加速器

## <a name="short-desription"></a>简短描述
介绍适用于 .NET framework 类的类型加速器

## <a name="long-description"></a>详细说明

类型加速器是 .NET framework 类的别名。 它们允许您访问特定的 .NET framework 类，而无需显式键入整个类名。 例如，可以将 **AliasAttribute** 类从中缩短 `[System.Management.Automation.AliasAttribute]` 到 `[Alias]` 。

> [!NOTE]
> 所有类型加速器仍需用方括号括起来 (`[]`) 。

## <a name="available-type-accelerators"></a>可用类型加速器

|        加速器          |                           完整类名                           |
|---------------------------- | ------------------------------------------------------------------- |
|adsi                         | Microsoft.directoryservices                             |
|adsisearcher                 | Microsoft.directoryservices. DirectorySearcher                          |
|Alias                        | System.web. AliasAttribute                         |
|AllowEmptyCollection         | System.web. AllowEmptyCollectionAttribute          |
|AllowEmptyString             | System.web. AllowEmptyStringAttribute              |
|AllowNull                    | System.web. AllowNullAttribute                     |
|ArgumentCompleter            | System.web. ArgumentCompleterAttribute             |
|ArgumentCompletions          | System.web. ArgumentCompletionsAttribute           |
|array                        | System.Array                                                        |
|bigint                       | BigInteger                                          |
|布尔                         | System.Boolean                                                      |
|字节                         | System.Byte                                                         |
|char                         | System.Char                                                         |
|cimclass                     | CimClass。                        |
|cimconverter                 | CimConverter。                    |
|ciminstance                  | Microsoft.Management.Infrastructure.CimInstance                     |
|CimSession                   | Microsoft.Management.Infrastructure.CimSession                      |
|cimtype                      | CimType。                         |
|CmdletBinding                | System.web. CmdletBindingAttribute                 |
|cultureinfo                  | System.Globalization.CultureInfo                                    |
|datetime                     | System.DateTime                                                     |
|Decimal                      | System.Decimal                                                      |
|Double                       | System.Double                                                       |
|Set-dsclocalconfigurationmanager | System.web. DscLocalConfigurationManagerAttribute  |
|DscProperty                  | System.web. DscPropertyAttribute                   |
|DscResource                  | System.web. DscResourceAttribute                   |
|ExperimentAction             | System.web. ExperimentAction                       |
|实验                 | System.web. ExperimentalAttribute                  |
|ExperimentalFeature          | System.web. ExperimentalFeature                    |
|float                        | System.Single                                                       |
|guid                         | System.Guid                                                         |
|散                    | System.Collections.Hashtable                                        |
|initialsessionstate          | System.Management.Automation.Runspaces.InitialSessionState          |
|int                          | System.Int32                                                        |
|int16                        | System.Int16                                                        |
|int32                        | System.Int32                                                        |
|int64                        | System.Int64                                                        |
|ipaddress                    | 系统 .Net. IPAddress                                                |
|IPEndpoint                   | 系统 .Net. IPEndPoint                                               |
|long                         | System.Int64                                                        |
|mailaddress                  | 系统 MailAddress                                         |
|NullString                   | "NullString"。                    |
|ObjectSecurity               | Accesscontrol-namespace. ObjectSecurity                        |
|OutputType                   | System.web. OutputTypeAttribute                    |
|参数                    | System.web. ParameterAttribute                     |
|PhysicalAddress              | System.net.networkinformation. PhysicalAddress                       |
|powershell                   | System.web。                             |
|psaliasproperty              | System.web. PSAliasProperty                        |
|pscredential                 | System.Management.Automation.PSCredential                           |
|pscustomobject               | System.Management.Automation.PSObject                               |
|PSDefaultValue               | System.Management.Automation.PSDefaultValueAttribute                |
|pslistmodifier               | System.web. PSListModifier                         |
|psmoduleinfo                 | System.Management.Automation.PSModuleInfo                           |
|psnoteproperty               | System.web. PSNoteProperty                         |
|psobject                     | System.Management.Automation.PSObject                               |
|psprimitivedictionary        | System.web. PSPrimitiveDictionary                  |
|pspropertyexpression         | PSPropertyExpression。                  |
|psscriptmethod               | System.web. PSScriptMethod                         |
|psscriptproperty             | System.web. PSScriptProperty                       |
|PSTypeNameAttribute          | System.web. PSTypeNameAttribute                    |
|system.management.automation.psvariable                   | System.Management.Automation.PSVariable                             |
|psvariableproperty           | System.web. PSVariableProperty                     |
|ref                          | System.web. PSReference                            |
|regex                        | System.Text.RegularExpressions.Regex                                |
|运行空间                     | System.web. Management。                     |
|runspacefactory              | "RunspaceFactory"。              |
|sbyte                        | System.SByte                                                        |
|scriptblock                  | System.object。                            |
|securestring                 | System.Security.SecureString                                        |
|semver                       | System.web. SemanticVersion                        |
|short                        | System.Int16                                                        |
| single                       | System.Single                                                       |
|string                       | System.String                                                       |
|SupportsWildcards            | System.web. SupportsWildcardsAttribute             |
|开关                       | System.Management.Automation.SwitchParameter                        |
|timespan                     | System.TimeSpan                                                     |
|type                         | System.Type                                                         |
|uint                         | System.UInt32                                                       |
|uint16                       | System.UInt16                                                       |
|uint32                       | System.UInt32                                                       |
|uint64                       | System.UInt64                                                       |
|ulong                        | System.UInt64                                                       |
|uri                          | System.Uri                                                          |
|ushort                       | System.UInt16                                                       |
|ValidateCount                | System.web. ValidateCountAttribute                 |
|ValidateDrive                | System.web. ValidateDriveAttribute                 |
|ValidateLength               | System.web. ValidateLengthAttribute                |
|ValidateNotNull              | System.web. ValidateNotNullAttribute               |
|ValidateNotNullOrEmpty       | System.web. ValidateNotNullOrEmptyAttribute        |
|ValidatePattern              | System.web. ValidatePatternAttribute               |
|ValidateRange                | System.web. ValidateRangeAttribute                 |
|ValidateScript               | System.web. ValidateScriptAttribute                |
|ValidateSet                  | System.web. ValidateSetAttribute                   |
|ValidateTrustedData          | System.web. ValidateTrustedDataAttribute           |
|ValidateUserDrive            | System.web. ValidateUserDriveAttribute             |
|版本                      | System.Version                                                      |
|void                         | System.Void                                                         |
|WildcardPattern              | System.web. WildcardPattern                        |
|wmi                          | System.Management.ManagementObject                                  |
|wmiclass                     | ManagementClass                                   |
|wmisearcher                  | ManagementObjectSearcher                          |
|System.security.cryptography.x509certificates.x500distinguishedname        | System.Security.Cryptography.X509Certificates.X500DistinguishedName |
|X509Certificate              | System.Security.Cryptography.X509Certificates.X509Certificate       |
|xml                          | System.Xml.XmlDocument                                              |

