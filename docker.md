Установка docker:

«Освежаем» операционную систему:
sudo apt-get update -y && sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y && sudo apt autoremove -y

Устанавливаем необходимые зависимости:
sudo apt-get -y install apt-transport-https ca-certificates curl software-properties-common

Импортитруем PGP-ключи
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

Добавляем нужный репозиторий
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(. /etc/os-release; echo "$UBUNTU_CODENAME") stable"

Обновляем списки репозиториев:
sudo apt-get update

Устанавливаем Docker:
sudo apt-get -y  install docker-ce docker-compose

После установки добавляем нашего текущего пользователя в группу docker
sudo groupadd docker
sudo gpasswd -a $USER docker
[//]: # (sudo usermod -aG docker $USER)

Пробуем запустить Докер:
docker run hello-world

Если всё ОК, то в результате Вы получите примерно следующее:
[sudo] пароль для ivan:        
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
719385e32844: Pull complete
Digest: sha256:88ec0acaa3ec199d3b7eaf73588f4518c25f9d34f58ce9a0df68429c5af48e8d
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
1. The Docker client contacted the Docker daemon.
2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
   (amd64)
3. The Docker daemon created a new container from that image which runs the
   executable that produces the output you are currently reading.
4. The Docker daemon streamed that output to the Docker client, which sent it
   to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
$ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
https://hub.docker.com/

For more examples and ideas, visit:
https://docs.docker.com/get-started/

==============================   Restart computer!!!   ==================================

Основные команды:
docker --version
Какие сборки есть список:
docker images

Какие рабочие контейнеры список:
docker ps

Все контейнеры включая нерабочие список:
docker ps -a

Удаление контейнера по имени:
docker rm NAME

Удаление контейнера по id:
docker rm d5bf324da929

Удаление контейнеров
docker rmi $(docker images -a -q) 

Удаление контейнера по id вложенным запросом получаем id:
docker rm $(sudo docker ps -a -q)

CMD ["java", "-jar", "/opt/app/japp.jar"]
docker stop some_name_or_id
docker stop some_container_name
docker run --name some_container_name -d --rm some
docker volume ls
docker volume create some_name

Устанавливаем postgresql:
docker run --name PG12-alpine -p 5432:5432 -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=zxcv -e POSTGRES_DB=GPN -d postgres:12-alpine