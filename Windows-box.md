1. cracking pfx files 

use https://github.com/crackpkcs12/crackpkcs12 to get the password for the pfx file and then use openssl to get the certificate out of the file. 
(forked it in https://github.com/anindya14/crackpkcs12)

openssl pkcs12 -clcerts -nokeys -in legacyy_dev_auth.pfx -out priv-key.pem

when promped for the import password use the password found by using the crackpkcs12 tool.

