# Docker
Instruction for Docker on Linux
```ruby
$ apt-get update                       # обновляемся
$ apt-get install apt-transport-https  # установить https протокол
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add  # - дабовить ключ
$ add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"  # актуализировать версию
$ apt-get update                 # ещё раз обновляемся
$ apt-get install docker-ce      # устанавливаем docker
$ systemctl status docker        # проверяем процесс докера
$ sudo usermod -aG docker $USER  # можно добавить юзера, как рута (optional)
```
Docker готов к работе!
```ruby
$ docker run hello-world  # запустить/скачать docker "image" test
$ docker images           # показать "образы", которые есть
$ docker ps               # показать запущенные "контейнеры"
$ docker ps -a            # показать "контейнеры", которые были запущены
$ docker search tomcat    # произвести поиск в консоли по Docker-Hub
$ docker pull tomcat      # скачать "image" tomcat
$ docker push name_image  # загрузить образ в Docker-Hub
$ docker run -it -p 8080 tomcat   # запустить "контейнер" it(интерактивно в консоли), p(порт веб-сервера 8080), томкэт
http://192.168.197.128:8080/      # идём тестить в браузер (ip естественно ваш вставляем)
$ docker run -d -p 8080 tomcat    # запустить "контейнер" deamon (как процесс)
$ docker run -d -p 8888:80 nginx  # запустить "контейнер" deamon (как процесс), p(делаем переброс порта веб-сервера с 80 на 8888), nginx
$ docker stop e1d090e425fd        # остановить "контейнер" CONTAINER ID
$ docker rm ada1329e87c9          # удалить "контейнер" CONTAINER ID (который не используется)
$ docker rmi tomcat               # удалить "образ" REPOSITORY
$ docker network ls               # посмотреть сети подключения докера
$ lsof -i -P -n  | grep docker    # посмотреть открытые порты докера
$ docker start                    # запустить контейнер
$ docker logs                     # посмотреть логи контейнера
$ docker exec                     # запустить команду внутри контейнера
$ docker stop name_container      # остановить контейнер
$ docker stop $(docker ps -a -q)  # остановить все контейнеры
$ docker kill name_container      # резко остановить контейнер
docker build -t [имя-образа] [путь-до-dockerfile]    # создать образ из Dockerfile
```
