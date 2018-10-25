# <a name="microsoft-open-source-code-of-conduct"></a>Microsoft Open Source-gedragscode

Dit project onderschrijft de [Microsoft Open Source gedragscode](https://opensource.microsoft.com/codeofconduct/).
Zie voor meer informatie de [Veelgestelde vragen over gedragscode](https://opensource.microsoft.com/codeofconduct/faq/) of neem contact op met [ opencode@microsoft.com ](mailto:opencode@microsoft.com) met aanvullende vragen of opmerkingen.

[![Status maken](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)

## <a name="powershell-documentation"></a>PowerShell-documentatie

Welkom bij de PowerShell-Docs-opslagplaats, behuizing van de officiële PowerShell-documentatie.

## <a name="repository-structure"></a>Structuur van de opslagplaats

Elk van de volgende op het hoogste niveau mappen in deze opslagplaats bevat een DocSet die is gepubliceerd naar [Microsoft-Docs](https://docs.microsoft.com/powershell).

- [/Developer/](https://docs.microsoft.com/powershell/developer/) is de toekomstige start van de PowerShell SDK-documentatie
  - We zijn bezig met het migreren van deze inhoud van MSDN
- [/DSC/](https://docs.microsoft.com/powershell/dsc/) is voor de functie Desired State Configuration
- [/Gallery/](https://docs.microsoft.com/powershell/gallery) is voor de [PowerShell Gallery](https://www.powershellgallery.com/)
- [/jea/](https://docs.microsoft.com/powershell/jea/) is voor de functie Just Enough Administration
- [/Reference/](https://docs.microsoft.com/powershell/scripting/) is bedoeld voor PowerShell conceptuele onderwerpen en -Moduleverwijzing voorkomen in versie 3.0, 4.0, 5.0, 5.1 en 6.0
  - Deze inhoud is ook de bron van de help-inhoud opgehaald door de `Get-Help` cmdlet
- [/WMF](https://docs.microsoft.com/powershell/wmf/readme) bevat opmerkingen bij de release voor de Windows Management Framework, het pakket gebruikt voor het distribueren van nieuwe versies van PowerShell met eerdere versies van Windows.

## <a name="contributing"></a>Bijdragen

Wij mergen actief [pull-requests](https://help.github.com/articles/using-pull-requests/) in de *staging* branch.
Houd er rekening mee dat voordat u een pull-request verzendt, u [akkoord moet gaan met de Contribution License Agreement](https://cla.microsoft.com/) om ervoor te zorgen dat de community gratis gebruik kunt maken van uw bijdragen.

Lees voor meer informatie over bijdragen op onze [gids voor bijdragers](CONTRIBUTING.md). De gids bevat informatie over hoe je bijdraagt aan documentatie, voorgestelde hulpprogramma's, en stijl en indelingsvereisten. Gebruik de Issue- en Pull-requests  sjablonen om documentatie consistent te houden in verschillende versies.

## <a name="licenses"></a>Licenties

Er zijn twee licentiebestanden voor dit project.
De MIT-licentie geldt voor de code die is opgenomen in deze opslagplaats.
Creative Commons-licentie geldt voor de documentatie.
