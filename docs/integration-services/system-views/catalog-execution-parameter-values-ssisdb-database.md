---
description: catalog.execution_parameter_values (SSISDB-Datenbank)
title: catalog.execution_parameter_values (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: ec93e67b-04ce-4aae-ab96-3ad20e9793ad
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 022d1d29438da9bebeb7e7544b01445f27803fce
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88495217"
---
# <a name="catalogexecution_parameter_values-ssisdb-database"></a>catalog.execution_parameter_values (SSISDB-Datenbank)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Zeigt die tatsächlichen Parameterwerte an, die von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paketen während einer Instanz der Ausführung verwendet werden.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|execution_parameter_id|**bigint**|Eindeutiger Bezeichner (ID) des Ausführungsparameters.|  
|execution_id|**bigint**|Eindeutige ID für die Instanz der Ausführung.|  
|object_type|**smallint**|Wenn der Wert `20`ist, ist der Parameter ein Projektparameter. Wenn der Wert `30`ist, ist der Parameter ein Paketparameter. Wenn der Wert `50` ist, entspricht der Parameter einem der folgenden Werte:<br /><br /> **LOGGING_LEVEL**<br /><br /> **DUMP_ON_ERROR**<br /><br /> **DUMP_ON_EVENT**<br /><br /> **DUMP_EVENT_CODE**<br /><br /> **CALLER_INFO**<br /><br /> **SYNCHRONIZED**|  
|parameter_data_type|**nvarchar(128)**|Der Datentyp des Parameters.|  
|parameter_name|**sysname**|Der Name des Parameters.|  
|parameter_value|**sql_variant**|Der Wert des Parameters. Wenn `0` vertraulich ist, wird der Nur-Text-Wert angezeigt. Wenn `1` vertraulich ist, wird der Wert **NULL** angezeigt.|  
|sensitive|**bit**|Wenn der Wert `1`lautet, ist der Parameterwert vertraulich. Wenn der Wert `0`lautet, ist der Parameterwert nicht vertraulich.|  
|Erforderlich|**bit**|Wenn der Wert `1`lautet, ist der Parameterwert erforderlich, um die Ausführung zu starten. Wenn der Wert `0`lautet, ist der Parameterwert nicht erforderlich, um die Ausführung zu starten.|  
|value_set|**bit**|Wenn der Wert `1`ist, wurde der Parameterwert zugewiesen. Wenn der Wert `0`ist, wurde der Parameterwert nicht zugewiesen.|  
|runtime_override|**bit**|Wenn der Wert `1`ist, wurde der ursprüngliche Parameterwert geändert, bevor die Ausführung gestartet wurde. Wenn der Wert `0`lautet, ist der Parameterwert der ursprünglich festgelegte Wert.|  
  
## <a name="remarks"></a>Bemerkungen  
 In dieser Sicht wird eine Zeile für jeden Ausführungsparameter im Katalog angezeigt. Ein Ausführungsparameterwert ist der Wert, der einem Projektparameter oder Paketparameter während einer einzelnen Instanz der Ausführung zugewiesen wird.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für die Instanz der Ausführung  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
> [!NOTE]  
>  Wenn Sie über die Berechtigung verfügen, einen Vorgang auf dem Server auszuführen, verfügen Sie auch über die Berechtigung, Informationen zu dem Vorgang anzuzeigen. Sicherheit auf Zeilenebene wird erzwungen. Es werden nur Zeilen angezeigt, zu deren Anzeige Sie berechtigt sind.  
  
  
