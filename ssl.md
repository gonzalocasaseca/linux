# SSL Notes

## Get SSL certificate and check expiration date
Connected to the LDAP server via openssl s_client:

~~~bash
openssl s_client -connect 1.2.3.4:443
~~~

Copy everything between ```-----BEGIN CERTIFICATE-----``` and ```-----END CERTIFICATE-----``` (including these delimiters) and paste it in a new text file.

Or:

~~~bash
echo -n | openssl s_client -connect 1.2.3.4:443 | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > server.pem
~~~

Then ran:

~~~bash
openssl x509 -in ./server.cert -noout -text
~~~

Look for the Validity field:

~~~bash
Validity
Not Before: Sep 10 00:00:00 2012 GMT
Not After : Sep 15 12:00:00 2014 GMT
~~~

**Or all in one**

~~~bash
echo | openssl s_client -connect 1.2.3.4:443 2>/dev/null | openssl x509 -noout -dates
~~~