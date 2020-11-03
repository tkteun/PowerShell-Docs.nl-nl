---
external help file: Microsoft.PowerShell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflowUtility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflowutility/invoke-asworkflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-AsWorkflow
ms.openlocfilehash: b96bce9fe4d574fe2b7e9c7c0f1e05ee0508adce
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250286"
---
# <span data-ttu-id="5330c-103">Invoke-AsWorkflow</span><span class="sxs-lookup"><span data-stu-id="5330c-103">Invoke-AsWorkflow</span></span>

## <span data-ttu-id="5330c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="5330c-104">SYNOPSIS</span></span>
<span data-ttu-id="5330c-105">Hiermee wordt een opdracht of expressie uitgevoerd als een Windows Power shell-werk stroom.</span><span class="sxs-lookup"><span data-stu-id="5330c-105">Runs a command or expression as a Windows PowerShell Workflow.</span></span>

## <span data-ttu-id="5330c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="5330c-106">SYNTAX</span></span>

### <span data-ttu-id="5330c-107">Opdracht (standaard)</span><span class="sxs-lookup"><span data-stu-id="5330c-107">Command (Default)</span></span>

```
Invoke-AsWorkflow [-CommandName <String>] [-Parameter <Hashtable>] [-InputObject <Object>] [<CommonParameters>]
```

### <span data-ttu-id="5330c-108">Expression</span><span class="sxs-lookup"><span data-stu-id="5330c-108">Expression</span></span>

```
Invoke-AsWorkflow [-Expression <String>] [-InputObject <Object>] [<CommonParameters>]
```

## <span data-ttu-id="5330c-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5330c-109">DESCRIPTION</span></span>

<span data-ttu-id="5330c-110">De `Invoke-AsWorkflow` werk stroom voert een wille keurige opdracht of expressie uit als inline script in een werk stroom.</span><span class="sxs-lookup"><span data-stu-id="5330c-110">The `Invoke-AsWorkflow` workflow runs any command or expression as an inline script in a workflow.</span></span>
<span data-ttu-id="5330c-111">Deze werk stromen gebruiken de standaard werk stroom semantiek, hebben alle algemene werk stroom parameters en hebben alle voor delen van werk stromen, inclusief de mogelijkheid om te stoppen, te hervatten en te herstellen.</span><span class="sxs-lookup"><span data-stu-id="5330c-111">These workflows use the standard workflow semantics, have all workflow common parameters, and have all benefits of workflows, including the ability to stop, resume, and recover.</span></span>

<span data-ttu-id="5330c-112">Werk stromen zijn ontworpen voor langlopende opdrachten die essentiële gegevens verzamelen, maar kunnen worden gebruikt om elke opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="5330c-112">Workflows are designed for long-running commands that collect critical data, but can be used to run any command.</span></span>
<span data-ttu-id="5330c-113">Zie [about_Workflows](../PSWorkflow/About/about_Workflows.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5330c-113">For more information, see [about_Workflows](../PSWorkflow/About/about_Workflows.md).</span></span>

<span data-ttu-id="5330c-114">U kunt ook algemene werk stroom parameters toevoegen aan deze opdracht.</span><span class="sxs-lookup"><span data-stu-id="5330c-114">You can also add workflow common parameters to this command.</span></span>
<span data-ttu-id="5330c-115">Zie [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md) voor meer informatie over algemene werk stroom parameters</span><span class="sxs-lookup"><span data-stu-id="5330c-115">For more information about workflow common parameters, see [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)</span></span>

<span data-ttu-id="5330c-116">Deze werk stroom is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5330c-116">This workflow is introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="5330c-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="5330c-117">EXAMPLES</span></span>

### <span data-ttu-id="5330c-118">Voor beeld 1: een cmdlet uitvoeren als werk stroom</span><span class="sxs-lookup"><span data-stu-id="5330c-118">Example 1: Run a cmdlet as a workflow</span></span>

```powershell
Invoke-AsWorkflow -PSComputerName (Get-Content Servers.txt) -CommandName Get-ExecutionPolicy
```

```output
PSComputerName                     PSSourceJobInstanceId                   Value
--------------                     ---------------------                   -----
Server01                           77b1cdf8-8226-4662-9067-cd2fa5c3b711    AllSigned
Server02                           a33542d7-3cdd-4339-ab99-0e7cd8e59462    Unrestricted
Server03                           279bac28-066a-4646-9497-8fcdcfe9757e    AllSigned
localhost                          0d858009-2cc4-47a4-a2e0-da17dc2883d0    RemoteSigned
```

<span data-ttu-id="5330c-119">Met deze opdracht wordt de `Get-ExecutionPolicy` cmdlet op honderden computers uitgevoerd als een werk stroom.</span><span class="sxs-lookup"><span data-stu-id="5330c-119">This command runs the `Get-ExecutionPolicy` cmdlet as a workflow on hundreds of computers.</span></span>

<span data-ttu-id="5330c-120">De opdracht gebruikt de para meter **opdrachtnaam** om de cmdlet op te geven die in de werk stroom wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5330c-120">The command uses the **CommandName** parameter to specify the cmdlet that runs in the workflow.</span></span>
<span data-ttu-id="5330c-121">De gemeen schappelijke para meter **PSComputerName** workflow wordt gebruikt om de computers op te geven waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5330c-121">It uses the **PSComputerName** workflow common parameter to specify the computers on which the command runs.</span></span>
<span data-ttu-id="5330c-122">De waarde van de para meter **PSComputerName** is een `Get-Content` opdracht waarmee een lijst met computer namen uit het Servers.txt bestand wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="5330c-122">The value of the **PSComputerName** parameter is a `Get-Content` command that gets a list of computer names from the Servers.txt file.</span></span>
<span data-ttu-id="5330c-123">De waarde van de para meter bevindt zich tussen haakjes om Windows Power shell te laten werken om de opdracht uit te voeren `Get-Command` voordat de waarde wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5330c-123">The parameter value is enclosed in parentheses to direct Windows PowerShell to run the `Get-Command` command before using the value.</span></span>

<span data-ttu-id="5330c-124">Net als bij alle externe opdrachten, als de opdracht wordt uitgevoerd op de lokale computer (als de waarde van de para meter PSComputerName de lokale computer bevat), moet u Windows Power shell starten met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="5330c-124">As with all remote commands, if the command runs on the local computer, (if the value of the PSComputerName parameter includes the local computer), you must start Windows PowerShell with the "Run as administrator" option.</span></span>

### <span data-ttu-id="5330c-125">Voor beeld 2: een cmdlet met para meters uitvoeren</span><span class="sxs-lookup"><span data-stu-id="5330c-125">Example 2: Run a cmdlet with parameters</span></span>

```powershell
$s = Import-Csv .\Servers.csv -Header ServerName, ServerID
Invoke-AsWorkflow -CommandName Get-ExecutionPolicy -Parameter @{Scope="Process"} -PSComputerName {$s.ServerName} -PSConnectionRetryCount 5
```

<span data-ttu-id="5330c-126">Met de eerste opdracht wordt de `Import-Csv` cmdlet gebruikt om een object te maken op basis van de inhoud in het Servers.csv-bestand.</span><span class="sxs-lookup"><span data-stu-id="5330c-126">The first command uses the `Import-Csv` cmdlet to create an object from the content in the Servers.csv file.</span></span> <span data-ttu-id="5330c-127">De opdracht gebruikt de `Header` para meter voor het maken van een `ServerName` eigenschap voor de kolom die de namen van de doel computers bevat, ook wel ' externe knoop punten ' genoemd.</span><span class="sxs-lookup"><span data-stu-id="5330c-127">The command uses the `Header` parameter to create a `ServerName` property for the column that contains the names of the target computers, also known as "remote nodes."</span></span> <span data-ttu-id="5330c-128">De opdracht slaat het resultaat op in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="5330c-128">The command saves the result in the `$s` variable.</span></span>

<span data-ttu-id="5330c-129">Met de tweede opdracht wordt de `Invoke-AsWorkflow` werk stroom gebruikt om een opdracht uit te voeren `Get-ExecutionPolicy` op de computers in het Servers.csv-bestand.</span><span class="sxs-lookup"><span data-stu-id="5330c-129">The second command uses the `Invoke-AsWorkflow` workflow to run a `Get-ExecutionPolicy` command on the computers in the Servers.csv file.</span></span> <span data-ttu-id="5330c-130">De opdracht gebruikt de para meter **opdrachtnaam** van `Invoke-AsWorkflow`  om de opdracht op te geven die in de werk stroom moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5330c-130">The command uses the **CommandName** parameter of `Invoke-AsWorkflow`  to specify the command to run in the workflow.</span></span> <span data-ttu-id="5330c-131">Hierbij wordt de para `Parameter` meter van gebruikt `Invoke-AsWorkflow` om de `Scope` para meter van de cmdlet op te geven `Get-ExecutionPolicy` met de waarde **process**. De opdracht gebruikt ook de `PSConnectionRetryCount` algemene werk stroom parameter om de opdracht te beperken tot vijf pogingen op elke computer en de `PSComputerName` algemene werk stroom parameter om de namen van de externe knoop punten (doel computers) op te geven.</span><span class="sxs-lookup"><span data-stu-id="5330c-131">It uses the `Parameter` parameter of `Invoke-AsWorkflow` to specify the `Scope` parameter of the `Get-ExecutionPolicy` cmdlet with a value of **Process**.The command also uses the `PSConnectionRetryCount` workflow common parameter to limit the command to five attempts on each computer and the `PSComputerName` workflow common parameter to specify the names of the remote nodes (target computers).</span></span> <span data-ttu-id="5330c-132">De waarde van de `PSComputerName` para meter is een expressie die de `ServerName` eigenschap van elk object in de variabele ophaalt `$s` .</span><span class="sxs-lookup"><span data-stu-id="5330c-132">The value of the `PSComputerName` parameter is an expression that gets the `ServerName` property of every object in the `$s` variable.</span></span>

<span data-ttu-id="5330c-133">Met deze opdrachten wordt een `Get-ExecutionPolicy` opdracht uitgevoerd als werk stroom op honderden computers.</span><span class="sxs-lookup"><span data-stu-id="5330c-133">These commands run a `Get-ExecutionPolicy` command as a workflow on hundreds of computers.</span></span>
<span data-ttu-id="5330c-134">De opdracht gebruikt de `Scope` para meter van de `Get-ExecutionPolicy` cmdlet met een waarde van het **proces** om het uitvoerings beleid in de huidige sessie op te halen.</span><span class="sxs-lookup"><span data-stu-id="5330c-134">The command uses the `Scope` parameter of the `Get-ExecutionPolicy` cmdlet with a value of **Process** to get the execution policy in the current session.</span></span>

### <span data-ttu-id="5330c-135">Voor beeld 3: een expressie als een werk stroom uitvoeren</span><span class="sxs-lookup"><span data-stu-id="5330c-135">Example 3: Run an expression as a workflow</span></span>

```powershell
Invoke-AsWorkflow -Expression "ipconfig /all" -PSComputerName (Get-Content DomainControllers.txt) -AsJob -JobName IPConfig
```

```output
Id     Name          PSJobTypeName   State         HasMoreData   Location                Command
--     ----          -------------   -----         -----------   --------                -------
2      IpConfig      PSWorkflowJob   Completed     True          Server01, Server01...   Invoke-AsWorkflow
```

<span data-ttu-id="5330c-136">Met deze opdracht wordt de `Invoke-AsWorkflow` werk stroom gebruikt om een ipconfig-opdracht uit te voeren als een werk stroom taak op de computers die worden vermeld in het DomainControllers.txt-bestand.</span><span class="sxs-lookup"><span data-stu-id="5330c-136">This command uses the `Invoke-AsWorkflow` workflow to run an Ipconfig command as a workflow job on the computers listed in the DomainControllers.txt file.</span></span>

<span data-ttu-id="5330c-137">De opdracht gebruikt de `Expression` para meter om op te geven welke expressie moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5330c-137">The command uses the `Expression` parameter to specify the expression to run.</span></span>
<span data-ttu-id="5330c-138">Er wordt gebruikgemaakt `PSComputerName` van de algemene werk stroom parameter om de namen van de externe knoop punten (doel computers) op te geven.</span><span class="sxs-lookup"><span data-stu-id="5330c-138">It uses the `PSComputerName` workflow common parameter to specify the names of the remote nodes (target computers).</span></span>

<span data-ttu-id="5330c-139">De opdracht gebruikt ook de `AsJob` `JobName` algemene para meters en werk stroom parameters om de werk stroom uit te voeren als een achtergrond taak op elke computer met de taak naam ' ipconfig '.</span><span class="sxs-lookup"><span data-stu-id="5330c-139">The command also uses the `AsJob` and `JobName` workflow common parameters to run the workflow as a background job on each computer with the "Ipconfig" job name.</span></span>

<span data-ttu-id="5330c-140">De opdracht retourneert een `ContainerParentJob` object ( `System.Management.Automation.ContainerParentJob` ) dat de werk stroom taken op elke computer bevat.</span><span class="sxs-lookup"><span data-stu-id="5330c-140">The command returns a `ContainerParentJob` object (`System.Management.Automation.ContainerParentJob`) that contains the workflow jobs on each computer.</span></span>

## <span data-ttu-id="5330c-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5330c-141">PARAMETERS</span></span>

### <span data-ttu-id="5330c-142">-Opdrachtnaam</span><span class="sxs-lookup"><span data-stu-id="5330c-142">-CommandName</span></span>

<span data-ttu-id="5330c-143">Hiermee wordt de opgegeven cmdlet of geavanceerde functie uitgevoerd als een werk stroom.</span><span class="sxs-lookup"><span data-stu-id="5330c-143">Runs the specified cmdlet or advanced function as a workflow.</span></span>
<span data-ttu-id="5330c-144">Voer de cmdlet of functie naam in, zoals `Update-Help` , `Set-ExecutionPolicy` of `Set-NetFirewallRule` .</span><span class="sxs-lookup"><span data-stu-id="5330c-144">Enter the cmdlet or function name, such as `Update-Help`, `Set-ExecutionPolicy`, or `Set-NetFirewallRule`.</span></span>

```yaml
Type: System.String
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5330c-145">-Expressie</span><span class="sxs-lookup"><span data-stu-id="5330c-145">-Expression</span></span>

<span data-ttu-id="5330c-146">Hiermee geeft u de expressie op die met deze cmdlet wordt uitgevoerd als een werk stroom.</span><span class="sxs-lookup"><span data-stu-id="5330c-146">Specifies the  expression that this cmdlet runs as a workflow.</span></span>
<span data-ttu-id="5330c-147">Voer de expressie in als een teken reeks, zoals `"ipconfig /all"` .</span><span class="sxs-lookup"><span data-stu-id="5330c-147">Enter the expression as a string, such as `"ipconfig /all"`.</span></span>
<span data-ttu-id="5330c-148">Als de expressie spaties of speciale tekens bevat, plaatst u de expressie tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="5330c-148">If the expression includes spaces or special characters, enclose the expression in quotation marks.</span></span>

```yaml
Type: System.String
Parameter Sets: Expression
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5330c-149">-Para meter</span><span class="sxs-lookup"><span data-stu-id="5330c-149">-Parameter</span></span>

<span data-ttu-id="5330c-150">Hiermee geeft u de para meters en parameter waarden op van de opdracht die is opgegeven in de `CommandName` para meter.</span><span class="sxs-lookup"><span data-stu-id="5330c-150">Specifies the parameters and parameter values of the command that is specified in the `CommandName` parameter.</span></span>
<span data-ttu-id="5330c-151">Voer een hash-tabel in waarin elke sleutel een parameter naam is en de waarde ervan de parameter waarde is, bijvoorbeeld `@{ExecutionPolicy="AllSigned"}` .</span><span class="sxs-lookup"><span data-stu-id="5330c-151">Enter a hash table in which each key is a parameter name and its value is the parameter value, such as `@{ExecutionPolicy="AllSigned"}`.</span></span>

<span data-ttu-id="5330c-152">Zie [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)voor meer informatie over hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="5330c-152">For information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5330c-153">-Input object</span><span class="sxs-lookup"><span data-stu-id="5330c-153">-InputObject</span></span>

<span data-ttu-id="5330c-154">Wordt gebruikt om invoer van de pijp lijn toe te staan.</span><span class="sxs-lookup"><span data-stu-id="5330c-154">Used to allows pipeline input.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5330c-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5330c-155">CommonParameters</span></span>

<span data-ttu-id="5330c-156">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5330c-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5330c-157">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5330c-157">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

### <span data-ttu-id="5330c-158">WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="5330c-158">WorkflowCommonParameters</span></span>

<span data-ttu-id="5330c-159">Deze cmdlet ondersteunt ook specifieke algemene para meters voor werk stromen.</span><span class="sxs-lookup"><span data-stu-id="5330c-159">This cmdlet also supports workflow specific common parameters.</span></span>
<span data-ttu-id="5330c-160">Zie [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5330c-160">For information, see [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md).</span></span>

## <span data-ttu-id="5330c-161">INVOER</span><span class="sxs-lookup"><span data-stu-id="5330c-161">INPUTS</span></span>

### <span data-ttu-id="5330c-162">System. object</span><span class="sxs-lookup"><span data-stu-id="5330c-162">System.Object</span></span>

<span data-ttu-id="5330c-163">U kunt elk object door sluizen naar de `InputObject` para meter.</span><span class="sxs-lookup"><span data-stu-id="5330c-163">You can pipe any object to the `InputObject` parameter.</span></span>

## <span data-ttu-id="5330c-164">UITVOER</span><span class="sxs-lookup"><span data-stu-id="5330c-164">OUTPUTS</span></span>

### <span data-ttu-id="5330c-165">Geen</span><span class="sxs-lookup"><span data-stu-id="5330c-165">None</span></span>

<span data-ttu-id="5330c-166">Met deze opdracht wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="5330c-166">This command does not generate any output.</span></span>
<span data-ttu-id="5330c-167">De werk stroom wordt echter wel uitgevoerd, waardoor uitvoer kan worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="5330c-167">However, it runs the workflow, which might generate output.</span></span>

## <span data-ttu-id="5330c-168">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="5330c-168">NOTES</span></span>

## <span data-ttu-id="5330c-169">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="5330c-169">RELATED LINKS</span></span>

[<span data-ttu-id="5330c-170">New-New psworkflowexecutionoption</span><span class="sxs-lookup"><span data-stu-id="5330c-170">New-PSWorkflowExecutionOption</span></span>](../PSWorkflow/New-PSWorkflowExecutionOption.md)

[<span data-ttu-id="5330c-171">New-PSWorkflowSession</span><span class="sxs-lookup"><span data-stu-id="5330c-171">New-PSWorkflowSession</span></span>](../PSWorkflow/New-PSWorkflowSession.md)

[<span data-ttu-id="5330c-172">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="5330c-172">about_Workflows</span></span>](../PSWorkflow/About/about_Workflows.md)

[<span data-ttu-id="5330c-173">about_Workflow_Common_Parameters</span><span class="sxs-lookup"><span data-stu-id="5330c-173">about_Workflow_Common_Parameters</span></span>](../PSWorkflow/About/about_WorkflowCommonParameters.md)
