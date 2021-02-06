---
title: PowerShell-Docs 风格指南
description: 本文介绍用于撰写 PowerShell 文档的风格规则。
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 6f23f63cffc9fed9cbbcf84539875bfaf4247732
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/12/2020
ms.locfileid: "99596816"
---
# <a name="powershell-docs-style-guide"></a>PowerShell-Docs 风格指南

本文介绍特定于 PowerShell-Docs 内容的风格指南。 它以 [概述](overview.md#get-started-writing-docs)中概述的信息为基础。

## <a name="product-terminology"></a>产品术语

PowerShell 有多个变体。

- **PowerShell** - 这是默认名称。 我们将 PowerShell 7 和更高版本视为真实的 PowerShell。
- **PowerShell Core** - 基于 .NET Core 生成的 PowerShell。 术语 " **核心** " 的使用应限制为需要在 Windows PowerShell 中区分它的情况。
- **Windows PowerShell** - 基于 .NET Framework 生成的 PowerShell。 Windows PowerShell 仅对 Windows 提供，并且需要完整的 Framework。

  通常，可以将文档中的 "Windows PowerShell" 的引用更改为 _PowerShell_。
  讨论特定于 _Windows powershell_ 的行为时应使用 "windows powershell"。

相关产品

- **) Visual Studio Code (VS Code** -这是 Microsoft 的免费开源编辑器。 首次提及时，应使用完整名称。 之后，可以使用 VS Code  。 不要使用 "VSCode"。
- 适用于 Visual Studio Code 的 PowerShell 扩展  - 此扩展会将 VS Code 转换为适用于 PowerShell 的首选 IDE。 首次提及时，应使用完整名称。 之后，可以使用 PowerShell 扩展  。
- Azure PowerShell  - 这是用于管理 Azure 服务的 PowerShell 模块的集合。
- Azure Stack PowerShell  - 这是用于管理 Microsoft 混合云解决方案的 PowerShell 模块的集合。

## <a name="markdown-specifics"></a>Markdown 详情

用于生成文档的 Microsoft 开放发布系统 (OPS) 使用 [markdig][] 处理 Markdown 文档。 Markdig 根据最新 [CommonMark][] 规范的规则分析文档。

新的 CommonMark 规范比某些 Markdown 元素的构造要严格得多。 请密切关注本文档中提供的详细信息。

### <a name="blank-lines-spaces-and-tabs"></a>空白行、空格和制表符

在 Markdown 中，空白行还表示块的末尾。 在不同类型的 Markdown 块之间（例如，在段落和列表或标题之间）应该有一个空白行。

在 HTML 中，多个连续的空行呈现为一个空白行。 它们不起作用。
在代码块中，连续的空行中断代码块。

删除行尾的多余空格。

> [!NOTE]
> 间距在 Markdown 中非常重要。 始终使用空格而不是硬制表符。 尾随空格可更改 Markdown 的呈现方式。

### <a name="titles-and-headings"></a>标题

只使用 [ATX 标题][atx]（# 样式，不用 `=` 或 `-` 样式标题）。

- 使用句首大写形式 - 只对专有名词和标题的首个字母使用大写形式
- `#` 与标题的首个字母之间必须有一个空格
- 标题前后应该都留有一个空白行
- 每个文档只有 1 个 H1
- 标题级别应按 1 递增。 不跳过级别
- 请勿在标头中使用粗体或其他标记

### <a name="limit-line-length-to-100-characters"></a>将行长度限制为 100 个字符

这适用于概念性文章和 cmdlet 参考。 限制行长度可以改进 git diff 和历史记录的可读性。 同时也便于其他作者参与撰写文档。

在 Visual Studio Code 中使用 [Reflow Markdown][reflow] 扩展可以轻松地重排段落以适应指定的行长度。

About_topics 限制为 80 个字符。 有关更具体的信息，请参阅 [格式 About_ 文件](#formatting-about_-files)。

### <a name="lists"></a>列表

如果列表包含多个句子或段落，请考虑使用子层标题而不是列表。

列表前后应该都留有一个空白行。

#### <a name="unordered-lists"></a>未排序列表

不要以句点结尾列出项，除非它们包含多个句子。 对于列表项项目符号，使用连字符 (`-`)。 这样可以避免与使用星号 [`*`] 的粗体或斜体标记混淆。 若要在项目符号项下添加段落或其他元素，请插入一个换行符，并使缩进与项目符号后的第一个字符对齐。

例如：

```markdown
This is a list that contain child elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Child bullet item

    Sentence explaining the child bullet.

- Second bullet item
- Third bullet item
```

这是一个列表，其中包含项目符号项下的子元素。

- 第一个项目符号项

  说明第一个项目符号的句子。

  - 子项目符号项

    解释子项目符号的句子。

- 第二个项目符号项
- 第三个项目符号项

#### <a name="ordered-lists"></a>已排序列表

若要在带编号的项下添加段落或其他元素，请使缩进与项编号后的第一个字符对齐。 编号列表中的所有项均应使用数字 `1.`，而不是递增每个项的编号数字值。 Markdown 呈现会自动递增该值。 这使重新排序项目变得更加容易，并使下级内容的缩进标准化。

例如：

```markdown
1. For the first element, insert a single space after the 1. Long sentences should be
   wrapped to the next line and must line up with the first character after the numbered
   list marker.

   To include a second element (like this one), insert a line break after the first
   and align indentations. The indentation of the second element must line up with
   the first character after the numbered list marker. For single digit items, like
   this one, you indent to column 4. For double digits items, for example item number
   10, you indent to column 5.

1. The next numbered item starts here.
```

最终呈现的 Markdown 如下：

1. 对于第一个元素，在 1 之后插入一个空格。 长句应换行到下一行，并且必须与编号列表标记后的第一个字符对齐。

   若要包括第二个元素（如本例所示），请在第一个元素后插入一个换行符，并对齐缩进。 第二个元素的缩进必须与编号列表标记后的第一个字符对齐。 对于这样的一位数的项，缩进到第 4 列。 对于两位数的项（例如项编号 10），缩进到第 5 列。

1. 下一个带编号的项从此处开始。

### <a name="images"></a>映像

用于添加图像的语法如下：

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

其中 `alt text` 是图像的简要说明，`<folder path>` 是图像的相对路径。 必须为视觉障碍人士的屏幕阅读器使用替代文本。

图像应存储在 `media/<article-name>` 包含项目的文件夹中的文件夹内。
不要在项目之间共享图像。 在 `media` 文件夹下创建与文章的文件名相匹配的文件夹。 将该文章的图像复制到该新文件夹。 如果多个文章使用一个图像，则每个图像文件夹都必须具有该图像文件的副本。 这种做法可防止更改一篇文章的图像影响到另一篇文章。

支持下列图像文件类型： `*.png` 、 `*.gif` 、 `*.jpeg` 、 `*.jpg` 、 `*.svg`

### <a name="markdown-extensions-supported-by-open-publishing"></a>公开发布支持 Markdown 扩展

[Microsoft Docs 创作包](/contribute/how-to-write-docs-auth-pack)包含的工具支持发布系统独有的功能。 警报是一种 Markdown 扩展，用于创建在 docs.microsoft.com 上呈现的 blockquotes，颜色和图标突出显示内容的重要性。 支持以下警报类型：

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

这些警报在 docs.microsoft.com 上如下所示：

备注块

> [!NOTE]
> Information the user should notice even if skimming.

Tip 块

> [!TIP]
> Optional information to help a user be more successful.

重要块

> [!IMPORTANT]
> Essential information required for user success.

警告块

> [!CAUTION]
> Negative potential consequences of an action.

警告块

> [!WARNING]
> 操作必然造成的危险后果。

### <a name="hyperlinks"></a>超链接

- 超链接必须使用 Markdown 语法 `[friendlyname](url-or-path)` 。 支持[链接引用][linkref]。
- 发布系统支持三种类型的链接：
  - URL 链接
  - 文件链接
  - 交叉引用链接
- 指向 docs.microsoft.com 上的其他文章的链接必须是站点相对路径
- 除非对于目标站点无效，否则外部网站的所有 Url 都应使用 HTTPS。
- 链接必须具有友好名称，通常为链接项目的标题
- 底部的 " _相关链接_ " 部分中的所有项都应为超链接
- 请勿在超链接的方括号内使用反撇号、粗体或其他标记。
- 当你记录特定的 URI 时，可以使用 Bare Url。 此 URI 必须包含在反撇号中。 例如：

  ```markdown
  By default, if you don't specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content-on-docsmicrosoftcom"></a>链接到 docs.microsoft.com 上的其他内容

- 指向 docs.microsoft.com 上的其他文章的 **URL 链接** 必须是站点相对路径。 创建相对链接的最简单方法是从浏览器复制 URL，然后 `https://docs.microsoft.com/en-us` 从粘贴到 markdown 中的值中删除。 请勿在 Microsoft 属性的 Url 中包含区域设置 (`/en-us` 从 URL) 中删除。 从 URL 中删除任何不必要的查询参数。 应删除的示例：

  - `?view=powershell-5.1` -用于链接到特定版本的 PowerShell
  - `?redirectedfrom=MSDN` -从旧文章重定向到新位置时添加到 URL

  如果需要链接到文档的特定版本，则需要将 `&preserve_view=true` 参数添加到查询字符串。 例如： `?view=powershell-5.1&preserve_view=true`

- **文件链接** 用于从一个引用文章链接到另一个引用文章，或从一个概念文章链接到另一个。 如果需要链接到特定版本的 PowerShell 的参考文章，则必须使用 URL 链接。

  - 文件链接包含相对文件路径 (例如： `../folder/file.md`) 
  - 所有文件路径使用正斜杠 (`/`) 字符

- **交叉引用链接** 是发布系统支持的一项特殊功能。 您可以使用概念文章中的交叉引用链接链接到 .NET API 或 cmdlet 引用。

  有关 .NET API 参考的链接，请参阅中心参与者指南中的 [使用文档](/contribute/how-to-write-links#xref-cross-reference-links) 中的链接。

  指向 cmdlet 引用的链接具有以下格式： `xref:<module-name>.<cmdlet-name>` 。 例如，若要链接到位于 `Get-Content` **Microsoft 的 PowerShell** 模块中的 cmdlet。

  `[Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)`

URL 和文件链接上都允许深层链接。 将定位点添加到目标路径的末尾。
例如：

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

有关详细信息，请参阅 [使用文档中的链接](/contribute/how-to-write-links)。

## <a name="formatting-command-syntax-elements"></a>设置命令语法元素的格式

- 始终将全名用于 cmdlet 和参数。 除非您专门演示别名，否则请避免使用别名。

- 属性、参数、对象、类型名称、类名称和类方法应为 **粗体**。
  - 应将属性和参数值包装在反撇号 (`` ` ``) 中。
  - 使用括号式样式引用类型时，请使用反撇号。 例如： `[System.Io.FileInfo]`

- 语言关键字、cmdlet 名称、函数、变量、本机 Exe、文件路径和内联语法示例应包装在反撇号中 (`` ` ``) 字符。

  例如：

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - 按名称引用参数时，该名称应采用粗体。 演示使用带有连字符前缀的参数时，应使用反引号将参数引起来。 例如：

    ```markdown
    The parameter's name is **Name**, but it's typed as `-Name` when used on the command
    line as a parameter.
    ```

  - 演示外部命令的示例用法时，示例应由反引号引起来。
    始终在本机命令中包含文件扩展名。 例如：

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    包括文件扩展名可确保根据 PowerShell 的命令优先级执行正确的命令。

- 编写概念性文章（而非引用内容）时，cmdlet 名称的第一个实例应超链接到 cmdlet 文档中。 请勿在超链接的方括号内使用反撇号、粗体或其他标记。

  例如：

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  有关详细信息，请参阅本文中的 [超链接](#hyperlinks) 部分。

## <a name="markdown-for-code-samples"></a>Markdown 代码示例

Markdown 支持两种不同的代码样式：

- **代码跨越 (内联)** 由单个反撇号 (`` ` ``) 字符标记。 在段落内而不是作为独立的块中使用。
- **代码块** -由三反撇号 () 字符串括起来的多行块 `` ``` `` 。 代码块还可能在反撇号后面有一个语言标签。 语言标签对代码块的内容启用语法突出显示。

所有代码块都应包含在代码隔离区中。 不要对代码块使用缩进。 Markdown 允许此模式，但它可能会出现问题，应避免此模式。

代码块是一个或多个代码行，反撇号 (`` ``` ``) 代码隔离区。
代码隔离区标记必须位于代码示例前后其自己的行上。 代码块开头的标记可能具有可选的语言标签。 Microsoft 的开放发布系统 (OPS) 使用语言标签来支持语法突出显示功能。

有关支持的语言标记的完整列表，请参阅集中参与者指南中的 [隔离代码块](/contribute/code-in-docs#fenced-code-blocks) 。

OPS 还添加了可将代码块的内容复制到剪贴板的“复制”按钮。 这使你可以快速将代码粘贴到脚本中，以测试代码示例。 但是，并非我们文档中的所有示例都应按原样运行。 一些代码块是 PowerShell 概念的简单阐释。

文档中使用三种类型的代码块：

1. 语法块
1. 说明性示例
1. 可执行示例

### <a name="syntax-code-blocks"></a>语法代码块

语法代码块用于描述命令的语法结构。 不要在代码隔离上使用语言标记。 此示例演示 `Get-Command` cmdlet 所有可能的参数。

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

此示例以通用术语描述 `for` 语句：

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a>演示示例

演示示例用于解释 PowerShell 概念。 它们不会被复制到剪贴板上以执行。 它们最常用于易于键入并易于理解的简单示例。 代码块可以包括 PowerShell 提示符和示例输出。

以下简单示例演示了 PowerShell 比较运算符。 在这种情况下，我们不希望读者复制并运行此示例。

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

### <a name="executable-examples"></a>可执行示例

要复制和执行的复杂示例或示例应使用以下块样式标记：

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

PowerShell 命令显示的输出应包含在 Output 代码块中，以防止语法突出显示。 例如：

~~~markdown
```powershell
Get-Command -Module Microsoft.PowerShell.Security
```

```Output
CommandType  Name                        Version    Source
-----------  ----                        -------    ------
Cmdlet       ConvertFrom-SecureString    3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       ConvertTo-SecureString      3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-CmsMessage              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Credential              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-PfxCertificate          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       New-FileCatalog             3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Protect-CmsMessage          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Test-FileCatalog            3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Unprotect-CmsMessage        3.0.0.0    Microsoft.PowerShell.Security
```
~~~

" **输出** 代码" 标签不是语法突出显示系统支持的官方 "语言"。
但是，此标签非常有用，因为 OPS 会将 "输出" 标签添加到网页上的代码框框架中。 "输出" 代码框没有突出显示的语法。

## <a name="coding-style-rules"></a>编码样式规则

### <a name="avoid-line-continuation-in-code-samples"></a>避免在代码示例中出现行继续符

避免在 PowerShell 代码示例中使用行继续符 (`` ` ``)。 如果行尾出现多余的空格，则很难看到行继续符，并且可能会引发问题。

- 使用 PowerShell 展开缩短具有多个参数的 cmdlet 的行长度。
- 利用 PowerShell 的自然换行机会，如管道 (`|`) 字符、左大括号 (`{`) 、括号 (`(`) 和方括号 (`[`) 。

### <a name="avoid-using-powershell-prompts-in-examples"></a>避免在示例中使用 PowerShell 提示

不建议使用提示字符串，因此应将其限制为旨在说明命令行用法的方案。 对于其中的大多数示例，提示字符串应为 `PS>` 。 此提示与特定于 OS 的指示器无关。

在示例中需要提示，以说明更改提示的命令或显示的路径对于方案非常重要。 下面的示例演示使用注册表提供程序时提示的变化。

```powershell
PS C:\> cd HKCU:\System\
PS HKCU:\System\> dir

    Hive: HKEY_CURRENT_USER\System

Name                   Property
----                   --------
CurrentControlSet
GameConfigStore        GameDVR_Enabled                       : 1
                       GameDVR_FSEBehaviorMode               : 2
                       Win32_AutoGameModeDefaultProfile      : {2, 0, 1, 0...}
                       Win32_GameModeRelatedProcesses        : {1, 0, 1, 0...}
                       GameDVR_HonorUserFSEBehaviorMode      : 0
                       GameDVR_DXGIHonorFSEWindowsCompatible : 0
```

### <a name="dont-use-aliases-in-examples"></a>不要在示例中使用别名

使用所有 cmdlet 和参数的完整名称，除非专门记录别名。
Cmdlet 和参数名称必须使用正确的 [Pascal 大小写][] 名称。

### <a name="using-parameters-in-examples"></a>在示例中使用参数

避免使用位置参数。 通常，应始终在示例中包含参数名称，即使参数是位置。 这样可减少在示例中产生混淆的可能性。

## <a name="formatting-cmdlet-reference-articles"></a>格式化 cmdlet 参考文章

Cmdlet 引用文章具有特定的结构。 此结构由 PlatyPS 定义[][]。
Platypus 为 Markdown 中的 PowerShell 模块生成 cmdlet 帮助。 编辑 Markdown 文件后，使用 PlatyPS 创建 `Get-Help` cmdlet 使用的 MAML 帮助文件。

PlatyPS 具有用于 cmdlet 引用的硬编码架构，并且已写入代码中。 [platyPS.schema.md][] 文档尝试描述此结构。 架构冲突会导致生成错误，必须先修复这些错误然后才能接受你撰写的内容。

- 请勿删除任何 ATX 标头结构。 PlatyPS 需要一组特定的标头。
- 输入类型和输出类型标头必须具有类型。 如果该 cmdlet 不接受输入或返回值，则使用值 `None` 。
- 任何段落都可使用内联代码范围。
- 仅在 " **示例** " 部分中允许隔离代码块。

在 Platypus 架构中， **示例** 是 H2 标头。 每个示例都是一个 H3 标头。 在示例中，该架构不允许按段落分隔代码块。 架构允许以下结构：

```
### Example X - Title sentence

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

为每个示例编号并添加简短标题。

例如：

~~~markdown
### Example 1: Get cmdlets, functions, and aliases

This command gets the PowerShell cmdlets, functions, and aliases that are installed on the
computer.

```powershell
Get-Command
```

### Example 2: Get commands in the current session

```powershell
Get-Command -ListImported
```
~~~

## <a name="formatting-about_-files"></a>设置 About_ 文件的格式

`About_*` 文件是以 Markdown 编写的，但以纯文本文件的形式提供。 我们使用 [Pandoc][] 将 Markdown 转换为纯文本。 `About_*` 在所有版本的 PowerShell 和发布工具中，文件的格式都是最兼容的。

基本格式设置指南：

- 将普通行限制为80个字符
- 代码块限制为76个字符
- Blockquotes (和警报) 的范围限制为78个字符
- 使用这些特殊的元字符时 `\` ， `$` 和 `<` ：
  - 在标头中，这些字符必须使用前导字符进行转义， `\` 或使用反撇号 (包含在代码中 `` ` ``) 
  - 在段落中，应将这些字符放入代码跨越。 例如：

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- 表格需要超过76个字符
  - 手动将单元格内容换到多行
  - 在每一行上使用开始和结束 `|` 字符
  - 下面的示例说明了如何正确构造一个表，该表包含在单元内的多个行上进行换行的信息。

    ~~~markdown
    ```
    |Operator|Description                |Example                          |
    |--------|---------------------------|---------------------------------|
    |`-is`   |Returns TRUE when the input|`(get-date) -is [DateTime]`      |
    |        |is an instance of the      |`True`                           |
    |        |specified .NET type.       |                                 |
    |`-isNot`|Returns TRUE when the input|`(get-date) -isNot [DateTime]`   |
    |        |not an instance of the     |`False`                          |
    |        |specified.NET type.        |                                 |
    |`-as`   |Converts the input to the  |`"5/7/07" -as [DateTime]`        |
    |        |specified .NET type.       |`Monday, May 7, 2007 12:00:00 AM`|
    ```
    ~~~

    > [!NOTE]
    > 76列限制仅适用于 `About_*` 主题。 你可以使用概念或 cmdlet 参考文章中的宽列。

## <a name="next-steps"></a>后续步骤

[编辑清单](editorial-checklist.md)

<!-- link references -->
[atx]: https://github.github.com/gfm/#atx-headings
[CommonMark]: https://spec.commonmark.org/
[markdig]: https://github.com/lunet-io/markdig
[Pandoc]: https://pandoc.org
[Pascal 大小写]: https://en.wikipedia.org/wiki/PascalCase
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[PlatyPS]: https://github.com/powershell/platyps
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
[linkref]: https://spec.commonmark.org/0.29/#link-reference-definitions
