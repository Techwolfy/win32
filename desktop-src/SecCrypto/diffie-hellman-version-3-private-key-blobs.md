---
Description: Describes the format of an exported Diffie-Hellman version 3 private key BLOB.
ms.assetid: c759e6e1-f7af-4cd6-a67e-ff0da1e91eb1
title: Diffie-Hellman Version 3 Private Key BLOBs
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# Diffie-Hellman Version 3 Private Key BLOBs

When a Diffie-Hellman version 3 [*private key*](https://msdn.microsoft.com/2fe6cfd3-8a2e-4dbe-9fb8-332633daa97a) BLOB is exported, it is in a format as follows:


```C++
BLOBHEADER        blobheader;
DHPRIVKEY_VER3   dhprivkeyver3;
BYTE p[dhprivkeyver3.bitlenP/8]; 
            // Where P is the prime modulus
BYTE q[dhprivkeyver3.bitlenQ/8]; 
            // Where Q is a large factor of P-1
BYTE g[dhprivkeyver3.bitlenP/8]; 
            // Where G is the generator parameter
BYTE j[dhprivkeyver3.bitlenJ/8]; 
            // Where J is (P-1)/Q
BYTE y[dhprivkeyver3.bitlenP/8]; 
            // Where Y is (G^X) mod P
BYTE x[dhprivkeyver3.bitlenX/8]; 
            // Where X is the private exponent
```



This [*BLOB*](https://msdn.microsoft.com/2e570727-7da0-4e17-bf5d-6fe0e6aef65b) format is exported when the CRYPT\_BLOB\_VER3 flag is used with [**CryptExportKey**](/windows/desktop/api/Wincrypt/nf-wincrypt-cryptexportkey). Because the version is in the BLOB, there is no need to specify a flag when using this BLOB with [**CryptImportKey**](/windows/desktop/api/Wincrypt/nf-wincrypt-cryptimportkey).

The following table describes each component of the [*key BLOB*](https://msdn.microsoft.com/f17042c3-ba1a-408f-af55-5f171b0dee33).



| Field         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| blobheader    | A [**BLOBHEADER**](/windows/desktop/api/Wincrypt/ns-wincrypt-_publickeystruc) structure.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| dhprivkeyver3 | A [**DHPRIVKEY\_VER3**](/windows/desktop/api/Wincrypt/ns-wincrypt-_privkeyver3) structure. The **magic** member should be set to 0x34484400 for private keys. Notice that the hexadecimal value is just an [*ASCII*](https://msdn.microsoft.com/0baaa937-f635-4500-8dcd-9dbbd6f4cd02) encoding of "DH4".                                                                                                                                                                                                                                                                                            |
| P             | The P value is located directly after the [**DHPRIVKEY\_VER3**](/windows/desktop/api/Wincrypt/ns-wincrypt-_privkeyver3) structure, and should always be the length in bytes of the **DHPRIVKEY\_VER3** **bitlenP** field (bit length of P) divided by eight ([*little-endian*](https://msdn.microsoft.com/65dd9a04-fc7c-4179-95ff-dac7dad4668f) format).                                                                                                                                                                                                                            |
| Q             | The Q value is located directly after the P value and should always be the length in bytes of the [**DHPRIVKEY\_VER3**](/windows/desktop/api/Wincrypt/ns-wincrypt-_privkeyver3) **bitlenQ** field divided by eight ([*little-endian*](https://msdn.microsoft.com/65dd9a04-fc7c-4179-95ff-dac7dad4668f) format). If the bitlenQ value is 0, then the value is absent from the BLOB.                                                                                                                                                                                                  |
| G             | The G value is located directly after the Q value and should always be the length in bytes of the [**DHPRIVKEY\_VER3**](/windows/desktop/api/Wincrypt/ns-wincrypt-_privkeyver3) **bitlenP** field (bit length of P) divided by eight. If the length of the data is one or more bytes shorter than P divided by 8, the data must be padded with the necessary bytes (of zero value) to make the data the desired length ([*little-endian*](https://msdn.microsoft.com/65dd9a04-fc7c-4179-95ff-dac7dad4668f) format).                                                                 |
| J             | The J value is located directly after the G value and should always be the length in bytes of the [**DHPRIVKEY\_VER3**](/windows/desktop/api/Wincrypt/ns-wincrypt-_privkeyver3) **bitlenJ** field divided by eight ([*little-endian*](https://msdn.microsoft.com/65dd9a04-fc7c-4179-95ff-dac7dad4668f) format). If the bitlenJ value is 0, then the value is absent from the BLOB.                                                                                                                                                                                                  |
| Y             | The Y value, (G^X) mod P, is located directly after the J value, and should always be the length in bytes of the [**DHPRIVKEY\_VER3**](/windows/desktop/api/Wincrypt/ns-wincrypt-_privkeyver3) **bitlenP** field (bit length of P) divided by eight. If the length of the data that results from the calculation of (G^X) mod P is one or more bytes shorter than P divided by 8, the data must be padded with the necessary bytes (of zero value) to make the data the desired length ([*little-endian*](https://msdn.microsoft.com/65dd9a04-fc7c-4179-95ff-dac7dad4668f) format). |
| X             | The X value is a random large integer such that the public portion of the DH key pair, Y, is equal to: Y = (G^X) mod P<br/>                                                                                                                                                                                                                                                                                                                                                                                                                      |



 

When calling [**CryptExportKey**](/windows/desktop/api/Wincrypt/nf-wincrypt-cryptexportkey), the developer can choose whether to encrypt the key. The key is encrypted if the *hExpKey* parameter contains a valid handle to a session key. Everything but the [**BLOBHEADER**](/windows/desktop/api/Wincrypt/ns-wincrypt-_publickeystruc) portion of the BLOB is encrypted. Note that the encryption algorithm and encryption key parameters are not stored along with the [*private key BLOB*](https://msdn.microsoft.com/2fe6cfd3-8a2e-4dbe-9fb8-332633daa97a). The application must manage and store this information. If zero is passed for *hExpKey*, the private key will be exported without encryption.

> [!Note]  
> It is dangerous to export private keys without encryption because they are then vulnerable to interception and use by unauthorized entities.

 

 

 



