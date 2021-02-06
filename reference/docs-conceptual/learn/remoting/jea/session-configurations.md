---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 会话配置
description: 会话配置定义了可使用 JEA 终结点的人员及其有权访问的角色。
ms.openlocfilehash: b616d5bf260bbdfe89b6422fd4a8b4866f7fdc67
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501552"
---
# <a name="jea-session-configurations"></a>JEA 会话配置

JEA 终结点通过在系统上创建和注册 PowerShell 会话配置文件进行注册。 会话配置定义了可使用 JEA 终结点的人员及其有权访问的角色。 它们还定义了一些全局设置，这些设置应用于 JEA 会话中的所有用户。

## <a name="create-a-session-configuration-file"></a>创建会话配置文件

要注册 JEA 终结点，必须指定该终结点的配置方式。 需要考虑很多选项。 最重要的选项是：

- 谁有权访问 JEA 终结点
- 他们分配到哪些角色
- JEA 在后台使用哪个标识
- JEA 终结点的名称

这些选项是在 PowerShell 数据文件中定义的，该文件被称为 PowerShell 会话配置文件，扩展名为 `.pssc`。 可使用任意文本编辑器编辑会话配置文件。

请运行以下命令，创建一个空白的模板配置文件。

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> 默认情况下，模板文件仅包含最常用的配置选项。 使用 `-Full` 切换，在生成的 PSSC 中包含所有适用设置。

`-SessionType RestrictedRemoteServer` 字段指示 JEA 使用该会话配置进行安全管理。 此类型的会话在 NoLanguage 模式下运行，且只有权访问以下默认命令（和别名）：

- Clear-Host (cls, clear)
- Exit-PSSession (exsn, exit)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Measure-Object (measure)
- Out-Default
- Select-Object (select)

PowerShell 提供程序均不可用，也不提供任何外部程序（可执行文件或脚本）。

有关语言模式的详细信息，请参阅 [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes)。

### <a name="choose-the-jea-identity"></a>选择 JEA 标识

JEA 在后台运行已连接用户的命令时需要使用标识（即帐户）。
由你定义 JEA 在会话配置文件中使用哪个标识。

#### <a name="local-virtual-account"></a>本地虚拟帐户

如果为 JEA 终结点定义的所有角色均用于管理本地计算机，并且本地管理员帐户足以成功运行命令，则本地虚拟帐户非常有用。
虚拟帐户是特定用户所独有的临时帐户，仅在 PowerShell 会话的持续时间内有效。 在成员服务器或工作站上，虚拟帐户属于本地计算机的管理员组。 在 Active Directory 域控制器上，虚拟帐户属于域的 **域管理员** 组。

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

如果会话配置定义的角色不需要完全管理权限，则可指定将包含虚拟帐户的安全组。 在成员服务器或工作站上，指定的安全组必须是本地组，而不是来自域的组。

指定一个或多个安全组后，不可将虚拟帐户分配给本地或域管理员组。

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> 虚拟帐户在本地服务器安全策略中被临时授予“作为服务登录”的权限。 如果指定的 VirtualAccountGroups 之一已在策略中被授予此权限，则无法对策略添加和删除单个虚拟帐户。 对于会仔细审核域控制器安全策略修订的域控制器这类情形，这可能会十分有用。 这仅在具有 2018 年 11 月或更高版本汇总的 Windows Server 2016 和具有 2019 年 1 月或更高版本汇总的 Windows Server 2019 中可用。

#### <a name="group-managed-service-account"></a>组托管服务帐户

组托管服务帐户 (GMSA) 是 JEA 用户需要访问文件共享和 Web 服务等网络资源时适合使用的标识。 GMSA 提供域标识，用于对域内任何计算机上的资源进行身份验证。 GMSA 提供的权限由你正在访问的资源而定。 你不具有任何计算机或服务的管理员权限，除非计算机或服务管理员已向 GMSA 显式授予这些权限。

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

仅在必要时才应使用 GMSA：

- 使用 GMSA 时，很难追溯到执行操作的用户。 每位用户都共享相同的运行身份标识。 你必须查看 PowerShell 会话脚本和日志，才能将各用户与其操作关联起来。

- GMSA 可访问连接用户无需访问的多个网络资源。 请始终尽力限制 JEA 会话中的有效权限以符合最低特权原则。

> [!NOTE]
> 组托管服务帐户仅适用于使用 PowerShell 5.1 或更高版本且已加入域的计算机。

要详细了解如何保护 JEA 会话，请参阅[安全注意事项](security-considerations.md)一文。

### <a name="session-transcripts"></a>会话脚本

建议将 JEA 终结点配置为自动记录用户会话的脚本。 通过 PowerShell 会话脚本，可查看连接用户、向其分配的运行方式标识以及该用户运行的命令。 对于需要了解谁执行了特定系统更改的审核团队，这些信息非常有用。

若要在会话配置文件中配置自动脚本，请提供应存储脚本的文件夹路径。

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

脚本由本地系统帐户写入到文件夹中，该帐户需要目录的读取和写入权限。 标准用户应无权访问该文件夹。 请限制有权审核脚本的安全管理员的数量。

### <a name="user-drive"></a>用户驱动器

如果连接用户需要将文件复制到 JEA 终结点或从中复制文件，可在会话配置文件中启用用户驱动器。 用户驱动器是映射到各连接用户的唯一文件夹的 **PSDrive**。 此文件夹允许用户将文件复制到系统或从中复制文件，但不提供访问完整文件系统的权限，也不公开 FileSystem 提供程序。 用户驱动器内容在会话之间持续存在，以便应对网络连接可能中断的情况。

```powershell
MountUserDrive = $true
```

默认情况下，用户驱动器允许每个用户存储最多 50 MB 的数据。 可使用“UserDriveMaximumSize”字段限制用户能使用的数据量。

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

如果不想持久保留用户驱动器中的数据，可在系统上配置计划任务，每晚自动清理文件夹。

> [!NOTE]
> 用户驱动器仅适用于 PowerShell 5.1 或更高版本。

有关 PSDrive 的详细信息，请参阅[管理 PowerShell 驱动器](/powershell/scripting/samples/managing-windows-powershell-drives)。

### <a name="role-definitions"></a>角色定义

会话配置文件中的角色定义可定义 **用户** 到 **角色** 的映射。 注册时，此字段中包含的所有用户或组都将获得 JEA 终结点的权限。
每个用户或组仅可在哈希表中以键的形式内附一次，但可向其分配多个角色。 角色功能名称应为角色功能文件的名称，但不带 `.psrc` 扩展名。

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

如果某用户属于角色定义中的多个组，则有权访问每个组的角色。 两个角色向同一个 cmdlet 授予访问权限时，向用户授予最宽松的参数集。

在角色定义字段中指定本地用户或组时，请务必使用计算机名称，而不是 localhost 或通配符。 可通过检查 `$env:COMPUTERNAME` 变量来查看计算机名称。

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>角色功能搜索顺序

如上例所示，角色功能由角色功能文件的基名称进行引用。 文件的基名称是不带扩展名的文件名。 如果多个角色功能适用于具有相同名称的系统，则 PowerShell 使用其隐式搜索顺序选择有效的角色功能文件。 JEA 不提供对名称相同的所有角色功能文件的访问权限。

JEA 使用 `$env:PSModulePath` 环境变量来确定扫描角色功能文件的路径。 在每个路径中，JEA 查找包含“RoleCapabilities”子文件夹的有效 PowerShell 模块。 与导入模块一样，与具有相同名称的自定义角色功能相比，JEA 更倾向于 Windows 随附的角色功能。

对于所有其他命名冲突，优先级由 Windows 枚举目录中文件的顺序决定。 不保证按字母顺序排序。 找到的匹配所指定名称的第一个角色功能文件用于连接用户。 由于角色功能搜索顺序具有不确定性，由此强烈建议让角色功能具有唯一的文件名。

### <a name="conditional-access-rules"></a>条件访问规则

RoleDefinitions 字段中包含的所有用户和组都将自动获得访问 JEA 终结点的权限。 通过条件访问规则，可优化此访问权限并要求用户隶属于其他不会影响其所拥有角色的安全组。 如果要将 JEA 与即时特权访问管理解决方案、智能卡身份验证或其他多重身份验证解决方案进行集成，此规则十分有用。

条件访问规则在会话配置文件的 RequiredGroups 字段中进行定义。
可在此处提供哈希表（选择性嵌套），利用“And”和“Or”键构造规则。 以下是如何使用此字段的一些示例：

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> 条件访问规则仅适用于 PowerShell 5.1 或更高版本。

### <a name="other-properties"></a>其他属性

会话配置文件还可执行角色功能文件能实现的所有操作，但无法授予连接用户访问不同命令的权限。 如果想要允许所有用户访问特定的 cmdlet、函数或提供程序，可直接在会话配置文件中执行此操作。
有关会话配置文件中受支持属性的完整列表，请运行 `Get-Help New-PSSessionConfigurationFile -Full`。

## <a name="testing-a-session-configuration-file"></a>测试会话配置文件

可使用 [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet 测试会话配置。 如果已手动编辑 `.pssc` 文件，则建议测试会话配置文件。 测试可确保语法正确无误。 如果会话配置文件没有通过此测试，则不能在系统上注册该文件。

## <a name="sample-session-configuration-file"></a>示例会话配置文件

下面的示例演示了如何创建和验证 JEA 的会话配置。 为了简便和易读，角色定义是在 `$roles` 变量中进行创建和存储的。 但并非必须这样做。

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>更新会话配置文件

要更改 JEA 会话配置的属性（包括用户到角色的映射），必须进行[注销](register-jea.md#unregistering-jea-configurations)。 然后，使用更新后的会话配置文件[重新注册](register-jea.md) JEA 会话配置。

## <a name="next-steps"></a>后续步骤

- [注册 JEA 配置](register-jea.md)
- [创作 JEA 角色](role-capabilities.md)
