# Mounting NFS Shares

### How Do I Find Out Shared Directories?

```text
$ showmount -e nas01
$ showmount -e nfs-server-ip-address-here
$ showmount -e nas01.lan.nixcraft.net.in
```

### Mac OS X NFS mount Command

```text
$ sudo mkdir /private/nfs
```

```text
$ sudo mount -t nfs 192.168.3.1:/mp3 /private/nfs
```

#### Tip: Operation not permitted Error

Try to mount it as follows with -o **resvport** command:

```text
$ sudo mount -t nfs -o resvport 192.168.3.1:/mp3 /private/nfs
```

OR mount an NFS in read/write mode, enter:

```text
$ sudo mount -t nfs -o resvport,rw 192.168.3.1:/mp3 /private/nfs
```

