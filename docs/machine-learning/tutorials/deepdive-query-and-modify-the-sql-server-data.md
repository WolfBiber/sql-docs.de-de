---
title: Ändern von Daten mithilfe von RevoScaleR
description: 'Tutorial 3 zu RevoScaleR: Hier erfahren Sie mehr über das Abfragen und Ändern von Daten mithilfe der R-Programmiersprache in SQL Server.'
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7fda48d4d59ab66ae285e4aeda1899a214a5b901
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85679895"
---
# <a name="query-and-modify-the-sql-server-data-sql-server-and-revoscaler-tutorial"></a>Abfragen und Ändern von SQL Server-Daten (Tutorial zu SQL Server und RevoScaleR)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Bei diesem Tutorial handelt es sich um das 3. Tutorial der [Tutorialreihe zu RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md). In diesem Tutorial erfahren Sie, wie Sie [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server verwenden.

Im vorherigen Tutorial haben Sie die Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geladen. In diesem Tutorial können Sie Daten mithilfe von **RevoScaleR** untersuchen und ändern:

> [!div class="checklist"]
> * Zurückgeben von grundlegenden Informationen zu den Variablen
> * Erstellen von kategorischen Daten aus Rohdaten

Kategorische Daten oder *Faktorvariablen* sind für explorative Datenvisualisierungen nützlich. Sie können sie als Eingaben für Histogramme verwenden, um eine Vorstellung davon zu erhalten, wie die Variablendaten aussehen.

## <a name="query-for-columns-and-types"></a>Abfragen von Spalten und Typen

Verwenden Sie zum Ausführen von R-Skripts eine integrierte Entwicklungsumgebung für R oder die Datei „RGui.exe“. 

Rufen Sie zunächst eine Liste der Spalten und ihrer Datentypen ab. Sie können die Funktion [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) verwenden und die Datenquelle angeben, die Sie analysieren möchten. Je nachdem, welche **RevoScaleR**-Version Sie verwenden, können Sie auch [rxGetVarNames](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarnames) verwenden. 
  
```R
rxGetVarInfo(data = sqlFraudDS)
```

**Ergebnisse**

```R
Var 1: custID, Type: integer
Var 2: gender, Type: integer
Var 3: state, Type: integer
Var 4: cardholder, Type: integer
Var 5: balance, Type: integer
Var 6: numTrans, Type: integer
Var 7: numIntlTrans, Type: integer
Var 8: creditLine, Type: integer
Var 9: fraudRisk, Type: integer
```

## <a name="create-categorical-data"></a>Erstellen von kategorischen Daten

Alle Variablen werden als Integer gespeichert, einige Variablen können aber Kategoriedaten darstellen. Diese werden in R als *Faktorvariablen* bezeichnet. Die Spalte *state* enthält beispielsweise Zahlen, die für Bezeichner für die 50 US-Bundesstaaten sowie Washington D.C. verwendet werden. Um das Verständnis der Daten zu erleichtern, ersetzen Sie die Zahlen durch eine Liste der Abkürzungen der US-Bundesstaaten.

In diesem Schritt erstellen Sie einen Zeichenfolgenvektor, der die Abkürzungen enthält. Anschließend ordnen Sie diese kategorischen Werte den ursprünglichen Integerbezeichnern zu. Verwenden Sie anschließend die neue Variable im Argument *colInfo*, um anzugeben, dass diese Spalte als Faktor behandelt werden soll. Wenn Sie die Daten analysieren oder verschieben, werden die Abkürzungen verwendet, und die Spalte wird als Faktor behandelt.

Wenn die Spalte vor der Verwendung als Faktor zu Abkürzungen zugeordnet wird, verbessert dies auch die Leistung. Weitere Informationen finden Sie unter [R und Datenoptimierung (R Services)](../r/r-and-data-optimization-r-services.md).

1. Erstellen Sie zunächst eine R-Variable, *stateAbb*, und definieren Sie den Zeichenfolgenvektor, der ihr zugeordnet werden soll.
  
    ```R
    stateAbb <- c("AK", "AL", "AR", "AZ", "CA", "CO", "CT", "DC",
        "DE", "FL", "GA", "HI","IA", "ID", "IL", "IN", "KS", "KY", "LA",
        "MA", "MD", "ME", "MI", "MN", "MO", "MS", "MT", "NB", "NC", "ND",
        "NH", "NJ", "NM", "NV", "NY", "OH", "OK", "OR", "PA", "RI","SC",
        "SD", "TN", "TX", "UT", "VA", "VT", "WA", "WI", "WV", "WY")
    ```

2. Als Nächstes erstellen Sie ein Spaltenobjekt namens *ccColInfo*, das die Zuordnung der vorhandenen Integer-Werte zu den Kategorieebenen angibt (Abkürzungen der US-Bundesstaaten).
  
    Diese Anweisung erstellt auch Faktorvariablen für „gender“ (Geschlecht) und „cardholder“ (Karteninhaber).
  
    ```R
    ccColInfo <- list(
    gender = list(
              type = "factor",
              levels = c("1", "2"),
              newLevels = c("Male", "Female")
              ),
    cardholder = list(
                  type = "factor",
                  levels = c("1", "2"),
                  newLevels = c("Principal", "Secondary")
                   ),
    state = list(
             type = "factor",
             levels = as.character(1:51),
             newLevels = stateAbb
             ),
    balance = list(type = "numeric")
    )
    ```
  
3. Um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle zu erstellen, die die aktualisierten Daten verwendet, rufen Sie die Funktion **RxSqlServerData** wie zuvor auf, fügen Sie jedoch das Argument *colInfo* hinzu.
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
    table = sqlFraudTable, colInfo = ccColInfo,
    rowsPerRead = sqlRowsPerRead)
    ```
  
    - Übergeben Sie für den *table* -Parameter die Variable *sqlFraudTable*, die die zuvor erstellte Datenquelle enthält.
    - Übergeben Sie für den *colInfo* -Parameter die Variable *ccColInfo* , die die Spaltendatentypen und Faktorebenen enthält.

4.  Sie können die **rxGetVarInfo** -Funktion nun dazu verwenden, um die Variablen in der neuen Datenquelle anzuzeigen.
  
    ```R
    rxGetVarInfo(data = sqlFraudDS)
    ```

    **Ergebnisse**
    
    ```R
    Var 1: custID, Type: integer
    Var 2: gender  2 factor levels: Male Female
    Var 3: state   51 factor levels: AK AL AR AZ CA ... VT WA WI WV WY
    Var 4: cardholder  2 factor levels: Principal Secondary
    Var 5: balance, Type: integer
    Var 6: numTrans, Type: integer
    Var 7: numIntlTrans, Type: integer
    Var 8: creditLine, Type: integer
    Var 9: fraudRisk, Type: integer
    ```

Die drei von Ihnen angegebenen Variablen (*gender*, *state*und *cardholder*) werden nun wie Faktoren verarbeitet.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Definieren und Verwenden von Rechenkontexten](../../machine-learning/tutorials/deepdive-define-and-use-compute-contexts.md)