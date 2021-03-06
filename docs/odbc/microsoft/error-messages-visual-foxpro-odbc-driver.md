---
description: Fehlermeldungen (Visual FoxPro-ODBC-Treiber)
title: Fehlermeldungen (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error messages [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], error messages
- SQLSTATE [ODBC]
- FoxPro ODBC driver [ODBC], error messages
ms.assetid: 58ea9734-4edf-44da-ba80-938aa7b340e4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1b76ec8703ebee8aa597849b23a5a22323caa350
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483603"
---
# <a name="error-messages-visual-foxpro-odbc-driver"></a>Fehlermeldungen (Visual FoxPro-ODBC-Treiber)
Wenn ein Fehler auftritt, gibt der Visual FoxPro-Treiber die folgenden Informationen zurück:  
  
-   Die systemeigene Fehlernummer und der Fehlermeldungs Text.  
  
-   SQLSTATE (ein ODBC-Fehlercode) und Fehlermeldungs Text  
  
 Wenn Sie [SQLError](../../odbc/microsoft/sqlerror-visual-foxpro-odbc-driver.md)aufrufen, greifen Sie auf diese Fehlerinformationen zu.  
  
## <a name="native-errors"></a>Native Fehler  
 Bei Fehlern, die in der Datenquelle auftreten, gibt der Visual FoxPro-Treiber die systemeigene Fehlernummer und den Fehlermeldungs Text zurück. Eine Liste der systemeigenen Fehlernummern finden Sie unter [native Fehlermeldungen des Visual FoxPro-ODBC-Treibers](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md).  
  
## <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (ODBC-Fehlercodes)  
 Bei Fehlern, die vom Visual FoxPro-Treiber erkannt und zurückgegeben werden, ordnet der Treiber die zurückgegebene systemeigene Fehlernummer dem entsprechenden SQLSTATE zu. Wenn eine systemeigene Fehlernummer keinen ODBC-Fehlercode aufweist, der zugeordnet werden kann, gibt der Visual FoxPro-Treiber SQLSTATE S1000 (allgemeiner Fehler) zurück.  
  
 Eine Liste der SQLSTATE-Werte, die vom Visual FoxPro-ODBC-Treiber für entsprechende Visual FoxPro-Fehler generiert werden, finden Sie unter [ODBC-Fehler Codes](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md).  
  
## <a name="syntax"></a>Syntax  
 Fehlermeldungen weisen das folgende Format auf:  
  
 **[** *Hersteller* **] [** *ODBC_component* **]** *ERROR_MESSAGE*  
  
 Die Präfixe in eckigen Klammern ([]) identifizieren die Fehlerquelle, wie in der folgenden Tabelle definiert.  
  
|Datenquellen-|Präfix|Wert|  
|-----------------|------------|-----------|  
|Treiber-Manager|Verkäufern<br />[ODBC_component]<br />[data_source]|[Microsoft]<br />[ODBC-Treiber-Manager]<br />–|  
|Visual FoxPro-Treiber|Verkäufern<br />[ODBC_component]<br />[data_source]|[Microsoft]<br />[Visual FoxPro-Treiber für ODBC]<br />–|  
  
 Wenn der Visual FoxPro-ODBC-Treiber z. b. die Datei Employee. dbf nicht finden konnte, wird möglicherweise die folgende Fehlermeldung zurückgegeben:  
  
 "[*Microsoft*] [*ODBC Visual FoxPro Driver*] die Datei ' Employee. DBF ' ist nicht vorhanden"
