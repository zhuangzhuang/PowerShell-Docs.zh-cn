---
description: 说明如何创建自定义 PowerShell 在控制台提示符下读取输入的方式。
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_psconsolehostreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSConsoleHostReadLine
ms.openlocfilehash: 2f69cd4c0c8f65f4a963eae561647d6de30a067e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596033"
---
# <a name="about_psconsolehostreadline"></a>about_PSConsoleHostReadLine

## <a name="short-description"></a>简短说明
说明如何创建自定义 PowerShell 在控制台提示符下读取输入的方式。

## <a name="long-description"></a>详细说明

从 Windows PowerShell 3.0 开始，你可以编写一个名为 PSConsoleHostReadLine 的函数，用于重写处理控制台输入的默认方式。

### <a name="examples"></a>示例

下面的示例启动记事本并从用户创建的文本文件获取输入：

```powershell
function PSConsoleHostReadLine
{
  $inputFile = Join-Path $env:TEMP PSConsoleHostReadLine
  Set-Content $inputFile "PS > "

  # Notepad opens. Enter your command in it, save the file, and then exit.
  notepad $inputFile | Out-Null
  $userInput = Get-Content $inputFile
  $resultingCommand = $userInput.Replace("PS >", "")
  $resultingCommand
}
```

### <a name="remarks"></a>REMARKS

默认情况下，PowerShell 在所谓的 "加工模式" 下从控制台读取输入，在这种模式下，Windows 控制台子系统处理所有 keypresses、F7 菜单和其他输入。 按 Enter 或 Tab 键时，PowerShell 将获取已键入到该点的文本。 在按 Enter 或 Tab 之前，无法知道您按下了 Ctrl + R、Ctrl + A、Ctrl + E 或其他任何键。在 Windows PowerShell 3.0 中，PSConsoleHostReadLine 函数解决了此问题。 在 PowerShell 控制台主机中定义名为 PSConsoleHostReadline 的函数时，PowerShell 将调用而不是 "加工模式" 输入机制。

### <a name="see-also"></a>另请参阅

[about_Prompts](about_Prompts.md)

