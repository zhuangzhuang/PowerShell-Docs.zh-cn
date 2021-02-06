---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: d55925b0580542459e62e60108f855508232f232
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597042"
---
# <span data-ttu-id="51483-102">Add-Type</span><span class="sxs-lookup"><span data-stu-id="51483-102">Add-Type</span></span>

## <span data-ttu-id="51483-103">摘要</span><span class="sxs-lookup"><span data-stu-id="51483-103">SYNOPSIS</span></span>
<span data-ttu-id="51483-104">将 Microsoft .NET Core 类添加到 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="51483-104">Adds a Microsoft .NET Core class to a PowerShell session.</span></span>

## <span data-ttu-id="51483-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="51483-105">SYNTAX</span></span>

### <span data-ttu-id="51483-106">FromSource (默认值) </span><span class="sxs-lookup"><span data-stu-id="51483-106">FromSource (Default)</span></span>

```
Add-Type [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="51483-107">FromMember</span><span class="sxs-lookup"><span data-stu-id="51483-107">FromMember</span></span>

```
Add-Type [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>]
 [-UsingNamespace <String[]>] [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="51483-108">FromPath</span><span class="sxs-lookup"><span data-stu-id="51483-108">FromPath</span></span>

```
Add-Type [-Path] <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="51483-109">FromLiteralPath</span><span class="sxs-lookup"><span data-stu-id="51483-109">FromLiteralPath</span></span>

```
Add-Type -LiteralPath <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="51483-110">FromAssemblyName</span><span class="sxs-lookup"><span data-stu-id="51483-110">FromAssemblyName</span></span>

```
Add-Type -AssemblyName <String[]> [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="51483-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="51483-111">DESCRIPTION</span></span>

<span data-ttu-id="51483-112">`Add-Type`Cmdlet 可让你在 PowerShell 会话中定义 Microsoft .NET 核心类。</span><span class="sxs-lookup"><span data-stu-id="51483-112">The `Add-Type` cmdlet lets you define a Microsoft .NET Core class in your PowerShell session.</span></span> <span data-ttu-id="51483-113">然后，可以使用 cmdlet 实例化对象， `New-Object` 并像使用任何 .Net Core 对象一样使用对象。</span><span class="sxs-lookup"><span data-stu-id="51483-113">You can then instantiate objects, by using the `New-Object` cmdlet, and use the objects just as you would use any .NET Core object.</span></span> <span data-ttu-id="51483-114">如果将命令添加 `Add-Type` 到 powershell 配置文件，则该类可用于所有 powershell 会话。</span><span class="sxs-lookup"><span data-stu-id="51483-114">If you add an `Add-Type` command to your PowerShell profile, the class is available in all PowerShell sessions.</span></span>

<span data-ttu-id="51483-115">你可以通过指定现有程序集或源代码文件来指定类型，也可以指定内联源代码或保存在变量中的源代码。</span><span class="sxs-lookup"><span data-stu-id="51483-115">You can specify the type by specifying an existing assembly or source code files, or you can specify the source code inline or saved in a variable.</span></span> <span data-ttu-id="51483-116">甚至可以仅指定方法，并 `Add-Type` 定义和生成类。</span><span class="sxs-lookup"><span data-stu-id="51483-116">You can even specify only a method and `Add-Type` defines and generates the class.</span></span> <span data-ttu-id="51483-117">在 Windows 上，可以使用此功能在 PowerShell 中将平台调用 (P/Invoke) 调用非托管函数。</span><span class="sxs-lookup"><span data-stu-id="51483-117">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span> <span data-ttu-id="51483-118">如果指定源代码，将 `Add-Type` 编译指定的源代码，并生成包含新 .Net Core 类型的内存中程序集。</span><span class="sxs-lookup"><span data-stu-id="51483-118">If you specify source code, `Add-Type` compiles the specified source code and generates an in-memory assembly that contains the new .NET Core types.</span></span>

<span data-ttu-id="51483-119">您可以使用的参数 `Add-Type` 指定替代语言和编译器，c # 是默认值、编译器选项、程序集依赖项、类命名空间、类型名称和生成的程序集。</span><span class="sxs-lookup"><span data-stu-id="51483-119">You can use the parameters of `Add-Type` to specify an alternate language and compiler, C# is the default, compiler options, assembly dependencies, the class namespace, the names of the type, and the resulting assembly.</span></span>

<span data-ttu-id="51483-120">从 PowerShell 7 开始， `Add-Type` 如果已存在具有相同名称的类型，则不会编译类型。</span><span class="sxs-lookup"><span data-stu-id="51483-120">Beginning in PowerShell 7, `Add-Type` does not compile a type if a type with the same name already exists.</span></span> <span data-ttu-id="51483-121">此外，还 `Add-Type` 会在包含的文件夹下的文件夹中查找程序集 `ref` `pwsh.dll` 。</span><span class="sxs-lookup"><span data-stu-id="51483-121">Also, `Add-Type` looks for assemblies in a `ref` folder under the folder that contains `pwsh.dll`.</span></span>

## <span data-ttu-id="51483-122">示例</span><span class="sxs-lookup"><span data-stu-id="51483-122">EXAMPLES</span></span>

### <span data-ttu-id="51483-123">示例1：向会话添加 .NET 类型</span><span class="sxs-lookup"><span data-stu-id="51483-123">Example 1: Add a .NET type to a session</span></span>

<span data-ttu-id="51483-124">此示例通过指定存储在变量中的源代码，将 **BasicTest** 类添加到会话中。</span><span class="sxs-lookup"><span data-stu-id="51483-124">This example adds the **BasicTest** class to the session by specifying source code that is stored in a variable.</span></span> <span data-ttu-id="51483-125">**BasicTest** 类用于添加整数、创建对象和将整数相乘。</span><span class="sxs-lookup"><span data-stu-id="51483-125">The **BasicTest** class is used to add integers, create an object, and multiply integers.</span></span>

```powershell
$Source = @"
public class BasicTest
{
  public static int Add(int a, int b)
    {
        return (a + b);
    }
  public int Multiply(int a, int b)
    {
    return (a * b);
    }
}
"@

Add-Type -TypeDefinition $Source
[BasicTest]::Add(4, 3)
$BasicTestObject = New-Object BasicTest
$BasicTestObject.Multiply(5, 2)
```

<span data-ttu-id="51483-126">`$Source`变量存储类的源代码。</span><span class="sxs-lookup"><span data-stu-id="51483-126">The `$Source` variable stores the source code for the class.</span></span> <span data-ttu-id="51483-127">该类型具有一个名为的静态方法 `Add` 和一个名为的非静态方法 `Multiply` 。</span><span class="sxs-lookup"><span data-stu-id="51483-127">The type has a static method called `Add` and a non-static method called `Multiply`.</span></span>

<span data-ttu-id="51483-128">`Add-Type`Cmdlet 可将类添加到会话中。</span><span class="sxs-lookup"><span data-stu-id="51483-128">The `Add-Type` cmdlet adds the class to the session.</span></span> <span data-ttu-id="51483-129">由于它使用内联源代码，因此该命令使用 **TypeDefinition** 参数来指定变量中的代码 `$Source` 。</span><span class="sxs-lookup"><span data-stu-id="51483-129">Because it's using inline source code, the command uses the **TypeDefinition** parameter to specify the code in the `$Source` variable.</span></span>

<span data-ttu-id="51483-130">`Add` **BasicTest** 类的静态方法使用双冒号字符 (`::`) 来指定类的静态成员。</span><span class="sxs-lookup"><span data-stu-id="51483-130">The `Add` static method of the **BasicTest** class uses the double-colon characters (`::`) to specify a static member of the class.</span></span> <span data-ttu-id="51483-131">添加整数并显示总和。</span><span class="sxs-lookup"><span data-stu-id="51483-131">The integers are added and the sum is displayed.</span></span>

<span data-ttu-id="51483-132">`New-Object`Cmdlet 实例化 **BasicTest** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="51483-132">The `New-Object` cmdlet instantiates an instance of the **BasicTest** class.</span></span> <span data-ttu-id="51483-133">它将新对象保存在 `$BasicTestObject` 变量中。</span><span class="sxs-lookup"><span data-stu-id="51483-133">It saves the new object in the `$BasicTestObject` variable.</span></span>

<span data-ttu-id="51483-134">`$BasicTestObject` 使用 `Multiply` 方法。</span><span class="sxs-lookup"><span data-stu-id="51483-134">`$BasicTestObject` uses the `Multiply` method.</span></span> <span data-ttu-id="51483-135">整数相乘并显示产品。</span><span class="sxs-lookup"><span data-stu-id="51483-135">The integers are multiplied and the product is displayed.</span></span>

### <span data-ttu-id="51483-136">示例2：检查添加的类型</span><span class="sxs-lookup"><span data-stu-id="51483-136">Example 2: Examine an added type</span></span>

<span data-ttu-id="51483-137">此示例使用 `Get-Member` cmdlet 检查在 `Add-Type` `New-Object` **示例 1** 中创建的和 cmdlet 的对象。</span><span class="sxs-lookup"><span data-stu-id="51483-137">This example uses the `Get-Member` cmdlet to examine the objects that the `Add-Type` and `New-Object` cmdlets created in **Example 1**.</span></span>

```powershell
[BasicTest] | Get-Member
```

```Output
   TypeName: System.RuntimeType

Name                 MemberType Definition
----                 ---------- ----------
AsType               Method     type AsType()
Clone                Method     System.Object Clone(), System.Object ICloneable.Clone()
Equals               Method     bool Equals(System.Object obj), bool Equals(type o)
FindInterfaces       Method     type[] FindInterfaces(System.Reflection.TypeFilter filter...
...
```

```powershell
[BasicTest] | Get-Member -Static
```

```Output
  TypeName: BasicTest

Name            MemberType Definition
----            ---------- ----------
Add             Method     static int Add(int a, int b)
Equals          Method     static bool Equals(System.Object objA, System.Object objB)
new             Method     BasicTest new()
ReferenceEquals Method     static bool ReferenceEquals(System.Object objA, System.Object objB)
```

```powershell
$BasicTestObject | Get-Member
```

```Output
   TypeName: BasicTest

Name        MemberType Definition
----        ---------- ----------
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
Multiply    Method     int Multiply(int a, int b)
ToString    Method     string ToString()
```

<span data-ttu-id="51483-138">`Get-Member`Cmdlet 可获取添加到会话中的 **BasicTest** 类的类型和成员 `Add-Type` 。</span><span class="sxs-lookup"><span data-stu-id="51483-138">The `Get-Member` cmdlet gets the type and members of the **BasicTest** class that `Add-Type` added to the session.</span></span> <span data-ttu-id="51483-139">该 `Get-Member` 命令显示它是一个派生自 **system.object** 类的 **RuntimeType** 对象。</span><span class="sxs-lookup"><span data-stu-id="51483-139">The `Get-Member` command reveals that it's a **System.RuntimeType** object, which is derived from the **System.Object** class.</span></span>

<span data-ttu-id="51483-140">`Get-Member`**静态** 参数获取 **BasicTest** 类的静态属性和方法。</span><span class="sxs-lookup"><span data-stu-id="51483-140">The `Get-Member` **Static** parameter gets the static properties and methods of the **BasicTest** class.</span></span> <span data-ttu-id="51483-141">输出显示此 `Add` 方法已包括在内。</span><span class="sxs-lookup"><span data-stu-id="51483-141">The output shows that the `Add` method is included.</span></span>

<span data-ttu-id="51483-142">`Get-Member`Cmdlet 将获取存储在变量中的对象的成员 `$BasicTestObject` 。</span><span class="sxs-lookup"><span data-stu-id="51483-142">The `Get-Member` cmdlet gets the members of the object stored in the `$BasicTestObject` variable.</span></span>
<span data-ttu-id="51483-143">`$BasicTestObject` 是通过对 `New-Object` **BasicTest** 类使用 cmdlet 创建的。</span><span class="sxs-lookup"><span data-stu-id="51483-143">`$BasicTestObject` was created by using the `New-Object` cmdlet with the **BasicTest** class.</span></span> <span data-ttu-id="51483-144">输出显示变量的值 `$BasicTestObject` 是 **BasicTest** 类的一个实例，并且它包括一个名为的成员 `Multiply` 。</span><span class="sxs-lookup"><span data-stu-id="51483-144">The output reveals that the value of the `$BasicTestObject` variable is an instance of the **BasicTest** class and that it includes a member called `Multiply`.</span></span>

### <span data-ttu-id="51483-145">示例3：从程序集添加类型</span><span class="sxs-lookup"><span data-stu-id="51483-145">Example 3: Add types from an assembly</span></span>

<span data-ttu-id="51483-146">此示例将程序集的类添加 `NJsonSchema.dll` 到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="51483-146">This example adds the classes from the `NJsonSchema.dll` assembly to the current session.</span></span>

```powershell
Set-Location -Path $PSHOME
$AccType = Add-Type -AssemblyName *jsonschema* -PassThru
```

<span data-ttu-id="51483-147">`Set-Location` 使用 **Path** 参数指定 `$PSHOME` 变量。</span><span class="sxs-lookup"><span data-stu-id="51483-147">`Set-Location` uses the **Path** parameter to specify the `$PSHOME` variable.</span></span> <span data-ttu-id="51483-148">变量引用 DLL 文件所在的 PowerShell 安装目录。</span><span class="sxs-lookup"><span data-stu-id="51483-148">The variable references the PowerShell installation directory where the DLL file is located.</span></span>

<span data-ttu-id="51483-149">`$AccType`变量存储使用 cmdlet 创建的对象 `Add-Type` 。</span><span class="sxs-lookup"><span data-stu-id="51483-149">The `$AccType` variable stores an object created with the `Add-Type` cmdlet.</span></span> <span data-ttu-id="51483-150">`Add-Type` 使用 **AssemblyName** 参数指定程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="51483-150">`Add-Type` uses the **AssemblyName** parameter to specify the name of the assembly.</span></span> <span data-ttu-id="51483-151">星号 (`*`) 通配符允许您获取正确的程序集，即使您不确定名称或其拼写时也是如此。</span><span class="sxs-lookup"><span data-stu-id="51483-151">The asterisk (`*`) wildcard character allows you to get the correct assembly even when you aren't sure of the name or its spelling.</span></span> <span data-ttu-id="51483-152">**PassThru** 参数生成对象，这些对象表示添加到会话中的类。</span><span class="sxs-lookup"><span data-stu-id="51483-152">The **PassThru** parameter generates objects that represent the classes that are added to the session.</span></span>

### <span data-ttu-id="51483-153">示例4：调用本机 Windows Api</span><span class="sxs-lookup"><span data-stu-id="51483-153">Example 4: Call native Windows APIs</span></span>

<span data-ttu-id="51483-154">此示例演示如何在 PowerShell 中调用本机 Windows Api。</span><span class="sxs-lookup"><span data-stu-id="51483-154">This example demonstrates how to call native Windows APIs in PowerShell.</span></span> <span data-ttu-id="51483-155">`Add-Type` 使用平台调用 (P/Invoke) 机制从 PowerShell 调用中的函数 `User32.dll` 。</span><span class="sxs-lookup"><span data-stu-id="51483-155">`Add-Type` uses the Platform Invoke (P/Invoke) mechanism to call a function in `User32.dll` from PowerShell.</span></span> <span data-ttu-id="51483-156">此示例仅适用于运行 Windows 操作系统的计算机。</span><span class="sxs-lookup"><span data-stu-id="51483-156">This example only works on computers running the Windows operating system.</span></span>

```powershell
$Signature = @"
[DllImport("user32.dll")]public static extern bool ShowWindowAsync(IntPtr hWnd, int nCmdShow);
"@

$ShowWindowAsync = Add-Type -MemberDefinition $Signature -Name "Win32ShowWindowAsync" -Namespace Win32Functions -PassThru

# Minimize the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $pid).MainWindowHandle, 2)

# Restore the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $Pid).MainWindowHandle, 4)
```

<span data-ttu-id="51483-157">`$Signature`变量存储函数的 c # 签名 `ShowWindowAsync` 。</span><span class="sxs-lookup"><span data-stu-id="51483-157">The `$Signature` variable stores the C# signature of the `ShowWindowAsync` function.</span></span> <span data-ttu-id="51483-158">为了确保生成的方法在 PowerShell 会话中可见， `public` 关键字已添加到标准签名中。</span><span class="sxs-lookup"><span data-stu-id="51483-158">To ensure that the resulting method is visible in a PowerShell session, the `public` keyword was added to the standard signature.</span></span> <span data-ttu-id="51483-159">有关详细信息，请参阅 [ShowWindowAsync 函数](/windows/win32/api/winuser/nf-winuser-showwindowasync)。</span><span class="sxs-lookup"><span data-stu-id="51483-159">For more information, see [ShowWindowAsync function](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span></span>

<span data-ttu-id="51483-160">`$ShowWindowAsync`变量存储通过 `Add-Type` **PassThru** 参数创建的对象。</span><span class="sxs-lookup"><span data-stu-id="51483-160">The `$ShowWindowAsync` variable stores the object created by the `Add-Type` **PassThru** parameter.</span></span>
<span data-ttu-id="51483-161">`Add-Type`Cmdlet 将 `ShowWindowAsync` 函数作为静态方法添加到 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="51483-161">The `Add-Type` cmdlet adds the `ShowWindowAsync` function to the PowerShell session as a static method.</span></span> <span data-ttu-id="51483-162">该命令使用 **MemberDefinition** 参数来指定保存在变量中的方法定义 `$Signature` 。</span><span class="sxs-lookup"><span data-stu-id="51483-162">The command uses the **MemberDefinition** parameter to specify the method definition saved in the `$Signature` variable.</span></span> <span data-ttu-id="51483-163">该命令使用 **Name** 和 **Namespace** 参数来指定类的名称和命名空间。</span><span class="sxs-lookup"><span data-stu-id="51483-163">The command uses the **Name** and **Namespace** parameters to specify a name and namespace for the class.</span></span> <span data-ttu-id="51483-164">**PassThru** 参数生成一个表示类型的对象。</span><span class="sxs-lookup"><span data-stu-id="51483-164">The **PassThru** parameter generates an object that represents the types.</span></span>

<span data-ttu-id="51483-165">`ShowWindowAsync`在命令中使用新的静态方法来最小化和还原 PowerShell 控制台。</span><span class="sxs-lookup"><span data-stu-id="51483-165">The new `ShowWindowAsync` static method is used in the commands to minimize and restore the PowerShell console.</span></span> <span data-ttu-id="51483-166">此方法采用两个参数：窗口句柄和指定如何显示窗口的整数。</span><span class="sxs-lookup"><span data-stu-id="51483-166">The method takes two parameters: the window handle, and an integer that specifies how the window is displayed.</span></span>

<span data-ttu-id="51483-167">若要最大程度地减少 PowerShell 控制台，请 `ShowWindowAsync` 将 `Get-Process` cmdlet 与自动变量一起使用， `$PID` 以获取托管当前 PowerShell 会话的进程。</span><span class="sxs-lookup"><span data-stu-id="51483-167">To minimize the PowerShell console, `ShowWindowAsync` uses the `Get-Process` cmdlet with the `$PID` automatic variable to get the process that is hosting the current PowerShell session.</span></span> <span data-ttu-id="51483-168">然后，它使用当前进程的 **MainWindowHandle** 属性和值 `2` （表示 `SW_MINIMIZE` 值）。</span><span class="sxs-lookup"><span data-stu-id="51483-168">Then it uses the **MainWindowHandle** property of the current process and a value of `2`, which represents the `SW_MINIMIZE` value.</span></span>

<span data-ttu-id="51483-169">若要还原窗口，请将的 `ShowWindowAsync` 值 `4` 用于窗口位置，它表示 `SW_RESTORE` 值。</span><span class="sxs-lookup"><span data-stu-id="51483-169">To restore the window, `ShowWindowAsync` uses a value of `4` for the window position, which represents the `SW_RESTORE` value.</span></span>

<span data-ttu-id="51483-170">若要最大化窗口，请使用 `3` 表示的值 `SW_MAXIMIZE` 。</span><span class="sxs-lookup"><span data-stu-id="51483-170">To maximize the window, use the value of `3` that represents `SW_MAXIMIZE`.</span></span>

## <span data-ttu-id="51483-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="51483-171">PARAMETERS</span></span>

### <span data-ttu-id="51483-172">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="51483-172">-AssemblyName</span></span>

<span data-ttu-id="51483-173">指定包含类型的程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="51483-173">Specifies the name of an assembly that includes the types.</span></span> <span data-ttu-id="51483-174">`Add-Type` 采用指定程序集中的类型。</span><span class="sxs-lookup"><span data-stu-id="51483-174">`Add-Type` takes the types from the specified assembly.</span></span> <span data-ttu-id="51483-175">基于程序集名称创建类型时，此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="51483-175">This parameter is required when you're creating types based on an assembly name.</span></span>

<span data-ttu-id="51483-176">输入程序集的完整名称或简单名称（也称为 "部分名称"）。</span><span class="sxs-lookup"><span data-stu-id="51483-176">Enter the full or simple name, also known as the partial name, of an assembly.</span></span> <span data-ttu-id="51483-177">在程序集名称中允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="51483-177">Wildcard characters are permitted in the assembly name.</span></span> <span data-ttu-id="51483-178">如果输入简单名称或部分名称，则将 `Add-Type` 其解析为完整名称，然后使用完整名称加载程序集。</span><span class="sxs-lookup"><span data-stu-id="51483-178">If you enter a simple or partial name, `Add-Type` resolves it to the full name, and then uses the full name to load the assembly.</span></span>

<span data-ttu-id="51483-179">此参数不接受路径或文件名。</span><span class="sxs-lookup"><span data-stu-id="51483-179">This parameter doesn't accept a path or a filename.</span></span> <span data-ttu-id="51483-180">若要输入程序集动态链接库的路径 (DLL) 文件，请使用 **path** 参数。</span><span class="sxs-lookup"><span data-stu-id="51483-180">To enter the path to the assembly dynamic-link library (DLL) file, use the **Path** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromAssemblyName
Aliases: AN

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="51483-181">-CompilerOptions</span><span class="sxs-lookup"><span data-stu-id="51483-181">-CompilerOptions</span></span>

<span data-ttu-id="51483-182">指定用于源代码编译器的选项。</span><span class="sxs-lookup"><span data-stu-id="51483-182">Specifies the options for the source code compiler.</span></span> <span data-ttu-id="51483-183">这些选项无需修改即可发送到编译器。</span><span class="sxs-lookup"><span data-stu-id="51483-183">These options are sent to the compiler without revision.</span></span>

<span data-ttu-id="51483-184">此参数允许指示编译器生成可执行文件、嵌入资源或设置命令行选项，如 `/unsafe` 选项。</span><span class="sxs-lookup"><span data-stu-id="51483-184">This parameter allows you to direct the compiler to generate an executable file, embed resources, or set command-line options, such as the `/unsafe` option.</span></span>

<span data-ttu-id="51483-185">不能在同一命令中使用 **CompilerOptions** 和 **ReferencedAssemblies** 参数。</span><span class="sxs-lookup"><span data-stu-id="51483-185">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51483-186">-IgnoreWarnings</span><span class="sxs-lookup"><span data-stu-id="51483-186">-IgnoreWarnings</span></span>

<span data-ttu-id="51483-187">忽略编译器警告。</span><span class="sxs-lookup"><span data-stu-id="51483-187">Ignores compiler warnings.</span></span> <span data-ttu-id="51483-188">使用此参数可防止将 `Add-Type` 编译器警告作为错误处理。</span><span class="sxs-lookup"><span data-stu-id="51483-188">Use this parameter to prevent `Add-Type` from handling compiler warnings as errors.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51483-189">-Language</span><span class="sxs-lookup"><span data-stu-id="51483-189">-Language</span></span>

<span data-ttu-id="51483-190">指定在源代码中使用的语言。</span><span class="sxs-lookup"><span data-stu-id="51483-190">Specifies the language that is used in the source code.</span></span> <span data-ttu-id="51483-191">此参数可接受的值为 **CSharp**。</span><span class="sxs-lookup"><span data-stu-id="51483-191">The acceptable value for this parameter is **CSharp**.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.Language
Parameter Sets: FromSource, FromMember
Aliases:
Accepted values: CSharp

Required: False
Position: Named
Default value: CSharp
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51483-192">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="51483-192">-LiteralPath</span></span>

<span data-ttu-id="51483-193">指定包含类型的源代码文件或程序集 DLL 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="51483-193">Specifies the path to source code files or assembly DLL files that contain the types.</span></span> <span data-ttu-id="51483-194">与 **Path** 不同， **LiteralPath** 参数的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="51483-194">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="51483-195">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="51483-195">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="51483-196">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="51483-196">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="51483-197">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="51483-197">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51483-198">-MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="51483-198">-MemberDefinition</span></span>

<span data-ttu-id="51483-199">指定类的新属性或方法。</span><span class="sxs-lookup"><span data-stu-id="51483-199">Specifies new properties or methods for the class.</span></span> <span data-ttu-id="51483-200">`Add-Type` 生成支持属性或方法所需的模板代码。</span><span class="sxs-lookup"><span data-stu-id="51483-200">`Add-Type` generates the template code that is required to support the properties or methods.</span></span>

<span data-ttu-id="51483-201">在 Windows 上，可以使用此功能在 PowerShell 中将平台调用 (P/Invoke) 调用非托管函数。</span><span class="sxs-lookup"><span data-stu-id="51483-201">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51483-202">-Name</span><span class="sxs-lookup"><span data-stu-id="51483-202">-Name</span></span>

<span data-ttu-id="51483-203">指定要创建的类的名称。</span><span class="sxs-lookup"><span data-stu-id="51483-203">Specifies the name of the class to create.</span></span> <span data-ttu-id="51483-204">当从成员定义生成类型时，此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="51483-204">This parameter is required when generating a type from a member definition.</span></span>

<span data-ttu-id="51483-205">类型名称和命名空间在一个会话中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="51483-205">The type name and namespace must be unique within a session.</span></span> <span data-ttu-id="51483-206">不能卸载或更改类型。</span><span class="sxs-lookup"><span data-stu-id="51483-206">You can't unload a type or change it.</span></span>
<span data-ttu-id="51483-207">若要更改类型的代码，必须更改名称或启动新的 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="51483-207">To change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="51483-208">否则，该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="51483-208">Otherwise, the command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51483-209">-Namespace</span><span class="sxs-lookup"><span data-stu-id="51483-209">-Namespace</span></span>

<span data-ttu-id="51483-210">指定类型的命名空间。</span><span class="sxs-lookup"><span data-stu-id="51483-210">Specifies a namespace for the type.</span></span>

<span data-ttu-id="51483-211">如果此参数不包括在命令中，则会在 **将. microsoft.powershell.commands.newwebserviceproxy.autogeneratedtypes 和** 命名空间中创建该类型。</span><span class="sxs-lookup"><span data-stu-id="51483-211">If this parameter isn't included in the command, the type is created in the **Microsoft.PowerShell.Commands.AddType.AutoGeneratedTypes** namespace.</span></span> <span data-ttu-id="51483-212">如果参数包含在包含空字符串值或值的命令中 `$Null` ，则将在全局命名空间中生成类型。</span><span class="sxs-lookup"><span data-stu-id="51483-212">If the parameter is included in the command with an empty string value or a value of `$Null`, the type is generated in the global namespace.</span></span>

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51483-213">-OutputAssembly</span><span class="sxs-lookup"><span data-stu-id="51483-213">-OutputAssembly</span></span>

<span data-ttu-id="51483-214">在该位置中为具有指定名称的程序集生成 DLL 文件。</span><span class="sxs-lookup"><span data-stu-id="51483-214">Generates a DLL file for the assembly with the specified name in the location.</span></span> <span data-ttu-id="51483-215">输入可选的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="51483-215">Enter an optional path and filename.</span></span> <span data-ttu-id="51483-216">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="51483-216">Wildcard characters are permitted.</span></span> <span data-ttu-id="51483-217">默认情况下， `Add-Type` 仅在内存中生成程序集。</span><span class="sxs-lookup"><span data-stu-id="51483-217">By default, `Add-Type` generates the assembly only in memory.</span></span>

```yaml
Type: System.String
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="51483-218">-OutputType</span><span class="sxs-lookup"><span data-stu-id="51483-218">-OutputType</span></span>

<span data-ttu-id="51483-219">指定输出程序集的输出类型。</span><span class="sxs-lookup"><span data-stu-id="51483-219">Specifies the output type of the output assembly.</span></span> <span data-ttu-id="51483-220">默认情况下，不指定输出类型。</span><span class="sxs-lookup"><span data-stu-id="51483-220">By default, no output type is specified.</span></span> <span data-ttu-id="51483-221">仅当命令中指定了输出程序集时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="51483-221">This parameter is valid only when an output assembly is specified in the command.</span></span> <span data-ttu-id="51483-222">有关这些值的详细信息，请参阅 [OutputAssemblyType 枚举](/dotnet/api/microsoft.powershell.commands.outputassemblytype)。</span><span class="sxs-lookup"><span data-stu-id="51483-222">For more information about the values, see [OutputAssemblyType Enumeration](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span></span>

<span data-ttu-id="51483-223">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="51483-223">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="51483-224">控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="51483-224">ConsoleApplication</span></span>
- <span data-ttu-id="51483-225">库</span><span class="sxs-lookup"><span data-stu-id="51483-225">Library</span></span>
- <span data-ttu-id="51483-226">Windowsapplication.zip</span><span class="sxs-lookup"><span data-stu-id="51483-226">WindowsApplication</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51483-227">在 PowerShell 7.1 `ConsoleApplication` 和不受支持的情况下， `WindowsApplication` 如果指定为 **OutputType** 参数的值，则 PowerShell 将引发一个终止错误。</span><span class="sxs-lookup"><span data-stu-id="51483-227">As of PowerShell 7.1, `ConsoleApplication` and `WindowsApplication` are not supported and PowerShell throws a terminating error if either are specified as values for the **OutputType** parameter.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.OutputAssemblyType
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OT
Accepted values: ConsoleApplication, Library, WindowsApplication

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51483-228">-PassThru</span><span class="sxs-lookup"><span data-stu-id="51483-228">-PassThru</span></span>

<span data-ttu-id="51483-229">返回表示已添加的类型的 **System.Runtime** 对象。</span><span class="sxs-lookup"><span data-stu-id="51483-229">Returns a **System.Runtime** object that represents the types that were added.</span></span> <span data-ttu-id="51483-230">默认情况下，此 cmdlet 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="51483-230">By default, this cmdlet doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51483-231">-Path</span><span class="sxs-lookup"><span data-stu-id="51483-231">-Path</span></span>

<span data-ttu-id="51483-232">指定包含类型的源代码文件或程序集 DLL 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="51483-232">Specifies the path to source code files or assembly DLL files that contain the types.</span></span>

<span data-ttu-id="51483-233">如果提交源代码文件，则会在 `Add-Type` 文件中编译代码，并创建类型的内存中程序集。</span><span class="sxs-lookup"><span data-stu-id="51483-233">If you submit source code files, `Add-Type` compiles the code in the files and creates an in-memory assembly of the types.</span></span> <span data-ttu-id="51483-234">**Path** 的值中指定的文件扩展名确定使用的编译器 `Add-Type` 。</span><span class="sxs-lookup"><span data-stu-id="51483-234">The file extension specified in the value of **Path** determines the compiler that `Add-Type` uses.</span></span>

<span data-ttu-id="51483-235">如果提交程序集文件，则 `Add-Type` 从程序集中获取类型。</span><span class="sxs-lookup"><span data-stu-id="51483-235">If you submit an assembly file, `Add-Type` takes the types from the assembly.</span></span> <span data-ttu-id="51483-236">若要指定内存中程序集或全局程序集缓存，请使用 **AssemblyName** 参数。</span><span class="sxs-lookup"><span data-stu-id="51483-236">To specify an in-memory assembly or the global assembly cache, use the **AssemblyName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51483-237">-ReferencedAssemblies</span><span class="sxs-lookup"><span data-stu-id="51483-237">-ReferencedAssemblies</span></span>

<span data-ttu-id="51483-238">指定类型所依赖的程序集。</span><span class="sxs-lookup"><span data-stu-id="51483-238">Specifies the assemblies upon which the type depends.</span></span> <span data-ttu-id="51483-239">默认情况下， `Add-Type` 引用 `System.dll` 和 `System.Management.Automation.dll` 。</span><span class="sxs-lookup"><span data-stu-id="51483-239">By default, `Add-Type` references `System.dll` and `System.Management.Automation.dll`.</span></span> <span data-ttu-id="51483-240">除了引用默认程序集之外，还将引用你通过使用此参数指定的程序集。</span><span class="sxs-lookup"><span data-stu-id="51483-240">The assemblies that you specify by using this parameter are referenced in addition to the default assemblies.</span></span>

<span data-ttu-id="51483-241">从 PowerShell 6 开始， **ReferencedAssemblies** 不包括默认的 .net 程序集。</span><span class="sxs-lookup"><span data-stu-id="51483-241">Beginning in PowerShell 6, **ReferencedAssemblies** doesn't include the default .NET assemblies.</span></span> <span data-ttu-id="51483-242">必须在传递给此参数的值中包含对它们的特定引用。</span><span class="sxs-lookup"><span data-stu-id="51483-242">You must include a specific reference to them in the value passed to this parameter.</span></span>

<span data-ttu-id="51483-243">不能在同一命令中使用 **CompilerOptions** 和 **ReferencedAssemblies** 参数。</span><span class="sxs-lookup"><span data-stu-id="51483-243">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: RA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51483-244">-TypeDefinition</span><span class="sxs-lookup"><span data-stu-id="51483-244">-TypeDefinition</span></span>

<span data-ttu-id="51483-245">指定包含类型定义的源代码。</span><span class="sxs-lookup"><span data-stu-id="51483-245">Specifies the source code that contains the type definitions.</span></span> <span data-ttu-id="51483-246">以字符串或 here-string 的形式输入源代码或输入一个包含源代码的变量。</span><span class="sxs-lookup"><span data-stu-id="51483-246">Enter the source code in a string or here-string, or enter a variable that contains the source code.</span></span> <span data-ttu-id="51483-247">有关字符串的详细信息，请参阅 [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="51483-247">For more information about here-strings, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span></span>

<span data-ttu-id="51483-248">在类型定义中包括命名空间声明。</span><span class="sxs-lookup"><span data-stu-id="51483-248">Include a namespace declaration in your type definition.</span></span> <span data-ttu-id="51483-249">如果省略命名空间声明，则你的类型可能会与其他类型或其他类型的快捷方式同名，从而导致意外覆盖。</span><span class="sxs-lookup"><span data-stu-id="51483-249">If you omit the namespace declaration, your type might have the same name as another type or the shortcut for another type, causing an unintentional overwrite.</span></span> <span data-ttu-id="51483-250">例如，如果定义了一个名为 **exception** 的类型，则使用 **exception** 作为 system.exception 的快捷 **方式的脚本将失败** 。</span><span class="sxs-lookup"><span data-stu-id="51483-250">For example, if you define a type called **Exception**, scripts that use **Exception** as the shortcut for **System.Exception** will fail.</span></span>

```yaml
Type: System.String
Parameter Sets: FromSource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51483-251">-UsingNamespace</span><span class="sxs-lookup"><span data-stu-id="51483-251">-UsingNamespace</span></span>

<span data-ttu-id="51483-252">指定类所需的其他命名空间。</span><span class="sxs-lookup"><span data-stu-id="51483-252">Specifies other namespaces that are required for the class.</span></span> <span data-ttu-id="51483-253">这非常类似于 c # 关键字 `Using` 。</span><span class="sxs-lookup"><span data-stu-id="51483-253">This is much like the C# keyword, `Using`.</span></span>

<span data-ttu-id="51483-254">默认情况下， `Add-Type` 引用 **系统** 命名空间。</span><span class="sxs-lookup"><span data-stu-id="51483-254">By default, `Add-Type` references the **System** namespace.</span></span> <span data-ttu-id="51483-255">如果使用 **MemberDefinition** 参数，则 `Add-Type` 默认情况下也会引用 **InteropServices** 命名空间。</span><span class="sxs-lookup"><span data-stu-id="51483-255">When the **MemberDefinition** parameter is used, `Add-Type` also references the **System.Runtime.InteropServices** namespace by default.</span></span> <span data-ttu-id="51483-256">除了引用默认命名空间之外，还将引用你通过使用 **UsingNamespace** 参数添加的命名空间。</span><span class="sxs-lookup"><span data-stu-id="51483-256">The namespaces that you add by using the **UsingNamespace** parameter are referenced in addition to the default namespaces.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases: Using

Required: False
Position: Named
Default value: System namespace
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51483-257">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="51483-257">CommonParameters</span></span>

<span data-ttu-id="51483-258">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="51483-258">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="51483-259">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="51483-259">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="51483-260">输入</span><span class="sxs-lookup"><span data-stu-id="51483-260">INPUTS</span></span>

### <span data-ttu-id="51483-261">无</span><span class="sxs-lookup"><span data-stu-id="51483-261">None</span></span>

<span data-ttu-id="51483-262">不能将对象向下发送到 `Add-Type` 。</span><span class="sxs-lookup"><span data-stu-id="51483-262">You can't send objects down the pipeline to `Add-Type`.</span></span>

## <span data-ttu-id="51483-263">输出</span><span class="sxs-lookup"><span data-stu-id="51483-263">OUTPUTS</span></span>

### <span data-ttu-id="51483-264">None 或 system.string</span><span class="sxs-lookup"><span data-stu-id="51483-264">None or System.Type</span></span>

<span data-ttu-id="51483-265">当使用 **PassThru** 参数时，将 `Add-Type` 返回表示新类型的 **system.object** 对象。</span><span class="sxs-lookup"><span data-stu-id="51483-265">When you use the **PassThru** parameter, `Add-Type` returns a **System.Type** object that represents the new type.</span></span> <span data-ttu-id="51483-266">否则，此 cmdlet 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="51483-266">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="51483-267">注释</span><span class="sxs-lookup"><span data-stu-id="51483-267">NOTES</span></span>

<span data-ttu-id="51483-268">你添加的类型仅存在当前会话中。</span><span class="sxs-lookup"><span data-stu-id="51483-268">The types that you add exist only in the current session.</span></span> <span data-ttu-id="51483-269">若要在所有会话中使用这些类型，请将它们添加到 PowerShell 配置文件中。</span><span class="sxs-lookup"><span data-stu-id="51483-269">To use the types in all sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="51483-270">有关配置文件的详细信息，请参阅 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="51483-270">For more information about the profile, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="51483-271">类型名称和命名空间在一个会话中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="51483-271">Type names and namespaces must be unique within a session.</span></span> <span data-ttu-id="51483-272">不能卸载或更改类型。</span><span class="sxs-lookup"><span data-stu-id="51483-272">You can't unload a type or change it.</span></span> <span data-ttu-id="51483-273">如果需要更改类型的代码，则必须更改名称或启动新的 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="51483-273">If you need to change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="51483-274">否则，该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="51483-274">Otherwise, the command fails.</span></span>

<span data-ttu-id="51483-275">在 Windows PowerShell 中 (版本5.1 及更低版本) ，你需要 `Add-Type` 对尚未加载的任何内容使用。</span><span class="sxs-lookup"><span data-stu-id="51483-275">In Windows PowerShell (version 5.1 and below), you need to use `Add-Type` for anything that isn't already loaded.</span></span> <span data-ttu-id="51483-276">最常见的情况是，这适用于在全局程序集缓存 (GAC) 中找到的程序集。</span><span class="sxs-lookup"><span data-stu-id="51483-276">Most commonly, this applies to assemblies found in the Global Assembly Cache (GAC).</span></span>
<span data-ttu-id="51483-277">在 PowerShell 6 及更高版本中，没有 GAC，因此 PowerShell 在中安装其自己的程序集 `$PSHome` 。</span><span class="sxs-lookup"><span data-stu-id="51483-277">In PowerShell 6 and higher, there is no GAC, so PowerShell installs its own assemblies in `$PSHome`.</span></span>
<span data-ttu-id="51483-278">这些程序集是在请求时自动加载的，因此无需使用 `Add-Type` 来加载这些程序集。</span><span class="sxs-lookup"><span data-stu-id="51483-278">These assemblies are automatically loaded on request, so there's no need to use `Add-Type` to load them.</span></span> <span data-ttu-id="51483-279">但是， `Add-Type` 仍允许使用来允许脚本与任何 PowerShell 版本隐式兼容。</span><span class="sxs-lookup"><span data-stu-id="51483-279">However, using `Add-Type` is still permitted to allow scripts to be implicitly compatible with any version of PowerShell.</span></span>

<span data-ttu-id="51483-280">GAC 中的程序集可以按类型名称而不是按路径进行加载。</span><span class="sxs-lookup"><span data-stu-id="51483-280">Assemblies in the GAC can be loaded by type name, rather than by path.</span></span> <span data-ttu-id="51483-281">从任意路径加载程序集需要 `Add-Type` ，因为不能自动加载这些程序集。</span><span class="sxs-lookup"><span data-stu-id="51483-281">Loading assemblies from an arbitrary path requires `Add-Type`, since those assemblies cannot not be loaded automatically.</span></span>

## <span data-ttu-id="51483-282">相关链接</span><span class="sxs-lookup"><span data-stu-id="51483-282">RELATED LINKS</span></span>

[<span data-ttu-id="51483-283">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="51483-283">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_profiles.md)

[<span data-ttu-id="51483-284">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="51483-284">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="51483-285">Add-Member</span><span class="sxs-lookup"><span data-stu-id="51483-285">Add-Member</span></span>](Add-Member.md)

[<span data-ttu-id="51483-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="51483-286">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="51483-287">OutputAssemblyType</span><span class="sxs-lookup"><span data-stu-id="51483-287">OutputAssemblyType</span></span>](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[<span data-ttu-id="51483-288">平台调用 (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="51483-288">Platform Invoke (P/Invoke)</span></span>](/dotnet/standard/native-interop/pinvoke)

[<span data-ttu-id="51483-289">Where-Object</span><span class="sxs-lookup"><span data-stu-id="51483-289">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
