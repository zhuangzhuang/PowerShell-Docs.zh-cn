---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: Just Enough Administration (JEA) 概述
description: JEA 是一项安全技术，通过它可以对 PowerShell 管理的任何内容进行委托管理。
ms.openlocfilehash: cc1c49960e274b58635c1ca4e6769a54c3c7ded6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501705"
---
# <a name="just-enough-administration"></a>Just Enough Administration

Just Enough Administration (JEA) 是一项安全技术，委派的管理员可通过它执行由 PowerShell 管理的任意操作。 使用 JEA，你可以：

- 减少计算机上的管理员数量，使用虚拟帐户或组托管服务帐户代表普通用户执行特权操作。
- 通过指定用户可运行的 cmdlet、函数和外部命令，**限制用户可执行的操作**。
- 使用准确显示用户在会话中所执行命令的脚本和日志，**更好地了解你的用户进行的操作**。

**JEA 为何很重要？**

用于管理服务器的高特权帐户会造成严重的安全风险。 如果攻击者破坏这些帐户其中之一，他们可在组织中启动[横向攻击](https://aka.ms/pth)。 每个遭到入侵的帐户都会向攻击者提供访问更多帐户和资源的权限，使他们离窃取公司机密、发起拒绝服务攻击等更近一步。

而且，删除管理特权有时也并不容易。 考虑以下常见场景，即在与 Active Directory 域控制器相同的计算机上安装了 DNS 角色。 DNS 管理员需要本地管理员特权才能解决 DNS 服务器方面的问题。 但为此，你必须让这些管理员成为权限较高的域管理员安全组的成员。 该方法将有效地给予 DNS 管理员对整个域的控制全以及对该计算机上所有资源的访问权。

JEA 通过“最小特权”原则来解决此问题。 通过 JEA，可为 DNS 管理员配置管理终结点，使其仅能够访问完成工作所需的 PowerShell 命令。 这意味着你可以提供适当的访问权限以修复中毒的 DNS 缓存或重启 DNS 服务器，而无需无意间授予他们对 Active Directory 的权限，或授予他们浏览文件系统、运行具有潜在危险的脚本的权限。 更棒的是，将 JEA 会话配置为使用具有临时特权的虚拟帐户时，DNS 管理员可使用非管理员凭据连接到服务器，而且仍可运行通常需要管理员特权的命令。 JEA 使你能够从具有广泛权限的本地/域管理员角色中删除用户，并谨慎控制他们可在每台计算机上执行的操作。

## <a name="next-steps"></a>后续步骤

要详细了解 JEA 的使用要求，请参阅[先决条件](prerequisites.md)一文。

## <a name="samples-and-dsc-resource"></a>示例和 DSC 资源

示例 JEA 配置和 JEA DSC 资源可以在 [JEA GitHub 存储库](https://github.com/PowerShell/JEA)中找到。
