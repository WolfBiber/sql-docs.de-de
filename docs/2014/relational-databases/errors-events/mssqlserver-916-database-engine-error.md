---
title: MSSQLSERVER_916 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 916 (Database Engine error)
ms.assetid: 73eb6581-99fe-49a5-9b42-e239d7ffe27f
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9734019354c2a2143c184b65e44951835eb73cc0
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37418995"
---
# <a name="mssqlserver916"></a>MSSQLSERVER_916
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|916|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|NOTUSER|  
|Meldungstext|Der Serverprinzipal „%.*ls“ kann unter dem aktuellen Sicherheitskontext nicht auf die „%.\*ls“-Datenbank zugreifen.|  
  
## <a name="explanation"></a>Erklärung  
 Unter diesem Anmeldenamen sind keine ausreichenden Berechtigungen verfügbar, um eine Verbindung mit der benannten Datenbank herzustellen. Anmeldenamen, unter denen eine Verbindung mit dieser Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hergestellt werden kann, die jedoch keine bestimmten Berechtigungen in einer Datenbank aufweisen, erhalten die Berechtigungen des Gastbenutzers. Dies ist eine Sicherheitsmaßnahme, um zu verhindern, dass Benutzer in einer Datenbank eine Verbindung mit anderen Datenbanken herstellen, für die sie keine Rechte besitzen. Diese Fehlermeldung kann ausgegeben werden, wenn der Gastbenutzer keine CONNECT-Berechtigung für die benannte Datenbank hat und die TRUSTWORTHY-Eigenschaft nicht festgelegt ist. Diese Fehlermeldung kann ausgegeben werden, wenn der Gastbenutzer keine CONNECT-Berechtigung für die benannte Datenbank hat.  
  
 Wenn die CONNECT-Berechtigung für die msdb-Datenbank verweigert oder aufgehoben wird, kann [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] diese Fehlermeldung erhalten, wenn der Objekt-Explorer versucht, den richtlinienbasierten Verwaltungsstatus der einzelnen Datenbanken anzuzeigen. Der Objekt-Explorer verwendet die Berechtigungen des aktuellen Anmeldenamens, um diese Informationen aus der msdb-Datenbank abzufragen, wodurch der Fehler verursacht wird. Die folgende Fehlermeldung wird ebenfalls ausgegeben:  
  
 Fehler beim Abrufen von Daten für diese Anforderung. (Microsoft.SqlServer.Management.Sdk.Sfc)  
  
## <a name="user-action"></a>Benutzeraktion  
  
> [!WARNING]  
>  Bevor Sie diese Sicherheitsmaßnahme umgehen, sollten Sie sichergehen, dass Sie genau wissen, wie Benutzer in den verschiedenen Datenbanken authentifiziert werden. Mithilfe der folgenden Methoden können Benutzer, die über Berechtigungen für eine Datenbank verfügen, eine Verbindung mit anderen Datenbanken herstellen. Auf diese Weise können Daten für böswillige Benutzer offen gelegt werden. Wenn enthaltene Datenbanken aktiviert sind, können Datenbankbesitzer in einer Datenbank über die folgenden Schritte Zugriff auf andere Datenbanken auf der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gewähren.  
  
 Sie können auf eine der folgenden Arten eine Verbindung mit der Datenbank herstellen:  
  
-   Gewähren Sie spezifischen Anmeldezugriff für die benannte Datenbank. Im folgenden Beispiel wird dem Anmeldenamen `Adventure-Works\Larry` Zugriff auf die `msdb`-Datenbank gewährt.  
  
     USE msdb ;  
  
     GO  
  
     GRANT CONNECT TO [AdventureWorks\Larry] ;  
  
-   Gewähren Sie dem Gastbenutzer für die in der Fehlermeldung genannte Datenbank die CONNECT-Berechtigung. Im folgenden Beispiel wird die `CONNECT`-Berechtigung für die `msdb`-Datenbank dem Benutzer `guest` erteilt.  
  
     USE msdb ;  
  
     GO  
  
     GRANT CONNECT TO guest ;  
  
-   Aktivieren Sie die TRUSTWORTHY-Eigenschaft für die Datenbank, die den Benutzer authentifiziert hat.  
  
     `ALTER DATABASE AdventureWorks SET TRUSTWORTHY ON;`  
  
  