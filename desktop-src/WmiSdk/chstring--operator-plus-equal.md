---
Description: The += concatenation operator joins characters to the end of this string. The operator accepts another CHString object, a character pointer, or a single character.
audience: developer
author: REDMOND\\markl
manager: REDMOND\\markl
ms.assetid: 026ff9af-4cda-4261-aa27-e215d49b80ce
ms.prod: windows-server-dev
ms.technology: windows-management-instrumentation
ms.tgt_platform: multiple
title: CHString::operator+=
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# CHString::operator+=

\[The [**CHString**](chstring.md) class is part of the WMI Provider Framework which is now considered in final state, and no further development, enhancements, or updates will be available for non-security related issues affecting these libraries. The [MI APIs](https://msdn.microsoft.com/library/jj152383) should be used for all new development.\]

The += concatenation operator joins characters to the end of this string. The operator accepts another [**CHString**](chstring.md) object, a character pointer, or a single character.

``` syntax
const CHString& operator +=(
  const CHString& string )
throw( CHeap_Exception );

const CHString& operator +=(
  WCHAR ch )
throw( CHeap_Exception );

const CHString& operator +=(
  LPCWSTR lpsz )
throw( CHeap_Exception );

const CHString operator +=(
  char ch )
throw( CHeap_Exception );
```

## Parameters

<dl> <dt>

<span id="string"></span><span id="STRING"></span>*string*
</dt> <dd>

A [**CHString**](chstring.md) string that concatenates to this string.

</dd> <dt>

<span id="ch"></span><span id="CH"></span>*ch*
</dt> <dd>

A character to concatenate to this string.

</dd> <dt>

<span id="lpsz"></span><span id="LPSZ"></span>*lpsz*
</dt> <dd>

Pointer to a **NULL**-terminated string to concatenate to this string.

</dd> </dl>

## Remarks

Be aware that memory exceptions can occur whenever you use this concatenation operator because new storage may be allocated for characters added to this [**CHString**](chstring.md) object.

## Examples

The following example shows the use of **CHString::operator +=**:


```C++
CHString s( L"abc" );
assert( ( s += L"def" ) == L"abcdef" );
```



## Requirements



|                                     |                                                                                                                                                               |
|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows Vista<br/>                                                                                                                                      |
| Minimum supported server<br/> | Windows Server 2008<br/>                                                                                                                                |
| Header<br/>                   | <dl> <dt>ChString.h (include FwCommon.h)</dt> </dl>                                                    |
| Library<br/>                  | <dl> <dt>FrameDyn.lib</dt> </dl>                                                                       |
| DLL<br/>                      | <dl> <dt>FrameDynOS.dll; </dt> <dt>FrameDyn.dll</dt> </dl> |



## See also

<dl> <dt>

[**CHString**](chstring.md)
</dt> </dl>

 

 



