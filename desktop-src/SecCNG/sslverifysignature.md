---
Description: Verifies the specified signature by using the supplied hash and the public key.
ms.assetid: fa274851-15f2-4be0-9e2f-4cdced36daff
title: SslVerifySignature function
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# SslVerifySignature function

The **SslVerifySignature** function verifies the specified signature by using the supplied [*hash*](https://msdn.microsoft.com/library/windows/desktop/ms721586#-security-hash-gly) and the [*public key*](https://msdn.microsoft.com/library/windows/desktop/ms721603#-security-public-key-gly).

## Syntax


```C++
SECURITY_STATUS WINAPI SslVerifySignature(
  _In_ NCRYPT_PROV_HANDLE hSslProvider,
  _In_ NCRYPT_KEY_HANDLE  hPublicKey,
  _In_ PBYTE              pbHashValue,
  _In_ DWORD              cbHashValue,
  _In_ PBYTE              pbSignature,
  _In_ DWORD              cbSignature,
  _In_ DWORD              dwFlags
);
```



## Parameters

<dl> <dt>

*hSslProvider* \[in\]
</dt> <dd>

The handle to the [*Secure Sockets Layer protocol*](https://msdn.microsoft.com/library/windows/desktop/ms721625#-security-secure-sockets-layer-protocol-gly) (SSL) protocol provider instance.

</dd> <dt>

*hPublicKey* \[in\]
</dt> <dd>

The handle to the public key.

</dd> <dt>

*pbHashValue* \[in\]
</dt> <dd>

A pointer to a buffer that contains the hash to use to verify the signature.

</dd> <dt>

*cbHashValue* \[in\]
</dt> <dd>

The size, in bytes, of the *pbHashValue* buffer.

</dd> <dt>

*pbSignature* \[in\]
</dt> <dd>

A pointer to a buffer that contains the signature to verify.

</dd> <dt>

*cbSignature* \[in\]
</dt> <dd>

The size, in bytes, of the *pbSignature* buffer.

</dd> <dt>

*dwFlags* \[in\]
</dt> <dd>

This parameter is reserved for future use.

</dd> </dl>

## Return value

If the function succeeds, it returns zero.

If the function fails, it returns a nonzero error value.

Possible return codes include, but are not limited to, the following.



| Return code/value                                                                                                                                                    | Description                                          |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|
| <dl> <dt>**NTE\_INVALID\_HANDLE**</dt> <dt>0x80090026L</dt> </dl> | One of the provided handles is not valid.<br/> |



 

## Remarks

The **SslVerifySignature** function is not currently called by Windows. This function is a required part of the SSL Provider interface and should be fully implemented to ensure forward compatibility.

Current implementations of the server side of the [*Transport Layer Security protocol*](https://msdn.microsoft.com/library/windows/desktop/ms721627#-security-transport-layer-security-protocol-gly) (TLS) connection call the [**NCryptVerifySignature**](/windows/desktop/api/Ncrypt/nf-ncrypt-ncryptverifysignature) function during the client authentication to process the certificate verify message.

## Requirements



|                                     |                                                                                          |
|-------------------------------------|------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows Vista \[desktop apps only\]<br/>                                           |
| Minimum supported server<br/> | Windows Server 2008 \[desktop apps only\]<br/>                                     |
| Header<br/>                   | <dl> <dt>Sslprovider.h</dt> </dl> |
| DLL<br/>                      | <dl> <dt>Ncrypt.dll</dt> </dl>    |



 

 



