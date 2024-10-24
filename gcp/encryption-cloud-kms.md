# Encryption
- It is process of secret way of hiding the actual text. it can be password, files,  etc..
- It must be done at 3 stages
  - Data at Rest
  - Data in Motion
  - Data in Transit

> Encryption ways
  - Symmetric Key Encryption
    - Same key for both encyption and decryption 
  - ASymmetric Key Encryption
    - public key for encryption but private key for decryption
    - It uses public key cryptography such as RSA
   
# Cloud KMS
- It is key management service, which creates & manages cryptographic keys
- controls the use in applicaitons & gcp services
- It provides api for encrypt, decrypt or sign data
- It uses existing cryptography keys create on premises
- Integrates with most of gcp services by encypting data in multiple ways
  - Google Managed Key: No configuration
  - Custom Managed Key: Key managed by KMS
  - Customer Supplied Key: User defined key
- It is useful for both software and hardware
- Example: we can use in VM's configuration 
