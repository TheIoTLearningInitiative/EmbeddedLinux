# Logs

```
root@edison:~# nano /etc/systemd/journald.conf
Storage=persistent
Storage=None
root@edison:~# nano /etc/systemd/journald.conf
SystemMaxUse=20M
root@edison:~# cd /var/log/journal/
root@edison:/var/log/journal# rm -rf *
```

