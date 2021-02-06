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
# <a name="about-classes-and-desired-state-configuration"></a>关于类和所需状态配置

## <a name="short-description"></a>简短说明

介绍如何在 PowerShell 中使用所需状态配置 (DSC) 在 PowerShell 中进行开发。

## <a name="long-description"></a>长说明

从 Windows PowerShell 5.0 开始，添加语言以定义类和其他用户定义的类型，方法是使用类似于其他面向对象的编程语言的正式语法和语义。 其目标是使开发人员和 IT 专业人员能够在更广泛的用例中使用 PowerShell，从而简化 PowerShell 项目（如 DSC 资源）的开发，并加速管理图面的覆盖面。

## <a name="supported-scenarios"></a>支持的方案

支持以下方案：

- 使用 PowerShell 语言定义 DSC 资源及其关联的类型。
- 使用熟悉的面向对象的编程构造（例如类、属性、方法和继承）在 PowerShell 中定义自定义类型。
- 使用 PowerShell 语言调试类型。
- 使用正式的机制以及适当的级别生成和处理异常。

## <a name="define-dsc-resources-with-classes"></a>用类定义 DSC 资源

除了语法更改之外，类定义的 DSC 资源和 cmdlet DSC 资源提供程序之间的主要区别是以下各项：

- 不需要 MOF) 文件 (管理对象格式。
- 模块文件中的 DSCResource 子文件夹不是必需的。
- PowerShell 模块文件可以包含多个 DSC 资源类。

## <a name="create-a-class-defined-dsc-resource-provider"></a>创建类定义的 DSC 资源提供程序

下面的示例是一个类定义的 DSC 资源提供程序，它保存为模块 Mydscresource.psd1。 必须始终在类定义的 DSC 资源提供程序中包含密钥属性。

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

## <a name="create-a-module-manifest"></a>创建模块清单

在创建类定义的 DSC 资源提供程序并将其另存为模块之后，为该模块创建一个模块清单。 若要让基于类的资源对 DSC 引擎可用，你必须在清单文件中添加 `DscResourcesToExport` 声明，以指示模块导出资源。 在此示例中，下面的模块清单另存为 MyDscResource.psd1。

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

## <a name="deploy-a-dsc-resource-provider"></a>部署 DSC 资源提供程序

通过在或中创建 Mydscresource.psd1 文件夹部署新的 DSC 资源提供程序 `$pshome\Modules` `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules` 。

你不需要创建一个 DSCResource 子文件夹。 将模块和模块清单文件（MyDscResource.psm1 和 MyDscResource.psd1）复制到 MyDscResource 文件夹。

从这时开始，你可以像对其他 DSC 资源进行的操作一样，创建并运行配置脚本。

## <a name="create-a-dsc-configuration-script"></a>创建 DSC 配置脚本

如前面所述，将类和清单文件保存到文件夹结构中之后，就可以创建一个使用新资源的配置。 以下配置引用 Mydscresource.psd1 模块。 将配置保存为脚本，MyResource.ps1。

有关如何运行 DSC 配置的信息，请参阅 [Windows PowerShell Desired State Configuration 概述](/powershell/scripting/dsc/overview/dscforengineers)。

在运行配置之前，请创建 `C:\test.txt` 。 此配置将检查文件是否存在于中 `c:\test\test.txt` 。 如果文件不存在，则配置从复制文件 `C:\test.txt` 。

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

像运行任何 DSC 配置脚本一样运行此脚本。 若要启动配置，请在提升的 PowerShell 控制台中运行以下内容：

`PS C:\test> .\MyResource.ps1`

## <a name="inheritance-in-powershell-classes"></a>PowerShell 类中的继承

### <a name="declare-base-classes-for-powershell-classes"></a>为 PowerShell 类声明基类

可以将 PowerShell 类声明为另一个 PowerShell 类的基类型，如下面的示例所示，其中， **水果** 是 **apple** 的基类型。

```powershell
class fruit
{
    [int]sold() {return 100500}
}

class apple : fruit {}
    [apple]::new().sold() # return 100500
```

### <a name="declare-implemented-interfaces-for-powershell-classes"></a>为 PowerShell 类声明实现的接口

可以在基类型后声明实现的接口，也可以在冒号 (`:`) 如果未指定任何基类型，则为。 使用逗号分隔所有类型名称。 这类似于 c # 语法。

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

### <a name="call-base-class-constructors"></a>调用基类构造函数

若要从子类调用基类构造函数，请添加 `base` 关键字，如以下示例中所示：

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

如果基类具有默认构造函数 (没有) 的参数，则可以省略显式构造函数调用，如下所示。

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-methods"></a>调用基类方法

你可以重写子类中的现有方法。 若要执行替代，请使用相同的名称和签名声明方法。

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

若要从重写实现中调用基类方法，请在调用时强制转换为基类 `([baseclass]$this)` 。

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

所有 PowerShell 方法都是虚拟的。 您可以使用与替代相同的语法来隐藏子类中的非虚拟 .NET 方法：使用相同的名称和签名声明方法。

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

### <a name="current-limitations-with-class-inheritance"></a>类继承的当前限制

类继承的限制是没有语法在 PowerShell 中声明接口。

## <a name="defining-custom-types-in-powershell"></a>在 PowerShell 中定义自定义类型

Windows PowerShell 5.0 引入了几个语言元素。

### <a name="class-keyword"></a>Class 关键字

定义一个新类。
`class`关键字为 true .NET Framework 类型。
类成员是公共的。

```powershell
class MyClass
{
}
```

### <a name="enum-keyword-and-enumerations"></a>Enum 关键字和枚举

添加了对 `enum` 关键字的支持，这是一项重大更改。 `enum`分隔符当前为换行符。 对于已在使用的用户来说，一种解决方法 `enum` 是在单词前面插入一个与号 (`&`) 。 当前限制：你不能在自身中定义枚举器，但可以根据另一个枚举器对其进行初始化 `enum` `enum` ，如以下示例中所示：

当前无法指定基类型。 基类型始终为 [int]。

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

枚举器值必须是分析时间常量。 枚举器值不能设置为已调用的命令的结果。

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

`Enum` 支持算术运算，如以下示例中所示：

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="hidden-keyword"></a>Hidden 关键字

`hidden`Windows PowerShell 5.0 中引入的关键字隐藏默认结果中的类成员 `Get-Member` 。 指定 hidden 属性，如以下行所示：

```powershell
hidden [type] $classmember = <value>
```

除非完成发生在定义隐藏成员的类中，否则不会使用 tab 自动补全或 IntelliSense 显示隐藏成员。

添加了新的属性 **system.management.automation.hiddenattribute**，以便 c # 代码可以在 PowerShell 中具有相同的语义。

有关详细信息，请参阅 [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md)。

### <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource` 现在是一个真正的动态关键字。 PowerShell 用于分析指定的模块的根模块，搜索包含 DscResource 属性的类。

### <a name="properties"></a>属性

新字段 `ImplementingAssembly` 已添加到中 `ModuleInfo` 。 如果脚本定义类，或将已加载的二进制模块的程序集 `ImplementingAssembly` 设置为为脚本模块创建的动态程序集。 当 ModuleType = Manifest 时，不会对该字段进行设置。

字段上的反射 `ImplementingAssembly` 发现模块中的资源。 这意味着你可以发现用 PowerShell 或其他托管语言编写的资源。

包含初始值设定项的字段。

`[int] $i = 5`

支持静态，其工作方式类似于类型约束，因此可按任意顺序指定。

`static [int] $count = 0`

可选类型。

`$s = "hello"`

所有成员都是公开的。 属性要求使用换行符或分号。 如果未指定任何对象类型，则属性类型为 **object**。

### <a name="constructors-and-instantiation"></a>构造函数和实例化

PowerShell 类可具有与类具有相同名称的构造函数。 这些构造函数可进行重载。 支持静态构造函数。
在运行构造函数中的任何代码之前，将初始化具有初始化表达式的属性。 静态属性在静态构造函数的主体之前进行初始化，而实例属性则在非静态构造函数的主体之前进行初始化。 目前，没有用于从另一个构造函数（如 c # 语法）调用构造函数的语法： `": this()")` 。 解决方法是定义一种常用的 Init 方法。

下面是实例化类的方法：

- 使用默认构造函数实例化。 请注意， `New-Object` 在此版本中不受支持。

  `$a = [MyClass]::new()`

- 使用参数调用构造函数。

  `$b = [MyClass]::new(42)`

- 将数组传递给带多个参数的构造函数

  `$c = [MyClass]::new(@(42,43,44), "Hello")`

对于此版本，类型名称只在词法上可见，这意味着它在定义类的模块或脚本外部不可见。 函数可以返回在 PowerShell 中定义的类的实例，并且实例在模块或脚本的外部工作良好。

`Get-Member`**静态** 参数列出了构造函数，因此可以像其他方法一样查看重载。 此语法的性能比 `New-Object` 快得多。

名为 **new** 的伪静态方法适用于 .NET 类型，如下面的示例中所示。 `[hashtable]::new()`

你现在可以使用 `Get-Member` 查看构造函数重载，或如此示例所示：

```powershell
[hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

### <a name="methods"></a>方法

PowerShell 类方法被实现为仅有一个结束块的 ScriptBlock。 所有方法都是公开的。 下面介绍了定义一个名为 **DoSomething** 的方法的示例。

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

### <a name="method-invocation"></a>方法调用

支持重载方法。 重载方法与现有方法命名相同，但由其指定的值区分。

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

### <a name="invocation"></a>调用

请参阅 [方法调用](#method-invocation)。

### <a name="attributes"></a>特性

添加了三个新属性： `DscResource` 、 `DscResourceKey` 和 `DscResourceMandatory` 。

### <a name="return-types"></a>返回类型

返回类型是一种构造。 返回值将被转换为预期类型。
如果没有指定返回类型，则返回类型为 void。 不能有意或无意地将对象和对象的流式处理写入管道。

### <a name="lexical-scoping-of-variables"></a>变量的词法作用域

下例介绍了词法作用域在此版本中的工作原理。

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

## <a name="example-create-custom-classes"></a>示例：创建自定义类

下面的示例创建了几个新的自定义类来实现 HTML 动态样式表语言 (DSL) 。 由于不能在模块的范围之外使用类型，因此该示例添加了 helper 函数来创建特定的元素类型作为元素类的一部分（如标题样式和表）。

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

## <a name="see-also"></a>请参阅

[about_Enum](../../Microsoft.PowerShell.Core/About/about_Enum.md)

[about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Methods](../../Microsoft.PowerShell.Core/About/about_Methods.md)

[构建自定义 PowerShell 所需状态配置资源](/powershell/scripting/dsc/resources/authoringResource)

