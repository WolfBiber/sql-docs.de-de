---
description: GetRowsOptionEnum
title: GetRowsOptionEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- GetRowsOptionEnum
helpviewer_keywords:
- GetRowsOptionEnum enumeration [ADO]
ms.assetid: adc109b9-79f4-4946-a5eb-658e22e9a8a5
author: rothja
ms.author: jroth
ms.openlocfilehash: 7a827c5dc7e2ae5b59911385982b826944da021c
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990871"
---
# <a name="getrowsoptionenum"></a>GetRowsOptionEnum
Gibt an, wie viele Datensätze aus einem [Recordset](./recordset-object-ado.md)abgerufen werden sollen.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adgetrowsrest**|-1|Ruft die restlichen Datensätze im **Recordset**entweder von der aktuellen Position oder einem Lesezeichen ab, das durch den *Start* -Parameter der [GetRows](./getrows-method-ado.md) -Methode angegeben wird.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoumums. getrowsoption. Rest|  
  
## <a name="applies-to"></a>Gilt für  
 [GetRows-Methode (ADO)](./getrows-method-ado.md)