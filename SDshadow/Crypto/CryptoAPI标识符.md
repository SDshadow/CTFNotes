| Identifier                | Value      | Description                                                  |
| :------------------------ | :--------- | :----------------------------------------------------------- |
| CALG_3DES                 | 0x00006603 | [*Triple DES*](https://learn.microsoft.com/en-us/windows/desktop/SecGloss/t-gly) encryption algorithm. |
| CALG_3DES_112             | 0x00006609 | Two-key [*triple DES*](https://learn.microsoft.com/en-us/windows/desktop/SecGloss/t-gly) encryption with effective key length equal to 112 bits. |
| CALG_AES                  | 0x00006611 | Advanced Encryption Standard (AES). This algorithm is supported by the [Microsoft AES Cryptographic Provider](https://learn.microsoft.com/en-us/windows/win32/seccrypto/microsoft-aes-cryptographic-provider). |
| CALG_AES_128              | 0x0000660e | 128 bit AES. This algorithm is supported by the [Microsoft AES Cryptographic Provider](https://learn.microsoft.com/en-us/windows/win32/seccrypto/microsoft-aes-cryptographic-provider). |
| CALG_AES_192              | 0x0000660f | 192 bit AES. This algorithm is supported by the [Microsoft AES Cryptographic Provider](https://learn.microsoft.com/en-us/windows/win32/seccrypto/microsoft-aes-cryptographic-provider). |
| CALG_AES_256              | 0x00006610 | 256 bit AES. This algorithm is supported by the [Microsoft AES Cryptographic Provider](https://learn.microsoft.com/en-us/windows/win32/seccrypto/microsoft-aes-cryptographic-provider). |
| CALG_AGREEDKEY_ANY        | 0x0000aa03 | Temporary algorithm identifier for handles of Diffie-Hellman–agreed keys. |
| CALG_CYLINK_MEK           | 0x0000660c | An algorithm to create a 40-bit DES key that has parity bits and zeroed key bits to make its key length 64 bits. This algorithm is supported by the [Microsoft Base Cryptographic Provider](https://learn.microsoft.com/en-us/windows/win32/seccrypto/microsoft-base-cryptographic-provider). |
| CALG_DES                  | 0x00006601 | DES encryption algorithm.                                    |
| CALG_DESX                 | 0x00006604 | DESX encryption algorithm.                                   |
| CALG_DH_EPHEM             | 0x0000aa02 | Diffie-Hellman ephemeral key exchange algorithm.             |
| CALG_DH_SF                | 0x0000aa01 | Diffie-Hellman store and forward key exchange algorithm.     |
| CALG_DSS_SIGN             | 0x00002200 | DSA [*public key*](https://learn.microsoft.com/en-us/windows/desktop/SecGloss/p-gly) signature algorithm. |
| CALG_ECDH                 | 0x0000aa05 | Elliptic curve Diffie-Hellman key exchange algorithm. **Note:** This algorithm is supported only through [Cryptography API: Next Generation](https://learn.microsoft.com/en-us/windows/desktop/SecCNG/cng-portal). **Windows Server 2003 and Windows XP:** This algorithm is not supported. |
| CALG_ECDH_EPHEM           | 0x0000ae06 | Ephemeral elliptic curve Diffie-Hellman key exchange algorithm. **Note:** This algorithm is supported only through [Cryptography API: Next Generation](https://learn.microsoft.com/en-us/windows/desktop/SecCNG/cng-portal). **Windows Server 2003 and Windows XP:** This algorithm is not supported. |
| CALG_ECDSA                | 0x00002203 | Elliptic curve digital signature algorithm. **Note:** This algorithm is supported only through [Cryptography API: Next Generation](https://learn.microsoft.com/en-us/windows/desktop/SecCNG/cng-portal). **Windows Server 2003 and Windows XP:** This algorithm is not supported. |
| CALG_ECMQV                | 0x0000a001 | Elliptic curve Menezes, Qu, and Vanstone (MQV) key exchange algorithm. This algorithm is not supported. |
| CALG_HASH_REPLACE_OWF     | 0x0000800b | One way function hashing algorithm.                          |
| CALG_HUGHES_MD5           | 0x0000a003 | Hughes MD5 hashing algorithm.                                |
| CALG_HMAC                 | 0x00008009 | HMAC keyed hash algorithm. This algorithm is supported by the [Microsoft Base Cryptographic Provider](https://learn.microsoft.com/en-us/windows/win32/seccrypto/microsoft-base-cryptographic-provider). |
| CALG_KEA_KEYX             | 0x0000aa04 | KEA key exchange algorithm (FORTEZZA). This algorithm is not supported. |
| CALG_MAC                  | 0x00008005 | [*MAC*](https://learn.microsoft.com/en-us/windows/desktop/SecGloss/m-gly) keyed hash algorithm. This algorithm is supported by the [Microsoft Base Cryptographic Provider](https://learn.microsoft.com/en-us/windows/win32/seccrypto/microsoft-base-cryptographic-provider). |
| CALG_MD2                  | 0x00008001 | MD2 hashing algorithm. This algorithm is supported by the [Microsoft Base Cryptographic Provider](https://learn.microsoft.com/en-us/windows/win32/seccrypto/microsoft-base-cryptographic-provider). |
| CALG_MD4                  | 0x00008002 | MD4 hashing algorithm.                                       |
| CALG_MD5                  | 0x00008003 | MD5 hashing algorithm. This algorithm is supported by the [Microsoft Base Cryptographic Provider](https://learn.microsoft.com/en-us/windows/win32/seccrypto/microsoft-base-cryptographic-provider). |
| CALG_NO_SIGN              | 0x00002000 | No signature algorithm.                                      |
| CALG_OID_INFO_CNG_ONLY    | 0xffffffff | The algorithm is only implemented in CNG. The macro, IS_SPECIAL_OID_INFO_ALGID, can be used to determine whether a cryptography algorithm is only supported by using the CNG functions. |
| CALG_OID_INFO_PARAMETERS  | 0xfffffffe | The algorithm is defined in the encoded parameters. The algorithm is only supported by using CNG. The macro, IS_SPECIAL_OID_INFO_ALGID, can be used to determine whether a cryptography algorithm is only supported by using the CNG functions. |
| CALG_PCT1_MASTER          | 0x00004c04 | Used by the Schannel.dll operations system. This **ALG_ID** should not be used by applications. |
| CALG_RC2                  | 0x00006602 | RC2 block encryption algorithm. This algorithm is supported by the [Microsoft Base Cryptographic Provider](https://learn.microsoft.com/en-us/windows/win32/seccrypto/microsoft-base-cryptographic-provider). |
| CALG_RC4                  | 0x00006801 | RC4 stream encryption algorithm. This algorithm is supported by the [Microsoft Base Cryptographic Provider](https://learn.microsoft.com/en-us/windows/win32/seccrypto/microsoft-base-cryptographic-provider). |
| CALG_RC5                  | 0x0000660d | RC5 block encryption algorithm.                              |
| CALG_RSA_KEYX             | 0x0000a400 | RSA public key exchange algorithm. This algorithm is supported by the [Microsoft Base Cryptographic Provider](https://learn.microsoft.com/en-us/windows/win32/seccrypto/microsoft-base-cryptographic-provider). |
| CALG_RSA_SIGN             | 0x00002400 | RSA public key signature algorithm. This algorithm is supported by the [Microsoft Base Cryptographic Provider](https://learn.microsoft.com/en-us/windows/win32/seccrypto/microsoft-base-cryptographic-provider). |
| CALG_SCHANNEL_ENC_KEY     | 0x00004c07 | Used by the Schannel.dll operations system. This **ALG_ID** should not be used by applications. |
| CALG_SCHANNEL_MAC_KEY     | 0x00004c03 | Used by the Schannel.dll operations system. This **ALG_ID** should not be used by applications. |
| CALG_SCHANNEL_MASTER_HASH | 0x00004c02 | Used by the Schannel.dll operations system. This **ALG_ID** should not be used by applications. |
| CALG_SEAL                 | 0x00006802 | SEAL encryption algorithm. This algorithm is not supported.  |
| CALG_SHA                  | 0x00008004 | SHA hashing algorithm. This algorithm is supported by the [Microsoft Base Cryptographic Provider](https://learn.microsoft.com/en-us/windows/win32/seccrypto/microsoft-base-cryptographic-provider). |
| CALG_SHA1                 | 0x00008004 | Same as **CALG_SHA**. This algorithm is supported by the [Microsoft Base Cryptographic Provider](https://learn.microsoft.com/en-us/windows/win32/seccrypto/microsoft-base-cryptographic-provider). |
| CALG_SHA_256              | 0x0000800c | 256 bit SHA hashing algorithm. This algorithm is supported by Microsoft Enhanced RSA and AES Cryptographic Provider..**Windows XP with SP3:** This algorithm is supported by the Microsoft Enhanced RSA and AES Cryptographic Provider (Prototype). **Windows XP with SP2, Windows XP with SP1 and Windows XP:** This algorithm is not supported. |
| CALG_SHA_384              | 0x0000800d | 384 bit SHA hashing algorithm. This algorithm is supported by Microsoft Enhanced RSA and AES Cryptographic Provider.**Windows XP with SP3:** This algorithm is supported by the Microsoft Enhanced RSA and AES Cryptographic Provider (Prototype). **Windows XP with SP2, Windows XP with SP1 and Windows XP:** This algorithm is not supported. |
| CALG_SHA_512              | 0x0000800e | 512 bit SHA hashing algorithm. This algorithm is supported by Microsoft Enhanced RSA and AES Cryptographic Provider.**Windows XP with SP3:** This algorithm is supported by the Microsoft Enhanced RSA and AES Cryptographic Provider (Prototype). **Windows XP with SP2, Windows XP with SP1 and Windows XP:** This algorithm is not supported. |
| CALG_SKIPJACK             | 0x0000660a | Skipjack block encryption algorithm (FORTEZZA). This algorithm is not supported. |
| CALG_SSL2_MASTER          | 0x00004c05 | Used by the Schannel.dll operations system. This **ALG_ID** should not be used by applications. |
| CALG_SSL3_MASTER          | 0x00004c01 | Used by the Schannel.dll operations system. This **ALG_ID** should not be used by applications. |
| CALG_SSL3_SHAMD5          | 0x00008008 | Used by the Schannel.dll operations system. This **ALG_ID** should not be used by applications. |
| CALG_TEK                  | 0x0000660b | TEK (FORTEZZA). This algorithm is not supported.             |
| CALG_TLS1_MASTER          | 0x00004c06 | Used by the Schannel.dll operations system. This **ALG_ID** should not be used by applications. |
| CALG_TLS1PRF              | 0x0000800a | Used by the Schannel.dll operations system. This **ALG_ID** should not be used by applications. |