---
title: View Job Step Information
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- displaying job step information
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- viewing job step information
ms.assetid: e3f06492-dc86-4e06-b186-ea58aff6d591
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 2dc60fb5ef44ff4b94cf8326e97d552f34c3b1c7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85729722"
---
# <a name="view-job-step-information"></a>View Job Step Information
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Thema wird beschrieben, wie Sie die Auftragsschrittdetails im Auftragsschritt-Eigenschaftendialogfeld anzeigen. Es enthält auch Informationen zum Anzeigen der Auftragsschrittausgabe.  
  
-   **Vorbereitungen:**  
  
    [Einschränkungen](#Restrictions)  
  
    [Sicherheit](#Security)  
  
-   **So zeigen Sie Auftragsschrittinformationen an mit**  
  
    [SQL Server Management Studio](#SSMS)  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Vorbereitungen  
  
### <a name="limitations-and-restrictions"></a><a name="Restrictions"></a>Einschränkungen  
Wenn der Auftragsschritt so konfiguriert wurde, dass seine Ausgabe in eine Tabelle oder Datei geschrieben wird, und der Auftrag wurde mindestens einmal ausgeführt, können Sie die Ausgabe auf der Seite **Erweitert** des Dialogfelds **Auftragsschritt-Eigenschaften** anzeigen. Beim Löschen eines Auftrags oder Auftragsschritts wird das Ausgabeprotokoll automatisch gelöscht.  
  
### <a name="security"></a><a name="Security"></a>Sicherheit  
  
#### <a name="permissions"></a><a name="Permissions"></a>Berechtigungen  
Sie können nur die Aufträge anzeigen, die Sie besitzen, es sei denn, Sie sind ein Mitglied der festen Serverrolle **sysadmin** . Mitglieder dieser Rolle können alle Aufträge und Auftragsschrittdetails anzeigen.  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>Verwenden von SQL Server Management Studio  
  
#### <a name="to-view-job-step-information"></a>So zeigen Sie Auftragsschrittinformationen an  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)] her, und erweitern Sie diese dann.  
  
2.  Erweitern Sie **SQL Server-Agent**, erweitern Sie **Aufträge**, klicken Sie mit der rechten Maustaste auf den Auftrag, dessen Auftragsschritte Sie anzeigen möchten, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Wählen Sie im Dialogfeld **Auftragseigenschaften** die Seite **Schritte** aus.  
  
4.  Klicken Sie auf den anzuzeigenden Auftragsschritt, und klicken Sie auf **Bearbeiten**.  
  
5.  Sie können auf der Seite **Allgemein** des Dialogfelds **Auftragsschritt-Eigenschaften** den Typ des Auftragsschritts anzeigen und welche Aktion er ausführt.  
  
6.  Klicken Sie auf die Seite **Erweitert** , um die Aktionen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents anzuzeigen wenn der Auftragsschritt erfolgreich ausgeführt wird oder einen Fehler erzeugt, wie oft der Auftragsschritt wiederholt werden sollte, wohin die Auftragsschrittausgabe geschrieben wird und welcher Benutzer den Auftragsschritt ausführt.  
  
#### <a name="to-view-job-step-output"></a>So zeigen Sie die Auftragsschrittausgabe an  
  
1.  Klicken Sie im Dialogfeld **Auftragsschritt-Eigenschaften** auf die Seite **Erweitert** .  
  
2.  Abhängig von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Version, mit der Sie verbunden sind, können Sie entweder die Auftragsschritt-Ausgabedatei oder die Auftragsschritt-Ausgabetabelle wie folgt anzeigen:  
  
    -   Wenn Sie mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder einer höheren Version verbunden sind, können Sie nur dann auf **Anzeigen** klicken, wenn **In Tabelle protokollieren** aktiviert ist. In diesem Fall wird die Auftragsschrittausgabe in die **sysjobstepslogs** -Tabelle der **msdb** -Datenbank geschrieben.  
  
    -   Die Schaltfläche **Anzeigen** ist deaktiviert, wenn die Auftragsschrittausgabe in eine Datei geschrieben wird. Verwenden Sie den Editor zum Anzeigen der Auftragsschritt-Ausgabedatei.  
  
