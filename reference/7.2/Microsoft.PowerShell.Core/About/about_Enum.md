---
description: '`enum`语句用于声明枚举。 枚举是由一组称为枚举器列表的命名标签组成的不同类型。'
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_enum?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Enum
ms.openlocfilehash: 5572a717bbf9b546a30b227b3baf215196c4145d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597046"
---
# <a name="about-enum"></a>关于枚举

## <a name="short-description"></a>简短说明
`enum`语句用于声明枚举。 枚举是由一组称为枚举器列表的命名标签组成的不同类型。

## <a name="long-description"></a>详细说明

`enum`语句允许您创建一组强类型的标签。 可以在代码中使用该枚举，而不必分析或检查拼写错误。

枚举内部表示为整数，起始值为零。 向列表中的第一个标签分配值0。 剩余的标签用连续数字分配。

在定义中，可以为标签提供任何整数值。 未分配值的标签采用下一个整数值。

## <a name="syntax-basic"></a>Basic) 语法 (

```syntax
enum <enum-name> {
    <label> [= <int-value>]
    ...
}
```

## <a name="usage-example"></a>用例

下面的示例演示可视为媒体文件的对象的枚举。 定义将显式值分配给、、的基础 `music` 值 `picture` `video` 。 紧跟显式赋值后的标签获取下一个整数值。 可以通过将相同的值分配给另一个标签来创建同义词;请参阅： `ogg` 、、、、、或的构造值 `oga` `mogg` `jpg` `jpeg` `mpg` `mpeg` 。

```powershell
enum MediaTypes {
    unknown
    music = 10
    mp3
    aac
    ogg = 15
    oga = 15
    mogg = 15
    picture = 20
    jpg
    jpeg = 21
    png
    video = 40
    mpg
    mpeg = 41
    avi
    m4v
}
```

`GetEnumNames()`方法返回枚举的标签列表。

```powershell
[MediaTypes].GetEnumNames()
unknown
music
mp3
aac
ogg
oga
mogg
picture
jpg
jpeg
png
video
mpg
mpeg
avi
m4v
```

`GetEnumValues()`方法返回枚举的值列表。

```powershell
[MediaTypes].GetEnumValues()
unknown
music
mp3
aac
oga
oga
oga
picture
jpeg
jpeg
png
video
mpeg
mpeg
avi
m4v
```

**注意**： GetEnumNames ( # A1 和 GetEnumValues ( # A3 似乎返回相同的结果。
但是，在内部，PowerShell 将值更改为标签。 仔细阅读列表，你会注意到， `oga` 和在 `mogg` "获取名称" 结果下，但不在、、和的 "获取值" 类似的输出中 `jpg` `jpeg` `mpg` `mpeg` 。

```powershell
[MediaTypes].GetEnumName(15)
oga

[MediaTypes].GetEnumNames() | ForEach-Object {
  "{0,-10} {1}" -f $_,[int]([MediaTypes]::$_)
}
unknown    0
music      10
mp3        11
aac        12
ogg        15
oga        15
mogg       15
picture    20
jpg        21
jpeg       21
png        22
video      40
mpg        41
mpeg       41
avi        42
m4v        43
```

## <a name="enumerations-as-flags"></a>作为标志的枚举

枚举可定义为位标志的集合。
其中，在任何给定点，枚举表示一个或多个已打开的标志。

为了使作为标志的枚举正常工作，每个标签都应具有两个值的幂。

## <a name="syntax-flags"></a>语法 (标志) 

```syntax
[Flags()] enum <enum-name> {
    <label 0> [= 1]
    <label 1> [= 2]
    <label 2> [= 4]
    <label 3> [= 8]
    ...
}
```

## <a name="flags-usage-example"></a>标志用法示例

在下面的示例中，将创建 *FileAttributes* 枚举。

```powershell
[Flags()] enum FileAttributes {
    Archive = 1
    Compressed = 2
    Device = 4
    Directory = 8
    Encrypted = 16
    Hidden = 32
}

[FileAttributes]$file1 = [FileAttributes]::Archive
[FileAttributes]$file1 +=[FileAttributes]::Compressed
[FileAttributes]$file1 +=  [FileAttributes]::Device
"file1 attributes are: $file1"

[FileAttributes]$file2 = [FileAttributes]28 ## => 16 + 8 + 4
"file2 attributes are: $file2"
```

```output
file1 attributes are: Archive, Compressed, Device
file2 attributes are: Device, Directory, Encrypted
```

若要测试特定的是否已设置，可以使用二进制比较运算符 `-band` 。 在此示例中，我们将测试的值为的 **设备** 和 **存档** 属性 `$file2` 。

```
PS > ($file2 -band [FileAttributes]::Device) -eq [FileAttributes]::Device
True

PS > ($file2 -band [FileAttributes]::Archive) -eq [FileAttributes]::Archive
False
```

