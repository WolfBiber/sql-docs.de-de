---
description: Dynamische Verwaltungssichten in Verbindung mit dem SQL Server-Betriebssystem (Transact-SQL)
title: SQL Server mit dem Betriebs System verbundene dynamische Verwaltungs Sichten (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/17/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operating systems [SQL Server], dynamic management objects
- SQL Operating System dynamic management objects [SQL Server]
- SQL OS dynamic management objects [SQL Server]
- dynamic management objects [SQL Server], SQL OS
ms.assetid: 3030c86a-0a74-4fed-ac0f-392e244cb965
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6ca14e58a777603fc0bbfed73834597641fddf08
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89548916"
---
# <a name="sql-server-operating-system-related-dynamic-management-views-transact-sql"></a>Dynamische Verwaltungssichten in Verbindung mit dem SQL Server-Betriebssystem (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

In diesem Abschnitt werden dynamische Verwaltungs Sichten (DMV) dokumentiert, die dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Betriebs System (SQLOS) zugeordnet sind. SQLOS ist für die Verwaltung von Betriebssystemressourcen zuständig, die für spezifisch sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .


|  |  |
|---------|---------|
|**sys.dm_os_buffer_descriptors** | **sys.dm_os_buffer_pool_extension_configuration**|
|**sys.dm_os_child_instances** | **sys.dm_os_cluster_nodes** |
|**sys.dm_os_cluster_properties** | **sys.dm_os_dispatcher_pools** |
|**sys.dm_os_enumerate_fixed_drives** | **sys.dm_os_host_info** |
|**sys.dm_os_hosts** | **sys.dm_os_latch_stats** |
|**sys.dm_os_loaded_modules** |**sys.dm_os_memory_brokers**|
|**sys.dm_os_memory_cache_clock_hands**|**sys.dm_os_memory_cache_counters** |
|**sys.dm_os_memory_cache_entries**|**sys.dm_os_memory_cache_hash_tables**|
|**sys.dm_os_memory_clerks**|**sys.dm_os_memory_nodes**|
|**sys.dm_os_nodes**|**sys.dm_os_performance_counters**|
|**sys.dm_os_process_memory**|**sys.dm_os_schedulers**|
|**sys.dm_os_server_diagnostics_log_configurations**|**sys.dm_os_spinlock_stats** |
|**sys.dm_os_stacks**|**sys.dm_os_sys_info**|
|**sys.dm_os_sys_memory**|**sys.dm_os_tasks**|
|**sys.dm_os_threads** |**sys.dm_os_virtual_address_dump**|
|**sys.dm_os_volume_stats**|**sys.dm_os_waiting_tasks**|
|**sys.dm_os_wait_stats**|**sys.dm_os_windows_info**|
|**sys.dm_os_workers** ||








 Die folgenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dynamischen Verwaltungs Sichten im Zusammenhang mit dem Betriebs System sind [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] .  
  
|||  
|-|-|  
|**sys.dm_os_function_symbolic_name**|**sys.dm_os_ring_buffers**|  
|**sys.dm_os_memory_allocations**|**sys.dm_os_sublatches**|  
|**sys.dm_os_worker_local_storage**||  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

