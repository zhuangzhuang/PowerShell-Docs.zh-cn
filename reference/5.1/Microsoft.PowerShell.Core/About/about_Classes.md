---
description: 描述如何使用类创建自己的自定义类型。
Locale: en-US
ms.date: 01/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_classes?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes
ms.openlocfilehash: 6459ee4e80515360dcd1c16ac027ead8fa17bacc
ms.sourcegitcommit: 94d597c4fb38793bc49ca7610e2c9973b1e577c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/21/2021
ms.locfileid: "98620075"
---
# <a name="about-classes"></a>关于类

## <a name="short-description"></a>简短说明
描述如何使用类创建自己的自定义类型。

## <a name="long-description"></a>长说明

PowerShell 5.0 添加了一种正式的语法来定义类和其他用户定义类型。 通过添加类，开发人员和 IT 专业人员可以将 PowerShell 用于更广泛的用例。 它简化了 PowerShell 项目的开发并加快了管理面的覆盖范围。

类声明是一个蓝图，用于在运行时创建对象的实例。 在定义类时，类名称是类型的名称。 例如，如果声明名为 **device** 的类并将变量初始化 `$dev` 为 **设备** 的新实例， `$dev` 则为 **设备** 类型的对象或实例。 **设备** 的每个实例都可以在其属性中具有不同的值。

## <a name="supported-scenarios"></a>支持的方案

- 使用熟悉的面向对象的编程语义（如类、属性、方法、继承等）在 PowerShell 中定义自定义类型。
- 使用 PowerShell 语言调试类型。
- 使用正式的机制生成并处理异常。
- 使用 PowerShell 语言定义 DSC 资源及其关联的类型。

## <a name="syntax"></a>语法

使用以下语法声明类：

```syntax
class <class-name> [: [<base-class>][,<interface-list]] {
    [[<attribute>] [hidden] [static] <property-definition> ...]
    [<class-name>([<constructor-argument-list>])
      {<constructor-statement-list>} ...]
    [[<attribute>] [hidden] [static] <method-definition> ...]
}
```

使用以下语法之一对类进行实例化：

```syntax
[$<variable-name> =] New-Object -TypeName <class-name> [
  [-ArgumentList] <constructor-argument-list>]
```

```syntax
[$<variable-name> =] [<class-name>]::new([<constructor-argument-list>])
```

> [!NOTE]
> 使用语法时 `[<class-name>]::new()` ，类名称的两侧的方括号是必需的。 括号指示 PowerShell 的类型定义。

### <a name="example-syntax-and-usage"></a>示例语法和用法

此示例显示创建可用类所需的最少语法。

```powershell
class Device {
    [string]$Brand
}

$dev = [Device]::new()
$dev.Brand = "Microsoft"
$dev
```

```Output
Brand
-----
Microsoft
```

## <a name="class-properties"></a>类属性

属性是在类范围中声明的变量。 属性可以是任何内置类型，也可以是其他类的实例。 类的属性数量没有限制。

### <a name="example-class-with-simple-properties"></a>带有简单属性的示例类

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

$device = [Device]::new()
$device.Brand = "Microsoft"
$device.Model = "Surface Pro 4"
$device.VendorSku = "5072641000"

$device
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-complex-types-in-class-properties"></a>类属性中的复杂类型示例

此示例使用 **Device** 类定义一个空 **机架** 类。 下面的示例演示如何将设备添加到机架，以及如何从预加载的机架开始。

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

class Rack {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new(8)

}

$rack = [Rack]::new()

$rack
```

```Output

Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, $null, $null...}


```

## <a name="class-methods"></a>类方法

方法定义类可以执行的操作。 方法可能采用提供输入数据的参数。 方法可以返回输出。 方法返回的数据可以是任何定义的数据类型。

定义类的方法时，可以使用自动变量引用当前类对象 `$this` 。 这允许您访问在当前类中定义的属性和其他方法。

### <a name="example-simple-class-with-properties-and-methods"></a>具有属性和方法的示例简单类

扩展 **机架** 类以在其中添加和删除设备。

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    [string]ToString(){
        return ("{0}|{1}|{2}" -f $this.Brand, $this.Model, $this.VendorSku)
    }
}

class Rack {
    [int]$Slots = 8
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void]RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }

    [int[]] GetAvailableSlots(){
        [int]$i = 0
        return @($this.Devices.foreach{ if($_ -eq $null){$i}; $i++})
    }
}

$rack = [Rack]::new()

$surface = [Device]::new()
$surface.Brand = "Microsoft"
$surface.Model = "Surface Pro 4"
$surface.VendorSku = "5072641000"

$rack.AddDevice($surface, 2)

$rack
$rack.GetAvailableSlots()
```

```Output

Slots     : 8
Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, Microsoft|Surface Pro 4|5072641000, $null...}

0
1
3
4
5
6
7

```

## <a name="output-in-class-methods"></a>类方法中的输出

方法应具有定义的返回类型。 如果方法不返回 output，则输出类型应为 `[void]` 。

在类方法中，除了语句中提到的对象之外，不会向管道发送任何对象 `return` 。 不会从代码中意外输出到管道。

> [!NOTE]
> 这在本质上与 PowerShell 函数处理输出的方式不同，其中一切都进入管道。

从类方法内部写入错误流的非终止错误不会通过。 必须使用 `throw` 来呈现终止错误。
使用 `Write-*` cmdlet，您仍然可以从类方法中写入 PowerShell 的输出流。 但是，应避免使用此方法，以便方法仅使用语句发出对象 `return` 。

### <a name="method-output"></a>方法输出

此示例演示除了语句外，不会从类方法中意外输出到管道 `return` 。

```powershell
class FunWithIntegers
{
    [int[]]$Integers = 0..10

    [int[]]GetOddIntegers(){
        return $this.Integers.Where({ ($_ % 2) })
    }

    [void] GetEvenIntegers(){
        # this following line doesn't go to the pipeline
        $this.Integers.Where({ ($_ % 2) -eq 0})
    }

    [string]SayHello(){
        # this following line doesn't go to the pipeline
        "Good Morning"

        # this line goes to the pipeline
        return "Hello World"
    }
}

$ints = [FunWithIntegers]::new()
$ints.GetOddIntegers()
$ints.GetEvenIntegers()
$ints.SayHello()
```

```Output
1
3
5
7
9
Hello World

```

## <a name="constructor"></a>构造函数

构造函数使你能够在创建类的实例时设置默认值和验证对象逻辑。 构造函数具有与类相同的名称。 构造函数可能具有参数，用于初始化新对象的数据成员。

类可以定义零个或多个构造函数。 如果未定义任何构造函数，则将为该类提供默认的无参数构造函数。 此构造函数将所有成员初始化为其默认值。 为对象类型和字符串提供了 null 值。 定义构造函数时，不会创建默认的无参数构造函数。 如果需要，请创建一个无参数的构造函数。

### <a name="constructor-basic-syntax"></a>构造函数基本语法

在此示例中，设备类是使用属性和构造函数定义的。
若要使用此类，用户需要为构造函数中列出的参数提供值。

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$surface
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-with-multiple-constructors"></a>具有多个构造函数的示例

在此示例中，使用属性、默认构造函数和构造函数来定义 **设备** 类以初始化实例。

默认构造函数将该 **品牌** 设置为 **Undefined**，并将 **模型** 和 **供应商-sku** 保留为 null 值。

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(){
        $this.Brand = 'Undefined'
    }

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$somedevice = [Device]::new()
[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$somedevice
$surface
```

```Output
Brand       Model           VendorSku
-----       -----           ---------
Undefined
Microsoft   Surface Pro 4   5072641000
```

## <a name="hidden-attribute"></a>隐藏属性

`hidden`属性隐藏属性或方法。 用户仍可访问该属性或方法，并且在该对象可用的所有范围内均可用。 隐藏的成员在 cmdlet 中是隐藏的 `Get-Member` ，不能在类定义之外使用 tab 自动补全或 IntelliSense 来显示。

有关详细信息，请参阅 [About_hidden](About_hidden.md)。

### <a name="example-using-hidden-attributes"></a>使用隐藏特性的示例

创建 **机架** 对象时，设备的槽数是固定值，不应在任何时间更改。 此值在创建时是已知的。

使用 hidden 属性允许开发人员保持隐藏的槽数，并防止意外更改机架的大小。

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    [int] hidden $Slots = 8
    [string]$Brand
    [string]$Model
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)
    }
}

[Rack]$r1 = [Rack]::new("Microsoft", "Surface Pro 4", 16)

$r1
$r1.Devices.Length
$r1.Slots
```

```Output
Brand     Model         Devices
-----     -----         -------
Microsoft Surface Pro 4 {$null, $null, $null, $null...}
16
16
```

"公告 **槽** " 属性未显示在 `$r1` 输出中。 但是，该大小已由构造函数更改。

## <a name="static-attribute"></a>静态属性

`static`特性定义类中存在的属性或方法，无需任何实例。

静态属性始终可用，与类实例化无关。 静态属性跨类的所有实例共享。 静态方法始终可用。 整个会话范围内的所有静态属性。

### <a name="example-using-static-attributes-and-methods"></a>使用静态属性和方法的示例

假设你的数据中心中存在此处实例化的机架。 因此，您希望在代码中跟踪机架。

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    hidden [int] $Slots = 8
    static [Rack[]]$InstalledRacks = @()
    [string]$Brand
    [string]$Model
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [string]$id, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.AssetId = $id
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)

        ## add rack to installed racks
        [Rack]::InstalledRacks += $this
    }

    static [void]PowerOffRacks(){
        foreach ($rack in [Rack]::InstalledRacks) {
            Write-Warning ("Turning off rack: " + ($rack.AssetId))
        }
    }
}
```

### <a name="testing-static-property-and-method-exist"></a>测试静态属性和方法存在

```
PS> [Rack]::InstalledRacks.Length
0

PS> [Rack]::PowerOffRacks()

PS> (1..10) | ForEach-Object {
>>   [Rack]::new("Adatum Corporation", "Standard-16",
>>     $_.ToString("Std0000"), 16)
>> } > $null

PS> [Rack]::InstalledRacks.Length
10

PS> [Rack]::InstalledRacks[3]
Brand              Model       AssetId Devices
-----              -----       ------- -------
Adatum Corporation Standard-16 Std0004 {$null, $null, $null, $null...}

PS> [Rack]::PowerOffRacks()
WARNING: Turning off rack: Std0001
WARNING: Turning off rack: Std0002
WARNING: Turning off rack: Std0003
WARNING: Turning off rack: Std0004
WARNING: Turning off rack: Std0005
WARNING: Turning off rack: Std0006
WARNING: Turning off rack: Std0007
WARNING: Turning off rack: Std0008
WARNING: Turning off rack: Std0009
WARNING: Turning off rack: Std0010
```

请注意，每次运行此示例时，机架数都会增加。

## <a name="property-validation-attributes"></a>属性验证特性

通过验证特性，可以测试为属性指定的值是否满足定义的要求。 在分配值时触发验证。 请参阅 [about_functions_advanced_parameters](about_functions_advanced_parameters.md)。

### <a name="example-using-validation-attributes"></a>使用验证特性的示例

```powershell
class Device {
    [ValidateNotNullOrEmpty()][string]$Brand
    [ValidateNotNullOrEmpty()][string]$Model
}

[Device]$dev = [Device]::new()

Write-Output "Testing dev"
$dev

$dev.Brand = ""
```

```Output
Testing dev

Brand Model
----- -----

Exception setting "Brand": "The argument is null or empty. Provide an
argument that is not null or empty, and then try the command again."
At C:\tmp\Untitled-5.ps1:11 char:1
+ $dev.Brand = ""
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], SetValueInvocationException
    + FullyQualifiedErrorId : ExceptionWhenSetting
```

## <a name="inheritance-in-powershell-classes"></a>PowerShell 类中的继承

可以通过创建从现有类派生的新类来扩展类。 派生类继承基类的属性。 您可以根据需要添加或重写方法和属性。

PowerShell 不支持多重继承。 类不能从多个类继承。 不过，您可以使用接口来实现此目的。

继承实现由 `:` 运算符定义; 这意味着扩展此类或实现这些接口。 派生类应始终在类声明中的最左侧。

### <a name="example-using-simple-inheritance-syntax"></a>使用简单继承语法的示例

此示例显示了简单的 PowerShell 类继承语法。

```powershell
Class Derived : Base {...}
```

此示例演示了具有基类的接口声明的继承。

```powershell
Class Derived : Base, Interface {...}
```

### <a name="example-of-simple-inheritance-in-powershell-classes"></a>PowerShell 类中的简单继承示例

在此示例中，在前面的示例中使用的 **机架** 和 **设备** 类更好地定义为：避免属性重复，更好地对齐通用属性，并重复使用常见业务逻辑。

数据中心内的大多数对象都是公司资产，因此，开始将其作为资产进行跟踪是有意义的。 设备类型由 `DeviceType` 枚举定义，有关枚举的详细信息，请参阅 [about_Enum](about_Enum.md) 。

在我们的示例中，我们仅定义 `Rack` 和 `ComputeServer` ; 这两个扩展都是 `Device` 类的。

```powershell
enum DeviceType {
    Undefined = 0
    Compute = 1
    Storage = 2
    Networking = 4
    Communications = 8
    Power = 16
    Rack = 32
}

class Asset {
    [string]$Brand
    [string]$Model
}

class Device : Asset {
    hidden [DeviceType]$devtype = [DeviceType]::Undefined
    [string]$Status

    [DeviceType] GetDeviceType(){
        return $this.devtype
    }
}

class ComputeServer : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Compute
    [string]$ProcessorIdentifier
    [string]$Hostname
}

class Rack : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Rack
    hidden [int]$Slots = 8

    [string]$Datacenter
    [string]$Location
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack (){
        ## Just create the default rack with 8 slots
    }

    Rack ([int]$s){
        ## Add argument validation logic here
        $this.Devices = [Device[]]::new($s)
    }

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void] RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }
}

$FirstRack = [Rack]::new(16)
$FirstRack.Status = "Operational"
$FirstRack.Datacenter = "PNW"
$FirstRack.Location = "F03R02.J10"

(0..15).ForEach({
    $ComputeServer = [ComputeServer]::new()
    $ComputeServer.Brand = "Fabrikam, Inc."       ## Inherited from Asset
    $ComputeServer.Model = "Fbk5040"              ## Inherited from Asset
    $ComputeServer.Status = "Installed"           ## Inherited from Device
    $ComputeServer.ProcessorIdentifier = "x64"    ## ComputeServer
    $ComputeServer.Hostname = ("r1s" + $_.ToString("000")) ## ComputeServer
    $FirstRack.AddDevice($ComputeServer, $_)
  })

$FirstRack
$FirstRack.Devices
```

```Output
Datacenter : PNW
Location   : F03R02.J10
Devices    : {r1s000, r1s001, r1s002, r1s003...}
Status     : Operational
Brand      :
Model      :

ProcessorIdentifier : x64
Hostname            : r1s000
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

ProcessorIdentifier : x64
Hostname            : r1s001
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

<... content truncated here for brevity ...>

ProcessorIdentifier : x64
Hostname            : r1s015
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040
```

### <a name="calling-base-class-constructors"></a>调用基类构造函数

若要从子类调用基类构造函数，请添加 `base` 关键字。

```powershell
class Person {
    [int]$Age

    Person([int]$a)
    {
        $this.Age = $a
    }
}

class Child : Person
{
    [string]$School

    Child([int]$a, [string]$s ) : base($a) {
        $this.School = $s
    }
}

[Child]$littleone = [Child]::new(10, "Silver Fir Elementary School")

$littleone.Age
```

```Output

10
```

### <a name="invoke-base-class-methods"></a>调用基类方法

若要重写子类中的现有方法，请使用相同的名称和签名声明方法。

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
}

[ChildClass1]::new().days()
```

```Output

2
```

若要从重写实现中调用基类方法，请在调用时强制转换为基类 ( [baseclass] $this) 。

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
    [int]basedays() {return ([BaseClass]$this).days()}
}

[ChildClass1]::new().days()
[ChildClass1]::new().basedays()
```

```Output

2
1
```

### <a name="inheriting-from-interfaces"></a>从接口继承

PowerShell 类可以使用用于扩展基类的相同继承语法来实现接口。 由于接口允许多个继承，因此，实现接口的 PowerShell 类可以从多个类型继承，方法是在冒号后 `:` 使用逗号 () 分隔类型名称 () `,` 。 实现接口的 PowerShell 类必须实现该接口的所有成员。 省略实现接口成员将导致脚本中出现分析时错误。

> [!NOTE]
> PowerShell 当前不支持在 PowerShell 脚本中声明新接口。

```powershell
class MyComparable : System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="importing-classes-from-a-powershell-module"></a>从 PowerShell 模块导入类

`Import-Module``#requires`语句仅导入模块定义的模块函数、别名和变量。 不导入类。 `using module`语句将导入模块中定义的类。 如果该模块未在当前会话中加载，则该 `using` 语句将失败。 有关语句的详细信息 `using` ，请参阅 [about_Using](about_Using.md)。

`using module`语句从根模块导入类 (`ModuleToProcess` 脚本模块或二进制模块的) 。 它不会始终导入嵌套模块中定义的类，也不会将类中定义的类中定义的类始终导入到模块中。 要提供给模块外用户的类应在根模块中定义。

## <a name="loading-newly-changed-code-during-development"></a>在开发过程中加载新更改的代码

在开发脚本模块的过程中，通常会对代码进行更改，并使用 Force 参数加载模块的新版本 `Import-Module` 。  这仅适用于根模块中的函数更改。 `Import-Module` 不会重新加载任何嵌套模块。 此外，无法加载任何更新的类。

若要确保您运行的是最新版本，必须使用 cmdlet 卸载该模块 `Remove-Module` 。 `Remove-Module` 删除根模块、所有嵌套的模块以及模块中定义的任何类。 然后，可以使用和语句重载该模块和类 `Import-Module` `using module` 。

另一种常见的开发做法是将代码分成不同的文件。 如果在一个文件中使用另一个模块中定义的类，则应使用 `using module` 语句来确保函数具有所需的类定义。

## <a name="the-psreference-type-is-not-supported-with-class-members"></a>类成员不支持 PSReference 类型

对 `[ref]` 类成员使用类型强制转换将失败。 使用参数的 Api `[ref]` 不能与类成员一起使用。 **PSReference** 类旨在支持 COM 对象。 COM 对象的情况下，需要通过引用传递中的值。

有关类型的详细信息 `[ref]` ，请参阅 [PSReference 类](/dotnet/api/system.management.automation.psreference)。

## <a name="see-also"></a>另请参阅

- [About_hidden](About_hidden.md)
- [about_Enum](about_Enum.md)
- [about_Language_Keywords](about_language_keywords.md)
- [about_Methods](about_methods.md)
- [about_Using](about_using.md)
