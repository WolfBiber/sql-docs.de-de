---
description: sys.dm_exec_cursors (Transact-SQL)
title: sys. dm_exec_cursors (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_cursors_TSQL
- dm_exec_cursors
- dm_exec_cursors_TSQL
- sys.dm_exec_cursors
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_cursors dynamic management function
ms.assetid: f520b63c-36af-40f1-bf71-6901d6331d3d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 351f97ed08d1a6a79f8611d19842dc93138277ce
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543931"
---
# <a name="sysdm_exec_cursors-transact-sql"></a>sys.dm_exec_cursors (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen über die Cursor zurück, die in verschiedenen Datenbanken geöffnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dm_exec_cursors (session_id | 0 )  
```  
  
## <a name="arguments"></a>Argumente  
 *session_id* | 0  
 ID der Sitzung. Wenn *session_id* angegeben wird, gibt diese Funktion Informationen zu Cursorn in der angegebenen Sitzung zurück.  
  
 Wenn 0 angegeben wird, gibt diese Funktion Informationen zu allen Cursorn für alle Sitzungen zurück.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|ID der Sitzung, die diesen Cursor enthält.|  
|**cursor_id**|**int**|ID des Cursorobjekts.|  
|**name**|**nvarchar(256)**|Name des Cursors gemäß der Definition durch den Benutzer.|  
|**properties**|**nvarchar(256)**|Gibt die Eigenschaften des Cursors an. Die Werte der folgenden Eigenschaften werden zu einem Wert dieser Spalte verkettet:<br />Deklarationsschnittstelle<br />Cursortyp <br />Cursorparallelität<br />Cursorbereich<br />Cursorschachtelungsebene<br /><br /> Beispielsweise kann der Wert, der in dieser Spalte zurückgegeben wird, "TSQL &#124; Dynamic &#124;-optimistische &#124; Global (0)" lauten.|  
|**sql_handle**|**varbinary(64)**|Handle zum Text des Batches, durch den der Cursor deklariert wurde.|  
|**statement_start_offset**|**int**|Anzahl von Zeichen im derzeit ausgeführten Batch oder in der derzeit ausgeführten gespeicherten Prozedur, an der die derzeit ausgeführte Anweisung beginnt. Kann in Verbindung mit dem **sql_handle**, dem **statement_end_offset**und der dynamischen Verwaltungsfunktion [sys. dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md) verwendet werden, um die derzeit ausgeführte Anweisung für die Anforderung abzurufen.|  
|**statement_end_offset**|**int**|Anzahl von Zeichen im derzeit ausgeführten Batch oder in der derzeit ausgeführten gespeicherten Prozedur, an der die derzeit ausgeführte Anweisung endet. Kann zusammen mit **sql_handle**, **statement_start_offset**und der dynamischen Verwaltungsfunktion **sys.dm_exec_sql_text** zum Abrufen der zurzeit ausgeführten Anweisung für die Anforderung verwendet werden.|  
|**plan_generation_num**|**bigint**|Eine Sequenznummer, anhand der nach einer Neukompilierung zwischen einzelnen Instanzen von Plänen unterschieden werden kann.|  
|**creation_time**|**datetime**|Der Timestamp, wann dieser Cursor erstellt wurde.|  
|**is_open**|**bit**|Gibt an, ob der Cursor geöffnet ist.|  
|**is_async_population**|**bit**|Gibt an, ob der Hintergrundthread weiterhin einen KEYSET- oder STATIC-Cursor asynchron auffüllt.|  
|**is_close_on_commit**|**bit**|Gibt an, ob der Cursor mithilfe von CURSOR_CLOSE_ON_COMMIT deklariert wurde.<br /><br /> 1 = Cursor wird geschlossen, wenn die Transaktion endet.|  
|**fetch_status**|**int**|Gibt den letzten Abrufstatus des Cursors zurück. Dies ist der letzte zurückgegebene @ @FETCH_STATUS value.|  
|**fetch_buffer_size**|**int**|Gibt Informationen zur Größe des Fetchpuffers zurück.<br /><br /> 1 = Transact-SQL-Cursor. Für API-Cursor kann ein höherer Wert festgelegt werden.|  
|**fetch_buffer_start**|**int**|Für FAST_FORWARD- und DYNAMIC-Cursor wird 0 zurückgegeben, falls der Cursor nicht geöffnet ist oder falls er vor der ersten Zeile positioniert ist. Andernfalls wird –1 zurückgegeben.<br /><br /> Für STATIC- und KEYSET-Cursor wird 0 zurückgegeben, falls der Cursor nicht geöffnet ist, und -1, falls der Cursor nach der letzten Zeile positioniert ist.<br /><br /> Andernfalls wird die Zeilennummer zurückgegeben, in der der Cursor positioniert ist.|  
|**ansi_position**|**int**|Cursorposition innerhalb des Fetchpuffers.|  
|**worker_time**|**bigint**|Der Zeitaufwand in Mikrosekunden zum Ausführen dieses Cursors durch den Arbeitsthread.|  
|**falsch**|**bigint**|Anzahl von Lesevorgängen, die der Cursor ausgeführt hat.|  
|**AF**|**bigint**|Anzahl von Schreibvorgängen, die der Cursor ausgeführt hat.|  
|**dormant_duration**|**bigint**|Millisekunden seit dem Start der letzten Abfrage (Öffnen oder Abrufen) für diesen Cursor.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="remarks"></a>Hinweise  
 Die folgende Tabelle stellt Informationen zur Cursordeklarationsschnittstelle bereit und enthält die möglichen Werte für die Eigenschaftenspalte.  
  
|Eigenschaft|BESCHREIBUNG|  
|--------------|-----------------|  
|API|Cursor wurde mithilfe einer der Datenzugriffs-APIs (ODBC, OLE DB) deklariert.|  
|TSQL|Cursor wurde mithilfe der DECLARE CURSOR-Syntax von Transact-SQL deklariert.|  
  
 Die folgende Tabelle stellt Informationen zum Cursortyp bereit und enthält die möglichen Werte für die Eigenschaftenspalte.  
  
|type|BESCHREIBUNG|  
|----------|-----------------|  
|Keyset|Cursor wurde als Keyset deklariert.|  
|Dynamisch|Cursor wurde als dynamisch deklariert.|  
|Momentaufnahme|Cursor wurde als Momentaufnahme oder statisch deklariert.|  
|Fast_Forward|Cursor wurde als Vorwärtscursor deklariert.|  
  
 Die folgende Tabelle stellt Informationen zur Cursorparallelität bereit und enthält die möglichen Werte für die Eigenschaftenspalte.  
  
|Parallelität|BESCHREIBUNG|  
|-----------------|-----------------|  
|Nur Leseberechtigung|Cursor wurde als schreibgeschützt deklariert.|  
|Scroll Locks|Cursor verwendet Scrollsperren.|  
|Optimistisch|Cursor verwendet die Steuerung durch vollständige Parallelität.|  
  
 Die folgende Tabelle stellt Informationen zum Cursorbereich bereit und enthält die möglichen Werte für die Eigenschaftenspalte.  
  
|Bereich|BESCHREIBUNG|  
|-----------|-----------------|  
|Lokal|Gibt an, dass der Gültigkeitsbereich des Cursors lokal zu dem Batch, der gespeicherten Prozedur oder dem Trigger ist, in dem bzw. in der er erstellt wurde.|  
|Global|Gibt an, dass der Bereich des Cursors global zur Verbindung ist.|  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-detecting-old-cursors"></a>A. Erkennen von alten Cursorn  
 Dieses Beispiel gibt Informationen zu Cursorn zurück, die auf dem Server länger als über den angegebenen Zeitraum von 36 Stunden hinweg geöffnet waren.  
  
```  
SELECT creation_time, cursor_id, name, c.session_id, login_name   
FROM sys.dm_exec_cursors(0) AS c   
JOIN sys.dm_exec_sessions AS s ON c.session_id = s.session_id   
WHERE DATEDIFF(hh, c.creation_time, GETDATE()) > 36;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungs Sichten und-Funktionen im Zusammenhang mit der Ausführung &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
  

