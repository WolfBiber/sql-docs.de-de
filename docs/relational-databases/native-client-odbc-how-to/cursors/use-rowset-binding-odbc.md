---
description: Verwenden der Rowsetbindung (ODBC)
title: Verwenden der Rowsetbindung (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowset binding [ODBC]
ms.assetid: a7be05f0-6b11-4b53-9fbc-501e591eef09
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 763477caaba41016b5137463c6d607f548d1d5a5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494063"
---
# <a name="use-rowset-binding-odbc"></a>Verwenden der Rowsetbindung (ODBC)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

    
### <a name="to-use-column-wise-binding"></a>So verwenden Sie spaltenbezogene Bindungen  
  
1.  Gehen Sie für jede gebundene Spalte wie folgt vor:  
  
    -   Weisen Sie ein Array von R (oder mehr) Spaltenpuffern zum Speichern von Datenwerten zu, wobei R die Anzahl der Zeilen im Rowset ist.  
  
    -   Weisen Sie optional ein Array von R (oder mehr) Spaltenpuffern zum Speichern von Datenlängen zu.  
  
    -   Rufen Sie [SQLBindCol](../../../relational-databases/native-client-odbc-api/sqlbindcol.md) auf, um die Spaltendatenwert- und die Datenlängenarrays an die Spalte des Rowsets zu binden.  
  
2.  Rufen Sie [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) auf, um die folgenden Attribute festzulegen:  
  
    -   Stellen Sie SQL_ATTR_ROW_ARRAY_SIZE auf die Anzahl der Zeilen im Rowset ein (R).  
  
    -   Stellen Sie SQL_ATTR_ROW_BIND_TYPE auf SQL_BIND_BY_COLUMN ein.  
  
    -   Legen Sie fest, dass das SQL_ATTR_ROWS FETCHED_PTR-Attribut auf eine SQLUINTEGER-Variable verweist, die die Anzahl der abgerufenen Zeilen enthält.  
  
    -   Lassen Sie SQL_ATTR_ROW_STATUS_PTR auf ein Array[R] von SQLUSSMALLINT-Variablen verweisen, die die Zeilenstatusindikatoren enthalten.  
  
3.  Ausführen der Anweisung.  
  
4.  Jeder Aufruf von [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) oder [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) ruft R-Zeilen ab und überträgt die Daten in die gebundenen Spalten.  

### <a name="to-use-row-wise-binding"></a>So verwenden Sie zeilenbezogene Bindungen  
  
1.  Weisen Sie ein Array [R] mit Strukturen zu, wobei R der Anzahl der Zeilen im Rowset entspricht. Die Struktur verfügt über ein Element für jede Spalte, und jedes Element besteht aus zwei Teilen:  
  
    -   Der erste Teil ist eine Variable des entsprechenden Datentyps zum Speichern der Spaltendaten.  
  
    -   Der zweite Teil ist eine SQLINTEGER-Variable zum Speichern des Spaltenstatusindikators.  
  
2.  Rufen Sie [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) auf, um die folgenden Attribute festzulegen:  
  
    -   Stellen Sie SQL_ATTR_ROW_ARRAY_SIZE auf die Anzahl der Zeilen im Rowset ein (R).  
  
    -   Legen Sie SQL_ATTR_ROW_BIND_TYPE auf die Größe der in Schritt 1 zugeordneten Struktur fest.  
  
    -   Legen Sie fest, dass das SQL_ATTR_ROWS_FETCHED_PTR-Attribut auf eine SQLUINTEGER-Variable verweist, die die Anzahl der abgerufenen Zeilen enthält.  
  
    -   Lassen Sie SQL_ATTR_PARAMS_STATUS_PTR auf ein Array[R] von SQLUSSMALLINT-Variablen verweisen, die die Zeilenstatusindikatoren enthalten.  
  
3.  Rufen Sie für jede Spalte im Resultset [SQLBindCol](../../../relational-databases/native-client-odbc-api/sqlbindcol.md) auf, um mit den Datenwert- und den Datenlängenzeigern der Spalte auf die Variablen im ersten Element des Arrays mit Strukturen zu zeigen, die in Schritt 1 zugewiesen wurden.  
  
4.  Ausführen der Anweisung.  
  
5.  Jeder Aufruf von [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) oder [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) ruft R-Zeilen ab und überträgt die Daten in die gebundenen Spalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gewusst-wie-Themen zur Verwendung von Cursorn &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/cursors/using-cursors-how-to-topics-odbc.md)   
 [Implementierung von Cursorn](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)   
 [Verwenden von Cursorn &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-how-to/cursors/use-cursors-odbc.md)  
  
  
