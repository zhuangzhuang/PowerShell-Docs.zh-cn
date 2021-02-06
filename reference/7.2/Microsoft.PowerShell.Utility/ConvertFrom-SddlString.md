---
external help file: Microsoft.PowerShell.Utility-help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-sddlstring?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SddlString
ms.openlocfilehash: 5c8e963486c0d4f5f3e7d643cb65c752720f37d1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603401"
---
# ConvertFrom-SddlString

## 摘要
将 SDDL 字符串转换为自定义对象。

## SYNTAX

### 全部

```
ConvertFrom-SddlString [-Sddl] <String> [-Type <AccessRightTypeNames>] [<CommonParameters>]
```

## DESCRIPTION

`ConvertFrom-SddlString`Cmdlet 可将安全描述符定义语言字符串转换为具有以下属性的自定义 **PSCustomObject** 对象： Owner、Group、descriptor.discretionaryacl、SystemAcl 和 RawDescriptor。

所有者、组、Descriptor.discretionaryacl 和 SystemAcl 属性包含 SDDL 字符串中指定的访问权限的可读文本表示形式。

此 cmdlet 是在 PowerShell 5.0 中引入的。

## 示例

### 示例1：将文件系统访问权限 SDDL 转换为 PSCustomObject

```powershell
$acl = Get-Acl -Path C:\Windows
ConvertFrom-SddlString -Sddl $acl.Sddl
```

第一个命令使用 `Get-Acl` cmdlet 来获取 C：\Windows 文件夹的安全描述符，并将其保存在变量中。

第二个命令使用 `ConvertFrom-SddlString` cmdlet 来获取 sddl 字符串的文本表示形式，该对象包含在表示安全描述符的对象的 "sddl" 属性中。

### 示例2：将注册表访问权限 SDDL 转换为 PSCustomObject

```powershell
$acl = Get-Acl HKLM:\SOFTWARE\Microsoft\
ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights
```

第一个命令使用 `Get-Acl` cmdlet 来获取 HKLM： \ SOFTWARE\Microsoft\ 密钥的安全描述符，并将其保存在变量中。

第二个命令使用 `ConvertFrom-SddlString` cmdlet 来获取 sddl 字符串的文本表示形式，该对象包含在表示安全描述符的对象的 "sddl" 属性中。

它使用 `-Type` 参数来指定 SDDL 字符串表示注册表安全描述符。

### 示例3：使用带有和不带参数的 ConvertFrom-SddlString 将注册表访问权限 SDDL 转换为 PSCustomObject `-Type`

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Microsoft\

ConvertFrom-SddlString -Sddl $acl.Sddl | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateDirectories, Delete, ExecuteKey, FullControl, GenericExecute, GenericWrite, ListDirectory, ReadExtendedAttributes, ReadPermissions, TakeOwnership, Traverse, WriteData, WriteExtendedAttributes, WriteKey)

ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateLink, CreateSubKey, Delete, EnumerateSubKeys, ExecuteKey, FullControl, GenericExecute, GenericWrite, Notify, QueryValues, ReadPermissions, SetValue, TakeOwnership, WriteKey)
```

第一个命令使用 `Get-Acl` cmdlet 来获取 HKLM： \ SOFTWARE\Microsoft\ 密钥的安全描述符，并将其保存在变量中。

第二个命令使用 `ConvertFrom-SddlString` cmdlet 来获取 sddl 字符串的文本表示形式，该对象包含在表示安全描述符的对象的 "sddl" 属性中。

它不使用 `-Type` 参数，因此显示的访问权限用于文件系统。

第三个命令将 `ConvertFrom-SddlString` cmdlet 与参数一起使用 `-Type` ，以使返回的访问权限用于注册表。

## PARAMETERS

### -Sddl

指定表示安全描述符的字符串（SDDL 语法）。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Type

指定 SDDL 字符串表示的权限类型。

此参数的可接受值为：

- FileSystemRights
- RegistryRights
- ActiveDirectoryRights
- MutexRights
- SemaphoreRights
- CryptoKeyRights
- EventWaitHandleRights

默认情况下，cmdlet 使用文件系统权限。

CryptoKeyRights 和 ActiveDirectoryRights 在 PowerShell Core 中不受支持。

```yaml
Type: Microsoft.PowerShell.Commands.ConvertFromSddlStringCommand+AccessRightTypeNames
Parameter Sets: (All)
Aliases:
Accepted values: FileSystemRights, RegistryRights, ActiveDirectoryRights, MutexRights, SemaphoreRights, CryptoKeyRights, EventWaitHandleRights

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将 SDDL 字符串传递给 `ConvertFrom-SddlString` 。

## 输出

## 注释

此 cmdlet 仅在 Windows 平台上可用。

## 相关链接

[安全描述符定义语言](/windows/win32/secauthz/security-descriptor-definition-language)
