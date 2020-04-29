---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: .NET-en COM-objecten maken nieuw object
ms.openlocfilehash: 6e98a159451bc7da4ba3b37eaeb813eb71590d2b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71325172"
---
# <a name="creating-net-and-com-objects-new-object"></a><span data-ttu-id="e5c44-103">.NET- en COM-objecten maken (New-Object)</span><span class="sxs-lookup"><span data-stu-id="e5c44-103">Creating .NET and COM Objects (New-Object)</span></span>

<span data-ttu-id="e5c44-104">Er zijn software onderdelen met .NET Framework en COM-interfaces waarmee u veel systeem beheer taken kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="e5c44-104">There are software components with .NET Framework and COM interfaces that enable you to perform many system administration tasks.</span></span> <span data-ttu-id="e5c44-105">Met Windows Power shell kunt u deze onderdelen gebruiken, zodat u niet beperkt bent tot de taken die kunnen worden uitgevoerd met behulp van-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e5c44-105">Windows PowerShell lets you use these components, so you are not limited to the tasks that can be performed by using cmdlets.</span></span> <span data-ttu-id="e5c44-106">Veel van de cmdlets in de eerste versie van Windows Power shell werken niet op externe computers.</span><span class="sxs-lookup"><span data-stu-id="e5c44-106">Many of the cmdlets in the initial release of Windows PowerShell do not work against remote computers.</span></span> <span data-ttu-id="e5c44-107">Er wordt gedemonstreerd hoe u deze beperking omzeilt bij het beheer van gebeurtenis logboeken met behulp van de klasse .NET Framework **System. Diagnostics. Eventlog** rechtstreeks vanuit Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="e5c44-107">We will demonstrate how to get around this limitation when managing event logs by using the .NET Framework **System.Diagnostics.EventLog** class directly from Windows PowerShell.</span></span>

## <a name="using-new-object-for-event-log-access"></a><span data-ttu-id="e5c44-108">Nieuwe objecten gebruiken voor toegang tot gebeurtenis logboeken</span><span class="sxs-lookup"><span data-stu-id="e5c44-108">Using New-Object for Event Log Access</span></span>

<span data-ttu-id="e5c44-109">De .NET Framework Class-bibliotheek bevat een klasse met de naam **System. Diagnostics. Eventlog** die kan worden gebruikt om gebeurtenis logboeken te beheren.</span><span class="sxs-lookup"><span data-stu-id="e5c44-109">The .NET Framework Class Library includes a class named **System.Diagnostics.EventLog** that can be used to manage event logs.</span></span> <span data-ttu-id="e5c44-110">U kunt een nieuw exemplaar van een .NET Framework klasse maken met behulp van de cmdlet **New-object** met de para meter **TypeName** .</span><span class="sxs-lookup"><span data-stu-id="e5c44-110">You can create a new instance of a .NET Framework class by using the **New-Object** cmdlet with the **TypeName** parameter.</span></span> <span data-ttu-id="e5c44-111">Met de volgende opdracht maakt u bijvoorbeeld een verwijzing naar gebeurtenis logboek:</span><span class="sxs-lookup"><span data-stu-id="e5c44-111">For example, the following command creates an event log reference:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

<span data-ttu-id="e5c44-112">Hoewel de opdracht een exemplaar van de klasse Event Class heeft gemaakt, bevat het exemplaar geen gegevens.</span><span class="sxs-lookup"><span data-stu-id="e5c44-112">Although the command has created an instance of the EventLog class, the instance does not include any data.</span></span> <span data-ttu-id="e5c44-113">Dat komt omdat er geen specifiek gebeurtenis logboek is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e5c44-113">That is because we did not specify a particular event log.</span></span> <span data-ttu-id="e5c44-114">Hoe krijg ik een echt gebeurtenis logboek?</span><span class="sxs-lookup"><span data-stu-id="e5c44-114">How do you get a real event log?</span></span>

### <a name="using-constructors-with-new-object"></a><span data-ttu-id="e5c44-115">Constructors gebruiken met New-object</span><span class="sxs-lookup"><span data-stu-id="e5c44-115">Using Constructors with New-Object</span></span>

<span data-ttu-id="e5c44-116">Als u naar een specifiek gebeurtenis logboek wilt verwijzen, moet u de naam van het logboek opgeven.</span><span class="sxs-lookup"><span data-stu-id="e5c44-116">To refer to a specific event log, you need to specify the name of the log.</span></span> <span data-ttu-id="e5c44-117">**New-object** heeft een **argument List** -para meter.</span><span class="sxs-lookup"><span data-stu-id="e5c44-117">**New-Object** has an **ArgumentList** parameter.</span></span> <span data-ttu-id="e5c44-118">De argumenten die u doorgeeft als waarden voor deze para meter worden gebruikt door een speciale opstart methode van het object.</span><span class="sxs-lookup"><span data-stu-id="e5c44-118">The arguments you pass as values to this parameter are used by a special startup method of the object.</span></span> <span data-ttu-id="e5c44-119">De methode wordt een *constructor* genoemd, omdat deze wordt gebruikt om het object samen te stellen.</span><span class="sxs-lookup"><span data-stu-id="e5c44-119">The method is called a *constructor* because it is used to construct the object.</span></span> <span data-ttu-id="e5c44-120">Als u bijvoorbeeld een verwijzing naar het toepassings logboek wilt ophalen, geeft u de teken reeks ' Application ' op als een argument:</span><span class="sxs-lookup"><span data-stu-id="e5c44-120">For example, to get a reference to the Application log, you specify the string 'Application' as an argument:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> <span data-ttu-id="e5c44-121">Aangezien de meeste van de .NET Framework kern klassen zich in de systeem naam ruimte bevinden, probeert Windows Power shell automatisch klassen te zoeken die u opgeeft in de naam ruimte van het systeem als er geen overeenkomst kan worden gevonden voor de door u opgegeven TypeName.</span><span class="sxs-lookup"><span data-stu-id="e5c44-121">Since most of the .NET Framework core classes are contained in the System namespace, Windows PowerShell will automatically attempt to find classes you specify in the System namespace if it cannot find a match for the typename you specify.</span></span> <span data-ttu-id="e5c44-122">Dit betekent dat u Diagnostische gegevens. EventLog in plaats van System. Diagnostics. EventLog kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="e5c44-122">This means that you can specify Diagnostics.EventLog instead of System.Diagnostics.EventLog.</span></span>

### <a name="storing-objects-in-variables"></a><span data-ttu-id="e5c44-123">Objecten in variabelen opslaan</span><span class="sxs-lookup"><span data-stu-id="e5c44-123">Storing Objects in Variables</span></span>

<span data-ttu-id="e5c44-124">Mogelijk wilt u een verwijzing naar een object opslaan, zodat u deze in de huidige shell kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e5c44-124">You might want to store a reference to an object, so you can use it in the current shell.</span></span> <span data-ttu-id="e5c44-125">Hoewel u met Windows Power shell veel werk met pijp lijnen kunt maken, is het niet meer nodig om variabelen op te slaan naar objecten in variabelen, waardoor het handiger is om deze objecten te manipuleren.</span><span class="sxs-lookup"><span data-stu-id="e5c44-125">Although Windows PowerShell lets you do a lot of work with pipelines, lessening the need for variables, sometimes storing references to objects in variables makes it more convenient to manipulate those objects.</span></span>

<span data-ttu-id="e5c44-126">Met Windows Power shell kunt u variabelen maken die hoofd objecten worden genoemd.</span><span class="sxs-lookup"><span data-stu-id="e5c44-126">Windows PowerShell lets you create variables that are essentially named objects.</span></span> <span data-ttu-id="e5c44-127">De uitvoer van een geldige Windows Power shell-opdracht kan worden opgeslagen in een variabele.</span><span class="sxs-lookup"><span data-stu-id="e5c44-127">The output from any valid Windows PowerShell command can be stored in a variable.</span></span> <span data-ttu-id="e5c44-128">Namen van variabelen beginnen altijd met $.</span><span class="sxs-lookup"><span data-stu-id="e5c44-128">Variable names always begin with $.</span></span> <span data-ttu-id="e5c44-129">Als u de verwijzing naar het toepassings logboek wilt opslaan in een variabele met de naam $AppLog, typt u de naam van de variabele, gevolgd door een gelijkteken en typt u vervolgens de opdracht die wordt gebruikt om het toepassings logboek object te maken:</span><span class="sxs-lookup"><span data-stu-id="e5c44-129">If you want to store the Application log reference in a variable named $AppLog, type the name of the variable, followed by an equal sign and then type the command used to create the Application log object:</span></span>

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

<span data-ttu-id="e5c44-130">Als u vervolgens $AppLog typt, ziet u dat deze het toepassings logboek bevat:</span><span class="sxs-lookup"><span data-stu-id="e5c44-130">If you then type $AppLog, you can see that it contains the Application log:</span></span>

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

### <a name="accessing-a-remote-event-log-with-new-object"></a><span data-ttu-id="e5c44-131">Toegang tot een extern gebeurtenis logboek met New-object</span><span class="sxs-lookup"><span data-stu-id="e5c44-131">Accessing a Remote Event Log with New-Object</span></span>

<span data-ttu-id="e5c44-132">De opdrachten die in de voor gaande sectie worden gebruikt, zijn gericht op de lokale computer. de cmdlet **get-eventlog** kan dat doen.</span><span class="sxs-lookup"><span data-stu-id="e5c44-132">The commands used in the preceding section target the local computer; the **Get-EventLog** cmdlet can do that.</span></span> <span data-ttu-id="e5c44-133">Als u toegang wilt krijgen tot het toepassings logboek op een externe computer, moet u de naam van het logboek en een computer naam (of IP-adres) als argumenten opgeven.</span><span class="sxs-lookup"><span data-stu-id="e5c44-133">To access the Application log on a remote computer, you must supply both the log name and a computer name (or IP address) as arguments.</span></span>

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

<span data-ttu-id="e5c44-134">Nu hebben we een verwijzing naar een gebeurtenis logboek dat is opgeslagen in de variabele $RemoteAppLog, welke taken kunnen we uitvoeren?</span><span class="sxs-lookup"><span data-stu-id="e5c44-134">Now that we have a reference to an event log stored in the $RemoteAppLog variable, what tasks can we perform on it?</span></span>

### <a name="clearing-an-event-log-with-object-methods"></a><span data-ttu-id="e5c44-135">Een gebeurtenis logboek wissen met object methoden</span><span class="sxs-lookup"><span data-stu-id="e5c44-135">Clearing an Event Log with Object Methods</span></span>

<span data-ttu-id="e5c44-136">Objecten bevatten vaak methoden die kunnen worden aangeroepen om taken uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="e5c44-136">Objects often have methods that can be called to perform tasks.</span></span> <span data-ttu-id="e5c44-137">U kunt **Get-member** gebruiken om de methoden weer te geven die zijn gekoppeld aan een object.</span><span class="sxs-lookup"><span data-stu-id="e5c44-137">You can use **Get-Member** to display the methods associated with an object.</span></span> <span data-ttu-id="e5c44-138">De volgende opdracht en de geselecteerde uitvoer tonen een aantal methoden van de klasse Event Class:</span><span class="sxs-lookup"><span data-stu-id="e5c44-138">The following command and selected output show some the methods of the EventLog class:</span></span>

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

<span data-ttu-id="e5c44-139">De methode **Clear ()** kan worden gebruikt om het gebeurtenis logboek te wissen.</span><span class="sxs-lookup"><span data-stu-id="e5c44-139">The **Clear()** method can be used to clear the event log.</span></span> <span data-ttu-id="e5c44-140">Wanneer u een methode aanroept, moet u altijd de naam van de methode door haakjes volgen, zelfs als de methode geen argumenten vereist.</span><span class="sxs-lookup"><span data-stu-id="e5c44-140">When calling a method, you must always follow the method name by parentheses, even if the method does not require arguments.</span></span> <span data-ttu-id="e5c44-141">Hiermee kan Windows Power shell onderscheid maken tussen de methode en een mogelijke eigenschap met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="e5c44-141">This lets Windows PowerShell distinguish between the method and a potential property with the same name.</span></span> <span data-ttu-id="e5c44-142">Typ het volgende om de methode **Clear** aan te roepen:</span><span class="sxs-lookup"><span data-stu-id="e5c44-142">Type the following to call the **Clear** method:</span></span>

```
PS> $RemoteAppLog.Clear()
```

<span data-ttu-id="e5c44-143">Typ het volgende om het logboek weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e5c44-143">Type the following to display the log.</span></span> <span data-ttu-id="e5c44-144">U ziet dat het gebeurtenis logboek is gewist en nu 0 vermeldingen bevat in plaats van 262:</span><span class="sxs-lookup"><span data-stu-id="e5c44-144">You will see that the event log was cleared, and now has 0 entries instead of 262:</span></span>

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

## <a name="creating-com-objects-with-new-object"></a><span data-ttu-id="e5c44-145">COM-objecten maken met New-object</span><span class="sxs-lookup"><span data-stu-id="e5c44-145">Creating COM Objects with New-Object</span></span>
<span data-ttu-id="e5c44-146">U kunt **New-object** gebruiken om te werken met component object model-onderdelen (com).</span><span class="sxs-lookup"><span data-stu-id="e5c44-146">You can use **New-Object** to work with Component Object Model (COM) components.</span></span> <span data-ttu-id="e5c44-147">Onderdelen variëren van de verschillende bibliotheken die zijn opgenomen in Windows Script Host (WSH) tot ActiveX-toepassingen, zoals Internet Explorer, die op de meeste systemen zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e5c44-147">Components range from the various libraries included with Windows Script Host (WSH) to ActiveX applications such as Internet Explorer that are installed on most systems.</span></span>

<span data-ttu-id="e5c44-148">**New-object** maakt gebruik van .NET Framework runtime-aanroep bare wrappers om COM-objecten te maken, zodat deze dezelfde beperkingen heeft als .NET Framework bij het aanroepen van COM-objecten.</span><span class="sxs-lookup"><span data-stu-id="e5c44-148">**New-Object** uses .NET Framework Runtime-Callable Wrappers to create COM objects, so it has the same limitations that .NET Framework does when calling COM objects.</span></span> <span data-ttu-id="e5c44-149">Als u een COM-object wilt maken, moet u de para meter **ComObject** opgeven met de programmatische id of *ProgID* van de COM-klasse die u wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e5c44-149">To create a COM object, you need to specify the **ComObject** parameter with the Programmatic Identifier or *ProgId* of the COM class you want to use.</span></span> <span data-ttu-id="e5c44-150">Een volledige bespreking van de beperkingen van het COM-gebruik en het bepalen van de beschik bare Progid's op een systeem valt buiten het bereik van deze gebruikers handleiding, maar de meeste bekende objecten van omgevingen zoals WSH kunnen worden gebruikt in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="e5c44-150">A complete discussion of the limitations of COM use and determining what ProgIds are available on a system is beyond the scope of this user's guide, but most well-known objects from environments such as WSH can be used within Windows PowerShell.</span></span>

<span data-ttu-id="e5c44-151">U kunt de WSH-objecten maken door deze progid's op te geven: **WScript. shell**, **WScript. Network**, **Scripting. Dictionary**en **Scripting. File System object**.</span><span class="sxs-lookup"><span data-stu-id="e5c44-151">You can create the WSH objects by specifying these progids: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, and **Scripting.FileSystemObject**.</span></span> <span data-ttu-id="e5c44-152">Met de volgende opdrachten maakt u deze objecten:</span><span class="sxs-lookup"><span data-stu-id="e5c44-152">The following commands create these objects:</span></span>

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

<span data-ttu-id="e5c44-153">Hoewel de meeste functies van deze klassen op andere manieren beschikbaar worden gesteld in Windows Power shell, zijn een aantal taken, zoals het maken van snelkoppelingen, nog eenvoudiger te gebruiken met de WSH-klassen.</span><span class="sxs-lookup"><span data-stu-id="e5c44-153">Although most of the functionality of these classes is made available in other ways in Windows PowerShell, a few tasks such as shortcut creation are still easier to do using the WSH classes.</span></span>

## <a name="creating-a-desktop-shortcut-with-wscriptshell"></a><span data-ttu-id="e5c44-154">Een snelkoppeling op het bureau blad maken met WScript. shell</span><span class="sxs-lookup"><span data-stu-id="e5c44-154">Creating a Desktop Shortcut with WScript.Shell</span></span>

<span data-ttu-id="e5c44-155">Een taak die snel kan worden uitgevoerd met een COM-object, is het maken van een snelkoppeling.</span><span class="sxs-lookup"><span data-stu-id="e5c44-155">One task that can be performed quickly with a COM object is creating a shortcut.</span></span> <span data-ttu-id="e5c44-156">Stel dat u een snelkoppeling op het bureau blad wilt maken die is gekoppeld aan de basismap voor Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="e5c44-156">Suppose you want to create a shortcut on your desktop that links to the home folder for Windows PowerShell.</span></span> <span data-ttu-id="e5c44-157">Eerst moet u een verwijzing naar **WScript. shell**maken, die we in een variabele met de naam **$WshShell**opslaan:</span><span class="sxs-lookup"><span data-stu-id="e5c44-157">You first need to create a reference to **WScript.Shell**, which we will store in a variable named **$WshShell**:</span></span>

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

<span data-ttu-id="e5c44-158">Get-member werkt met COM-objecten, zodat u de leden van het object kunt verkennen door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="e5c44-158">Get-Member works with COM objects, so you can explore the members of the object by typing:</span></span>

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

<span data-ttu-id="e5c44-159">**Get-member** heeft een optionele **input object** -para meter die u kunt gebruiken in plaats van sluizen om invoer te leveren voor **Get-member**.</span><span class="sxs-lookup"><span data-stu-id="e5c44-159">**Get-Member** has an optional **InputObject** parameter you can use instead of piping to provide input to **Get-Member**.</span></span> <span data-ttu-id="e5c44-160">U krijgt dezelfde uitvoer zoals hierboven wordt weer gegeven als u in plaats daarvan de opdracht **Get-member-input object $WshShell**hebt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e5c44-160">You would get the same output as shown above if you instead used the command **Get-Member -InputObject $WshShell**.</span></span> <span data-ttu-id="e5c44-161">Als u **input object**gebruikt, wordt het argument als één item beschouwd.</span><span class="sxs-lookup"><span data-stu-id="e5c44-161">If you use **InputObject**, it treats its argument as a single item.</span></span> <span data-ttu-id="e5c44-162">Dit betekent dat als u meerdere objecten in een variabele hebt, **Get-member** ze als een matrix met objecten behandelt.</span><span class="sxs-lookup"><span data-stu-id="e5c44-162">This means that if you have several objects in a variable, **Get-Member** treats them as an array of objects.</span></span> <span data-ttu-id="e5c44-163">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="e5c44-163">For example:</span></span>

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

<span data-ttu-id="e5c44-164">De **WScript. shell CreateShortcut** -methode accepteert één argument, het pad naar het snelkoppelings bestand dat moet worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e5c44-164">The **WScript.Shell CreateShortcut** method accepts a single argument, the path to the shortcut file to create.</span></span> <span data-ttu-id="e5c44-165">We kunnen het volledige pad naar het bureau blad typen, maar er is een eenvoudiger manier.</span><span class="sxs-lookup"><span data-stu-id="e5c44-165">We could type in the full path to the desktop, but there is an easier way.</span></span> <span data-ttu-id="e5c44-166">Het bureau blad wordt gewoonlijk vertegenwoordigd door een map met de naam bureau blad in de basismap van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="e5c44-166">The desktop is normally represented by a folder named Desktop inside the home folder of the current user.</span></span> <span data-ttu-id="e5c44-167">Windows Power Shell heeft een variabele **$Home** die het pad naar deze map bevat.</span><span class="sxs-lookup"><span data-stu-id="e5c44-167">Windows PowerShell has a variable **$Home** that contains the path to this folder.</span></span> <span data-ttu-id="e5c44-168">We kunnen het pad naar de basismap opgeven met behulp van deze variabele, en vervolgens de naam van de map Bureau blad en de naam voor de snelkoppeling toevoegen door te typen:</span><span class="sxs-lookup"><span data-stu-id="e5c44-168">We can specify the path to the home folder by using this variable, and then add the name of the Desktop folder and the name for the shortcut to create by typing:</span></span>

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

<span data-ttu-id="e5c44-169">Wanneer u iets gebruikt dat lijkt op een naam van een variabele binnen dubbele aanhalings tekens, probeert Windows Power shell een overeenkomende waarde te vervangen.</span><span class="sxs-lookup"><span data-stu-id="e5c44-169">When you use something that looks like a variable name inside double-quotes, Windows PowerShell tries to substitute a matching value.</span></span> <span data-ttu-id="e5c44-170">Als u gebruikmaakt van enkele aanhalings tekens, wordt de waarde van de variabele niet vervangen door Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="e5c44-170">If you use single-quotes, Windows PowerShell does not try to substitute the variable value.</span></span> <span data-ttu-id="e5c44-171">Typ bijvoorbeeld de volgende opdrachten:</span><span class="sxs-lookup"><span data-stu-id="e5c44-171">For example, try typing the following commands:</span></span>

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

<span data-ttu-id="e5c44-172">We hebben nu een variabele met de naam **$lnk** die een nieuwe snelkoppeling referentie bevat.</span><span class="sxs-lookup"><span data-stu-id="e5c44-172">We now have a variable named **$lnk** that contains a new shortcut reference.</span></span> <span data-ttu-id="e5c44-173">Als u de leden wilt zien, kunt u deze door sluizen naar **Get-lid**.</span><span class="sxs-lookup"><span data-stu-id="e5c44-173">If you want to see its members, you can pipe it to **Get-Member**.</span></span> <span data-ttu-id="e5c44-174">De onderstaande uitvoer toont de leden die we nodig hebben om het maken van de snelkoppeling te volt ooien:</span><span class="sxs-lookup"><span data-stu-id="e5c44-174">The output below shows the members we need to use to finish creating our shortcut:</span></span>

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

<span data-ttu-id="e5c44-175">We moeten het **TargetPath**opgeven, de toepassingsmap voor Windows Power shell, en vervolgens de snelkoppeling opslaan **$lnk** door de methode **Save** aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="e5c44-175">We need to specify the **TargetPath**, which is the application folder for Windows PowerShell, and then save the shortcut **$lnk** by calling the **Save** method.</span></span> <span data-ttu-id="e5c44-176">Het pad naar de map van de Windows Power shell-toepassing wordt opgeslagen in de variabele **$PSHome**, dus we kunnen dit doen door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="e5c44-176">The Windows PowerShell application folder path is stored in the variable **$PSHome**, so we can do this by typing:</span></span>

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

## <a name="using-internet-explorer-from-windows-powershell"></a><span data-ttu-id="e5c44-177">Internet Explorer gebruiken vanuit Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="e5c44-177">Using Internet Explorer from Windows PowerShell</span></span>

<span data-ttu-id="e5c44-178">Veel toepassingen (met inbegrip van de Microsoft Office-familie van toepassingen en Internet Explorer) kunnen worden geautomatiseerd met behulp van COM.</span><span class="sxs-lookup"><span data-stu-id="e5c44-178">Many applications (including the Microsoft Office family of applications and Internet Explorer) can be automated by using COM.</span></span> <span data-ttu-id="e5c44-179">Internet Explorer illustreert enkele van de typische technieken en problemen die betrekking hebben op het werken met op COM gebaseerde toepassingen.</span><span class="sxs-lookup"><span data-stu-id="e5c44-179">Internet Explorer illustrates some of the typical techniques and issues involved in working with COM-based applications.</span></span>

<span data-ttu-id="e5c44-180">U maakt een Internet Explorer-exemplaar door de Internet Explorer ProgId, **InternetExplorer. toepassing**, op te geven:</span><span class="sxs-lookup"><span data-stu-id="e5c44-180">You create an Internet Explorer instance by specifying the Internet Explorer ProgId, **InternetExplorer.Application**:</span></span>

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

<span data-ttu-id="e5c44-181">Met deze opdracht start u Internet Explorer, maar wordt het niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e5c44-181">This command starts Internet Explorer, but does not make it visible.</span></span> <span data-ttu-id="e5c44-182">Als u Get-process typt, ziet u dat er een proces met de naam Iexplore wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e5c44-182">If you type Get-Process, you can see that a process named iexplore is running.</span></span> <span data-ttu-id="e5c44-183">Als u Windows Power shell afsluit, wordt het proces nog steeds uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e5c44-183">In fact, if you exit Windows PowerShell, the process will continue to run.</span></span> <span data-ttu-id="e5c44-184">U moet de computer opnieuw opstarten of een hulp programma als taak beheer gebruiken om het Iexplore-proces te beëindigen.</span><span class="sxs-lookup"><span data-stu-id="e5c44-184">You must reboot the computer or use a tool like Task Manager to end the iexplore process.</span></span>

> [!NOTE]
> <span data-ttu-id="e5c44-185">COM-objecten die als afzonderlijke processen worden gestart, ook wel *ActiveX-uitvoer bare bestanden*genoemd, kunnen een gebruikers interface venster niet weer geven wanneer ze worden opgestart.</span><span class="sxs-lookup"><span data-stu-id="e5c44-185">COM objects that start as separate processes, commonly called *ActiveX executables*, may or may not display a user interface window when they start up.</span></span> <span data-ttu-id="e5c44-186">Als ze een venster maken, maar dit niet zichtbaar maken, zoals Internet Explorer, wordt de focus meestal verplaatst naar het Windows-bureau blad en moet u het venster zichtbaar maken om ermee te communiceren.</span><span class="sxs-lookup"><span data-stu-id="e5c44-186">If they create a window but do not make it visible, like Internet Explorer, the focus will generally move to the Windows desktop and you must make the window visible to interact with it.</span></span>

<span data-ttu-id="e5c44-187">Door $ie te typen **| Get-lid**, u kunt eigenschappen en methoden voor Internet Explorer weer geven.</span><span class="sxs-lookup"><span data-stu-id="e5c44-187">By typing **$ie | Get-Member**, you can view properties and methods for Internet Explorer.</span></span> <span data-ttu-id="e5c44-188">Als u het venster Internet Explorer wilt weer geven, stelt u de eigenschap Visible in op $true door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="e5c44-188">To see the Internet Explorer window, set the Visible property to $true by typing:</span></span>

```powershell
$ie.Visible = $true
```

<span data-ttu-id="e5c44-189">U kunt vervolgens naar een specifiek webadres navigeren met behulp van de methode Navigate:</span><span class="sxs-lookup"><span data-stu-id="e5c44-189">You can then navigate to a specific Web address by using the Navigate method:</span></span>

```powershell
$ie.Navigate("https://devblogs.microsoft.com/scripting/")
```

<span data-ttu-id="e5c44-190">Met andere leden van het object model van Internet Explorer kunt u tekst inhoud ophalen van de webpagina.</span><span class="sxs-lookup"><span data-stu-id="e5c44-190">Using other members of the Internet Explorer object model, it is possible to retrieve text content from the Web page.</span></span> <span data-ttu-id="e5c44-191">Met de volgende opdracht wordt de HTML-tekst in de hoofd tekst van de huidige webpagina weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="e5c44-191">The following command will display the HTML text in the body of the current Web page:</span></span>

```powershell
$ie.Document.Body.InnerText
```

<span data-ttu-id="e5c44-192">Als u Internet Explorer wilt sluiten in Power shell, roept u de methode Quit () aan:</span><span class="sxs-lookup"><span data-stu-id="e5c44-192">To close Internet Explorer from within PowerShell, call its Quit() method:</span></span>

```powershell
$ie.Quit()
```

<span data-ttu-id="e5c44-193">Hiermee wordt het sluiten afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="e5c44-193">This will force it to close.</span></span> <span data-ttu-id="e5c44-194">De variabele $ie heeft geen geldige verwijzing meer, zelfs als deze nog steeds een COM-object is.</span><span class="sxs-lookup"><span data-stu-id="e5c44-194">The $ie variable no longer contains a valid reference even though it still appears to be a COM object.</span></span> <span data-ttu-id="e5c44-195">Als u dit probeert te gebruiken, wordt er een automatiserings fout weer geven:</span><span class="sxs-lookup"><span data-stu-id="e5c44-195">If you attempt to use it, you will get an automation error:</span></span>

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

<span data-ttu-id="e5c44-196">U kunt de resterende verwijzing verwijderen met een opdracht als $ie = $null of de variabele volledig verwijderen door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="e5c44-196">You can either remove the remaining reference with a command like $ie = $null, or completely remove the variable by typing:</span></span>

```powershell
Remove-Variable ie
```

> [!NOTE]
> <span data-ttu-id="e5c44-197">Er is geen algemene standaard voor of ActiveX-uitvoer bare bestanden worden afgesloten of blijven worden uitgevoerd wanneer u een verwijzing naar een verwijdert.</span><span class="sxs-lookup"><span data-stu-id="e5c44-197">There is no common standard for whether ActiveX executables exit or continue to run when you remove a reference to one.</span></span> <span data-ttu-id="e5c44-198">Afhankelijk van de omstandigheden zoals of de toepassing zichtbaar is, of er een bewerkte document wordt uitgevoerd en zelfs of Windows Power shell nog steeds wordt uitgevoerd, wordt de toepassing mogelijk niet afgesloten.</span><span class="sxs-lookup"><span data-stu-id="e5c44-198">Depending on circumstances such as whether the application is visible, whether an edited document is running in it, and even whether Windows PowerShell is still running, the application may or may not exit.</span></span> <span data-ttu-id="e5c44-199">Daarom moet u het beëindigings gedrag testen voor elk ActiveX-uitvoerbaar bestand dat u wilt gebruiken in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="e5c44-199">For this reason, you should test termination behavior for each ActiveX executable you want to use in Windows PowerShell.</span></span>

## <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a><span data-ttu-id="e5c44-200">Waarschuwingen ontvangen over door .NET Framework verpakte COM-objecten</span><span class="sxs-lookup"><span data-stu-id="e5c44-200">Getting Warnings About .NET Framework-Wrapped COM Objects</span></span>

<span data-ttu-id="e5c44-201">In sommige gevallen kan een COM-object zijn gekoppeld aan een .NET Framework *runtime-aanroep bare wrapper* of RCW. dit wordt gebruikt door **Nieuw-object**.</span><span class="sxs-lookup"><span data-stu-id="e5c44-201">In some cases, a COM object might have an associated .NET Framework *Runtime-Callable Wrapper* or RCW, and this will be used by **New-Object**.</span></span> <span data-ttu-id="e5c44-202">Aangezien het gedrag van de RCW kan afwijken van het gedrag van het normale COM-object, heeft **New-object** een **strikte** para meter om u te waarschuwen over RCW-toegang.</span><span class="sxs-lookup"><span data-stu-id="e5c44-202">Since the behavior of the RCW may be different from the behavior of the normal COM object, **New-Object** has a **Strict** parameter to warn you about RCW access.</span></span> <span data-ttu-id="e5c44-203">Als u de **strikte** para meter opgeeft en vervolgens een COM-object maakt dat gebruikmaakt van een RCW, wordt er een waarschuwings bericht weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="e5c44-203">If you specify the **Strict** parameter and then create a COM object that uses an RCW, you get a warning message:</span></span>

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

<span data-ttu-id="e5c44-204">Hoewel het object nog wordt gemaakt, wordt u gewaarschuwd dat het geen standaard-COM-object is.</span><span class="sxs-lookup"><span data-stu-id="e5c44-204">Although the object is still created, you are warned that it is not a standard COM object.</span></span>
