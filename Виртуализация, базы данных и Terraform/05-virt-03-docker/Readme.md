## Задача 1

Сценарий выполения задачи:

- создайте свой репозиторий на https://hub.docker.com;
- выберете любой образ, который содержит веб-сервер Nginx;
- создайте свой fork образа;
- реализуйте функциональность:
запуск веб-сервера в фоне с индекс-страницей, содержащей HTML-код ниже:
```
<html>
<head>
Hey, Netology
</head>
<body>
<h1>I’m DevOps Engineer!</h1>
</body>
</html>
```
Опубликуйте созданный форк в своем репозитории и предоставьте ответ в виде ссылки на https://hub.docker.com/username_repo.
*** 
### Ответ:
###### Кратко. Ссылка на образ: https://hub.docker.com/repository/docker/pupsik/netology-nginx

###### Подробнее:
Создан html файл с заданным содержимым.
Создан Dockerfile со следующим содержимым:
```
    FROM nginx:1.21.5
    COPY ./index.html /usr/share/nginx/html/index.html
```
Выполнен build:
```
docker build -t pupsik/netology-nginx:1.0.0 .
```
И push в hub.docker:
```
docker push pupsik/netology-nginx:1.0.0
```
Для проверки задачи с запуском nginx в фоне с заданным html:
1. Получить образ:
```
docker pull pupsik/netology-nginx:1.0.0
```
2. Выполнить команду:
```
docker run -d --name example_nginx -p 8080:80  pupsik/netology-nginx:1.0.0
```
3. Открыть localhost:8080 (например через curl):
```
curl localhost:8080
<html>
<head>
Hey, Netology
</head>
<body>
<h1>Im DevOps Engineer!</h1>
</body>
</html>
```



## Задача 2

Посмотрите на сценарий ниже и ответьте на вопрос:
"Подходит ли в этом сценарии использование Docker контейнеров или лучше подойдет виртуальная машина, физическая машина? Может быть возможны разные варианты?"

Детально опишите и обоснуйте свой выбор.

--

Сценарий:

Высоконагруженное монолитное java веб-приложение;
    
    Монолитное приложение (нельзя переделать в микросервисное без переделки архитектуры всего кода), 
    учитывая высокую нагрузку лучше использовать физический сервер. 
    
Nodejs веб-приложение;

    Для веб-приложения отлично подойдет контейнеризация (docker). Приемуществом будет легкое масштабирование. 
Мобильное приложение c версиями для Android и iOS;
    
    Мобильное приложение лучше размещать на виртуальном сервере(физический сервер 
    не требуется из-за относительно невысокой нагрузки, при этом docker можно использовать для разворачивания api) 
Шина данных на базе Apache Kafka;

    Подойдет и контейнеризация и виртуальная машина, в зависимости от критичности к потере данных. 

Elasticsearch кластер для реализации логирования продуктивного веб-приложения - три ноды elasticsearch, два logstash и две ноды kibana;

    ELK стак можно разместить как на виртуалках, так и с помощью контейнеров docker. 
    Отказоустойчивость к работе ELK и сохранности данных обеспечит сам ELK стак 
    за счет внутренних механизмов (replica nods)
Мониторинг-стек на базе Prometheus и Grafana;

    Со стеком мониторинга Prometheus и Grafana не знаком, но судя по подробной документации на dockerhub,
    для этого стака можно смело использовать docker
    
    

MongoDB, как основное хранилище данных для java-приложения;

    Базу данных рекомендуется хранить на физической машине, главное требование - высокая нагрузка.
Gitlab сервер для реализации CI/CD процессов и приватный (закрытый) Docker Registry.

    И для первого и для второго подойдет docker

## Задача 3

Запустите первый контейнер из образа ***centos*** c любым тэгом в фоновом режиме, подключив папку ```/data``` из текущей рабочей директории на хостовой машине в ```/data``` контейнера;

    docker run -t -d -v /home/test/data:/home/test/data centos:8

Запустите второй контейнер из образа ***debian*** в фоновом режиме, подключив папку ```/data``` из текущей рабочей директории на хостовой машине в ```/data``` контейнера;

    docker run -t -d -v /home/test/data:/home/test/data debian:10
Подключитесь к первому контейнеру с помощью ```docker exec``` и создайте текстовый файл любого содержания в ```/data```;

    docker exec -it a2c049851c9a bash
    cd /home/test/data
    touch netology_test
Добавьте еще один файл в папку ```/data``` на хостовой машине;

    touch netology_2
Подключитесь во второй контейнер и отобразите листинг и содержание файлов в ```/data``` контейнера.
     
    docker exec -it 0769f033b86e bash
    cd /home/test/data
    
    root@0769f033b86e:/home/test/data# ls
    netology_2  netology_test
## Задача 4 (*)

Воспроизвести практическую часть лекции самостоятельно.

Соберите Docker образ с Ansible, загрузите на Docker Hub и пришлите ссылку вместе с остальными ответами к задачам.

##### Dockerfile был нагло скопипастен из лекции.

    docker build -t pupsik/ansible:netology .

    docker push pupsikn/ansible:netology
Результат - https://hub.docker.com/repository/docker/pupsik/ansible

---
