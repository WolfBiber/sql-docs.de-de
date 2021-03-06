---
description: MSmerge_settingshistory (Transact-SQL)
title: MSmerge_settingshistory (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_settingshistory
- MSmerge_settingshistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_settingshistory system table
ms.assetid: 0bdf2d5f-5502-44cd-aa9d-2d5006ad20ce
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 841f2986d09bd048f857e45a8bde3c5db6d0fc70
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545600"
---
# <a name="msmerge_settingshistory-transact-sql"></a>MSmerge_settingshistory (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **MSmerge_settingshistory** Tabelle wird verwendet, um den Verlauf der Änderungen an Artikel-und Veröffentlichungs Eigenschaften für die Mergereplikation beizubehalten, wobei eine Zeile für jede Änderung an einer Mergereplikationstopologie vorgenommen wird. In dieser Tabelle werden auch Informationen zu dem Zeitpunkt gespeichert, zu dem die ursprünglichen Eigenschaftseinstellungen vorgenommen wurden. Diese Tabelle wird in der Veröffentlichungs- und in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**EventTime**|**datetime**|Die Uhrzeit, zu der das Ereignis aufgetreten ist|  
|**pubid**|**uniqueidentifier**|Die eindeutige ID für eine bestimmte Veröffentlichung|  
|**artid**|**uniqueidentifier**|Die eindeutige ID des angegebenen Artikels.|  
|**EventType**|**tinyint**|Gibt den Ereignistyp an, der aufgezeichnet wird. Es kann einer der folgenden Typen sein:<br /><br /> **1** -anfängliche Eigenschafts Einstellung auf Veröffentlichungs Ebene.<br /><br /> **2** : Ändern Sie eine Veröffentlichungs Eigenschaft.<br /><br /> **101** -ursprüngliche Artikel Eigenschafts Einstellung.<br /><br /> **102** -ändern Sie eine Artikel Eigenschaft.|  
|**propertyname**|**sysname**|Der Name der festgelegten oder geänderten Eigenschaft|  
|**previousvalue**|**sysname**|Der vorhergehende Eigenschaftswert, falls eine Eigenschaft geändert wurde|  
|**NewValue**|**sysname**|Der Wert, zu dem die Eigenschaft geändert oder mit dem die Eigenschaft erstellt wurde|  
|**eventtext**|**nvarchar (2000)**|Die Zeichenfolge, die das Ereignis beschreibt|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
