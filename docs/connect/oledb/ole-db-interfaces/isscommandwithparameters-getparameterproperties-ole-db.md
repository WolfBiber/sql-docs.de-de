---
title: ISSCommandWithParameters::GetParameterProperties (OLE DB) | Microsoft-Dokumentation
description: "'ISSCommandWithParameters::GetParameterProperties' (OLE DB)"
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- GetParameterProperties method
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 288657a0871046168e7319d5c650a12eab61c6ce
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006749"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>'ISSCommandWithParameters::GetParameterProperties' (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Gibt ein Array aus SSPARAMPROPS-Eigenschaftensatzstrukturen zurück – einen SSPARAMPROPS-Eigenschaftensatz für jeden UDT- oder XML-Parameter.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT GetParameterProperties(  
      DB_UPARAMS *pcParams,  
      SSPARAMPROPS **prgParamProperties);  
```  
  
## <a name="arguments"></a>Argumente  
 *pcParams*[out] [in]  
 Ein Zeiger auf den Arbeitsspeicher, der die Anzahl von SSPARAMPROPS-Strukturen enthält, die in *prgParamProperties*zurückgegeben werden.  
  
 *prgParamProperties*[out]  
 Ein Zeiger auf den Arbeitsspeicher, in den ein Array aus SSPARAMPROPS-Strukturen zurückgegeben wird. Der Anbieter teilt Speicher für die Strukturen zu und gibt die Adresse an den Arbeitsspeicher zurück. Der Consumer gibt diesen Speicher mit **IMalloc::Free** frei, wenn er die Strukturen nicht mehr benötigt. Bevor der Consumer **IMalloc::Free** für *prgParamProperties* aufrufen kann, muss er auch **VariantClear** für die *vValue*-Eigenschaft jeder DBPROP-Struktur aufrufen, um einem Speicherverlust vorzubeugen. Zu diesem kann es kommen, wenn die Variante einen Verweistyp enthält (z.B. BSTR). Wenn *pcParams* bei der Ausgabe 0 (null) ist oder ein anderer Fehler als DB_E_ERRORSOCCURRED auftritt, teilt der Anbieter keinen Arbeitsspeicher zu und stellt sicher, dass *prgParamProperties* bei Ausgabe ein NULL-Zeiger ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Die **GetParameterProperties**-Methode gibt dieselben Fehlercodes zurück wie die **ICommandProperties::GetProperties** -Methode von OLE DB, allerdings können DB_S_ERRORSOCCURRED und DB_E_ERRORSOCCURED nicht ausgelöst werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **ISSCommandWithParameters::GetParameterProperties**-Methode verhält sich in Bezug auf **GetParameterInfo** konsistent. Wenn [ISSCommandWithParameters::SetParameterProperties](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) und **SetParameterInfo** nicht aufgerufen wurden oder mit einem Wert von 0 (null) für **cParams** aufgerufen wurden, leitet „GetParameterInfo“ Parameterinformationen ab und gibt diese zurück. Wenn **ISSCommandWithParameters::SetParameterProperties** oder **SetParameterInfo** für mindestens einen Parameter aufgerufen wurde, gibt die **ISSCommandWithParameters::GetParameterProperties**-Methode Eigenschaften nur für die Parameter zurück, für die **ISSCommandWithParameters::SetParameterProperties** aufgerufen wurde. Wenn **ISSCommandWithParameters::SetParameterProperties** nach **ISSCommandWithParameters::GetParameterProperties** oder **GetParameterInfo** aufgerufen wird, geben nachfolgende Aufrufe von **ISSCommandWithParameters::GetParameterProperties** die überschriebenen Werte für jene Parameter zurück, für die die **ISSCommandWithParameters::SetParameterProperties**-Methode aufgerufen wurde.  
  
 Die SSPARAMPROPS-Struktur ist folgendermaßen definiert:  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|Member|BESCHREIBUNG|  
|------------|-----------------|  
|*iOrdinal*|Die Ordnungszahl des übergebenen Parameters|  
|*cPropertySets*|Die Anzahl von DBPROPSET-Strukturen in *rgPropertySets*|  
|*rgPropertySets*|Ein Zeiger auf den Speicher, in den ein Array aus DBPROPSET-Strukturen zurückgegeben werden soll|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
