---
title: Große CLR-benutzerdefinierte Typen | Microsoft-Dokumentation
description: Große CLR-benutzerdefinierte Typen im OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 20469f3cd6a1b98a6fd08db195e883ccff4ac776
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006952"
---
# <a name="large-clr-user-defined-types"></a>Große benutzerdefinierte CLR-Typen
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  In SQL Server 2005 waren benutzerdefinierte Typen (User-Defined Types, UDTs) in der Common Language Runtime (CLR) auf eine Größe von 8.000 Bytes beschränkt. Diese Einschränkung wurde in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] und höheren Versionen aufgehoben. CLR-UDTs werden jetzt auf eine ähnliche Weise wie große Objekttypen (LOB) behandelt. UDTs mit genau oder weniger als 8.000 Byte verhalten sich also genau wie in SQL Server 2005. Größere UDTs werden aber unterstützt und zeigen ihre Größe als "unbegrenzt" an.  
  
 Weitere Informationen finden Sie unter [Große CLR-benutzerdefinierte Typen &#40;OLE DB&#41;](../../oledb/ole-db/large-clr-user-defined-types-ole-db.md).  
  
## <a name="use-cases"></a>Anwendungsfälle   
  
 Für OLE DB umfasst die Unterstützung großer UDTs die Möglichkeit zum Streamen von UDT-Werten zum und vom Server mithilfe der ISequentialStream-Bindung.  
  
 UDTs kleiner oder gleich 8.000 Byte verhalten sich wie in SQL Server 2005. Für OLE DB können Sie immer noch kleine UDTs mithilfe einer ISequentialStream-Bindung streamen.  
  
 Manchmal muss systemeigener Code den Inhalt von CLR-UDTs verstehen, muss aber keine verwalteten Objekte instanziieren. In diesem Fall können Sie die benutzerdefinierte Serialisierung verwenden, um UDT-Werte auf dem Server in ein für die Clients bekanntes Format zu konvertieren.  
  
 Bei Anwendungen, die über einen vorhandenen Datenzugriffscode verfügen, können Sie das CLR-UDT-Verhalten auf dem Client nutzen, indem Sie UDTs über systemeigene APIs abrufen und sie mithilfe von C++ CLI Interop in Anwendungen des gemischten Modus instanziieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)    
  
  
