---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Implementeren naar Azure Automation
ms.openlocfilehash: ced67809387a85e089259edf6b091d68e58ba6a7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="deploy-to-azure-automation"></a>Implementeren naar Azure Automation

De implementeren in Azure Automation-knop op de detailpagina item implementeert het item uit de galerie PowerShell voor Azure Automation.

![Implementeren in Azure Automation-knop](../../Images/DeployToAzureAutomationButton.png)

Wanneer u klikt, wordt deze omgeleid naar de Azure-beheerportal, waar u zich aanmelden met de referenties van uw Azure-account.
Als het item afhankelijkheden bevat, wordt alle afhankelijkheden geïmplementeerd voor Azure Automation ook.

> [!WARNING]
> Als het artikel en de versie nog in uw Automation-account bestaat, overschrijft opnieuw implementeren van de PowerShell Gallery het item in uw Automation-account.

Als u een module implementeert, wordt deze weergegeven in de sectie Modules van Azure Automation.  Als u een script implementeert, wordt deze weergegeven in de sectie Runbooks van Azure Automation.

De implementeren in Azure Automation-knop kan worden uitgeschakeld door de tag AzureAutomationNotSupported toe te voegen aan de itemmetagegevens.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Acceptatie van de licentie vereisen bij implementeren naar Azure Automation

Als de module wordt geïmplementeerd op Azure Automation acceptatie van de licentie vereist, gebruikersinterface portal een disclaimer met de melding wordt weergegeven, deze module acceptatie van de licentie is vereist. Op OK klikt, u kunt de licentievoorwaarden accepteren.'

![Implementeren in Azure Automation acceptatie van de licentie is vereist](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>meer informatie

- [Acceptatie van de licentie in PowerShellGet vereisen](../../concepts/module-license-acceptance.md)
- [Vereisen dat gebruikers van de licentie in PowerShell Gallery](items-that-require-license-acceptance.md)
- [Azure Automation-website](http://azure.microsoft.com/services/automation/)