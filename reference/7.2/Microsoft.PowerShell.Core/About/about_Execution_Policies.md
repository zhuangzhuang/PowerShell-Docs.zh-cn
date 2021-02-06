---
description: 介绍 PowerShell 执行策略并说明如何管理它们。
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Execution_Policies
ms.openlocfilehash: 1a2b8458b39233f96d47a52e3fea21b31e9b3c42
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603608"
---
# <a name="about-execution-policies"></a>关于执行策略

## <a name="short-description"></a>简短说明
介绍 PowerShell 执行策略并说明如何管理它们。

## <a name="long-description"></a>详细说明

PowerShell 执行策略是一项安全功能，用于控制 PowerShell 加载配置文件和运行脚本的条件。 此功能有助于防止恶意脚本的执行。

在 Windows 计算机上，可以为本地计算机、当前用户或特定会话设置执行策略。 你还可以使用组策略设置为计算机和用户设置执行策略。

本地计算机和当前用户的执行策略存储在注册表中。 不需要在 PowerShell 配置文件中设置执行策略。
特定会话的执行策略仅存储在内存中，并在会话关闭时丢失。

执行策略不是限制用户操作的安全系统。 例如，当用户无法运行脚本时，可以通过在命令行中键入脚本内容来轻松地绕过策略。 相反，执行策略可帮助用户设置基本规则并防止无意中违反它们。

在非 Windows 计算机上，默认的执行策略是不 **受限制** 的，无法更改。 `Set-ExecutionPolicy`Cmdlet 可用，但 PowerShell 会显示不受支持的控制台消息。 虽然 `Get-ExecutionPolicy` 在非 windows 平台上返回不 **受限制** ，但行为确实与 **回避** 匹配，因为这些平台不实现 Windows 安全区域。

## <a name="powershell-execution-policies"></a>PowerShell 执行策略

这些策略的强制仅在 Windows 平台上发生。 PowerShell 执行策略如下所示：

### <a name="allsigned"></a>AllSigned

- 脚本可以运行。
- 要求所有脚本和配置文件都由受信任的发布者签名，包括在本地计算机上编写的脚本。
- 在从尚未归类为受信任或不受信任的发布者运行脚本之前，将提示您。
- 运行已签名但恶意脚本的风险。

### <a name="bypass"></a>免验证

- 不阻止任何操作，并且没有任何警告或提示。
- 此执行策略适用于以下配置：将 PowerShell 脚本内置于更大的应用程序或配置，其中 PowerShell 是具有其自己的安全模型的程序的基础。

### <a name="default"></a>默认

- 设置默认的执行策略。
- Windows 客户端 **限制**。
- 适用于 Windows server 的 **RemoteSigned** 。

### <a name="remotesigned"></a>RemoteSigned

- Windows server 计算机的默认执行策略。
- 脚本可以运行。
- 要求来自受信任的发布者的脚本和配置文件的数字签名，这些脚本和配置文件是从 internet 下载的，其中包括电子邮件和即时消息程序。
- 不需要在本地计算机上编写的脚本上的数字签名，也不需要从 internet 下载。
- 如果未对脚本进行阻止，则运行从 internet 下载的脚本，而不是未签名的脚本，例如通过使用 `Unblock-File` cmdlet。
- 从 internet 以外的源运行未签名脚本的风险，以及可能是恶意的签名脚本。

### <a name="restricted"></a>受限制

- Windows 客户端计算机的默认执行策略。
- 允许单独的命令，但不允许脚本。
- 阻止运行所有脚本文件，包括格式设置和配置文件 (`.ps1xml`) 、模块脚本文件 (`.psm1`) 和 PowerShell 配置文件 (`.ps1`) 。

### <a name="undefined"></a>Undefined

- 当前作用域中没有设置执行策略。
- 如果所有作用域中的执行策略均未 **定义**，则对 windows 客户端和 Windows Server **RemoteSigned** 的有效执行策略将 **受到限制**。

### <a name="unrestricted"></a>非受限

- 非 Windows 计算机的默认执行策略无法更改。
- 未签名的脚本可以运行。 存在运行恶意脚本的风险。
- 在运行不在本地 intranet 区域中的脚本和配置文件之前警告用户。

> [!NOTE]
> 在不区分通用命名约定 (UNC) 路径与 internet 路径的系统上，可能无法使用 **RemoteSigned** 执行策略来运行 unc 路径标识的脚本。

## <a name="execution-policy-scope"></a>执行策略作用域

可以设置仅在特定作用域内有效的执行策略。

**作用域** 的有效值为 **MachinePolicy**、 **UserPolicy**、 **Process**、 **CurrentUser** 和 **LocalMachine**。 设置执行策略时， **LocalMachine** 为默认值。

**作用域** 值按优先级顺序列出。 优先级相同的策略在当前会话中有效，即使在优先级较低的情况下设置了限制性更强的策略也是如此。

有关详细信息，请参阅 [set-executionpolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)。

### <a name="machinepolicy"></a>MachinePolicy

为计算机的所有用户组策略设置。

### <a name="userpolicy"></a>UserPolicy

为计算机的当前用户组策略设置。

### <a name="process"></a>过程

**进程** 范围仅影响当前 PowerShell 会话。 执行策略保存在环境变量中 `$env:PSExecutionPolicyPreference` ，而不是保存在注册表中。 关闭 PowerShell 会话后，会删除变量和值。

### <a name="currentuser"></a>CurrentUser

执行策略仅影响当前用户。 它存储在 **HKEY_CURRENT_USER** 注册表子项中。

### <a name="localmachine"></a>LocalMachine

执行策略会影响当前计算机上的所有用户。 它存储在 **HKEY_LOCAL_MACHINE** 注册表子项中。

## <a name="managing-the-execution-policy-with-powershell"></a>通过 PowerShell 管理执行策略

若要获取当前 PowerShell 会话的有效执行策略，请使用 `Get-ExecutionPolicy` cmdlet。

以下命令将获取有效的执行策略：

```powershell
Get-ExecutionPolicy
```

若要获取影响当前会话的所有执行策略，并按优先顺序显示它们：

```powershell
Get-ExecutionPolicy -List
```

结果与以下示例输出类似：

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine       AllSigned
```

在这种情况下，有效的执行策略是 **RemoteSigned** ，因为当前用户的执行策略优先于为本地计算机设置的执行策略。

若要获取为特定作用域设置的执行策略，请使用的 **作用域** 参数 `Get-ExecutionPolicy` 。

例如，以下命令将获取 **CurrentUser** 作用域的执行策略：

```powershell
Get-ExecutionPolicy -Scope CurrentUser
```

### <a name="change-the-execution-policy"></a>更改执行策略

若要更改 Windows 计算机上的 PowerShell 执行策略，请使用 `Set-ExecutionPolicy` cmdlet。 更改立即生效。 不需要重新启动 PowerShell。

如果设置作用域 **LocalMachine** 或 **CurrentUser** 的执行策略，则更改将保存在注册表中并保持有效，直到再次更改。

如果为 **进程** 范围设置了执行策略，则它不会保存在注册表中。 将保留执行策略，直到关闭当前进程和任何子进程。

> [!NOTE]
> 在 Windows Vista 和更高版本的 Windows 中，若要运行更改本地计算机的执行策略的命令 **，则** 可以通过 "以 **管理员身份运行** " 选项启动 PowerShell。

更改执行策略：

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName>
```

例如：

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

若要设置特定范围中的执行策略，请执行以下操作：

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName> -Scope <scope>
```

例如：

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

用于更改执行策略的命令可以成功，但仍不会更改有效的执行策略。

例如，为本地计算机设置执行策略的命令可能会成功，但会被当前用户的执行策略覆盖。

### <a name="remove-the-execution-policy"></a>删除执行策略

若要删除特定作用域的执行策略，请将执行策略设置为 **Undefined**。

例如，要为本地计算机的所有用户删除执行策略，请执行以下操作：

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope LocalMachine
```

删除 **作用域** 的执行策略：

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
```

如果未在任何范围内设置执行策略，则会 **限制** 有效执行策略，这是 Windows 客户端的默认设置。

### <a name="set-a-different-policy-for-one-session"></a>为一个会话设置不同的策略

你可以使用 **pwsh.exe** 的 **set-executionpolicy** 参数为新的 PowerShell 会话设置执行策略。 策略只影响当前会话和子会话。

若要为新会话设置执行策略，请在命令行中启动 PowerShell，如 **cmd.exe** 或 powershell，然后使用 **pwsh.exe** 的 **set-executionpolicy** 参数设置执行策略。

例如：

```powershell
pwsh.exe -ExecutionPolicy AllSigned
```

你设置的执行策略未存储在注册表中。 相反，它存储在 `$env:PSExecutionPolicyPreference` 环境变量中。 关闭设置了策略的会话时，将删除该变量。 不能通过编辑变量值来更改策略。

在会话期间，为会话设置的执行策略优先于在注册表中为本地计算机或当前用户设置的执行策略。 但是，它不会优先于通过使用组策略设置的执行策略。

## <a name="use-group-policy-to-manage-execution-policy"></a>使用组策略来管理执行策略

您可以使用 " **打开脚本执行** 组策略" 设置来管理企业中的计算机的执行策略。 组策略设置将替代在所有作用域中在 PowerShell 中设置的执行策略。

" **打开脚本执行** " 策略设置如下所示：

- 如果禁用 " **启用脚本执行**"，脚本将不会运行。 这等效于 **受限制** 的执行策略。
- 如果启用 "启用 **脚本执行**"，则可以选择执行策略。 组策略设置等效于以下执行策略设置：

  | 组策略                                  | 执行策略 |
  | --------------------------------------------- | ---------------- |
  | 允许所有脚本                             | 非受限     |
  | 允许本地脚本和远程签名的脚本 | RemoteSigned     |
  | 仅允许签名脚本                     | AllSigned        |

- 如果未配置 " **启用脚本执行** "，则它不起作用。 在 PowerShell 中设置的执行策略是有效的。

PowerShellExecutionPolicy 和 PowerShellExecutionPolicy 文件将 **打开脚本执行** 策略添加到组策略编辑器中的 "计算机配置" 和 "用户配置" 节点，路径如下。

对于 Windows XP 和 Windows Server 2003：

管理 \Windows 组件 \Windows PowerShell

对于 Windows Vista 和更高版本的 Windows：

管理 Templates\Classic 管理模板 \
Windows \Windows PowerShell

"计算机配置" 节点中设置的策略优先于 "用户配置" 节点中设置的策略。

有关详细信息，请参阅 [about_Group_Policy_Settings](about_Group_Policy_Settings.md)。

### <a name="execution-policy-precedence"></a>执行策略优先级

在确定会话的有效执行策略时，PowerShell 将按以下优先顺序评估执行策略：

- 组策略： MachinePolicy
- 组策略： UserPolicy
- 执行策略：处理 (或 `pwsh.exe -ExecutionPolicy`) 
- 执行策略： CurrentUser
- 执行策略： LocalMachine

## <a name="manage-signed-and-unsigned-scripts"></a>管理签名和未签名的脚本

在 Windows 中，Internet Explorer 和 Microsoft Edge 等程序将备用数据流添加到下载的文件中。 这会将该文件标记为 "来自 Internet"。 如果 PowerShell 执行策略是 **RemoteSigned**，则 powershell 不会运行从 internet 下载的未签名脚本，其中包括电子邮件和即时消息程序。

你可以对脚本进行签名，或选择运行未签名的脚本，而无需更改执行策略。

从 PowerShell 3.0 开始，可以使用 cmdlet 的 **Stream** 参数 `Get-Item` 来检测因从 internet 下载而被阻止的文件。 使用 `Unblock-File` cmdlet 取消阻止脚本，以便可以在 PowerShell 中运行它们。

有关详细信息，请参阅 [about_Signing](about_Signing.md)、 [获取项](xref:Microsoft.PowerShell.Management.Get-Item)和 [取消阻止文件](xref:Microsoft.PowerShell.Utility.Unblock-File)。

> [!NOTE]
> 下载文件的其他方法可能不会将文件标记为来自 Internet 区域。 示例包括：
>
> - `curl.exe`
> - `Invoke-RestMethod`
> - `Invoke-WebRequest`

## <a name="execution-policy-on-windows-server-core-and-window-nano-server"></a>Windows Server Core 和 Window Nano Server 上的执行策略

在某些情况下，当 PowerShell 6 在 Windows Server Core 或 Windows Nano Server 上运行时，执行策略可能会失败并出现以下错误：

```Output
AuthorizationManager check failed.
At line:1 char:1
+ C:\scriptpath\scriptname.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

PowerShell 使用 Windows Desktop Shell 中的 Api (`explorer.exe`) 验证脚本文件的区域。 Windows Shell 在 Windows Server Core 和 Windows Nano Server 上不可用。

如果 Windows 桌面 Shell 不可用或无响应，也可能会在任何 Windows 系统上收到此错误。 例如，在登录过程中，PowerShell 登录脚本可以在 Windows 桌面准备就绪之前开始执行，从而导致失败。

使用 **绕过** 或 **AllSigned** 的执行策略不需要区域检查来避免此问题。

## <a name="see-also"></a>另请参阅

[about_Environment_Variables](about_Environment_Variables.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Signing](about_Signing.md)

[Get-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)

[Pwsh 控制台帮助](about_pwsh.md)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Unblock-File](xref:Microsoft.PowerShell.Utility.Unblock-File)

