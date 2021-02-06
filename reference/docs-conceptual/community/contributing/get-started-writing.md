---
title: 开始参与撰写 PowerShell 文档
description: 本文简要介绍如何作为参与者开始参与撰写 PowerShell 文档。
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: ddcbf79de1ab05b901ce1abd67f65b2524ed164d
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/12/2020
ms.locfileid: "99597841"
---
# <a name="get-started-contributing-to-powershell-documentation"></a>开始参与撰写 PowerShell 文档

本文简要介绍如何作为参与者开始参与撰写 PowerShell 文档。

## <a name="powershell-docs-structure"></a>PowerShell-Docs 结构

[PowerShell 文档存储库][psdocs]分为两组内容：引用和概念。

### <a name="reference-content"></a>参考内容

参考内容是 PowerShell cmdlet 参考，适用于 PowerShell 中提供的 cmdlet。
在版本文件夹 (5.1、7.0、7.1 和 7.2) 中收集 [引用][ref] 。 此内容仅包含 PowerShell 随附的模块的 cmdlet 参考。 此内容还用于创建由 cmdlet 显示的帮助信息 `Get-Help` 。

### <a name="conceptual-content"></a>概念内容

概念性文档包含以下内容：

- 发行说明
- 设置说明
- 示例脚本和操作指南文章
- DSC 文档
- SDK 文档

[概念文档][conceptual]不按版本进行组织。 每个 PowerShell 版本都将显示所有项目。 我们正在努力创建特定版本的文章。 如果文档中提供了该功能，则将使用相应的信息更新本指南。

> [!NOTE]
> 在添加、删除或重命名概念项目时，必须更新和包含在拉取请求中的目录。

## <a name="creating-new-articles"></a>创建新项目

必须为要提供的任何新文档创建 GitHub 问题。 检查现有问题，确保不会重复工作。 已分配的问题被视为 `in progress` 。 如果你想要协作解决某个问题，请联系分配给该问题的人员。

类似于 PowerShell [RFC 过程][rfc]，在编写内容之前创建问题。 此问题可确保不会浪费时间和精力处理 PowerShell-Docs 团队拒绝的工作。 此问题使我们能够与你联系，以确定内容的范围以及它在 PowerShell 文档中的位置。 所有文章都必须包含在目录中 (TOC) 。 建议的目录位置应包含在问题讨论中。

> [!NOTE]
> 引用内容的目录由发布系统自动生成。 无需更新目录。

## <a name="updating-existing-articles"></a>更新现有项目

在适用的情况下，在此存储库中维护的所有 PowerShell 版本中复制 cmdlet 引用文章。 在报告有关 cmdlet 引用或项目的问题时 `About_` ，你必须指定此问题影响的版本。 GitHub 中的问题模板包含版本的清单。 使用此复选框可指定受影响的内容版本。

查看文章的所有版本，查看其他版本是否需要相同的更改。 对文件的每个版本应用相应的更改。

## <a name="localized-content"></a>本地化内容

PowerShell 文档以英文编写，翻译为17个其他语言。 英语内容存储在名为的 GitHub 存储库中 `MicrosoftDocs/PowerShell-Docs` 。 对于每种语言，本地化内容都存储在单独的存储库中。 存储库使用相同的 basename，但将区域设置名称添加到结尾。 例如， `MicrosoftDocs/PowerShell-Docs.de-de` 包含转换为德语的内容。

通常，问题和更改应提交到英语存储库。 所有翻译首先从英语内容开始。 我们同时使用人工翻译和机器翻译。

| 转换方法  |                              语言                               |
| ------------------- | -------------------------------------------------------------------- |
| 人工翻译   | 反 DE，es，fr-fr，it，a，ja-jp，ko-KR，pt-BR，ru-RU，zh-chs，zh-chs |
| 机器翻译 | cs-CZ、hu-HU、nl-NL、pl、pt、sv-SE、tr-TR                      |

计算机翻译翻译的内容可能并不总是产生正确的词选择和语法。 如果你在翻译时发现任何语言出现错误，而不是本文的技术细节，请在本地化存储库中提出问题。 说明为什么您认为翻译不正确。 我们的本地化团队查看并响应这些问题。

## <a name="next-steps"></a>后续步骤

可以通过两种常见方式在 GitHub 中提交更改。 以下两种方法都在中心参与者指南中进行了介绍：

1. 可以快速编辑 GitHub web 界面中的 [现有文档](/contribute/#quick-edits-to-existing-documents) 。
1. 使用 [完整 GitHub 工作流][making-changes] 来添加新项目、更新多个文件或其他大更改。

在开始任何更改之前，应创建 PowerShell-Docs 存储库的分支。 应在复制 PowerShell 文档的工作分支中进行更改。如果使用 GitHub 中的 **快速编辑** 方法，则会为你处理这些步骤。 如果使用的是 **完整 GitHub 工作流**，则必须将设置为在 [本地运行][fork]。

两种方法都是通过创建拉取请求 (PR) 结束。 有关详细信息和最佳实践，请参阅 [提交拉取请求](pull-requests.md) 。

<!--link refs-->
[conceptual]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference/docs-conceptual
[fork]: /contribute/get-started-setup-local#fork-the-repository
[making-changes]: /contribute/how-to-write-workflows-major#making-your-changes
[psdocs]: https://github.com/MicrosoftDocs/PowerShell-Docs
[ref]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference
[rfc]: https://github.com/PowerShell/powershell-rfc/blob/master/RFC0000-RFC-Process.md
