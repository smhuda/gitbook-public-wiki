# SSL/TLS Security

## Downgrade Attack prevention

```text
 openssl s_client –tls1 -fallback_scsv -connect example.com:443
```

If your server supports something better than SSLv3 and checks for the presence of the TLS\_FALLBACK\_SCSV cipher, it should abort the connection with an error like the following:

```text
 tlsv1 alert inappropriate fallback:s3_pkt.c:1262:SSL alert number 86
```

## Cipher Suites

DES Cipher \(Connection should fail\):

```text
 openssl s_client -cipher DES -connect example.com:443

```

### 3DES Cipher \(Connection should fail\)

```text
 openssl s_client -cipher 3DES -connect example.com:443

```

### Export Cipher \(Connection should fail\):

```text
 openssl s_client -cipher EXPORT -connect example.com:443

```

### Low Cipher \(Connection should fail\):

```text
 openssl s_client -cipher LOW -connect example.com:443

```

### RC4 Cipher \(Connection should fail\):

```text
 openssl s_client -cipher RC4 -connect example.com:443

```

### NULL Cipher \(Connection should fail\):

```text
 openssl s_client -cipher NULL -connect example.com:443

```

### Perfect Forward Secrecy Cipher \(Connection should NOT fail\):

```text
 openssl s_client -cipher EECDH, EDH NULL -connect example.com:443

```

## Renegotiation

### **Secure Renegotiation**

```text
 openssl s_client -connect [host]:[port]

```

Testing this should return the following

```text
 Secure Renegotiation IS NOT supported

```

### **Client-initiated Renegotiation**

Once the connection is established, the server will wait for us to type the next command. We can write the following two lines in order to initiate a renegotiation by specifying R in the second line, followed by enter or return.

```text
 openssl s_client -connect [host]:[port]
 
 HEAD / HTTP/1.0
 R
 <Enter or Return key>

```

A system that does not support client-initiated renegotiation will return an error and end the connection, or the connection will time out. Please note that below is just one of the many different error messages that you can encounter when your renegotiation is blocked.

```text
 RENEGOTIATING
 write:errno=104
```

## Logjam

```text
 openssl s_client -connect [host]:[port] -cipher "EDH"
```

The DH parameter size used is displayed in the output next to “Server Temp Key”. Please note that you’ll need at least OpenSSL 1.0.2 to display the ‘Sever Temp Key’ parameter.

```text
 ---
 No client certificate CA names sent
 Peer signing digest: SHA512
 Server Temp Key: DH, 2048 bits
 ---
 SSL handshake has read 6641 bytes and written 455 bytes
 ---
 New, TLSv1/SSLv3, Cipher is DHE-RSA-AES256-GCM-SHA384
 ...

```

## TLS Service Supports Anonymous DH Key Exchange

```text
$ sslscan --xml=sslscan-output.xml [host]:[port]
$ cat sslscan-output.xml | grep -i accept | grep ADH
```

### TLS Insecure Renegotiation Supported

```text
$ openssl s_client -connect [host]:[port]
```

Check the output for the following string: "Secure Renegotiation is NOT supported"

Type "R" with a SINGLE carriage return:

```text
R
```

If the connection stays open, issue an HTTP request with DOUBLE carriage returns:

```text
GET / HTTP/1.0<ENTER><ENTER>
```

If the server replies with some data, it is affected by this issue

### **Determine the server's preferred cipher suite**

Using OpenSSL, we can connect presenting the list of all ciphers:

```text
openssl s_client -connect [host]:[port] -cipher 'ALL:COMPLEMENTOFALL'
```

### Output:

```text
...
...
SSL-Session:
   Protocol  : TLSv1
   Cipher    : AES128-SHA
...
...
```

### TLS Weak Ciphers Supported

```text
sslscan [host]:[port] | grep Accept
```

Any cipher with key length shorter than 128 bit is to be considered weak.

### NULL TLS Ciphers Supported

```text
sslscan [host]:[port] > sslscan.out
cat sslscan.out | grep -i null
```

```text
openssl s_client -connect [host]:[port] -cipher NULL
```

## CRIME Attack

```text
openssl s_client -connect [host]:[port]
OUTPUT:
...
...
Compression: zlib compression
Expansion: zlib comprression
...
Compression: 1 (zlib compression)
```

or the one-liner:

```text
echo -ne "\\n\\n! | openssl s_client -connect [host]:[port] | grep "Compression\\|Expansion"
```

```text
openssl s_client -nextprotoneg NULL [host]:[port]
OUTPUT:
CONNECTED(00000003)
Protocols advertised by server: h2, spdy/3.1, http/1.1
...
```

## BREACH Attack

```text
 openssl s_client -connect [host]:[port]
```

Submitting the following will allow us to see if HTTP compression is supported by the server.

```text
 GET / HTTP/1.1
 Host: [host]
 Accept-Encoding: compress, gzip
```

If the response contains encoded data, similar to the following response, it indicates that HTTP compression is supported; therefore the remote host is vulnerable.

```text
 HTTP/1.1 200 OK
 Server: nginx/1.1.19
 Date: Sun, 19 Mar 2015 20:48:31 GMT
 Content-Type: text/html
 Last-Modified: Thu, 19 Mar 2015 23:34:28 GMT
 Transfer-Encoding: chunked
 Connection: keep-alive
 Content-Encoding: gzip

```

A system which does not support deflate or compression will ignore the compress header request and respond with uncompressed data, indicating that it is not vulnerable.

## HeartBleed Attack

```text
python hb_test.py [host]:[port]
```

Metasploit has a dedicate module that can be used to exploit the vulnerability:

```text
use auxiliary/scanner/ssl/openssl_heartbleed
set RHOST ip_address
set RPORT 443
run
```

Also nmap:

```text
nmap -p 443 --script ssl-heartbleed [host]
```

## FREAK Attack

```text
nmap --script ssl-enum-ciphers -p 443 www.website.com |grep EXPORT
```

A specific tool can be downloaded from [https://tools.keycdn.com/freak](https://tools.keycdn.com/freak)

## SSL Certificate Expired

```text
$openssl s_client -connect [host]:[port]
```

```text
...
...
 Not Before: Oct 26:00:00:00 2011 GMT
      Not After: Sep 30 23:59:59 2013 GMT
...
...
```

## SSL Certificate Signed Using Weak Hashing Algorithm

```text
$openssl s_client -connect [host]:[port]
```

```text
....
....
 Signature Algorithm: sha1WithRSAEncryption
 ...
...
...
```

