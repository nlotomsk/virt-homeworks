# Домашнее задание к занятию 5. «Оркестрация кластером Docker контейнеров на примере Docker Swarm»

## Как сдавать задания

Обязательны к выполнению задачи без звёздочки. Их нужно выполнить, чтобы получить зачёт и диплом о профессиональной переподготовке.

Задачи со звёдочкой (*) — это дополнительные задачи и/или задачи повышенной сложности. Их выполнять не обязательно, но они помогут вам глубже понять тему.

Домашнее задание выполните в файле readme.md в GitHub-репозитории. В личном кабинете отправьте на проверку ссылку на .md-файл в вашем репозитории.

Любые вопросы по решению задач задавайте в чате учебной группы.

---


## Важно

1. Перед отправкой работы на проверку удаляйте неиспользуемые ресурсы.
Это нужно, чтобы не расходовать средства, полученные в результате использования промокода.
Подробные рекомендации [здесь](https://github.com/netology-code/virt-homeworks/blob/virt-11/r/README.md).

2. [Ссылки для установки открытого ПО](https://github.com/netology-code/devops-materials/blob/master/README.md).

---

## Задача 1

Дайте письменые ответы на вопросы:

- В чём отличие режимов работы сервисов в Docker Swarm-кластере: replication и global?
```
Если global это означает, что данный сервис будет запущен ровно в одном экземпляре 
на всех возможных нодах. А replicated означает, что n-ое кол-во контейнеров для 
данного сервиса будет запущено на всех доступных нодах.
```
[Оригинал статьи](https://habr.com/ru/post/659813/)

- Какой алгоритм выбора лидера используется в Docker Swarm-кластере?
```
Лидер нода выбирается из управляючих нод путем Raft согласованного алгоритма.
Сам Raft-алгоритм имеет ограничение на количество управляющих нод. 
Распределенные решения должны быть одобрены большинством управляющих 
узлов, называемых кворумом. Это означает, что рекомендуется нечетное 
количество управляющих узлов.
```

[Оригинал статьи](https://kamaok.org.ua/?p=2980)

- Что такое Overlay Network?
```
Use overlay networks
The overlay network driver creates a distributed network among multiple
Docker daemon hosts. This network sits on top of (overlays) the host-
specific networks, allowing containers connected to it (including swarm s
ervice containers) to communicate securely when encryption is enabled. 
Docker transparently handles routing of each packet to and from the 
correct Docker daemon host and the correct destination container.

When you initialize a swarm or join a Docker host to an existing swarm, 
two new networks are created on that Docker host:

an overlay network called ingress, which handles the control and data 
traffic related to swarm services. When you create a swarm service and 
do not connect it to a user-defined overlay network, it connects to 
the ingress network by default.
a bridge network called docker_gwbridge, which connects the individual 
Docker daemon to the other daemons participating in the swarm.
You can create user-defined overlay networks using docker network create, 
in the same way that you can create user-defined bridge networks. Services 
or containers can be connected to more than one network at a time. Services 
or containers can only communicate across networks they are each connected to.

Although you can connect both swarm services and standalone containers 
to an overlay network, the default behaviors and configuration concerns 
are different. For that reason, the rest of this topic is divided into o
perations that apply to all overlay networks, those that apply to swarm 
ervice networks, and those that apply to overlay networks used by standalone 
containers.
```

[Оригинал статьи](https://docs.docker.com/network/overlay/)

## Задача 2

Создайте ваш первый Docker Swarm-кластер в Яндекс Облаке.

Чтобы получить зачёт, предоставьте скриншот из терминала (консоли) с выводом команды:
```
docker node ls
```
![image](https://user-images.githubusercontent.com/93542374/223503177-46fb6088-78a3-4173-bfb7-37d14dee21b6.png)


## Задача 3

Создайте ваш первый, готовый к боевой эксплуатации кластер мониторинга, состоящий из стека микросервисов.

Чтобы получить зачёт, предоставьте скриншот из терминала (консоли), с выводом команды:
```
docker service ls
```

![image](https://user-images.githubusercontent.com/93542374/223503517-a9526282-478a-425b-a96d-85e0e2acea3f.png)


## Задача 4 (*)

Выполните на лидере Docker Swarm-кластера команду, указанную ниже, и дайте письменное описание её функционала — что она делает и зачем нужна:
```
# см.документацию: https://docs.docker.com/engine/swarm/swarm_manager_locking/
docker swarm update --autolock=true
```

![image](https://user-images.githubusercontent.com/93542374/223503704-74658c64-78c5-488a-b484-d141d264df94.png)


