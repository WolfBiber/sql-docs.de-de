---
title: Wideworldimporters OLAP-Daten Bank Katalog-SQL | Microsoft-Dokumentation
description: Informieren Sie sich über die Schemas, Tabellen und gespeicherten Prozeduren, die für die Data Warehousing-und analytische Verarbeitung in der wideworldimportersdw-Datenbank verwendet werden.
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 08/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 167b9d1d9990c20be8c01a3407a5423644e524f8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "79112431"
---
# <a name="wideworldimportersdw-database-catalog"></a>Wideworldimportersdw-Daten Bank Katalog
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
Erläuterungen zu den Schemas, Tabellen und gespeicherten Prozeduren in der wideworldimportersdw-Datenbank. 

Die wideworldimportersdw-Datenbank wird für die Data Warehousing-und analytische Verarbeitung verwendet. Die Transaktionsdaten zu Verkäufen und Käufen werden in der wideworldimporters-Datenbank generiert und mithilfe eines **täglichen ETL-Prozesses**in die wideworldimportersdw-Datenbank geladen.

Die Daten in wideworldimportersdw spiegeln daher die Daten in wideworldimporters wider, die Tabellen sind jedoch unterschiedlich angeordnet. Obwohl wideworldimporters ein herkömmliches normalisiertes Schema aufweist, verwendet wideworldimportersdw den [Stern Schema](https://wikipedia.org/wiki/Star_schema) Ansatz für den Tabellen Entwurf. Neben den Fakten-und Dimensions Tabellen enthält die Datenbank eine Reihe von Stagingtabellen, die im ETL-Prozess verwendet werden.

## <a name="schemas"></a>Schemas

Die unterschiedlichen Tabellentypen werden in drei Schemas organisiert.

|Schema|BESCHREIBUNG|
|-----------------------------|---------------------|
|Dimension|Dimensions Tabellen.|
|Fakt|Fakten Tabellen.|  
|Integration|Stagingtabellen und andere Objekte, die für ETL benötigt werden.|  

## <a name="tables"></a>Tabellen

Die Dimensions-und Fakten Tabellen sind unten aufgeführt. Die Tabellen im Integrations Schema werden nur für den ETL-Prozess verwendet und sind nicht aufgeführt.

### <a name="dimension-tables"></a>Dimensions Tabellen

Wideworldimportersdw verfügt über die folgenden Dimensions Tabellen. Die Beschreibung enthält die Beziehung zu den Quell Tabellen in der wideworldimporters-Datenbank.

|Tabelle|Quell Tabellen|
|-----------------------------|---------------------|
|City|`Application.Cities`, `Application.StateProvinces`, `Application.Countries`.|
|Kunde|`Sales.Customers`, `Sales.BuyingGroups`, `Sales.CustomerCategories`.|
|Datum|Neue Tabelle mit Informationen zu Datumsangaben, einschließlich des Finanz Jahrs (basierend auf dem 1. November-Start für das Finanz Jahr).|
|Employee|`Application.People`.|
|Stockitem|`Warehouse.StockItems`, `Warehouse.Colors`, `Warehouse.PackageType`.|
|Lieferanten|`Purchasing.Suppliers`, `Purchasing.SupplierCategories`.|
|PaymentMethod|`Application.PaymentMethods`.|
|TransactionType|`Application.TransactionTypes`.|

### <a name="fact-tables"></a>Fakten Tabellen

Wideworldimportersdw verfügt über die folgenden Fakten Tabellen. Die Beschreibung enthält die Beziehung zu den Quell Tabellen in der wideworldimporters-Datenbank sowie die Klassen von Analytics/Berichterstattungs Abfragen, mit denen jede Fakten Tabelle normalerweise verwendet wird.

|Tabelle|Quell Tabellen|Beispiel Analyse|
|-----------------------------|---------------------|---------------------|
|Order|`Sales.Orders` und `Sales.OrderLines`|Sales People, Picker-und Packer-Produktivität und Zeit für die Auswahl von Aufträgen. Außerdem sind niedrige Aktien Situationen, die zu Aufträgen führen.|
|Sale|`Sales.Invoices` und `Sales.InvoiceLines`|Verkaufsdaten, Übermittlungs Daten, Rentabilität im Zeitverlauf, Rentabilität durch Vertriebsmitarbeiter.|
|Kauf|`Purchasing.PurchaseOrderLines`|Vs tatsächliche Vorlaufzeiten erwartet|
|Transaktion|`Sales.CustomerTransactions` und `Purchasing.SupplierTransactions`|Messen von Problem Daten im Vergleich zum Abschluss von Datumsangaben und Summen.|
|Movement|`Warehouse.StockTransactions`|Bewegungen im Zeitverlauf.|
|Aktien Aufbewahrung|`Warehouse.StockItemHoldings`|Auf der Hand.|

## <a name="stored-procedures"></a>Gespeicherte Prozeduren

Die gespeicherten Prozeduren werden hauptsächlich für den ETL-Prozess und für Konfigurations Zwecke verwendet.

Alle Erweiterungen des Beispiels werden empfohlen, das `Reports` Schema für Reporting Services Berichte und das Schema für den `PowerBI` Power BI-Zugriff zu verwenden.

### <a name="application-schema"></a>Anwendungs Schema

Diese Prozeduren werden verwendet, um das Beispiel zu konfigurieren. Sie dienen zum Anwenden von Enterprise Edition-Features auf die Standard Edition-Version des Beispiels, zum Hinzufügen von polybase und zum reseed-ETL.

|Verfahren|Zweck|
|-----------------------------|---------------------|
|Configuration_ApplyPartitionedColumnstoreIndexing|Wendet sowohl Partitionierungs-als auch columnstore--Indizes für Fakten Tabellen an.|
|Configuration_ConfigureForEnterpriseEdition|Wendet die Partitionierung, columnstore--Indizierung und den Speicher internen Speicher an.|
|Configuration_EnableInMemory|Ersetzt die Stagingtabellen für die Integration durch SCHEMA_ONLY Speicher optimierte Tabellen, um die ETL-Leistung zu verbessern.|
|Configuration_ApplyPolyBase|Konfiguriert eine externe Datenquelle, ein Dateiformat und eine Tabelle.|
|Configuration_PopulateLargeSaleTable|Wendet Änderungen an der Enterprise Edition an und füllt dann eine größere Datenmenge für das 2012-Kalenderjahr als zusätzlichen Verlauf auf.|
|Configuration_ReseedETL|Entfernt vorhandene Daten und startet die ETL-Kerne neu. Dies ermöglicht das erneute Auffüllen der OLAP-Datenbank, um die aktualisierten Zeilen in der OLTP-Datenbank abzugleichen.|

### <a name="integration-schema"></a>Integrations Schema

Im ETL-Prozess verwendete Prozeduren fallen in die folgenden Kategorien:
- Hilfsprozeduren für die ETL-Paket-alle Get *-Prozeduren.
- Prozeduren, die vom ETL-Paket zum Migrieren von bereitgestellten Daten in die DW-Tabellen migriert werden.
- `PopulateDateDimensionForYear`: Nimmt ein Jahr in Kraft und stellt sicher, dass alle Datumsangaben für dieses `Dimension.Date` Jahr in der Tabelle aufgefüllt werden.

### <a name="sequences-schema"></a>Sequenz Schema

Prozeduren zum Konfigurieren der Sequenzen in der Datenbank.

|Verfahren|Zweck|
|-----------------------------|---------------------|
|Reseedallsequenzen|Ruft die Prozedur `ReseedSequenceBeyondTableValue` für alle Sequenzen auf.|
|Reseedsequencebeyondtablevalue|Wird verwendet, um den nächsten Sequenzwert hinter dem Wert in einer Tabelle, die dieselbe Sequenz verwendet, neu zu positionieren. (Wie eine `DBCC CHECKIDENT` für Identitäts Spalten Äquivalent für Sequenzen, aber über potenziell mehrere Tabellen hinweg.)|
