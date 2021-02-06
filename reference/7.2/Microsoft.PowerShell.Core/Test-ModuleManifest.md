---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-modulemanifest?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ModuleManifest
ms.openlocfilehash: c86a7253335b91011d2eb225bc53d1c5cc671aff
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597441"
---
# <span data-ttu-id="24a4f-102">Test-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="24a4f-102">Test-ModuleManifest</span></span>

## <span data-ttu-id="24a4f-103">摘要</span><span class="sxs-lookup"><span data-stu-id="24a4f-103">SYNOPSIS</span></span>
<span data-ttu-id="24a4f-104">验证模块清单文件是否准确描述了模块的内容。</span><span class="sxs-lookup"><span data-stu-id="24a4f-104">Verifies that a module manifest file accurately describes the contents of a module.</span></span>

## <span data-ttu-id="24a4f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="24a4f-105">SYNTAX</span></span>

```
Test-ModuleManifest [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="24a4f-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="24a4f-106">DESCRIPTION</span></span>

<span data-ttu-id="24a4f-107">**New-modulemanifest** cmdlet 验证模块清单中列出的文件 () 文件实际上是否位于指定的路径中。</span><span class="sxs-lookup"><span data-stu-id="24a4f-107">The **Test-ModuleManifest** cmdlet verifies that the files that are listed in the module manifest (.psd1) file are actually in the specified paths.</span></span>

<span data-ttu-id="24a4f-108">此 cmdlet 旨在帮助模块作者测试其清单文件。</span><span class="sxs-lookup"><span data-stu-id="24a4f-108">This cmdlet is designed to help module authors test their manifest files.</span></span>
<span data-ttu-id="24a4f-109">模块用户还可以在脚本和命令中使用此 cmdlet 来检测错误，然后再运行依赖于该模块的脚本。</span><span class="sxs-lookup"><span data-stu-id="24a4f-109">Module users can also use this cmdlet in scripts and commands to detect errors before they run scripts that depend on the module.</span></span>

<span data-ttu-id="24a4f-110">**New-modulemanifest** 返回表示模块的对象。</span><span class="sxs-lookup"><span data-stu-id="24a4f-110">**Test-ModuleManifest** returns an object that represents the module.</span></span>
<span data-ttu-id="24a4f-111">这是 Get-Module 返回的相同类型的对象。</span><span class="sxs-lookup"><span data-stu-id="24a4f-111">This is the same type of object that Get-Module returns.</span></span>
<span data-ttu-id="24a4f-112">如果有任何文件在清单中指定的位置上不存在，则该 cmdlet 还将针对每个缺少的文件生成一个错误。</span><span class="sxs-lookup"><span data-stu-id="24a4f-112">If any files are not in the locations specified in the manifest, the cmdlet also generates an error for each missing file.</span></span>

## <span data-ttu-id="24a4f-113">示例</span><span class="sxs-lookup"><span data-stu-id="24a4f-113">EXAMPLES</span></span>

### <span data-ttu-id="24a4f-114">示例1：测试清单</span><span class="sxs-lookup"><span data-stu-id="24a4f-114">Example 1: Test a manifest</span></span>

```powershell
test-ModuleManifest -Path "$pshome\Modules\TestModule.psd1"
```

<span data-ttu-id="24a4f-115">此命令将测试 TestModule.psd1 模块清单。</span><span class="sxs-lookup"><span data-stu-id="24a4f-115">This command tests the TestModule.psd1 module manifest.</span></span>

### <span data-ttu-id="24a4f-116">示例2：使用管道测试清单</span><span class="sxs-lookup"><span data-stu-id="24a4f-116">Example 2: Test a manifest by using the pipeline</span></span>

```powershell
"$pshome\Modules\TestModule.psd1" | test-modulemanifest
```

```Output
Test-ModuleManifest : The specified type data file 'C:\Windows\System32\Wi
ndowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml' could not be processed because the file was not found. Please correct the path and try again.
At line:1 char:34
+ "$pshome\Modules\TestModule.psd1" | test-modulemanifest <<<<
+ CategoryInfo          : ResourceUnavailable: (C:\Windows\System32\WindowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml:String) [Test-ModuleManifest], FileNotFoundException
+ FullyQualifiedErrorId : Modules_TypeDataFileNotFound,Microsoft.PowerShell.Commands.TestModuleManifestCommandName

Name              : TestModule
Path              : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule\TestModule.psd1
Description       :
Guid              : 6f0f1387-cd25-4902-b7b4-22cff6aefa7b
Version           : 1.0
ModuleBase        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule
ModuleType        : Manifest
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {}
ExportedVariables : {}
NestedModules     : {}
```

<span data-ttu-id="24a4f-117">此命令使用管道运算符 (|) 将路径字符串发送到 **new-modulemanifest**。</span><span class="sxs-lookup"><span data-stu-id="24a4f-117">This command uses a pipeline operator (|) to send a path string to **Test-ModuleManifest**.</span></span>

<span data-ttu-id="24a4f-118">命令输出显示测试未通过，因为找不到清单中所列出的 TestTypes.ps1xml 文件。</span><span class="sxs-lookup"><span data-stu-id="24a4f-118">The command output shows that the test failed, because the TestTypes.ps1xml file, which was listed in the manifest, was not found.</span></span>

### <span data-ttu-id="24a4f-119">示例3：编写用于测试模块清单的函数</span><span class="sxs-lookup"><span data-stu-id="24a4f-119">Example 3: Write a function to test a module manifest</span></span>

```powershell
function Test-ManifestBool ($path)
```

```Output
{$a = dir $path | Test-ModuleManifest -ErrorAction SilentlyContinue; $?}
```

<span data-ttu-id="24a4f-120">此函数类似于 **new-modulemanifest**，但它返回一个布尔值。</span><span class="sxs-lookup"><span data-stu-id="24a4f-120">This function is like **Test-ModuleManifest**, but it returns a Boolean value.</span></span>
<span data-ttu-id="24a4f-121">如果清单已通过测试 $False，则函数返回 $True; 否则返回。</span><span class="sxs-lookup"><span data-stu-id="24a4f-121">The function returns $True if the manifest passed the test and $False otherwise.</span></span>

<span data-ttu-id="24a4f-122">该函数使用 Get-ChildItem cmdlet alias = dir 来获取由 $path 变量指定的模块清单。</span><span class="sxs-lookup"><span data-stu-id="24a4f-122">The function uses the Get-ChildItem cmdlet, alias = dir, to get the module manifest specified by the $path variable.</span></span>
<span data-ttu-id="24a4f-123">该命令使用管道运算符 (|) 将文件对象传递给 **new-modulemanifest**。</span><span class="sxs-lookup"><span data-stu-id="24a4f-123">The command uses a pipeline operator (|) to pass the file object to **Test-ModuleManifest**.</span></span>

<span data-ttu-id="24a4f-124">**New-modulemanifest** 使用值为 SilentlyContinue 的 *ErrorAction* 通用参数来禁止显示该命令生成的任何错误。</span><span class="sxs-lookup"><span data-stu-id="24a4f-124">**Test-ModuleManifest** uses the *ErrorAction* common parameter with a value of SilentlyContinue to suppress the display of any errors that the command generates.</span></span>
<span data-ttu-id="24a4f-125">它还会保存 **new-modulemanifest** 在 $a 变量中返回的 **PSModuleInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="24a4f-125">It also saves the **PSModuleInfo** object that **Test-ModuleManifest** returns in the $a variable.</span></span>
<span data-ttu-id="24a4f-126">因此，不会显示该对象。</span><span class="sxs-lookup"><span data-stu-id="24a4f-126">Therefore, the object is not displayed.</span></span>

<span data-ttu-id="24a4f-127">然后，在单独的命令中，该函数显示 $？</span><span class="sxs-lookup"><span data-stu-id="24a4f-127">Then, in a separate command, the function displays the value of the $?</span></span>
<span data-ttu-id="24a4f-128">自动变量。</span><span class="sxs-lookup"><span data-stu-id="24a4f-128">automatic variable.</span></span>
<span data-ttu-id="24a4f-129">如果上面的命令未生成错误，则该命令将显示 $True，否则 $False。</span><span class="sxs-lookup"><span data-stu-id="24a4f-129">If the previous command generates no error, the command displays $True, and $False otherwise.</span></span>

<span data-ttu-id="24a4f-130">您可以在条件语句中使用此函数，例如可能位于 **import-module** 命令或使用模块的命令之前的语句。</span><span class="sxs-lookup"><span data-stu-id="24a4f-130">You can use this function in conditional statements, such as those that might precede an **Import-Module** command or a command that uses the module.</span></span>

## <span data-ttu-id="24a4f-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="24a4f-131">PARAMETERS</span></span>

### <span data-ttu-id="24a4f-132">-Path</span><span class="sxs-lookup"><span data-stu-id="24a4f-132">-Path</span></span>

<span data-ttu-id="24a4f-133">指定清单文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="24a4f-133">Specifies a path and file name for the manifest file.</span></span>
<span data-ttu-id="24a4f-134">输入包含 psd1 文件扩展名的模块清单文件的可选路径和名称。</span><span class="sxs-lookup"><span data-stu-id="24a4f-134">Enter an optional path and name of the module manifest file that has the .psd1 file name extension.</span></span>
<span data-ttu-id="24a4f-135">默认位置为当前目录。</span><span class="sxs-lookup"><span data-stu-id="24a4f-135">The default location is the current directory.</span></span>
<span data-ttu-id="24a4f-136">支持通配符，但必须将其解析为单个模块清单文件。</span><span class="sxs-lookup"><span data-stu-id="24a4f-136">Wildcard characters are supported, but must resolve to a single module manifest file.</span></span>
<span data-ttu-id="24a4f-137">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="24a4f-137">This parameter is required.</span></span>
<span data-ttu-id="24a4f-138">还可以通过管道将路径传递给 **new-modulemanifest**。</span><span class="sxs-lookup"><span data-stu-id="24a4f-138">You can also pipe a path to **Test-ModuleManifest**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="24a4f-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="24a4f-139">CommonParameters</span></span>

<span data-ttu-id="24a4f-140">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="24a4f-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="24a4f-141">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="24a4f-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="24a4f-142">输入</span><span class="sxs-lookup"><span data-stu-id="24a4f-142">INPUTS</span></span>

### <span data-ttu-id="24a4f-143">System.String</span><span class="sxs-lookup"><span data-stu-id="24a4f-143">System.String</span></span>

<span data-ttu-id="24a4f-144">可以通过管道将模块清单的路径传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="24a4f-144">You can pipe the path to a module manifest to this cmdlet.</span></span>

## <span data-ttu-id="24a4f-145">输出</span><span class="sxs-lookup"><span data-stu-id="24a4f-145">OUTPUTS</span></span>

### <span data-ttu-id="24a4f-146">System.Management.Automation.PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="24a4f-146">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="24a4f-147">此 cmdlet 将返回表示模块的 **PSModuleInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="24a4f-147">This cmdlet returns a **PSModuleInfo** object that represents the module.</span></span>
<span data-ttu-id="24a4f-148">即使清单有错误，它也会返回此对象。</span><span class="sxs-lookup"><span data-stu-id="24a4f-148">It returns this object even if the manifest has errors.</span></span>

## <span data-ttu-id="24a4f-149">注释</span><span class="sxs-lookup"><span data-stu-id="24a4f-149">NOTES</span></span>

## <span data-ttu-id="24a4f-150">相关链接</span><span class="sxs-lookup"><span data-stu-id="24a4f-150">RELATED LINKS</span></span>

[<span data-ttu-id="24a4f-151">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="24a4f-151">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="24a4f-152">Get-Module</span><span class="sxs-lookup"><span data-stu-id="24a4f-152">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="24a4f-153">Import-Module</span><span class="sxs-lookup"><span data-stu-id="24a4f-153">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="24a4f-154">New-Module</span><span class="sxs-lookup"><span data-stu-id="24a4f-154">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="24a4f-155">New-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="24a4f-155">New-ModuleManifest</span></span>](New-ModuleManifest.md)

[<span data-ttu-id="24a4f-156">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="24a4f-156">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="24a4f-157">about_Modules</span><span class="sxs-lookup"><span data-stu-id="24a4f-157">about_Modules</span></span>](About/about_Modules.md)

