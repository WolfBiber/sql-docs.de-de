---
title: Migrieren von Sybase ASE-Datenbanken zu SQL Server Azure SQL-Datenbank | Microsoft-Dokumentation
description: Verwenden Sie diesen empfohlenen Vorgang, um SAP Adaptive Server Enterprise-Datenbanken mithilfe von SQL Server Migration Assistant (SSMA) zu SQL Server oder Azure SQL-Datenbank zu migrieren.
ms.custom: ''
ms.date: 11/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ed7952d4-8331-44d7-bccf-3440e17238b2
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: e0a938d615b15dc7b280a6c6b9337a546e0059bf
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87934679"
---
# <a name="migrating-sap-ase-databases-to-sql-server---azure-sql-database-sybasetosql"></a>Migrieren von SAP ASE-Datenbanken zu SQL Server Azure SQL-Datenbank (sybaseto SQL)
SQL Server Migration Assistant (SSMA) für SAP Adaptive Server Enterprise (ASE) ist eine umfassende Umgebung, die Sie bei der schnellen Migration von SAP ASE-Datenbanken zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank unterstützt. Mithilfe von SSMA für SAP ASE können Sie Datenbankobjekte und-Daten überprüfen, Datenbanken für die Migration bewerten, Datenbankobjekte zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank migrieren und dann Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank migrieren.  
  
## <a name="recommended-migration-process"></a>Empfohlener Migrationsprozess  
Verwenden Sie den folgenden Prozess, um Objekte und Daten aus SAP ASE-Datenbanken zu oder Azure SQL-Datenbank erfolgreich zu migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
1.  [Erstellen Sie ein neues SSMA-Projekt](working-with-ssma-projects-sybasetosql.md).  
  
    Nachdem Sie das Projekt erstellt haben, können Sie die Optionen für die Projekt Konvertierung, die Migration und die Typzuordnung festlegen. Weitere Informationen zu Projekteinstellungen finden Sie unter [Festlegen von Projektoptionen &#40;sybaseto SQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md). Weitere Informationen zum Anpassen von Datentyp Zuordnungen finden Sie unterzuordnen von [Sybase-ASE und SQL Server-Datentypen &#40;sybasetosql&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
2.  Stellen [Sie eine Verbindung zum SAP ASE-Datenbankserver](connecting-to-sybase-ase-sybasetosql.md)her  
  
3.  Stellen [Sie eine Verbindung mit einer Instanz SQL Server](connecting-to-sql-server-sybasetosql.md) , oder stellen [Sie eine Verbindung mit einer Instanz von Azure SQL-Datenbank](connecting-to-azure-sql-db-sybasetosql.md)  
  
4.  Ordnen [Sie SAP ASE-Datenbankschemas SQL Server/Azure SQL-Datenbank-Datenbankschemas zu](https://msdn.microsoft.com/2c927003-c49d-4fe1-8e3e-5b2899166268).  
  
5.  Erstellen Sie optional [Bewertungsberichte](assessing-sybase-ase-database-objects-for-conversion-sybasetosql.md) , um die Datenbankobjekte zu konvertieren und die Konvertierungs Zeit einzuschätzen.  
  
6.  [Konvertieren von SAP ASE-Datenbankschemas in SQL Server/Azure SQL-Datenbankschemas](https://msdn.microsoft.com/509cb65d-2f54-427a-83d7-37919cc4e3e3).  
  
7.  [Laden Sie die konvertierten Datenbankobjekte in SQL Server/Azure SQL-Datenbank](https://msdn.microsoft.com/4c59256f-99a8-4351-9559-a455813dbd06).  
  
    Speichern Sie ein Skript, und führen Sie es in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank aus, oder synchronisieren Sie die Datenbankobjekte.  
  
8.  [Migrieren von Daten zu SQL Server/Azure SQL-Datenbank](https://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811).  
  
9. Aktualisieren Sie ggf. die Datenbankanwendungen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA für SAP ASE &#40;sybasedesql&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
[Informationen zu den ersten Schritten mit SSMA für SAP ASE &#40;sybaseto SQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)  
  
