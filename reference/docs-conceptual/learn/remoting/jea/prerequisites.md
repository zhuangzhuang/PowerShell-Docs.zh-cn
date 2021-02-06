---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 先决条件
description: 本文介绍使用 JEA 前必须满足的先决条件。
ms.openlocfilehash: 5cc70a06887a2d0a840cc83117f865d3148056e1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501722"
---
# <a name="prerequisites"></a>先决条件

Just Enough Administration 是 PowerShell 5.0 及更高版本随附的功能。 本文介绍使用 JEA 前必须满足的先决条件。

## <a name="check-which-version-of-powershell-is-installed"></a>查看安装的 PowerShell 版本类型

若要查看系统上安装的 PowerShell 版本类型，请查看 Windows PowerShell 提示符中的 `$PSVersionTable` 变量。

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

JEA 适用于 PowerShell 5.0 及更高版本。 要使用完整功能，建议安装适用于系统的 PowerShell 最新版。 下表介绍了 JEA 在 Windows Server 上的可用性：

| 服务器操作系统 |                JEA 可用性                |
| ----------------------- | ---------------------------------------------- |
| Windows Server 2016 及更高版本    | 已预安装                                   |
| Windows Server 2012 R2  | 包含 WMF 5.1 的完整功能                |
| Windows Server 2012     | 包含 WMF 5.1 的完整功能                |
| Windows Server 2008 R2  | 减少了功能<sup>1</sup>（如果 WMF 5.1 已安装） |

此外，还可以在家庭或工作计算机上使用 JEA：

| 客户端操作系统 |                   JEA 可用性                   |
| ----------------------- | ---------------------------------------------------- |
| Windows 10 1607 及更高版本        | 已预安装                                         |
| Windows 10 1603 版、1511 版   | 已预安装，但减少了功能<sup>2</sup> |
| Windows 10 1507 版         | 不可用                                        |
| Windows 8、8.1          | 包含 WMF 5.1 的完整功能                      |
| Windows 7               | 减少了功能<sup>1</sup>（如果 WMF 5.1 已安装）       |

- <sup>1</sup> 无法将 JEA 配置为在 Windows Server 2008 R2 或 Windows 7 上使用组托管服务帐户。 *支持* 虚拟帐户和其他 JEA 功能。

- <sup>2</sup> Windows 10 版本 1511 和 1603 不支持以下 JEA 功能：

  - 作为组托管服务帐户运行
  - 会话配置中的条件访问规则
  - 用户驱动器
  - 授予对本地用户帐户的访问权限

  若要获取对这些功能的支持，请将 Windows 更新到 1607 版（周年更新）或更高版本。

### <a name="install-windows-management-framework"></a>安装 Windows Management Framework

如果运行的是较旧版本的 PowerShell，则可能需要使用最新的 Windows Management Framework (WMF) 更新来更新系统。 有关详细信息，请参阅 [WMF 文档](/powershell/scripting/wmf/overview)。

建议在升级所有服务器之前，测试工作负载与 WMF 的兼容性。

Windows 10 用户需安装最新功能更新才能获取当前版本的 Windows PowerShell。

## <a name="enable-powershell-remoting"></a>启用 PowerShell 远程处理

PowerShell 远程处理提供了构建 JEA 的基础。 必须先确保 PowerShell 远程处理功能已启用且受到适当保护，然后才能使用 JEA。 有关详细信息，请参阅 [WinRM 安全性](/powershell/scripting/learn/remoting/winrmsecurity)。

在 Windows Server 2012、2012 R2 和 2016 中，默认启用 PowerShell 远程处理。 可通过在提升的 PowerShell 窗口中运行以下命令来启用 PowerShell 远程处理。

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>启用 PowerShell 模块和脚本块日志记录（可选）

执行以下步骤将为系统上的所有 PowerShell 操作启用日志记录。 PowerShell 模块日志记录不是 JEA 必需的，但建议启用日志记录，以确保在中心位置记录用户运行的命令。

可使用组策略配置 PowerShell 模块日志记录策略。

1. 在工作站上打开“本地组策略编辑器”，或在 Active Directory 域控制器中，打开“组策略管理控制台”中的“组策略对象”
2. 导航到“计算机配置\\管理模板\\Windows 组件\\Windows PowerShell”
3. 双击“打开模块日志记录”
4. 单击“启用”
5. 在“选项”部分中，单击“模块名称”旁的“显示”
6. 在弹出窗口中键入 `*`，记录所有模块的命令。
7. 单击“确定”设置策略
8. 双击“打开 PowerShell 脚本块日志记录”
9. 单击“启用”
10. 单击“确定”设置策略
11. （仅在已加入域的计算机上）运行 `gpupdate` 或等待组策略处理更新后的策略，然后应用相应设置

也可通过“组策略”启用系统范围的 PowerShell 脚本。

## <a name="next-steps"></a>后续步骤

[创建角色功能文件](role-capabilities.md)

[创建会话配置文件](session-configurations.md)

## <a name="see-also"></a>另请参阅

[WinRM 安全性](/powershell/scripting/learn/remoting/winrmsecurity)

[PowerShell ♥ 蓝队](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
