---
description: 介绍 PowerShell 脚本语言中的关键字。
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_keywords?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Keywords
ms.openlocfilehash: 4136e5fe6b0e3ad2ba1ec41d2dc9a8fba7b88f56
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597029"
---
# <a name="about-language-keywords"></a>关于语言关键字

## <a name="short-description"></a>简短说明
介绍 PowerShell 脚本语言中的关键字。

## <a name="long-description"></a>详细说明

PowerShell 包含以下语言关键字。 有关详细信息，请参阅关键字的 "关于" 主题和表后面的信息。

关键字     | 参考
---         | ---
开始       | [about_Functions](about_Functions.md)， [about_Functions_Advanced](about_Functions_Advanced.md)
中断       | [about_Break](about_Break.md)， [about_Trap](about_Trap.md)
捕获       | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
实例       | [about_Classes](about_Classes.md)
继续    | [about_Continue](about_Continue.md)， [about_Trap](about_Trap.md)
数据        | [about_Data_Sections](about_Data_Sections.md)
定义      | 保留以供将来使用
应做事项          | [about_Do](about_Do.md)， [about_While](about_While.md)
DynamicParam| [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)
Else        | [about_If](about_If.md)
Elseif      | [about_If](about_If.md)
结束         | [about_Functions](about_Functions.md)， [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)
枚举        | [about_Enum](about_Enum.md)
退出        | [本主题中所述](#exit)
筛选器      | [about_Functions](about_Functions.md)
最终     | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
For         | [about_For](about_For.md)
ForEach     | [about_ForEach](about_ForEach.md)
From        | 保留以供将来使用
函数    | [about_Functions](about_Functions.md)， [about_Functions_Advanced](about_Functions_Advanced.md)
Hidden      | [about_Hidden](about_Hidden.md)
如果          | [about_If](about_If.md)
在          | [about_ForEach](about_ForEach.md)
Param       | [about_Functions](about_Functions.md)
过程     | [about_Functions](about_Functions.md)， [about_Functions_Advanced](about_Functions_Advanced.md)
返回      | [about_Return](about_Return.md)
Static      | [about_Classes](about_Classes.md)
交换机      | [about_Switch](about_Switch.md)
Throw       | [about_Throw](about_Throw.md)， [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)
Trap        | [about_Trap](about_Trap.md)、 [about_Break](about_Break.md) [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
尝试         | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
Until       | [about_Do](about_Do.md)
使用       | [about_Using](about_Using.md)， [about_Classes](about_Classes.md)
Var         | 保留以供将来使用
While       | [about_While](about_While.md)， [about_Do](about_Do.md)

语言关键字

### <a name="begin"></a>开始

指定函数体的一部分，以及 `DynamicParam` 、 `Process` 和 `End` 关键字。 `Begin`语句列表在从管道接收任何对象之前运行一次。

语法：

```Syntax
function <name> {
    DynamicParam {<statement list>}
    begin {<statement list>}
    process {<statement list>}
    end {<statement list>}
}
```

### <a name="break"></a>中断

导致脚本退出循环。

语法：

```Syntax
while (<condition>) {
   <statements>
   ...

   break
   ...

   <statements>
}
```

### <a name="catch"></a>捕获

如果在附带的 Try 语句列表中出现错误，则指定要运行的语句列表。 错误类型需要方括号。 第二对方括号指示错误类型是可选的。

语法：

```Syntax
try {<statement list>}
catch [[<error type>]] {<statement list>}
```

### <a name="class"></a>实例

在 PowerShell 中指定新类。

语法：

```Syntax
class <class-name> {
    [[hidden] [static] <property-definition> ...]
    [<class-name>([argument-list>]) {<constructor-statement-list>} ...]
    [[hidden] [static] <method-definition> ...]
}
```

### <a name="continue"></a>继续

使脚本停止运行循环并返回到该条件。 如果满足条件，则脚本将再次开始循环。

语法：

```Syntax
while (<condition>) {
   <statements>
   ...

   continue
   ...

   <statements>
}
```

### <a name="data"></a>数据

在脚本中，定义了一个部分，用于隔离脚本逻辑中的数据。 还可以包含 `If` 语句和一些有限的命令。

语法：

```Syntax
data <variable> [-supportedCommand <cmdlet-name>] {<permitted content>}
```

### <a name="do"></a>应做事项

与 `While` 或关键字一起用作 `Until` 循环构造。 PowerShell 至少运行一次语句列表，这不同于使用的循环 `While` 。

`While` 的语法：

```Syntax
do {<statement list>} while (<condition>)
```

`Until` 的语法：

```Syntax
do {<statement list>} until (<condition>)
```

### <a name="dynamicparam"></a>DynamicParam

指定函数体的一部分，以及 `Begin` 、 `Process` 和 `End` 关键字。 动态参数是在运行时添加的。

语法：

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="else"></a>Else

与关键字一起使用 `If` 以指定默认语句列表。

语法：

```Syntax
if (<condition>) {<statement list>}
else {<statement list>}
```

### <a name="elseif"></a>Elseif

与和关键字一起使用， `If` `Else` 以指定其他条件。 `Else`关键字是可选的。

语法：

```Syntax
if (<condition>) {<statement list>}
elseif (<condition>) {<statement list>}
else {<statement list>}
```

### <a name="end"></a>结束

指定函数体的一部分，以及 `DynamicParam` 、 `Begin` 和 `End` 关键字。 在 `End` 从管道接收到所有对象之后，语句列表将运行一次。

语法：

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="enum"></a>枚举

`enum` 用于声明枚举;一种由一组称为枚举器列表的命名标签组成的不同类型。

语法：

```Syntax
enum <enum-name> {
    <label> [= <int-value>]
    ...
}
```

### <a name="exit"></a>退出

导致 PowerShell 退出脚本或 PowerShell 实例。

语法：

```Syntax
exit
exit <exitcode>
```

当你 `pwsh` 与 **file** 参数一起使用时， `.ps1` (脚本) 文件本身应该包含用于处理在运行脚本时出现的任何错误或异常的说明。 只应使用 `exit` 语句指示脚本的执行后状态。

在 Windows 上，允许使用介于和之间的任何数字 `[int]::MinValue` `[int]::MaxValue` 。

在 Unix 上，只允许使用介于和之间的正数 `[byte]::MinValue` `[byte]::MaxValue` 。 范围内的负数 `-1` `-255` 将通过添加256自动转换为正数。 例如， `-2` 将转换为 `254` 。

在 PowerShell 中， `exit` 语句设置变量的值 `$LASTEXITCODE` 。 在 Windows 命令行界面 ( # A0) 中，exit 语句设置环境变量的值 `%ERRORLEVEL%` 。

任何非数字或超出平台特定范围的参数均转换为的值 `0` 。

在下面的示例中，用户通过添加到脚本文件将错误级别变量值设置为 4 `exit 4` `test.ps1` 。

```cmd
C:\scripts\test>type test.ps1
1
2
3
exit 4

C:\scripts\test>pwsh -file ./test.ps1
1
2
3

C:\scripts\test>echo %ERRORLEVEL%
4
```

当你运行 `pwsh.exe -File <path to a script>` 并且脚本文件以命令结束时 `exit` ，退出代码将设置为与命令一起使用的数值参数 `exit` 。 如果脚本中没有 `exit` 语句，则在 `0` 脚本完成且没有错误或 `1` 脚本从未经处理的异常中终止时，始终会出现退出代码。

### <a name="filter"></a>筛选器

指定一个函数，该函数在此函数中对每个输入对象运行一次语句。 它与只包含进程块的函数具有相同的效果。

语法：

```Syntax
filter <name> {<statement list>}
```

### <a name="finally"></a>最终

定义在与 Try 和 Catch 关联的语句之后运行的语句列表。 `Finally`即使按下 `CTRL+C` 了脚本或使用脚本中的 Exit 关键字，语句列表也会运行。

语法：

```Syntax
try {<statement list>}
catch [<error type>] {<statement list>}
finally {<statement list>}
```

### <a name="for"></a>For

使用条件定义循环。

语法：

```Syntax
for (<initialize>; <condition>; <iterate>) { <statement list> }
```

### <a name="foreach"></a>ForEach

使用集合中的每个成员定义循环。

语法：

```Syntax
ForEach (<item> in <collection>) { <statement list> }
```

### <a name="from"></a>From

留待将来使用。

### <a name="function"></a>函数

创建可重用代码的命名语句列表。 可以命名函数所属的作用域。 使用关键字可以指定一个或多个命名参数 `Param` 。 在函数语句列表中，可以包含 `DynamicParam` 、、 `Begin` `Process` 和 `End` 语句列表。

语法：

```Syntax
function [<scope:>]<name> {
   param ([type]<$pname1> [, [type]<$pname2>])
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

您还可以选择在函数名称后定义语句列表之外的一个或多个参数。

语法：

```Syntax
function [<scope:>]<name> [([type]<$pname1>, [[type]<$pname2>])] {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="if"></a>如果

定义条件。

语法：

```Syntax
if (<condition>) {<statement list>}
```

### <a name="hidden"></a>Hidden

从 cmdlet 的默认结果中隐藏类成员 `Get-Member` ，并从 IntelliSense 和 tab 键完成结果中隐藏类成员。

语法：

```Syntax
Hidden [data type] $member_name
```

### <a name="in"></a>在

在语句中用于 `ForEach` 创建使用集合的每个成员的循环。

语法：

```Syntax
ForEach (<item> in <collection>){<statement list>}
```

### <a name="inlinescript"></a>InlineScript

在共享 PowerShell 会话中运行工作流命令。 此关键字仅在 PowerShell 工作流中有效。

语法：

```Syntax
workflow <verb>-<noun>
{
   InlineScript
   {
      <Command/Expression>
      ...

   }
}
```

`InlineScript`关键字指示一个 `InlineScript` 活动，该活动在) 会话 (非工作流的共享标准中运行命令。 您可以使用 `InlineScript` 关键字来运行在工作流中无效的命令，以及运行共享数据的命令。 默认情况下，InlineScript 脚本块中的命令在单独的进程中运行。

有关详细信息，请参阅 [在工作流中运行 PowerShell 命令](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574197(v=ws.11))。

### <a name="param"></a>Param

定义函数中的参数。

语法：

```Syntax
function [<scope:>]<name> {
   param ([type]<$pname1>[, [[type]<$pname2>]])
   <statement list>
}
```

### <a name="process"></a>过程

指定函数正文的一部分，以及 `DynamicParam` 、 `Begin` 和 `End` 关键字。 当 `Process` 语句列表接收到管道的输入时， `Process` 语句列表将为管道中的每个元素运行一次。 如果管道不提供任何对象，则 `Process` 不会运行语句列表。 如果该命令是管道中的第一个命令，则 `Process` 语句列表将运行一次。

语法：

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="return"></a>返回

使 PowerShell 保留当前范围（如脚本或函数），并将可选表达式写入输出。

语法：

```Syntax
return [<expression>]
```

### <a name="static"></a>Static

指定定义的属性或方法对于定义的类的所有实例都是通用的。

`Class`有关用法示例，请参阅。

### <a name="switch"></a>交换机

若要检查多个条件，请使用 `Switch` 语句。 `Switch`语句等效于一系列 `If` 语句，但它更简单。

`Switch`语句列出每个条件和一个可选操作。 如果条件获得，则执行该操作。

语法 1：

```Syntax
switch [-regex|-wildcard|-exact][-casesensitive] ( <value> )
{
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   ...

   default {<statement list>}
}
```

语法 2：

```Syntax
switch [-regex|-wildcard|-exact][-casesensitive] -file <filename>
{
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   ...

   default {<statement list>}
}
```

### <a name="throw"></a>Throw

将对象作为错误引发。

语法：

```Syntax
throw [<object>]
```

### <a name="trap"></a>Trap

如果遇到错误，则定义要运行的语句列表。 错误类型需要方括号。 第二对方括号指示错误类型是可选的。

语法：

```Syntax
trap [[<error type>]] {<statement list>}
```

### <a name="try"></a>尝试

定义在运行语句时要检查是否有错误的语句列表。 如果发生错误，PowerShell 将继续在 `Catch` 或语句中运行 `Finally` 。 错误类型需要方括号。 第二对方括号指示错误类型是可选的。

语法：

```Syntax
try {<statement list>}
catch [[<error type>]] {<statement list>}
finally {<statement list>}
```

### <a name="until"></a>Until

在语句中用作 `Do` 循环构造，其中至少执行一次语句列表。

语法：

```Syntax
do {<statement list>} until (<condition>)
```

### <a name="using"></a>使用

允许指示在会话中使用的命名空间。 类和成员需要更少的键入来提及它们。 还可以包含模块中的类。

语法 #1：

```Syntax
using namespace <.Net-framework-namespace>
```

语法 #2：

```Syntax
using module <module-name>
```

### <a name="while"></a>While

`while`语句是循环构造，其中的条件在执行语句之前进行测试。 如果条件为 FALSE，则不执行语句。

语句语法：

```Syntax
while (<condition>) {
   <statements>
 }
```

在语句中使用时 `Do` ， `while` 是循环构造的一部分，其中至少执行一次语句列表。

Do 循环语法：

```Syntax
do {<statement list>} while (<condition>)
```

## <a name="see-also"></a>另请参阅

- [about_Special_Characters](about_Special_Characters.md)
- [about_Wildcards](about_Wildcards.md)

