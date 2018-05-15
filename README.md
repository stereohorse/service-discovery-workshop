# Подготовка среды для тренинга по Service Discovery

## Настройка

### Установить инструменты

```bash
> brew cask install docker virtualbox vagrant \
    && brew install ansible
```

### Установить hostmanager плагин для vagrant

```bash
> vagrant plugin install vagrant-hostmanager
```

### Загрузить vagrant-образ для тестовой среды

```bash
> vagrant box add stereohorse/alfa-infra-sandbox
```

### Создать учётную запись на Docker Hub

Вот [здесь](https://hub.docker.com/). Затем нужно залогиниться из командной строки:

```bash
> docker login
```

### Установить JDK 8

По этой [ссылке](http://www.oracle.com/technetwork/java/javase/downloads/index.html). После установки проверяем версию:

```bash
$ javac -version

javac 1.8.0_<номер, котрый можно проигнорировать>
```

### Установить IntelliJ IDEA

Подойдёт и Community Edition.


## Проверяем установку

```bash
# загружаем этот репозиторий
git clone git@github.com:stereohorse/service-discovery-workshop.git

cd service-discovery-workshop

# запускаем виртуальные машины
vagrant up
```

После этого открываем в браузере:

1. [vm1:5050](http://vm1:5050)
2. [vm2:8080](http://vm1:8080)

Должны открыться UI Mesos и Marathon. После этого останавливаем виртуальные машины:

```bash
> vagrant suspend
```
