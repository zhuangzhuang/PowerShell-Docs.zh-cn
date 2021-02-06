---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-psdrive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSDrive
ms.openlocfilehash: 54b65a636fe05ed82d4f022b5bb8cbf8acaf7bab
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597234"
---
# New-PSDrive

## 摘要
创建临时映射网络驱动器和永久映射网络驱动器

## SYNTAX

### 全部

```
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Description <String>]
 [-Scope <String>] [-Persist] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

该 `New-PSDrive` cmdlet 将创建映射到数据存储区中的位置或与数据存储区中的某个位置（例如网络驱动器、本地计算机上的目录或注册表项）以及与远程计算机上的文件系统位置关联的持久 Windows 映射网络驱动器的临时驱动器。

临时驱动器仅存在于当前 PowerShell 会话中以及在当前会话中创建的会话中。 它们的名称可以在 PowerShell 中有效，并且可以映射到任何本地或远程资源。 您可以使用临时 PowerShell 驱动器访问关联数据存储中的数据，就像使用任何映射的网络驱动器一样。 您可以使用或来将位置更改到驱动器中，通过使用来 `Set-Location` 访问驱动器的内容 `Get-Item` `Get-ChildItem` 。

由于临时驱动器仅适用于 PowerShell，因此不能通过使用文件资源管理器、Windows Management Instrumentation (WMI) 、组件对象模型 (COM) 、Microsoft .NET 框架或使用 **NET use** 等工具来访问临时驱动器。

PowerShell 3.0 中添加了以下功能 `New-PSDrive` ：

- 映射的网络驱动器。 你可以使用的 **持久** 参数 `New-PSDrive` 来创建 Windows 映射网络驱动器。 与临时 PowerShell 驱动器不同，Windows 映射网络驱动器不是会话特定的。 它们保存在 Windows 中，可以通过使用标准的 Windows 工具（例如文件资源管理器和 **net use**）进行管理。 映射网络驱动器必须以驱动器号命名，并且连接到某个远程文件系统位置。 如果命令的作用域为本地，则不会有任何点，则 **持久性** 参数不会在运行该命令的范围之外保存 **new-psdrive** 的创建。 如果在 `New-PSDrive` 脚本中运行，并且希望驱动器无限期地保留，则必须将脚本保存到点。 为了获得最佳结果，若要强制新驱动器无限期保留，请将 **Scope** 参数添加到命令中，并将其值设置为 **Global**。 有关点到的详细信息，请参阅 [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing)。
- 外部驱动器。 当外部驱动器连接到计算机时，PowerShell 会自动将 **new-psdrive** 添加到代表新驱动器的文件系统中。 无需重新启动 PowerShell。 同样，当外部驱动器与计算机断开连接时，PowerShell 会自动删除表示已删除驱动器的 **new-psdrive** 。
- 通用命名约定 (UNC) 路径的凭据。

当 **根** 参数的值为 UNC 路径（例如）时，将 `\\Server\Share` 使用 **credential** 参数的值中指定的凭据创建 **new-psdrive**。 否则，在创建新的文件系统驱动器时， **凭据** 不起作用。

一些代码示例使用展开来减小行长度，提高可读性。 有关详细信息，请参阅 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。

## 示例

### 示例1：创建映射到网络共享的临时驱动器

此示例将创建一个映射到网络共享的临时 PowerShell 驱动器。

```powershell
New-PSDrive -Name "Public" -PSProvider "FileSystem" -Root "\\Server01\Public"
```

```Output
Name       Provider      Root
----       --------      ----
Public     FileSystem    \\Server01\Public
```

`New-PSDrive` 使用 **Name** 参数指定名为的 powershell 驱动器 `Public` ，并使用 **PSProvider** 参数来指定 powershell `FileSystem` 提供程序。 **Root** 参数指定网络共享的 UNC 路径。

查看 PowerShell 会话的内容： `Get-ChildItem -Path Public:`

### 示例2：创建映射到本地目录的临时驱动器

此示例将创建一个临时 PowerShell 驱动器，用于访问本地计算机上的某个目录。

```powershell
$parameters = @{
    Name = "MyDocs"
    PSProvider = "FileSystem"
    Root = "C:\Users\User01\Documents"
    Description = "Maps to my My Documents folder."
}
New-PSDrive @parameters
```

```Output
Name        Provider      Root
----        --------      ----
MyDocs      FileSystem    C:\Users\User01\Documents
```

展开创建参数键和值。 **Name** 参数指定驱动器名称， **MyDocs**。 **PSProvider** 参数指定 PowerShell `FileSystem` 提供程序。 **Root** 指定本地计算机的目录。 **Description** 参数描述驱动器的用途。 `New-PSDrive` 使用 splatted 参数创建 `MyDocs` 驱动器。

查看 PowerShell 会话的内容： `Get-ChildItem -Path MyDocs:`

### 示例3：创建用于注册表项的临时驱动器

此示例创建一个提供对注册表项的访问的临时 PowerShell 驱动器。 它会创建一个名为 MyCompany 的驱动器，该驱动器映射到 `HKLM:\Software\MyCompany` 注册表项。

```powershell
New-PSDrive -Name "MyCompany" -PSProvider "Registry" -Root "HKLM:\Software\MyCompany"
```

```Output
Name           Provider      Root
----           --------      ----
MyCompany      Registry      HKLM:\Software\MyCompany
```

`New-PSDrive` 使用 **Name** 参数指定名为的 powershell 驱动器 `MyCompany` ，并使用 **PSProvider** 参数来指定 powershell `Registry` 提供程序。 **Root** 参数指定注册表位置。

查看 PowerShell 会话的内容： `Get-ChildItem -Path MyCompany:`

### 示例4：使用凭据创建永久映射网络驱动器

此示例将使用域服务帐户凭据进行身份验证的网络驱动器进行映射。
有关存储凭据的 **PSCredential** 对象以及如何将密码存储为 **SecureString** 的详细信息，请参阅 **Credential** 参数的描述。

```powershell
$cred = Get-Credential -Credential Contoso\ServiceAccount
New-PSDrive -Name "S" -Root "\\Server01\Scripts" -Persist -PSProvider "FileSystem" -Credential $cred
Net Use
```

```Output
Status       Local     Remote                    Network
---------------------------------------------------------
OK           S:        \\Server01\Scripts        Microsoft Windows Network
```

> [!NOTE]
> 请记住，如果在脚本中使用上述代码片段，请将 **作用域** 参数值设置为 "Global"，以确保驱动器在当前作用域外保持不变。

`$cred`变量存储包含服务帐户凭据的 **PSCredential** 对象。 `Get-Credential` 提示输入存储在 **SecureString** 中的密码。

`New-PSDrive` 使用几个参数创建映射网络驱动器。 **名称** 指定 `S` Windows 接受的驱动器号。 和 **Root** 定义 `\\Server01\Scripts` 为远程计算机上的位置。 **持久性** 将创建保存在本地计算机上的 Windows 映射网络驱动器。 **PSProvider** 指定 `FileSystem` 提供程序。 **Credential** 使用该 `$cred` 变量获取用于身份验证的服务帐户凭据。

可以在本地计算机上的 PowerShell 会话、文件资源管理器和 **网络使用** 等工具中查看映射的驱动器。 查看 PowerShell 会话的内容： `Get-ChildItem -Path S:`

### 示例5：创建持久和临时驱动器

此示例显示了永久映射网络驱动器与映射到同一网络共享的临时 PowerShell 驱动器之间的差异。

如果关闭 PowerShell 会话并打开一个新的会话，则该临时 `PSDrive:` 磁盘不可用，但永久 `X:` 驱动器可用。 确定使用哪种方法来映射网络驱动器时，请考虑使用驱动器的方式。 例如，它是否必须是永久性的，以及驱动器是否对其他 Windows 功能可见。

```powershell
# Create a temporary PowerShell drive called PSDrive:
# that's mapped to the \\Server01\Public network share.
New-PSDrive -Name "PSDrive" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Use the Persist parameter of New-PSDrive to create the X: mapped network drive,
# which is also mapped to the \\Server01\Public network share.
New-PSDrive -Persist -Name "X" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Now, you can use the Get-PSDrive drive cmdlet to examine the two drives.
# The drives appear to be the same, although the network share name appears only
# in the root of the PSDrive: drive.
Get-PSDrive -Name "PSDrive", "X"
```

```Output
Name       Provider      Root
----       --------      ----

PsDrive    FileSystem    \\Server01\public
X          FileSystem    X:\
```

```powershell
# Get-Member cmdlet shows that the drives have the same object type,
# System.Management.Automation.PSDriveInfo.
Get-PSDrive "PSDrive", "x" | Get-Member
```

```Output
TypeName: System.Management.Automation.PSDriveInfo

Name                MemberType   Definition
----                ----------   ----------
CompareTo           Method       System.Int32 CompareTo(PSDriveInfo drive),
Equals              Method       System.Boolean Equals(Object obj),
GetHashCode         Method       System.Int32 GetHashCode()
...
```

```powershell
# Net Use and Get-CimInstance for the Win32_LogicalDisk class,
# and Win32_NetworkConnection class find only the persistent X: drive.
# PowerShell temporary drives are known only to PowerShell.
Net Use
Get-CimInstance Win32_LogicalDisk | Format-Table -Property DeviceID
Get-CimInstance Win32_NetworkConnection
```

```Output
Status       Local     Remote                    Network
--------------------------------------------------------
OK           X:        \\contoso-pc\data         Microsoft Windows Network

deviceid
--------
C:
D:
X:

LocalName    RemoteName              ConnectionState          Status
---------    ----------              ---------------          ------
X:           \\products\public       Disconnected             Unavailable
```

## PARAMETERS

### -Confirm

提示你在运行 cmdlet 之前进行确认。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定有权执行此操作的用户帐户。 默认为当前用户。

由于 PowerShell 3.0，当 **Root** 参数的值为 UNC 路径时，你可以使用凭据来创建文件系统驱动器。

键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。 如果键入用户名，系统会提示输入密码。

凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Description

指定驱动器的简短文本说明。 键入任意字符串。

若要查看所有会话驱动器的说明，请参阅 `Get-PSDrive | Format-Table Name, Description` 。

若要查看特定驱动器的说明，请键入 `(Get-PSDrive <DriveName>).Description` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定新驱动器的名称。 对于永久映射网络驱动器，请使用驱动器号。 对于临时 PowerShell 驱动器，你并不限于驱动器号，请使用任何有效的字符串。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -持久性

指示此 cmdlet 创建 Windows 映射网络驱动器。 **持久性** 参数仅在 Windows 上可用。

映射网络驱动器保存于本地计算机的 Windows 中。 它们是持久性的，而不是特定于会话的，可以在文件资源管理器和其他工具中进行查看和管理。

在本地对命令进行作用域时，如果没有点到 **，则不会在运行** 命令的范围之外保存 **new-psdrive** 的创建。 如果在 `New-PSDrive` 脚本中运行，并且希望新驱动器无限期地保留，则必须将脚本置于点端。 为了获得最佳结果，若要强制新驱动器保留，请将 **Global** 指定为 **Scope** 参数的值，并在命令中包含 " **永久保存** "。

驱动器名称必须是字母，如 `D` 或 `E` 。 **Root** 参数的值必须是另一台计算机的 UNC 路径。 **PSProvider** 参数的值必须是 `FileSystem` 。

若要断开 Windows 映射网络驱动器，请使用 `Remove-PSDrive` cmdlet。 在断开 Windows 映射网络驱动器时，将从计算机中永久删除该映射，而不仅是从当前会话中删除。

映射网络驱动器特定于用户帐户。 使用其他用户的凭据启动的会话中不显示使用其他用户的凭据在提升的会话或会话中创建的映射驱动器。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

指定支持此类型的驱动器的 PowerShell 提供程序。

例如，如果驱动器与网络共享或文件系统目录相关联，则 PowerShell 提供程序为 `FileSystem` 。 如果驱动器与注册表项关联，则提供程序为 `Registry` 。

临时 PowerShell 驱动器可以与任何 PowerShell 提供程序相关联。 映射的网络驱动器只能与 `FileSystem` 提供程序相关联。

若要查看 PowerShell 会话中提供程序的列表，请使用 `Get-PSProvider` cmdlet。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -根

指定 PowerShell 驱动器映射到的数据存储位置。

例如，指定一个网络共享，例如 `\\Server01\Public` 本地目录（如 `C:\Program Files` ）或注册表项（如） `HKLM:\Software\Microsoft` 。

临时 PowerShell 驱动器可以与任何受支持的提供程序驱动器上的本地或远程位置关联。 映射网络驱动器只能与远程计算机上的文件系统位置关联。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Scope

指定驱动器的作用域。 此参数的可接受值为： **Global**、 **Local**、 **Script** 或相对于当前作用域的数字。 范围号0到范围数。 当前作用域编号为0，其父级为1。 有关详细信息，请参阅 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。 cmdlet 未运行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入用于此 cmdlet。

## 输出

### System.Management.Automation.PSDriveInfo

## 注释

`New-PSDrive` 设计用于处理由任何提供程序公开的数据。 若要列出会话中可用的提供程序，请使用 `Get-PSProvider` 。 有关提供程序的详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

映射网络驱动器特定于用户帐户。 使用其他用户的凭据启动的会话中不显示使用其他用户的凭据在提升的会话或会话中创建的映射驱动器。

## 相关链接

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Get-PSDrive](Get-PSDrive.md)

[Remove-PSDrive](Remove-PSDrive.md)

