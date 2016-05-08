Logs
==

## JournalCtl

> journalctl — Query the systemd journal. journalctl may be used to query the contents of the systemd journal as written by systemd-journald.service. [Homepage](https://www.freedesktop.org/software/systemd/man/journalctl.html)

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

Show logging space

```sh
root@edison:~# journalctl --disk-usage
No journal files were found.
Journals take up 0B on disk.
```


