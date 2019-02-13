## Autenticación
```
root@edge init.d]# kinit kode30
Password for kode30@KODE.COM:

```
## Validamos Ticket
```
[root@edge init.d]# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: kode30@KODE.COM

Valid starting       Expires              Service principal
02/13/2019 15:22:54  02/14/2019 15:22:54  krbtgt/KODE.COM@KODE.COM
```
