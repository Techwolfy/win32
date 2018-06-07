---
Description: Registers a service that provides virtual machine-specific resource-related objects.
ms.assetid: 85782C4D-E0A3-4EED-9A26-7928862C559B
title: Msvm\_VirtualSystemResourceRegistration class
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# Msvm\_VirtualSystemResourceRegistration class

Registers a service that provides virtual machine-specific resource-related objects.

The following syntax is simplified Managed Object Format (MOF) code, and it includes all of the inherited properties.

## Syntax

``` syntax
class Msvm_VirtualSystemResourceRegistration : Msvm_VirtualizationComponentRegistration
{
  Msvm_ResourceTypeDefinition         REF ResourceType;
  Msvm_VirtualSystemResourceComponent REF Component;
  boolean                                 IsRootDevice = False;
};
```

## Members

The **Msvm\_VirtualSystemResourceRegistration** class has these types of members:

-   [Properties](#properties)

### Properties

The **Msvm\_VirtualSystemResourceRegistration** class has these properties.

<dl> <dt>

**Component**
</dt> <dd> <dl> <dt>

Data type: **[**Msvm\_VirtualSystemResourceComponent**](msvm-virtualsystemresourcecomponent.md)**
</dt> <dt>

Access type: Read-only
</dt> </dl>

A reference to an instance that describes the COM object that implements this class.

</dd> <dt>

**IsRootDevice**
</dt> <dd> <dl> <dt>

Data type: **boolean**
</dt> <dt>

Access type: Read-only
</dt> </dl>

**True** if this registration indicates whether the specified resource type is the root (or parent-less) device for this service; otherwise, **False**. Only one registration can exist when **IsRootDevice** is set to **True**. Otherwise, this registration represents a mapping to a sub-device. This property is always set to **False**.

</dd> <dt>

**ResourceType**
</dt> <dd> <dl> <dt>

Data type: **[**Msvm\_ResourceTypeDefinition**](msvm-resourcetypedefinition.md)**
</dt> <dt>

Access type: Read-only
</dt> </dl>

A reference to an instance that describes a resource type supported by the service. This property is inherited from [**Msvm\_VirtualizationComponentRegistration**](msvm-virtualizationcomponentregistration.md).

</dd> </dl>

## Remarks

Access to the **Msvm\_VirtualSystemResourceRegistration** class might be restricted by UAC Filtering. For more information, see [User Account Control and WMI](https://msdn.microsoft.com/library/aa826699).

## Requirements



|                                     |                                                                                                         |
|-------------------------------------|---------------------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows 8 \[desktop apps only\]<br/>                                                              |
| Minimum supported server<br/> | Windows Server 2012 \[desktop apps only\]<br/>                                                    |
| End of client support<br/>    | Windows 8.1<br/>                                                                                  |
| End of server support<br/>    | Windows Server 2012 R2<br/>                                                                       |
| Namespace<br/>                | Root\\Virtualization\\V2<br/>                                                                     |
| MOF<br/>                      | <dl> <dt>WindowsVirtualization.V2.mof</dt> </dl> |
| DLL<br/>                      | <dl> <dt>Vmms.exe</dt> </dl>                     |



## See also

<dl> <dt>

[**Msvm\_VirtualizationComponentRegistration**](https://msdn.microsoft.com/library/windows/desktop/hh850251)
</dt> <dt>

[**Msvm\_VirtualizationComponentRegistration**](msvm-virtualizationcomponentregistration.md)
</dt> </dl>

 

 



