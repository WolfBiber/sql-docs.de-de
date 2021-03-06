---
title: PDF-Geräteinformationseinstellungen - Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie mehr über die Geräteinformationseinstellungen, die für das Rendering von Berichten im PDF-Format verfügbar sind.
ms.date: 03/16/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], PDF rendering
- PDF [Reporting Services]
ms.assetid: 9a4aabe5-dbdc-4884-b999-1200983fee47
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 126740ad794007e06d7565ddeea8a977fe07798b
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245279"
---
# <a name="pdf-device-information-settings"></a>PDF-Geräteinformationseinstellungen
  In der folgenden Tabelle werden die Einstellungen der Geräteinformationen zum Rendern von Berichten in das PDF-Format aufgeführt.  
  
|Einstellung|Wert|  
|-------------|-----------|  
| **AccessiblePDF** | Gibt an, ob eine barrierefreie PDF-Datei bzw. eine PDF-Datei mit Tags gerendert werden soll. Eine solche Datei ist zwar größer, kann aber von Sprachausgabesoftware und anderen Unterstützungstechnologien besser verarbeitet werden. Der Standardwert ist **false**. (in Power BI-Berichtsserver der Version von März 2018 und in neueren Versionen verfügbar) |
|**Spalten**|Die für den Bericht gewünschte Anzahl der Spalten. Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**ColumnSpacing**|Der für den Bericht gewünschte Spaltenabstand. Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**DpiX**|Die Auflösung des Ausgabegeräts in x-Richtung.|  
|**DpiY**|Die Auflösung des Ausgabegeräts in y-Richtung.|  
|**EndPage**|Die letzte Seite des zu rendernden Berichts. Der Standardwert ist der Wert für **StartPage**.|  
|**HumanReadablePDF**|Gibt an, ob eine nicht komprimierte PDF-Datei gerendert werden soll. Eine solche Datei ist zwar größer, aber in einem Nur-Text-Editor besser lesbar. Der Standardwert ist **false.**|  
|**MarginBottom**|Der für den Bericht gewünschte Wert für den unteren Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z. B. „1in“). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**MarginLeft**|Der für den Bericht gewünschte Wert für den linken Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z. B. „1in“). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**MarginRight**|Der für den Bericht gewünschte Wert für den rechten Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z. B. „1in“). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**MarginTop**|Der für den Bericht gewünschte Wert für den oberen Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z. B. „1in“). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**PageHeight**|Die für den Bericht gewünschte Seitenhöhe in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z. B. „11in“). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**PageWidth**|Die für den Bericht gewünschte Seitenbreite in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert angeben, gefolgt von „in“ (z. B. 8,5in). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**StartPage**|Die erste Seite des zu rendernden Berichts. Der Wert **0** gibt an, dass alle Seiten des Berichts gerendert werden. Der Standardwert ist **1**.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei „RSReportServer.config“](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz (SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
