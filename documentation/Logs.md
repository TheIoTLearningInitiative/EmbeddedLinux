# Logs

Limit 

```sh
    root@edison:~# nano /etc/systemd/journald.conf
    SystemMaxUse=20M
```

```sh
    root@edison:~# nano /etc/systemd/journald.conf
    Storage=persistent
    Storage=None
```

```sh
    root@edison:~# cd /var/log/journal/
    root@edison:/var/log/journal# rm -rf *
```

