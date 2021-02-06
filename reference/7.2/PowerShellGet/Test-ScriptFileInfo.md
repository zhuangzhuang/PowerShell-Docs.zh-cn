---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/test-scriptfileinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ScriptFileInfo
ms.openlocfilehash: 35de1c9b7c975a68ac2f5a01c97a78eeef6d1184
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597435"
---
# <span data-ttu-id="6dc2d-102">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="6dc2d-102">Test-ScriptFileInfo</span></span>

## <span data-ttu-id="6dc2d-103">摘要</span><span class="sxs-lookup"><span data-stu-id="6dc2d-103">SYNOPSIS</span></span>
<span data-ttu-id="6dc2d-104">验证脚本的注释块。</span><span class="sxs-lookup"><span data-stu-id="6dc2d-104">Validates a comment block for a script.</span></span>

## <span data-ttu-id="6dc2d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6dc2d-105">SYNTAX</span></span>

### <span data-ttu-id="6dc2d-106">PathParameterSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="6dc2d-106">PathParameterSet (Default)</span></span>

```
Test-ScriptFileInfo [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="6dc2d-107">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="6dc2d-107">LiteralPathParameterSet</span></span>

```
Test-ScriptFileInfo -LiteralPath <String> [<CommonParameters>]
```

## <span data-ttu-id="6dc2d-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6dc2d-108">DESCRIPTION</span></span>

<span data-ttu-id="6dc2d-109">**New-scriptfileinfo** cmdlet 验证将使用 Publish-Script cmdlet 发布的脚本开头的注释块。</span><span class="sxs-lookup"><span data-stu-id="6dc2d-109">The **Test-ScriptFileInfo** cmdlet validates the comment block at the beginning of a script that will be published with the Publish-Script cmdlet.</span></span>
<span data-ttu-id="6dc2d-110">如果注释块出现错误，则此 cmdlet 将返回有关错误所在位置的信息或纠正方法。</span><span class="sxs-lookup"><span data-stu-id="6dc2d-110">If the comment block has an error, this cmdlet returns information about where the error is located or how to correct it.</span></span>

## <span data-ttu-id="6dc2d-111">示例</span><span class="sxs-lookup"><span data-stu-id="6dc2d-111">EXAMPLES</span></span>

### <span data-ttu-id="6dc2d-112">示例1：测试脚本文件</span><span class="sxs-lookup"><span data-stu-id="6dc2d-112">Example 1: Test a script file</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "C:\temp\temp_scripts\New-ScriptFile.ps1"
Version    Name                      Author               Description
-------    ----                      ------               -----------
1.0        New-ScriptFile            pattif               my new script file test
```

<span data-ttu-id="6dc2d-113">此命令测试 New-ScriptFile.ps1 脚本文件并显示结果。</span><span class="sxs-lookup"><span data-stu-id="6dc2d-113">This command tests the New-ScriptFile.ps1 script file and displays the results.</span></span>
<span data-ttu-id="6dc2d-114">脚本文件包含有效的元数据。</span><span class="sxs-lookup"><span data-stu-id="6dc2d-114">The script file includes valid metadata.</span></span>

### <span data-ttu-id="6dc2d-115">示例2：测试包含所有元数据属性值的脚本文件</span><span class="sxs-lookup"><span data-stu-id="6dc2d-115">Example 2: Test a script file that has values for all metadata properties</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "D:\code\Test-Runbook.ps1" | Format-List *
Name                       : Test-Runbook
Path                       : D:\code\Test-Runbook.ps1
ScriptBase                 : D:\code
ReleaseNotes               : {contoso script now supports following features, Feature 1, Feature 2, Feature 3...}
Version                    : 1.0
Guid                       : eb246b19-17da-4392-8c89-7c280f69ad0e
Author                     : pattif
CompanyName                : Microsoft Corporation
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
Tags                       : {Tag1, Tag2, Tag3}
LicenseUri                 : https://contoso.com/License
ProjectUri                 : https://contoso.com/
IconUri                    : https://contoso.com/MyScriptIcon
ExternalModuleDependencies : ExternalModule1
RequiredScripts            : {Start-WFContosoServer, Stop-ContosoServerScript}
ExternalScriptDependencies : Stop-ContosoServerScript
Description                : Contoso Script example
RequiredModules            : {RequiredModule1, @{ ModuleName = 'RequiredModule2'; ModuleVersion = '1.0' }, @{ ModuleName = 'RequiredModule3'; RequiredVersion = '2.0' }, ExternalModule1}
ExportedCommands           : {Test-WebUri, ValidateAndAdd-PSScriptInfoEntry, Get-PSScriptInfo, My-Workflow...}
ExportedFunctions          : {Test-WebUri, ValidateAndAdd-PSScriptInfoEntry, Get-PSScriptInfo, My-AdvPSCmdlet}
ExportedWorkflows          : My-Workflow
```

<span data-ttu-id="6dc2d-116">此命令 Test-Runbook.ps1 测试脚本文件，并使用管道运算符将结果传递给 Format-List cmdlet 以设置结果的格式。</span><span class="sxs-lookup"><span data-stu-id="6dc2d-116">This command tests the script file Test-Runbook.ps1 and uses the pipeline operator to pass the results to the Format-List cmdlet to format the results.</span></span>

### <span data-ttu-id="6dc2d-117">示例3：测试没有元数据的脚本文件</span><span class="sxs-lookup"><span data-stu-id="6dc2d-117">Example 3: Test a script file that has no metadata</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "D:\code\Hello-World.ps1"
Test-ScriptFileInfo : Script 'D:\code\Hello-World.ps1' is missing required metadata properties. Verify that the script file has Version, Description
and Author properties. You can use the Update-ScriptFileInfo or New-ScriptFileInfo cmdlet to add or update the PSScriptInfo to the script file.
At line:1 char:1
+ Test-ScriptFileInfo D:\code\Hello-World.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidArgument: (D:\code\Hello-World.ps1:String) [Test-ScriptFileInfo], ArgumentException

+ FullyQualifiedErrorId : MissingRequiredPSScriptInfoProperties,Test-ScriptFile
```

<span data-ttu-id="6dc2d-118">此命令测试 Hello-World.ps1 的脚本文件，该文件没有关联的元数据。</span><span class="sxs-lookup"><span data-stu-id="6dc2d-118">This command tests the script file Hello-World.ps1, which has no metadata associated with it.</span></span>

## <span data-ttu-id="6dc2d-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6dc2d-119">PARAMETERS</span></span>

### <span data-ttu-id="6dc2d-120">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6dc2d-120">-LiteralPath</span></span>

<span data-ttu-id="6dc2d-121">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="6dc2d-121">Specifies a path to one or more locations.</span></span>
<span data-ttu-id="6dc2d-122">与 *Path* 参数不同， *LiteralPath* 参数的值严格按照输入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="6dc2d-122">Unlike the *Path* parameter, the value of the *LiteralPath* parameter is used exactly as it is entered.</span></span>
<span data-ttu-id="6dc2d-123">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="6dc2d-123">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="6dc2d-124">如果路径包含转义符，请将其括在单引号内。</span><span class="sxs-lookup"><span data-stu-id="6dc2d-124">If the path includes escape characters, enclose them in single quotation marks.</span></span>
<span data-ttu-id="6dc2d-125">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="6dc2d-125">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6dc2d-126">-Path</span><span class="sxs-lookup"><span data-stu-id="6dc2d-126">-Path</span></span>

<span data-ttu-id="6dc2d-127">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="6dc2d-127">Specifies a path to one or more locations.</span></span>
<span data-ttu-id="6dc2d-128">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="6dc2d-128">Wildcards are permitted.</span></span>
<span data-ttu-id="6dc2d-129">默认位置为当前目录 (.)。</span><span class="sxs-lookup"><span data-stu-id="6dc2d-129">The default location is the current directory (.).</span></span>

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="6dc2d-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6dc2d-130">CommonParameters</span></span>

<span data-ttu-id="6dc2d-131">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6dc2d-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6dc2d-132">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6dc2d-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6dc2d-133">输入</span><span class="sxs-lookup"><span data-stu-id="6dc2d-133">INPUTS</span></span>

### <span data-ttu-id="6dc2d-134">System.String</span><span class="sxs-lookup"><span data-stu-id="6dc2d-134">System.String</span></span>

## <span data-ttu-id="6dc2d-135">输出</span><span class="sxs-lookup"><span data-stu-id="6dc2d-135">OUTPUTS</span></span>

### <span data-ttu-id="6dc2d-136">System.Object</span><span class="sxs-lookup"><span data-stu-id="6dc2d-136">System.Object</span></span>

## <span data-ttu-id="6dc2d-137">注释</span><span class="sxs-lookup"><span data-stu-id="6dc2d-137">NOTES</span></span>

## <span data-ttu-id="6dc2d-138">相关链接</span><span class="sxs-lookup"><span data-stu-id="6dc2d-138">RELATED LINKS</span></span>

[<span data-ttu-id="6dc2d-139">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="6dc2d-139">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)

[<span data-ttu-id="6dc2d-140">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="6dc2d-140">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="6dc2d-141">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="6dc2d-141">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)

