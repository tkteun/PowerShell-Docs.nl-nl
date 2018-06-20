---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: .NET- en COM-objecten Nieuw Object maken
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: 1ffd8d4afa419ec0c24321e44aa4a2f41a9bee44
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953385"
---
# <a name="creating-net-and-com-objects-new-object"></a><span data-ttu-id="bfdc1-103">.NET- en COM-objecten (Nieuw Object) maken</span><span class="sxs-lookup"><span data-stu-id="bfdc1-103">Creating .NET and COM Objects (New-Object)</span></span>

<span data-ttu-id="bfdc1-104">Er zijn softwareonderdelen met .NET Framework en COM-interfaces waarmee u veel system-beheertaken uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-104">There are software components with .NET Framework and COM interfaces that enable you to perform many system administration tasks.</span></span> <span data-ttu-id="bfdc1-105">Windows PowerShell kunt u deze onderdelen te gebruiken zodat u niet beperkt tot de taken die kunnen worden uitgevoerd zijn met behulp van cmdlets.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-105">Windows PowerShell lets you use these components, so you are not limited to the tasks that can be performed by using cmdlets.</span></span> <span data-ttu-id="bfdc1-106">Veel van de cmdlets in de initiële versie van Windows PowerShell werkt niet op externe computers.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-106">Many of the cmdlets in the initial release of Windows PowerShell do not work against remote computers.</span></span> <span data-ttu-id="bfdc1-107">Wordt gedemonstreerd hoe u deze beperking omzeilen bij het beheren van gebeurtenislogboeken met behulp van .NET Framework **System.Diagnostics.EventLog** klasse rechtstreeks vanuit Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-107">We will demonstrate how to get around this limitation when managing event logs by using the .NET Framework **System.Diagnostics.EventLog** class directly from Windows PowerShell.</span></span>

### <a name="using-new-object-for-event-log-access"></a><span data-ttu-id="bfdc1-108">Nieuw Object gebruiken voor gebeurtenislogboek-toegang</span><span class="sxs-lookup"><span data-stu-id="bfdc1-108">Using New-Object for Event Log Access</span></span>

<span data-ttu-id="bfdc1-109">.NET Framework Class Library bevat een klasse met de naam **System.Diagnostics.EventLog** die kunnen worden gebruikt voor het beheren van gebeurtenislogboeken.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-109">The .NET Framework Class Library includes a class named **System.Diagnostics.EventLog** that can be used to manage event logs.</span></span> <span data-ttu-id="bfdc1-110">U kunt een nieuw exemplaar van een .NET Framework-klasse maken met behulp van de **New-Object** cmdlet uit met de **TypeName** parameter.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-110">You can create a new instance of a .NET Framework class by using the **New-Object** cmdlet with the **TypeName** parameter.</span></span> <span data-ttu-id="bfdc1-111">De volgende opdracht maakt bijvoorbeeld een verwijzing naar een gebeurtenislogboek:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-111">For example, the following command creates an event log reference:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

<span data-ttu-id="bfdc1-112">Hoewel de opdracht een instantie van de klasse EventLog gemaakt heeft, bevatten het exemplaar geen gegevens.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-112">Although the command has created an instance of the EventLog class, the instance does not include any data.</span></span> <span data-ttu-id="bfdc1-113">Dat komt doordat er een bepaald gebeurtenislogboek niet is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-113">That is because we did not specify a particular event log.</span></span> <span data-ttu-id="bfdc1-114">Hoe krijg ik een echte gebeurtenislogboek?</span><span class="sxs-lookup"><span data-stu-id="bfdc1-114">How do you get a real event log?</span></span>

#### <a name="using-constructors-with-new-object"></a><span data-ttu-id="bfdc1-115">Met behulp van Constructors met nieuw Object</span><span class="sxs-lookup"><span data-stu-id="bfdc1-115">Using Constructors with New-Object</span></span>

<span data-ttu-id="bfdc1-116">Om te verwijzen naar een specifiek gebeurtenislogboek, moet u de naam van het logboek opgeven.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-116">To refer to a specific event log, you need to specify the name of the log.</span></span> <span data-ttu-id="bfdc1-117">**Nieuw Object** heeft een **ArgumentList** parameter.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-117">**New-Object** has an **ArgumentList** parameter.</span></span> <span data-ttu-id="bfdc1-118">De argumenten die u aan deze parameter als waarden doorgeven worden gebruikt door een speciale opstartmethode van het object.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-118">The arguments you pass as values to this parameter are used by a special startup method of the object.</span></span> <span data-ttu-id="bfdc1-119">De methode wordt aangeroepen een *constructor* omdat deze wordt gebruikt om het object te maken.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-119">The method is called a *constructor* because it is used to construct the object.</span></span> <span data-ttu-id="bfdc1-120">Bijvoorbeeld als u een verwijzing naar het toepassingslogboek, geeft u de tekenreeks 'Toepassing' als een argument:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-120">For example, to get a reference to the Application log, you specify the string 'Application' as an argument:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> <span data-ttu-id="bfdc1-121">Aangezien de meeste van de .NET Framework core-klassen zijn opgenomen in de naamruimte System, probeert Windows PowerShell automatisch te vinden van de klassen die u in de naamruimte System opgeeft als er een overeenkomst voor de typename die u opgeeft geen gevonden.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-121">Since most of the .NET Framework core classes are contained in the System namespace, Windows PowerShell will automatically attempt to find classes you specify in the System namespace if it cannot find a match for the typename you specify.</span></span> <span data-ttu-id="bfdc1-122">Dit betekent dat u Diagnostics.EventLog in plaats van System.Diagnostics.EventLog kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-122">This means that you can specify Diagnostics.EventLog instead of System.Diagnostics.EventLog.</span></span>

#### <a name="storing-objects-in-variables"></a><span data-ttu-id="bfdc1-123">Opslaan van objecten in variabelen</span><span class="sxs-lookup"><span data-stu-id="bfdc1-123">Storing Objects in Variables</span></span>

<span data-ttu-id="bfdc1-124">Het is raadzaam voor het opslaan van een verwijzing naar een object, zodat u deze in de huidige shell gebruiken kunt.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-124">You might want to store a reference to an object, so you can use it in the current shell.</span></span> <span data-ttu-id="bfdc1-125">Hoewel Windows PowerShell u veel work met pijplijnen kunt, vermindering van de noodzaak van variabelen, maakt soms verwijzingen naar objecten opslaan in variabelen het eenvoudiger om deze objecten te bewerken.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-125">Although Windows PowerShell lets you do a lot of work with pipelines, lessening the need for variables, sometimes storing references to objects in variables makes it more convenient to manipulate those objects.</span></span>

<span data-ttu-id="bfdc1-126">Windows PowerShell kunt u variabelen maken die in principe zijn benoemde objecten.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-126">Windows PowerShell lets you create variables that are essentially named objects.</span></span> <span data-ttu-id="bfdc1-127">De uitvoer van een geldige Windows PowerShell-opdracht kan worden opgeslagen in een variabele.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-127">The output from any valid Windows PowerShell command can be stored in a variable.</span></span> <span data-ttu-id="bfdc1-128">Namen van variabelen beginnen altijd met $.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-128">Variable names always begin with $.</span></span> <span data-ttu-id="bfdc1-129">Als u wilt de verwijzing van het logboek Application opslaat in een variabele met de naam $AppLog, typ de naam van wordt de variabele, gevolgd door een gelijkteken en typ de opdracht die wordt gebruikt voor het maken van het toepassingsobject logboek:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-129">If you want to store the Application log reference in a variable named $AppLog, type the name of the variable, followed by an equal sign and then type the command used to create the Application log object:</span></span>

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

<span data-ttu-id="bfdc1-130">Als u vervolgens $AppLog typt, ziet u dat deze het toepassingslogboek bevat:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-130">If you then type $AppLog, you can see that it contains the Application log:</span></span>

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### <a name="accessing-a-remote-event-log-with-new-object"></a><span data-ttu-id="bfdc1-131">Toegang tot een externe Nieuw Object-gebeurtenislogboek</span><span class="sxs-lookup"><span data-stu-id="bfdc1-131">Accessing a Remote Event Log with New-Object</span></span>

<span data-ttu-id="bfdc1-132">De opdrachten in de vorige sectie gericht op de lokale computer; de **Get EventLog** cmdlet kunt dit doen.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-132">The commands used in the preceding section target the local computer; the **Get-EventLog** cmdlet can do that.</span></span> <span data-ttu-id="bfdc1-133">Voor toegang tot het toepassingslogboek op een externe computer, moet u zowel de naam van het logboek en een computernaam (of IP-adres) opgeven als argumenten.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-133">To access the Application log on a remote computer, you must supply both the log name and a computer name (or IP address) as arguments.</span></span>

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

<span data-ttu-id="bfdc1-134">Nu dat we een verwijzing naar een gebeurtenislogboek opgeslagen in de variabele $RemoteAppLog hebben, welke taken kunnen we op uitvoeren?</span><span class="sxs-lookup"><span data-stu-id="bfdc1-134">Now that we have a reference to an event log stored in the $RemoteAppLog variable, what tasks can we perform on it?</span></span>

#### <a name="clearing-an-event-log-with-object-methods"></a><span data-ttu-id="bfdc1-135">Wissen van een gebeurtenislogboek met objectmethoden</span><span class="sxs-lookup"><span data-stu-id="bfdc1-135">Clearing an Event Log with Object Methods</span></span>

<span data-ttu-id="bfdc1-136">Objecten hebben vaak methoden die kunnen worden aangeroepen als taken wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-136">Objects often have methods that can be called to perform tasks.</span></span> <span data-ttu-id="bfdc1-137">U kunt **Get-lid** om de methoden die zijn gekoppeld aan een object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-137">You can use **Get-Member** to display the methods associated with an object.</span></span> <span data-ttu-id="bfdc1-138">De volgende opdracht en de geselecteerde uitvoer zijn voorbeelden de methoden van de EventLog-klasse:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-138">The following command and selected output show some the methods of the EventLog class:</span></span>

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

<span data-ttu-id="bfdc1-139">De **Clear()** methode kan worden gebruikt om te wissen van het gebeurtenislogboek.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-139">The **Clear()** method can be used to clear the event log.</span></span> <span data-ttu-id="bfdc1-140">Wanneer u een methode aanroept, moet u altijd de methodenaam volgen door haakjes, zelfs als de methode geen argumenten vereist.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-140">When calling a method, you must always follow the method name by parentheses, even if the method does not require arguments.</span></span> <span data-ttu-id="bfdc1-141">Hiermee kunt Windows PowerShell onderscheid maken tussen de methode en een mogelijke eigenschap met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-141">This lets Windows PowerShell distinguish between the method and a potential property with the same name.</span></span> <span data-ttu-id="bfdc1-142">Typ het volgende aan te roepen de **wissen** methode:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-142">Type the following to call the **Clear** method:</span></span>

```
PS> $RemoteAppLog.Clear()
```

<span data-ttu-id="bfdc1-143">Typ het volgende om het logboek weer te geven.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-143">Type the following to display the log.</span></span> <span data-ttu-id="bfdc1-144">U ziet dat het gebeurtenislogboek is uitgeschakeld en nu 0 vermeldingen in plaats van 262 is:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-144">You will see that the event log was cleared, and now has 0 entries instead of 262:</span></span>

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### <a name="creating-com-objects-with-new-object"></a><span data-ttu-id="bfdc1-145">COM-objecten maken met een nieuw Object</span><span class="sxs-lookup"><span data-stu-id="bfdc1-145">Creating COM Objects with New-Object</span></span>
<span data-ttu-id="bfdc1-146">U kunt **New-Object** werken met onderdelen van de Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="bfdc1-146">You can use **New-Object** to work with Component Object Model (COM) components.</span></span> <span data-ttu-id="bfdc1-147">Het bereik van de onderdelen van de verschillende bibliotheken opgenomen ActiveX-toepassingen zoals Internet Explorer die zijn geïnstalleerd op de meeste systemen met Windows Script Host (WSH).</span><span class="sxs-lookup"><span data-stu-id="bfdc1-147">Components range from the various libraries included with Windows Script Host (WSH) to ActiveX applications such as Internet Explorer that are installed on most systems.</span></span>

<span data-ttu-id="bfdc1-148">**Nieuw Object** gebruikmaakt van .NET Framework Runtime-Callable-Wrappers COM-objecten te maken, zodat deze dezelfde beperkingen als .NET Framework biedt heeft bij het aanroepen van COM-objecten.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-148">**New-Object** uses .NET Framework Runtime-Callable Wrappers to create COM objects, so it has the same limitations that .NET Framework does when calling COM objects.</span></span> <span data-ttu-id="bfdc1-149">Voor het maken van een COM-object, moet u opgeven de **ComObject** parameter met de programma-id of *ProgId* van de COM-klasse die u wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-149">To create a COM object, you need to specify the **ComObject** parameter with the Programmatic Identifier or *ProgId* of the COM class you want to use.</span></span> <span data-ttu-id="bfdc1-150">Een uitgebreide bespreking van de beperkingen van de COM-gebruik en het bepalen van wat ProgID's zijn beschikbaar op een systeem valt buiten het bereik van deze handleiding, maar het meest bekende objecten uit omgevingen zoals WSH kunnen worden gebruikt in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-150">A complete discussion of the limitations of COM use and determining what ProgIds are available on a system is beyond the scope of this user's guide, but most well-known objects from environments such as WSH can be used within Windows PowerShell.</span></span>

<span data-ttu-id="bfdc1-151">U kunt de objecten WSH maken door op te geven deze ProgID: **instantie**, **WScript.Network**, **Scripting.Dictionary**, en  **Scripting.FileSystemObject**.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-151">You can create the WSH objects by specifying these progids: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, and **Scripting.FileSystemObject**.</span></span> <span data-ttu-id="bfdc1-152">De volgende opdrachten maakt deze objecten:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-152">The following commands create these objects:</span></span>

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

<span data-ttu-id="bfdc1-153">Hoewel de meeste functionaliteit van deze klassen beschikbaar zijn op andere manieren in Windows PowerShell wordt gemaakt, zijn een paar taken, zoals het maken van snelkoppeling nog steeds gemakkelijker te doen met behulp van de klassen WSH.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-153">Although most of the functionality of these classes is made available in other ways in Windows PowerShell, a few tasks such as shortcut creation are still easier to do using the WSH classes.</span></span>

### <a name="creating-a-desktop-shortcut-with-wscriptshell"></a><span data-ttu-id="bfdc1-154">Maken van een snelkoppeling op het bureaublad met instantie</span><span class="sxs-lookup"><span data-stu-id="bfdc1-154">Creating a Desktop Shortcut with WScript.Shell</span></span>

<span data-ttu-id="bfdc1-155">Een taak die snel kan worden uitgevoerd met een COM-object met het maken van een snelkoppeling.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-155">One task that can be performed quickly with a COM object is creating a shortcut.</span></span> <span data-ttu-id="bfdc1-156">Stel dat u wilt een snelkoppeling op het bureaublad maken die verwijst naar de basismap voor Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-156">Suppose you want to create a shortcut on your desktop that links to the home folder for Windows PowerShell.</span></span> <span data-ttu-id="bfdc1-157">U moet eerst maakt u een verwijzing naar **instantie**, die wordt opgeslagen in een variabele met de naam **$WshShell**:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-157">You first need to create a reference to **WScript.Shell**, which we will store in a variable named **$WshShell**:</span></span>

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

<span data-ttu-id="bfdc1-158">Get-lid werkt met COM-objecten, zodat u op de leden van het object door te typen vindt:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-158">Get-Member works with COM objects, so you can explore the members of the object by typing:</span></span>

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

<span data-ttu-id="bfdc1-159">**Get-lid** is een optionele **InputObject** parameter kunt u in plaats van piping om te voorzien van gegevens **Get-lid**.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-159">**Get-Member** has an optional **InputObject** parameter you can use instead of piping to provide input to **Get-Member**.</span></span> <span data-ttu-id="bfdc1-160">Krijgt u hetzelfde uitvoer zoals hierboven als u in plaats daarvan de opdracht gebruikt **lid zijn van Get - InputObject $WshShell**.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-160">You would get the same output as shown above if you instead used the command **Get-Member -InputObject $WshShell**.</span></span> <span data-ttu-id="bfdc1-161">Als u **InputObject**, worden behandeld als het argument als één item.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-161">If you use **InputObject**, it treats its argument as a single item.</span></span> <span data-ttu-id="bfdc1-162">Dit betekent dat als er meerdere objecten in een variabele, **Get-lid** ze worden beschouwd als een matrix met objecten.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-162">This means that if you have several objects in a variable, **Get-Member** treats them as an array of objects.</span></span> <span data-ttu-id="bfdc1-163">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-163">For example:</span></span>

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

<span data-ttu-id="bfdc1-164">De **instantie CreateShortcut** methode accepteert één argument, het pad naar het snelkoppelingsbestand maken.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-164">The **WScript.Shell CreateShortcut** method accepts a single argument, the path to the shortcut file to create.</span></span> <span data-ttu-id="bfdc1-165">We kunnen typt in het volledige pad naar het bureaublad, maar er is een eenvoudigere manier.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-165">We could type in the full path to the desktop, but there is an easier way.</span></span> <span data-ttu-id="bfdc1-166">Het bureaublad wordt normaal gesproken vertegenwoordigd door een map met de naam Desktop binnen de basismap van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-166">The desktop is normally represented by a folder named Desktop inside the home folder of the current user.</span></span> <span data-ttu-id="bfdc1-167">Windows PowerShell is een variabele **$Home** die het pad naar deze map bevat.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-167">Windows PowerShell has a variable **$Home** that contains the path to this folder.</span></span> <span data-ttu-id="bfdc1-168">We kunnen het pad naar de basismap opgeven met behulp van deze variabele en voeg vervolgens de naam van de map bureaublad en de naam voor de snelkoppeling maken door te typen:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-168">We can specify the path to the home folder by using this variable, and then add the name of the Desktop folder and the name for the shortcut to create by typing:</span></span>

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

<span data-ttu-id="bfdc1-169">Wanneer u iets dat op de naam van een variabele binnen dubbele aanhalingstekens lijkt gebruikt, wordt Windows PowerShell probeert te vervangen door een overeenkomende waarde.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-169">When you use something that looks like a variable name inside double-quotes, Windows PowerShell tries to substitute a matching value.</span></span> <span data-ttu-id="bfdc1-170">Als u één aanhalingstekens gebruikt, probeert Windows PowerShell niet vervangen door de variabele waarde.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-170">If you use single-quotes, Windows PowerShell does not try to substitute the variable value.</span></span> <span data-ttu-id="bfdc1-171">Probeer bijvoorbeeld de volgende opdrachten te typen:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-171">For example, try typing the following commands:</span></span>

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

<span data-ttu-id="bfdc1-172">We hebt nu een variabele met de naam **$lnk** die een nieuwe snelkoppeling-verwijzing bevat.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-172">We now have a variable named **$lnk** that contains a new shortcut reference.</span></span> <span data-ttu-id="bfdc1-173">Als u zien van de leden wilt, kunt u het doorsluizen naar **Get-lid**.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-173">If you want to see its members, you can pipe it to **Get-Member**.</span></span> <span data-ttu-id="bfdc1-174">De onderstaande uitvoer ziet u de leden moeten we onze snelkoppeling gebruiken:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-174">The output below shows the members we need to use to finish creating our shortcut:</span></span>

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

<span data-ttu-id="bfdc1-175">Moeten we geven de **TargetPath**, dit is de toepassingsmap voor Windows PowerShell en sla de snelkoppeling **$lnk** door het aanroepen van de **opslaan** methode.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-175">We need to specify the **TargetPath**, which is the application folder for Windows PowerShell, and then save the shortcut **$lnk** by calling the **Save** method.</span></span> <span data-ttu-id="bfdc1-176">Het pad van de Windows PowerShell-toepassing wordt opgeslagen in de variabele **$PSHome**, zodat we dit door te typen doen kunt:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-176">The Windows PowerShell application folder path is stored in the variable **$PSHome**, so we can do this by typing:</span></span>

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

### <a name="using-internet-explorer-from-windows-powershell"></a><span data-ttu-id="bfdc1-177">Met behulp van Internet Explorer vanuit Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bfdc1-177">Using Internet Explorer from Windows PowerShell</span></span>

<span data-ttu-id="bfdc1-178">Veel toepassingen (met inbegrip van de Microsoft Office-familie van toepassingen en Internet Explorer) kunnen worden geautomatiseerd met behulp van COM.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-178">Many applications (including the Microsoft Office family of applications and Internet Explorer) can be automated by using COM.</span></span> <span data-ttu-id="bfdc1-179">Internet Explorer ziet u enkele van de gangbare technieken en problemen die zijn betrokken bij het werken met COM gebaseerde toepassingen.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-179">Internet Explorer illustrates some of the typical techniques and issues involved in working with COM-based applications.</span></span>

<span data-ttu-id="bfdc1-180">U een exemplaar van Internet Explorer maken door de Internet Explorer ProgId **InternetExplorer.Application**:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-180">You create an Internet Explorer instance by specifying the Internet Explorer ProgId, **InternetExplorer.Application**:</span></span>

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

<span data-ttu-id="bfdc1-181">Met deze opdracht Start Internet Explorer, maar is niet zichtbaar maken.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-181">This command starts Internet Explorer, but does not make it visible.</span></span> <span data-ttu-id="bfdc1-182">Als u een Get-Process typt, ziet u dat een proces met de naam iexplore wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-182">If you type Get-Process, you can see that a process named iexplore is running.</span></span> <span data-ttu-id="bfdc1-183">Zelfs als u Windows PowerShell afsluit, blijft het proces actief.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-183">In fact, if you exit Windows PowerShell, the process will continue to run.</span></span> <span data-ttu-id="bfdc1-184">U moet de computer opnieuw opstarten of een hulpprogramma zoals Taakbeheer gebruiken om de iexplore proces te beëindigen.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-184">You must reboot the computer or use a tool like Task Manager to end the iexplore process.</span></span>

> [!NOTE]
> <span data-ttu-id="bfdc1-185">COM-objecten die worden gestart als afzonderlijke processen genoemd *uitvoerbare bestanden ActiveX*, kan of kunnen niet een gebruikersinterface-venster weergeven wanneer deze opgestart worden.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-185">COM objects that start as separate processes, commonly called *ActiveX executables*, may or may not display a user interface window when they start up.</span></span> <span data-ttu-id="bfdc1-186">Als ze geen venster maken, maar maak niet wordt weergegeven, zoals Internet Explorer, de focus in het algemeen wordt verplaatst naar het Windows-bureaublad en moet u het venster zichtbaar ermee te maken.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-186">If they create a window but do not make it visible, like Internet Explorer, the focus will generally move to the Windows desktop and you must make the window visible to interact with it.</span></span>

<span data-ttu-id="bfdc1-187">Door te typen **$ie | Get-lid**, kunt u eigenschappen en methoden voor Internet Explorer weergeven.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-187">By typing **$ie | Get-Member**, you can view properties and methods for Internet Explorer.</span></span> <span data-ttu-id="bfdc1-188">Stel de eigenschap Visible op $true door te voeren overzicht van de Internet Explorer-venster:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-188">To see the Internet Explorer window, set the Visible property to $true by typing:</span></span>

```powershell
$ie.Visible = $true
```

<span data-ttu-id="bfdc1-189">U kunt vervolgens naar een specifieke webadres navigeren met behulp van de methode navigeren:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-189">You can then navigate to a specific Web address by using the Navigate method:</span></span>

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

<span data-ttu-id="bfdc1-190">Met andere leden van het Internet Explorer-objectmodel, is het mogelijk tekstinhoud ophalen van de webpagina.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-190">Using other members of the Internet Explorer object model, it is possible to retrieve text content from the Web page.</span></span> <span data-ttu-id="bfdc1-191">De volgende opdracht worden de HTML-tekst in de hoofdtekst van de huidige webpagina weergegeven:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-191">The following command will display the HTML text in the body of the current Web page:</span></span>

```powershell
$ie.Document.Body.InnerText
```

<span data-ttu-id="bfdc1-192">Roep de methode Quit() Internet Explorer uit in PowerShell om af te sluiten:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-192">To close Internet Explorer from within PowerShell, call its Quit() method:</span></span>

```powershell
$ie.Quit()
```

<span data-ttu-id="bfdc1-193">Deze toepassing nu afsluiten.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-193">This will force it to close.</span></span> <span data-ttu-id="bfdc1-194">Een geldige verwijzing naar bevat de ie-variabele $ niet langer zelfs als deze nog steeds lijkt te zijn van een COM-object.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-194">The $ie variable no longer contains a valid reference even though it still appears to be a COM object.</span></span> <span data-ttu-id="bfdc1-195">Als u probeert te gebruiken, krijgt u een automatiseringsfout:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-195">If you attempt to use it, you will get an automation error:</span></span>

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

<span data-ttu-id="bfdc1-196">U kunt een verwijderen ie naar de resterende verwijzen met een opdracht zoals $ = $null of volledig verwijderen van de variabele door te typen:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-196">You can either remove the remaining reference with a command like $ie = $null, or completely remove the variable by typing:</span></span>

```powershell
Remove-Variable ie
```

> [!NOTE]
> <span data-ttu-id="bfdc1-197">Er is geen algemene standaard voor uitvoerbare bestanden ActiveX sluiten of worden uitgevoerd wanneer u een verwijzing naar een verwijdert.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-197">There is no common standard for whether ActiveX executables exit or continue to run when you remove a reference to one.</span></span> <span data-ttu-id="bfdc1-198">Afhankelijk van de omstandigheden zoals bepaalt of de toepassing zichtbaar is, of een bewerkte document erin wordt uitgevoerd en zelfs of Windows PowerShell wordt nog steeds uitgevoerd, wordt de toepassing kan of kan niet worden afgesloten.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-198">Depending on circumstances such as whether the application is visible, whether an edited document is running in it, and even whether Windows PowerShell is still running, the application may or may not exit.</span></span> <span data-ttu-id="bfdc1-199">Daarom moet u beëindiging gedrag testen voor elke ActiveX uitvoerbare dat u wilt gebruiken in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-199">For this reason, you should test termination behavior for each ActiveX executable you want to use in Windows PowerShell.</span></span>

### <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a><span data-ttu-id="bfdc1-200">Waarschuwingen over .NET Framework ingepakt COM-objecten</span><span class="sxs-lookup"><span data-stu-id="bfdc1-200">Getting Warnings About .NET Framework-Wrapped COM Objects</span></span>

<span data-ttu-id="bfdc1-201">In sommige gevallen kan een COM-object een bijbehorende .NET Framework wellicht *Runtime-Callable Wrapper* RCW en dit wordt gebruikt door **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-201">In some cases, a COM object might have an associated .NET Framework *Runtime-Callable Wrapper* or RCW, and this will be used by **New-Object**.</span></span> <span data-ttu-id="bfdc1-202">Omdat het gedrag van de RCW van het gedrag van het normale COM-object afwijken kan **New-Object** heeft een **Strict** parameter om u te waarschuwen over RCW toegang.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-202">Since the behavior of the RCW may be different from the behavior of the normal COM object, **New-Object** has a **Strict** parameter to warn you about RCW access.</span></span> <span data-ttu-id="bfdc1-203">Als u opgeeft de **Strict** parameter en maak vervolgens een COM-object dat gebruikmaakt van een RCW, wordt er een waarschuwing weergegeven:</span><span class="sxs-lookup"><span data-stu-id="bfdc1-203">If you specify the **Strict** parameter and then create a COM object that uses an RCW, you get a warning message:</span></span>

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

<span data-ttu-id="bfdc1-204">Hoewel het object nog steeds gemaakt is, wordt u gewaarschuwd dat het niet standaard COM-object is.</span><span class="sxs-lookup"><span data-stu-id="bfdc1-204">Although the object is still created, you are warned that it is not a standard COM object.</span></span>