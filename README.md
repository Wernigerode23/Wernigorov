# Домашнее задание к занятию 3 «Резервное копирование» Вернигоров Дмитрий

### Задание 1
- Составьте команду rsync, которая позволяет создавать зеркальную копию домашней директории пользователя в директорию `/tmp/backup`
- Необходимо исключить из синхронизации все директории, начинающиеся с точки (скрытые)
- Необходимо сделать так, чтобы rsync подсчитывал хэш-суммы для всех файлов, даже если их время модификации и размер идентичны в источнике и приемнике.
- На проверку направить скриншот с командой и результатом ее выполнения

###  Решение 1
```
rsync -ac --delete --exclude=".*/" . /tmp/backup
```
![image](https://github.com/Wernigerode23/Wernigorov/assets/153208339/88732638-b29f-42df-a9c9-959ccfada1ff)



### Задание 2
- Написать скрипт и настроить задачу на регулярное резервное копирование домашней директории пользователя с помощью rsync и cron.
- Резервная копия должна быть полностью зеркальной
- Резервная копия должна создаваться раз в день, в системном логе должна появляться запись об успешном или неуспешном выполнении операции
- Резервная копия размещается локально, в директории `/tmp/backup`
- На проверку направить файл crontab и скриншот с результатом работы утилиты.

### Решение 2

```
rsync -a --delete /home/joos/ /tmp/backup

if [ "$?" -eq 0 ]; then
        logger "Backup successfully"
else    logger "Backup failed"
fi
```
```
0 * * * * /home/joos/rsync.sh
```

![2](https://github.com/znak72/klaster3/blob/main/2.png)
