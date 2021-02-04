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
# <a name="about-classes"></a><span data-ttu-id="f58d8-103">关于类</span><span class="sxs-lookup"><span data-stu-id="f58d8-103">About Classes</span></span>

## <a name="short-description"></a><span data-ttu-id="f58d8-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="f58d8-104">Short description</span></span>
<span data-ttu-id="f58d8-105">描述如何使用类创建自己的自定义类型。</span><span class="sxs-lookup"><span data-stu-id="f58d8-105">Describes how you can use classes to create your own custom types.</span></span>

## <a name="long-description"></a><span data-ttu-id="f58d8-106">长说明</span><span class="sxs-lookup"><span data-stu-id="f58d8-106">Long description</span></span>

<span data-ttu-id="f58d8-107">PowerShell 5.0 添加了一种正式的语法来定义类和其他用户定义类型。</span><span class="sxs-lookup"><span data-stu-id="f58d8-107">PowerShell 5.0 adds a formal syntax to define classes and other user-defined types.</span></span> <span data-ttu-id="f58d8-108">通过添加类，开发人员和 IT 专业人员可以将 PowerShell 用于更广泛的用例。</span><span class="sxs-lookup"><span data-stu-id="f58d8-108">The addition of classes enables developers and IT professionals to embrace PowerShell for a wider range of use cases.</span></span> <span data-ttu-id="f58d8-109">它简化了 PowerShell 项目的开发并加快了管理面的覆盖范围。</span><span class="sxs-lookup"><span data-stu-id="f58d8-109">It simplifies development of PowerShell artifacts and accelerates coverage of management surfaces.</span></span>

<span data-ttu-id="f58d8-110">类声明是一个蓝图，用于在运行时创建对象的实例。</span><span class="sxs-lookup"><span data-stu-id="f58d8-110">A class declaration is a blueprint used to create instances of objects at run time.</span></span> <span data-ttu-id="f58d8-111">在定义类时，类名称是类型的名称。</span><span class="sxs-lookup"><span data-stu-id="f58d8-111">When you define a class, the class name is the name of the type.</span></span> <span data-ttu-id="f58d8-112">例如，如果声明名为 **device** 的类并将变量初始化 `$dev` 为 **设备** 的新实例， `$dev` 则为 **设备** 类型的对象或实例。</span><span class="sxs-lookup"><span data-stu-id="f58d8-112">For example, if you declare a class named **Device** and initialize a variable `$dev` to a new instance of **Device**, `$dev` is an object or instance of type **Device**.</span></span> <span data-ttu-id="f58d8-113">**设备** 的每个实例都可以在其属性中具有不同的值。</span><span class="sxs-lookup"><span data-stu-id="f58d8-113">Each instance of **Device** can have different values in its properties.</span></span>

## <a name="supported-scenarios"></a><span data-ttu-id="f58d8-114">支持的方案</span><span class="sxs-lookup"><span data-stu-id="f58d8-114">Supported scenarios</span></span>

- <span data-ttu-id="f58d8-115">使用熟悉的面向对象的编程语义（如类、属性、方法、继承等）在 PowerShell 中定义自定义类型。</span><span class="sxs-lookup"><span data-stu-id="f58d8-115">Define custom types in PowerShell using familiar object-oriented programming semantics like classes, properties, methods, inheritance, etc.</span></span>
- <span data-ttu-id="f58d8-116">使用 PowerShell 语言调试类型。</span><span class="sxs-lookup"><span data-stu-id="f58d8-116">Debug types using the PowerShell language.</span></span>
- <span data-ttu-id="f58d8-117">使用正式的机制生成并处理异常。</span><span class="sxs-lookup"><span data-stu-id="f58d8-117">Generate and handle exceptions using formal mechanisms.</span></span>
- <span data-ttu-id="f58d8-118">使用 PowerShell 语言定义 DSC 资源及其关联的类型。</span><span class="sxs-lookup"><span data-stu-id="f58d8-118">Define DSC resources and their associated types by using the PowerShell language.</span></span>

## <a name="syntax"></a><span data-ttu-id="f58d8-119">语法</span><span class="sxs-lookup"><span data-stu-id="f58d8-119">Syntax</span></span>

<span data-ttu-id="f58d8-120">使用以下语法声明类：</span><span class="sxs-lookup"><span data-stu-id="f58d8-120">Classes are declared using the following syntax:</span></span>

```syntax
class <class-name> [: [<base-class>][,<interface-list]] {
    [[<attribute>] [hidden] [static] <property-definition> ...]
    [<class-name>([<constructor-argument-list>])
      {<constructor-statement-list>} ...]
    [[<attribute>] [hidden] [static] <method-definition> ...]
}
```

<span data-ttu-id="f58d8-121">使用以下语法之一对类进行实例化：</span><span class="sxs-lookup"><span data-stu-id="f58d8-121">Classes are instantiated using either of the following syntaxes:</span></span>

```syntax
[$<variable-name> =] New-Object -TypeName <class-name> [
  [-ArgumentList] <constructor-argument-list>]
```

```syntax
[$<variable-name> =] [<class-name>]::new([<constructor-argument-list>])
```

> [!NOTE]
> <span data-ttu-id="f58d8-122">使用语法时 `[<class-name>]::new()` ，类名称的两侧的方括号是必需的。</span><span class="sxs-lookup"><span data-stu-id="f58d8-122">When using the `[<class-name>]::new()` syntax, brackets around the class name are mandatory.</span></span> <span data-ttu-id="f58d8-123">括号指示 PowerShell 的类型定义。</span><span class="sxs-lookup"><span data-stu-id="f58d8-123">The brackets signal a type definition for PowerShell.</span></span>

### <a name="example-syntax-and-usage"></a><span data-ttu-id="f58d8-124">示例语法和用法</span><span class="sxs-lookup"><span data-stu-id="f58d8-124">Example syntax and usage</span></span>

<span data-ttu-id="f58d8-125">此示例显示创建可用类所需的最少语法。</span><span class="sxs-lookup"><span data-stu-id="f58d8-125">This example shows the minimum syntax needed to create a usable class.</span></span>

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

## <a name="class-properties"></a><span data-ttu-id="f58d8-126">类属性</span><span class="sxs-lookup"><span data-stu-id="f58d8-126">Class properties</span></span>

<span data-ttu-id="f58d8-127">属性是在类范围中声明的变量。</span><span class="sxs-lookup"><span data-stu-id="f58d8-127">Properties are variables declared at class scope.</span></span> <span data-ttu-id="f58d8-128">属性可以是任何内置类型，也可以是其他类的实例。</span><span class="sxs-lookup"><span data-stu-id="f58d8-128">A property may be of any built-in type or an instance of another class.</span></span> <span data-ttu-id="f58d8-129">类的属性数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="f58d8-129">Classes have no restriction in the number of properties they have.</span></span>

### <a name="example-class-with-simple-properties"></a><span data-ttu-id="f58d8-130">带有简单属性的示例类</span><span class="sxs-lookup"><span data-stu-id="f58d8-130">Example class with simple properties</span></span>

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

### <a name="example-complex-types-in-class-properties"></a><span data-ttu-id="f58d8-131">类属性中的复杂类型示例</span><span class="sxs-lookup"><span data-stu-id="f58d8-131">Example complex types in class properties</span></span>

<span data-ttu-id="f58d8-132">此示例使用 **Device** 类定义一个空 **机架** 类。</span><span class="sxs-lookup"><span data-stu-id="f58d8-132">This example defines an empty **Rack** class using the **Device** class.</span></span> <span data-ttu-id="f58d8-133">下面的示例演示如何将设备添加到机架，以及如何从预加载的机架开始。</span><span class="sxs-lookup"><span data-stu-id="f58d8-133">The examples, following this one, show how to add devices to the rack and how to start with a pre-loaded rack.</span></span>

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

## <a name="class-methods"></a><span data-ttu-id="f58d8-134">类方法</span><span class="sxs-lookup"><span data-stu-id="f58d8-134">Class methods</span></span>

<span data-ttu-id="f58d8-135">方法定义类可以执行的操作。</span><span class="sxs-lookup"><span data-stu-id="f58d8-135">Methods define the actions that a class can perform.</span></span> <span data-ttu-id="f58d8-136">方法可能采用提供输入数据的参数。</span><span class="sxs-lookup"><span data-stu-id="f58d8-136">Methods may take parameters that provide input data.</span></span> <span data-ttu-id="f58d8-137">方法可以返回输出。</span><span class="sxs-lookup"><span data-stu-id="f58d8-137">Methods can return output.</span></span> <span data-ttu-id="f58d8-138">方法返回的数据可以是任何定义的数据类型。</span><span class="sxs-lookup"><span data-stu-id="f58d8-138">Data returned by a method can be any defined data type.</span></span>

<span data-ttu-id="f58d8-139">定义类的方法时，可以使用自动变量引用当前类对象 `$this` 。</span><span class="sxs-lookup"><span data-stu-id="f58d8-139">When defining a method for a class, you reference the current class object by using the `$this` automatic variable.</span></span> <span data-ttu-id="f58d8-140">这允许您访问在当前类中定义的属性和其他方法。</span><span class="sxs-lookup"><span data-stu-id="f58d8-140">This allows you to access properties and other methods defined in the current class.</span></span>

### <a name="example-simple-class-with-properties-and-methods"></a><span data-ttu-id="f58d8-141">具有属性和方法的示例简单类</span><span class="sxs-lookup"><span data-stu-id="f58d8-141">Example simple class with properties and methods</span></span>

<span data-ttu-id="f58d8-142">扩展 **机架** 类以在其中添加和删除设备。</span><span class="sxs-lookup"><span data-stu-id="f58d8-142">Extending the **Rack** class to add and remove devices to or from it.</span></span>

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

## <a name="output-in-class-methods"></a><span data-ttu-id="f58d8-143">类方法中的输出</span><span class="sxs-lookup"><span data-stu-id="f58d8-143">Output in class methods</span></span>

<span data-ttu-id="f58d8-144">方法应具有定义的返回类型。</span><span class="sxs-lookup"><span data-stu-id="f58d8-144">Methods should have a return type defined.</span></span> <span data-ttu-id="f58d8-145">如果方法不返回 output，则输出类型应为 `[void]` 。</span><span class="sxs-lookup"><span data-stu-id="f58d8-145">If a method doesn't return output, then the output type should be `[void]`.</span></span>

<span data-ttu-id="f58d8-146">在类方法中，除了语句中提到的对象之外，不会向管道发送任何对象 `return` 。</span><span class="sxs-lookup"><span data-stu-id="f58d8-146">In class methods, no objects get sent to the pipeline except those mentioned in the `return` statement.</span></span> <span data-ttu-id="f58d8-147">不会从代码中意外输出到管道。</span><span class="sxs-lookup"><span data-stu-id="f58d8-147">There's no accidental output to the pipeline from the code.</span></span>

> [!NOTE]
> <span data-ttu-id="f58d8-148">这在本质上与 PowerShell 函数处理输出的方式不同，其中一切都进入管道。</span><span class="sxs-lookup"><span data-stu-id="f58d8-148">This is fundamentally different from how PowerShell functions handle output, where everything goes to the pipeline.</span></span>

<span data-ttu-id="f58d8-149">从类方法内部写入错误流的非终止错误不会通过。</span><span class="sxs-lookup"><span data-stu-id="f58d8-149">Non-terminating errors written to the error stream from inside a class method are not passed through.</span></span> <span data-ttu-id="f58d8-150">必须使用 `throw` 来呈现终止错误。</span><span class="sxs-lookup"><span data-stu-id="f58d8-150">You must use `throw` to surface a terminating error.</span></span>
<span data-ttu-id="f58d8-151">使用 `Write-*` cmdlet，您仍然可以从类方法中写入 PowerShell 的输出流。</span><span class="sxs-lookup"><span data-stu-id="f58d8-151">Using the `Write-*` cmdlets, you can still write to PowerShell's output streams from within a class method.</span></span> <span data-ttu-id="f58d8-152">但是，应避免使用此方法，以便方法仅使用语句发出对象 `return` 。</span><span class="sxs-lookup"><span data-stu-id="f58d8-152">However, this should be avoided so that the method emits objects using only the `return` statement.</span></span>

### <a name="method-output"></a><span data-ttu-id="f58d8-153">方法输出</span><span class="sxs-lookup"><span data-stu-id="f58d8-153">Method output</span></span>

<span data-ttu-id="f58d8-154">此示例演示除了语句外，不会从类方法中意外输出到管道 `return` 。</span><span class="sxs-lookup"><span data-stu-id="f58d8-154">This example demonstrates no accidental output to the pipeline from class methods, except on the `return` statement.</span></span>

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

## <a name="constructor"></a><span data-ttu-id="f58d8-155">构造函数</span><span class="sxs-lookup"><span data-stu-id="f58d8-155">Constructor</span></span>

<span data-ttu-id="f58d8-156">构造函数使你能够在创建类的实例时设置默认值和验证对象逻辑。</span><span class="sxs-lookup"><span data-stu-id="f58d8-156">Constructors enable you to set default values and validate object logic at the moment of creating the instance of the class.</span></span> <span data-ttu-id="f58d8-157">构造函数具有与类相同的名称。</span><span class="sxs-lookup"><span data-stu-id="f58d8-157">Constructors have the same name as the class.</span></span> <span data-ttu-id="f58d8-158">构造函数可能具有参数，用于初始化新对象的数据成员。</span><span class="sxs-lookup"><span data-stu-id="f58d8-158">Constructors might have arguments, to initialize the data members of the new object.</span></span>

<span data-ttu-id="f58d8-159">类可以定义零个或多个构造函数。</span><span class="sxs-lookup"><span data-stu-id="f58d8-159">The class can have zero or more constructors defined.</span></span> <span data-ttu-id="f58d8-160">如果未定义任何构造函数，则将为该类提供默认的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="f58d8-160">If no constructor is defined, the class is given a default parameterless constructor.</span></span> <span data-ttu-id="f58d8-161">此构造函数将所有成员初始化为其默认值。</span><span class="sxs-lookup"><span data-stu-id="f58d8-161">This constructor initializes all members to their default values.</span></span> <span data-ttu-id="f58d8-162">为对象类型和字符串提供了 null 值。</span><span class="sxs-lookup"><span data-stu-id="f58d8-162">Object types and strings are given null values.</span></span> <span data-ttu-id="f58d8-163">定义构造函数时，不会创建默认的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="f58d8-163">When you define constructor, no default parameterless constructor is created.</span></span> <span data-ttu-id="f58d8-164">如果需要，请创建一个无参数的构造函数。</span><span class="sxs-lookup"><span data-stu-id="f58d8-164">Create a parameterless constructor if one is needed.</span></span>

### <a name="constructor-basic-syntax"></a><span data-ttu-id="f58d8-165">构造函数基本语法</span><span class="sxs-lookup"><span data-stu-id="f58d8-165">Constructor basic syntax</span></span>

<span data-ttu-id="f58d8-166">在此示例中，设备类是使用属性和构造函数定义的。</span><span class="sxs-lookup"><span data-stu-id="f58d8-166">In this example, the Device class is defined with properties and a constructor.</span></span>
<span data-ttu-id="f58d8-167">若要使用此类，用户需要为构造函数中列出的参数提供值。</span><span class="sxs-lookup"><span data-stu-id="f58d8-167">To use this class, the user is required to provide values for the parameters listed in the constructor.</span></span>

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

### <a name="example-with-multiple-constructors"></a><span data-ttu-id="f58d8-168">具有多个构造函数的示例</span><span class="sxs-lookup"><span data-stu-id="f58d8-168">Example with multiple constructors</span></span>

<span data-ttu-id="f58d8-169">在此示例中，使用属性、默认构造函数和构造函数来定义 **设备** 类以初始化实例。</span><span class="sxs-lookup"><span data-stu-id="f58d8-169">In this example, the **Device** class is defined with properties, a default constructor, and a constructor to initialize the instance.</span></span>

<span data-ttu-id="f58d8-170">默认构造函数将该 **品牌** 设置为 **Undefined**，并将 **模型** 和 **供应商-sku** 保留为 null 值。</span><span class="sxs-lookup"><span data-stu-id="f58d8-170">The default constructor sets the **brand** to **Undefined**, and leaves **model** and **vendor-sku** with null values.</span></span>

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

## <a name="hidden-attribute"></a><span data-ttu-id="f58d8-171">隐藏属性</span><span class="sxs-lookup"><span data-stu-id="f58d8-171">Hidden attribute</span></span>

<span data-ttu-id="f58d8-172">`hidden`属性隐藏属性或方法。</span><span class="sxs-lookup"><span data-stu-id="f58d8-172">The `hidden` attribute hides a property or method.</span></span> <span data-ttu-id="f58d8-173">用户仍可访问该属性或方法，并且在该对象可用的所有范围内均可用。</span><span class="sxs-lookup"><span data-stu-id="f58d8-173">The property or method is still accessible to the user and is available in all scopes in which the object is available.</span></span> <span data-ttu-id="f58d8-174">隐藏的成员在 cmdlet 中是隐藏的 `Get-Member` ，不能在类定义之外使用 tab 自动补全或 IntelliSense 来显示。</span><span class="sxs-lookup"><span data-stu-id="f58d8-174">Hidden members are hidden from the `Get-Member` cmdlet and can't be displayed using tab completion or IntelliSense outside the class definition.</span></span>

<span data-ttu-id="f58d8-175">有关详细信息，请参阅 [About_hidden](About_hidden.md)。</span><span class="sxs-lookup"><span data-stu-id="f58d8-175">For more information, see [About_hidden](About_hidden.md).</span></span>

### <a name="example-using-hidden-attributes"></a><span data-ttu-id="f58d8-176">使用隐藏特性的示例</span><span class="sxs-lookup"><span data-stu-id="f58d8-176">Example using hidden attributes</span></span>

<span data-ttu-id="f58d8-177">创建 **机架** 对象时，设备的槽数是固定值，不应在任何时间更改。</span><span class="sxs-lookup"><span data-stu-id="f58d8-177">When a **Rack** object is created, the number of slots for devices is a fixed value that shouldn't be changed at any time.</span></span> <span data-ttu-id="f58d8-178">此值在创建时是已知的。</span><span class="sxs-lookup"><span data-stu-id="f58d8-178">This value is known at creation time.</span></span>

<span data-ttu-id="f58d8-179">使用 hidden 属性允许开发人员保持隐藏的槽数，并防止意外更改机架的大小。</span><span class="sxs-lookup"><span data-stu-id="f58d8-179">Using the hidden attribute allows the developer to keep the number of slots hidden and prevents unintentional changes the size of the rack.</span></span>

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

<span data-ttu-id="f58d8-180">"公告 **槽** " 属性未显示在 `$r1` 输出中。</span><span class="sxs-lookup"><span data-stu-id="f58d8-180">Notice **Slots** property isn't shown in `$r1` output.</span></span> <span data-ttu-id="f58d8-181">但是，该大小已由构造函数更改。</span><span class="sxs-lookup"><span data-stu-id="f58d8-181">However, the size was changed by the constructor.</span></span>

## <a name="static-attribute"></a><span data-ttu-id="f58d8-182">静态属性</span><span class="sxs-lookup"><span data-stu-id="f58d8-182">Static attribute</span></span>

<span data-ttu-id="f58d8-183">`static`特性定义类中存在的属性或方法，无需任何实例。</span><span class="sxs-lookup"><span data-stu-id="f58d8-183">The `static` attribute defines a property or a method that exists in the class and needs no instance.</span></span>

<span data-ttu-id="f58d8-184">静态属性始终可用，与类实例化无关。</span><span class="sxs-lookup"><span data-stu-id="f58d8-184">A static property is always available, independent of class instantiation.</span></span> <span data-ttu-id="f58d8-185">静态属性跨类的所有实例共享。</span><span class="sxs-lookup"><span data-stu-id="f58d8-185">A static property is shared across all instances of the class.</span></span> <span data-ttu-id="f58d8-186">静态方法始终可用。</span><span class="sxs-lookup"><span data-stu-id="f58d8-186">A static method is available always.</span></span> <span data-ttu-id="f58d8-187">整个会话范围内的所有静态属性。</span><span class="sxs-lookup"><span data-stu-id="f58d8-187">All static properties live for the entire session span.</span></span>

### <a name="example-using-static-attributes-and-methods"></a><span data-ttu-id="f58d8-188">使用静态属性和方法的示例</span><span class="sxs-lookup"><span data-stu-id="f58d8-188">Example using static attributes and methods</span></span>

<span data-ttu-id="f58d8-189">假设你的数据中心中存在此处实例化的机架。</span><span class="sxs-lookup"><span data-stu-id="f58d8-189">Assume the racks instantiated here exist in your data center.</span></span> <span data-ttu-id="f58d8-190">因此，您希望在代码中跟踪机架。</span><span class="sxs-lookup"><span data-stu-id="f58d8-190">So, you would like to keep track of the racks in your code.</span></span>

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

### <a name="testing-static-property-and-method-exist"></a><span data-ttu-id="f58d8-191">测试静态属性和方法存在</span><span class="sxs-lookup"><span data-stu-id="f58d8-191">Testing static property and method exist</span></span>

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

<span data-ttu-id="f58d8-192">请注意，每次运行此示例时，机架数都会增加。</span><span class="sxs-lookup"><span data-stu-id="f58d8-192">Notice that the number of racks increases each time you run this example.</span></span>

## <a name="property-validation-attributes"></a><span data-ttu-id="f58d8-193">属性验证特性</span><span class="sxs-lookup"><span data-stu-id="f58d8-193">Property validation attributes</span></span>

<span data-ttu-id="f58d8-194">通过验证特性，可以测试为属性指定的值是否满足定义的要求。</span><span class="sxs-lookup"><span data-stu-id="f58d8-194">Validation attributes allow you to test that values given to properties meet defined requirements.</span></span> <span data-ttu-id="f58d8-195">在分配值时触发验证。</span><span class="sxs-lookup"><span data-stu-id="f58d8-195">Validation is triggered the moment that the value is assigned.</span></span> <span data-ttu-id="f58d8-196">请参阅 [about_functions_advanced_parameters](about_functions_advanced_parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="f58d8-196">See [about_functions_advanced_parameters](about_functions_advanced_parameters.md).</span></span>

### <a name="example-using-validation-attributes"></a><span data-ttu-id="f58d8-197">使用验证特性的示例</span><span class="sxs-lookup"><span data-stu-id="f58d8-197">Example using validation attributes</span></span>

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

## <a name="inheritance-in-powershell-classes"></a><span data-ttu-id="f58d8-198">PowerShell 类中的继承</span><span class="sxs-lookup"><span data-stu-id="f58d8-198">Inheritance in PowerShell classes</span></span>

<span data-ttu-id="f58d8-199">可以通过创建从现有类派生的新类来扩展类。</span><span class="sxs-lookup"><span data-stu-id="f58d8-199">You can extend a class by creating a new class that derives from an existing class.</span></span> <span data-ttu-id="f58d8-200">派生类继承基类的属性。</span><span class="sxs-lookup"><span data-stu-id="f58d8-200">The derived class inherits the properties of the base class.</span></span> <span data-ttu-id="f58d8-201">您可以根据需要添加或重写方法和属性。</span><span class="sxs-lookup"><span data-stu-id="f58d8-201">You can add or override methods and properties as required.</span></span>

<span data-ttu-id="f58d8-202">PowerShell 不支持多重继承。</span><span class="sxs-lookup"><span data-stu-id="f58d8-202">PowerShell does not support multiple inheritance.</span></span> <span data-ttu-id="f58d8-203">类不能从多个类继承。</span><span class="sxs-lookup"><span data-stu-id="f58d8-203">Classes cannot inherit from more than one class.</span></span> <span data-ttu-id="f58d8-204">不过，您可以使用接口来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="f58d8-204">However, you can use interfaces for that purpose.</span></span>

<span data-ttu-id="f58d8-205">继承实现由 `:` 运算符定义; 这意味着扩展此类或实现这些接口。</span><span class="sxs-lookup"><span data-stu-id="f58d8-205">Inheritance implementation is defined by the `:` operator; which means to extend this class or implements these interfaces.</span></span> <span data-ttu-id="f58d8-206">派生类应始终在类声明中的最左侧。</span><span class="sxs-lookup"><span data-stu-id="f58d8-206">The derived class should always be leftmost in the class declaration.</span></span>

### <a name="example-using-simple-inheritance-syntax"></a><span data-ttu-id="f58d8-207">使用简单继承语法的示例</span><span class="sxs-lookup"><span data-stu-id="f58d8-207">Example using simple inheritance syntax</span></span>

<span data-ttu-id="f58d8-208">此示例显示了简单的 PowerShell 类继承语法。</span><span class="sxs-lookup"><span data-stu-id="f58d8-208">This example shows the simple PowerShell class inheritance syntax.</span></span>

```powershell
Class Derived : Base {...}
```

<span data-ttu-id="f58d8-209">此示例演示了具有基类的接口声明的继承。</span><span class="sxs-lookup"><span data-stu-id="f58d8-209">This example shows inheritance with an interface declaration coming after the base class.</span></span>

```powershell
Class Derived : Base, Interface {...}
```

### <a name="example-of-simple-inheritance-in-powershell-classes"></a><span data-ttu-id="f58d8-210">PowerShell 类中的简单继承示例</span><span class="sxs-lookup"><span data-stu-id="f58d8-210">Example of simple inheritance in PowerShell classes</span></span>

<span data-ttu-id="f58d8-211">在此示例中，在前面的示例中使用的 **机架** 和 **设备** 类更好地定义为：避免属性重复，更好地对齐通用属性，并重复使用常见业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="f58d8-211">In this example the **Rack** and **Device** classes used in the previous examples are better defined to: avoid property repetitions, better align common properties, and reuse common business logic.</span></span>

<span data-ttu-id="f58d8-212">数据中心内的大多数对象都是公司资产，因此，开始将其作为资产进行跟踪是有意义的。</span><span class="sxs-lookup"><span data-stu-id="f58d8-212">Most objects in the data center are company assets, which makes sense to start tracking them as assets.</span></span> <span data-ttu-id="f58d8-213">设备类型由 `DeviceType` 枚举定义，有关枚举的详细信息，请参阅 [about_Enum](about_Enum.md) 。</span><span class="sxs-lookup"><span data-stu-id="f58d8-213">Device types are defined by the `DeviceType` enumeration, see [about_Enum](about_Enum.md) for details on enumerations.</span></span>

<span data-ttu-id="f58d8-214">在我们的示例中，我们仅定义 `Rack` 和 `ComputeServer` ; 这两个扩展都是 `Device` 类的。</span><span class="sxs-lookup"><span data-stu-id="f58d8-214">In our example, we're only defining `Rack` and `ComputeServer`; both extensions to the `Device` class.</span></span>

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

### <a name="calling-base-class-constructors"></a><span data-ttu-id="f58d8-215">调用基类构造函数</span><span class="sxs-lookup"><span data-stu-id="f58d8-215">Calling base class constructors</span></span>

<span data-ttu-id="f58d8-216">若要从子类调用基类构造函数，请添加 `base` 关键字。</span><span class="sxs-lookup"><span data-stu-id="f58d8-216">To invoke a base class constructor from a subclass, add the `base` keyword.</span></span>

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

### <a name="invoke-base-class-methods"></a><span data-ttu-id="f58d8-217">调用基类方法</span><span class="sxs-lookup"><span data-stu-id="f58d8-217">Invoke base class methods</span></span>

<span data-ttu-id="f58d8-218">若要重写子类中的现有方法，请使用相同的名称和签名声明方法。</span><span class="sxs-lookup"><span data-stu-id="f58d8-218">To override existing methods in subclasses, declare methods using the same name and signature.</span></span>

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

<span data-ttu-id="f58d8-219">若要从重写实现中调用基类方法，请在调用时强制转换为基类 ( [baseclass] $this) 。</span><span class="sxs-lookup"><span data-stu-id="f58d8-219">To call base class methods from overridden implementations, cast to the base class ([baseclass]$this) on invocation.</span></span>

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

### <a name="inheriting-from-interfaces"></a><span data-ttu-id="f58d8-220">从接口继承</span><span class="sxs-lookup"><span data-stu-id="f58d8-220">Inheriting from interfaces</span></span>

<span data-ttu-id="f58d8-221">PowerShell 类可以使用用于扩展基类的相同继承语法来实现接口。</span><span class="sxs-lookup"><span data-stu-id="f58d8-221">PowerShell classes can implement an interface using the same inheritance syntax used to extend base classes.</span></span> <span data-ttu-id="f58d8-222">由于接口允许多个继承，因此，实现接口的 PowerShell 类可以从多个类型继承，方法是在冒号后 `:` 使用逗号 () 分隔类型名称 () `,` 。</span><span class="sxs-lookup"><span data-stu-id="f58d8-222">Because interfaces allow multiple inheritance, a PowerShell class implementing an interface may inherit from multiple types, by separating the type names after the colon (`:`) with commas (`,`).</span></span> <span data-ttu-id="f58d8-223">实现接口的 PowerShell 类必须实现该接口的所有成员。</span><span class="sxs-lookup"><span data-stu-id="f58d8-223">A PowerShell class that implements an interface must implement all the members of that interface.</span></span> <span data-ttu-id="f58d8-224">省略实现接口成员将导致脚本中出现分析时错误。</span><span class="sxs-lookup"><span data-stu-id="f58d8-224">Omitting the implemention interface members causes a parse-time error in the script.</span></span>

> [!NOTE]
> <span data-ttu-id="f58d8-225">PowerShell 当前不支持在 PowerShell 脚本中声明新接口。</span><span class="sxs-lookup"><span data-stu-id="f58d8-225">PowerShell does not currently support declaring new interfaces in PowerShell script.</span></span>

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

## <a name="importing-classes-from-a-powershell-module"></a><span data-ttu-id="f58d8-226">从 PowerShell 模块导入类</span><span class="sxs-lookup"><span data-stu-id="f58d8-226">Importing classes from a PowerShell module</span></span>

<span data-ttu-id="f58d8-227">`Import-Module``#requires`语句仅导入模块定义的模块函数、别名和变量。</span><span class="sxs-lookup"><span data-stu-id="f58d8-227">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="f58d8-228">不导入类。</span><span class="sxs-lookup"><span data-stu-id="f58d8-228">Classes are not imported.</span></span> <span data-ttu-id="f58d8-229">`using module`语句将导入模块中定义的类。</span><span class="sxs-lookup"><span data-stu-id="f58d8-229">The `using module` statement imports the classes defined in the module.</span></span> <span data-ttu-id="f58d8-230">如果该模块未在当前会话中加载，则该 `using` 语句将失败。</span><span class="sxs-lookup"><span data-stu-id="f58d8-230">If the module isn't loaded in the current session, the `using` statement fails.</span></span> <span data-ttu-id="f58d8-231">有关语句的详细信息 `using` ，请参阅 [about_Using](about_Using.md)。</span><span class="sxs-lookup"><span data-stu-id="f58d8-231">For more information about the `using` statement, see [about_Using](about_Using.md).</span></span>

<span data-ttu-id="f58d8-232">`using module`语句从根模块导入类 (`ModuleToProcess` 脚本模块或二进制模块的) 。</span><span class="sxs-lookup"><span data-stu-id="f58d8-232">The `using module` statement imports classes from the root module (`ModuleToProcess`) of a script module or binary module.</span></span> <span data-ttu-id="f58d8-233">它不会始终导入嵌套模块中定义的类，也不会将类中定义的类中定义的类始终导入到模块中。</span><span class="sxs-lookup"><span data-stu-id="f58d8-233">It does not consistently import classes defined in nested modules or classes defined in scripts that are dot-sourced into the module.</span></span> <span data-ttu-id="f58d8-234">要提供给模块外用户的类应在根模块中定义。</span><span class="sxs-lookup"><span data-stu-id="f58d8-234">Classes that you want to be available to users outside of the module should be defined in the root module.</span></span>

## <a name="loading-newly-changed-code-during-development"></a><span data-ttu-id="f58d8-235">在开发过程中加载新更改的代码</span><span class="sxs-lookup"><span data-stu-id="f58d8-235">Loading newly changed code during development</span></span>

<span data-ttu-id="f58d8-236">在开发脚本模块的过程中，通常会对代码进行更改，并使用 Force 参数加载模块的新版本 `Import-Module` 。 </span><span class="sxs-lookup"><span data-stu-id="f58d8-236">During development of a script module, it is common to make changes to the code then load the new version of the module using `Import-Module` with the **Force** parameter.</span></span> <span data-ttu-id="f58d8-237">这仅适用于根模块中的函数更改。</span><span class="sxs-lookup"><span data-stu-id="f58d8-237">This works for changes to functions in the root module only.</span></span> <span data-ttu-id="f58d8-238">`Import-Module` 不会重新加载任何嵌套模块。</span><span class="sxs-lookup"><span data-stu-id="f58d8-238">`Import-Module` does not reload any nested modules.</span></span> <span data-ttu-id="f58d8-239">此外，无法加载任何更新的类。</span><span class="sxs-lookup"><span data-stu-id="f58d8-239">Also, there is no way to load any updated classes.</span></span>

<span data-ttu-id="f58d8-240">若要确保您运行的是最新版本，必须使用 cmdlet 卸载该模块 `Remove-Module` 。</span><span class="sxs-lookup"><span data-stu-id="f58d8-240">To ensure that you are running the latest version, you must unload the module using the `Remove-Module` cmdlet.</span></span> <span data-ttu-id="f58d8-241">`Remove-Module` 删除根模块、所有嵌套的模块以及模块中定义的任何类。</span><span class="sxs-lookup"><span data-stu-id="f58d8-241">`Remove-Module` removes the root module, all nested modules, and any classes defined in the modules.</span></span> <span data-ttu-id="f58d8-242">然后，可以使用和语句重载该模块和类 `Import-Module` `using module` 。</span><span class="sxs-lookup"><span data-stu-id="f58d8-242">Then you can reload the module and the classes using `Import-Module` and the `using module` statement.</span></span>

<span data-ttu-id="f58d8-243">另一种常见的开发做法是将代码分成不同的文件。</span><span class="sxs-lookup"><span data-stu-id="f58d8-243">Another common development practice is to separate your code into different files.</span></span> <span data-ttu-id="f58d8-244">如果在一个文件中使用另一个模块中定义的类，则应使用 `using module` 语句来确保函数具有所需的类定义。</span><span class="sxs-lookup"><span data-stu-id="f58d8-244">If you have function in one file that use classes defined in another module, you should using the `using module` statement to ensure that the functions have the class definitions that are needed.</span></span>

## <a name="the-psreference-type-is-not-supported-with-class-members"></a><span data-ttu-id="f58d8-245">类成员不支持 PSReference 类型</span><span class="sxs-lookup"><span data-stu-id="f58d8-245">The PSReference type is not supported with class members</span></span>

<span data-ttu-id="f58d8-246">对 `[ref]` 类成员使用类型强制转换将失败。</span><span class="sxs-lookup"><span data-stu-id="f58d8-246">Using the `[ref]` type-cast with a class member silently fails.</span></span> <span data-ttu-id="f58d8-247">使用参数的 Api `[ref]` 不能与类成员一起使用。</span><span class="sxs-lookup"><span data-stu-id="f58d8-247">APIs that use `[ref]` parameters cannot be used with class members.</span></span> <span data-ttu-id="f58d8-248">**PSReference** 类旨在支持 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="f58d8-248">The **PSReference** class was designed to support COM objects.</span></span> <span data-ttu-id="f58d8-249">COM 对象的情况下，需要通过引用传递中的值。</span><span class="sxs-lookup"><span data-stu-id="f58d8-249">COM objects have cases where you need to pass a value in by reference.</span></span>

<span data-ttu-id="f58d8-250">有关类型的详细信息 `[ref]` ，请参阅 [PSReference 类](/dotnet/api/system.management.automation.psreference)。</span><span class="sxs-lookup"><span data-stu-id="f58d8-250">For more information about the `[ref]` type, see [PSReference Class](/dotnet/api/system.management.automation.psreference).</span></span>

## <a name="see-also"></a><span data-ttu-id="f58d8-251">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f58d8-251">See also</span></span>

- [<span data-ttu-id="f58d8-252">About_hidden</span><span class="sxs-lookup"><span data-stu-id="f58d8-252">About_hidden</span></span>](About_hidden.md)
- [<span data-ttu-id="f58d8-253">about_Enum</span><span class="sxs-lookup"><span data-stu-id="f58d8-253">about_Enum</span></span>](about_Enum.md)
- [<span data-ttu-id="f58d8-254">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="f58d8-254">about_Language_Keywords</span></span>](about_language_keywords.md)
- [<span data-ttu-id="f58d8-255">about_Methods</span><span class="sxs-lookup"><span data-stu-id="f58d8-255">about_Methods</span></span>](about_methods.md)
- [<span data-ttu-id="f58d8-256">about_Using</span><span class="sxs-lookup"><span data-stu-id="f58d8-256">about_Using</span></span>](about_using.md)
