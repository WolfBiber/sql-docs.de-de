---
description: Änderungsnachverfolgung-sys. dm_tran_commit_table
title: sys. dm_tran_commit_table (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_tran_commit_table
- dm_tran_commit_table_TSQL
- sys.dm_tran_commit_table
- sys.dm_tran_commit_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_commit_table dynamic management view
ms.assetid: 732d23c5-1f6c-4e96-bc85-8f29b520cf0e
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4b35493324a0a7585c7f07a11b8dc234048b4e3f
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89537686"
---
# <a name="change-tracking---sysdm_tran_commit_table"></a>Änderungsnachverfolgung-sys. dm_tran_commit_table
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Zeigt eine Zeile für jede Transaktion an, für die von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Änderungsnachverfolgung ein Commit für eine Tabelle ausgeführt wird, die nachverfolgt wird. Die Verwaltungs Sicht sys. dm_tran_commit_table, die für die unter Stütz barkeit bereitgestellt wird und die transaktionsbezogenen Informationen verfügbar macht, die von der Änderungs Nachverfolgung in der sys.syscommittab-Systemtabelle gespeichert werden. Die Tabelle sys.syscommittab ermöglicht eine effiziente persistente Zuordnung zwischen einer datenbankspezifischen Transaktions-ID und den Commit-Protokollfolgenummern (Log Sequence Number, LSN) und den Commit-Timestamps der Transaktion. Die Daten, die in der sys.syscommittab-Tabelle gespeichert und in dieser Verwaltungs Sicht verfügbar gemacht werden, unterliegen der Bereinigung gemäß der Beibehaltungs Dauer, die bei der Konfiguration der Änderungs Nachverfolgung angegeben wurde.  
  
> [!NOTE]  
>  Um dies von oder aus aufzurufen [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , verwenden Sie den Namen **sys. dm_pdw_nodes_tran_commit_table**.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|commit_ts|**bigint**|Eine monoton steigende Zahl, die als datenbankspezifischer Timestamp für jede Transaktion dient, für die ein Commit ausgeführt wurde.|  
|xdes_id|**bigint**|Eine datenbankspezifische interne ID für die Transaktion.|  
|commit_lbn|**bigint**|Die Nummer des Protokollblocks, der den Protokolldatensatz für den Commit der Transaktion enthält.|  
|commit_csn|**bigint**|Die instanzspezifische Commitfolgenummer für die Transaktion.|  
|commit_time|**smalldatetime**|Der Zeitpunkt, zu dem für die Transaktion ein Commit ausgeführt wurde.|  
|pdw_node_id|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] , [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, auf dem sich diese Distribution befindet.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Informationen zur Änderungsnachverfolgung &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-tracking-sql-server.md)  
  
  


