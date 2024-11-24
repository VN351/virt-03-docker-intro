# Задание 1

Сценарий выполнения задачи:
   - Установите docker и docker compose plugin на свою linux рабочую станцию или ВМ.
   - Если dockerhub недоступен создайте файл /etc/docker/daemon.json с содержимым: `{"registry-mirrors": ["https://mirror.gcr.io", "https://daocloud.io", "https://c.163.com/", "https://registry.docker-cn.com"]}`
   - Зарегистрируйтесь и создайте публичный репозиторий с именем "custom-nginx" на https://hub.docker.com (ТОЛЬКО ЕСЛИ У ВАС ЕСТЬ ДОСТУП);
   - скачайте образ nginx:1.21.1;
   - Создайте Dockerfile и реализуйте в нем замену дефолтной индекс-страницы(/usr/share/nginx/html/index.html), на файл index.html с содержимым:
   ```
   <html>
   <head>
   Hey, Netology
   </head>
   <body>
   <h1>I will be DevOps Engineer!</h1>
   </body>
   </html>
   ```
   - Соберите и отправьте созданный образ в свой dockerhub-репозитории c tag 1.0.0 (ТОЛЬКО ЕСЛИ ЕСТЬ ДОСТУП).
   - Предоставьте ответ в виде ссылки на https://hub.docker.com/<username_repo>/custom-nginx/general.

# Ответ к заданию 1

[Ссылка не репозиторий](https://hub.docker.com/repository/docker/venom3191/custom-nginx/general)

# Задание 2

1. Запустите ваш образ custom-nginx:1.0.0 командой docker run в соответвии с требованиями:
   - имя контейнера "ФИО-custom-nginx-t2"
   - контейнер работает в фоне
   - контейнер опубликован на порту хост системы 127.0.0.1:8080
2. Не удаляя, переименуйте контейнер в "custom-nginx-t2"
3. Выполните команду `date +"%d-%m-%Y %T.%N %Z" ; sleep 0.150 ; docker ps ; ss -tlpn | grep 127.0.0.1:8080  ; docker logs custom-nginx-t2 -n1 ; docker exec -it custom-nginx-t2 base64 /usr/share/nginx/html/index.html`
4. Убедитесь с помощью curl или веб браузера, что индекс-страница доступна.
В качестве ответа приложите скриншоты консоли, где видно все введенные команды и их вывод.

# Ответ к заданию 2

![alt text](https://github.com/VN351/virt-03-docker-intro/raw/main/images/task-2.png)

# Задание 3

1. Воспользуйтесь docker help или google, чтобы узнать как подключиться к стандартному потоку ввода/вывода/ошибок контейнера "custom-nginx-t2".
2. Подключитесь к контейнеру и нажмите комбинацию Ctrl-C.
3. Выполните docker ps -a и объясните своими словами почему контейнер остановился.
4. Перезапустите контейнер
5. Зайдите в интерактивный терминал контейнера "custom-nginx-t2" с оболочкой bash.
6. Установите любимый текстовый редактор(vim, nano итд) с помощью apt-get.
7. Отредактируйте файл "/etc/nginx/conf.d/default.conf", заменив порт "listen 80" на "listen 81".
8. Запомните(!) и выполните команду nginx -s reload, а затем внутри контейнера curl http://127.0.0.1:80 ; curl http://127.0.0.1:81.
9. Выйдите из контейнера, набрав в консоли exit или Ctrl-D.
10. Проверьте вывод команд: ss -tlpn | grep 127.0.0.1:8080 , docker port custom-nginx-t2, curl http://127.0.0.1:8080. Кратко объясните суть возникшей проблемы.
11.   - Это дополнительное, необязательное задание. Попробуйте самостоятельно исправить конфигурацию контейнера, используя доступные источники в интернете. Не изменяйте конфигурацию nginx и не удаляйте контейнер. Останавливать контейнер можно. пример источника
12. Удалите запущенный контейнер "custom-nginx-t2", не останавливая его.(воспользуйтесь --help или google)

# Ответы к заданию 3

1. ![alt text](https://github.com/VN351/virt-03-docker-intro/raw/main/images/task-3-1.png)
2. - 3. ![alt text](https://github.com/VN351/virt-03-docker-intro/raw/main/images/task-3-2.png)
   ### Объяснение
      - Контейнеры Docker работают в изолированном окружении, и их жизненный цикл напрямую связан с основным процессом, запущенным внутри. Если основной процесс завершает работу (например, из-за получения сигнала SIGINT), контейнер также останавливается.
4. 6. ![alt text](https://github.com/VN351/virt-03-docker-intro/raw/main/images/task-3-3.png)
7. 


