---
description: 介绍如何在 PowerShell 中使用所需状态配置 (DSC) 在 PowerShell 中进行开发。
Locale: en-US
ms.date: 01/11/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes_and_DSC
ms.openlocfilehash: a5819ac54f34393e0fbbf3b8933e840730c5d827
ms.sourcegitcommit: cc72c40315fd2981d3009b335accbfa52d57640c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/30/2020
ms.locfileid: "99603784"
---
# <a name="about-classes-and-desired-state-configuration"></a><span data-ttu-id="66a25-103">关于类和所需状态配置</span><span class="sxs-lookup"><span data-stu-id="66a25-103">About Classes and Desired State Configuration</span></span>

## <a name="short-description"></a><span data-ttu-id="66a25-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="66a25-104">Short description</span></span>

<span data-ttu-id="66a25-105">介绍如何在 PowerShell 中使用所需状态配置 (DSC) 在 PowerShell 中进行开发。</span><span class="sxs-lookup"><span data-stu-id="66a25-105">Describes how you can use classes to develop in PowerShell with Desired State Configuration (DSC).</span></span>

## <a name="long-description"></a><span data-ttu-id="66a25-106">长说明</span><span class="sxs-lookup"><span data-stu-id="66a25-106">Long description</span></span>

<span data-ttu-id="66a25-107">从 Windows PowerShell 5.0 开始，添加语言以定义类和其他用户定义的类型，方法是使用类似于其他面向对象的编程语言的正式语法和语义。</span><span class="sxs-lookup"><span data-stu-id="66a25-107">Starting in Windows PowerShell 5.0, language was added to define classes and other user-defined types, by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="66a25-108">其目标是使开发人员和 IT 专业人员能够在更广泛的用例中使用 PowerShell，从而简化 PowerShell 项目（如 DSC 资源）的开发，并加速管理图面的覆盖面。</span><span class="sxs-lookup"><span data-stu-id="66a25-108">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts such as DSC resources, and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios"></a><span data-ttu-id="66a25-109">支持的方案</span><span class="sxs-lookup"><span data-stu-id="66a25-109">Supported scenarios</span></span>

<span data-ttu-id="66a25-110">支持以下方案：</span><span class="sxs-lookup"><span data-stu-id="66a25-110">The following scenarios are supported:</span></span>

- <span data-ttu-id="66a25-111">使用 PowerShell 语言定义 DSC 资源及其关联的类型。</span><span class="sxs-lookup"><span data-stu-id="66a25-111">Define DSC resources and their associated types by using the PowerShell language.</span></span>
- <span data-ttu-id="66a25-112">使用熟悉的面向对象的编程构造（例如类、属性、方法和继承）在 PowerShell 中定义自定义类型。</span><span class="sxs-lookup"><span data-stu-id="66a25-112">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, and inheritance.</span></span>
- <span data-ttu-id="66a25-113">使用 PowerShell 语言调试类型。</span><span class="sxs-lookup"><span data-stu-id="66a25-113">Debug types by using the PowerShell language.</span></span>
- <span data-ttu-id="66a25-114">使用正式的机制以及适当的级别生成和处理异常。</span><span class="sxs-lookup"><span data-stu-id="66a25-114">Generate and handle exceptions by using formal mechanisms, and at the right level.</span></span>

## <a name="define-dsc-resources-with-classes"></a><span data-ttu-id="66a25-115">用类定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="66a25-115">Define DSC resources with classes</span></span>

<span data-ttu-id="66a25-116">除了语法更改之外，类定义的 DSC 资源和 cmdlet DSC 资源提供程序之间的主要区别是以下各项：</span><span class="sxs-lookup"><span data-stu-id="66a25-116">Apart from syntax changes, the major differences between a class-defined DSC resource and a cmdlet DSC resource provider are the following items:</span></span>

- <span data-ttu-id="66a25-117">不需要 MOF) 文件 (管理对象格式。</span><span class="sxs-lookup"><span data-stu-id="66a25-117">A Management Object Format (MOF) file is not required.</span></span>
- <span data-ttu-id="66a25-118">模块文件中的 DSCResource 子文件夹不是必需的。</span><span class="sxs-lookup"><span data-stu-id="66a25-118">A DSCResource subfolder in the module folder is not required.</span></span>
- <span data-ttu-id="66a25-119">PowerShell 模块文件可以包含多个 DSC 资源类。</span><span class="sxs-lookup"><span data-stu-id="66a25-119">A PowerShell module file can contain multiple DSC resource classes.</span></span>

## <a name="create-a-class-defined-dsc-resource-provider"></a><span data-ttu-id="66a25-120">创建类定义的 DSC 资源提供程序</span><span class="sxs-lookup"><span data-stu-id="66a25-120">Create a class-defined DSC resource provider</span></span>

<span data-ttu-id="66a25-121">下面的示例是一个类定义的 DSC 资源提供程序，它保存为模块 Mydscresource.psd1。</span><span class="sxs-lookup"><span data-stu-id="66a25-121">The following example is a class-defined DSC resource provider that is saved as a module, MyDSCResource.psm1.</span></span> <span data-ttu-id="66a25-122">必须始终在类定义的 DSC 资源提供程序中包含密钥属性。</span><span class="sxs-lookup"><span data-stu-id="66a25-122">You must always include a key property in a class-defined DSC resource provider.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}

<#
    This resource manages the file in a specific path.
    [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
        This property is the fully qualified path to the file that is
        expected to be present or absent.

        The [DscProperty(Key)] attribute indicates the property is a
        key and its value uniquely identifies a resource instance.
        Defining this attribute also means the property is required
        and DSC will ensure a value is set before calling the resource.

        A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
        This property defines the fully qualified path to a file that will
        be placed on the system if $Ensure = Present and $Path does not
        exist.

        NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
        This property reports the file's create timestamp.

        [DscProperty(NotConfigurable)] attribute indicates the property is
        not configurable in DSC configuration.  Properties marked this way
        are populated by the Get() method to report additional details
        about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#

        This method is equivalent of the Test-TargetResource script
        function. It should return True or False, showing whether the
        resource is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
{
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate
        resources. This method returns an instance of this class with the
        updated key properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }
        return $this
    }

    <#
        Helper method to check if the file exists and it is correct file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($null -eq $item)
        {
            $present = $false
        }
        elseif( $item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }
        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if(-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo]
        $destFileInfo = new-object System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            $FullName = $destFileInfo.Directory.FullName
            $Message = "Creating directory $FullName"

            Write-Verbose -Message $Message

            #use CreateDirectory instead of New-Item to avoid code
            # to handle the non-terminating error
            [System.IO.Directory]::CreateDirectory($FullName)
        }

        if(Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $this.SourcePath to $this.Path"

        #DSC engine catches and reports any error that occurs
        Copy-Item -Path $this.SourcePath -Destination $this.Path -Force
    }
}
```

## <a name="create-a-module-manifest"></a><span data-ttu-id="66a25-123">创建模块清单</span><span class="sxs-lookup"><span data-stu-id="66a25-123">Create a module manifest</span></span>

<span data-ttu-id="66a25-124">在创建类定义的 DSC 资源提供程序并将其另存为模块之后，为该模块创建一个模块清单。</span><span class="sxs-lookup"><span data-stu-id="66a25-124">After creating the class-defined DSC resource provider, and saving it as a module, create a module manifest for the module.</span></span> <span data-ttu-id="66a25-125">若要让基于类的资源对 DSC 引擎可用，你必须在清单文件中添加 `DscResourcesToExport` 声明，以指示模块导出资源。</span><span class="sxs-lookup"><span data-stu-id="66a25-125">To make a class-based resource available to the DSC engine, you must include a `DscResourcesToExport` statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="66a25-126">在此示例中，下面的模块清单另存为 MyDscResource.psd1。</span><span class="sxs-lookup"><span data-stu-id="66a25-126">In this example, the following module manifest is saved as MyDscResource.psd1.</span></span>

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

}
```

## <a name="deploy-a-dsc-resource-provider"></a><span data-ttu-id="66a25-127">部署 DSC 资源提供程序</span><span class="sxs-lookup"><span data-stu-id="66a25-127">Deploy a DSC resource provider</span></span>

<span data-ttu-id="66a25-128">通过在或中创建 Mydscresource.psd1 文件夹部署新的 DSC 资源提供程序 `$pshome\Modules` `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="66a25-128">Deploy the new DSC resource provider by creating a MyDscResource folder in `$pshome\Modules` or `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules`.</span></span>

<span data-ttu-id="66a25-129">你不需要创建一个 DSCResource 子文件夹。</span><span class="sxs-lookup"><span data-stu-id="66a25-129">You do not need to create a DSCResource subfolder.</span></span> <span data-ttu-id="66a25-130">将模块和模块清单文件（MyDscResource.psm1 和 MyDscResource.psd1）复制到 MyDscResource 文件夹。</span><span class="sxs-lookup"><span data-stu-id="66a25-130">Copy the module and module manifest files (MyDscResource.psm1 and MyDscResource.psd1) to the MyDscResource folder.</span></span>

<span data-ttu-id="66a25-131">从这时开始，你可以像对其他 DSC 资源进行的操作一样，创建并运行配置脚本。</span><span class="sxs-lookup"><span data-stu-id="66a25-131">From this point, you create and run a configuration script as you would with any DSC resource.</span></span>

## <a name="create-a-dsc-configuration-script"></a><span data-ttu-id="66a25-132">创建 DSC 配置脚本</span><span class="sxs-lookup"><span data-stu-id="66a25-132">Create a DSC configuration script</span></span>

<span data-ttu-id="66a25-133">如前面所述，将类和清单文件保存到文件夹结构中之后，就可以创建一个使用新资源的配置。</span><span class="sxs-lookup"><span data-stu-id="66a25-133">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="66a25-134">以下配置引用 Mydscresource.psd1 模块。</span><span class="sxs-lookup"><span data-stu-id="66a25-134">The following configuration references the MyDSCResource module.</span></span> <span data-ttu-id="66a25-135">将配置保存为脚本，MyResource.ps1。</span><span class="sxs-lookup"><span data-stu-id="66a25-135">Save the configuration as a script, MyResource.ps1.</span></span>

<span data-ttu-id="66a25-136">有关如何运行 DSC 配置的信息，请参阅 [Windows PowerShell Desired State Configuration 概述](/powershell/scripting/dsc/overview/dscforengineers)。</span><span class="sxs-lookup"><span data-stu-id="66a25-136">For information about how to run a DSC configuration, see [Windows PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/dscforengineers).</span></span>

<span data-ttu-id="66a25-137">在运行配置之前，请创建 `C:\test.txt` 。</span><span class="sxs-lookup"><span data-stu-id="66a25-137">Before you run the configuration, create `C:\test.txt`.</span></span> <span data-ttu-id="66a25-138">此配置将检查文件是否存在于中 `c:\test\test.txt` 。</span><span class="sxs-lookup"><span data-stu-id="66a25-138">The configuration checks if the file exists at `c:\test\test.txt`.</span></span> <span data-ttu-id="66a25-139">如果文件不存在，则配置从复制文件 `C:\test.txt` 。</span><span class="sxs-lookup"><span data-stu-id="66a25-139">If the file does not exist, the configuration copies the file from `C:\test.txt`.</span></span>

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "C:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

<span data-ttu-id="66a25-140">像运行任何 DSC 配置脚本一样运行此脚本。</span><span class="sxs-lookup"><span data-stu-id="66a25-140">Run this script as you would any DSC configuration script.</span></span> <span data-ttu-id="66a25-141">若要启动配置，请在提升的 PowerShell 控制台中运行以下内容：</span><span class="sxs-lookup"><span data-stu-id="66a25-141">To start the configuration, in an elevated PowerShell console, run the following:</span></span>

`PS C:\test> .\MyResource.ps1`

## <a name="inheritance-in-powershell-classes"></a><span data-ttu-id="66a25-142">PowerShell 类中的继承</span><span class="sxs-lookup"><span data-stu-id="66a25-142">Inheritance in PowerShell classes</span></span>

### <a name="declare-base-classes-for-powershell-classes"></a><span data-ttu-id="66a25-143">为 PowerShell 类声明基类</span><span class="sxs-lookup"><span data-stu-id="66a25-143">Declare base classes for PowerShell classes</span></span>

<span data-ttu-id="66a25-144">可以将 PowerShell 类声明为另一个 PowerShell 类的基类型，如下面的示例所示，其中， **水果** 是 **apple** 的基类型。</span><span class="sxs-lookup"><span data-stu-id="66a25-144">You can declare a PowerShell class as a base type for another PowerShell class, as shown in the following example, in which **fruit** is a base type for **apple**.</span></span>

```powershell
class fruit
{
    [int]sold() {return 100500}
}

class apple : fruit {}
    [apple]::new().sold() # return 100500
```

### <a name="declare-implemented-interfaces-for-powershell-classes"></a><span data-ttu-id="66a25-145">为 PowerShell 类声明实现的接口</span><span class="sxs-lookup"><span data-stu-id="66a25-145">Declare implemented interfaces for PowerShell classes</span></span>

<span data-ttu-id="66a25-146">可以在基类型后声明实现的接口，也可以在冒号 (`:`) 如果未指定任何基类型，则为。</span><span class="sxs-lookup"><span data-stu-id="66a25-146">You can declare implemented interfaces after base types, or immediately after a colon (`:`) if there is no base type specified.</span></span> <span data-ttu-id="66a25-147">使用逗号分隔所有类型名称。</span><span class="sxs-lookup"><span data-stu-id="66a25-147">Separate all type names by using commas.</span></span> <span data-ttu-id="66a25-148">这类似于 c # 语法。</span><span class="sxs-lookup"><span data-stu-id="66a25-148">This is similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableTest : test, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

### <a name="call-base-class-constructors"></a><span data-ttu-id="66a25-149">调用基类构造函数</span><span class="sxs-lookup"><span data-stu-id="66a25-149">Call base class constructors</span></span>

<span data-ttu-id="66a25-150">若要从子类调用基类构造函数，请添加 `base` 关键字，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="66a25-150">To call a base class constructor from a subclass, add the `base` keyword, as shown in the following example:</span></span>

```powershell
class A {
    [int]$a
    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

    [B]::new().a # return 103
```

<span data-ttu-id="66a25-151">如果基类具有默认构造函数 (没有) 的参数，则可以省略显式构造函数调用，如下所示。</span><span class="sxs-lookup"><span data-stu-id="66a25-151">If a base class has a default constructor (no parameters), you can omit an explicit constructor call, as shown.</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-methods"></a><span data-ttu-id="66a25-152">调用基类方法</span><span class="sxs-lookup"><span data-stu-id="66a25-152">Call base class methods</span></span>

<span data-ttu-id="66a25-153">你可以重写子类中的现有方法。</span><span class="sxs-lookup"><span data-stu-id="66a25-153">You can override existing methods in subclasses.</span></span> <span data-ttu-id="66a25-154">若要执行替代，请使用相同的名称和签名声明方法。</span><span class="sxs-lookup"><span data-stu-id="66a25-154">To do the override, declare methods by using the same name and signature.</span></span>

```powershell
class baseClass
{
    [int]days() {return 100500}
}
class childClass1 : baseClass
{
    [int]days () {return 200600}
}

    [childClass1]::new().days() # return 200600
```

<span data-ttu-id="66a25-155">若要从重写实现中调用基类方法，请在调用时强制转换为基类 `([baseclass]$this)` 。</span><span class="sxs-lookup"><span data-stu-id="66a25-155">To call base class methods from overridden implementations, cast to the base class `([baseclass]$this)` on invocation.</span></span>

```powershell
class childClass2 : baseClass
{
    [int]days()
    {
        return 3 * ([baseClass]$this).days()
    }
}

    [childClass2]::new().days() # return 301500
```

<span data-ttu-id="66a25-156">所有 PowerShell 方法都是虚拟的。</span><span class="sxs-lookup"><span data-stu-id="66a25-156">All PowerShell methods are virtual.</span></span> <span data-ttu-id="66a25-157">您可以使用与替代相同的语法来隐藏子类中的非虚拟 .NET 方法：使用相同的名称和签名声明方法。</span><span class="sxs-lookup"><span data-stu-id="66a25-157">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: declare methods with same name and signature.</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

### <a name="current-limitations-with-class-inheritance"></a><span data-ttu-id="66a25-158">类继承的当前限制</span><span class="sxs-lookup"><span data-stu-id="66a25-158">Current limitations with class inheritance</span></span>

<span data-ttu-id="66a25-159">类继承的限制是没有语法在 PowerShell 中声明接口。</span><span class="sxs-lookup"><span data-stu-id="66a25-159">A limitation with class inheritance is that there is no syntax to declare interfaces in PowerShell.</span></span>

## <a name="defining-custom-types-in-powershell"></a><span data-ttu-id="66a25-160">在 PowerShell 中定义自定义类型</span><span class="sxs-lookup"><span data-stu-id="66a25-160">Defining custom types in PowerShell</span></span>

<span data-ttu-id="66a25-161">Windows PowerShell 5.0 引入了几个语言元素。</span><span class="sxs-lookup"><span data-stu-id="66a25-161">Windows PowerShell 5.0 introduced several language elements.</span></span>

### <a name="class-keyword"></a><span data-ttu-id="66a25-162">Class 关键字</span><span class="sxs-lookup"><span data-stu-id="66a25-162">Class keyword</span></span>

<span data-ttu-id="66a25-163">定义一个新类。</span><span class="sxs-lookup"><span data-stu-id="66a25-163">Defines a new class.</span></span>
<span data-ttu-id="66a25-164">`class`关键字为 true .NET Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="66a25-164">The `class` keyword is a true .NET Framework type.</span></span>
<span data-ttu-id="66a25-165">类成员是公共的。</span><span class="sxs-lookup"><span data-stu-id="66a25-165">Class members are public.</span></span>

```powershell
class MyClass
{
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="66a25-166">Enum 关键字和枚举</span><span class="sxs-lookup"><span data-stu-id="66a25-166">Enum keyword and enumerations</span></span>

<span data-ttu-id="66a25-167">添加了对 `enum` 关键字的支持，这是一项重大更改。</span><span class="sxs-lookup"><span data-stu-id="66a25-167">Support for the `enum` keyword was added and is a breaking change.</span></span> <span data-ttu-id="66a25-168">`enum`分隔符当前为换行符。</span><span class="sxs-lookup"><span data-stu-id="66a25-168">The `enum` delimiter is currently a newline.</span></span> <span data-ttu-id="66a25-169">对于已在使用的用户来说，一种解决方法 `enum` 是在单词前面插入一个与号 (`&`) 。</span><span class="sxs-lookup"><span data-stu-id="66a25-169">A workaround for those who are already using `enum` is to insert an ampersand (`&`) before the word.</span></span> <span data-ttu-id="66a25-170">当前限制：你不能在自身中定义枚举器，但可以根据另一个枚举器对其进行初始化 `enum` `enum` ，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="66a25-170">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize `enum` in terms of another `enum`, as shown in the following example:</span></span>

<span data-ttu-id="66a25-171">当前无法指定基类型。</span><span class="sxs-lookup"><span data-stu-id="66a25-171">The base type cannot currently be specified.</span></span> <span data-ttu-id="66a25-172">基类型始终为 [int]。</span><span class="sxs-lookup"><span data-stu-id="66a25-172">The base type is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="66a25-173">枚举器值必须是分析时间常量。</span><span class="sxs-lookup"><span data-stu-id="66a25-173">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="66a25-174">枚举器值不能设置为已调用的命令的结果。</span><span class="sxs-lookup"><span data-stu-id="66a25-174">The enumerator value cannot be set to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="66a25-175">`Enum` 支持算术运算，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="66a25-175">`Enum` supports arithmetic operations, as shown in the following example:</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="hidden-keyword"></a><span data-ttu-id="66a25-176">Hidden 关键字</span><span class="sxs-lookup"><span data-stu-id="66a25-176">Hidden keyword</span></span>

<span data-ttu-id="66a25-177">`hidden`Windows PowerShell 5.0 中引入的关键字隐藏默认结果中的类成员 `Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="66a25-177">The `hidden` keyword, introduced in Windows PowerShell 5.0, hides class members from default `Get-Member` results.</span></span> <span data-ttu-id="66a25-178">指定 hidden 属性，如以下行所示：</span><span class="sxs-lookup"><span data-stu-id="66a25-178">Specify the hidden property as shown in the following line:</span></span>

```powershell
hidden [type] $classmember = <value>
```

<span data-ttu-id="66a25-179">除非完成发生在定义隐藏成员的类中，否则不会使用 tab 自动补全或 IntelliSense 显示隐藏成员。</span><span class="sxs-lookup"><span data-stu-id="66a25-179">Hidden members are not displayed by using tab completion or IntelliSense, unless the completion occurs in the class that defines the hidden member.</span></span>

<span data-ttu-id="66a25-180">添加了新的属性 **system.management.automation.hiddenattribute**，以便 c # 代码可以在 PowerShell 中具有相同的语义。</span><span class="sxs-lookup"><span data-stu-id="66a25-180">A new attribute, **System.Management.Automation.HiddenAttribute**, was added, so that C# code can have the same semantics within PowerShell.</span></span>

<span data-ttu-id="66a25-181">有关详细信息，请参阅 [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md)。</span><span class="sxs-lookup"><span data-stu-id="66a25-181">For more information, see [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md).</span></span>

### <a name="import-dscresource"></a><span data-ttu-id="66a25-182">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="66a25-182">Import-DscResource</span></span>

<span data-ttu-id="66a25-183">`Import-DscResource` 现在是一个真正的动态关键字。</span><span class="sxs-lookup"><span data-stu-id="66a25-183">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="66a25-184">PowerShell 用于分析指定的模块的根模块，搜索包含 DscResource 属性的类。</span><span class="sxs-lookup"><span data-stu-id="66a25-184">PowerShell parses the specified module's root module, searching for classes that contain the DscResource attribute.</span></span>

### <a name="properties"></a><span data-ttu-id="66a25-185">属性</span><span class="sxs-lookup"><span data-stu-id="66a25-185">Properties</span></span>

<span data-ttu-id="66a25-186">新字段 `ImplementingAssembly` 已添加到中 `ModuleInfo` 。</span><span class="sxs-lookup"><span data-stu-id="66a25-186">A new field, `ImplementingAssembly`, was added to `ModuleInfo`.</span></span> <span data-ttu-id="66a25-187">如果脚本定义类，或将已加载的二进制模块的程序集 `ImplementingAssembly` 设置为为脚本模块创建的动态程序集。</span><span class="sxs-lookup"><span data-stu-id="66a25-187">If the script defines classes, or the loaded assembly for binary modules `ImplementingAssembly` is set to the dynamic assembly created for a script module.</span></span> <span data-ttu-id="66a25-188">当 ModuleType = Manifest 时，不会对该字段进行设置。</span><span class="sxs-lookup"><span data-stu-id="66a25-188">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="66a25-189">字段上的反射 `ImplementingAssembly` 发现模块中的资源。</span><span class="sxs-lookup"><span data-stu-id="66a25-189">Reflection on the `ImplementingAssembly` field discovers resources in a module.</span></span> <span data-ttu-id="66a25-190">这意味着你可以发现用 PowerShell 或其他托管语言编写的资源。</span><span class="sxs-lookup"><span data-stu-id="66a25-190">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="66a25-191">包含初始值设定项的字段。</span><span class="sxs-lookup"><span data-stu-id="66a25-191">Fields with initializers.</span></span>

`[int] $i = 5`

<span data-ttu-id="66a25-192">支持静态，其工作方式类似于类型约束，因此可按任意顺序指定。</span><span class="sxs-lookup"><span data-stu-id="66a25-192">Static is supported and works like an attribute, similar to the type constraints, so it can be specified in any order.</span></span>

`static [int] $count = 0`

<span data-ttu-id="66a25-193">可选类型。</span><span class="sxs-lookup"><span data-stu-id="66a25-193">A type is optional.</span></span>

`$s = "hello"`

<span data-ttu-id="66a25-194">所有成员都是公开的。</span><span class="sxs-lookup"><span data-stu-id="66a25-194">All members are public.</span></span> <span data-ttu-id="66a25-195">属性要求使用换行符或分号。</span><span class="sxs-lookup"><span data-stu-id="66a25-195">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="66a25-196">如果未指定任何对象类型，则属性类型为 **object**。</span><span class="sxs-lookup"><span data-stu-id="66a25-196">If no object type is specified, the property type is **Object**.</span></span>

### <a name="constructors-and-instantiation"></a><span data-ttu-id="66a25-197">构造函数和实例化</span><span class="sxs-lookup"><span data-stu-id="66a25-197">Constructors and instantiation</span></span>

<span data-ttu-id="66a25-198">PowerShell 类可具有与类具有相同名称的构造函数。</span><span class="sxs-lookup"><span data-stu-id="66a25-198">PowerShell classes can have constructors that have the same name as their class.</span></span> <span data-ttu-id="66a25-199">这些构造函数可进行重载。</span><span class="sxs-lookup"><span data-stu-id="66a25-199">Constructors can be overloaded.</span></span> <span data-ttu-id="66a25-200">支持静态构造函数。</span><span class="sxs-lookup"><span data-stu-id="66a25-200">Static constructors are supported.</span></span>
<span data-ttu-id="66a25-201">在运行构造函数中的任何代码之前，将初始化具有初始化表达式的属性。</span><span class="sxs-lookup"><span data-stu-id="66a25-201">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="66a25-202">静态属性在静态构造函数的主体之前进行初始化，而实例属性则在非静态构造函数的主体之前进行初始化。</span><span class="sxs-lookup"><span data-stu-id="66a25-202">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="66a25-203">目前，没有用于从另一个构造函数（如 c # 语法）调用构造函数的语法： `": this()")` 。</span><span class="sxs-lookup"><span data-stu-id="66a25-203">Currently, there is no syntax for calling a constructor from another constructor such as the C# syntax: `": this()")`.</span></span> <span data-ttu-id="66a25-204">解决方法是定义一种常用的 Init 方法。</span><span class="sxs-lookup"><span data-stu-id="66a25-204">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="66a25-205">下面是实例化类的方法：</span><span class="sxs-lookup"><span data-stu-id="66a25-205">The following are ways of instantiating classes:</span></span>

- <span data-ttu-id="66a25-206">使用默认构造函数实例化。</span><span class="sxs-lookup"><span data-stu-id="66a25-206">Instantiating by using the default constructor.</span></span> <span data-ttu-id="66a25-207">请注意， `New-Object` 在此版本中不受支持。</span><span class="sxs-lookup"><span data-stu-id="66a25-207">Note that `New-Object` is not supported in this release.</span></span>

  `$a = [MyClass]::new()`

- <span data-ttu-id="66a25-208">使用参数调用构造函数。</span><span class="sxs-lookup"><span data-stu-id="66a25-208">Calling a constructor with a parameter.</span></span>

  `$b = [MyClass]::new(42)`

- <span data-ttu-id="66a25-209">将数组传递给带多个参数的构造函数</span><span class="sxs-lookup"><span data-stu-id="66a25-209">Passing an array to a constructor with multiple parameters</span></span>

  `$c = [MyClass]::new(@(42,43,44), "Hello")`

<span data-ttu-id="66a25-210">对于此版本，类型名称只在词法上可见，这意味着它在定义类的模块或脚本外部不可见。</span><span class="sxs-lookup"><span data-stu-id="66a25-210">For this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="66a25-211">函数可以返回在 PowerShell 中定义的类的实例，并且实例在模块或脚本的外部工作良好。</span><span class="sxs-lookup"><span data-stu-id="66a25-211">Functions can return instances of a class defined in PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="66a25-212">`Get-Member`**静态** 参数列出了构造函数，因此可以像其他方法一样查看重载。</span><span class="sxs-lookup"><span data-stu-id="66a25-212">The `Get-Member` **Static** parameter lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="66a25-213">此语法的性能比 `New-Object` 快得多。</span><span class="sxs-lookup"><span data-stu-id="66a25-213">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

<span data-ttu-id="66a25-214">名为 **new** 的伪静态方法适用于 .NET 类型，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="66a25-214">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span> `[hashtable]::new()`

<span data-ttu-id="66a25-215">你现在可以使用 `Get-Member` 查看构造函数重载，或如此示例所示：</span><span class="sxs-lookup"><span data-stu-id="66a25-215">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
[hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

### <a name="methods"></a><span data-ttu-id="66a25-216">方法</span><span class="sxs-lookup"><span data-stu-id="66a25-216">Methods</span></span>

<span data-ttu-id="66a25-217">PowerShell 类方法被实现为仅有一个结束块的 ScriptBlock。</span><span class="sxs-lookup"><span data-stu-id="66a25-217">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="66a25-218">所有方法都是公开的。</span><span class="sxs-lookup"><span data-stu-id="66a25-218">All methods are public.</span></span> <span data-ttu-id="66a25-219">下面介绍了定义一个名为 **DoSomething** 的方法的示例。</span><span class="sxs-lookup"><span data-stu-id="66a25-219">The following shows an example of defining a method named **DoSomething**.</span></span>

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x)       # method syntax
    }
    private _doSomething($a) {}
}
```

### <a name="method-invocation"></a><span data-ttu-id="66a25-220">方法调用</span><span class="sxs-lookup"><span data-stu-id="66a25-220">Method invocation</span></span>

<span data-ttu-id="66a25-221">支持重载方法。</span><span class="sxs-lookup"><span data-stu-id="66a25-221">Overloaded methods are supported.</span></span> <span data-ttu-id="66a25-222">重载方法与现有方法命名相同，但由其指定的值区分。</span><span class="sxs-lookup"><span data-stu-id="66a25-222">Overloaded methods are named the same as an existing method but differentiated by their specified values.</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

### <a name="invocation"></a><span data-ttu-id="66a25-223">调用</span><span class="sxs-lookup"><span data-stu-id="66a25-223">Invocation</span></span>

<span data-ttu-id="66a25-224">请参阅 [方法调用](#method-invocation)。</span><span class="sxs-lookup"><span data-stu-id="66a25-224">See [Method invocation](#method-invocation).</span></span>

### <a name="attributes"></a><span data-ttu-id="66a25-225">特性</span><span class="sxs-lookup"><span data-stu-id="66a25-225">Attributes</span></span>

<span data-ttu-id="66a25-226">添加了三个新属性： `DscResource` 、 `DscResourceKey` 和 `DscResourceMandatory` 。</span><span class="sxs-lookup"><span data-stu-id="66a25-226">Three new attributes were added: `DscResource`, `DscResourceKey`, and `DscResourceMandatory`.</span></span>

### <a name="return-types"></a><span data-ttu-id="66a25-227">返回类型</span><span class="sxs-lookup"><span data-stu-id="66a25-227">Return types</span></span>

<span data-ttu-id="66a25-228">返回类型是一种构造。</span><span class="sxs-lookup"><span data-stu-id="66a25-228">Return type is a contract.</span></span> <span data-ttu-id="66a25-229">返回值将被转换为预期类型。</span><span class="sxs-lookup"><span data-stu-id="66a25-229">The return value is converted to the expected type.</span></span>
<span data-ttu-id="66a25-230">如果没有指定返回类型，则返回类型为 void。</span><span class="sxs-lookup"><span data-stu-id="66a25-230">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="66a25-231">不能有意或无意地将对象和对象的流式处理写入管道。</span><span class="sxs-lookup"><span data-stu-id="66a25-231">There is no streaming of objects and objects cannot be written to the pipeline either intentionally or by accident.</span></span>

### <a name="lexical-scoping-of-variables"></a><span data-ttu-id="66a25-232">变量的词法作用域</span><span class="sxs-lookup"><span data-stu-id="66a25-232">Lexical scoping of variables</span></span>

<span data-ttu-id="66a25-233">下例介绍了词法作用域在此版本中的工作原理。</span><span class="sxs-lookup"><span data-stu-id="66a25-233">The following shows an example of how lexical scoping works in this release.</span></span>

```powershell
$d = 42  # Script scope

function bar
{
    $d = 0  # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d  # error, not found dynamically
        return $script:d # no error

        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="example-create-custom-classes"></a><span data-ttu-id="66a25-234">示例：创建自定义类</span><span class="sxs-lookup"><span data-stu-id="66a25-234">Example: Create custom classes</span></span>

<span data-ttu-id="66a25-235">下面的示例创建了几个新的自定义类来实现 HTML 动态样式表语言 (DSL) 。</span><span class="sxs-lookup"><span data-stu-id="66a25-235">The following example creates several new, custom classes to implement an HTML Dynamic Stylesheet Language (DSL).</span></span> <span data-ttu-id="66a25-236">由于不能在模块的范围之外使用类型，因此该示例添加了 helper 函数来创建特定的元素类型作为元素类的一部分（如标题样式和表）。</span><span class="sxs-lookup"><span data-stu-id="66a25-236">The example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

```powershell
# Classes that define the structure of the document
#
class Html
{
    [string] $docType
    [HtmlHead] $Head
    [Element[]] $Body

    [string] Render()
    {
        $text = "<html>`n<head>`n"
        $text += $Head
        $text += "`n</head>`n<body>`n"
        $text += $Body -join "`n" # Render all of the body elements
        $text += "</body>`n</html>"
        return $text
    }
    [string] ToString() { return $this.Render() }
}

class HtmlHead
{
    $Title
    $Base
    $Link
    $Style
    $Meta
    $Script
    [string] Render() { return "<title>$Title</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($Attributes)
        {
            foreach ($attr in $Attributes.Keys)
            {
                $attributesText = " $attr=`"$($Attributes[$attr])`""
            }
        }

        return "<${tag}${attributesText}>$text</$tag>`n"
    }
    [string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren't visible outside of the module.
#
function H1 {[Element] @{Tag = "H1"; Text = $args.foreach{$_} -join " "}}
function H2 {[Element] @{Tag = "H2"; Text = $args.foreach{$_} -join " "}}
function H3 {[Element] @{Tag = "H3"; Text = $args.foreach{$_} -join " "}}
function P  {[Element] @{Tag = "P" ; Text = $args.foreach{$_} -join " "}}
function B  {[Element] @{Tag = "B" ; Text = $args.foreach{$_} -join " "}}
function I  {[Element] @{Tag = "I" ; Text = $args.foreach{$_} -join " "}}
function HREF
{
    param (
        $Name,
        $Link
    )

    return [Element] @{
        Tag = "A"
        Attributes = @{ HREF = $link }
        Text = $name
    }
}
function Table
{
    param (
        [Parameter(Mandatory)]
        [object[]]
            $Data,
        [Parameter()]
        [string[]]
            $Properties = "*",
        [Parameter()]
        [hashtable]
            $Attributes = @{ border=2; cellpadding=2; cellspacing=2 }
    )

    $bodyText = ""
    # Add the header tags
    $bodyText +=  $Properties.foreach{TH $_}
    # Add the rows
    $bodyText += foreach ($row in $Data)
                {
                            TR (-join $Properties.Foreach{ TD ($row.$_) } )
                }

    $table = [Element] @{
                Tag = "Table"
                Attributes = $Attributes
                Text = $bodyText
            }
    $table
}
function TH  {([Element] @{Tag="TH"; Text=$args.foreach{$_} -join " "})}
function TR  {([Element] @{Tag="TR"; Text=$args.foreach{$_} -join " "})}
function TD  {([Element] @{Tag="TD"; Text=$args.foreach{$_} -join " "})}

function Style
{
    return  [Element]  @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```

## <a name="see-also"></a><span data-ttu-id="66a25-237">请参阅</span><span class="sxs-lookup"><span data-stu-id="66a25-237">See also</span></span>

[<span data-ttu-id="66a25-238">about_Enum</span><span class="sxs-lookup"><span data-stu-id="66a25-238">about_Enum</span></span>](../../Microsoft.PowerShell.Core/About/about_Enum.md)

[<span data-ttu-id="66a25-239">about_Hidden</span><span class="sxs-lookup"><span data-stu-id="66a25-239">about_Hidden</span></span>](../../Microsoft.PowerShell.Core/About/about_hidden.md)

[<span data-ttu-id="66a25-240">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="66a25-240">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="66a25-241">about_Methods</span><span class="sxs-lookup"><span data-stu-id="66a25-241">about_Methods</span></span>](../../Microsoft.PowerShell.Core/About/about_Methods.md)

[<span data-ttu-id="66a25-242">构建自定义 PowerShell 所需状态配置资源</span><span class="sxs-lookup"><span data-stu-id="66a25-242">Build Custom PowerShell Desired State Configuration Resources</span></span>](/powershell/scripting/dsc/resources/authoringResource)

