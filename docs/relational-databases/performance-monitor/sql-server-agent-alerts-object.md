---
title: SQL Server-Agent, Alerts-Objekt | Microsoft-Dokumentation
description: Hier lernen Sie das Leistungsobjekt „SQL Server-Agent-Warnungen“ kennen, das Leistungsindikatoren enthält, die Informationen über SQL Server-Agent-Warnungen melden.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Alerts object
- SQLAgent:Alerts
ms.assetid: e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 9fe293b70b074322380dc55f4294971908c106ee
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2020
ms.locfileid: "86457464"
---
# <a name="sql-server-agent-alerts-object"></a>SQL Server-Agent, Warnungen-Objekt
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Das Leistungsobjekt **Warnungen** des SQL Server-Agents enthält Leistungsindikatoren mit Informationen über SQL Server-Agent-Warnungen. In der nachfolgenden Tabelle sind die in diesem Objekt enthaltenen Indikatoren aufgelistet.  
  
 Die folgende Tabelle enthält die Leistungsindikatoren **SQLAgent:Warnungen** .  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|**Aktivierte Warnungen**|Dieser Leistungsindikator berichtet die Gesamtanzahl der Warnungen, die der SQL Server-Agent seit dem letzten Neustart aktiviert hat.|  
|**Aktivierte Warnungen/Minute**|Dieser Leistungsindikator berichtet die Anzahl der Warnungen, die der SQL Server-Agent innerhalb der letzten Minute aktiviert hat.|  
  
> [!NOTE]  
>  Um dieses SQL Server-Agent-Objekt verwenden zu können, muss der Benutzer ein Mitglied der festen Serverrolle **sysadmin** sein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Warnungen](../../ssms/agent/alerts.md)   
 [Verwenden von Leistungsobjekten](../../ssms/agent/use-performance-objects.md)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
