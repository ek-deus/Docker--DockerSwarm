УСТАНОВКА
Установка Docker Swarm
curl -ssl https://get.docker.com | bash

Прим. перев.: в Docker версий 1.12.0+ ничего дополнительно устанавливать не требуется, т.к. Docker Swarm встроен в Docker Engine в виде специального режима (Swarm mode).


НАСТРОЙКА
Инициализация Swarm
docker swarm init --advertise-addr 192.168.10.1
Подключение рабочего узла (worker) к Swarm
docker swarm join-token worker
Подключение управляющего узла (manager) к Swarm
docker swarm join-token manager
РАБОТА
Список сервисов
docker service ls
Список узлов
docker node ls
Создание сервиса
docker service create --name vote -p 8080:80 instavote/vote
Список заданий Swarm
docker service ps
Масштабирование сервиса
docker service scale vote=3
Обновление сервиса
docker service update --image instavote/vote:movies vote

docker service update --force --update-parallelism 1 --update-delay 30s nginx

docker service update --update-parallelism 5--update-delay 2s --image instavote/vote:indent vote

docker service update --limit-cpu 2 nginx

docker service update --replicas=5 nginx
ШПАРГАЛКИ
