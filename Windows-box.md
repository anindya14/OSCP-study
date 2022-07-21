1. cracking pfx files 

use https://github.com/crackpkcs12/crackpkcs12 to get the password for the pfx file and then use openssl to get the certificate out of the file. 
(forked it in https://github.com/anindya14/crackpkcs12)

Command for Extracting the private key 
openssl pkcs12 -in legacyy_dev_auth.pfx -nocerts -out priv-key.pem -nodes

when promped for the import password use the password found by using the crackpkcs12 tool.

Command for extracting the certificate
openssl pkcs12 -in legacyy_dev_auth.pfx -clcerts -nokeys -out certificate.pem
