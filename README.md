# Keenetic Extra - Wiki

### Для работы по ssh
`$ ssh admin@192.168.0.1`


### Команды ОС
http://docs.help.keenetic.com/cli/3.1/en/cli_manual_kn-1710_tr.pdf


### Работа с файловой структурой
В системе доступны несколько ресурсов. Их можно увидеть командой `ls`. Например файлы конфигов можно использовать напрямую по алиасу
```
(config)> more startup-config
```

в общем случае нужно указывать полный путь (с указанием ресурса)
```
(config)> ls flash:/
(config)> more storage:/backups/startup-config
```


### Бакапы
Бакап конфига лежит в storage (в папке backups)
```
(config)> ls storage:/backups
```

Чтобы загрузить этот конфиг для дальнейшего использования (вступает в силу после перезагрузки)
```
(config)> copy storage:/backups/startup-config startup-config
```

Чтобы попробовать этот конфиг без перезаписи постоянного конфига
```
(config)> copy storage:/backups/startup-config running-config
```

### Подключение по ftp / sftp
При подключении по *ftp* открывается список конфиг файлов и лог, а также файл прошивки.

При подключении по *sftp* открывается структура всех файлов в директории `/tmp/mnt`, при этом хранилище доступно по пути `/storage`.

### Если не работает веб-интерфейс
Попробуй по `ssh` обновить прошивку
```
(config)> components list
(config)> components commit
```
Соединение отключится и роутер будет недоступен некоторое время.
