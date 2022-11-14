# Docker
Instruction for Docker on Linux
```ruby
$ sudo apt update  # обновляемся
$ sudo apt install apt-transport-https  # установить https протокол
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add  # - дабовить ключ
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"  # актуализировать версию
$ sudo apt update  # ещё раз обновляемся
$ sudo apt install docker-ce  # устанавливаем docker
$ sudo systemctl status docker  # проверяем процесс докера
(optional) $ sudo usermod -aG docker $USER  # можно добавить юзера, как рута
```
Docker готов к работе!
```ruby
$ sudo docker run hello-world  # запустить/скачать docker "image" test
$ sudo docker images  # показать "образы", которые есть
$ sudo docker ps  # показать запущенные "контейнеры"
$ sudo docker ps -a  # показать "контейнеры", которые были запущены
$ sudo docker search tomcat  # произвести поиск в консоли по Docker-Hub
$ sudo docker pull tomcat  # скачать "image" tomcat
$ sudo docker run -it -p 8080 tomcat  # запустить "контейнер" it(интерактивно в консоли), p(порт веб-сервера 8080), томкэт
http://192.168.197.128:8080/  # идём тестить в браузер (ip естественно ваш вставляем)
$ sudo docker run -d -p 8080 tomcat  # запустить "контейнер" deamon (как процесс)
$ sudo docker run -d -p 8888:80 nginx  # запустить "контейнер" deamon (как процесс), p(делаем переброс порта веб-сервера с 80 на 8888), nginx
$ sudo docker stop e1d090e425fd  # остановить "контейнер" CONTAINER ID
$ sudo docker rm ada1329e87c9  # стереть "контейнер" CONTAINER ID (который не используется)
$ sudo docker rmi tomcat  # удалить "образ" REPOSITORY
```




## Dont write!!!
docker build -t denis .
docker images

docker run -it  -p 1234:80  denis:latest
docker run -d -p  1234:80  denis:latest

docker  ps     # list containers
docker  ps -a  # list all containers

docker tag denis_ubuntu denis_ubuntu-PROD
docker tag denis_ubuntu denis_ubuntu-PROD:v2

docker rm   # delete container
docker rmi  # delete image

UPDATE IMAGE
~~~~~~~~~~~~~
docker run -d -p 7777:80 denis_ubuntu4
docker exec -it 5267e21d140 /bin/bash
echo "V2" >> /var/www/html/index.html
exit
docker commit 5267e21d140 denis_v2:latest

Export/Import Docker Image to file
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
docker save image:tag > arch_name.tar
docker load -i arch_name.tar


Import/Export Docker Image to AWS ECR
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
docker build -t denis:v1 .
aws ecr get-login --no-include-email --region=ca-central-1 
docker tag  denis:v1  12345678.dkr.ecr.ca-central-1.amazonaws.com/myrepo:latest
docker push 12345678.dkr.ecr.ca-central-1.amazonaws.com/myrepo:lastest

docker pull 12345678.dkr.ecr.ca-central-1.amazonaws.com/myrepo:latest



Kill and Delete Containers and Images
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
docker rm -f $(docker ps -aq)        # Delete all Containers
docker rmi -f $(docker images -q)    # Delete all Images


# docker network ls - посмотреть сети подключения докера
# lsof -i -P -n  | grep docker - посмотреть открытые порты докера
