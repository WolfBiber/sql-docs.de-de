---
description: sys.database_usage (Azure SQL-Datenbank)
title: sys. database_usage (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- database_usage
- database_usage_TSQL
- sys.database_usage_TSQL
- sys.database_usage
dev_langs:
- TSQL
helpviewer_keywords:
- database_usage
- sys.database_usage
ms.assetid: be6820de-60bf-4ddd-ace7-4077893d630f
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: c72973c21b2e660667b2bed31d771f3ce19c43b4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88455263"
---
# <a name="sysdatabase_usage-azure-sql-database"></a>sys.database_usage (Azure SQL-Datenbank)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  **Hinweis: Dies gilt nur für Azure SQL-Datenbank v11.**  
  
 Listet die Anzahl, den Typ und die Dauer der Datenbanken auf dem [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Server auf.  
  
 Die **sys. database_usage** -Sicht enthält die folgenden Spalten.  
  
|Spaltenname|Beschreibung|  
|-----------------|-----------------|  
|time|Das Datum, an dem die Verwendungsereignisse eingetreten sind.|  
|sku|Der Typ der Dienst Ebene für die Datenbank: **Web**, **Business**, **Basic**, **Standard**, **Premium**|  
|quantity|Die maximale Anzahl von Datenbanken eines SKU-Typs, der an diesem Tag vorhanden war.|  
  
## <a name="permissions"></a>Berechtigungen  
 Der schreibgeschützte Zugriff auf diese Ansicht ist für alle Benutzer verfügbar, die über Berechtigungen zum Herstellen einer Verbindung mit der **Master** -Datenbank verfügen.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **sys. database_usage** -Sicht gibt eine Zeile für jeden Tag Ihres Abonnements zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Preis Details zur SQL-Datenbank](https://go.microsoft.com/fwlink/?LinkID=394978)   
 [Konten und Abrechnung in der Azure SQL-Datenbank](https://msdn.microsoft.com/library/windowsazure/ee621788.aspx)  
  
  
