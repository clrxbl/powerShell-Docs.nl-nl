---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: DSC voor Linux nxEnvironment Resource
ms.openlocfilehash: 3c9f39760e0fba7fac060f29f9e808a3a434401f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189479"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>DSC voor Linux nxEnvironment Resource

De **nxEnvironment** in PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme op voor het beheren van omgevingsvariabelen op een Linux-knooppunt.

## <a name="syntax"></a>Syntaxis

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap |  Beschrijving |
|---|---|
| Naam| Geeft de naam van de omgevingsvariabele waarvoor u wilt om te controleren of een specifieke status.|
| Value| De waarde om toe te wijzen aan de omgevingsvariabele.|
| Zorg ervoor dat| Bepaalt of Controleer of de variabele bestaat. Deze eigenschap instellen op 'Aanwezig' om te controleren of dat de variabele bestaat. Stel deze in op 'Ontbreekt' om te controleren of dat de variabele bestaat niet. De standaardwaarde is 'Aanwezig'.|
| Pad| Hiermee definieert u de variabele die wordt geconfigureerd. Deze eigenschap instellen op **$true** als de variabele de **pad** variabele, anders wordt ingesteld op **$false**. De standaardwaarde is **$false**. Als de variabele die wordt geconfigureerd de **pad** variabele, de waarde wordt opgegeven via de **waarde** eigenschap worden toegevoegd aan de bestaande waarde.|
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Als u meer informatie

* Als **pad** ontbreekt of is ingesteld op **$false**, omgevingsvariabelen worden beheerd in `/etc/environment`. Uw programma's of scripts mogelijk configuratie bron vereist de `/etc/environment` bestand voor toegang tot de beheerde omgevingsvariabelen.
* Als **pad** is ingesteld op **$true**, de omgevingsvariabele wordt beheerd in het bestand `/etc/profile.d/DSCenvironment.sh`. Dit bestand wordt gemaakt als deze niet bestaat. Als **Zorg ervoor dat** is ingesteld op 'Afwezig' en **pad** is ingesteld op **$true**, een bestaande omgevingsvariabele wordt alleen verwijderd uit `/etc/profile.d/DSCenvironment.sh` en niet vanuit andere bestanden.

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet u hoe u de **nxEnvironment** resource ervoor te zorgen dat **TestEnvironmentVariable** aanwezig is en de waarde 'Test-waarde'. Als **TestEnvironmentVariable** is niet aanwezig is, wordt deze gemaakt.

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```