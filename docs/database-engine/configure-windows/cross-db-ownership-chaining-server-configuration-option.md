---
title: Datenbankübergreifende Besitzverkettung (Serverkonfigurationsoption) | Microsoft-Dokumentation
description: Informationen zur Option „cross db ownership chaining“ in SQL Server Hier finden Sie wichtige Faktoren für die Aktivierung und Deaktivierung der datenbankübergreifenden Besitzverkettung.
ms.custom: ''
ms.date: 08/15/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cross-database ownership chaining
- cross db ownership chaining option
- chaining ownership
ms.assetid: 7b2d49f2-b91c-4aee-a52b-6cc49bed03af
author: markingmyname
ms.author: maghan
ms.openlocfilehash: eefc2b48f43aa91afa982775829648d76856b392
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772616"
---
# <a name="cross-db-ownership-chaining-server-configuration-option"></a>Datenbankübergreifende Besitzverkettung (Serverkonfigurationsoption)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Mit der Option **cross db ownership chaining** lässt sich die datenbankübergreifende Besitzverkettung für eine Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konfigurieren.  
  
 Mithilfe dieser Serveroption können Sie die datenbankübergreifende Besitzverkettung für alle Datenbanken auf Datenbankebene steuern oder die datenbankübergreifende Besitzverkettung für alle Datenbanken ermöglichen:  
  
-   Wenn **Datenbankübergreifende Besitzverkettung** für die Instanz deaktiviert ist (0), ist die datenbankübergreifende Besitzverkettung für alle Datenbanken deaktiviert.  
  
-   Wenn **Datenbankübergreifende Besitzverkettung** für die Instanz aktiviert ist (1), ist die datenbankübergreifende Besitzverkettung für alle Datenbanken aktiviert.  
  
-   Sie können die datenbankübergreifende Besitzverkettung für einzelne Datenbanken mithilfe der SET-Klausel der ALTER DATABASE-Anweisung festlegen. Wenn Sie eine neue Datenbank erstellen, können Sie die datenbankübergreifende Besitzverkettungsoption für die neue Datenbank mithilfe der CREATE DATABASE-Anweisung festlegen.  
  
     Es ist nicht empfehlenswert, die Option **Datenbankübergreifende Besitzverkettung** auf 1 festzulegen, es sei denn, alle von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz gehosteten Datenbanken müssen an der datenbankübergreifenden Besitzverkettung teilnehmen. Darüber hinaus sollten Ihnen die Sicherheitsauswirkungen dieser Einstellung bewusst sein.  

Um den aktuellen Status der datenbankübergreifenden Besitzverkettung zu bestimmen, führen Sie die folgende Abfrage aus:  
```sql
SELECT is_db_chaining_on, name FROM sys.databases;
```  
Das Ergebnis „1“ weist darauf hin, dass die datenbankübergreifende Besitzverkettung aktiviert ist.

## <a name="controlling-cross-database-ownership-chaining"></a>Steuern der datenbankübergreifenden Besitzverkettung  
 Vor dem Aktivieren bzw. Deaktivieren der datenbankübergreifenden Besitzverkettung sollten Sie Folgendes berücksichtigen:  
  
-   Sie müssen Mitglied der **sysadmin** -Rolle sein, um die datenbankübergreifende Besitzverkettung aktivieren oder deaktivieren zu können.  
  
-   Vor dem Deaktivieren der datenbankübergreifenden Besitzverkettung auf einem Produktionsserver sollten Sie jede Anwendung testen, einschließlich Anwendungen von Drittanbietern. Auf diese Weise können Sie sicherstellen, dass die Änderungen die Funktionalität der Anwendungen nicht beeinträchtigen.  
  
-   Sie können die Option **Datenbankübergreifende Besitzverkettung** ändern, wenn der Server ausgeführt wird und Sie RECONFIGURE mit **sp_configure**angeben.  
  
-   Verfügen Sie über Datenbanken, die eine datenbankübergreifende Besitzverkettung erfordern, ist es empfehlenswert, die Option **Datenbankübergreifende Besitzverkettung** für die Instanz mithilfe von **sp_configure**zu deaktivieren, und dann die datenbankübergreifende Besitzverkettung für einzelne Datenbanken, die sie erfordern, mithilfe der ALTER DATABASE-Anweisung zu aktivieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)  
  
  
