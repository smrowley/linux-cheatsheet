# Linux Cheatsheet

This is just a conglomeration of linux commands used to troubleshoot or do various things.

## Networking

### Use `openssl` to retrieve tls certs from server

#### With SNI

```
openssl s_client -showcerts -servername www.example.com -connect www.example.com:443 </dev/null
```

#### Without SNI

```
openssl s_client -showcerts -connect www.example.com:443 </dev/null
```

#### Full details

```
echo | \
    openssl s_client -servername www.example.com -connect www.example.com:443 2>/dev/null | \
    openssl x509 -text
```

For more details:

https://stackoverflow.com/questions/7885785/using-openssl-to-get-the-certificate-from-a-server


### Use `curl` with SNI

```
curl -vik --resolve example.com:443:198.18.110.10 https://example.com/
```