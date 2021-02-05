---
title: 编辑清单
description: 这是用于编辑 PowerShell 文档的规则的汇总列表。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: b5baf7366239084779d34e23f218e5e6222ed1a3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "81624731"
---
# <a name="editors-checklist"></a>编辑器的清单

这是在撰写新文章或更新现有文章时要应用的规则的摘要。 有关这些规则的详细说明和示例，请参阅参与者指南中的其他文章。

## <a name="metadata"></a>元数据

- `ms.date`：格式必须为 MM/DD/YYYY 
  - 更改有重大更新或真实更新时的日期
    - 重新组织文章
    - 修复事实错误
    - 添加新信息
  - 如果更新无意义，请不要更改日期
    - 修复拼写错误和格式设置
- `title`：包含空格的 43-59 个字符的唯一字符串
  - 不包括站点标识符（它是自动生成的）
  - 使用句首大写形式 - 仅大写第一个单词和所有专有名词
- `description`设置用户帐户 ：包含空格的 115-145 个字符 - 此摘要显示在搜索结果中

## <a name="formatting"></a>格式设置

- 段落中内联显示的反引号语法元素
  - Cmdlet 名称 `Verb-Noun`
  - 变量 `$counter`
  - 语法示例 `Verb-Noun -Parameter`
  - 文件路径 `C:\Program Files\PowerShell`、`/usr/bin/pwsh`
  - 不应在文档中单击的 URL
  - 属性值或参数值
- 对属性名称、参数名称、类名称、模块名称、实体名称、对象或类型名称使用粗体
  - 粗体用于语义标记，而不用于强调
  - 粗体 - 使用星号 `**`
- 斜体 - 使用下划线 `_`
  - 仅用于强调，而不用于语义标记
- 100 列处的换行符（对于 about_Topics  ，则为 80）
- 无硬 Tab - 仅使用空格
- 行中无尾随空格

### <a name="headers"></a>头文件

- H1 是第一个 - 每篇文章中只有一个 H1
- 仅使用 [ATX 标头](https://github.github.com/gfm/#atx-headings)
- 对所有标头使用句首大写形式
- 不要跨级别 - 如果没有 H2，则没有 H3
- H3 或 H4 的最大深度
- 前后空行
- PlatyPS 强制执行其架构中的特定标头 - 不要添加或删除标头

### <a name="code-blocks"></a>代码块

- 前后空行
- 使用已标记的代码栅栏 - powershell、输出或其他相应的语言 ID  
- 未标记的栅栏 - 语法块或其他 shell
- 将输出置于单独的代码块中，除了一些简单的示例，在这些示例中，你不打算让读者使用“复制”按钮 
- 请参阅[支持的语言](/contribute/code-in-docs#supported-languages)的列表

### <a name="lists"></a>列表

- 正确缩进
- 第一项之前和最后一项之后的空行
- 项目符号 - 使用连字符 (`-`)，而不是星号 (`*`) - 很容易与强调混淆
- 对于带编号的列表，所有数字都为“1.”

## <a name="terminology"></a>术语

- PowerShell 与Windows PowerShell 与PowerShell Core
- 请参阅[产品术语](powershell-style-guide.md#product-terminology)

## <a name="cmdlet-reference-examples"></a>Cmdlet 参考示例

- cmdlet 参考中必须至少有一个示例
- 示例应仅是足以演示用法的代码
- PowerShell 语法
  - 使用 cmdlet 和参数的全名 - 无别名
  - 当命令行太长时，展开参数
  - 避免使用续行符反引号 - 仅在必要时使用
- 删除或简化 PowerShell 提示符 (`PS>`)（示例需要时除外）
- Cmdlet 参考示例必须遵循以下 PlatyPS 架构

  ~~~Markdown
  ### Example 1 - Descriptive title

  Zero or more short descriptive paragraphs explaining the context of the example followed by one or
  more code blocks. Recommend at least one and no more than two.

  ```powershell
  ... one or more PowerShell code statements ...
  ```

  ```Output
  Example output of the code above.
  ```

  Zero or more optional follow up paragraphs that explain the details of the code and output.
  ~~~

- 不要在代码块之间放置段落。 所有描述性内容必须位于代码块之前或之后。

## <a name="linking-to-other-documents"></a>链接到其他文档

- 在 docset 之外或在 cmdlet 参考和概念之间链接
  - 链接到 docs.microsoft.com 时使用相对 URL（删除 `https://docs.microsoft.com/en-us`）
  - 不在 Microsoft 属性的 URL 中包含区域设置（例如， 从 URL 中删除 `/en-us`）
  - 外部网站的所有 URL 都应使用 HTTPS，除非它对目标站点无效
- 在 docset 中
  - 链接到文件路径（例如 `../folder/file.md`）
  - 所有文件路径都使用正斜杠 (`/`) 字符
- 图像链接应包含唯一的替换文字
