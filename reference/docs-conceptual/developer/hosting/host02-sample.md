---
title: Host02-voor beeld | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ab83bcb-2d31-4744-a8bc-2ee22e48fc1b
caps.latest.revision: 17
ms.openlocfilehash: cb21a4dd9bbc9ccd0f93ae6f7ecbc09cd89c29d3
ms.sourcegitcommit: ea7d87a7a56f368e3175219686dfa2870053c644
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818087"
---
# <a name="host02-sample"></a><span data-ttu-id="122d5-102">Voorbeeld Host02</span><span class="sxs-lookup"><span data-stu-id="122d5-102">Host02 Sample</span></span>

<span data-ttu-id="122d5-103">In dit voor beeld ziet u hoe u een host-toepassing schrijft die gebruikmaakt van de Windows Power shell-runtime samen met een aangepaste implementatie van de host.</span><span class="sxs-lookup"><span data-stu-id="122d5-103">This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="122d5-104">Met de hosttoepassing wordt de host-cultuur ingesteld op Duits, wordt de cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) uitgevoerd en worden de resultaten weer gegeven zoals u deze zou zien met behulp van pwrsh. exe, waarna de huidige gegevens en tijd in het Duits worden afgedrukt.</span><span class="sxs-lookup"><span data-stu-id="122d5-104">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

## <a name="requirements"></a><span data-ttu-id="122d5-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="122d5-105">Requirements</span></span>

 <span data-ttu-id="122d5-106">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="122d5-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="122d5-107">Laat zien</span><span class="sxs-lookup"><span data-stu-id="122d5-107">Demonstrates</span></span>

- <span data-ttu-id="122d5-108">Het maken van een aangepaste host waarvan de klassen zijn afgeleid van de klasse [System. Management. Automation. host. PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) , de klasse [System. Management. Automation. host. Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) en de klasse [System. Management. Automation. host. Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface) .</span><span class="sxs-lookup"><span data-stu-id="122d5-108">Creating a custom host whose classes derive from the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class, the [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) class, and the [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface) class.</span></span>

- <span data-ttu-id="122d5-109">Een runs Pace maken die gebruikmaakt van de aangepaste host.</span><span class="sxs-lookup"><span data-stu-id="122d5-109">Creating a runspace that uses the custom host.</span></span>

- <span data-ttu-id="122d5-110">De host-cultuur wordt ingesteld op Duits.</span><span class="sxs-lookup"><span data-stu-id="122d5-110">Setting the host culture to German.</span></span>

- <span data-ttu-id="122d5-111">Het maken van een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object dat een script uitvoert om de processen op te halen en te sorteren, haalt de huidige datum op die in het Duits wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="122d5-111">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that runs a script to retrieve and sort the processes, then retrieves the current date which is displayed in German.</span></span>

## <a name="example"></a><span data-ttu-id="122d5-112">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="122d5-112">Example</span></span>

 <span data-ttu-id="122d5-113">De volgende code toont een implementatie van een host-toepassing die gebruikmaakt van de aangepaste host.</span><span class="sxs-lookup"><span data-stu-id="122d5-113">The following code shows an implementation of a host application that uses the custom host.</span></span>

```csharp
// Copyright (c) 2006 Microsoft Corporation. All rights reserved.
//
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
// PARTICULAR PURPOSE.
//
using System;
using System.Collections.Generic;
using System.Text;
using System.Management.Automation;
using System.Management.Automation.Host;
using System.Management.Automation.Runspaces;
using System.Globalization;

namespace Microsoft.Samples.PowerShell.Host
{
  class Host02
  {
    /// <summary>
    /// Define the property that the PSHost implementation will
    /// use to tell the host application that it should exit.
    /// </summary>
    public bool ShouldExit
    {
      get { return shouldExit; }
      set { shouldExit = value; }
    }
    private bool shouldExit;

    /// <summary>
    /// Define the property that the PSHost implementation will
    /// use to tell the host application what exit code to use
    /// when exiting.
    /// </summary>
    public int ExitCode
    {
      get { return exitCode; }
      set { exitCode = value; }
    }
    private int exitCode;

    /// <summary>
    /// This sample uses the PowerShell runtime along with a host
    /// implementation to call get-process and display the results
    /// as you would see them in powershell.exe.
    /// </summary>
    /// <param name="args">Ignored</param>
    static void Main(string[] args)
    {
      // Set the current culture to German. We want this to be picked up when the MyHost
      // instance is created...
      System.Threading.Thread.CurrentThread.CurrentCulture = CultureInfo.GetCultureInfo("de-de");

      // Create the runspace so that you can access the pipeline.
      MyHost myHost = new MyHost(new Host02());

      Runspace myRunSpace = RunspaceFactory.CreateRunspace(myHost);
      myRunSpace.Open();

      // Create the pipeline.
      Pipeline pipe = myRunSpace.CreatePipeline();

      // Add the script we want to run. This script does two things.
      // First, it runs the Get-Process cmdlet with the cmdlet output
      // sorted by handle count. Second, the GetDate cmdlet is piped
      // to the Out-String cmdlet so that we can see the
      // date displayed in German.

      pipe.Commands.AddScript(@"
                    get-process | sort handlecount
                    # This should display the date in German...
                    get-date | out-string
                    ");

      // Add the default outputter to the end of the pipe and indicate
      // that it should handle both output and errors from the previous
      // commands. This will result in the output being written using the PSHost
      // and PSHostUserInterface classes instead of returning objects to the hosting
      // application.
      pipe.Commands.Add("out-default");
      pipe.Commands[0].MergeMyResults(PipelineResultTypes.Error,PipelineResultTypes.Output);

      // Invoke the pipeline. There will not be any objects
      // returned. The Out-Default cmdlet consumes the objects.
      pipe.Invoke();

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="example"></a><span data-ttu-id="122d5-114">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="122d5-114">Example</span></span>

 <span data-ttu-id="122d5-115">De volgende code is de implementatie van de klasse [System. Management. Automation. host. PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) die wordt gebruikt door deze hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="122d5-115">The following code is the implementation of the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class that is used by this host application.</span></span> <span data-ttu-id="122d5-116">Deze elementen die niet zijn geïmplementeerd, genereren een uitzonde ring of retour neren niets.</span><span class="sxs-lookup"><span data-stu-id="122d5-116">Those elements that are not implemented throw an exception or return nothing.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Host
{
  using System;
  using System.Globalization;
  using System.Management.Automation.Host;

  /// <summary>
  /// This is a sample implementation of the PSHost abstract class for
  /// console applications. Not all members are implemented. Those that
  /// are not implemented throw a NotImplementedException exception or
  /// return nothing.
  /// </summary>
  internal class MyHost : PSHost
  {
    /// <summary>
    /// A reference to the PSHost implementation.
    /// </summary>
    private Host02 program;

    /// <summary>
    /// The culture information of the thread that created
    /// this object.
    /// </summary>
    private CultureInfo originalCultureInfo =
        System.Threading.Thread.CurrentThread.CurrentCulture;

    /// <summary>
    /// The UI culture information of the thread that created
    /// this object.
    /// </summary>
    private CultureInfo originalUICultureInfo =
        System.Threading.Thread.CurrentThread.CurrentUICulture;

    /// <summary>
    /// The identifier of this PSHost implementation.
    /// </summary>
    private Guid myId = Guid.NewGuid();

    /// <summary>
    /// Initializes a new instance of the MyHost class. Keep
    /// a reference to the host application object so that it
    /// can be informed of when to exit.
    /// </summary>
    /// <param name="program">
    /// A reference to the host application object.
    /// </param>
    public MyHost(Host02 program)
    {
      this.program = program;
    }

    /// <summary>
    /// A reference to the implementation of the PSHostUserInterface
    /// class for this application.
    /// </summary>
    private MyHostUserInterface myHostUserInterface = new MyHostUserInterface();

    /// <summary>
    /// Gets the culture information to use. This implementation
    /// returns a snapshot of the culture information of the thread
    /// that created this object.
    /// </summary>
    public override System.Globalization.CultureInfo CurrentCulture
    {
      get { return this.originalCultureInfo; }
    }

    /// <summary>
    /// Gets the UI culture information to use. This implementation
    /// returns a snapshot of the UI culture information of the thread
    /// that created this object.
    /// </summary>
    public override System.Globalization.CultureInfo CurrentUICulture
    {
      get { return this.originalUICultureInfo; }
    }

    /// <summary>
    /// Gets an identifier for this host. This implementation always
    /// returns the GUID allocated at instantiation time.
    /// </summary>
    public override Guid InstanceId
    {
      get { return this.myId; }
    }

    /// <summary>
    /// Gets a string that contains the name of this host implementation.
    /// Keep in mind that this string may be used by script writers to
    /// identify when your host is being used.
    /// </summary>
    public override string Name
    {
      get { return "MySampleConsoleHostImplementation"; }
    }

    /// <summary>
    /// Gets an instance of the implementation of the PSHostUserInterface
    /// class for this application. This instance is allocated once at startup time
    /// and returned every time thereafter.
    /// </summary>
    public override PSHostUserInterface UI
    {
      get { return this.myHostUserInterface; }
    }

    /// <summary>
    /// Gets the version object for this application. Typically this
    /// should match the version resource in the application.
    /// </summary>
    public override Version Version
    {
      get { return new Version(1, 0, 0, 0); }
    }

    /// <summary>
    /// This API Instructs the host to interrupt the currently running
    /// pipeline and start a new nested input loop. In this example this
    /// functionality is not needed so the method throws a
    /// NotImplementedException exception.
    /// </summary>
    public override void EnterNestedPrompt()
    {
      throw new NotImplementedException(
            "The method or operation is not implemented.");
    }

    /// <summary>
    /// This API instructs the host to exit the currently running input loop.
    /// In this example this functionality is not needed so the method
    /// throws a NotImplementedException exception.
    /// </summary>
    public override void ExitNestedPrompt()
    {
      throw new NotImplementedException(
            "The method or operation is not implemented.");
    }

    /// <summary>
    /// This API is called before an external application process is
    /// started. Typically it is used to save state so that the parent
    /// can restore state that has been modified by a child process (after
    /// the child exits). In this example this functionality is not
    /// needed so the method returns nothing.
    /// </summary>
    public override void NotifyBeginApplication()
    {
      return;
    }

    /// <summary>
    /// This API is called after an external application process finishes.
    /// Typically it is used to restore state that a child process has
    /// altered. In this example, this functionality is not needed so
    /// the method returns nothing.
    /// </summary>
    public override void NotifyEndApplication()
    {
      return;
    }

    /// <summary>
    /// Indicate to the host application that exit has
    /// been requested. Pass the exit code that the host
    /// application should use when exiting the process.
    /// </summary>
    /// <param name="exitCode">The exit code that the
    /// host application should use.</param>
    public override void SetShouldExit(int exitCode)
    {
      this.program.ShouldExit = true;
      this.program.ExitCode = exitCode;
    }
  }
}
```

## <a name="example"></a><span data-ttu-id="122d5-117">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="122d5-117">Example</span></span>

 <span data-ttu-id="122d5-118">De volgende code is de implementatie van de klasse [System. Management. Automation. host. Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) die wordt gebruikt door deze hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="122d5-118">The following code is the implementation of the [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) class that is used by this host application.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Host
{
  using System;
  using System.Collections.Generic;
  using System.Globalization;
  using System.Management.Automation;
  using System.Management.Automation.Host;

  /// <summary>
  /// A sample implementation of the PSHostUserInterface abstract class for
  /// console applications. Not all members are implemented. Those that are
  /// not implemented throw a NotImplementedException exception. Members that
  /// are implemented include those that map easily to Console APIs.
  /// </summary>
  internal class MyHostUserInterface : PSHostUserInterface
  {
    /// <summary>
    /// An instance of the PSRawUserInterface class.
    /// </summary>
    private MyRawUserInterface myRawUi = new MyRawUserInterface();

    /// <summary>
    /// Gets an instance of the PSRawUserInterface class for this host
    /// application.
    /// </summary>
    public override PSHostRawUserInterface RawUI
    {
      get { return this.myRawUi; }
    }

    /// <summary>
    /// Prompts the user for input. In this example this functionality is not
    /// needed so the method throws a NotImplementException exception.
    /// </summary>
    /// <param name="caption">The caption or title of the prompt.</param>
    /// <param name="message">The text of the prompt.</param>
    /// <param name="descriptions">A collection of FieldDescription objects that
    /// describe each field of the prompt.</param>
    /// <returns>Throws a NotImplementedException exception.</returns>
    public override Dictionary<string, PSObject> Prompt(
                                                        string caption,
                                                        string message,
                                                        System.Collections.ObjectModel.Collection<FieldDescription> descriptions)
    {
       throw new NotImplementedException(
           "The method or operation is not implemented.");
    }

    /// <summary>
    /// Provides a set of choices that enable the user to choose a
    /// single option from a set of options. In this example this
    /// functionality is not needed so the method throws a
    /// NotImplementException exception.
    /// </summary>
    /// <param name="caption">Text that proceeds (a title) the choices.</param>
    /// <param name="message">A message that describes the choice.</param>
    /// <param name="choices">A collection of ChoiceDescription objects that describes
    /// each choice.</param>
    /// <param name="defaultChoice">The index of the label in the Choices parameter
    /// collection. To indicate no default choice, set to -1.</param>
    /// <returns>Throws a NotImplementedException exception.</returns>
    public override int PromptForChoice(string caption, string message, System.Collections.ObjectModel.Collection<ChoiceDescription> choices, int defaultChoice)
    {
      throw new NotImplementedException("The method or operation is not implemented.");
    }

    /// <summary>
    /// Prompts the user for credentials with a specified prompt window caption,
    /// prompt message, user name, and target name. In this example this
    /// functionality is not needed so the method throws a
    /// NotImplementException exception.
    /// </summary>
    /// <param name="caption">The caption for the message window.</param>
    /// <param name="message">The text of the message.</param>
    /// <param name="userName">The user name whose credential is to be prompted for.</param>
    /// <param name="targetName">The name of the target for which the credential is collected.</param>
    /// <returns>Throws a NotImplementedException exception.</returns>
    public override PSCredential PromptForCredential(
                                                     string caption,
                                                     string message,
                                                     string userName,
                                                     string targetName)
    {
      throw new NotImplementedException("The method or operation is not implemented.");
    }

    /// <summary>
    /// Prompts the user for credentials by using a specified prompt window caption,
    /// prompt message, user name and target name, credential types allowed to be
    /// returned, and UI behavior options. In this example this functionality
    /// is not needed so the method throws a NotImplementException exception.
    /// </summary>
    /// <param name="caption">The caption for the message window.</param>
    /// <param name="message">The text of the message.</param>
    /// <param name="userName">The user name whose credential is to be prompted for.</param>
    /// <param name="targetName">The name of the target for which the credential is collected.</param>
    /// <param name="allowedCredentialTypes">A PSCredentialTypes constant that
    /// identifies the type of credentials that can be returned.</param>
    /// <param name="options">A PSCredentialUIOptions constant that identifies the UI
    /// behavior when it gathers the credentials.</param>
    /// <returns>Throws a NotImplementedException exception.</returns>
    public override PSCredential PromptForCredential(
                                                     string caption,
                                                     string message,
                                                     string userName,
                                                     string targetName,
                                                     PSCredentialTypes allowedCredentialTypes,
                                                     PSCredentialUIOptions options)
    {
      throw new NotImplementedException("The method or operation is not implemented.");
    }

    /// <summary>
    /// Reads characters that are entered by the user until a newline
    /// (carriage return) is encountered.
    /// </summary>
    /// <returns>The characters that are entered by the user.</returns>
    public override string ReadLine()
    {
      return Console.ReadLine();
    }

    /// <summary>
    /// Reads characters entered by the user until a newline (carriage return)
    /// is encountered and returns the characters as a secure string. In this
    /// example this functionality is not needed so the method throws a
    /// NotImplementException exception.
    /// </summary>
    /// <returns>Throws a NotImplemented exception.</returns>
    public override System.Security.SecureString ReadLineAsSecureString()
    {
      throw new NotImplementedException("The method or operation is not implemented.");
    }

    /// <summary>
    /// Writes characters to the output display of the host.
    /// </summary>
    /// <param name="value">The characters to be written.</param>
    public override void Write(string value)
    {
      System.Console.Write(value);
    }

    /// <summary>
    /// Writes characters to the output display of the host and specifies the
    /// foreground and background colors of the characters. This implementation
    /// ignores the colors.
    /// </summary>
    /// <param name="foregroundColor">The color of the characters.</param>
    /// <param name="backgroundColor">The background color to use.</param>
    /// <param name="value">The characters to be written.</param>
    public override void Write(
                               ConsoleColor foregroundColor,
                               ConsoleColor backgroundColor,
                               string value)
    {
       // Colors are ignored.
       System.Console.Write(value);
    }

    /// <summary>
    /// Writes a debug message to the output display of the host.
    /// </summary>
    /// <param name="message">The debug message that is displayed.</param>
    public override void WriteDebugLine(string message)
    {
      Console.WriteLine(String.Format(
                                      CultureInfo.CurrentCulture,
                                      "DEBUG: {0}",
                                      message));
    }

    /// <summary>
    /// Writes an error message to the output display of the host.
    /// </summary>
    /// <param name="value">The error message that is displayed.</param>
    public override void WriteErrorLine(string value)
    {
      Console.WriteLine(String.Format(
                                      CultureInfo.CurrentCulture,
                                      "ERROR: {0}",
                                      value));
    }

    /// <summary>
    /// Writes a newline character (carriage return)
    /// to the output display of the host.
    /// </summary>
    public override void WriteLine()
    {
      System.Console.WriteLine();
    }

    /// <summary>
    /// Writes a line of characters to the output display of the host
    /// and appends a newline character(carriage return).
    /// </summary>
    /// <param name="value">The line to be written.</param>
    public override void WriteLine(string value)
    {
      System.Console.WriteLine(value);
    }

    /// <summary>
    /// Writes a line of characters to the output display of the host
    /// with foreground and background colors and appends a newline (carriage return).
    /// </summary>
    /// <param name="foregroundColor">The foreground color of the display. </param>
    /// <param name="backgroundColor">The background color of the display. </param>
    /// <param name="value">The line to be written.</param>
    public override void WriteLine(ConsoleColor foregroundColor, ConsoleColor backgroundColor, string value)
    {
      // Write to the output stream, ignore the colors
      System.Console.WriteLine(value);
    }

    /// <summary>
    /// Writes a progress report to the output display of the host.
    /// </summary>
    /// <param name="sourceId">Unique identifier of the source of the record. </param>
    /// <param name="record">A ProgressReport object.</param>
    public override void WriteProgress(long sourceId, ProgressRecord record)
    {
    }

    /// <summary>
    /// Writes a verbose message to the output display of the host.
    /// </summary>
    /// <param name="message">The verbose message that is displayed.</param>
    public override void WriteVerboseLine(string message)
    {
      Console.WriteLine(String.Format(CultureInfo.CurrentCulture, "VERBOSE: {0}", message));
    }

    /// <summary>
    /// Writes a warning message to the output display of the host.
    /// </summary>
    /// <param name="message">The warning message that is displayed.</param>
    public override void WriteWarningLine(string message)
    {
      Console.WriteLine(String.Format(CultureInfo.CurrentCulture, "WARNING: {0}", message));
    }
  }
}
```

## <a name="example"></a><span data-ttu-id="122d5-119">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="122d5-119">Example</span></span>

 <span data-ttu-id="122d5-120">De volgende code is de implementatie van de klasse [System. Management. Automation. host. Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface) die wordt gebruikt door deze hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="122d5-120">The following code is the implementation of the [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface) class that is used by this host application.</span></span> <span data-ttu-id="122d5-121">Deze elementen die niet zijn geïmplementeerd, genereren een uitzonde ring of retour neren niets.</span><span class="sxs-lookup"><span data-stu-id="122d5-121">Those elements that are not implemented throw an exception or return nothing.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Host
{
  using System;
  using System.Management.Automation.Host;

  /// <summary>
  /// A sample implementation of the PSHostRawUserInterface for console
  /// applications. Members of this class that easily map to the .NET
  /// console class are implemented. More complex methods are not
  /// implemented and throw a NotImplementedException exception.
  /// </summary>
  internal class MyRawUserInterface : PSHostRawUserInterface
  {
    /// <summary>
    /// Gets or sets the background color of the displayed text.
    /// This maps to the corresponding Console.Background property.
    /// </summary>
    public override ConsoleColor BackgroundColor
    {
      get { return Console.BackgroundColor; }
      set { Console.BackgroundColor = value; }
    }

    /// <summary>
    /// Gets or sets the size of the host buffer. In this example the
    /// buffer size is adapted from the Console buffer size members.
    /// </summary>
    public override Size BufferSize
    {
      get { return new Size(Console.BufferWidth, Console.BufferHeight); }
      set { Console.SetBufferSize(value.Width, value.Height); }
    }

    /// <summary>
    /// Gets or sets the cursor position. In this example this
    /// functionality is not needed so the property throws a
    /// NotImplementException exception.
    /// </summary>
    public override Coordinates CursorPosition
    {
      get { throw new NotImplementedException(
                 "The method or operation is not implemented."); }
      set { throw new NotImplementedException(
                 "The method or operation is not implemented."); }
    }

    /// <summary>
    /// Gets or sets the size of the displayed cursor. In this example
    /// the cursor size is taken directly from the Console.CursorSize
    /// property.
    /// </summary>
    public override int CursorSize
    {
      get { return Console.CursorSize; }
      set { Console.CursorSize = value; }
    }

    /// <summary>
    /// Gets or sets the foreground color of the displayed text.
    /// This maps to the corresponding Console.ForegroundColor property.
    /// </summary>
    public override ConsoleColor ForegroundColor
    {
      get { return Console.ForegroundColor; }
      set { Console.ForegroundColor = value; }
    }

    /// <summary>
    /// Gets a value indicating whether the user has pressed a key. This maps
    /// to the corresponding Console.KeyAvailable property.
    /// </summary>
    public override bool KeyAvailable
    {
      get { return Console.KeyAvailable; }
    }

    /// <summary>
    /// Gets the dimensions of the largest window that could be
    /// rendered in the current display, if the buffer was at the least
    /// that large. This example uses the Console.LargestWindowWidth and
    /// Console.LargestWindowHeight properties to determine the returned
    /// value of this property.
    /// </summary>
    public override Size MaxPhysicalWindowSize
    {
      get { return new Size(Console.LargestWindowWidth, Console.LargestWindowHeight); }
    }

    /// <summary>
    /// Gets the dimensions of the largest window size that can be
    /// displayed. This example uses the Console.LargestWindowWidth and
    /// console.LargestWindowHeight properties to determine the returned
    /// value of this property.
    /// </summary>
    public override Size MaxWindowSize
    {
      get { return new Size(Console.LargestWindowWidth, Console.LargestWindowHeight); }
    }

    /// <summary>
    /// Gets or sets the position of the displayed window. This example
    /// uses the Console window position APIs to determine the returned
    /// value of this property.
    /// </summary>
    public override Coordinates WindowPosition
    {
      get { return new Coordinates(Console.WindowLeft, Console.WindowTop); }
      set { Console.SetWindowPosition(value.X, value.Y); }
    }

    /// <summary>
    /// Gets or sets the size of the displayed window. This example
    /// uses the corresponding Console window size APIs to determine the
    /// returned value of this property.
    /// </summary>
    public override Size WindowSize
    {
      get { return new Size(Console.WindowWidth, Console.WindowHeight); }
      set { Console.SetWindowSize(value.Width, value.Height); }
    }

    /// <summary>
    /// Gets or sets the title of the displayed window. The example
    /// maps the Console.Title property to the value of this property.
    /// </summary>
    public override string WindowTitle
    {
      get { return Console.Title; }
      set { Console.Title = value; }
    }

    /// <summary>
    /// This API resets the input buffer. In this example this
    /// functionality is not needed so the method returns nothing.
    /// </summary>
    public override void FlushInputBuffer()
    {
    }

    /// <summary>
    /// This API returns a rectangular region of the screen buffer. In
    /// this example this functionality is not needed so the method throws
    /// a NotImplementException exception.
    /// </summary>
    /// <param name="rectangle">Defines the size of the rectangle.</param>
    /// <returns>Throws a NotImplementedException exception.</returns>
    public override BufferCell[,] GetBufferContents(Rectangle rectangle)
    {
      throw new NotImplementedException(
               "The method or operation is not implemented.");
    }

    /// <summary>
    /// This API reads a pressed, released, or pressed and released keystroke
    /// from the keyboard device, blocking processing until a keystroke is
    /// typed that matches the specified keystroke options. In this example
    /// this functionality is not needed so the method throws a
    /// NotImplementException exception.
    /// </summary>
    /// <param name="options">Options, such as IncludeKeyDown,  used when
    /// reading the keyboard.</param>
    /// <returns>Throws a NotImplementedException exception.</returns>
    public override KeyInfo ReadKey(ReadKeyOptions options)
    {
      throw new NotImplementedException(
                "The method or operation is not implemented.");
    }

    /// <summary>
    /// This API crops a region of the screen buffer. In this example
    /// this functionality is not needed so the method throws a
    /// NotImplementException exception.
    /// </summary>
    /// <param name="source">The region of the screen to be scrolled.</param>
    /// <param name="destination">The region of the screen to receive the
    /// source region contents.</param>
    /// <param name="clip">The region of the screen to include in the operation.</param>
    /// <param name="fill">The character and attributes to be used to fill all cell.</param>
    public override void ScrollBufferContents(Rectangle source, Coordinates destination, Rectangle clip, BufferCell fill)
    {
      throw new NotImplementedException(
                "The method or operation is not implemented.");
    }

    /// <summary>
    /// This method copies an array of buffer cells into the screen buffer
    /// at a specified location. In this example this functionality is
    /// not needed so the method throws a NotImplementedException exception.
    /// </summary>
    /// <param name="origin">The parameter is not used.</param>
    /// <param name="contents">The parameter is not used.</param>
    public override void SetBufferContents(Coordinates origin,
                                           BufferCell[,] contents)
    {
      throw new NotImplementedException(
                "The method or operation is not implemented.");
    }

    /// <summary>
    /// This method copies a given character, foreground color, and background
    /// color to a region of the screen buffer. In this example this
    /// functionality is not needed so the method throws a
    /// NotImplementException exception./// </summary>
    /// <param name="rectangle">Defines the area to be filled. </param>
    /// <param name="fill">Defines the fill character.</param>
    public override void SetBufferContents(Rectangle rectangle, BufferCell fill)
    {
      throw new NotImplementedException(
                "The method or operation is not implemented.");
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="122d5-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="122d5-122">See Also</span></span>

 [<span data-ttu-id="122d5-123">System. Management. Automation. Power shell</span><span class="sxs-lookup"><span data-stu-id="122d5-123">System.Management.Automation.Powershell</span></span>](/dotnet/api/system.management.automation.powershell)

 [<span data-ttu-id="122d5-124">System. Management. Automation. host. PSHost</span><span class="sxs-lookup"><span data-stu-id="122d5-124">System.Management.Automation.Host.PSHost</span></span>](/dotnet/api/System.Management.Automation.Host.PSHost)

 [<span data-ttu-id="122d5-125">System. Management. Automation. host. Pshostuserinterface</span><span class="sxs-lookup"><span data-stu-id="122d5-125">System.Management.Automation.Host.Pshostuserinterface</span></span>](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface)

 [<span data-ttu-id="122d5-126">System. Management. Automation. host. Pshostrawuserinterface</span><span class="sxs-lookup"><span data-stu-id="122d5-126">System.Management.Automation.Host.Pshostrawuserinterface</span></span>](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)
