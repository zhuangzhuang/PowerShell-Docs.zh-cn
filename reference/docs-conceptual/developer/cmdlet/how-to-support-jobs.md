---
ms.date: 03/09/2021
ms.topic: reference
title: 如何支持作业
description: 如何支持作业
ms.openlocfilehash: 1528f5d934605caa4009688845a6caa7b95b86a3
ms.sourcegitcommit: e679533f966f4e97cddae24531a22436da13610c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2021
ms.locfileid: "102532112"
---
# <a name="how-to-support-jobs"></a><span data-ttu-id="8a531-103">如何支持作业</span><span class="sxs-lookup"><span data-stu-id="8a531-103">How to Support Jobs</span></span>

<span data-ttu-id="8a531-104">此示例演示如何在编写 cmdlet 时支持作业。</span><span class="sxs-lookup"><span data-stu-id="8a531-104">This example shows how to support jobs when you write cmdlets.</span></span> <span data-ttu-id="8a531-105">如果希望用户将 cmdlet 作为后台作业运行，则必须包括以下过程中所述的代码。</span><span class="sxs-lookup"><span data-stu-id="8a531-105">If you want users to run your cmdlet as a background job, you must include the code described in the following procedure.</span></span> <span data-ttu-id="8a531-106">有关后台作业的详细信息，请参阅 [后台作业](./background-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="8a531-106">For more information about background jobs, see [Background Jobs](./background-jobs.md).</span></span>

## <a name="to-support-jobs"></a><span data-ttu-id="8a531-107">支持作业</span><span class="sxs-lookup"><span data-stu-id="8a531-107">To support jobs</span></span>

1. <span data-ttu-id="8a531-108">定义 `AsJob` 开关参数，使用户可以决定是否将 cmdlet 作为作业运行。</span><span class="sxs-lookup"><span data-stu-id="8a531-108">Define an `AsJob` switch parameter so that the user can decide whether to run the cmdlet as a job.</span></span>

    <span data-ttu-id="8a531-109">下面的示例演示了 AsJob 参数声明。</span><span class="sxs-lookup"><span data-stu-id="8a531-109">The following example shows an AsJob parameter declaration.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter AsJob
    {
      get { return asjob; }
      set { asjob = value; }
    }
    private bool asjob;
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06AsJobParam](msh_samplesGetProc06#GetProc06AsJobParam)]  -->

1. <span data-ttu-id="8a531-110">创建一个派生自 [system.object](/dotnet/api/System.Management.Automation.Job) 类的对象。</span><span class="sxs-lookup"><span data-stu-id="8a531-110">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="8a531-111">此对象可以是自定义作业对象，也可以是 Windows PowerShell 提供的作业对象之一，如 [Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) 对象。</span><span class="sxs-lookup"><span data-stu-id="8a531-111">This object can be a custom job object or one of the job objects provided by Windows PowerShell, such a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

    <span data-ttu-id="8a531-112">下面的示例演示一个自定义作业对象。</span><span class="sxs-lookup"><span data-stu-id="8a531-112">The following example shows a custom job object.</span></span>

    ```csharp
    private SampleJob job = new SampleJob("Get-ProcAsJob");
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06JobObject](msh_samplesGetProc06#GetProc06JobObject)]  -->

1. <span data-ttu-id="8a531-113">在记录处理方法中，添加 `if` 语句以检测 cmdlet 是否应作为作业运行。</span><span class="sxs-lookup"><span data-stu-id="8a531-113">In a record processing method, add an `if` statement to detect whether the cmdlet should run as a job.</span></span> <span data-ttu-id="8a531-114">下面的代码使用 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法来实现。</span><span class="sxs-lookup"><span data-stu-id="8a531-114">The following code uses the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

    ```csharp
    protected override void ProcessRecord()
    {
      if (asjob)
      {
        // Add the job definition to the job repository,
        // return the job object, and then create the thread
        // used to run the job.
        JobRepository.Add(job);
        WriteObject(job);
        ThreadPool.QueueUserWorkItem(WorkItem);
      }
      else
      {
        job.ProcessJob();
        foreach (PSObject p in job.Output)
        {
          WriteObject(p);
        }
      }
    }
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06ProcessRecord](msh_samplesGetProc06#GetProc06ProcessRecord)]  -->

1. <span data-ttu-id="8a531-115">对于自定义作业对象，请实现 job 类。</span><span class="sxs-lookup"><span data-stu-id="8a531-115">For custom job objects, implement the job class.</span></span>

    ```csharp
    private class SampleJob : Job
    {
      internal SampleJob(string command)
          : base(command)
      {
        SetJobState(JobState.NotStarted);
      }
      public override string StatusMessage
      {
        get { throw new NotImplementedException(); }
      }

      public override bool HasMoreData
      {
        get
        {
          return hasMoreData;
        }
      }
      private bool hasMoreData = true;

      public override string Location
      {
        get { throw new NotImplementedException(); }
      }

      public override void StopJob()
      {
        throw new NotImplementedException();
      }

      internal void ProcessJob()
      {
        SetJobState(JobState.Running);
        DoProcessLogic();
        SetJobState(JobState.Completed);
      }

      // Retrieve the processes of the local computer.
      void DoProcessLogic()
      {
        Process[] p = Process.GetProcesses();

        foreach (Process pl in p)
        {
          Output.Add(PSObject.AsPSObject(pl));
        }
        Output.Complete();
      } // End DoProcessLogic.
    } // End SampleJob class.
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06JobClass](msh_samplesGetProc06#GetProc06JobClass)]  -->

1. <span data-ttu-id="8a531-116">如果该 cmdlet 执行工作，请调用 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 方法，以将进程对象返回到管道。</span><span class="sxs-lookup"><span data-stu-id="8a531-116">If the cmdlet performs the work, call the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method to return a process object to the pipeline.</span></span> <span data-ttu-id="8a531-117">如果以作业的形式执行工作，请将子作业添加到作业。</span><span class="sxs-lookup"><span data-stu-id="8a531-117">If the work is performed as a job, add child job to the job.</span></span>

    ```csharp
    void DoProcessLogic(bool asJob)
    {
      Process[] p = Process.GetProcesses();

      foreach (Process pl in p)
      {
        if (!asjob)
        {
          WriteObject(pl);
        }
        else
        {
          job.ChildJobs[0].Output.Add(new PSObject(pl));
        }
      }
    } // End DoProcessLogic.
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06Output](msh_samplesGetProc06#GetProc06Output)]  -->

## <a name="example"></a><span data-ttu-id="8a531-118">示例</span><span class="sxs-lookup"><span data-stu-id="8a531-118">Example</span></span>

<span data-ttu-id="8a531-119">下面的示例代码演示了可在内部或通过使用后台作业检索进程的 **Get Proc** cmdlet 的代码。</span><span class="sxs-lookup"><span data-stu-id="8a531-119">The following sample code shows the code for a **Get-Proc** cmdlet that can retrieve processes internally or by using a background job.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;  // Windows PowerShell namespace.
using System.Threading;              // Thread pool namespace for posting work.
using System.Diagnostics;            // Diagnostics namespace for retrieving
                                     // process objects.

// This sample shows a cmdlet whose work can be done by the cmdlet or by using
// a background job. Background jobs are executed in their own thread,
// independent of the pipeline thread in which the cmdlet is executed.
//
// To load this cmdlet, create a module folder and copy the GetProcessSample06.dll
// assembly into the module folder. Make sure that the path to the module folder
// is added to the $PSModulePath environment variable.
// Module folder path:
//    user/documents/WindowsPowerShell/modules/GetProcessSample06
//
// To import the module, run the following command: Import-Module GetProcessSample06.
// To test the cmdlet, run the following command: Get-Proc -name <process name>
//

//
namespace Microsoft.Samples.PowerShell.Commands
{
  /// <summary>
  ///  This cmdlet retrieves process internally or returns
  ///  a job that retrieves the processes.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public sealed class GetProcCommand : PSCmdlet
  {

    #region Parameters
    /// <summary>
    /// Specify the Name parameter. This parameter accepts
    /// process names from the command line.
    /// </summary>
    [Parameter(
               Position = 0,
               ValueFromPipeline = true,
               ValueFromPipelineByPropertyName = true)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return processNames; }
      set { processNames = value; }
    }
    private string[] processNames;

    /// <summary>
    /// Specify the AsJob parameter. This parameter indicates
    /// whether the cmdlet should retrieve the processes internally
    /// or return a Job object that retrieves the processes.
    /// </summary>
    [Parameter()]
    public SwitchParameter AsJob
    {
      get { return asjob; }
      set { asjob = value; }
    }
    private bool asjob;

    #endregion Parameters

    #region Cmdlet Overrides

    // Create a custom job object.
    private SampleJob job = new SampleJob("Get-ProcAsJob");

    /// <summary>
    /// Determines if the processes should be retrieved
    /// internally or if a Job object should be returned.
    /// </summary>
    protected override void ProcessRecord()
    {
      if (asjob)
      {
        // Add the job definition to the job repository,
        // return the job object, and then create the thread
        // used to run the job.
        JobRepository.Add(job);
        WriteObject(job);
        ThreadPool.QueueUserWorkItem(WorkItem);
      }
      else
      {
        job.ProcessJob();
        foreach (PSObject p in job.Output)
        {
          WriteObject(p);
        }
      }
    }
    #endregion Overrides

    // Implement a custom job that derives
    // from the System.Management.Automation.Job class.
    private class SampleJob : Job
    {
      internal SampleJob(string command)
          : base(command)
      {
        SetJobState(JobState.NotStarted);
      }
      public override string StatusMessage
      {
        get { throw new NotImplementedException(); }
      }

      public override bool HasMoreData
      {
        get
        {
          return hasMoreData;
        }
      }
      private bool hasMoreData = true;

      public override string Location
      {
        get { throw new NotImplementedException(); }
      }

      public override void StopJob()
      {
        throw new NotImplementedException();
      }

      internal void ProcessJob()
      {
        SetJobState(JobState.Running);
        DoProcessLogic();
        SetJobState(JobState.Completed);
      }

      // Retrieve the processes of the local computer.
      void DoProcessLogic()
      {
        Process[] p = Process.GetProcesses();

        foreach (Process pl in p)
        {
          Output.Add(PSObject.AsPSObject(pl));
        }
        Output.Complete();
      } // End DoProcessLogic.
    } // End SampleJob class.

    void WorkItem(object dummy)
    {
       job.ProcessJob();
    }

    // Display the results of the work. If not a job,
    // process objects are returned. If a job, the
    // output is added to the job as a child job.
    void DoProcessLogic(bool asJob)
    {
      Process[] p = Process.GetProcesses();

      foreach (Process pl in p)
      {
        if (!asjob)
        {
          WriteObject(pl);
        }
        else
        {
          job.ChildJobs[0].Output.Add(new PSObject(pl));
        }
      }
    } // End DoProcessLogic.
  } //End GetProcCommand
}
```

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesGetProc06#GetProc06All](msh_samplesGetProc06#GetProc06All)]  -->
