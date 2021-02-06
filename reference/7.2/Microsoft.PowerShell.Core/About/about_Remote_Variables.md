---
description: 说明如何在远程命令中使用本地和远程变量。
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Variables
ms.openlocfilehash: 1cd6d0c4562fcd63fc56f103ec41aa6f0bb4c01c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598070"
---
# <a name="about-remote-variables"></a>关于远程变量

## <a name="short-description"></a>简短说明

说明如何在远程命令中使用本地和远程变量。

## <a name="long-description"></a>长说明

你可以使用在远程计算机上运行的命令中的变量。 为变量赋值，然后使用变量代替值。

默认情况下，远程命令中的变量假定为在运行该命令的会话中定义。 在本地会话中定义的变量必须在命令中标识为局部变量。

## <a name="using-remote-variables"></a>使用远程变量

PowerShell 假设在运行该命令的会话中定义了远程命令中使用的变量。

在此示例中， `$ps` 变量在运行该命令的临时会话中定义 `Get-WinEvent` 。

```powershell
Invoke-Command -ComputerName S1 -ScriptBlock {
  $ps = "*PowerShell*"; Get-WinEvent -LogName $ps
}
```

当命令在持久会话（ **PSSession**）中运行时，必须在该会话中定义远程变量。

```powershell
$s = New-PSSession -ComputerName S1
Invoke-Command -Session $s -ScriptBlock {$ps = "*PowerShell*"}
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $ps}
```

## <a name="using-local-variables"></a>使用局部变量

可以使用远程命令中的局部变量，但必须在本地会话中定义此变量。

从 PowerShell 3.0 开始，可以使用 `Using` 作用域修饰符来标识远程命令中的局部变量。

的语法如下所示 `Using` ：

```
$Using:<VariableName>
```

在下面的示例中， `$ps` 变量是在本地会话中创建的，但在运行该命令的会话中使用。 `Using`作用域修饰符将 `$ps` 标识为局部变量。

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  Get-WinEvent -LogName $Using:ps
}
```

`Using`作用域修饰符可用于 **PSSession**。

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $Using:ps}
```

变量引用，如 `$using:var` `$var` 从调用方的上下文扩展为变量的值。 您无法访问调用方的变量对象。
`Using`作用域修饰符不能用于修改 **PSSession** 内的局部变量。 例如，下面的代码不起作用：

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {$Using:ps = 'Cannot assign new value'}
```

有关的详细信息 `Using` ，请参阅 [about_Scopes](./about_Scopes.md)

### <a name="using-splatting"></a>使用展开

PowerShell 展开将参数名称和值的集合传递给命令。 有关详细信息，请参阅 [about_Splatting](about_Splatting.md)。

在此示例中，展开变量 `$Splat` 是在本地计算机上设置的哈希表。 `Invoke-Command`连接到远程计算机会话。 **ScriptBlock** 将 `Using` 作用域修饰符与位于 () 符号一起使用， `@` 以表示 splatted 变量。

```powershell
$Splat = @{ Name = "Win*"; Include = "WinRM" }
Invoke-Command -Session $s -ScriptBlock { Get-Service @Using:Splat }
```

### <a name="other-situations-where-the-using-scope-modifier-is-needed"></a>需要 "Using" 作用域修饰符的其他情况

对于任何执行进程外的脚本或命令，都需要 `Using` 范围修饰符来嵌入调用会话范围内的变量值，以便使会话代码不能访问它们。 `Using`以下上下文支持作用域修饰符：

- 远程执行的命令，已开始 `Invoke-Command` 使用 **ComputerName**、 **HostName**、 **SSHConnection** 或 **Session** 参数 (远程会话) 
- 后台作业， `Start-Job` (进程外会话开始) 
- 通过 `Start-ThreadJob` 或 `ForEach-Object -Parallel` (单独的线程会话启动的线程作业) 

根据上下文，嵌入变量值是调用方的作用域中的数据的独立副本或对其的引用。 在远程和进程外会话中，它们始终是独立的副本。 在线程会话中，它们是通过引用传递的。

## <a name="serialization-of-variable-values"></a>变量值的序列化

远程执行的命令和后台作业在进程外运行。
进程外会话使用基于 XML 的序列化和反序列化来使变量的值可在进程边界内使用。 序列化进程将对象转换为包含原始对象属性但不包含其方法的 **PSObject** 。

对于有限类型的类型，请将解除冻结对象反序列化为原始类型。 解除冻结对象是原始对象实例的副本。
它具有类型属性和方法。 对于简单的类型（如 **system.object**），副本是精确的。 对于复杂类型，复制为完善。 例如，解除冻结证书对象不包含私钥。

所有其他类型的实例都是 **PSObject** 实例。 **PSTypeNames** 属性包含以 **反序列化** 的原始类型名称，例如 **Deserialized.System。Data DataTable**

## <a name="using-local-variables-with-argumentlist-parameter"></a>使用带有 **ArgumentList** 参数的局部变量

可以通过为远程命令定义参数并使用 cmdlet 的 **ArgumentList** 参数 `Invoke-Command` 将局部变量指定为参数值，来在远程命令中使用局部变量。

- 使用 `param` 关键字为远程命令定义参数。 参数名称是不需要与本地变量名称匹配的占位符。

- 使用命令中由关键字定义的参数 `param` 。

- 使用 cmdlet 的 **ArgumentList** 参数 `Invoke-Command` 将本地变量指定为参数值。

例如，以下命令在 `$ps` 本地会话中定义该变量，然后在远程命令中使用它。 该命令使用 `$log` 作为参数名称，使用局部变量 `$ps` 作为其值。

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  param($log)
  Get-WinEvent -LogName $log
} -ArgumentList $ps
```

## <a name="see-also"></a>请参阅

[about_PSSessions](about_PSSessions.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[about_Splatting](about_Splatting.md)

[about_Variables](about_Variables.md)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Start-ThreadJob](xref:ThreadJob.Start-ThreadJob)

@Microsoft.PowerShell.Core.ForEach-Object

