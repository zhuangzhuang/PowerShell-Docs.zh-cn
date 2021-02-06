---
description: 注册表
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_registry_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Registry 提供程序
ms.openlocfilehash: 2d57afc164885b4d207108a360215e63a5431632
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598859"
---
# <a name="registry-provider"></a><span data-ttu-id="ff7aa-103">注册表提供程序</span><span class="sxs-lookup"><span data-stu-id="ff7aa-103">Registry provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="ff7aa-104">提供程序名称</span><span class="sxs-lookup"><span data-stu-id="ff7aa-104">Provider name</span></span>

<span data-ttu-id="ff7aa-105">注册表</span><span class="sxs-lookup"><span data-stu-id="ff7aa-105">Registry</span></span>

## <a name="drives"></a><span data-ttu-id="ff7aa-106">驱动器</span><span class="sxs-lookup"><span data-stu-id="ff7aa-106">Drives</span></span>

<span data-ttu-id="ff7aa-107">`HKLM:`, `HKCU:`</span><span class="sxs-lookup"><span data-stu-id="ff7aa-107">`HKLM:`, `HKCU:`</span></span>

## <a name="capabilities"></a><span data-ttu-id="ff7aa-108">功能</span><span class="sxs-lookup"><span data-stu-id="ff7aa-108">Capabilities</span></span>

<span data-ttu-id="ff7aa-109">**ShouldProcess**、 **UseTransactions**</span><span class="sxs-lookup"><span data-stu-id="ff7aa-109">**ShouldProcess**, **UseTransactions**</span></span>

## <a name="short-description"></a><span data-ttu-id="ff7aa-110">简短说明</span><span class="sxs-lookup"><span data-stu-id="ff7aa-110">Short description</span></span>

<span data-ttu-id="ff7aa-111">提供对 PowerShell 中的注册表项、条目和值的访问权限。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-111">Provides access to the registry keys, entries, and values in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="ff7aa-112">详细说明</span><span class="sxs-lookup"><span data-stu-id="ff7aa-112">Detailed description</span></span>

<span data-ttu-id="ff7aa-113">PowerShell **注册表** 提供程序可让你获取、添加、更改、清除和删除 PowerShell 中的注册表项、条目和值。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-113">The PowerShell **Registry** provider lets you get, add, change, clear, and delete registry keys, entries, and values in PowerShell.</span></span>

<span data-ttu-id="ff7aa-114">**注册表** 驱动器是包含计算机上的注册表项和子项的分层命名空间。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-114">The **Registry** drives are a hierarchical namespace containing the registry keys and subkeys on your computer.</span></span> <span data-ttu-id="ff7aa-115">注册表条目和注册表值不是该层次结构的组成部分。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-115">Registry entries and values are not components of that hierarchy.</span></span> <span data-ttu-id="ff7aa-116">而是每个注册表项的属性。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-116">Instead, they are properties of each of the keys.</span></span>

<span data-ttu-id="ff7aa-117">**注册表** 提供程序支持以下 cmdlet，本文将对此进行介绍。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-117">The **Registry** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="ff7aa-118">Get-Location</span><span class="sxs-lookup"><span data-stu-id="ff7aa-118">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="ff7aa-119">Set-Location</span><span class="sxs-lookup"><span data-stu-id="ff7aa-119">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="ff7aa-120">Get-Item</span><span class="sxs-lookup"><span data-stu-id="ff7aa-120">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="ff7aa-121">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="ff7aa-121">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="ff7aa-122">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="ff7aa-122">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="ff7aa-123">Move-Item</span><span class="sxs-lookup"><span data-stu-id="ff7aa-123">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="ff7aa-124">New-Item</span><span class="sxs-lookup"><span data-stu-id="ff7aa-124">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="ff7aa-125">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="ff7aa-125">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="ff7aa-126">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ff7aa-126">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="ff7aa-127">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ff7aa-127">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="ff7aa-128">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ff7aa-128">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="ff7aa-129">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ff7aa-129">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="ff7aa-130">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="ff7aa-130">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="ff7aa-131">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="ff7aa-131">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="ff7aa-132">此提供程序公开的类型</span><span class="sxs-lookup"><span data-stu-id="ff7aa-132">Types exposed by this provider</span></span>

<span data-ttu-id="ff7aa-133">注册表项表示为 [Microsoft. RegistryKey](/dotnet/api/microsoft.win32.registrykey) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-133">Registry keys are represented as instances of the [Microsoft.Win32.RegistryKey](/dotnet/api/microsoft.win32.registrykey) class.</span></span> <span data-ttu-id="ff7aa-134">注册表项表示为 [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-134">Registry entries are represented as instances of the [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) class.</span></span>

## <a name="navigating-the-registry-drives"></a><span data-ttu-id="ff7aa-135">导航注册表驱动器</span><span class="sxs-lookup"><span data-stu-id="ff7aa-135">Navigating the Registry drives</span></span>

<span data-ttu-id="ff7aa-136">**注册表** 提供程序将其数据存储公开为两个默认驱动器。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-136">The **Registry** provider exposes its data store as two default drives.</span></span> <span data-ttu-id="ff7aa-137">注册表位置 HKEY_LOCAL_MACHINE 映射到 `HKLM:` 驱动器，HKEY_CURRENT_USER 映射到 `HKCU:` 驱动器。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-137">The registry location HKEY_LOCAL_MACHINE is mapped to the `HKLM:` drive and HKEY_CURRENT_USER is mapped to the `HKCU:` drive.</span></span> <span data-ttu-id="ff7aa-138">若要使用注册表，可以使用以下命令将位置更改为 `HKLM:` 驱动器。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-138">To work with the registry, you can change your location to the `HKLM:` drive using the following command.</span></span>

```powershell
Set-Location HKLM:
```

<span data-ttu-id="ff7aa-139">若要返回到文件系统驱动器，请键入驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-139">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="ff7aa-140">例如，键入：</span><span class="sxs-lookup"><span data-stu-id="ff7aa-140">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="ff7aa-141">还可以从任何其他 PowerShell 驱动器使用 **注册表** 提供程序。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-141">You can also work with the **Registry** provider from any other PowerShell drive.</span></span> <span data-ttu-id="ff7aa-142">若要从其他位置引用注册表项，请在路径中使用驱动器名称 (`HKLM:` ， `HKCU:`) 。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-142">To reference a registry key from another location, use the drive name (`HKLM:`, `HKCU:`) in the path.</span></span> <span data-ttu-id="ff7aa-143">使用反斜杠 (\\) 或正斜杠 (/) 来指示 **注册表** 驱动器的级别。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-143">Use a backslash (\\) or a forward slash (/) to indicate a level of the **Registry** drive.</span></span>

```powershell
PS C:\> cd HKLM:\Software
```

> [!NOTE]
> <span data-ttu-id="ff7aa-144">PowerShell 使用别名以允许你熟悉的方法来处理提供程序路径。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-144">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="ff7aa-145">命令（如 `dir` 和） `ls` 现在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的别名， `cd` 是 [集位置](xref:Microsoft.PowerShell.Management.Set-Location)的别名， `pwd` 是 [获取位置](xref:Microsoft.PowerShell.Management.Get-Location)的别名。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-145">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location), and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

<span data-ttu-id="ff7aa-146">最后一个示例显示了另一种可以用来导航 **注册表** 提供程序的路径语法。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-146">This last example shows another path syntax you can use to navigate the **Registry** provider.</span></span> <span data-ttu-id="ff7aa-147">此语法使用提供程序名称，后跟两个冒号 `::` 。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-147">This syntax uses the provider name, followed by two colons `::`.</span></span> <span data-ttu-id="ff7aa-148">此语法允许使用完整的 HIVE 名称，而不是映射的驱动器名称 `HKLM` 。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-148">This syntax allows you to use the full HIVE name, instead of the mapped drive name `HKLM`.</span></span>

```powershell
cd "Registry::HKEY_LOCAL_MACHINE\Software"
```

## <a name="displaying-the-contents-of-registry-keys"></a><span data-ttu-id="ff7aa-149">显示注册表项的内容</span><span class="sxs-lookup"><span data-stu-id="ff7aa-149">Displaying the contents of registry keys</span></span>

<span data-ttu-id="ff7aa-150">注册表分为多个键、子项和项。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-150">The registry is divided into keys, subkeys, and entries.</span></span> <span data-ttu-id="ff7aa-151">有关注册表结构的详细信息，请参阅 [注册表的结构](/windows/desktop/sysinfo/structure-of-the-registry)。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-151">For more information about registry structure, see [Structure of the Registry](/windows/desktop/sysinfo/structure-of-the-registry).</span></span>

<span data-ttu-id="ff7aa-152">在 **注册表** 驱动器中，每个密钥都是一个容器。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-152">In a **Registry** drive, each key is a container.</span></span> <span data-ttu-id="ff7aa-153">键可以包含任意数量的键。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-153">A key can contain any number of keys.</span></span> <span data-ttu-id="ff7aa-154">具有父键的注册表项称为 "子项"。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-154">A registry key that has a parent key is called a subkey.</span></span> <span data-ttu-id="ff7aa-155">你可以使用 `Get-ChildItem` 查看注册表项并 `Set-Location` 导航到密钥路径。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-155">You can use `Get-ChildItem` to view registry keys and `Set-Location` to navigate to a key path.</span></span>

<span data-ttu-id="ff7aa-156">注册表值是注册表项的属性。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-156">Registry values are attributes of a registry key.</span></span> <span data-ttu-id="ff7aa-157">在 **注册表** 驱动器中，它们被称为 " **项目属性**"。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-157">In the **Registry** drive, they are called **Item Properties**.</span></span> <span data-ttu-id="ff7aa-158">注册表项可以同时具有子键和项属性。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-158">A registry key can have both children keys and item properties.</span></span>

<span data-ttu-id="ff7aa-159">在此示例中，显示了和之间的差异 `Get-Item` `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-159">In this example, the difference between `Get-Item` and `Get-ChildItem` is shown.</span></span> <span data-ttu-id="ff7aa-160">当你 `Get-Item` 在 "后台处理程序" 注册表项上使用时，你可以查看其属性。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-160">When you use `Get-Item` on the "Spooler" registry key, you can view its properties.</span></span>

```
PS C:\ > Get-Item -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services


Name        Property
----        --------
Spooler     DependOnService    : {RPCSS, http}
            Description        : @%systemroot%\system32\spoolsv.exe,-2
            DisplayName        : @%systemroot%\system32\spoolsv.exe,-1
            ErrorControl       : 1
            FailureActions     : {16, 14, 0, 0...}
            Group              : SpoolerGroup
            ImagePath          : C:\WINDOWS\System32\spoolsv.exe
            ObjectName         : LocalSystem
            RequiredPrivileges : {SeTcbPrivilege, SeImpersonatePrivilege, ...
            ServiceSidType     : 1
            Start              : 2
            Type               : 27
```

<span data-ttu-id="ff7aa-161">每个注册表项也可以具有子项。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-161">Each registry key can also have subkeys.</span></span> <span data-ttu-id="ff7aa-162">使用 `Get-Item` 注册表项时，不显示子项。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-162">When you use `Get-Item` on a registry key, the subkeys are not displayed.</span></span> <span data-ttu-id="ff7aa-163">该 `Get-ChildItem` cmdlet 将显示 "后台处理程序" 键的子项，其中包括每个子项的属性。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-163">The `Get-ChildItem` cmdlet will show you children items of the "Spooler" key, including each subkey's properties.</span></span> <span data-ttu-id="ff7aa-164">使用时，不会显示父键属性 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-164">The parent keys properties are not shown when using `Get-ChildItem`.</span></span>

```
PS C:\> Get-ChildItem -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Spooler


Name             Property
----             --------
Performance      Close           : PerfClose
                 Collect         : PerfCollect
                 Collect Timeout : 2000
                 Library         : C:\Windows\System32\winspool.drv
                 Object List     : 1450
                 Open            : PerfOpen
                 Open Timeout    : 4000
Security         Security : {1, 0, 20, 128...}
```

<span data-ttu-id="ff7aa-165">此 `Get-Item` cmdlet 还可用于当前位置。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-165">The `Get-Item` cmdlet can also be used on the current location.</span></span> <span data-ttu-id="ff7aa-166">下面的示例导航到 "后台处理程序" 注册表项并获取项属性。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-166">The following example navigates to the "Spooler" registry key and gets the item properties.</span></span>
<span data-ttu-id="ff7aa-167">点 `.` 用于指示当前位置。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-167">The dot `.` is used to indicate the current location.</span></span>

```
PS C:\> cd HKLM:\System\CurrentControlSet\Services\Spooler
PS HKLM:\SYSTEM\CurrentControlSet\Services\Spooler> Get-Item .

    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services

Name             Property
----             --------
Spooler          DependOnService    : {RPCSS, http}
                 Description        : @%systemroot%\system32\spoolsv.exe,-2
...
```

<span data-ttu-id="ff7aa-168">有关本部分中所述 cmdlet 的详细信息，请参阅以下文章。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-168">For more information on the cmdlets covered in this section, see the following articles.</span></span>

<span data-ttu-id="ff7aa-169">-[获取项](xref:Microsoft.PowerShell.Management.Get-Item) 
-[Get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="ff7aa-169">-[Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
-[Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span></span>

## <a name="viewing-registry-key-values"></a><span data-ttu-id="ff7aa-170">查看注册表项值</span><span class="sxs-lookup"><span data-stu-id="ff7aa-170">Viewing registry key values</span></span>

<span data-ttu-id="ff7aa-171">注册表项值存储为每个注册表项的属性。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-171">Registry key values are stored as properties of each registry key.</span></span> <span data-ttu-id="ff7aa-172">`Get-ItemProperty`Cmdlet 将使用指定的名称查看注册表项属性。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-172">The `Get-ItemProperty` cmdlet views registry key properties using the name you specify.</span></span> <span data-ttu-id="ff7aa-173">结果为 **PSCustomObject** ，其中包含指定的属性。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-173">The result is a **PSCustomObject** containing the properties you specify.</span></span>

<span data-ttu-id="ff7aa-174">下面的示例使用 `Get-ItemProperty` cmdlet 查看所有属性。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-174">The Following example uses the `Get-ItemProperty` cmdlet to view all properties.</span></span> <span data-ttu-id="ff7aa-175">如果将生成的对象存储在变量中，则可以访问所需的属性值。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-175">Storing the resulting object in a variable allows you to access the desired property value.</span></span>

```powershell
$p = Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler
$p.DependOnService
```

```output
RPCSS
http
```

<span data-ttu-id="ff7aa-176">指定参数的值 `-Name` 会选择指定的属性，并返回 **PSCustomObject**。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-176">Specifying a value for the `-Name` parameter selects the properties you specify and returns the **PSCustomObject**.</span></span>  <span data-ttu-id="ff7aa-177">下面的示例演示使用参数时的输出差异 `-Name` 。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-177">The following example shows the difference in output when you use the `-Name` parameter.</span></span>

```
PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem

BUILD                      : 17134.1
Installation Directory     : C:\WINDOWS\system32\WBEM
MOF Self-Install Directory : C:\WINDOWS\system32\WBEM\MOF
PSPath                     : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath               : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName                : Wbem
PSDrive                    : HKLM
PSProvider                 : Microsoft.PowerShell.Core\Registry

PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD

BUILD        : 17134.1
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName  : Wbem
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
```

<span data-ttu-id="ff7aa-178">从 PowerShell 5.0 开始， `Get-ItemPropertyValue` cmdlet 仅返回指定属性的值。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-178">Beginning in PowerShell 5.0, the `Get-ItemPropertyValue` cmdlet returns only the value of the property you specify.</span></span>

```powershell
Get-ItemPropertyValue -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD
```

```output
17134.1
```

<span data-ttu-id="ff7aa-179">有关本部分中使用的 cmdlet 的详细信息，请参阅以下文章。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-179">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="ff7aa-180">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ff7aa-180">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="ff7aa-181">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="ff7aa-181">Get-ItemPropertyValue</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)

## <a name="changing-registry-key-values"></a><span data-ttu-id="ff7aa-182">更改注册表项值</span><span class="sxs-lookup"><span data-stu-id="ff7aa-182">Changing registry key values</span></span>

<span data-ttu-id="ff7aa-183">`Set-ItemProperty`Cmdlet 将设置注册表项的属性。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-183">The `Set-ItemProperty` cmdlet will set attributes for registry keys.</span></span> <span data-ttu-id="ff7aa-184">下面的示例使用将 `Set-ItemProperty` 后台处理程序服务启动类型更改为 "手动"。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-184">The following example uses `Set-ItemProperty` to change the spooler service start type to manual.</span></span> <span data-ttu-id="ff7aa-185">该示例使用 cmdlet 将 **StartType** 更改回 *自动* `Set-Service` 。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-185">The example changes the **StartType** back to *Automatic* using the `Set-Service` cmdlet.</span></span>

```
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler Automatic

PS C:\> $path = "HKLM:\SYSTEM\CurrentControlSet\Services\Spooler\"
PS C:\> Set-ItemProperty -Path $path -Name Start -Value 3
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler    Manual

PS C:\> Set-Service -Name Spooler -StartupType Automatic
```

<span data-ttu-id="ff7aa-186">每个注册表项都有一个 *默认* 值。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-186">Each registry key has a *default* value.</span></span> <span data-ttu-id="ff7aa-187">您可以使用或更改注册表项的 *默认* 值 `Set-Item` `Set-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-187">You can change the *default* value for a registry key with either `Set-Item` or `Set-ItemProperty`.</span></span>

```powershell
Set-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name "(default)" -Value "one"
Set-Item -Path HKLM:\SOFTWARE\Contoso -Value "two"
```

<span data-ttu-id="ff7aa-188">有关本部分中使用的 cmdlet 的详细信息，请参阅以下文章。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-188">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="ff7aa-189">Set-Item</span><span class="sxs-lookup"><span data-stu-id="ff7aa-189">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="ff7aa-190">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ff7aa-190">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="creating-registry-keys-and-values"></a><span data-ttu-id="ff7aa-191">创建注册表项和值</span><span class="sxs-lookup"><span data-stu-id="ff7aa-191">Creating registry keys and values</span></span>

<span data-ttu-id="ff7aa-192">该 `New-Item` cmdlet 将创建具有你提供的名称的注册表项。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-192">The `New-Item` cmdlet will create registry keys with a name that you provide.</span></span>
<span data-ttu-id="ff7aa-193">你还可以使用 `mkdir` 函数 `New-Item` 在内部调用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-193">You can also use the `mkdir` function, which calls the `New-Item` cmdlet internally.</span></span>

```
PS HKLM:\SOFTWARE\> mkdir ContosoCompany

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
ContosoCompany
```

<span data-ttu-id="ff7aa-194">可以使用 `New-ItemProperty` cmdlet 在指定的注册表项中创建值。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-194">You can use the `New-ItemProperty` cmdlet to create values in a registry key that you specify.</span></span> <span data-ttu-id="ff7aa-195">下面的示例在 ContosoCompany 注册表项上创建新的 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-195">The following example creates a new DWORD value on the ContosoCompany registry key.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\ContosoCompany"
New-ItemProperty -Path  -Name Test -Type DWORD -Value 1
```

> [!NOTE]
> <span data-ttu-id="ff7aa-196">有关其他允许的类型值，请查看本文中的动态参数部分。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-196">Review the dynamic parameters section in this article for other allowed type values.</span></span>

<span data-ttu-id="ff7aa-197">有关详细的 cmdlet 用法，请参阅 [set-itemproperty](xref:Microsoft.PowerShell.Management.New-ItemProperty)。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-197">For detailed cmdlet usage, see [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty).</span></span>

## <a name="copying-registry-keys-and-values"></a><span data-ttu-id="ff7aa-198">复制注册表项和值</span><span class="sxs-lookup"><span data-stu-id="ff7aa-198">Copying registry keys and values</span></span>

<span data-ttu-id="ff7aa-199">在 **注册表** 提供程序中，使用 `Copy-Item` cmdlet 复制注册表项和值。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-199">In the **Registry** provider, use the `Copy-Item` cmdlet copies registry keys and values.</span></span> <span data-ttu-id="ff7aa-200">使用 `Copy-ItemProperty` cmdlet 仅复制注册表值。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-200">Use the `Copy-ItemProperty` cmdlet to copy registry values only.</span></span>
<span data-ttu-id="ff7aa-201">以下命令将 "Contoso" 注册表项及其属性复制到指定位置 "HKLM： \ Software\Fabrikam"。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-201">The following command copies the "Contoso" registry key, and its properties to the specified location "HKLM:\Software\Fabrikam".</span></span>

<span data-ttu-id="ff7aa-202">`Copy-Item` 如果目标项不存在，则创建它。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-202">`Copy-Item` creates the destination key if it does not exist.</span></span> <span data-ttu-id="ff7aa-203">如果目标项存在，则会将源键的 `Copy-Item` 副本创建为子项， (目标键的子项) 。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-203">If the destination key exists, `Copy-Item` creates a duplicate of the source key as a child item (subkey) of the destination key.</span></span>

```powershell
Copy-Item -Path  HKLM:\Software\Contoso -Destination HKLM:\Software\Fabrikam
```

<span data-ttu-id="ff7aa-204">以下命令使用 cmdlet 将 " `Copy-ItemProperty` Server" 值从 "Contoso" 密钥复制到 "Fabrikam" 密钥。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-204">The following command uses the `Copy-ItemProperty` cmdlet to copy the "Server" value from the "Contoso" key to the "Fabrikam" key.</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Copy-ItemProperty -Path $source -Destination $dest -Name Server
```

<span data-ttu-id="ff7aa-205">有关本部分中使用的 cmdlet 的详细信息，请参阅以下文章。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-205">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="ff7aa-206">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="ff7aa-206">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="ff7aa-207">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ff7aa-207">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

## <a name="moving-registry-keys-and-values"></a><span data-ttu-id="ff7aa-208">移动注册表项和值</span><span class="sxs-lookup"><span data-stu-id="ff7aa-208">Moving registry keys and values</span></span>

<span data-ttu-id="ff7aa-209">`Move-Item`和 `Move-ItemProperty` cmdlet 的行为类似于其 "复制" 对应项。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-209">The `Move-Item` and `Move-ItemProperty` cmdlets behave like their "Copy" counterparts.</span></span> <span data-ttu-id="ff7aa-210">如果目标存在，则 `Move-Item` 将源键移动到目标项的下方。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-210">If the destination exists, `Move-Item` moves the source key underneath the destination key.</span></span> <span data-ttu-id="ff7aa-211">如果目标项不存在，则会将源键移动到目标路径。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-211">If the destination key does not exist, the source key is moved to the destination path.</span></span>

<span data-ttu-id="ff7aa-212">以下命令将 "Contoso" 键移动到路径 "HKLM： \ SOFTWARE\Fabrikam"。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-212">The following command moves the "Contoso" key to the path "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
Move-Item -Path HKLM:\SOFTWARE\Contoso -Destination HKLM:\SOFTWARE\Fabrikam
```

<span data-ttu-id="ff7aa-213">此命令将所有属性从 "HKLM： \ SOFTWARE\ContosoCompany" 移动到 "HKLM： \ SOFTWARE\Fabrikam"。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-213">This command moves all of the properties from "HKLM:\SOFTWARE\ContosoCompany" to "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Move-ItemProperty -Path $source -Destination $dest -Name *
```

<span data-ttu-id="ff7aa-214">有关本部分中使用的 cmdlet 的详细信息，请参阅以下文章。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-214">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="ff7aa-215">Move-Item</span><span class="sxs-lookup"><span data-stu-id="ff7aa-215">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="ff7aa-216">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ff7aa-216">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)

## <a name="renaming-registry-keys-and-values"></a><span data-ttu-id="ff7aa-217">重命名注册表项和值</span><span class="sxs-lookup"><span data-stu-id="ff7aa-217">Renaming registry keys and values</span></span>

<span data-ttu-id="ff7aa-218">你可以像对文件和文件夹一样重命名注册表项和值。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-218">You can rename registry keys and values just like you would files and folders.</span></span>
<span data-ttu-id="ff7aa-219">`Rename-Item` 重命名注册表项，同时 `Rename-ItemProperty` 重命名注册表值。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-219">`Rename-Item` renames registry keys, while `Rename-ItemProperty` renames registry values.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\Contoso"
Rename-ItemProperty -Path $path -Name ContosoTest -NewName FabrikamTest
Rename-Item -Path $path -NewName Fabrikam
```

## <a name="changing-security-descriptors"></a><span data-ttu-id="ff7aa-220">更改安全描述符</span><span class="sxs-lookup"><span data-stu-id="ff7aa-220">Changing security descriptors</span></span>

<span data-ttu-id="ff7aa-221">你可以使用和 cmdlet 限制对注册表项的访问 `Get-Acl` `Set-Acl` 。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-221">You can restrict access to registry keys using the `Get-Acl` and `Set-Acl` cmdlets.</span></span> <span data-ttu-id="ff7aa-222">下面的示例将具有 "完全控制" 的新用户添加到 "HKLM： \ SOFTWARE\Contoso" 注册表项。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-222">The following example adds a new user with full control to the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Contoso
$rule = New-Object System.Security.AccessControl.RegistryAccessRule `
("CONTOSO\jsmith", "FullControl", "Allow")
$acl.SetAccessRule($rule)
$acl | Set-Acl -Path HKLM:\SOFTWARE\Contoso
```

<span data-ttu-id="ff7aa-223">有关更多示例和 cmdlet 用法详细信息，请参阅以下文章。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-223">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="ff7aa-224">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="ff7aa-224">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="ff7aa-225">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="ff7aa-225">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="removing-and-clearing-registry-keys-and-values"></a><span data-ttu-id="ff7aa-226">删除和清除注册表项和值</span><span class="sxs-lookup"><span data-stu-id="ff7aa-226">Removing and clearing registry keys and values</span></span>

<span data-ttu-id="ff7aa-227">您可以通过使用 **Remove item** 删除包含的项，但如果项包含任何其他内容，系统将提示您确认删除。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-227">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="ff7aa-228">以下示例尝试删除密钥 "HKLM： \ SOFTWARE\Contoso"。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-228">The following example attempts to delete a key "HKLM:\SOFTWARE\Contoso".</span></span>

```
PS C:\> dir HKLM:\SOFTWARE\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Contoso

Name                           Property
----                           --------
ChildKey

PS C:\> Remove-Item -Path HKLM:\SOFTWARE\Contoso

Confirm
The item at HKLM:\SOFTWARE\Contoso has children and the -Recurse
parameter was not specified. If you continue, all children will be removed
with the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="ff7aa-229">若要在不提示的情况下删除包含的项，请指定 `-Recurse` 参数。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-229">To delete contained items without prompting, specify the `-Recurse` parameter.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso -Recurse
```

<span data-ttu-id="ff7aa-230">如果要删除 "HKLM： \ SOFTWARE\Contoso" 内的所有项，而不是 "HKLM： \ SOFTWARE\Contoso" 本身，请使用后面跟有通配符的尾随反斜杠 `\` 。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-230">If you wanted to remove all items within "HKLM:\SOFTWARE\Contoso" but not "HKLM:\SOFTWARE\Contoso" itself, use a trailing backslash `\` followed by a wildcard.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso\* -Recurse
```

<span data-ttu-id="ff7aa-231">此命令从 "HKLM： \ SOFTWARE\Contoso" 注册表项中删除 "ContosoTest" 注册表值。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-231">This command deletes the "ContosoTest" registry value from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name ContosoTest
```

<span data-ttu-id="ff7aa-232">`Clear-Item` 清除所有注册表项的注册表值。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-232">`Clear-Item` clears all registry values for a key.</span></span> <span data-ttu-id="ff7aa-233">下面的示例将清除 "HKLM： \ SOFTWARE\Contoso" 注册表项中的所有值。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-233">The following example clears all values from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span> <span data-ttu-id="ff7aa-234">若要仅清除特定属性，请使用 `Clear-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-234">To clear only a specific property, use `Clear-ItemProperty`.</span></span>

```
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name           Property
----           --------
Contoso        Server     : {a, b, c}
               HereString : {This is text which contains
               newlines. It also contains "quoted" strings}
               (default)  : 1

PS HKLM:\SOFTWARE\> Clear-Item .\Contoso\
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
Contoso
```

<span data-ttu-id="ff7aa-235">有关更多示例和 cmdlet 用法详细信息，请参阅以下文章。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-235">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="ff7aa-236">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="ff7aa-236">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="ff7aa-237">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ff7aa-237">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="ff7aa-238">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="ff7aa-238">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="ff7aa-239">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ff7aa-239">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)

## <a name="dynamic-parameters"></a><span data-ttu-id="ff7aa-240">动态参数</span><span class="sxs-lookup"><span data-stu-id="ff7aa-240">Dynamic parameters</span></span>

<span data-ttu-id="ff7aa-241">动态参数是 PowerShell 提供程序添加的 cmdlet 参数，只有在启用了提供程序的驱动器中使用 cmdlet 时，这些参数才可用。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-241">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="type-microsoftwin32registryvaluekind"></a><span data-ttu-id="ff7aa-242">键入 <RegistryValueKind></span><span class="sxs-lookup"><span data-stu-id="ff7aa-242">Type <Microsoft.Win32.RegistryValueKind></span></span>

<span data-ttu-id="ff7aa-243">建立或更改注册表值的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-243">Establishes or changes the data type of a registry value.</span></span> <span data-ttu-id="ff7aa-244">默认值为 `String` (REG_SZ) 。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-244">The default is `String` (REG_SZ).</span></span>

<span data-ttu-id="ff7aa-245">此参数可用于 [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-245">This parameter works as designed on the [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) cmdlet.</span></span> <span data-ttu-id="ff7aa-246">此外，还可以在注册表驱动器中用于 [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) cmdlet，但它不起作用。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-246">It is also available on the [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) cmdlet in the registry drives, but it has no effect.</span></span>

|<span data-ttu-id="ff7aa-247">值</span><span class="sxs-lookup"><span data-stu-id="ff7aa-247">Value</span></span> | <span data-ttu-id="ff7aa-248">说明</span><span class="sxs-lookup"><span data-stu-id="ff7aa-248">Description</span></span> |
| ---- | ----------- |
| `String` | <span data-ttu-id="ff7aa-249">指定以 null 结尾的字符串。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-249">Specifies a null-terminated string.</span></span> <span data-ttu-id="ff7aa-250">等效于 REG_SZ。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-250">Equivalent to REG_SZ.</span></span> |
| `ExpandString` | <span data-ttu-id="ff7aa-251">指定以 null 结尾的字符串，该字符串包含未展开的</span><span class="sxs-lookup"><span data-stu-id="ff7aa-251">Specifies a null-terminated string that contains unexpanded</span></span> |
|                | <span data-ttu-id="ff7aa-252">引用扩展时扩展的环境变量</span><span class="sxs-lookup"><span data-stu-id="ff7aa-252">references to environment variables that are expanded when</span></span> |
|                | <span data-ttu-id="ff7aa-253">检索值。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-253">the value is retrieved.</span></span> <span data-ttu-id="ff7aa-254">等效于 REG_EXPAND_SZ。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-254">Equivalent to REG_EXPAND_SZ.</span></span> |
| `Binary` | <span data-ttu-id="ff7aa-255">指定采用任意格式的二进制数据。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-255">Specifies binary data in any form.</span></span> <span data-ttu-id="ff7aa-256">等效于 REG_BINARY。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-256">Equivalent to REG_BINARY.</span></span> |
| `DWord` | <span data-ttu-id="ff7aa-257">指定一个 32 位的二进制数字。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-257">Specifies a 32-bit binary number.</span></span> <span data-ttu-id="ff7aa-258">等效于 REG_DWORD。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-258">Equivalent to REG_DWORD.</span></span> |
| `MultiString` | <span data-ttu-id="ff7aa-259">指定以 null 结尾的字符串的数组，由终止</span><span class="sxs-lookup"><span data-stu-id="ff7aa-259">Specifies an array of null-terminated strings terminated by</span></span> |
|               | <span data-ttu-id="ff7aa-260">两个 null 字符。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-260">two null characters.</span></span> <span data-ttu-id="ff7aa-261">等效于 REG_MULTI_SZ。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-261">Equivalent to REG_MULTI_SZ.</span></span> |
| `QWord` | <span data-ttu-id="ff7aa-262">指定一个 64 位的二进制数字。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-262">Specifies a 64-bit binary number.</span></span> <span data-ttu-id="ff7aa-263">等效于 REG_QWORD。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-263">Equivalent to REG_QWORD.</span></span> |
| `Unknown` | <span data-ttu-id="ff7aa-264">指示不受支持的注册表数据类型，例如</span><span class="sxs-lookup"><span data-stu-id="ff7aa-264">Indicates an unsupported registry data type, such as</span></span> |
|           | <span data-ttu-id="ff7aa-265">REG_RESOURCE_LIST。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-265">REG_RESOURCE_LIST.</span></span> |

#### <a name="cmdlets-supported"></a><span data-ttu-id="ff7aa-266">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="ff7aa-266">Cmdlets supported</span></span>

- [<span data-ttu-id="ff7aa-267">Set-Item</span><span class="sxs-lookup"><span data-stu-id="ff7aa-267">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="ff7aa-268">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ff7aa-268">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="using-the-pipeline"></a><span data-ttu-id="ff7aa-269">使用管道</span><span class="sxs-lookup"><span data-stu-id="ff7aa-269">Using the pipeline</span></span>

<span data-ttu-id="ff7aa-270">提供程序 cmdlet 接受管道输入。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-270">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="ff7aa-271">可以通过将提供程序数据从一个 cmdlet 发送到另一个提供程序 cmdlet 来使用管道来简化任务。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-271">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span> <span data-ttu-id="ff7aa-272">若要详细了解如何将管道与提供程序 cmdlet 配合使用，请参阅本文中提供的 cmdlet 参考。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-272">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="ff7aa-273">获取帮助</span><span class="sxs-lookup"><span data-stu-id="ff7aa-273">Getting help</span></span>

<span data-ttu-id="ff7aa-274">从 Windows PowerShell 3.0 开始，你可以获取有关提供程序 cmdlet 的自定义帮助主题，它们介绍了这些 cmdlet 在文件系统驱动器中的行为方式。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-274">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="ff7aa-275">若要获取针对文件系统驱动器进行自定义的帮助主题，请 `Get-Help` 在文件系统驱动器中运行命令，或使用 **Path** 参数指定文件系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="ff7aa-275">To get the help topics that are customized for the file system drive, run a `Get-Help` command in a file system drive or use the **Path** parameter to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path HKLM:
```

## <a name="see-also"></a><span data-ttu-id="ff7aa-276">请参阅</span><span class="sxs-lookup"><span data-stu-id="ff7aa-276">See also</span></span>

 [<span data-ttu-id="ff7aa-277">about_Providers</span><span class="sxs-lookup"><span data-stu-id="ff7aa-277">about_Providers</span></span>](../About/about_Providers.md)

