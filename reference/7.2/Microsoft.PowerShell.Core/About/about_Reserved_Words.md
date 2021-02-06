---
description: 列出不能用作标识符的保留字，因为它们在 PowerShell 中具有特殊含义。
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_reserved_words?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Reserved_Words
ms.openlocfilehash: 95911e328a50c173235f47a7610393124781555d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603396"
---
# <a name="about-reserved-words"></a>关于保留字

## <a name="short-description"></a>简短说明
列出不能用作标识符的保留字，因为它们在 PowerShell 中具有特殊含义。

## <a name="long-description"></a>详细说明

有些字词在 PowerShell 中具有特殊含义。 如果不使用引号显示这些字词，则 PowerShell 将尝试应用其特殊意义，而不是将其视为字符串。 若要在命令或脚本中使用这些字词作为参数参数，而不调用其特殊含义，请将保留字用引号引起来。

下面是 PowerShell 中的保留字：

```
assembly         exit            process
base             filter          public
begin            finally         return
break            for             sequence
catch            foreach         static
class            from (*)        switch
command          function        throw
configuration    hidden          trap
continue         if              try
data             in              type
define (*)       inlinescript    until
do               interface       using
dynamicparam     module          var (*)
else             namespace       while
elseif           parallel        workflow
end              param
enum             private

(*) These keywords are reserved for future use.
```

几个语言关键字（包括 `Foreach` 、、 `If` `For` 和 `While` ）都有其自己的帮助文章。 若要查看它们，请键入 `Get-Help about_` 并添加关键字。 例如，若要获取有关该语句的信息 `Foreach` ，请键入：

```powershell
Get-Help about_ForEach
```

有关 `Filter` 语句或语句语法的信息 `Return` ，请键入：

```powershell
Get-Help about_Functions
```

有关其他保留字的信息，请键入：

```powershell
Get-Help <Reserved_Word>
```

> [!NOTE]
> 并非每个保留字都有其自己的帮助文章。 如果不 `Get-Help` 返回项目，则可以使用以下命令搜索与保留字相关的文章：
>
> ```powershell
> Get-Help <Reserved_Word> -Category:HelpFile
> ```

## <a name="see-also"></a>另请参阅

- [about_Command_Syntax](about_Command_Syntax.md)
- [about_Language_Keywords](about_Language_Keywords.md)
- [about_Parsing](about_Parsing.md)
- [about_Quoting_Rules](about_Quoting_Rules.md)
- [about_Script_Blocks](about_Script_Blocks.md)
- [about_Special_Characters](about_Special_Characters.md)
