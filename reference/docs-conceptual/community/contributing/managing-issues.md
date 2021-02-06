---
title: 如何管理问题
description: 本文介绍 PowerShell-Docs 团队如何管理问题。
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 72267137a2657f51e5f616113adf92d80647acad
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/12/2020
ms.locfileid: "99597429"
---
# <a name="how-we-manage-issues"></a>如何管理问题

本文记录了如何管理 PowerShell-Docs 存储库中的问题。 本文旨在为 PowerShell-Docs 团队成员提供帮助。 它在此处发布，为公共参与者提供流程透明性。

## <a name="sources-of-issues"></a>问题源

- 社区参与者
- 内部参与者
- 来自社交媒体渠道的注释转录
- 通过 Docs 反馈窗体提供的反馈

## <a name="response-time-targets"></a>响应时间目标

80% 的新问题将在3个工作日内结束。

- 已会审-1 个工作日内
- 修复或更改-10 个工作日内

### <a name="labeling--milestones"></a>标记和里程碑

#### <a name="label-types"></a>标签类型

|   类型   | 说明                                                         |
| -------- | ------------------------------------------------------------------- |
| 区域     | 用于指示问题正在讨论哪个部分的 PowerShell 或文档。<br>有助于功能所有者查找其功能的问题。 |
| 问题    | 指示问题的类型                                         |
| 优先级 | 指示问题的优先级。 值范围 0 (高) -4 (低)   |
| 状态   | 指示工作项的状态或它的关闭原因          |
| 标记      | 用于附加分类的标签                        |
| 等待  | 指示我们正在等待某人或某个其他事件         |

#### <a name="milestones"></a>里程碑

应使用相应的里程碑标记的问题和 PR。 如果此问题不适用于特定版本，则不会使用里程碑。 应将尚未合并到 PowerShell 代码库中的更改的 Pr 和相关问题分配给 **未来** 里程碑。 合并代码更改后，将里程碑更改为相应的版本。

|    里程碑     |                    说明                     |
| ---------------- | -------------------------------------------------- |
| 7.0.0            | 与 PowerShell 7.0 相关的工作项               |
| 7.1.0            | 与 PowerShell 7.1 相关的工作项               |
| 7.2.0            | 与 PowerShell 7.2 相关的工作项               |
| 未来           | 工作项 PowerShell 的未来版本          |

## <a name="triage-process"></a>会审过程

PowerShell 文档团队成员每天查看问题，并在遇到新问题时对其进行会审。 团队每周都要讨论需要会审或保持未解决的问题。

### <a name="misplaced-product-feedback"></a>错放的产品反馈

- 输入将客户重定向到正确反馈通道的注释。
- 可选：将问题复制到相应的产品反馈位置，将链接添加到复制的项，并关闭问题。 请勿将问题复制到 UserVoice。

  PowerShell 问题的默认位置是 [https://github.com/PowerShell/PowerShell/issues/new/choose](https://github.com/PowerShell/PowerShell/issues/new/choose) 。

  以下主题区域对于问题有不同的位置：

  | 主题 |                                                     产品反馈 URL                                                     |
  | -------- | ---------------------------------------------------------------------------------------------------------------------------- |
  | dsc      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |
  | 库  | [https://github.com/powershell/powershellgallery/issues/new](https://github.com/powershell/powershellgallery/issues/new)     |
  | jea      | [https://github.com/powershell/jea/issues/new](https://github.com/powershell/jea/issues/new)                                 |
  | wmf      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |

### <a name="support-requests"></a>支持请求

- 如果支持问题很简单，请礼貌答复并关闭问题。
- 如果问题较为复杂，或者提交者回复了更多问题，请将这些问题重定向到论坛和支持渠道。 用于重定向到论坛的建议文本：

  ```Markdown
  > This is not the right forum for these kinds of questions. Try posting your question in a
  > community support forum. For a list of community forums see:
  > https://docs.microsoft.com/powershell/scripting/community/community-support
  ```

### <a name="code-of-conduct-violations"></a>行为准则冲突

- 编辑问题以删除任何冒犯性内容（如有必要）。
- 输入一条注释，指示此问题是垃圾邮件，关闭问题，然后将其锁定以防止进一步注释。
- 每周的会审中都应该讨论每个冲突，以确定需要进一步操作 (向 GitHub 或 Microsoft 合法) 报告。
