---
description: >-
  If you are working as a security professional  support function, you must be
  aware of curl command usage to test for security issues across web
  applications, services and APIs.
---

# CURL

## Test URL with injecting header

You can use curl by inserting a header with your data to test or troubleshoot the particular issue. Let’s see the following example to request with Content-Type.

```text
curl --header 'Content-Type: application/json' http://yoururl.com
```

## Display only response header

If you are doing some troubleshooting and quickly want to check the response header, you can use the following syntax.

```text
curl --head http://yoururl.com
```

## Connect HTTPS/SSL URL and ignore any SSL certificate error

When you try to access SSL/TLS cert secured URL and if that is having the wrong cert or CN doesn’t match, then you will get the following error. Good news, you can instruct cURL to ignore the cert error with `--insecure` flag.

```text
curl --insecure https://yoururl.com
```

## Download file from FTP Server

You can use curl to download the file as well by specifying username and password.

```text
curl -u user:password -O ftp://ftpurl/style.css
```

## Verbose

When we are testing, it’s a good idea to set the verbose mode on. As a result, the commands would provide helpful information such as the resolved IP address, the port we are trying to connect to and the headers.

```text
curl -v http://www.example.com/
```

## DELETE

Again, we specify that we want to use DELETE by using the -X option:

```text
curl -X DELETE http://localhost:8082/spring-rest/foos/9
```

## Miscellaneous

Some other curl flags to check for security of a web application, API or a web service.

```text
curl -LIN <target-url>
curl -X OPTIONS -i [<https://booking.co>](<https://booking.co/>)
curl -i [<https://booking.com>](<https://booking.com/>)
curl -s -D- [<https://booking.com>](<https://booking.com/>)
```

