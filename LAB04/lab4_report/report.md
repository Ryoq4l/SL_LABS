Файлы и права доступа

    whoami > files/1_info.txt – запись имени пользователя в файл.

    pwd >> files/1_info.txt – добавление текущей директории.

    uname -a >> files/1_info.txt – добавление информации об ОС.

    echo "This is a secret file..." > ~/secret.txt – создание секретного файла.

    chmod go-rw ~/secret.txt – запрет чтения/записи для группы и других.

    cat ~/secret.txt > files/secret_backup.md – создание резервной копии.

    chmod 755 files/secret_backup.md – установка прав rwxr-xr-x.

    mv ~/secret.txt files/ – перемещение секретного файла.

    sudo chown root files/secret_backup.md – смена владельца на root.

    ls /etc/host* > files/8_etc_hosts.txt – список файлов, начинающихся на host.

    find /var/log -type f -mtime -7 > files/9_recent_logs.txt – файлы в /var/log, изменённые за 7 дней.

Пользователи и группы

    sudo useradd -m -s /bin/bash auditor – создание пользователя auditor.

    sudo usermod -aG sudo auditor – добавление auditor в группу sudo.

    echo "auditor:password123" | sudo chpasswd – установка пароля.

    sudo su - auditor -c "echo 'Audit report...' > /home/auditor/audit_report.txt" – создание файла отчёта.

    sudo cp /home/auditor/audit_report.txt files/14_audit_report.txt – копирование отчёта.

    sudo userdel -r auditor – удаление пользователя и домашней директории.

    cat /etc/passwd | cut -d: -f1 > files/16_users.txt – список всех пользователей системы.

Поиск файлов и содержимого

    grep -r "localhost" /etc/ 2>/dev/null | cut -d: -f1 | uniq > files/17_localhost_files.txt – поиск файлов с localhost.

    find /usr/bin -type f -executable -user root > files/18_root_binaries.txt – исполняемые файлы root.

    find ~ -type f -size +1M > files/19_large_files.txt – файлы больше 1 МБ.

    mkdir test_search – создание тестовой папки.

    echo "port=8080" > test_search/data1.conf – создание конфигурационного файла.

    echo "debug=true" > test_search/data2.conf – создание конфигурационного файла.

    touch test_search/readme.txt – создание пустого файла.

    grep -l "port\|debug" test_search/* > files/21_config_files.txt – поиск файлов с port или debug.

    find test_search -type f -empty -delete – удаление пустых файлов.

Управление процессами

    sleep 1h & – запуск процесса sleep в фоне.

    ps -u $USER > files/24_my_processes.txt – список процессов текущего пользователя.

    pkill sleep – завершение процесса sleep.

    ps aux | grep systemd > files/27_systemd_processes.txt – поиск процессов systemd.

Часть 5: Системные журналы и мониторинг

    tail -20 /var/log/syslog > files/28_syslog_tail.txt – последние 20 строк syslog.

    grep "failed" /var/log/auth.log > files/29_failed_logins.txt – неудачные попытки входа.

    dpkg -l > files/30_installed_packages.txt – список установленных пакетов.

    ss -tuln > files/31_open_ports.txt – открытые порты системы.

Резервное копирование и архивация

    tar -czf lab4_files_backup.tar.gz files/ – архивация папки files.

    rm -rf files – удаление исходной папки.

    tar -xzf lab4_files_backup.tar.gz – восстановление из архива.

    cp -r ~/lab4_report ~/lab4_final – создание копии папки.

    rm -rf ~/lab4_final – удаление копии.

    tree ~/lab4_report > files/36_tree.txt – дерево директории.

git

    mkdir -p ~/SL_LABS/LAB04 – создание папки LAB04 в репозитории.

    cp -r ~/lab4_report ~/SL_LABS/LAB04/ – копирование отчёта.

    cd ~/SL_LABS – переход в репозиторий.

    git add . – добавление изменений.

    git commit -m "Lab 4: файлы, процессы, пользователи, поиск" – коммит.

    git push origin main – отправка на GitHub.
