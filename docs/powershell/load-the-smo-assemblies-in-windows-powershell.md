---
title: Laden der SMO-Assemblys in Windows PowerShell | Microsoft-Dokumentation
description: Hier erfahren Sie, wie die SQL Server Management Objects-Assemblys (SMO) in PowerShell-Skripts unter Windows geladen werden, die nicht den SQL Server PowerShell-Anbieter verwenden.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: sql-server-powershell
ms.topic: conceptual
ms.assetid: 8ca42b69-da5a-47f4-9085-34e443f0e389
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 673e94da44cbdd46a8873468b4421a1a8ea4e037
ms.sourcegitcommit: a9f16d7819ed0e2b7ad8f4a7d4d2397437b2bbb2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2020
ms.locfileid: "88714228"
---
# <a name="load-the-smo-assemblies-in-windows-powershell"></a>Laden der SMO-Assemblys in Windows PowerShell
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

In diesem Artikel wird beschrieben, wie die Assemblys von SQL Server Management Objects (SMO) in Windows PowerShell-Skripts geladen werden, die nicht den SQL Server PowerShell-Anbieter verwenden.  
  
> [!NOTE]
> Es gibt zwei SQL Server PowerShell-Module: **SqlServer** und **SQLPS**. Das **SQLPS**-Modul ist zwar in der SQL Server-Installation (für die Abwärtskompatibilität) enthalten, wird jedoch nicht mehr aktualisiert. Das **SqlServer**-Modul ist das aktuellste PowerShell-Modul. Das **SqlServer**-Modul enthält aktualisierte Versionen der Cmdlets in **SQLPS** sowie neue Cmdlets zur Unterstützung der neuesten SQL-Funktionen.  
> Vorherige Versionen des **SqlServer**-Moduls *waren* in SQL Server Management Studio (SSMS) enthalten, allerdings nur in den Versionen 16.x. Das **SqlServer**-Modul muss über den PowerShell-Katalog installiert werden, damit PowerShell mit SSMS 17.0 und höher verwendet werden kann.
> Informationen zur Installation des **SqlServer**-Moduls finden Sie unter [Installieren von SQL Server PowerShell](download-sql-server-ps-module.md).


Der bevorzugte Mechanismus zum Laden der SMO-Assemblys besteht im Laden des **SqlServer**-Moduls. Der im Modul enthaltene [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anbieter lädt die SMO-Assemblys automatisch und implementiert außerdem Funktionen, die die Nützlichkeit der SMO-Objekte in PowerShell-Skripts erweitern.
  
In zwei Szenarien müssen die SMO-Assemblys direkt geladen werden:  
  
-   Das Skript verweist vor dem ersten Befehl, der auf den Anbieter oder die Cmdlets der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Snap-Ins verweist, auf ein SMO-Objekt.  
  
-   Sie möchten SMO-Code portieren, der in einer anderen Sprache geschrieben wurde, die weder den Anbieter noch Cmdlets verwendet (z. B. C# oder Visual Basic).  
  
## <a name="example-loading-the-sql-server-management-objects"></a>Beispiel: Laden von SQL Server Management Objects  
 Mit folgendem Code werden die SMO-Assemblys geladen:  
  
```  
#  
# Loads the SQL Server Management Objects (SMO)  
#  
  
$ErrorActionPreference = "Stop"  
  
$sqlpsreg="HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.SqlServer.Management.PowerShell.sqlps"  
  
if (Get-ChildItem $sqlpsreg -ErrorAction "SilentlyContinue")  
{  
    throw "SQL Server Provider for Windows PowerShell is not installed."  
}  
else  
{  
    $item = Get-ItemProperty $sqlpsreg  
    $sqlpsPath = [System.IO.Path]::GetDirectoryName($item.Path)  
}  
  
$assemblylist =   
"Microsoft.SqlServer.Management.Common",  
"Microsoft.SqlServer.Smo",  
"Microsoft.SqlServer.Dmf ",  
"Microsoft.SqlServer.Instapi ",  
"Microsoft.SqlServer.SqlWmiManagement ",  
"Microsoft.SqlServer.ConnectionInfo ",  
"Microsoft.SqlServer.SmoExtended ",  
"Microsoft.SqlServer.SqlTDiagM ",  
"Microsoft.SqlServer.SString ",  
"Microsoft.SqlServer.Management.RegisteredServers ",  
"Microsoft.SqlServer.Management.Sdk.Sfc ",  
"Microsoft.SqlServer.SqlEnum ",  
"Microsoft.SqlServer.RegSvrEnum ",  
"Microsoft.SqlServer.WmiEnum ",  
"Microsoft.SqlServer.ServiceBrokerEnum ",  
"Microsoft.SqlServer.ConnectionInfoExtended ",  
"Microsoft.SqlServer.Management.Collector ",  
"Microsoft.SqlServer.Management.CollectorEnum",  
"Microsoft.SqlServer.Management.Dac",  
"Microsoft.SqlServer.Management.DacEnum",  
"Microsoft.SqlServer.Management.Utility"  
  
foreach ($asm in $assemblylist)  
{  
    $asm = [Reflection.Assembly]::LoadWithPartialName($asm)  
}  
  
Push-Location  
cd $sqlpsPath  
update-FormatData -prependpath SQLProvider.Format.ps1xml   
Pop-Location  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-PowerShell](sql-server-powershell.md)  
  
  
