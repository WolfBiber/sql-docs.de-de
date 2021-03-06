---
description: sys.user_token (Transact-SQL)
title: sys. user_token (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/27/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.user_token
- user_token
- sys.user_token_TSQL
- user_token_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- logins [SQL Server], security tokens
- sys.user_token catalog view
- user tokens [SQL Server]
- tokens [SQL Server]
- user_token catalog view
ms.assetid: be018103-5e57-43a4-9160-9bf420892aa7
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current||>= sql-server-2016||>= sql-server-linux-2017||= sqlallproducts-allversions|| = azure-sqldw-latest
ms.openlocfilehash: e8228ea67864645737524f9d449abb18fd1c1c6f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419944"
---
# <a name="sysuser_token-transact-sql"></a>sys.user_token (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md.md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Gibt eine Zeile für jeden Datenbankprinzipal zurück, der Teil des Benutzertokens in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**principal_id**|**int**|ID des Prinzipals. Der Wert ist innerhalb der Datenbank eindeutig.|  
|**sid**|**varbinary(85)**|Sicherheitsbezeichner des Prinzipals, wenn der Prinzipal datenbankextern definiert ist. Dieser Wert kann z. B. ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldename, ein Windows-Anmeldename, ein Anmeldename einer Windows-Gruppe oder ein einem Zertifikat zugeordneter Anmeldename sein. Andernfalls ist dieser Wert NULL.|  
|**name**|**nvarchar (128)**|Name des Prinzipals. Der Wert ist innerhalb der Datenbank eindeutig.|  
|**type**|**nvarchar (128)**|Beschreibung des Prinzipaltyps. Alle Typen werden **sid**zugeordnet. Der Wert kann in folgenden Formen vorliegen:<br /><br /> SQL USER<br /><br /> WINDOWS LOGIN<br /><br /> WINDOWS GROUP<br /><br /> ROLE<br /><br /> APPLICATION ROLE<br /><br /> DATABASE ROLE<br /><br /> USER MAPPED TO CERTIFICATE<br /><br /> USER MAPPED TO ASYMMETRIC KEY<br /><br /> CERTIFICATE<br /><br /> ASYMMETRIC KEY|  
|**ungs**|**nvarchar (128)**|Zeigt an, dass der Prinzipal an der Auswertung von GRANT- oder DENY-Berechtigungen teilnimmt oder als Authentifikator dient.<br /><br /> Die folgenden Werte sind möglich:<br /><br /> GRANT OR DENY<br /><br /> DENY ONLY<br /><br /> AUTHENTICATOR|  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. login_token &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-login-token-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
