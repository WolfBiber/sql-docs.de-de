---
description: sys. workload_management_workload_classifiers (Transact-SQL)
title: sys. workload_management_workload_classifiers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/05/2019
ms.prod: sql
ms.technology: system-objects
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: eae75e8580a1a8333574aceabe8be5581ff3087e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88475107"
---
# <a name="sysworkload_management_workload_classifiers-transact-sql"></a>sys. workload_management_workload_classifiers (Transact-SQL)

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

 Gibt Details zu workloaderklassifizierern zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|Eindeutige ID des Klassifizierers. Lässt keine NULL-Werte zu.||
group_name|**sysname**|Der Name der Arbeits Auslastungs Gruppe, der der Klassifizierer zugewiesen ist. Lässt keine NULL-Werte zu. Joinfähig mit sys. workload_management_workload_groups ||
name|**sysname**|Der Name des Klassifizierers. Muss für die-Instanz eindeutig sein. Lässt keine NULL-Werte zu.||
|importance|**sysname**|Die relative Wichtigkeit einer Anforderung in dieser Arbeits Auslastungs Gruppe und zwischen Arbeits Auslastungs Gruppen für freigegebene Ressourcen.  Die in der Klassifizierung angegebene Wichtigkeit überschreibt die Wichtigkeits Einstellung der Arbeits Auslastungs Gruppe. Lässt NULL-Werte zu.  Bei Null wird die Einstellung für die Arbeits Auslastungs Gruppen Wichtigkeit verwendet.|niedrig, below_normal, normal (Standard), above_normal, hoch |
|create_time|**datetime**|Uhrzeit, zu der der Klassifizierer erstellt wurde. Lässt keine NULL-Werte zu.||
modify_time|**datetime**|Uhrzeit, zu der die Klassifizierung zuletzt geändert wurde. Lässt keine NULL-Werte zu.||
is_enabled|**bit**|INTERNAL||
|&nbsp;||||
  
## <a name="permissions"></a>Berechtigungen

Erfordert die VIEW SERVER STATE-Berechtigung.

## <a name="next-steps"></a>Nächste Schritte

 Eine Liste aller Katalog Sichten für SQL Data Warehouse und parallele Data Warehouse finden Sie unter [SQL Data Warehouse und parallele Data Warehouse Katalog Sichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md). Informationen zum Erstellen eines workloadklassifizierers finden Sie unter CREATE worklofier [Classifier](../../t-sql/statements/create-workload-classifier-transact-sql.md) Weitere Informationen zur Klassifizierung der Arbeitsauslastung finden [Workload Classification](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification) Sie unter workloadklassifizierung.
