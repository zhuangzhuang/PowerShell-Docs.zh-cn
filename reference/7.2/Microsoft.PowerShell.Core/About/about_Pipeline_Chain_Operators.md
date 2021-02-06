---
description: 介绍如何 `&&` 在 PowerShell 中将管道与 and `||` 运算符链接。
Locale: en-US
ms.date: 09/30/2019
schema: 2.0.0
title: about_Pipeline_Chain_Operators
ms.openlocfilehash: ece84ec061126401e53bf58112cd79a07a816e8d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598908"
---
# <a name="about-pipeline-chain-operators"></a>关于管道链运算符

## <a name="short-description"></a>简短说明

介绍如何 `&&` 在 PowerShell 中将管道与 and `||` 运算符链接。

## <a name="long-description"></a>长说明

从 PowerShell 7 开始，PowerShell 实现 `&&` 和 `||` 运算符以有条件地链接管道。 这些运算符在 PowerShell 中已知为 *管道链运算符*，并且类似于 POSIX shell 中的 [和-或列表](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) （如 bash、zsh 和 Sh）以及 Windows 命令行界面中的 [条件处理符号](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) ( # A0) 。

如果左侧管道成功，则 `&&` 运算符将执行右侧管道。 相反，如果左侧管道失败，则 `||` 运算符将执行右侧管道。

这些运算符使用 `$?` 和 `$LASTEXITCODE` 变量来确定管道是否失败。 这允许你将其与本机命令一起使用，而不只是与 cmdlet 或函数一起使用。 例如：

```powershell
# Create an SSH key pair - if successful copy the public key to clipboard
ssh-keygen -t rsa -b 2048 && Get-Content -Raw ~\.ssh\id_rsa.pub | clip
```

### <a name="examples"></a>示例

#### <a name="two-successful-commands"></a>两个成功的命令

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

#### <a name="first-command-fails-causing-second-not-to-be-executed"></a>第一条命令失败，导致第二个命令失败

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

#### <a name="first-command-succeeds-so-the-second-command-is-not-executed"></a>第一个命令成功，因此不执行第二个命令

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

#### <a name="first-command-fails-so-the-second-command-is-executed"></a>第一条命令失败，因此将执行第二个命令

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error: Bad
Second
```

管道成功由变量的值定义 `$?` ，在基于其执行状态执行管道之后，PowerShell 会自动设置该变量的值。
这意味着管道链运算符具有以下等效性：

```powershell
Test-Command '1' && Test-Command '2'
```

的工作方式与

```powershell
Test-Command '1'; if ($?) { Test-Command '2' }
```

和

```powershell
Test-Command '1' || Test-Command '2'
```

的工作方式与

```powershell
Test-Command '1'; if (-not $?) { Test-Command '2' }
```

### <a name="assignment-from-pipeline-chains"></a>从管道链分配

从管道链分配变量会使该链中的所有管道串联：

```powershell
$result = Write-Output '1' && Write-Output '2'
$result
```

```Output
1
2
```

如果在分配管道链期间出现脚本终止错误，则分配不会成功：

```powershell
try
{
    $result = Write-Output 'Value' && $(throw 'Bad')
}
catch
{
    # Do nothing, just squash the error
}

"Result: $result"
```

```Output
Result:
```

### <a name="operator-syntax-and-precedence"></a>运算符语法和优先级

与其他运算符不同， `&&` 并对 `||` 管道进行操作，而不是在或等表达式上操作 `+` `-and` 。

`&&` 和的 `||` 优先级低于管道 (`|`) 或重定向 (`>`) ，但优先级高于作业运算符 () `&` 、赋值 (`=`) 或分号 (`;`) 。 这意味着，可以单独重定向管道链内的管道，并且可以将整个管道链 backgrounded、赋值给变量或分隔为语句。

若要在管道链中使用低优先级语法，请考虑使用括号 `(...)` 。
同样，若要在管道链中嵌入语句， `$(...)` 可以使用子表达式。
这可用于结合控制流的本机命令：

```powershell
foreach ($file in 'file1','file2','file3')
{
    # When find succeeds, the loop breaks
    find $file && Write-Output "Found $file" && $(break)
}
```

```Output
find: file1: No such file or directory
file2
Found file2
```

从 PowerShell 7 起，这些语法的行为已更改，以便 `$?` 在命令在括号或子表达式内成功或失败时设置为预期。

与 PowerShell 中的大多数其他运算符一样， `&&` 和 `||` 都是 *左结合* 运算符，这意味着它们从左侧进行分组。 例如：

```powershell
Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist" && Get-Content -Raw ./file.txt
```

将按以下方式分组：

```
[Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist"] && Get-Content -Raw ./file.txt
```

等效于：

```powershell
Get-ChildItem -Path ./file.txt

if (-not $?) { Write-Error "file.txt does not exist" }

if ($?) { Get-Content -Raw ./file.txt }
```

### <a name="error-interaction"></a>错误交互

管道链运算符不会吸收错误。 当管道链中的语句引发脚本终止错误时，管道链将终止。

例如：

```powershell
$(throw 'Bad') || Write-Output '2'
```

```Output
Exception: Bad
```

即使捕获到错误，管道链仍会终止：

```powershell
try
{
    $(throw 'Bad') || Write-Output '2'
}
catch
{
    Write-Output "Caught: $_"
}
Write-Output 'Done'
```

```Output
Caught: Bad
Done
```

如果错误是非终止的，或者只是终止了管道，则管道链将继续，并遵从的值 `$?` ：

```powershell
function Test-NonTerminatingError
{
    [CmdletBinding()]
    param()

    $exception = [System.Exception]::new('BAD')
    $errorId = 'BAD'
    $errorCategory = 'NotSpecified'

    $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

    $PSCmdlet.WriteError($errorRecord)
}

Test-NonTerminatingError || Write-Output 'Second'
```

```Output
Test-NonTerminatingError: BAD
Second
```

### <a name="chaining-pipelines-rather-than-commands"></a>链接管道，而不是命令

管道链运算符（按其名称）可用于链接管道，而不只是命令。 这与其他 shell 的行为匹配，但可能会导致难以 *成功* 确定：

```powershell
function Test-NotTwo
{
    [CmdletBinding()]
    param(
      [Parameter(ValueFromPipeline)]
      $Input
    )

    process
    {
        if ($Input -ne 2)
        {
            return $Input
        }

        $exception = [System.Exception]::new('Input is 2')
        $errorId = 'InputTwo'
        $errorCategory = 'InvalidData'

        $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

        $PSCmdlet.WriteError($errorRecord)
    }
}

1,2,3 | Test-NotTwo && Write-Output 'All done!'
```

```Output
1
Test-NotTwo : Input is 2
3
```

请注意， `Write-Output 'All done!'` 不会执行，因为在 `Test-NotTwo` 生成非终止错误后被视为已失败。

## <a name="see-also"></a>请参阅

- [about_Operators](about_Operators.md)
- [about_Automatic_Variables](about_Automatic_Variables.md)
- [about_pipelines](about_pipelines.md)

