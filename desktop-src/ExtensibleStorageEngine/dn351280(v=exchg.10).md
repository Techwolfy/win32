﻿---
title: Server2003Grbits fields (Microsoft.Isam.Esent.Interop.Server2003)
TOCTitle: Server2003Grbits fields
ms:assetid: Fields.T:Microsoft.Isam.Esent.Interop.Server2003.Server2003Grbits
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.isam.esent.interop.server2003.server2003grbits_fields(v=EXCHG.10)
ms:contentKeyID: 55104210
ms.date: 07/30/2014
ms.topic: article
---

# Server2003Grbits fields

Include protected members  
Include inherited members  

The [Server2003Grbits](dn351281\(v=exchg.10\).md) type exposes the following members.

## Fields

<table>
<thead>
<tr class="header">
<th> </th>
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><img src="images/Hh596466.pubfield(EXCHG.10).gif" title="Public field" alt="Public field" /><img src="images/Dn292146.static(EXCHG.10).gif" title="Static member" alt="Static member" /></td>
<td><a href="dn351203(v=exchg.10).md">EnumerateIgnoreUserDefinedDefault</a></td>
<td>If a given column is not present in the record and it has a user defined default value then no column value will be returned. This option will prevent the callback that computes the user defined default value for the column from being called when enumerating the values for that column.</td>
</tr>
<tr class="even">
<td><img src="images/Hh596466.pubfield(EXCHG.10).gif" title="Public field" alt="Public field" /><img src="images/Dn292146.static(EXCHG.10).gif" title="Static member" alt="Static member" /></td>
<td><a href="dn351284(v=exchg.10).md">ForwardOnly</a></td>
<td>This option requests that the temporary table only be created if the temporary table manager can use the implementation optimized for intermediate query results. If any characteristic of the temporary table would prevent the use of this optimization then the operation will fail with JET_errCannotMaterializeForwardOnlySort. A side effect of this option is to allow the temporary table to contain records with duplicate index keys. See <a href="hh558517(v=exchg.10).md">Unique</a> for more information.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh596466.pubfield(EXCHG.10).gif" title="Public field" alt="Public field" /><img src="images/Dn292146.static(EXCHG.10).gif" title="Static member" alt="Static member" /></td>
<td><a href="dn351209(v=exchg.10).md">WaitAllLevel0Commit</a></td>
<td>All transactions previously committed by any session that have not yet been flushed to the transaction log file will be flushed immediately. This API will wait until the transactions have been flushed before returning to the caller. This option may be used even if the session is not currently in a transaction. This option cannot be used in combination with any other option.</td>
</tr>
</tbody>
</table>


Top

## See also

#### Reference

[Server2003Grbits class](dn351281\(v=exchg.10\).md)

[Microsoft.Isam.Esent.Interop.Server2003 namespace](hh557147\(v=exchg.10\).md)
