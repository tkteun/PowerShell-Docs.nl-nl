---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-webserviceproxy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WebServiceProxy
ms.openlocfilehash: aea656bc8ad4416673a7abb7d32a58d45dd3cc4f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250593"
---
# <span data-ttu-id="a7d44-103">New-WebServiceProxy</span><span class="sxs-lookup"><span data-stu-id="a7d44-103">New-WebServiceProxy</span></span>

## <span data-ttu-id="a7d44-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a7d44-104">SYNOPSIS</span></span>
<span data-ttu-id="a7d44-105">Hiermee maakt u een Web Service proxy-object waarmee u de webservice in Power shell kunt gebruiken en beheren.</span><span class="sxs-lookup"><span data-stu-id="a7d44-105">Creates a Web service proxy object that lets you use and manage the Web service in PowerShell.</span></span>

## <span data-ttu-id="a7d44-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a7d44-106">SYNTAX</span></span>

### <span data-ttu-id="a7d44-107">Referenties (standaard)</span><span class="sxs-lookup"><span data-stu-id="a7d44-107">NoCredentials (Default)</span></span>

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [<CommonParameters>]
```

### <span data-ttu-id="a7d44-108">Referentie</span><span class="sxs-lookup"><span data-stu-id="a7d44-108">Credential</span></span>

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="a7d44-109">UseDefaultCredential</span><span class="sxs-lookup"><span data-stu-id="a7d44-109">UseDefaultCredential</span></span>

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-UseDefaultCredential]
 [<CommonParameters>]
```

## <span data-ttu-id="a7d44-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a7d44-110">DESCRIPTION</span></span>

<span data-ttu-id="a7d44-111">`New-WebServiceProxy`Met de cmdlet kunt u een webservice in Power shell gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a7d44-111">The `New-WebServiceProxy` cmdlet lets you use a Web service in PowerShell.</span></span> <span data-ttu-id="a7d44-112">Met de cmdlet maakt u verbinding met een webservice en maakt u een Web Service proxy-object in Power shell.</span><span class="sxs-lookup"><span data-stu-id="a7d44-112">The cmdlet connects to a Web service and creates a Web service proxy object in PowerShell.</span></span> <span data-ttu-id="a7d44-113">U kunt het proxy-object gebruiken om de webservice te beheren.</span><span class="sxs-lookup"><span data-stu-id="a7d44-113">You can use the proxy object to manage the Web service.</span></span>

<span data-ttu-id="a7d44-114">Een webservice is een XML-programma waarmee gegevens via een netwerk worden uitgewisseld, met name via internet.</span><span class="sxs-lookup"><span data-stu-id="a7d44-114">A Web service is an XML-based program that exchanges data over a network, especially over the Internet.</span></span> <span data-ttu-id="a7d44-115">Het Microsoft .NET Framework biedt Web Service proxy-objecten die de webservice vertegenwoordigen als een .NET Framework-object.</span><span class="sxs-lookup"><span data-stu-id="a7d44-115">The Microsoft .NET Framework provides Web service proxy objects that represent the Web service as a .NET Framework object.</span></span>

## <span data-ttu-id="a7d44-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a7d44-116">EXAMPLES</span></span>

### <span data-ttu-id="a7d44-117">Voor beeld 1: een proxy maken voor een webservice</span><span class="sxs-lookup"><span data-stu-id="a7d44-117">Example 1: Create a proxy for a Web service</span></span>

<span data-ttu-id="a7d44-118">In dit voor beeld wordt een .NET Framework proxy van de rekenmachine-webservice gemaakt in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="a7d44-118">This example creates a .NET Framework proxy of the calculator Web service in Windows PowerShell.</span></span>

```powershell
$calc = New-WebServiceProxy -Uri "http://www.dneonline.com/calculator.asmx?wsdl"
```

### <span data-ttu-id="a7d44-119">Voor beeld 2: een proxy maken voor een webservice en naam ruimte en klasse opgeven</span><span class="sxs-lookup"><span data-stu-id="a7d44-119">Example 2: Create a proxy for a Web service and specify namespace and class</span></span>

<span data-ttu-id="a7d44-120">In dit voor beeld wordt de `New-WebServiceProxy` cmdlet gebruikt om een .NET Framework proxy van de rekenmachine-webservice te maken.</span><span class="sxs-lookup"><span data-stu-id="a7d44-120">This example uses the `New-WebServiceProxy` cmdlet to create a .NET Framework proxy of the calculator Web service.</span></span>

```powershell
$URI = "http://www.dneonline.com/calculator.asmx?wsdl"
$calc = New-WebServiceProxy -Uri $URI -Namespace "WSProxy" -Class "Calculator"
```

<span data-ttu-id="a7d44-121">De opdracht gebruikt de **URI** -para meter om de URI en de para meters van de **naam ruimte** en **klasse** op te geven om de naam ruimte en klasse van het object op te geven.</span><span class="sxs-lookup"><span data-stu-id="a7d44-121">The command uses the **Uri** parameter to specify the URI and the **Namespace** and **Class** parameters to specify the namespace and class of the object.</span></span>

### <span data-ttu-id="a7d44-122">Voor beeld 3: methoden van een webserviceproxy weer geven</span><span class="sxs-lookup"><span data-stu-id="a7d44-122">Example 3: Display methods of a Web service proxy</span></span>

```powershell
$calc | Get-Member -MemberType method
```

```Output
   TypeName: WSProxy.Calculator

Name                      MemberType Definition
----                      ---------- ----------
Abort                     Method     void Abort()
Add                       Method     int Add(int intA, int intB)
AddAsync                  Method     void AddAsync(int intA, int intB), void AddAsync(int intA,
BeginAdd                  Method     System.IAsyncResult BeginAdd(int intA, int intB, System.Asy
BeginDivide               Method     System.IAsyncResult BeginDivide(int intA, int intB, System.
BeginMultiply             Method     System.IAsyncResult BeginMultiply(int intA, int intB, Syste
BeginSubtract             Method     System.IAsyncResult BeginSubtract(int intA, int intB, Syste
CancelAsync               Method     void CancelAsync(System.Object userState)
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type requestedT
Discover                  Method     void Discover()
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Divide                    Method     int Divide(int intA, int intB)
DivideAsync               Method     void DivideAsync(int intA, int intB), void DivideAsync(int
EndAdd                    Method     int EndAdd(System.IAsyncResult asyncResult)
EndDivide                 Method     int EndDivide(System.IAsyncResult asyncResult)
EndMultiply               Method     int EndMultiply(System.IAsyncResult asyncResult)
EndSubtract               Method     int EndSubtract(System.IAsyncResult asyncResult)
Equals                    Method     bool Equals(System.Object obj)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Multiply                  Method     int Multiply(int intA, int intB)
MultiplyAsync             Method     void MultiplyAsync(int intA, int intB), void MultiplyAsync(
Subtract                  Method     int Subtract(int intA, int intB)
SubtractAsync             Method     void SubtractAsync(int intA, int intB), void SubtractAsync(
ToString                  Method     string ToString()
```

<span data-ttu-id="a7d44-123">In dit voor beeld wordt de `Get-Member` cmdlet gebruikt om de methoden van het object Web Service proxy in de variabele weer te geven `$calc` .</span><span class="sxs-lookup"><span data-stu-id="a7d44-123">This example uses the `Get-Member` cmdlet to display the methods of the Web service proxy object in the `$calc` variable.</span></span> <span data-ttu-id="a7d44-124">We gebruiken deze methoden in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="a7d44-124">We uses these methods in the following example.</span></span>

<span data-ttu-id="a7d44-125">U ziet dat de **TypeName** van het proxy-object, WebServiceProxy, de naam ruimte en klassen namen weerspiegelt die in het vorige voor beeld zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a7d44-125">Notice that the **TypeName** of the proxy object, WebServiceProxy, reflects the namespace and class names that were specified in the previous example.</span></span>

### <span data-ttu-id="a7d44-126">Voor beeld 4: een webserviceproxy gebruiken</span><span class="sxs-lookup"><span data-stu-id="a7d44-126">Example 4: Use a Web service proxy</span></span>

```powershell
PS> $calc.Multiply(6,7)
42
```

<span data-ttu-id="a7d44-127">In dit voor beeld wordt de webserviceproxy gebruikt die is opgeslagen in de `$calc` variabele.</span><span class="sxs-lookup"><span data-stu-id="a7d44-127">This example uses the Web service proxy stored in the `$calc` variable.</span></span> <span data-ttu-id="a7d44-128">De opdracht maakt gebruik van de **vermenigvuldigings** methode van de proxy.</span><span class="sxs-lookup"><span data-stu-id="a7d44-128">The command uses the **Multiply** method of the proxy.</span></span>

## <span data-ttu-id="a7d44-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a7d44-129">PARAMETERS</span></span>

### <span data-ttu-id="a7d44-130">-Klasse</span><span class="sxs-lookup"><span data-stu-id="a7d44-130">-Class</span></span>

<span data-ttu-id="a7d44-131">Hiermee geeft u een naam op voor de proxy klasse die door de cmdlet wordt gemaakt voor de webservice.</span><span class="sxs-lookup"><span data-stu-id="a7d44-131">Specifies a name for the proxy class that the cmdlet creates for the Web service.</span></span> <span data-ttu-id="a7d44-132">De waarde van deze para meter wordt samen met de **naam ruimte** parameter gebruikt om een volledig gekwalificeerde naam voor de klasse op te geven.</span><span class="sxs-lookup"><span data-stu-id="a7d44-132">The value of this parameter is used together with the **Namespace** parameter to provide a fully qualified name for the class.</span></span> <span data-ttu-id="a7d44-133">De standaard waarde wordt gegenereerd op basis van de URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="a7d44-133">The default value is generated from the Uniform Resource Identifier (URI).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: FileName, FN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7d44-134">-Credential</span><span class="sxs-lookup"><span data-stu-id="a7d44-134">-Credential</span></span>

<span data-ttu-id="a7d44-135">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="a7d44-135">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="a7d44-136">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a7d44-136">The default is the current user.</span></span> <span data-ttu-id="a7d44-137">Dit is een alternatief voor het gebruik van de para meter **UseDefaultCredential** .</span><span class="sxs-lookup"><span data-stu-id="a7d44-137">This is an alternative to using the **UseDefaultCredential** parameter.</span></span>

<span data-ttu-id="a7d44-138">Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7d44-138">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="a7d44-139">Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="a7d44-139">If you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Credential
Aliases: Cred

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7d44-140">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="a7d44-140">-Namespace</span></span>

<span data-ttu-id="a7d44-141">Hiermee geeft u een naam ruimte voor de nieuwe klasse op.</span><span class="sxs-lookup"><span data-stu-id="a7d44-141">Specifies a namespace for the new class.</span></span>

<span data-ttu-id="a7d44-142">De waarde van deze para meter wordt samen met de waarde van de para meter **Class** gebruikt om een volledig gekwalificeerde naam voor de klasse te genereren.</span><span class="sxs-lookup"><span data-stu-id="a7d44-142">The value of this parameter is used together with the value of the **Class** parameter to generate a fully qualified name for the class.</span></span> <span data-ttu-id="a7d44-143">De standaard waarde is **micro soft. Power shell. commands. NewWebserviceProxy. AutogeneratedTypes** plus een type dat is gegenereerd op basis van de URI.</span><span class="sxs-lookup"><span data-stu-id="a7d44-143">The default value is **Microsoft.PowerShell.Commands.NewWebserviceProxy.AutogeneratedTypes** plus a type that is generated from the URI.</span></span>

<span data-ttu-id="a7d44-144">U kunt de waarde van de **naam ruimte** parameter instellen, zodat u toegang hebt tot meerdere webservices die dezelfde naam hebben.</span><span class="sxs-lookup"><span data-stu-id="a7d44-144">You can set the value of the **Namespace** parameter so that you can access multiple Web services that have the same name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7d44-145">-URI</span><span class="sxs-lookup"><span data-stu-id="a7d44-145">-Uri</span></span>

<span data-ttu-id="a7d44-146">Hiermee geeft u de URI van de webservice.</span><span class="sxs-lookup"><span data-stu-id="a7d44-146">Specifies the URI of the Web service.</span></span> <span data-ttu-id="a7d44-147">Voer een URI of het pad en de bestands naam in van een bestand dat een service beschrijving bevat.</span><span class="sxs-lookup"><span data-stu-id="a7d44-147">Enter a URI or the path and filename of a file that contains a service description.</span></span>

<span data-ttu-id="a7d44-148">De URI moet een `.asmx` pagina of een pagina retour neren die een service beschrijving retourneert.</span><span class="sxs-lookup"><span data-stu-id="a7d44-148">The URI must return an `.asmx` page or to a page that returns a service description.</span></span> <span data-ttu-id="a7d44-149">Als u een service beschrijving wilt retour neren van een webservice die is gemaakt met behulp van ASP.NET, voegt u '? ' toe? WSDL ' naar de URL van de webservice (bijvoorbeeld `http://www.contoso.com/MyWebService.asmx?WSDL` ).</span><span class="sxs-lookup"><span data-stu-id="a7d44-149">To return a service description of a Web service that was created using ASP.NET, append "?WSDL" to the URL of the Web service (for example, `http://www.contoso.com/MyWebService.asmx?WSDL`).</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: WL, WSDL, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7d44-150">-UseDefaultCredential</span><span class="sxs-lookup"><span data-stu-id="a7d44-150">-UseDefaultCredential</span></span>

<span data-ttu-id="a7d44-151">Geeft aan dat deze cmdlet de standaard referentie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a7d44-151">Indicates that this cmdlet uses the default credential.</span></span> <span data-ttu-id="a7d44-152">Met deze cmdlet wordt de eigenschap **UseDefaultCredential** in het resulterende proxy-object ingesteld op True.</span><span class="sxs-lookup"><span data-stu-id="a7d44-152">This cmdlet sets the **UseDefaultCredential** property in the resulting proxy object to True.</span></span> <span data-ttu-id="a7d44-153">Dit is een alternatief voor het gebruik van de para meter **Credential** .</span><span class="sxs-lookup"><span data-stu-id="a7d44-153">This is an alternative to using the **Credential** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseDefaultCredential
Aliases: UDC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7d44-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a7d44-154">CommonParameters</span></span>

<span data-ttu-id="a7d44-155">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a7d44-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a7d44-156">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a7d44-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a7d44-157">INVOER</span><span class="sxs-lookup"><span data-stu-id="a7d44-157">INPUTS</span></span>

### <span data-ttu-id="a7d44-158">Geen</span><span class="sxs-lookup"><span data-stu-id="a7d44-158">None</span></span>

<span data-ttu-id="a7d44-159">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7d44-159">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a7d44-160">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a7d44-160">OUTPUTS</span></span>

### <span data-ttu-id="a7d44-161">Een Web Service proxy-object</span><span class="sxs-lookup"><span data-stu-id="a7d44-161">A Web service proxy object</span></span>

<span data-ttu-id="a7d44-162">Met deze cmdlet wordt een object van een webservice-proxy geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="a7d44-162">This cmdlet returns a Web service proxy object.</span></span> <span data-ttu-id="a7d44-163">De naam ruimte en klasse van het object worden bepaald door de para meters van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="a7d44-163">The namespace and class of the object are determined by the parameters of the command.</span></span> <span data-ttu-id="a7d44-164">De standaard waarde wordt gegenereerd op basis van de invoer-URI.</span><span class="sxs-lookup"><span data-stu-id="a7d44-164">The default is generated from the input URI.</span></span>

## <span data-ttu-id="a7d44-165">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a7d44-165">NOTES</span></span>

<span data-ttu-id="a7d44-166">`New-WebServiceProxy` maakt gebruik van de klasse **System .net. webclient** om de opgegeven webservice te laden.</span><span class="sxs-lookup"><span data-stu-id="a7d44-166">`New-WebServiceProxy` uses the **System.Net.WebClient** class to load the specified Web service.</span></span>

## <span data-ttu-id="a7d44-167">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a7d44-167">RELATED LINKS</span></span>

[<span data-ttu-id="a7d44-168">New-Service</span><span class="sxs-lookup"><span data-stu-id="a7d44-168">New-Service</span></span>](New-Service.md)
