---
title: Überwachen von SQL Server-Komponenten | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mittels Überwachung Leistungstrends identifizieren können. SQL Server stellt einen Dienst in einer dynamischen Umgebung bereit, sodass im Laufe der Zeit möglicherweise Änderungen erforderlich werden.
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: e8f1b16b-ea40-4e12-886c-967ebda4e6e4
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 70fe75b97181815246d03de588bdd6d45af3ce9f
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458384"
---
# <a name="monitor-sql-server-components"></a>Überwachen von SQL Server-Komponenten
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Die Überwachung ist wichtig, da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Dienst in einer dynamischen Umgebung bereitstellt. Die Daten in der Anwendung ändern sich. Die Art des Zugriffs, den Benutzer benötigen, ändert sich. Die Art der Verbindungsherstellung ändert sich. Möglicherweise ändern sich sogar die Typen der Anwendungen, die auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifen, aber [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwaltet automatisch Ressourcen auf Systemebene, z.B. Arbeits- oder Datenträgerspeicher, um den Bedarf an manueller Optimierung auf Systemebene zu minimieren. Mithilfe der Überwachung können Administratoren Leistungstrends identifizieren, um zu bestimmen, ob Änderungen erforderlich sind.  
  
So überwachen Sie effektiv eine beliebige Komponente von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
1.  Bestimmen Sie, welche Ziele durch das Überwachen erreicht werden sollen.  
2.  Wählen Sie das geeignete Tool aus.    
3.  Identifizieren Sie die zu überwachenden Komponenten.  
4.  Wählen Sie Eigenschaften für diese Komponenten aus.  
5.  Überwachen Sie den Server.  
6.  Analysieren Sie die Daten.  
  
Diese Schritte werden unten der Reihe nach erläutert.  
  
## <a name="determine-your-monitoring-goals"></a>Bestimmen der Überwachungsziele  
Um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effektiv überwachen zu können, sollten Sie die Gründe für die Überwachung eindeutig identifizieren. Möglich sind z. B. folgende Gründe:  
  
-   Festlegen einer Basislinie für die Leistung.  
-   Identifzieren von Leistungsänderungen über einen bestimmten Zeitraum hinweg.  
-   Diagnostizieren bestimmter Leistungsprobleme.  
-   Identifizieren der zu optimierenden Komponenten oder Prozesse.  
-   Vergleichen der Auswirkungen unterschiedlicher Clientanwendungen auf die Leistung.  
-   Überwachen der Benutzeraktivität.  
-   Testen eines Servers unter verschiedenen Belastungen.  
-   Testen der Datenbankarchitektur.  
-   Testen der Wartungspläne.  
-   Testen der Sicherungs- und Wiederherstellungspläne.  
-   Bestimmen des Zeitpunkts für die Änderung der Hardwarekonfiguration.  
  
## <a name="select-the-appropriate-tool"></a>Auswählen des geeigneten Tools  
Nachdem Sie die Gründe für die Überwachung ermittelt haben, müssen Sie die geeigneten Tools für den Typ der Überwachung auswählen. Das Windows-Betriebssystem und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellen einen vollständigen Satz von Tools bereit, um Server in transaktionsintensiven Umgebungen zu überwachen. Diese Tools zeigen den Zustand einer Instanz der SQL Server-Datenbank-Engine oder einer Instanz von SQL Server Analysis Services an.  
  
Windows stellt die folgenden Tools bereit, um die auf einem Server ausgeführten Anwendungen zu überwachen:  
  
-   Den [Systemmonitor](../../relational-databases/performance/start-system-monitor-windows.md), mit dem Sie Echtzeitdaten zu Aktivitäten wie Speicher-, Festplatten- und Prozessorauslastung erfassen und anzeigen können.  
-   Leistungsprotokolle und Warnungen  
-   Task-Manager  
  
Weitere Informationen zu den Windows Server- oder Windows-Tools finden Sie in der Windows-Dokumentation.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt die folgenden Tools zum Überwachen der Komponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zur Verfügung:  
  
-   [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)
-   [SQL-Ablaufverfolgung](../../relational-databases/sql-trace/sql-trace.md)  
-   [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
-   [Distributed Replay Utility](../../tools/distributed-replay/sql-server-distributed-replay.md)  
-   [Aktivitätsmonitor](../../relational-databases/performance-monitor/activity-monitor.md)  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Grafischer Showplan  
-   [Gespeicherte Systemprozeduren](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)
-   [DBCC (Database Console Commands)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
-   [Dynamische Verwaltungssichten und -funktionen](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
-   [Funktionen](../../t-sql/functions/functions.md)   
-   [Ablaufverfolgungsflags](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)   

> [!IMPORTANT]
> Die SQL-Ablaufverfolgung und [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] sind veraltet. Der *Microsoft.SqlServer.Management.Trace*-Namespace, der die Objekte für die Microsoft SQL Server-Ablaufverfolgung und -Wiedergabe enthält, ist ebenfalls veraltet. 
> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 
> Verwenden Sie stattdessen erweiterte Ereignisse. Weitere Informationen zu [erweiterten Ereignissen](../../relational-databases/extended-events/extended-events.md) finden Sie unter [Schnellstart: Erweiterte Ereignisse in SQL Server](../../relational-databases/extended-events/quick-start-extended-events-in-sql-server.md) und [Verwenden des SSMS XEvent Profilers](../../relational-databases/extended-events/use-the-ssms-xe-profiler.md).

> [!NOTE]
> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] für die Analysis Services-Workloads ist NICHT veraltet und wird weiterhin unterstützt.

Weitere Informationen zu den Tools zur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Leistungsüberwachung finden Sie unter [Tools für die Leistungsüberwachung und -optimierung](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md).  
  
## <a name="identify-the-components-to-monitor"></a>Identifizieren der zu überwachenden Komponenten  
Der dritte Schritt bei der Überwachung einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] besteht im Identifizieren der zu überwachenden Komponenten. Wenn Sie z. B. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] verwenden, um eine Ablaufverfolgung für einen Server auszuführen, können Sie die Ablaufverfolgung so definieren, dass Daten zu bestimmten Ereignissen gesammelt werden. Darüber hinaus können Sie Ereignisse ausschließen, die für Ihre Situation nicht relevant sind.  
  
## <a name="select-metrics-for-monitored-components"></a>Auswählen der Eigenschaften für die überwachten Komponenten  
Nachdem Sie die zu überwachenden Komponenten identifiziert haben, bestimmen Sie die Eigenschaften für diese Komponenten. Nachdem Sie die Ereignisse ausgewählt haben, die bei der Ablaufverfolgung berücksichtigt werden sollen, können Sie beispielsweise festlegen, dass nur bestimmte Daten zu diesen Ereignissen berücksichtigt werden. Indem Sie die Ablaufverfolgung auf Daten beschränken, die für die Ablaufverfolgung relevant sind, werden die für die Ausführung der Ablaufverfolgung erforderlichen Systemressourcen minimiert.  
  
## <a name="monitor-the-server"></a>Überwachen des Servers  
Um den Server zu überwachen, führen Sie das Überwachungstool aus, das Sie zum Sammeln der Daten konfiguriert haben. Nachdem z. B. eine Ablaufverfolgung definiert wurde, können Sie die Ablaufverfolgung ausführen, um Daten zu Ereignissen zu sammeln, die auf dem Server ausgelöst wurden.  

## <a name="analyze-the-data"></a>Analysieren der Daten  
Nachdem die Ablaufverfolgung beendet wurde, können Sie die Daten analysieren, um zu überprüfen, ob Sie das Überwachungsziel erreicht haben. Falls Sie es nicht erreicht haben, ändern Sie die Komponenten oder Eigenschaften, die Sie beim Überwachen des Servers verwendet haben.  
  
Die folgenden Schritte sind zur Aufzeichnung von Ereignisdaten und zu deren Verwendung erforderlich.  
  
1.  Anwenden von Filtern, um die gesammelten Ereignisdaten einzuschränken.  
  
    Durch Einschränken der Ereignisdaten kann sich das System auf bestimmte Ereignisse konzentrieren, die wesentlich für das Überwachungsszenario sind. Wenn z. B. langsame Abfragen überwacht werden, kann ein Filter verwendet werden, um nur die Abfragen zu überwachen, die von der Anwendung für eine bestimmte Datenbank ausgegeben wurden und deren Ausführung mindestens 30 Sekunden dauert. 
    
    Weitere Informationen zum Filtern von Ablaufverfolgungen für erweiterte Ereignisse finden Sie unter [Schnellstart: Erweiterte Ereignisse in SQL Server](../../relational-databases/extended-events/quick-start-extended-events-in-sql-server.md#demo-of-ssms-integration). 
    
    Weitere Informationen zum Filtern einer SQL-Ablaufverfolgung finden Sie unter [Festlegen eines Ablaufverfolgungsfilters &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/set-a-trace-filter-transact-sql.md) und [Filtern von Ereignissen in einer Ablaufverfolgung &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md).  
  
2.  Überwachen (Aufzeichnen) der Ereignisse.  
  
    Sobald die Überwachung aktiviert wurde, zeichnet sie Daten der angegebenen Anwendung, der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]oder des Betriebssystems auf. Wenn beispielsweise die Datenträgeraktivität mithilfe des Systemmonitors überwacht wird, werden bei der Überwachung Ereignisdaten, z. B. Lese- und Schreibvorgänge auf dem Datenträger, aufgezeichnet und auf dem Bildschirm angezeigt. Weitere Informationen finden Sie unter [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md).  
  
3.  Speichern aufgezeichneter Ereignisdaten.  
  
    Durch das Speichern aufgezeichneter Daten können diese später analysiert werden. Aufgezeichnete Ereignisdaten werden in einer Datei gespeichert, die von dem Tool, das die Datei ursprünglich erstellt hat, zur späteren Analyse erneut geladen werden kann. Das Speichern aufgezeichneter Ereignisdaten ist wichtig, wenn Sie eine Leistungsbasislinie erstellen. Die Daten der Leistungsbasislinie werden gespeichert und für den Vergleich mit aktuell aufgezeichneten Ereignisdaten verwendet, um zu ermitteln, ob die Leistung optimal ist.
    
    Erweiterte Ereignisse ermöglichen das Speichern von Ereignisdaten in einer Ereignisdatei, einem Ereignisleistungsindikator, einem Histogramm oder einem Ringpuffer. Weitere Informationen finden Sie unter [Ziele für erweiterte Ereignisse in SQL Server](../../relational-databases/extended-events/targets-for-extended-events-in-sql-server.md).
    
    SQL Trace-Ereignisdaten können sogar mit dem Distributed Replay Utility oder [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] wiedergegeben werden. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ermöglicht das Speichern von Ereignisdaten in einer Datei oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle. Weitere Informationen finden Sie unter [Vorlagen und Berechtigungen in SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md).  
  
4.  Erstellen von Ablaufverfolgungsvorlagen, die die zum Aufzeichnen der Ereignisse angegebenen Einstellungen enthalten.  
  
    Ablaufverfolgungsvorlagen enthalten Spezifikationen zu den Ereignissen selbst, Ereignisdaten sowie Filter, die zum Aufzeichnen von Daten verwendet werden. Diese Vorlagen können zur späteren Überwachung einer bestimmten Gruppe von Ereignissen verwendet werden, ohne die Ereignisse, Ereignisdaten und Filter erneut zu definieren. Wenn Sie z. B. die Anzahl der Deadlocks und die Benutzer, die an diesen Deadlocks beteiligt sind, häufig überwachen möchten, können Sie eine Vorlage erstellen, die diese Ereignisse, Ereignisdaten und Ereignisfilter definiert. Speichern Sie die Vorlage, und wenden Sie den Filter erneut an, wenn Sie die Deadlocks das nächste Mal überwachen möchten.
    
    Die Definition einer erweiterten Ereignissitzung ist eine Vorlage, für die ein Skript erstellt und die wiederverwendet werden kann. Weitere Informationen zum Erstellen und Verwalten von Sitzungen finden Sie unter [Verwalten von Ereignissitzungen im Objekt-Explorer](../../relational-databases/extended-events/manage-event-sessions-in-the-object-explorer.md). Der [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] XEvent Profiler stellt bereits verwendungsbereite Vorlagen bereit. Weitere Informationen finden Sie unter [Verwenden des SSMS XEvent Profilers](../../relational-databases/extended-events/use-the-ssms-xe-profiler.md).
       
    [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] verwendet für diesen Zweck Ablaufverfolgungsvorlagen. Weitere Informationen finden Sie unter [Festlegen der Standardeinstellungen für Ablaufverfolgungsdefinitionen &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md) und [Erstellen einer Ablaufverfolgungsvorlage &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md).  
    
    > [!TIP]
    > Eine SQL Trace-Definition kann in eine Sitzung für erweiterte Ereignisse konvertiert werden. Weitere Informationen finden Sie unter [Konvertieren eines vorhandenen SQL-Ablaufverfolgungsskripts in eine Sitzung für erweiterte Ereignisse](../../relational-databases/extended-events/convert-an-existing-sql-trace-script-to-an-extended-events-session.md).
  
5.  Analysieren aufgezeichneter Ereignisdaten.  
  
     Zum Analysieren werden die aufgezeichneten Ereignisdaten in die Anwendung geladen, die die Daten aufgezeichnet hat. 
     
     So kann beispielsweise eine aufgezeichnete Ablaufverfolgung für erweiterte Ereignisse erneut in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] geladen werden, um sie anzuzeigen und zu analysieren. Weitere Informationen finden Sie unter [Erweiterte Ansicht von Zieldaten aus erweiterten Ereignissen in SQL Server](../../relational-databases/extended-events/advanced-viewing-of-target-data-from-extended-events-in-sql-server.md).

     SQL Trace-Daten können erneut in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] geladen werden, um sie anzuzeigen und zu analysieren. Weitere Informationen finden Sie unter [Anzeigen und Analysieren von Ablaufverfolgungen mit SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md).  
  
     Zur Analyse von Ereignisdaten gehört das Ermitteln der Abläufe und deren Ursachen. Mit diesen Informationen können Sie je nach Art der ausgeführten Analyse Änderungen zur Leistungsverbesserung vornehmen, z.B. das Hinzufügen von Arbeitsspeicher, das Ändern von Indizes und das Beheben von Codierungsproblemen im Zusammenhang mit [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen oder gespeicherten Prozeduren. So kann z.B. der [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Optimierungsratgeber für die Analyse einer aufgezeichneten Ablaufverfolgung aus erweiterten Ereignissen oder [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] verwendet werden und Indexempfehlungen auf der Grundlage der Ergebnisse vorschlagen.  
  
6.  Wiedergeben aufgezeichneter Ereignisdaten (optional).  
  
     Die Wiedergabe von Ereignissen ermöglicht das Erstellen einer Testkopie der Datenbankumgebung, von der die Daten aufgezeichnet wurden, und dann das Wiederholen der aufgezeichneten Ereignisse, so wie sie im echten System ursprünglich aufgetreten sind. Diese Funktion ist nur mit dem Distributed Replay Utility oder [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]verfügbar. Sie können die Ereignisse mit der Geschwindigkeit des ursprünglichen Auftretens oder so schnell wie möglich (um das System zu belasten) oder, wie in den meisten Fällen, schrittweise wiedergeben, wodurch das System nach jedem Ereignis analysiert werden kann. Durch das Analysieren der Ergebnisse in einer Testumgebung können Sie Schäden im Produktionssystem verhindern. Weitere Informationen finden Sie unter [Wiedergeben von Ablaufverfolgungen](../../tools/sql-server-profiler/replay-traces.md).  
  
  
