---
ms.date: 09/13/2016
ms.topic: reference
title: 添加和调用命令
description: 添加和调用命令
ms.openlocfilehash: f539172eaf119fe5774e158c77a00276c8ba9e0a
ms.sourcegitcommit: 880b00218708724a76503000c9eca181f4e00891
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2021
ms.locfileid: "99049419"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="9727e-103">添加和调用命令</span><span class="sxs-lookup"><span data-stu-id="9727e-103">Adding and invoking commands</span></span>

<span data-ttu-id="9727e-104">创建运行空间后，可以将 Windows PowerShellcommands 和脚本添加到管道，然后以同步或异步方式调用管道。</span><span class="sxs-lookup"><span data-stu-id="9727e-104">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="9727e-105">创建管道</span><span class="sxs-lookup"><span data-stu-id="9727e-105">Creating a pipeline</span></span>

<span data-ttu-id="9727e-106">[System.web](/dotnet/api/system.management.automation.powershell)类提供多种方法来向管道添加命令、参数和脚本。</span><span class="sxs-lookup"><span data-stu-id="9727e-106">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="9727e-107">您可以通过调用 Begininvoke [\* 方法的](/dotnet/api/System.Management.Automation.PowerShell.Invoke) 重载，或通过调用 [\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) 的重载，然后通过调用 [Endinvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) 方法，以同步方式调用该管道，或通过调用此方法来异步调用该管道。</span><span class="sxs-lookup"><span data-stu-id="9727e-107">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="9727e-108">AddCommand</span><span class="sxs-lookup"><span data-stu-id="9727e-108">AddCommand</span></span>

1. <span data-ttu-id="9727e-109">创建一个 " [管理](/dotnet/api/system.management.automation.powershell) " 对象。</span><span class="sxs-lookup"><span data-stu-id="9727e-109">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="9727e-110">添加要执行的命令。</span><span class="sxs-lookup"><span data-stu-id="9727e-110">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="9727e-111">调用命令。</span><span class="sxs-lookup"><span data-stu-id="9727e-111">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="9727e-112">如果在调用 Addcommand [\* 方法之前](/dotnet/api/System.Management.Automation.PowerShell.Invoke)多次调用了[\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法，则第一个命令的结果将通过管道传递到第二个命令，依此类推，直到第二个命令。</span><span class="sxs-lookup"><span data-stu-id="9727e-112">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="9727e-113">如果你不想通过管道将前一个命令的结果传递给命令，请通过调用 [Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) 来添加它。</span><span class="sxs-lookup"><span data-stu-id="9727e-113">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="9727e-114">AddParameter</span><span class="sxs-lookup"><span data-stu-id="9727e-114">AddParameter</span></span>

 <span data-ttu-id="9727e-115">前面的示例执行一个不带任何参数的命令。</span><span class="sxs-lookup"><span data-stu-id="9727e-115">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="9727e-116">你可以使用 [Pscommand. Addparameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) 方法将参数添加到命令。例如，以下代码获取在 `PowerShell` 计算机上运行的所有名为的进程的列表。</span><span class="sxs-lookup"><span data-stu-id="9727e-116">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="9727e-117">可以通过重复调用 [Addparameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) 来添加其他参数。</span><span class="sxs-lookup"><span data-stu-id="9727e-117">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Command")
                   .AddParameter("Name", "Get-VM")
                   .AddParameter("Module", "Hyper-V")
                   .Invoke();
```

<span data-ttu-id="9727e-118">你还可以通过调用 [Addparameters \*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) 方法添加参数名和值的字典，。</span><span class="sxs-lookup"><span data-stu-id="9727e-118">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "Get-VM");

parameters.Add("Module", "Hyper-V");
PowerShell.Create().AddCommand("Get-Command")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="9727e-119">AddStatement</span><span class="sxs-lookup"><span data-stu-id="9727e-119">AddStatement</span></span>

<span data-ttu-id="9727e-120">你可以通过使用 [Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) 方法模拟批处理，该方法将其他语句添加到管道的末尾下面的代码将获取名为的正在运行的进程的列表 `PowerShell` ，然后获取正在运行的服务的列表。</span><span class="sxs-lookup"><span data-stu-id="9727e-120">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="9727e-121">AddScript</span><span class="sxs-lookup"><span data-stu-id="9727e-121">AddScript</span></span>

<span data-ttu-id="9727e-122">您可以通过调用 [Addscript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) 方法来运行现有的脚本。</span><span class="sxs-lookup"><span data-stu-id="9727e-122">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="9727e-123">下面的示例向管道添加一个脚本并运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="9727e-123">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="9727e-124">此示例假定在名为的文件夹中已有一个名为的脚本 `MyScript.ps1` `D:\PSScripts` 。</span><span class="sxs-lookup"><span data-stu-id="9727e-124">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(File.ReadAllText(@"D:\PSScripts\MyScript.ps1")).Invoke();
```

<span data-ttu-id="9727e-125">还有一个版本的 [Addscript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) 方法，它采用名为的布尔参数 `useLocalScope` 。</span><span class="sxs-lookup"><span data-stu-id="9727e-125">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="9727e-126">如果将此参数设置为 `true` ，则脚本将在本地作用域中运行。</span><span class="sxs-lookup"><span data-stu-id="9727e-126">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="9727e-127">以下代码将在本地作用域中运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="9727e-127">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(File.ReadAllText(@"D:\PSScripts\MyScript.ps1"), true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="9727e-128">同步调用管道</span><span class="sxs-lookup"><span data-stu-id="9727e-128">Invoking a pipeline synchronously</span></span>

<span data-ttu-id="9727e-129">向管道添加元素后，可以调用它。</span><span class="sxs-lookup"><span data-stu-id="9727e-129">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="9727e-130">若要以同步方式调用管道，请调用[一个方法的重载。](/dotnet/api/System.Management.Automation.PowerShell.Invoke)</span><span class="sxs-lookup"><span data-stu-id="9727e-130">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="9727e-131">下面的示例演示如何以同步方式调用管道。</span><span class="sxs-lookup"><span data-stu-id="9727e-131">The following example shows how to synchronously invoke a pipeline.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="9727e-132">异步调用管道</span><span class="sxs-lookup"><span data-stu-id="9727e-132">Invoking a pipeline asynchronously</span></span>

<span data-ttu-id="9727e-133">您可以通过调用 [Begininvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) 的重载来异步调用管道，以创建 [IAsyncResult](/dotnet/api/system.iasyncresult) 对象，然后调用 [Endinvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) 方法，从而实现这一目标的调用。</span><span class="sxs-lookup"><span data-stu-id="9727e-133">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](/dotnet/api/system.iasyncresult) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="9727e-134">下面的示例演示如何以异步方式调用管道。</span><span class="sxs-lookup"><span data-stu-id="9727e-134">The following example shows how to invoke a pipeline asynchronously.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediately
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult asyncpl = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(asyncpl))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a><span data-ttu-id="9727e-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9727e-135">See Also</span></span>

 [<span data-ttu-id="9727e-136">创建 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="9727e-136">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="9727e-137">创建受限运行空间</span><span class="sxs-lookup"><span data-stu-id="9727e-137">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
