---
ms.date: 01/11/2021
ms.topic: reference
title: 基于注释的帮助的示例
description: 基于注释的帮助的示例
ms.openlocfilehash: 237e65c59cc3b35f48b6d667c8fb297994b03638
ms.sourcegitcommit: 4879b9cdfa3f03b04a07b84442dc1ca9ae0f6b46
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2021
ms.locfileid: "98105156"
---
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="b02ab-103">基于注释的帮助的示例</span><span class="sxs-lookup"><span data-stu-id="b02ab-103">Examples of Comment-Based Help</span></span>

<span data-ttu-id="b02ab-104">本主题包括演示如何对脚本和函数使用基于注释的帮助的示例。</span><span class="sxs-lookup"><span data-stu-id="b02ab-104">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="b02ab-105">示例1：为函数 Comment-Based 帮助</span><span class="sxs-lookup"><span data-stu-id="b02ab-105">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="b02ab-106">以下示例函数包含基于注释的帮助。</span><span class="sxs-lookup"><span data-stu-id="b02ab-106">The following sample function includes comment-based Help.</span></span>

```powershell
function Add-Extension
{
    param ([string]$Name,[string]$Extension = "txt")
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.

        .DESCRIPTION
        Adds a file name extension to a supplied name.
        Takes any strings for the file name or extension.

        .PARAMETER Name
        Specifies the file name.

        .PARAMETER Extension
        Specifies the extension. "Txt" is the default.

        .INPUTS
        None. You cannot pipe objects to Add-Extension.

        .OUTPUTS
        System.String. Add-Extension returns a string with the extension or file name.

        .EXAMPLE
        PS> extension -name "File"
        File.txt

        .EXAMPLE
        PS> extension -name "File" -extension "doc"
        File.doc

        .EXAMPLE
        PS> extension "File" "doc"
        File.doc

        .LINK
        Online version: http://www.fabrikam.com/extension.html

        .LINK
        Set-Item
    #>
}
```

<span data-ttu-id="b02ab-107">以下输出显示了 `Get-Help` 用于显示函数帮助的命令的结果 `Add-Extension` 。</span><span class="sxs-lookup"><span data-stu-id="b02ab-107">The following output shows the results of a `Get-Help` command that displays the help for the `Add-Extension` function.</span></span>

```powershell
PS> Get-Help Add-Extension -full
```

```Output
        NAME
            Add-Extension

        SYNOPSIS
            Adds a file name extension to a supplied name.

        SYNTAX
            Add-Extension [[-Name] <String>] [[-Extension] <String>] [<CommonParameters>]

        DESCRIPTION
            Adds a file name extension to a supplied name. Takes any strings for the file name or extension.

        PARAMETERS
           -Name
               Specifies the file name.

               Required?                    false
               Position?                    0
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

           -Extension
               Specifies the extension. "Txt" is the default.

               Required?                    false
               Position?                    1
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

            <CommonParameters>
               This cmdlet supports the common parameters: -Verbose, -Debug,
               -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
               -OutBuffer and -OutVariable. For more information, type
               "get-help about_commonparameters".

        INPUTS
            None. You cannot pipe objects to Add-Extension.

        OUTPUTS
            System.String. Add-Extension returns a string with the extension or file name.

            -------------------------- EXAMPLE 1 --------------------------

            PS> extension -name "File"
            File.txt

            -------------------------- EXAMPLE 2 --------------------------

            PS> extension -name "File" -extension "doc"
            File.doc

            -------------------------- EXAMPLE 3 --------------------------

            PS> extension "File" "doc"
            File.doc

        RELATED LINKS
            Online version: http://www.fabrikam.com/extension.html
            Set-Item
```

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="b02ab-108">示例2：为脚本 Comment-Based 帮助</span><span class="sxs-lookup"><span data-stu-id="b02ab-108">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="b02ab-109">以下示例函数包含基于注释的帮助。</span><span class="sxs-lookup"><span data-stu-id="b02ab-109">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="b02ab-110">请注意结束 **#>** 语句和语句之间的空行 `Param` 。</span><span class="sxs-lookup"><span data-stu-id="b02ab-110">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="b02ab-111">在不包含语句的脚本中 `Param` ，"帮助" 主题中的最后一个注释和第一个函数声明之间必须至少有两个空行。</span><span class="sxs-lookup"><span data-stu-id="b02ab-111">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="b02ab-112">如果没有这些空白行，请 `Get-Help` 将帮助主题与函数（而不是脚本）相关联。</span><span class="sxs-lookup"><span data-stu-id="b02ab-112">Without these blank lines, `Get-Help` associates the Help topic with the function, instead of the script.</span></span>

```powershell
<#
  .SYNOPSIS
  Performs monthly data updates.

  .DESCRIPTION
  The Update-Month.ps1 script updates the registry with new data generated
  during the past month and generates a report.

  .PARAMETER InputPath
  Specifies the path to the CSV-based input file.

  .PARAMETER OutputPath
  Specifies the name and path for the CSV-based output file. By default,
  MonthlyUpdates.ps1 generates a name from the date and time it runs, and
  saves the output in the local directory.

  .INPUTS
  None. You cannot pipe objects to Update-Month.ps1.

  .OUTPUTS
  None. Update-Month.ps1 does not generate any output.

  .EXAMPLE
  PS> .\Update-Month.ps1

  .EXAMPLE
  PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

  .EXAMPLE
  PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
```

<span data-ttu-id="b02ab-113">以下命令获取脚本帮助。</span><span class="sxs-lookup"><span data-stu-id="b02ab-113">The following command gets the script Help.</span></span> <span data-ttu-id="b02ab-114">由于脚本不在 Path 环境变量中列出的目录中，因此 `Get-Help` 获取脚本帮助的命令必须指定脚本路径。</span><span class="sxs-lookup"><span data-stu-id="b02ab-114">Because the script is not in a directory that is listed in the Path environment variable, the `Get-Help` command that gets the script Help must specify the script path.</span></span>

```powershell
PS> Get-Help c:\ps-test\update-month.ps1 -full
```

```Output
            NAME
                C:\ps-test\Update-Month.ps1

            SYNOPSIS
                Performs monthly data updates.

            SYNTAX
                C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
                <String>] [<CommonParameters>]

            DESCRIPTION
                The Update-Month.ps1 script updates the registry with new data
                generated during the past month and generates a report.

            PARAMETERS
               -InputPath
                   Specifies the path to the CSV-based input file.

                   Required?                    true
                   Position?                    0
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               -OutputPath
                   Specifies the name and path for the CSV-based output file. By
                   default, MonthlyUpdates.ps1 generates a name from the date
                   and time it runs, and saves the output in the local directory.

                   Required?                    false
                   Position?                    1
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               <CommonParameters>
                   This cmdlet supports the common parameters: -Verbose, -Debug,
                   -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
                   -OutBuffer and -OutVariable. For more information, type,
                   "get-help about_commonparameters".

            INPUTS
                   None. You cannot pipe objects to Update-Month.ps1.

            OUTPUTS
                   None. Update-Month.ps1 does not generate any output.

            -------------------------- EXAMPLE 1 --------------------------

            PS> .\Update-Month.ps1

            -------------------------- EXAMPLE 2 --------------------------

            PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

            -------------------------- EXAMPLE 3 --------------------------

            PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
            C:\Reports\2009\January.csv

            RELATED LINKS
```

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="b02ab-115">示例3： Param 语句中的参数说明</span><span class="sxs-lookup"><span data-stu-id="b02ab-115">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="b02ab-116">此示例演示如何在函数或脚本的语句中插入参数说明 `Param` 。</span><span class="sxs-lookup"><span data-stu-id="b02ab-116">This example shows how to insert parameter descriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="b02ab-117">当参数说明简短时，此格式最为有用。</span><span class="sxs-lookup"><span data-stu-id="b02ab-117">This format is most useful when the parameter descriptions are brief.</span></span>

```powershell
function Add-Extension
{
    param
    (
        [string]
        # Specifies the file name.
        $name,

        [string]
        # Specifies the file name extension. "Txt" is the default.
        $extension = "txt"
    )
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.
...
    #>
```

<span data-ttu-id="b02ab-118">结果与示例1的结果相同。</span><span class="sxs-lookup"><span data-stu-id="b02ab-118">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="b02ab-119">`Get-Help` 解释参数说明，就好像它们带有 `.Parameter` 关键字一样。</span><span class="sxs-lookup"><span data-stu-id="b02ab-119">`Get-Help` interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="b02ab-120">示例4：重定向到 XML 文件</span><span class="sxs-lookup"><span data-stu-id="b02ab-120">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="b02ab-121">您可以为函数和脚本编写基于 XML 的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="b02ab-121">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="b02ab-122">尽管基于注释的帮助更容易实现，但如果您希望更精确地控制帮助内容或者将帮助主题转换为多种语言，则需要基于 XML 的帮助。下面的示例演示脚本的前几行 `Update-Month.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="b02ab-122">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the `Update-Month.ps1` script.</span></span> <span data-ttu-id="b02ab-123">脚本使用关键字为 `.ExternalHelp` 脚本指定基于 XML 的帮助主题的路径。</span><span class="sxs-lookup"><span data-stu-id="b02ab-123">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="b02ab-124">下面的示例演示如何 `.ExternalHelp` 在函数中使用关键字。</span><span class="sxs-lookup"><span data-stu-id="b02ab-124">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="b02ab-125">示例5：重定向到其他帮助主题</span><span class="sxs-lookup"><span data-stu-id="b02ab-125">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="b02ab-126">下面的代码摘自 `Help` PowerShell 中内置函数的开头，该函数一次显示一个屏幕帮助文本。</span><span class="sxs-lookup"><span data-stu-id="b02ab-126">The following code is an excerpt from the beginning of the built-in `Help` function in PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="b02ab-127">由于 Get-Help cmdlet 的帮助主题描述了 Help 函数，因此 Help 函数使用 `.ForwardHelpTargetName` 和 `.ForwardHelpCategory` 关键字将用户重定向到 Get-Help cmdlet 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="b02ab-127">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

```powershell
function help
{

    <#
      .FORWARDHELPTARGETNAME Get-Help
      .FORWARDHELPCATEGORY Cmdlet
    #>
    [CmdletBinding(DefaultParameterSetName='AllUsersView')]
    param(
            [Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
            [System.String]
            ${Name},
    ...
```

<span data-ttu-id="b02ab-128">以下命令使用此功能。</span><span class="sxs-lookup"><span data-stu-id="b02ab-128">The following command uses this feature.</span></span> <span data-ttu-id="b02ab-129">当用户键入该 `Get-Help` 函数的命令时 `Help` ，将 `Get-Help` 显示该 cmdlet 的帮助主题 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="b02ab-129">When a user types a `Get-Help` command for the `Help` function, `Get-Help` displays the Help topic for the `Get-Help` cmdlet.</span></span>

```powershell
PS> get-help help
```

```Output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```
