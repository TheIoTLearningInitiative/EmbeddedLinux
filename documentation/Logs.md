Logs
==

## JournalCtl



Show logging space

```sh
    root@edison:~# journalctl --disk-usage
```

Limit logging space

```sh
    root@edison:~# nano /etc/systemd/journald.conf
    SystemMaxUse=20M
```

 Stop logging

```sh
    root@edison:~# nano /etc/systemd/journald.conf
    #Storage=persistent
    Storage=None
```

Remove all logs

```sh
    root@edison:~# cd /var/log/journal/
    root@edison:/var/log/journal# rm -rf *
```

