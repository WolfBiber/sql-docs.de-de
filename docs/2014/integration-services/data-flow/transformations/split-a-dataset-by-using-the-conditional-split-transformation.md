---
title: Teilen eines Datasets mithilfe der Transformation für bedingtes Teilen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Conditional Split transformation
- splitting dataset
- datasets [Integration Services], splitting
ms.assetid: 23b3e84f-9296-4dc9-81c0-c7f06ae3f1ff
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bac3634ca4e4cb6839114d6e0463f28d299f00c5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37252502"
---
# <a name="split-a-dataset-by-using-the-conditional-split-transformation"></a>Teilen eines Datasets mithilfe der Transformation für bedingtes Teilen
  Das Paket muss bereits mindestens einen Datenflusstask und eine Quelle enthalten, damit Sie eine Transformation für bedingtes Teilen hinzufügen und konfigurieren können.  
  
### <a name="to-conditionally-split-a-dataset"></a>So führen Sie eine bedingte Teilung eines Datasets aus  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Datenfluss** , und ziehen Sie dann aus **Toolbox**die Transformation für bedingtes Teilen auf die Entwurfsoberfläche.  
  
4.  Verbinden Sie die Transformation für bedingtes Teilen mit dem Datenfluss, indem Sie den Konnektor von der Datenquelle oder der vorherigen Transformation auf die Transformation für bedingtes Teilen ziehen.  
  
5.  Doppelklicken Sie auf die Transformation für bedingtes Teilen.  
  
6.  Erstellen Sie in **Transformations-Editor für bedingtes Teilen**die Ausdrücke, die als Bedingungen verwendet werden sollen, indem Sie Variablen, Spalten, Funktionen und Operatoren in die **Bedingung** -Spalte im Raster ziehen. Sie können den Ausdruck auch in die **Bedingung** -Spalte eingeben.  
  
    > [!NOTE]  
    >  Eine Variable oder Spalte kann in mehreren Ausdrücken verwendet werden.  
  
    > [!NOTE]  
    >  Falls der Ausdruck ungültig ist, wird der Ausdruckstext hervorgehoben dargestellt, und die Fehler werden in einer QuickInfo in der Spalte beschrieben.  
  
7.  Optional können Sie die Werte in der **Ausgabename** -Spalte ändern. Die Standardnamen sind Fall 1, Fall 2 usw.  
  
8.  Klicken Sie auf den Pfeil nach oben oder den Pfeil nach unten, um die Reihenfolge zu ändern, in der die Bedingungen ausgewertet werden.  
  
    > [!NOTE]  
    >  Positionieren Sie die Bedingungen, die höchstwahrscheinlich vorhanden sind, am Anfang der Liste.  
  
9. Optional können Sie den Namen der Standardausgabe für Datenzeilen ändern, die mit keiner Bedingung übereinstimmen.  
  
10. Klicken Sie auf **Fehlerausgabe konfigurieren**, um die Fehlerausgabe zu konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren einer Fehlerausgabe in einer Datenflusskomponente](../../configure-an-error-output-in-a-data-flow-component.md).  
  
11. Klicken Sie auf **OK**.  
  
12. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Transformation für bedingtes Teilen](conditional-split-transformation.md)   
 [Integration Services-Transformationen](integration-services-transformations.md)   
 [SQL Server Integration Services-Pfade](../integration-services-paths.md)   
 [SQL Server Integration Services-Datentypen](../integration-services-data-types.md)   
 [Datenflusstask] ((.. /.. /Control-Flow/Data-Flow-Task.MD)   
 [Integration Services-Ausdrücke &#40;SSIS&#41;](../../expressions/integration-services-ssis-expressions.md)  
  
  