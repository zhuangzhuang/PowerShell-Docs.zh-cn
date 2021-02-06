---
description: 介绍 `Prompt` 函数并演示如何创建自定义 `Prompt` 函数。
Locale: en-US
ms.date: 04/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_prompts?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Prompts
ms.openlocfilehash: 3887df636c3ad486a4dbe72fffdc8acd92d2b3e9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598245"
---
# <a name="about-prompts"></a>关于提示符

## <a name="short-description"></a>简短说明
介绍 `Prompt` 函数并演示如何创建自定义 `Prompt` 函数。

## <a name="long-description"></a>长说明

PowerShell 命令提示符指示 PowerShell 已准备好运行命令：

```
PS C:\>
```

PowerShell 提示符由内置 `Prompt` 函数决定。 你可以通过创建自己的 `Prompt` 函数并将其保存到 PowerShell 配置文件中来自定义该提示。

## <a name="about-the-prompt-function"></a>关于 Prompt 函数

`Prompt`函数确定 PowerShell 提示符的外观。
PowerShell 附带了一个内置 `Prompt` 函数，但你可以通过定义自己的函数来替代它 `Prompt` 。

`Prompt`函数具有以下语法：

```powershell
function Prompt { <function-body> }
```

`Prompt`函数必须返回对象。 作为最佳做法，返回一个字符串或格式化为字符串的对象。 建议最大长度是 80 个字符。

例如，以下 `Prompt` 函数返回一个 "Hello，World" 字符串，后跟一个右尖括号 (`>`) 。

```powershell
PS C:\> function prompt {"Hello, World > "}
Hello, World >
```

### <a name="getting-the-prompt-function"></a>获取 Prompt 函数

若要获取 `Prompt` 函数，请使用 `Get-Command` cmdlet 或 `Get-Item` 在函数驱动器中使用 cmdlet。

例如：

```powershell
PS C:\> Get-Command Prompt

CommandType     Name      ModuleName
-----------     ----      ----------
Function        prompt
```

若要获取设置提示值的脚本，请使用点方法获取函数的 **ScriptBlock** 属性 `Prompt` 。

例如：

```powershell
(Get-Command Prompt).ScriptBlock
```

```Output
"PS $($executionContext.SessionState.Path.CurrentLocation)$('>' * ($nestedPromptLevel + 1)) "
# .Link
# https://go.microsoft.com/fwlink/?LinkID=225750
# .ExternalHelp System.Management.Automation.dll-help.xml
```

与所有函数一样，该 `Prompt` 函数存储在 `Function:` 驱动器中。
若要显示用于创建当前函数的脚本 `Prompt` ，请键入：

```powershell
(Get-Item function:prompt).ScriptBlock
```

### <a name="the-default-prompt"></a>默认提示

仅当 `Prompt` 函数生成错误或不返回对象时，才会显示默认提示。

默认 PowerShell 提示符为：

```
PS>
```

例如，下面的命令将函数设置 `Prompt` 为 `$null` ，这是无效的。 因此会显示默认提示符。

```powershell
PS C:\> function prompt {$null}
PS>
```

因为 PowerShell 附带了内置提示，所以通常不会看到默认提示。

### <a name="built-in-prompt"></a>内置提示

PowerShell 包含内置 `Prompt` 函数。

```powershell
function prompt {
    $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
      else { '' }) + 'PS ' + $(Get-Location) +
        $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

函数使用 `Test-Path` cmdlet 来确定是否 `$PSDebugContext` 填充了自动变量。 如果 `$PSDebugContext` 填充了，则处于调试模式，并 `[DBG]:` 添加到提示符下，如下所示：

```Output
[DBG]: PS C:\ps-test>
```

如果 `$PSDebugContext` 未填充，则函数将添加 `PS` 到提示符。
函数使用 `Get-Location` cmdlet 来获取当前的文件系统目录位置。 然后，将 () 中添加一个右尖括号 `>` 。

例如：

```Output
PS C:\ps-test>
```

如果在嵌套提示符下，函数会向提示符添加两个尖括号 (`>>`) 。 如果自动变量的值大于1，则 (在嵌套提示符下 `$NestedPromptLevel` 。 ) 

例如，在嵌套提示符中进行调试时，提示符类似于以下提示符：

```Output
[DBG] PS C:\ps-test>>>
```

### <a name="changes-to-the-prompt"></a>对提示的更改

该 `Enter-PSSession` cmdlet 将远程计算机的名称前面预置到当前 `Prompt` 函数。 使用 `Enter-PSSession` cmdlet 启动与远程计算机的会话时，命令提示符将更改为包含远程计算机的名称。 例如：

```Output
PS Hello, World> Enter-PSSession Server01
[Server01]: PS Hello, World>
```

其他 PowerShell 主机应用程序和备用 shell 可能有其自己的自定义命令提示符。

有关 `$PSDebugContext` 和自动变量的详细信息 `$NestedPromptLevel` ，请参阅 [about_Automatic_Variables](about_Automatic_Variables.md)。

### <a name="how-to-customize-the-prompt"></a>如何自定义提示符

若要自定义提示，请编写新 `Prompt` 函数。 该函数不受保护，因此可以覆盖它。

若要编写 `Prompt` 函数，请键入以下内容：

```powershell
function prompt { }
```

随后在大括号之间，输入创建提示符的命令或字符串。

例如，下面的提示符包含计算机名称：

```powershell
function prompt {"PS [$env:COMPUTERNAME]> "}
```

在 Server01 计算机上，提示符类似于以下提示符：

```Output
PS [Server01] >
```

以下 `Prompt` 函数包含当前日期和时间：

```powershell
function prompt {"$(Get-Date)> "}
```

提示符类似于以下提示符：

```Output
03/15/2012 17:49:47>
```

还可以更改默认 `Prompt` 函数：

例如， `Prompt` `[ADMIN]:` 使用 " **以管理员身份运行** " 选项打开 PowerShell 时，以下已修改的函数会将添加到内置 powershell 提示符：

```powershell
function prompt {
  $identity = [Security.Principal.WindowsIdentity]::GetCurrent()
  $principal = [Security.Principal.WindowsPrincipal] $identity
  $adminRole = [Security.Principal.WindowsBuiltInRole]::Administrator

  $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
    elseif($principal.IsInRole($adminRole)) { "[ADMIN]: " }
    else { '' }
  ) + 'PS ' + $(Get-Location) +
    $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

使用 "以 **管理员身份运行** " 选项启动 PowerShell 时，将出现类似于下面的提示：

```Output
[ADMIN]: PS C:\ps-test>
```

以下 `Prompt` 函数显示下一个命令的历史记录 ID。 若要查看命令历史记录，请使用 `Get-History` cmdlet。

```powershell
function prompt {
   # The at sign creates an array in case only one history item exists.
   $history = @(Get-History)
   if($history.Count -gt 0)
   {
      $lastItem = $history[$history.Count - 1]
      $lastId = $lastItem.Id
   }

   $nextCommand = $lastId + 1
   $currentDirectory = Get-Location
   "PS: $nextCommand $currentDirectory >"
}
```

以下提示使用 `Write-Host` 和 `Get-Random` cmdlet 来创建随机更改颜色的提示。 由于 `Write-Host` 写入当前宿主应用程序但未返回对象，因此此函数包含一个 `Return` 语句。 如果不使用它，PowerShell 将使用默认提示 `PS>` 。

```powershell
function prompt {
    $color = Get-Random -Min 1 -Max 16
    Write-Host ("PS " + $(Get-Location) +">") -NoNewLine `
     -ForegroundColor $Color
    return " "
}
```

### <a name="saving-the-prompt-function"></a>保存 Prompt 函数

与任何函数一样，该 `Prompt` 函数仅存在于当前会话中。 若要为 `Prompt` 将来的会话保存该函数，请将其添加到 PowerShell 配置文件中。 有关配置文件的详细信息，请参阅 [about_Profiles](about_Profiles.md)。

## <a name="see-also"></a>请参阅

[Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Get-History](xref:Microsoft.PowerShell.Core.Get-History)

[Get-Random](xref:Microsoft.PowerShell.Utility.Get-Random)

[Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host)

[about_Profiles](about_Profiles.md)

[about_Functions](about_Functions.md)

[about_Scopes](about_Scopes.md)

[about_Debuggers](about_Debuggers.md)

[about_Automatic_Variables](about_Automatic_Variables.md)

