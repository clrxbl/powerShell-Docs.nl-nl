---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Update ModuleManifest
ms.openlocfilehash: ce3f6f173535d98648eb51adb1dbf84764e4f434
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="update-modulemanifest"></a>Update ModuleManifest
Updates van een manifestbestand van de module.

## <a name="description"></a>Beschrijving

Een module-manifest (.psd1)-bestand wordt bijgewerkt door de cmdlet Update-ModuleManifest.

### <a name="notes"></a>Opmerkingen
    - DscResourcesToExport wordt alleen ondersteund op de meest recente versie 5.0-PowerShell. We niet mogelijk om te werken van het veld als u op een lagere versie van PowerShell uitvoert.

## <a name="cmdlet-syntax"></a>De syntaxis van cmdlet
```powershell
Get-Command -Name Update-ModuleManifest -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Verwijzing naar het online help van cmdlet

[Update ModuleManifest](http://go.microsoft.com/fwlink/?LinkId=619311)

## <a name="example-commands"></a>Voorbeeldopdrachten

Deze nieuwe cmdlet wordt gebruikt om te manifestbestand met invoer eigenschapswaarden update. Het duurt alle parameters die nieuw ModuleManifest biedt.

We merken dat veel van de module auteurs wilt opgeven '\*' in de geëxporteerde waarden zoals FunctionsToExport, CmdletsToExport, enz. Tijdens de publicatie van de module voor PowerShell Gallery, niet-opgegeven functies en opdrachten niet ingevuld correct naar de galerie. Daarom raden we module auteurs update hun manifesten met de juiste waarden.

Als u hebt de modules die eigenschappen hebt geëxporteerd, vult Update ModuleManifest in het opgegeven manifestbestand met gegevens van geëxporteerde functies, -cmdlets, variabelen enzovoort:
```powershell
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'

#(Other properties removed here for Simplicity…)

# Functions to export from this module
FunctionsToExport = '*'
# Cmdlets to export from this module
CmdletsToExport = '*'
# Variables to export from this module
VariablesToExport = '*'
# Aliases to export from this module
AliasesToExport = '*'
}
```

Na de Update-ModuleManifest:
```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
#
# Module manifest for module 'NewManifest'
#
# Generated by: author name
#
# Generated on: 11/13/2015
#
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'
# Functions to export from this module
FunctionsToExport = 'Get-FooFn Get-FooWF'
# Cmdlets to export from this module
CmdletsToExport = 'Test-PSGetTestCmdlet'
}
```

Voor elke module er zijn ook metagegevensvelden gekoppeld. Om metagegevens correct weergegeven op PowrShell galerie, kunt u Update ModuleManifest onder PrivateData deze velden te vullen.

```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1" -Tags "Tag1" -LicenseUri "http://license.com" -ProjectUri "http://project.com" -IconUri "http://icon.com" -ReleaseNotes "Test module"
```

PrivateData hashtabel van de sjabloon manifestbestand heeft de volgende eigenschappen

```powershell
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''
    
        # A URL to the main website for this project.
        # ProjectUri = ''
        
        # A URL to an icon representing this module.
        # IconUri = ''
        
        # ReleaseNotes of this module
        # ReleaseNotes = ''
        
        # External dependent modules of this module
        # ExternalModuleDependencies = ''
    } # End of PSData hashtable
} # End of PrivateData hashtable
```
