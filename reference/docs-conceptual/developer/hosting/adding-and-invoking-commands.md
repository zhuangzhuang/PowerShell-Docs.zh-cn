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
# <a name="adding-and-invoking-commands"></a>添加和调用命令

创建运行空间后，可以将 Windows PowerShellcommands 和脚本添加到管道，然后以同步或异步方式调用管道。

## <a name="creating-a-pipeline"></a>创建管道

[System.web](/dotnet/api/system.management.automation.powershell)类提供多种方法来向管道添加命令、参数和脚本。 您可以通过调用 Begininvoke [* 方法的](/dotnet/api/System.Management.Automation.PowerShell.Invoke) 重载，或通过调用 [*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) 的重载，然后通过调用 [Endinvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) 方法，以同步方式调用该管道，或通过调用此方法来异步调用该管道。

### <a name="addcommand"></a>AddCommand

1. 创建一个 " [管理](/dotnet/api/system.management.automation.powershell) " 对象。

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. 添加要执行的命令。

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. 调用命令。

   ```csharp
   ps.Invoke();
   ```

如果在调用 Addcommand [* 方法之前](/dotnet/api/System.Management.Automation.PowerShell.Invoke)多次调用了[*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法，则第一个命令的结果将通过管道传递到第二个命令，依此类推，直到第二个命令。 如果你不想通过管道将前一个命令的结果传递给命令，请通过调用 [Addstatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) 来添加它。

### <a name="addparameter"></a>AddParameter

 前面的示例执行一个不带任何参数的命令。 你可以使用 [Pscommand. Addparameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) 方法将参数添加到命令。例如，以下代码获取在 `PowerShell` 计算机上运行的所有名为的进程的列表。

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

可以通过重复调用 [Addparameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) 来添加其他参数。

```csharp
PowerShell.Create().AddCommand("Get-Command")
                   .AddParameter("Name", "Get-VM")
                   .AddParameter("Module", "Hyper-V")
                   .Invoke();
```

你还可以通过调用 [Addparameters *](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) 方法添加参数名和值的字典，。

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "Get-VM");

parameters.Add("Module", "Hyper-V");
PowerShell.Create().AddCommand("Get-Command")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

你可以通过使用 [Addstatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) 方法模拟批处理，该方法将其他语句添加到管道的末尾下面的代码将获取名为的正在运行的进程的列表 `PowerShell` ，然后获取正在运行的服务的列表。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

您可以通过调用 [Addscript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript) 方法来运行现有的脚本。 下面的示例向管道添加一个脚本并运行该脚本。 此示例假定在名为的文件夹中已有一个名为的脚本 `MyScript.ps1` `D:\PSScripts` 。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(File.ReadAllText(@"D:\PSScripts\MyScript.ps1")).Invoke();
```

还有一个版本的 [Addscript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript) 方法，它采用名为的布尔参数 `useLocalScope` 。 如果将此参数设置为 `true` ，则脚本将在本地作用域中运行。 以下代码将在本地作用域中运行该脚本。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(File.ReadAllText(@"D:\PSScripts\MyScript.ps1"), true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>同步调用管道

向管道添加元素后，可以调用它。 若要以同步方式调用管道，请调用[一个方法的重载。](/dotnet/api/System.Management.Automation.PowerShell.Invoke) 下面的示例演示如何以同步方式调用管道。

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

### <a name="invoking-a-pipeline-asynchronously"></a>异步调用管道

您可以通过调用 [Begininvoke *](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) 的重载来异步调用管道，以创建 [IAsyncResult](/dotnet/api/system.iasyncresult) 对象，然后调用 [Endinvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) 方法，从而实现这一目标的调用。

 下面的示例演示如何以异步方式调用管道。

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

## <a name="see-also"></a>另请参阅

 [创建 InitialSessionState](./creating-an-initialsessionstate.md)

 [创建受限运行空间](./creating-a-constrained-runspace.md)
