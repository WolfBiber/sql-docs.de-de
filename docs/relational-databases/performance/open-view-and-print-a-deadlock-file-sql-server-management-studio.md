---
title: Öffnen, Anzeigen und Drucken einer Deadlockdatei (SSMS)
description: Erfahren Sie, wie Sie Deadlockinformationen erfassen, die SQL Server Profiler generiert, und sie in SQL Server Management Studio anzeigen.
ms.custom: seo-dt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], printing files
- deadlocks [SQL Server], opening files
- opening deadlock files
- printing deadlock files
ms.assetid: 5061b13f-2cb7-457a-b8d0-fbd437b510ab
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3c55ad170e9d6a9fe58865ab28ac75f018b6905b
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458433"
---
# <a name="open-view-and-print-a-deadlock-file-in-sql-server-management-studio-ssms"></a>Öffnen, Anzeigen und Drucken einer Deadlockdatei in SQL Server Management Studio (SSMS)

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Wenn von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ein Deadlock generiert wird, können Sie die entsprechenden Informationen in einer Datei speichern. Nach dem Speichern können Sie die Deadlockdatei zum Anzeigen oder Drucken in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] öffnen.  
  
## <a name="open-and-view-a-deadlock-file"></a>Öffnen und Anzeigen einer Deadlockdatei  
  
1. Zeigen Sie im Menü **Datei** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] auf **Öffnen**, und wählen Sie dann **Datei** aus.  
  
2. Wählen Sie im Dialogfeld **Datei öffnen** den Dateityp XDL im Feld **Dateityp** aus. Sie erhalten damit eine gefilterte Liste, die nur aus Deadlockdateien besteht.  
  
## <a name="print-a-deadlock-file"></a>Drucken einer Deadlockdatei  
  
1. Zeigen Sie im Menü **Datei** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] auf **Öffnen**, und wählen Sie dann **Datei** aus.  
  
2. Wählen Sie im Dialogfeld **Datei öffnen** den Dateityp XDL im Feld **Dateityp** aus. Sie erhalten damit eine gefilterte Liste, die nur aus Deadlockdateien besteht.  
  
3. Wählen Sie die zu druckende Deadlockdatei und dann **Öffnen** aus.  
  
4. Wählen Sie im Menü **Datei** die Option **Drucken** aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Speichern von Deadlockdiagrammen &#40;SQL Server Profiler&#41;](../../relational-databases/performance/save-deadlock-graphs-sql-server-profiler.md)  
  
  
