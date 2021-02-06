---
title: 参与 PowerShell 文档撰写
description: 本文概述了参与 PowerShell 文档撰写所需的步骤。
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 9fbdafa023eac80340437f30d2d6925a1a4ed3cb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "99596610"
---
# <a name="contributing-to-powershell-documentation"></a>参与 PowerShell 文档撰写

感谢你对 PowerShell 的支持！

参与者指南是一系列文章，介绍了在 Microsoft 创建文档时使用的工具和过程。 其中一些指南涵盖了发布到 [docs.microsoft.com][docs] 的任何文档集共有的信息。 一些指南专门介绍如何编写 PowerShell 文档。

在汇总的[参与者指南][contribute]中提供了一些常见文章。 本文介绍特定于 PowerShell 的指南。

## <a name="ways-to-contribute"></a>供稿途径

有两种供稿途径。 无论你使用哪种途径，我们都深表感谢。

- [提出问题][file-an-issue]有助于我们发现文档中的问题和缺陷。 有时，这些问题比较棘手，需要进一步调查研究。 在解决问题的过程中，我们能够针对问题展开讨论，并制定满意的解决方法。

- 将[拉取请求提交](pull-requests.md)到添加或更改内容是一个更复杂的过程。
  以下信息概述了将内容提交到文档会用到的工具、流程和标准。

## <a name="prepare-to-make-a-contribution"></a>准备参与撰写文档

参与撰写文档需要一个 GitHub 帐户。 使用下列清单来安装和配置发布所需的工具。

1. [注册 GitHub](/contribute/get-started-setup-github)
1. [安装 Git 和 Markdown 工具](/contribute/get-started-setup-tools)
1. [安装 Docs 创作包](/contribute/how-to-write-docs-auth-pack)
1. [安装 Posh-Git][posh-git] - 不是必需的，但建议安装
1. [设置本地 Git 存储库](/contribute/get-started-setup-local)
1. [巩固 Git 和 GitHub 基础知识](/contribute/git-github-fundamentals)

## <a name="get-started-writing-docs"></a>开始编写代码

可以通过两种方法来参与文档更改：

1. [快速编辑现有文档](/contribute/#quick-edits-to-existing-documents)
   - 少量更正、修正错别字或添加少量内容
1. [文档的完整 GitHub 工作流](/contribute/how-to-write-workflows-major)
   - 大篇幅更改、多个版本、添加或更改图像或撰写新文章

另外，请阅读汇总的《参与者指南》中的[撰写要领](/contribute/style-quick-start)部分。 另一个不错的资源是 [Microsoft 写作风格指南][style-guide]。 《Microsoft 写作风格指南》旨在帮助编辑人员、技术作者、开发人员、市场营销人员以及 IT 部门中的其他任何人编写更好的内容。

docs.microsoft.com [使用条款][terms-of-use]涵盖了公共存储库中对文档和代码示例所做的较小的更改和说明。

进行重大更改时，请使用完整的 GitHub 工作流。 如果你不是 Microsoft 的员工，重大更改会在拉取请求中生成一个注释，要求你提交在线[供稿许可协议 (CLA)][cla]。 你需要先填写这份在线表单，然后我们才能查看或接受拉取请求。

## <a name="code-of-conduct"></a>行为准则

发布到 docs.microsoft.com 的所有存储库均采用 [Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)或 [.NET Foundation 行为准则](https://dotnetfoundation.org/code-of-conduct)。 有关详细信息，请参阅[行为准则常见问题解答](https://opensource.microsoft.com/codeofconduct/faq/)。

## <a name="next-steps"></a>后续步骤

以下文章涵盖特定于 PowerShell 文档的信息。 对于与汇总的《参与者指南》中的指南重叠之处，我们将说明这些规则对于 PowerShell 内容有何不同。

请参阅以下文档：

- [如何提出问题](file-an-issue.md)
- [开始编写文档](get-started-writing.md)
- [提交拉取请求](pull-requests.md)
- [PowerShell-Docs 风格指南](powershell-style-guide.md)

其他资源

- [编辑清单](editorial-checklist.md)
- [如何管理问题](managing-issues.md)
- [如何管理拉取请求](managing-pull-requests.md)

<!--link refs-->
[cla]: https://cla.microsoft.com/
[contribute]: /contribute/
[docs]: https://docs.microsoft.com/
[file-an-issue]: file-an-issue.md
[posh-git]: https://www.powershellgallery.com/packages/posh-git
[psdocs]: /powershell
[style-guide]: /style-guide/welcome/
[terms-of-use]: /legal/termsofuse
