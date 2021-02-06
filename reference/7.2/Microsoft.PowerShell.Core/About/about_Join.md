---
description: 描述联接运算符 ( 联接) 如何将多个字符串合并为一个字符串。
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_join?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Join
ms.openlocfilehash: d76e95aaeca1b5b94bb1a2216576a985ffb209c0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597849"
---
# <a name="about-join"></a>关于联接

## <a name="short-description"></a>简短说明
描述联接运算符 ( 联接) 如何将多个字符串合并为一个字符串。

## <a name="long-description"></a>详细说明

联接运算符将一组字符串连接成一个字符串。 字符串将按照它们在命令中出现的顺序追加到结果字符串。

### <a name="syntax"></a>语法

下图显示了联接运算符的语法。

```powershell
-Join <String[]>
<String[]> -Join <Delimiter>
```

#### <a name="parameters"></a>参数

String []-指定要联接的一个或多个字符串。

分隔符-指定在串联的字符串之间放置的一个或多个字符。 默认值为 "" )  ( 分隔符。

备注

一元联接运算符 ( 联接 <string [] >) 的优先级高于逗号。 因此，如果您将逗号分隔的字符串列表提交给一元联接运算符，则在第一个逗号) 之前仅 (第一个字符串提交到联接运算符。

若要使用一元联接运算符，请将字符串括在括号中，或将字符串存储在变量中，然后提交要联接的变量。

例如：

```powershell
-join "a", "b", "c"
a
b
c

-join ("a", "b", "c")
abc

$z = "a", "b", "c"
-join $z
abc
```

### <a name="examples"></a>示例

下面的语句联接了三个字符串：

```powershell
-join ("Windows", "PowerShell", "2.0")
WindowsPowerShell2.0
```

下面的语句联接由空格分隔的三个字符串：

```powershell
"Windows", "PowerShell", "2.0" -join " "
Windows PowerShell 2.0
```

以下语句使用多字符分隔符来联接三个字符串：

```powershell
$a = "WIND", "S P", "ERSHELL"
$a -join "OW"
WINDOWS POWERSHELL
```

下面的语句将下一个字符串中的行联接到一个字符串中。 由于此字符串是一个字符串，因此必须先拆分此字符串中的行，然后才能联接它们。 您可以使用此方法重新加入已保存在以下字符串中的 XML 文件中的字符串：

```powershell
$a = @'
a
b
c
'@

(-split $a) -join " "
a b c
```

## <a name="see-also"></a>另请参阅

[about_Operators](about_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Split](about_Split.md)

